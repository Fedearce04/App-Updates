# App-Updates (Public)

Repositorio publico de distribucion Windows.

## Estructura minima

- `update.json` (manifest latest consumido por la app)
- `releases/vX.Y.Z/update.json` (copia historica opcional del manifest)
- Assets `.exe` en GitHub Releases (no dentro del git repo)

## Flujo de publicacion

1. Crear release `vX.Y.Z`.
2. Adjuntar `.exe` del instalador.
3. Actualizar `update.json` de raiz.
4. Mantener copia en `releases/vX.Y.Z/update.json`.

## URL que consume la app

`https://raw.githubusercontent.com/Fedearce04/App-Updates/main/update.json`
