# Release Checklist (v2.5.15)

- Generated UTC: 2026-03-12T02:12:12.6693021Z
- App repo: App (private)
- App origin: https://github.com/Fedearce04/App.git
- Source commit (App): 7128fb756b21
- Updates repo: Fedearce04/App-Updates (public)
- Asset: DentalSystem-Setup-2.5.15.exe
- SHA256: 3e4ee0a9f968fec3bca4017c86105c0d94810eb17b98b2e5c1c952f785a80d35

## Flujo

1. Confirmar commit y push del codigo fuente en App (validado automaticamente por este script).
2. Confirmar merge en main del repo App.
3. Crear tag en App: git tag v2.5.15 y git push origin v2.5.15.
4. Ir a https://github.com/Fedearce04/App-Updates/releases/new.
5. Crear release con tag v2.5.15 en App-Updates.
6. Subir asset DentalSystem-Setup-2.5.15.exe.
7. Subir update.json desde:
   - Versionado: release\app-updates\v2.5.15\update.json
   - Latest (raiz): release\app-updates\update.json
8. Ejecutar gate de publicacion (obligatorio, debe dar PASS):
   .\\scripts\\verify_windows_update_publication.ps1 -Version "2.5.15" -VerifyAssetSha256
9. Verificar URL publica:
   - Manifest: https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json
   - Asset: https://github.com/Fedearce04/App-Updates/releases/download/v2.5.15/DentalSystem-Setup-2.5.15.exe
10. Validar en app instalada que aparezca boton de actualizacion.

## Build recomendado en App (produccion)

.\\scripts\\build_windows_installer.ps1 -UseLinkedSupabase -Environment production -Version "2.5.15" -UpdateManifestUrl "https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json" -UpdateChannel "stable"
