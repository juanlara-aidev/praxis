<!--
  Esta página la lee un alumno de SinergIA por primera vez.
  Tono amigable, cero jerga. Mantener identidad: Juan Lara.
  Ver "Reglas de copy público" en praxis-dev/CLAUDE.md.
-->

# Praxis

> Hecho por **Juan Lara** · Para la comunidad **SinergIA**

Hola, soy Juan. Hice esta extensión para que cuando abras tu editor de código y quieras crear un proyecto SaaS completo, lo tengas listo en menos de un minuto sin pelearte con setup. Pensada para ti, alumno de SinergIA, estés empezando o ya hayas creado varios proyectos.

---

## Antes de empezar

Necesitas dos cosas:

1. Un editor de código instalado: **VS Code**, **Cursor**, **Windsurf** o **Antigravity**.
2. Tu correo de SinergIA a la mano (con el que entras a Skool).

Eso es todo.

---

## Instálala en 30 segundos

Copia el comando que corresponda a tu sistema, pégalo en una terminal y dale Enter. Descarga la extensión a una carpeta temporal de tu computadora y la instala automáticamente.

### En Windows (PowerShell)

```powershell
$tmp="$env:TEMP\praxis.vsix"; iwr "https://github.com/juanlara-aidev/praxis/releases/latest/download/praxis.vsix" -OutFile $tmp; code --install-extension $tmp --force
```

### En Windows (cmd.exe)

```cmd
curl -fL -o "%TEMP%\praxis.vsix" "https://github.com/juanlara-aidev/praxis/releases/latest/download/praxis.vsix" && code --install-extension "%TEMP%\praxis.vsix" --force
```

### En macOS o Linux

```bash
curl -fL -o /tmp/praxis.vsix "https://github.com/juanlara-aidev/praxis/releases/latest/download/praxis.vsix" && code --install-extension /tmp/praxis.vsix --force
```

> ¿Usas Cursor, Windsurf o Antigravity? Reemplaza `code` por `cursor`, `windsurf` o `antigravity` en el comando.

Cuando termine, recarga la ventana del editor: `Cmd/Ctrl + Shift + P` → escribe **Reload Window** → Enter.

---

## Tu primer uso, paso a paso

1. **Abre tu editor.** Vas a ver un nuevo ícono ⚡ en la barra lateral de la izquierda. Dale click — se abre el panel de Praxis.

2. **Verifica tu membresía.** El panel te pide tu correo de SinergIA. Escríbelo y dale a **Verificar**. Praxis confirma que eres miembro y te abre el dashboard.

3. **Activa Praxis en tu proyecto.** Abre la carpeta donde quieres crear tu app (puede estar vacía). En el panel de Praxis verás un botón grande **INICIAR**. Dale click.

4. **¡Listo!** En menos de un minuto Praxis te dejó:
   - El proyecto Next.js completo configurado.
   - Un archivo `CLAUDE.md` con instrucciones para que Claude trabaje en tu codebase.
   - 7 habilidades activas de inicio (brief, prp, bucle-agentico, frontend-design, playwright-cli, skill-creator y build-with-agent-team).
   - Conexiones automáticas con Next DevTools y Playwright.
   - Un `README.md` en la raíz con los siguientes pasos (`npm install`, configurar tu `.env.local`, `npm run dev`).

Después de eso, abre el `README.md` que te dejé y sigues los pasos. En SinergIA tienes los videos que te explican cada parte.

---

## Cómo se actualiza

Praxis se actualiza sola. En la parte de arriba del panel de Praxis siempre vas a ver un pequeño botón de **Actualizar**:

- Cuando estás al día, el botón aparece tenue (casi invisible).
- Cuando hay versión nueva, el botón se pone azul brillante con el número de la versión nueva.

En cualquiera de los dos casos, click en el botón → se descarga la versión más reciente → te ofrece recargar la ventana → listo. Tarda 5 segundos.

> 💡 ¿Algo raro pasa con la extensión? Dale click al botón de Actualizar aunque estés al día. Reinstala la última versión y arregla la mayoría de los problemas (archivos corruptos, ajustes que no se cargaron, lo que sea).

---

## ¿Y si ya tengo un proyecto que estaba trabajando?

Praxis sabe distinguir cuándo tu carpeta está vacía y cuándo ya tienes archivos. Si abres un proyecto que ya tenía cosas tuyas (un `CLAUDE.md` propio, un `README.md`, código en `src/`, etc.):

- Praxis te pregunta antes de tocar nada.
- **No se sobrescribe ningún archivo que ya tengas.** Tu `CLAUDE.md`, tu `README.md`, tu código quedan intactos byte por byte.
- Solo te agrega lo que falta: las habilidades en `.claude/skills/` que no tengas y las conexiones (MCPs) en `.mcp.json` que no estén configuradas.

Es seguro probarlo en un proyecto que ya estés desarrollando.

---

## Si algo se rompió

### "No se reconoce el comando `code` (o `cursor`, `windsurf`, `antigravity`)"

El comando del editor no está en el sistema. Abre tu editor, pulsa `Cmd/Ctrl + Shift + P`, escribe **Shell Command: Install 'code' command in PATH** y dale Enter (la versión correspondiente para Cursor/Windsurf/Antigravity tiene el mismo nombre con su prefijo). Después abre una terminal nueva y vuelve a intentar el comando de instalación.

### "Extract: UNC host '...' access is not allowed"

Te aparece si estás corriendo Windows dentro de Parallels, VMware o WSL. La carpeta donde descargaste el archivo apunta al disco del Mac/Linux y el editor lo bloquea por seguridad. **La solución es usar el comando de la sección "Instálala en 30 segundos"** — descarga el archivo a `%TEMP%` (que es una carpeta local de Windows) y se instala desde ahí. Si seguiste otro camino, copia el archivo `praxis.vsix` a `C:\Users\<tu-usuario>\` y ejecuta `code --install-extension "C:\Users\<tu-usuario>\praxis.vsix" --force` desde ahí.

### Cualquier otra cosa

Cuéntame en SinergIA. La comunidad probablemente ya pasó por lo mismo.

---

## ¿Tienes dudas o ideas?

- 💙 La **comunidad de SinergIA** en Skool: https://www.skool.com/sinergia
- 🐛 Para reportar bugs: [GitHub Issues del repo público](https://github.com/juanlara-aidev/praxis/issues)

---

Hecho con cariño por **Juan Lara** · Para la comunidad **SinergIA** 💙
