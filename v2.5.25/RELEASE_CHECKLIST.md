# Release Checklist (v2.5.25)

- Generated UTC: 2026-03-16T22:27:47.2323495Z
- App repo: App (private)
- App origin: https://github.com/Fedearce04/App.git
- Source commit (App): 103c84b3d613
- Updates repo: Fedearce04/App-Updates (public)
- Asset: DentalSystem-Setup-2.5.25.exe
- SHA256: 85e19cc0b6534226f401f9313835bbf855094dd5e296f23435846aa67812885f

## Flujo

1. Confirmar commit y push del codigo fuente en App (validado automaticamente por este script).
2. Confirmar merge en main del repo App.
3. Crear tag en App: git tag v2.5.25 y git push origin v2.5.25.
4. Ir a https://github.com/Fedearce04/App-Updates/releases/new.
5. Crear release con tag v2.5.25 en App-Updates.
6. Subir asset DentalSystem-Setup-2.5.25.exe.
7. Subir update.json desde:
   - Versionado: release\app-updates\v2.5.25\update.json
   - Latest (raiz): release\app-updates\update.json
8. Ejecutar gate de publicacion (obligatorio, debe dar PASS):
   .\\scripts\\verify_windows_update_publication.ps1 -Version "2.5.25" -VerifyAssetSha256
9. Verificar URL publica:
   - Manifest: https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json
   - Asset: https://github.com/Fedearce04/App-Updates/releases/download/v2.5.25/DentalSystem-Setup-2.5.25.exe
10. Validar en app instalada que aparezca boton de actualizacion.

## Build recomendado en App (produccion)

.\\scripts\\build_windows_installer.ps1 -UseLinkedSupabase -Environment production -Version "2.5.25" -UpdateManifestUrl "https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json" -UpdateChannel "stable"
