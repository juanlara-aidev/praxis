# Praxis

> Sistema inteligente de producción de software — extensión para VS Code, Cursor, Windsurf y Antigravity.

Este es el repositorio público de **releases** de Praxis. Si buscas el código fuente, está fuera de distribución.

---

## Instalación rápida (recomendada — un solo comando)

Usa el one-liner que corresponda a tu sistema. **Descarga el `.vsix` a una ruta local garantizada (`%TEMP%` / `/tmp`) y lo instala**, así evita problemas con rutas de red (`\\host\share\...`) que algunos editores bloquean por seguridad.

### Windows — PowerShell

```powershell
$tmp="$env:TEMP\praxis.vsix"; iwr "https://github.com/juanlara-aidev/praxis/releases/latest/download/praxis.vsix" -OutFile $tmp; code --install-extension $tmp --force
```

> Reemplaza `code` por `cursor`, `windsurf` o `antigravity` si usas otro editor.

### Windows — cmd.exe

```cmd
curl -fL -o "%TEMP%\praxis.vsix" "https://github.com/juanlara-aidev/praxis/releases/latest/download/praxis.vsix" && code --install-extension "%TEMP%\praxis.vsix" --force
```

### macOS / Linux — bash, zsh, fish

```bash
curl -fL -o /tmp/praxis.vsix "https://github.com/juanlara-aidev/praxis/releases/latest/download/praxis.vsix" && code --install-extension /tmp/praxis.vsix --force
```

> Reemplaza `code` por `cursor`, `windsurf` o `antigravity` si usas otro editor.

Después: recarga la ventana — `Cmd/Ctrl+Shift+P → Reload Window`.

---

## Instalación manual (si prefieres descargar primero)

1. Descarga el `.vsix` desde la pestaña [Releases](https://github.com/juanlara-aidev/praxis/releases/latest).
2. **Muévelo a una ruta local con letra de unidad** (Windows: `C:\Users\<tu-usuario>\AppData\Local\Temp\`, macOS/Linux: `/tmp/` o `~/`). No lo dejes en una carpeta sincronizada vía SMB / red / VM share.
3. Instala desde esa ruta:

   ```bash
   # ejemplo Windows
   code --install-extension "C:\Users\<tu-usuario>\AppData\Local\Temp\praxis.vsix" --force

   # ejemplo macOS / Linux
   code --install-extension /tmp/praxis.vsix --force
   ```
4. Recarga la ventana — `Cmd/Ctrl+Shift+P → Reload Window`.

---

## Solución de problemas

### `Extract: UNC host '<nombre>' access is not allowed`

Este error aparece **al instalar el `.vsix`** cuando éste está en una ruta de red estilo `\\Mac\Home\...`, `\\wsl$\...`, `\\server\share\...`. Suele pasar cuando corres Windows en una VM (Parallels, VMware, UTM) y la carpeta de Downloads del Windows apunta físicamente al disco del Mac/Linux host.

**Soluciones (de más sencilla a más permisiva)**:

1. **Usa el one-liner de "Instalación rápida" arriba.** Descarga el `.vsix` a `%TEMP%`, que siempre es una ruta local con letra de unidad. Resuelve el 100 % de los casos sin tocar settings.

2. **Mueve el `.vsix` a una ruta local antes de instalarlo.** Cualquier carpeta bajo `C:\` (no `\\Mac\...`, no `\\wsl$\...`) sirve.

3. **Permite el host UNC en VS Code.** Edita tus settings de usuario (`Cmd/Ctrl+,` → "Open User Settings (JSON)") y agrega el host que aparece en el error:

   ```json
   "security.allowedUNCHosts": ["mac", "wsl$"]
   ```

   Reinicia el editor. Después podrás instalar `.vsix` desde rutas UNC sin bloqueo.

> Una vez instalada, **Praxis se actualiza sola** desde el sidebar y siempre descarga a `%TEMP%` / `/tmp`. Este problema sólo aparece en la primera instalación.

### El comando `code` (o `cursor`, `windsurf`, `antigravity`) no se reconoce

El CLI del editor no está en tu `PATH`. Abre el editor y ejecuta:

```
Cmd/Ctrl+Shift+P → Shell Command: Install 'code' command in PATH
```

(o la variante para Cursor / Windsurf / Antigravity). Después abre una terminal nueva y reintenta el one-liner.

---

## Actualizaciones automáticas

Desde la versión `1.2.7` Praxis se actualiza sola con un **banner azul brillante** en la parte superior del sidebar que aparece SOLO cuando hay versión nueva:

- Banner full-width "↑ Actualizar a vX.Y.Z" — imposible no verlo.
- Toda el área del banner es el botón. Click → terminal integrado descarga + instala la nueva versión.
- Al terminar te ofrece recargar la ventana.
- Si quieres forzar un check manual: `Cmd/Ctrl+Shift+P` → "Praxis: Buscar actualizaciones de la extensión".

Cero GitHub manual. Cero descargas. Cero comandos tecleados.

---

## URL estable del último `.vsix`

Para scripts o automatizaciones, la última versión siempre está en:

```
https://github.com/juanlara-aidev/praxis/releases/latest/download/praxis.vsix
```

Esta URL no lleva versión en el filename — siempre resuelve al asset más reciente.

---

## Membresía

El uso está gated por membresía activa de [SinergIA](https://www.skool.com/sinergia). La extensión se puede instalar libremente; el panel de autenticación aparece al abrirla.
