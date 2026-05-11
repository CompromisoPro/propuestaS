# Plataforma Sello PRO — Documento de levantamiento

**Propósito:** alinear al equipo que va a construir la plataforma sobre qué es Sello PRO y qué tiene que hacer la plataforma. Reemplaza versiones anteriores que hablaban de "MVP" o "cuestionario digital", porque ninguno de los dos términos describe lo que se está construyendo.

**Estado:** levantamiento de negocio. La especificación técnica, el modelo de datos y los plazos los aporta el equipo de implementación a partir de este documento.

---

## 0. Aclaración previa, importante

Esto no es un cuestionario. No es un formulario. No es una autoevaluación digitalizada. Es una **plataforma operativa** donde conviven cinco tipos de usuarios (equipo Sello PRO, gerencia, empresa socia, consultor administrativo y asesor) durante un ciclo de **dos años** por empresa, gestionando contratos, evidencias, evaluaciones, planes de trabajo, reuniones, facturación y reportes.

Pensar este proyecto como "un Excel en la web" deja afuera el verdadero objetivo. La plataforma reemplaza el rol del consultor como **dueño de la información** y le devuelve ese control al equipo Sello PRO de la CChC.

**Objetivo estratégico real:** dejar de depender de consultores externos para entender qué pasa con las empresas selladas y para generar análisis sobre el programa.

---

## 1. Qué es el Sello PRO (versión corta para alinear)

- Programa de acompañamiento de la CChC dentro del Compromiso PRO.
- Ciclo de **dos años**: año 1 acompañamiento e implementación, año 2 revalidación.
- **Siete pilares** de evaluación: Gobernanza, Trabajadores, Seguridad y Salud Laboral, Cadena de Valor, Comunidad, Medio Ambiente, Innovación y Productividad.
- **Cinco niveles de logro** por criterio (1 a 5 estrellas, 5 es el máximo).
- **Doce cuestionarios distintos** según la combinación rubro × tamaño de la empresa. Cada cuestionario tiene su propio set de criterios (cantidad y contenido varían entre cuestionarios). Por ejemplo, el cuestionario para "Constructora-Inmobiliaria Grande" tiene 48 criterios; otros tipos de empresa pueden tener más o menos.
- Dentro de cada cuestionario hay un **subconjunto de criterios obligatorios** con nota mínima para alcanzar determinado nivel del sello. Cuáles son obligatorios depende de cada cuestionario.
- Más de 350 empresas a nivel nacional, distribuidas por sedes regionales con metas propias.

> **Nota sobre auditorías y ciclo de 3 años:** documentos anteriores hablan de tres años y de auditorías externas anuales. **Eso no aplica hoy.** Hoy es ciclo de 2 años sin auditoría externa. Se deja marcado como *posible implementación futura*, no como requisito.

---

## 2. Actores del sistema

| Actor | Rol resumido | Vista que necesita |
|---|---|---|
| **Jefa de equipo Sello PRO** | Dirige el programa, ve metas y procesos | Métricas, embudo de procesos, drill-down al detalle |
| **Encargado de convenios/alianzas** | Gestiona partnerships y empresas aliadas | Vista tipo CRM relacional |
| **Encargado comercial / seguimiento** | Procesos nuevos, revalidaciones, facturación | Pipeline + estado financiero |
| **Gerencia CChC** | Sponsor del programa | Dashboard en vivo, metas regionales |
| **Consultor administrativo** | Llamadas, contratos, agenda, soporte mail | Agenda + bandeja + contratos |
| **Asesor Sello PRO** | Núcleo operativo: evalúa, va a terreno, define plan, cierra proceso | Vista por empresa con todo el expediente |
| **Empresa socia** | El socio acompañado | Portal completo de su proceso |

---

## 3. Los 12 cuestionarios (concepto clave que el equipo externo debe internalizar)

Este es uno de los puntos que más se ha malentendido. Vale la pena dedicarle una sección.

- Existen **12 cuestionarios distintos**, uno por cada combinación rubro × tamaño de empresa.
- Cada cuestionario tiene **su propio listado de criterios**. La cantidad y el contenido cambian entre cuestionarios.
- Cada cuestionario tiene **su propio subconjunto de criterios obligatorios** con nota mínima para alcanzar cierto nivel del sello.
- El sistema, al ingresar una empresa, debe **asignar automáticamente el cuestionario correspondiente** según rubro × tamaño.
- El asesor debe poder **corregir la asignación** si el sistema se equivocó (por ejemplo, una empresa que cambió de tamaño o que opera entre dos rubros).
- Los cuestionarios son **maestros versionables**: cuando el equipo Sello PRO actualiza un criterio o cambia una rúbrica, ese cambio debe quedar trazado. **Las empresas que ya iniciaron proceso con una versión anterior mantienen su versión**, no se les cambia las reglas a mitad de camino.

