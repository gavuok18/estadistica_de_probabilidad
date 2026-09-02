# Estadística Probabilística · Aula interactiva

Aula virtual completa de la asignatura **Estadística Probabilística** — Corporación Universitaria
Remington, Facultad de Ciencias Básicas e Ingeniería.

**→ [Abrir la aplicación](https://gavuok18.github.io/estadistica_de_probabilidad/)**

---

## Qué es

Una sola página web que funciona en computador, Android y iPhone. Reúne el material de estudio del
curso, un laboratorio de herramientas de cálculo, talleres que se califican solos y un panel para
que el docente lleve las notas del grupo.

| Módulo | Contenido |
|---|---|
| 1 · El módulo oficial | Las tres unidades del módulo 2016, con cada resultado recalculado |
| 2 · Taller 1 resuelto | Resuelto paso a paso · **protegido con clave** |
| 3 · Teoría del Taller 1 | Conjuntos, operaciones, contingencia, probabilidad |
| 4 · Teoría del Taller 2 | Conteo, permutaciones, combinaciones, árbol, Bayes |
| 5 · Taller 2 | Pendiente del enunciado |
| 6 · Zona de estudio | 26 temas con buscador y filtros |
| 7 · Laboratorio | 7 herramientas interactivas de cálculo |
| 8 · Problemas | 18 ejercicios graduados con solución |
| 9 · Auditoría | Erratas encontradas en el material oficial |
| 10 · Ideas | Propuestas de ampliación |
| 11 · Seguimiento y notas | Planilla del docente, Excel y certificados |
| 12 · Talleres interactivos | Talleres autocalificados para el estudiante |
| 13 · Talleres y entregas | Panel del docente: crear talleres y ver entregas |

## Talleres interactivos

Las preguntas **no son fijas**: 31 generadores paramétricos sobre 15 temas producen variantes con
números distintos cada vez. Medido sobre 500 estudiantes simulados: **500 talleres únicos**, con un
promedio de solo **0,47 preguntas repetidas de cada 10** entre dos estudiantes cualesquiera.

Se presentan en **modo evaluación**: pantalla completa, sin copiar y pegar, sin clic derecho y sin
atajos del navegador. Si el estudiante sale de la pantalla o cambia de pestaña, el cronómetro se
detiene y queda registrado en la entrega. Cada taller se presenta una sola vez.

Tipos de ejercicio: opción múltiple, respuesta numérica con teclado de símbolos matemáticos,
escritura de conjuntos por extensión, construcción de diagramas de Venn y llenado de tablas de
contingencia.

## Para el docente

En *Talleres y entregas*: marca los temas, fija número de preguntas, tiempo y fecha de cierre, y
publica. Las entregas llegan en vivo con nota, tiempo e informe de integridad. Después decide qué
nota entra a la planilla oficial —la del taller físico, la de la aplicación, la mejor de las dos o el
promedio—. Incluye control de asistencia por sesión y gráfica de evolución del grupo.

## Puesta en marcha

La aplicación funciona tal cual, en modo local, sin configurar nada. Para que las notas de los
estudiantes lleguen al docente hay que conectar Firebase:

1. Entrar a [firebase.google.com](https://firebase.google.com) → **Crear un proyecto** (sin Analytics).
2. **Compilación → Firestore Database → Crear base de datos** → modo **producción** → región
   `southamerica-east1`.
3. ⚙ **Configuración del proyecto** → **Tus apps** → icono web `</>` → registrar → copiar el bloque
   `firebaseConfig`.
4. Pegar esos valores en [`config.js`](config.js).
5. En **Firestore → Reglas**, pegar el contenido de [`firestore.rules`](firestore.rules) y publicar.

### Sobre las reglas de seguridad

Un estudiante **solo puede crear su propia entrega, una sola vez**. El identificador del documento
debe ser exactamente `cédula__idTaller`, lo que impide suplantar a otro; y `update` y `delete` están
prohibidos, así que nadie puede repetir el taller ni mejorar su nota después.

## Archivos

```
index.html        la aplicación completa
config.js         configuración de Firebase (editar)
firestore.rules   reglas de seguridad de la base de datos
```

## Créditos y licencia

Contenido base: *Módulo Estadística Probabilística — Transversal*, 4.ª versión 2016, de
**Pablo Emilio Botero Tobón**, publicado por la Corporación Universitaria Remington bajo licencia
Creative Commons **Reconocimiento – No Comercial – Compartir Igual 2.5 Colombia**.

Este repositorio es material de estudio **sin fines comerciales** y conserva la atribución al autor
original. Los enunciados de los talleres pertenecen al docente de la asignatura.
