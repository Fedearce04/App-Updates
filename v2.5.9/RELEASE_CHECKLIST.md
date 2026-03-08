# Release Checklist (v2.5.9)

- Generated UTC: 2026-03-08T11:54:51.8521884Z
- App repo: App (private)
- Updates repo: Fedearce04/App-Updates (public)
- Asset: DentalSystem-Setup-2.5.9.exe
- SHA256: 01c6f61ac6dfa4544f35ab4d5f39c321e583fe379f94a5c04f61557a888710ac

## Flujo

1. Confirmar merge en main del repo App.
2. Crear tag en App: git tag v2.5.9 y git push origin v2.5.9.
3. Ir a https://github.com/Fedearce04/App-Updates/releases/new.
4. Crear release con tag v2.5.9 en App-Updates.
5. Subir asset DentalSystem-Setup-2.5.9.exe.
6. Subir update.json desde:
   - Versionado: release\app-updates\v2.5.9\update.json
   - Latest (raiz): release\app-updates\update.json
7. Verificar URL publica:
   - Manifest: https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json
   - Asset: https://github.com/Fedearce04/App-Updates/releases/download/v2.5.9/DentalSystem-Setup-2.5.9.exe
8. Validar en app instalada que aparezca boton de actualizacion.

## Build recomendado en App (produccion)

.\\scripts\\build_windows_installer.ps1 -UseLinkedSupabase -Environment production -Version "2.5.9" -UpdateManifestUrl "https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json" -UpdateChannel "stable"
