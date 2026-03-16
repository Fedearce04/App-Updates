# Release Checklist (v2.5.27)

- Generated UTC: 2026-03-16T23:49:21.7042930Z
- App repo: App (private)
- App origin: https://github.com/Fedearce04/App.git
- Source commit (App): 6f11d48f4f43
- Updates repo: Fedearce04/App-Updates (public)
- Asset: DentalSystem-Setup-2.5.27.exe
- SHA256: 224df54273ac0f420073d6004f5007b37ced7d3502445cd7a97f778aa67db404

## Flujo

1. Confirmar commit y push del codigo fuente en App (validado automaticamente por este script).
2. Confirmar merge en main del repo App.
3. Crear tag en App: git tag v2.5.27 y git push origin v2.5.27.
4. Ir a https://github.com/Fedearce04/App-Updates/releases/new.
5. Crear release con tag v2.5.27 en App-Updates.
6. Subir asset DentalSystem-Setup-2.5.27.exe.
7. Subir update.json desde:
   - Versionado: release\app-updates\v2.5.27\update.json
   - Latest (raiz): release\app-updates\update.json
8. Ejecutar gate de publicacion (obligatorio, debe dar PASS):
   .\\scripts\\verify_windows_update_publication.ps1 -Version "2.5.27" -VerifyAssetSha256
9. Verificar URL publica:
   - Manifest: https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json
   - Asset: https://github.com/Fedearce04/App-Updates/releases/download/v2.5.27/DentalSystem-Setup-2.5.27.exe
10. Validar en app instalada que aparezca boton de actualizacion.

## Build recomendado en App (produccion)

.\\scripts\\build_windows_installer.ps1 -UseLinkedSupabase -Environment production -Version "2.5.27" -UpdateManifestUrl "https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json" -UpdateChannel "stable"