Por qué importa: modelar esto como "un solo cuestionario configurable" no funciona en este caso. Son 12 instrumentos distintos que comparten el lenguaje de pilares y estrellas, pero tienen contenido propio. La plataforma necesita gestionar los 12 como entidades separadas.

---

## 4. Las vistas de la plataforma

Cada vista que viene a continuación es **un conjunto de pantallas y funcionalidades para un tipo de usuario**. No son módulos técnicos. Es cómo el negocio piensa la plataforma.

---

### 4.1 Vista equipo Sello PRO

Hoy son tres personas con roles distintos. Cada una necesita ver algo diferente al entrar.

**4.1.1 Jefa del equipo**

Lo primero que ve al entrar:

- KPIs del programa: cuántos sellos activos, cuántos en proceso, cuántos cerrados en el año, % de cumplimiento de meta anual.
- Distribución de procesos por etapa (embudo): empresas en autoevaluación, en visita a terreno, en plan de trabajo, en evaluación final, selladas, en revalidación.
- Tipos de procesos abiertos por rubro y tamaño.
- Capacidad de hacer *drill-down* desde cualquier número hasta la lista de empresas que lo componen.

**4.1.2 Encargado de convenios y alianzas**

Vista tipo CRM relacional. Necesita:

- Listado de empresas socias + listado de aliados/partners.
- Estado de convenios activos, vencimientos próximos, renovaciones.
- Historial de contactos por entidad.
- Notas y próximas acciones.

**4.1.3 Encargado comercial y de seguimiento**

Vista de pipeline + facturación:

- Empresas nuevas en ingreso.
- Empresas en proceso de revalidación.
- Estado del sello por empresa (vigente, por vencer, vencido).
- **Procesos pendientes de facturación** — aquí hay una pestaña dedicada con: monto, etapa de cobro, factura emitida sí/no, pagada sí/no, días vencidos.
- Proyección de ingresos según pipeline.

---

### 4.2 Vista empresa socia (la más compleja)

Aquí es donde es más fácil perder el foco: pensar que es una autoevaluación y termina. **No.** La empresa debe **vivir dentro de la plataforma** durante dos años. Esa es la vara.

**4.2.1 Onboarding y datos de la empresa**

Antes de cualquier evaluación, la empresa completa su ficha:

- Datos legales y de identificación.
- Estructura organizacional básica.
- Personas responsables del proceso (quién responde qué).
- Contexto operativo (rubro confirmado, tamaño, regiones donde opera).

Esta ficha es la fuente de verdad para que el sistema asigne el **cuestionario correspondiente** según la combinación rubro × tamaño.

**4.2.2 Autoevaluación inicial**

- Pantalla por criterio (no toda la evaluación en un scroll infinito, considerando que cada cuestionario puede tener decenas de criterios).
- Cada criterio muestra:
  - Nombre y pilar al que pertenece.
  - Descripción clara del criterio.
  - **Ejemplos simples** de qué significa cada nivel del 1 al 5, para que la empresa no se pierda.
  - Selector de nota (1 a 5 estrellas).
  - **Espacio para subir evidencias por criterio**: PDFs, fotos, planillas, links. Optimizado para múltiples archivos.
  - Campo de comentario libre.
- Progreso visible: cuántos criterios completados, cuántos quedan, por pilar.
- Posibilidad de guardar como borrador y retomar.

**4.2.3 Espera de revisión y visita a terreno**

Una vez enviada la autoevaluación, la empresa pasa a un estado de espera. En este momento:

- Ve el estado de su proceso ("autoevaluación enviada, en revisión por asesor").
- Puede subir evidencia adicional si el asesor se la solicita.
- Ve la fecha programada de visita a terreno cuando el asesor la fije.

**4.2.4 Plan de trabajo y vista de seguimiento (el corazón de los dos años)**

Después del diagnóstico, la empresa tiene una **vista de seguimiento permanente** durante los dos años:

- Resumen por pilar: nota autoevaluación, nota terreno, nota diagnóstico, **meta acordada** por criterio.
- Indicador visual de qué criterios ya alcanzan la meta y cuáles están en rojo.
- Por criterio, al hacer clic:
  - Qué significa llegar a cada estrella (rúbrica detallada).
  - **Verificadores** que se exigen para cada nivel.
  - **Ejemplos** de empresas que ya lo lograron (anonimizado si corresponde).
  - **Herramientas y guías sugeridas** para avanzar.
  - Espacio para que la empresa suba sus avances.
  - Historial de evidencias y comentarios cruzados con el asesor.
- Criterios obligatorios marcados (los que tienen nota mínima para alcanzar nivel).

**4.2.5 Módulo administrativo de la empresa**

- Su contrato.
- Meses transcurridos del proceso y meses restantes.
- Facturas y estado de pago.
- Documentos formales (carta de interés, anexos, etc.).
- Datos de contacto del consultor administrativo y del asesor asignados.

