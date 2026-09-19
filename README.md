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
| 13 · Talleres y entregas | Panel del docente: talleres, entregas, accesos y actividad |

## Acceso

Al aula se entra con cuenta. El estudiante escribe **su cédula** como usuario; la primera vez, la
contraseña es también su cédula, y puede cambiarla él mismo desde la barra azul que le aparece
arriba. El docente y el administrador entran con su correo.

Crear las cuentas es trabajo de un botón: en *Talleres y entregas → Cuentas de los estudiantes*
aparece la lista de la planilla con **Crear acceso** al lado de cada nombre, y un **Crear los accesos
que faltan** para hacerlos todos de una vez. No hay que pasar por la consola de Firebase, y crear
cuentas no cierra la sesión del docente.

Si un estudiante olvida su contraseña: en la consola de Firebase, *Authentication → Users*, se borra
esa cuenta y se vuelve a pulsar *Crear acceso*. No se pierde nada de su progreso, porque el
seguimiento se guarda por cédula y no por cuenta.

## Seguimiento de la lectura

Mientras el estudiante estudia, la aplicación anota módulo a módulo cuántas veces entró, cuánto
tiempo estuvo con la página delante —solo cuenta el tiempo con la pestaña activa— y hasta dónde llegó
leyendo. Un módulo se da por **leído** cuando ha recorrido el 90 % de su contenido y le ha dedicado un
tiempo mínimo, que la propia aplicación calcula según lo que ocupa cada módulo (unas 180 palabras por
minuto). El docente puede subir o bajar esa exigencia, y lo ya registrado se vuelve a evaluar solo.

Los 18 problemas del banco piden ahora **la respuesta antes de enseñar la solución**. Se admite coma o
punto decimal, fracción (`27/62`) y porcentaje (`43,55 %`). La aplicación dice qué está bien y qué
mal, y registra el intento y el acierto.

El estudiante ve en la portada lo mismo que ve el docente: cuántos módulos lleva leídos, cuántos
ejercicios ha resuelto y cuánto tiempo ha estudiado.

### La nota de Seguimiento y asistencia

En *Talleres y entregas → Actividad en la app* hay una matriz de estudiantes por módulos, con lo que
cada uno abrió, terminó y resolvió, exportable a Excel. De ahí sale la evaluación 3 de la planilla:

```
Seguimiento y asistencia = 50 % asistencia presencial + 50 % actividad en la app
        actividad en la app = 60 % módulos leídos + 40 % ejercicios resueltos
```

Los cuatro porcentajes se editan, igual que la lista de módulos que se exigen. Quien no ha entrado
nunca cuenta 1,0 en la mitad de la app, y la aplicación avisa de cuántos están en ese caso.

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

Hay que conectar Firebase: es lo que sostiene el acceso de los estudiantes, el seguimiento y las
notas del grupo.

1. Entrar a [firebase.google.com](https://firebase.google.com) → **Crear un proyecto** (sin Analytics).
2. **Compilación → Firestore Database → Crear base de datos** → modo **producción** → región
   `southamerica-east1`.
3. ⚙ **Configuración del proyecto** → **Tus apps** → icono web `</>` → registrar → copiar el bloque
   `firebaseConfig`.
4. Pegar esos valores en [`config.js`](config.js).
5. En **Firestore → Reglas**, pegar el contenido de [`firestore.rules`](firestore.rules) y publicar.
6. En **Authentication → Sign-in method**, activar **Correo electrónico/contraseña** y crear ahí las
   dos cuentas del profesorado. Las de los estudiantes se crean luego desde la propia aplicación.

Los pasos 5 y 6 no son opcionales: sin ellos no entra nadie.

Sin conexión con el servidor, la aplicación deja entrar igual y sirve como material de estudio. Lo
que se lea y se resuelva queda guardado en ese equipo y se suma a la ficha del estudiante la primera
vez que entre con su cédula.

### Sobre las reglas de seguridad

La cuenta de cada estudiante es el correo interno `<cédula>@alumnos.estprob.local`, que no existe como
buzón: es solo la forma que tiene Firebase de identificarlo. Ese correo, firmado por Firebase, es lo
que comprueban las reglas, así que **nadie puede escribir el progreso ni la entrega de otro** aunque
lo intente directamente contra la API.

Tener cuenta tampoco basta: el estudiante necesita además su ficha en `/alumnos`, que solo escribe el
docente. Quien se registre por su cuenta se queda en la puerta.

Un estudiante **solo puede crear su propia entrega, una sola vez**. El identificador del documento
debe ser exactamente `cédula__idTaller` y la cédula tiene que ser la suya; `update` y `delete` están
prohibidos, así que nadie puede repetir el taller ni mejorar su nota después. Las notas y el progreso
del grupo solo los lee el docente.

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
