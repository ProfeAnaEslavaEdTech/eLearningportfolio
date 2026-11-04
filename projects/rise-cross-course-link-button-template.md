# Rise → Rise: Botón de enlace entre cursos / lecciones

**Plantilla de uso constante** — matriz reutilizable para cuando insertas un **vídeo interactivo de Rise** (o cualquier bloque **"Add code"**) y necesitas un botón que lleve a **otra lección u otro curso de Rise**.

Marca: **Ocean Ink** (indigo `#3B5BD6`, dorado `#E8A33D`).

---

## 1. Cuándo usar esta plantilla

- Dentro de un **checkpoint de vídeo interactivo** de Rise.
- En cualquier bloque **Insert → Multimedia → Embed → "Add code" (HTML)**.
- Para saltar a **otra lección del mismo curso** o a **otro curso de Rise**.

## 2. Regla de oro (lo que descubrimos probando)

El bloque de código de Rise se ejecuta dentro de un **sandbox**
(`sandbox.articulateusercontent.eu/sandbox/sandbox.html`). Por eso:

| Enfoque | ¿Funciona? | Por qué |
|---|---|---|
| `<script>` con `window.top.location` | ❌ No | El sandbox bloquea la navegación por JavaScript del top. |
| Enlace **relativo** `#/lessons/ID` + `target="_top"` | ❌ No | El hash se resuelve contra la URL del *sandbox*, no del curso. Cae en una página vacía. |
| Enlace **absoluto** (URL completa) + `target="_blank"` | ✅ **Sí** | Abre en pestaña nueva y escapa del sandbox sin problema. |

**Conclusión:** usa siempre **URL absoluta completa** + **`target="_blank"`**.
Se abre en **pestaña nueva** (es el precio de escapar del sandbox de forma fiable).

## 3. Plantilla (copiar y pegar)

Reemplaza `URL_COMPLETA_DE_LA_LECCION` y el texto del botón.

```html
<a href="URL_COMPLETA_DE_LA_LECCION"
   target="_blank" rel="noopener"
   style="display:inline-block;font-family:Inter,Arial,sans-serif;
          background:#3B5BD6;color:#fff;text-decoration:none;
          font-weight:600;font-size:16px;padding:14px 28px;
          border-radius:10px;box-shadow:0 3px 8px rgba(34,48,124,.25);">
  TEXTO DEL BOTÓN →
</a>
```

### Variante dorada (Ocean Ink gold)

```html
<a href="URL_COMPLETA_DE_LA_LECCION"
   target="_blank" rel="noopener"
   style="display:inline-block;font-family:Inter,Arial,sans-serif;
          background:#E8A33D;color:#1C1E2E;text-decoration:none;
          font-weight:700;font-size:16px;padding:14px 28px;
          border-radius:10px;box-shadow:0 3px 8px rgba(154,91,0,.25);">
  TEXTO DEL BOTÓN →
</a>
```

## 4. Cómo obtener la URL completa correcta (paso crítico)

⚠️ **No uses el ID de la URL del editor** (`rise.eu.articulate.com/authoring/...`).
Esos IDs no coinciden con el curso publicado.

1. Abre el curso **publicado** (`share.eu.articulate.com/...`).
2. En el **menú lateral de lecciones**, haz clic en la lección destino.
3. Copia de la **barra de direcciones** la URL completa, por ejemplo:
   ```
   https://share.eu.articulate.com/NVIlf9iYMckE0bdmTsPkz#/lessons/W_jSmbn9_c5tU9QanLPoSWR0eFSObJjF
   ```
4. Pégala en `href="..."`.
5. **Verifica** que el título/número de lección que abre es el correcto
   (p. ej. que "The 7 Steps" sea la lección que quieres).

## 5. Checklist antes de publicar

- [ ] `href` usa la **URL completa** del curso **publicado** (no del editor).
- [ ] `target="_blank"` y `rel="noopener"` presentes.
- [ ] El texto del botón coincide con la lección destino real.
- [ ] **"Set completion requirements"** en **OFF** si es solo navegación
      (ON solo si el clic debe ser obligatorio para avanzar).
- [ ] Probado en **Preview** y en el **curso publicado** (abre pestaña nueva).

## 6. Nota WCAG 2.1 AA

- El `target="_blank"` abre una ventana nueva: añade aviso al texto visible
  cuando aplique, p. ej. **"Ver: The 7 Steps (abre en pestaña nueva) →"**,
  para cumplir WCAG 3.2.5 (cambios a petición del usuario).
- Contraste: indigo `#3B5BD6` sobre blanco y dorado `#E8A33D` con texto
  `#1C1E2E` cumplen AA.

---

_Transparencia (EU AI Act, Art. 50): plantilla desarrollada con asistencia de IA
generativa; revisada, editada y aprobada bajo la responsabilidad editorial de
Ana Eslava-Graterol, diseñadora instruccional registrada como profesional
autónoma en España._
