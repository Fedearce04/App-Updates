# Release Checklist (v2.5.20)

- Generated UTC: 2026-03-13T16:48:23.7069705Z
- App repo: App (private)
- App origin: https://github.com/Fedearce04/App.git
- Source commit (App): b78da4a81767
- Updates repo: Fedearce04/App-Updates (public)
- Asset: DentalSystem-Setup-2.5.20.exe
- SHA256: e10d5984270260ec6f21104887bc0fc9f11739b35cc2ec35a769352fa20e51b6

## Flujo

1. Confirmar commit y push del codigo fuente en App (validado automaticamente por este script).
2. Confirmar merge en main del repo App.
3. Crear tag en App: git tag v2.5.20 y git push origin v2.5.20.
4. Ir a https://github.com/Fedearce04/App-Updates/releases/new.
5. Crear release con tag v2.5.20 en App-Updates.
6. Subir asset DentalSystem-Setup-2.5.20.exe.
7. Subir update.json desde:
   - Versionado: release\app-updates\v2.5.20\update.json
   - Latest (raiz): release\app-updates\update.json
8. Ejecutar gate de publicacion (obligatorio, debe dar PASS):
   .\\scripts\\verify_windows_update_publication.ps1 -Version "2.5.20" -VerifyAssetSha256
9. Verificar URL publica:
   - Manifest: https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json
   - Asset: https://github.com/Fedearce04/App-Updates/releases/download/v2.5.20/DentalSystem-Setup-2.5.20.exe
10. Validar en app instalada que aparezca boton de actualizacion.

## Build recomendado en App (produccion)

.\\scripts\\build_windows_installer.ps1 -UseLinkedSupabase -Environment production -Version "2.5.20" -UpdateManifestUrl "https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json" -UpdateChannel "stable"
