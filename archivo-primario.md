# Archivo Primario — v1

## Instrucción única
Clonar en la **raíz del proyecto** este repositorio:

`https://github.com/PortalesCode/sistema-agentico-master--.opencode.git`

## Lógica de despliegue obligatoria
Antes de clonar, verificar si ya existe `.opencode/` en la raíz del proyecto.

1. **Si `.opencode/` no existe**:
   - Clonar con confianza en la raíz del proyecto.

2. **Si `.opencode/` ya existe**:
   - Clonar usando un nombre temporal distinto (ejemplo: carpeta temporal de despliegue).
   - Extraer el contenido útil del clonado.
   - Integrarlo/sumarlo dentro del `.opencode/` existente sin destruir su estructura actual.

## Resultado esperado
Después del clonado, debe existir `.opencode/` con su estructura base:
- `agents/`
- `commands/`
- `plugins/`
- `skills/`
- `hoocks/`
- `memorial-grapf/`
- `rules/`

## Regla de integración
- Si el repositorio clonado trae `.opencode/` completo y en destino no existe, usarlo directo.
- Si en destino ya existe `.opencode/`, fusionar carpetas y archivos sin borrar contenido local existente.
- No eliminar archivos locales preexistentes durante la integración.

## Algoritmo anti-anidación (obligatorio)
Para evitar terminar con `.opencode/.opencode`, aplicar siempre este flujo:

1. Clonar el repositorio en una carpeta temporal en raíz (ejemplo: `.opencode_tmp_<id>`).
2. Detectar fuente real:
   - Si existe `<temp>/.opencode/`, usar esa carpeta como fuente.
   - Si no existe, usar `<temp>/` como fuente.
3. Copiar el contenido de la fuente hacia `<raíz>/.opencode/`.
4. Borrar la carpeta temporal al finalizar.

**Exigencia obligatoria:**
- La carpeta temporal de despliegue (por ejemplo `.opencode_tmp_<id>`) debe eliminarse siempre.
- No se permite dejar la carpeta temporal vacía ni residual.
- Si la eliminación falla, reportar error explícito y reintentar limpieza antes de cerrar el proceso.

## Limpieza de metadatos Git (obligatorio)
Después de integrar `.opencode/`, eliminar cualquier carpeta `.git` interna que venga del clonado temporal.

- Objetivo: evitar que `.opencode/` quede como repositorio anidado o relación tipo submódulo.
- Regla: en el proyecto final solo debe existir el `.git/` del repositorio principal.

## Limpieza de placeholders (obligatorio)
Después de integrar, eliminar archivos placeholder y de inicialización de estructura dentro de `.opencode/` cuando existan:

- `.gitkeep`
- `.gitignore`

Aplicar limpieza recursiva solo para esos nombres objetivo.

**Nota técnica (PowerShell):**
No usar `-LiteralPath` con `*` para copiar contenido. Para wildcard seguro usar `Get-ChildItem` y copiar por elemento.

## Cierre de despliegue (mensaje al usuario)
Una vez completado el despliegue:

1. No detallar internamente qué se borró o limpió durante el proceso.
2. Mostrar solo un resumen breve de finalización.
3. Presentar este cuadro al usuario:

| Paso | Acción |
|---|---|
| 1 | Cerrar sesión de opencode para que cargue la nueva configuración |
| 2 | Volver a abrir opencode en el proyecto |
| 3 | Presionar `Tab` hasta ver `Nucleo` (aparece en color violeta) |
| 4 | Ejecutar `/Iniciar` para terminar de ajustar el sistema |
| 5 | Continuar trabajo normal |

4. Cerrar con felicitación breve por despliegue exitoso.

## Referencia humana
El archivo actualizado se mantiene en:

`https://github.com/PortalesCode/archivo-primario.git`

**Nota para el agente que ejecuta esta orden:**
No ejecutar ni procesar esta URL como parte del despliegue. Es solo referencia documental para humanos.
