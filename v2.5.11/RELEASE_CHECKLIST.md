# Release Checklist (v2.5.11)

- Generated UTC: 2026-03-09T22:36:08.5666663Z
- App repo: App (private)
- Updates repo: Fedearce04/App-Updates (public)
- Asset: DentalSystem-Setup-2.5.11.exe
- SHA256: 21089aae34ab953016346ab024c23621ec5a9edc1edec1fdff1d7e3b64361081

## Flujo

1. Confirmar merge en main del repo App.
2. Crear tag en App: git tag v2.5.11 y git push origin v2.5.11.
3. Ir a https://github.com/Fedearce04/App-Updates/releases/new.
4. Crear release con tag v2.5.11 en App-Updates.
5. Subir asset DentalSystem-Setup-2.5.11.exe.
6. Subir update.json desde:
   - Versionado: release\app-updates\v2.5.11\update.json
   - Latest (raiz): release\app-updates\update.json
7. Verificar URL publica:
   - Manifest: https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json
   - Asset: https://github.com/Fedearce04/App-Updates/releases/download/v2.5.11/DentalSystem-Setup-2.5.11.exe
8. Validar en app instalada que aparezca boton de actualizacion.

## Build recomendado en App (produccion)

.\\scripts\\build_windows_installer.ps1 -UseLinkedSupabase -Environment production -Version "2.5.11" -UpdateManifestUrl "https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json" -UpdateChannel "stable"
