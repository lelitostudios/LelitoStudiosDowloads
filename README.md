# LELITO STUDIOS — Content / Distribución

Este repositorio sirve como **servidor de contenido** del launcher Lelito Studios:
módulos remotos, configuración remota y manifest de actualizaciones.

## Archivos
- `lela-remoto.json` → eventos/estado/noticias en vivo (se aplica al abrir el launcher o cada 6 h).
- `lela-manifest.json` → feed de actualización del launcher (`electron-updater` / manifest).
- `lela-mods-manifest.json` → mods remotos por evento + loader (clave `evento/loader`).

## Mods remotos
Carpetas de mods **por evento y loader**:
```
files/mods/
├── tortaland/fabric/   ← mods del Tortaland Fabric
├── tortaland/forge/    ← mods del Tortaland Forge
└── beta-test/
    ├── fabric/
    ├── forge/
    └── vanilla/
```
Para añadir/actualizar mods:
1. Suelta el `.jar` en su carpeta (`files/mods/<evento>/<loader>/`).
2. Regenera el manifest:
   `node scripts\gen-mods-manifest.mjs --event tortaland --loader forge --dir "D:\mods\tortaland\forge" --base "https://raw.githubusercontent.com/lelitostudios/LelitoStudiosDowloads/main/files/mods/tortaland/forge/" --out lela-mods-manifest.json`
3. Commit + push. El launcher descarga solo lo que cambió (hash SHA-256).

> Nota: Arena UHC es **Vanilla** (sin mods) → no necesita carpeta ni entrada en el manifest.