**4.2.6 Canal de comunicación**

- Solicitudes generales al equipo Sello PRO (tipo ticket).
- *(Por evaluar)* Consultas por criterio dirigidas al asesor. Tener cuidado: si se abre por criterio, el asesor puede saturarse. Posible solución: agrupar consultas semanalmente o tener una sesión de dudas mensual.
- Notificaciones / muro de novedades del programa (la plataforma como canal de comunicación con socios, no solo como herramienta).

---

### 4.3 Vista consultor administrativo

Persona que no evalúa, pero sostiene la operación.

- Agenda de llamadas y seguimientos por empresa.
- Bandeja de mails del Sello PRO con asignación.
- **Generación de contrato**: arma el borrador, lo envía al área legal de CChC para oficializar, registra estado (borrador → enviado a legal → firmado → vigente).
- Coordinación de reuniones entre empresa y asesor (calendario integrado).
- Vista por empresa de todo lo administrativo: estado de contrato, próximos hitos, próximas reuniones, últimas comunicaciones.

---

### 4.4 Vista asesor Sello PRO (núcleo operativo)

Esta es la vista más densa porque el asesor toca todo el proceso. La plantilla actual en Excel (referencia) tiene cinco hojas: Info Empresa, Notas Criterios, Resumen Pilares, Terrenos, Plan Desarrollo. **Eso es lo mínimo que la plataforma debe replicar y superar.**

**4.4.1 Listado de empresas asignadas**

- Lista de empresas a cargo, con estado, próxima acción, días desde última actividad, alertas.

**4.4.2 Ficha de empresa (corazón de su trabajo)**

Por cada empresa el asesor accede a:

- **Datos de la empresa** y del proceso (fechas clave, evaluador, estado).
- **Notas por criterio** con cuatro columnas: autoevaluación, terreno, diagnóstico corregido, nota final. Más columnas de mejora y observaciones.
- **Resumen por pilar** con ponderaciones y promedio calculado automáticamente, y la **nota Sello PRO final**.
- **Registro de visitas a terreno**: fecha, tipo, proyecto/obra, ubicación, criterios evaluados, hallazgos, notas ajustadas, evidencia recopilada, responsable.
- **Plan de desarrollo**: por criterio — nota actual, meta, acción de mejora, herramienta sugerida, responsable de parte de la empresa, fecha límite, % avance, estado.

**4.4.3 Capacidades especiales del asesor**

Esto va más allá de la plantilla actual:

- **Aplicabilidad de criterios**: poder marcar un criterio como "no aplica" a esta empresa, **con justificación obligatoria escrita**. Toda exclusión queda trazada.
- **Modificación de fechas**: cambiar fecha de entrega final o de hitos intermedios, con justificación.
- **Adjuntar antecedentes propios**: el asesor también sube documentos al expediente.
- **Notas de reunión**: cada reunión queda registrada con fecha, asistentes, temas tratados, acuerdos, próximos pasos.
- **Cierre de proceso**: poner notas finales, generar el informe de cierre, marcar la empresa como sellada.
- **Feedback estructurado** a la empresa por criterio (no solo verbal).
- **Vista de pares**: el asesor puede ver — solo lectura — qué hicieron otros asesores en empresas similares, para alinear criterios.

---

### 4.5 Vista gerencia CChC

Dashboard ejecutivo en vivo:

- Cuántas empresas selladas (acumulado y del año).
- Cuántas en proceso, segmentadas por etapa.
- % y cantidad de cumplimiento de meta nacional.
- **Mapa de Chile con desglose por sede regional**:
  - Meta de cada sede.
  - Cumplimiento actual.
  - Ranking de sedes.
- **Proyección de cierres**: lógica que estima qué empresas terminarán el proceso en los próximos N meses según la etapa actual y los plazos típicos. Por ejemplo: si una empresa está en plan de trabajo hace 7 meses y al ciclo le quedan 5 meses, se proyecta como cierre probable en ese rango.
- Distribución por rubro y tamaño.
- Tendencia mensual de nuevas inscripciones y cierres.

---

### 4.6 Panel de administración (ingreso de socio nuevo)

Cuadro de mando exclusivo del equipo Sello PRO para dar de alta una empresa. **Tiene que ser sólido y ágil**, porque es la puerta de entrada al sistema.

Funcionalidades:

- Crear empresa: RUT, razón social, nombre fantasía, rubro, tamaño, sede regional.
- Asignar consultor administrativo y asesor.
- Crear los usuarios de la empresa (login para las personas responsables del lado del socio).
- Subir documentos del expediente inicial: **contrato, carta de interés, antecedentes, cualquier archivo con nombre libre**, todos quedan archivados en el panel de la empresa indexados por su ID.
- Definir fechas clave del proceso.
- Generar el cuestionario correspondiente automáticamente según rubro × tamaño.

