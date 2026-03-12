# Release Checklist (v2.5.16)

- Generated UTC: 2026-03-12T17:24:52.9757140Z
- App repo: App (private)
- App origin: https://github.com/Fedearce04/App.git
- Source commit (App): dd9bd74f8969
- Updates repo: Fedearce04/App-Updates (public)
- Asset: DentalSystem-Setup-2.5.16.exe
- SHA256: 1c117ad1983325763281ef946ae07dbc84aad69ca50f7c96a910a4e54bd1ad4b

## Flujo

1. Confirmar commit y push del codigo fuente en App (validado automaticamente por este script).
2. Confirmar merge en main del repo App.
3. Crear tag en App: git tag v2.5.16 y git push origin v2.5.16.
4. Ir a https://github.com/Fedearce04/App-Updates/releases/new.
5. Crear release con tag v2.5.16 en App-Updates.
6. Subir asset DentalSystem-Setup-2.5.16.exe.
7. Subir update.json desde:
   - Versionado: release\app-updates\v2.5.16\update.json
   - Latest (raiz): release\app-updates\update.json
8. Ejecutar gate de publicacion (obligatorio, debe dar PASS):
   .\\scripts\\verify_windows_update_publication.ps1 -Version "2.5.16" -VerifyAssetSha256
9. Verificar URL publica:
   - Manifest: https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json
   - Asset: https://github.com/Fedearce04/App-Updates/releases/download/v2.5.16/DentalSystem-Setup-2.5.16.exe
10. Validar en app instalada que aparezca boton de actualizacion.

## Build recomendado en App (produccion)

.\\scripts\\build_windows_installer.ps1 -UseLinkedSupabase -Environment production -Version "2.5.16" -UpdateManifestUrl "https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json" -UpdateChannel "stable"
