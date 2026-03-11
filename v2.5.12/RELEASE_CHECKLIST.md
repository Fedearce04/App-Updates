# Release Checklist (v2.5.12)

- Generated UTC: 2026-03-11T03:17:16.9489539Z
- App repo: App (private)
- App origin: https://github.com/Fedearce04/App.git
- Source commit (App): c92963061bb4
- Updates repo: Fedearce04/App-Updates (public)
- Asset: DentalSystem-Setup-2.5.12.exe
- SHA256: f656060c18b6d926774c79873dc86b4a8b5c33e25eeeae4adb0abda29bda7eb2

## Flujo

1. Confirmar commit y push del codigo fuente en App (validado automaticamente por este script).
2. Confirmar merge en main del repo App.
3. Crear tag en App: git tag v2.5.12 y git push origin v2.5.12.
4. Ir a https://github.com/Fedearce04/App-Updates/releases/new.
5. Crear release con tag v2.5.12 en App-Updates.
6. Subir asset DentalSystem-Setup-2.5.12.exe.
7. Subir update.json desde:
   - Versionado: release\app-updates\v2.5.12\update.json
   - Latest (raiz): release\app-updates\update.json
8. Verificar URL publica:
   - Manifest: https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json
   - Asset: https://github.com/Fedearce04/App-Updates/releases/download/v2.5.12/DentalSystem-Setup-2.5.12.exe
9. Validar en app instalada que aparezca boton de actualizacion.

## Build recomendado en App (produccion)

.\\scripts\\build_windows_installer.ps1 -UseLinkedSupabase -Environment production -Version "2.5.12" -UpdateManifestUrl "https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json" -UpdateChannel "stable"