---

## 5. Estados del expediente de la empresa

Los estados que la plataforma debe gestionar (mínimo):

1. **Ingreso** — datos cargados, sin contrato firmado.
2. **Contrato vigente** — proceso iniciado.
3. **Autoevaluación en curso**.
4. **Autoevaluación enviada / pendiente de revisión**.
5. **Visita a terreno programada / realizada**.
6. **Diagnóstico en elaboración**.
7. **Plan de trabajo definido**.
8. **En seguimiento** (la fase larga de los dos años).
9. **Evaluación final en curso**.
10. **Sellada** — acompañamiento completado, Sello PRO entregado.
11. **En revalidación** (año 2).
12. **Cerrada / no renovada** — caso de salida del programa.

Cada estado dispara permisos, vistas y alertas distintas.

---

## 6. Funcionalidades transversales

- **Sistema de notificaciones y recordatorios automáticos**: cada cierto tiempo, recordatorios al socio sobre sus criterios pendientes del plan de trabajo. Mantenerlos "vivos" dentro de la plataforma.
- **Muro de noticias / comunicaciones del programa**: el equipo Sello PRO publica novedades, casos, herramientas. Visible para todas las empresas.
- **Buscador global** en el lado interno.
- **Trazabilidad de cambios**: quién cambió qué nota, qué fecha, qué criterio. Auditable.
- **Exportaciones** a Excel/PDF de cualquier vista, porque el negocio aún va a querer compartir resúmenes externos.
- **Roles y permisos granulares**: matriz rol × pantalla × acción.
- **Almacenamiento de archivos**: por empresa, indexado, con tipos de documento clasificados.

---

## 7. Lo que está fuera del alcance actual (posible implementación futura)

Para evitar que el equipo externo mezcle scope:

- Auditorías externas anuales (hoy no aplican, ciclo es de 2 años).
- Tercer año del ciclo y renovaciones más allá de la primera revalidación.
- Integraciones con sistemas externos de CChC más allá del expediente local.
- Explotación analítica avanzada (BI sobre el dataset histórico una vez consolidado).
- Funcionalidades para verificadores externos / auditores como rol propio.

Estas cosas vienen, pero **no ahora**. Marcarlas como "futuro" evita que el equipo externo las use como excusa para hinchar el alcance o atrasarse.

---

## 8. Riesgos del proyecto (a nombrar en voz alta con el equipo externo)

1. **Subestimación de la complejidad**: si al avanzar el levantamiento la plataforma sigue descrita como "una autoevaluación", conviene revisar la comprensión del dominio antes que la parte técnica.
2. **Mezcla de scope**: confundir lo que está en este documento con el ciclo completo de 3 años + auditorías que aparece en documentos antiguos.
3. **Subestimación de migración**: hay muchas planillas heterogéneas hoy. La estructura objetivo está, pero el trabajo de migración manual no es trivial.
4. **Subestimación de permisos**: hay cinco roles internos + la empresa, cada uno con vistas distintas y acciones distintas. La matriz de permisos no es opcional.
5. **Diseño tipo "formulario gigante"**: si la autoevaluación termina siendo un scroll con todos los criterios del cuestionario en una sola página, fracasa. Tiene que ser una experiencia por criterio, con contexto, evidencia y ayuda.
6. **No considerar la fase de seguimiento de 2 años**: la mayor parte del valor está en mantener a la empresa activa durante el ciclo, no solo en evaluarla al inicio.

---

## 9. Cómo medir si la plataforma cumple

Tres preguntas simples para validar cualquier propuesta que llegue del equipo externo:

1. **¿La empresa puede vivir 2 años aquí adentro sin volver a abrir un mail o un Excel del consultor?** Si la respuesta es no, falta funcionalidad.
2. **¿El equipo Sello PRO puede contestar "cuántas empresas selladas tenemos en Antofagasta este año" sin pedírselo a un consultor?** Si la respuesta es no, no se cumplió el objetivo estratégico.
3. **¿Un asesor nuevo que entra mañana puede tomar una empresa y ver todo su historial sin preguntar a nadie?** Si la respuesta es no, falta consolidación de información.

---

## 10. Cierre

Este documento es el levantamiento de negocio del lado interno, hecho para enfocar y acelerar el trabajo de descubrimiento conjunto. No es la especificación técnica. Esa la entrega el equipo de implementación a partir de aquí, con: arquitectura propuesta, modelo de datos, plan por fases, estimación y propuesta de validación con usuarios reales.

Lo que sí se exige: que el plan por fases respete que **la plataforma es una sola** aunque se construya por partes, y que no se entregue un "pedazo de autoevaluación" como si fuese el producto.

---

*Documento de levantamiento — Sello PRO — versión 1.0*
