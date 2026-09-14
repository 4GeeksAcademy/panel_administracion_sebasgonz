# SPECS.md — Panel de Administración AgentHub

## 1. Propósito del Documento

Este documento define la especificación funcional, estructural y visual del panel de administración de AgentHub, una startup orientada a la gestión, contratación, monitoreo y operación de agentes inteligentes reutilizables.

La especificación está diseñada para guiar la construcción frontend del panel administrativo sin definir todavía implementación, marcado HTML, lógica de programación ni integraciones backend. Su alcance se limita a arquitectura de interfaz, comportamiento esperado, composición de secciones, estados de interacción y criterios de aceptación visuales y funcionales.

## 2. Objetivo del Producto

AgentHub requiere un panel administrativo que permita a operadores internos visualizar el estado comercial, operativo y técnico de la plataforma desde una interfaz centralizada. El producto debe facilitar la supervisión de clientes, usuarios, agentes, skills, contrataciones y errores de ejecución.

El panel debe priorizar claridad operativa, densidad informativa moderada, navegación persistente y acciones contextuales consistentes. La experiencia debe sentirse profesional, precisa y orientada a administración SaaS.

### 2.1 Descripción del Producto y Usuario Administrador

AgentHub es una plataforma SaaS para registrar, configurar, publicar, contratar y supervisar agentes inteligentes y las skills que amplían sus capacidades. El panel de administración es la superficie operativa desde la que se controlan usuarios, agentes, catálogo de skills, contratos y fallos de ejecución.

El usuario administrador es un operador interno de AgentHub con permisos para consultar el estado global del negocio y de la plataforma, inspeccionar registros detallados y ejecutar acciones administrativas sobre las entidades visibles. No es el cliente final que alquila un agente ni el usuario que consume directamente sus respuestas.

### 2.2 Stack Tecnológico y Restricciones

El prototipo debe respetar el siguiente stack y sus límites:

- HTML semántico como estructura de la interfaz.
- Tailwind CSS cargado mediante CDN y utilizado también con sus utilidades `dark:` para el tema oscuro.
- JavaScript vanilla para navegación, estado local, dropdowns, modales, expansión de skills y cambio de tema.
- Sin React, Vue, Angular, Svelte ni cualquier otro framework de frontend.
- Sin backend, API, base de datos, autenticación real ni persistencia remota.
- Datos hardcodeados o definidos localmente únicamente para demostrar la interfaz y sus interacciones.
- Sin dependencia de un proceso de compilación para ejecutar el prototipo en el navegador.

## 3. Principios de Arquitectura Frontend

### 3.1 Estructura General

La aplicación debe organizarse como una interfaz administrativa de una sola superficie principal, compuesta por:

- Navegación lateral persistente.
- Barra superior persistente.
- Área de contenido dinámica por sección.
- Sistema uniforme de tarjetas, tablas, badges, dropdowns y modales.
- Compatibilidad visual completa con modo claro y modo oscuro.

### 3.2 Navegación Principal

La navegación lateral debe exponer exactamente las seis secciones principales del panel:

1. Dashboard.
2. Gestión de usuarios.
3. Gestión de agentes.
4. Skills.
5. Contrataciones de agentes.
6. Log de errores.

La navegación debe permanecer visible durante la interacción normal en escritorio. En pantallas pequeñas, debe adaptarse a un patrón compacto sin perder acceso a ninguna sección.

Cada elemento de navegación debe indicar su estado activo mediante tratamiento visual diferenciado, como contraste de fondo, borde lateral, peso tipográfico o color de acento.

### 3.3 Barra Superior

La barra superior debe contener, como mínimo:

- Identificación contextual de la sección activa.
- Toggle global de modo claro y modo oscuro.
- Área opcional para acciones futuras, perfil administrativo o estado del sistema.

El toggle de tema debe cambiar toda la interfaz entre modo claro y modo oscuro. La implementación futura debe basarse en las utilidades `dark:` de Tailwind para mantener consistencia visual a nivel de componentes.

### 3.4 Sistema de Interacción

Los patrones interactivos deben mantenerse consistentes en todas las secciones:

- Dropdown contextual para acciones por fila o por entidad.
- Modal overlay para visualización de detalles complejos.
- Backdrop clicable para cerrar modales.
- Botón explícito de cierre dentro de cada modal.
- Badges para representar estado, gravedad o categoría.
- Transiciones suaves para expansiones, colapsos y aparición de overlays.

## 4. Requisitos Globales de Interfaz

### 4.1 Modo Claro y Modo Oscuro

La interfaz debe soportar dos temas visuales completos:

- Modo claro: fondo principal claro, superficies blancas o neutras, texto de alto contraste y acentos controlados.
- Modo oscuro: fondo principal oscuro, superficies elevadas con contraste suficiente, texto legible y acentos equivalentes al modo claro.

El cambio de tema debe afectar:

- Layout principal.
- Navegación lateral.
- Barra superior.
- Tarjetas de métricas.
- Tablas.
- Dropdowns.
- Modales.
- Backdrops.
- Badges.
- Controles expandibles.
- Áreas de marcador de posición.

### 4.2 Accesibilidad Operativa

La interfaz debe cumplir criterios mínimos de accesibilidad funcional:

- Contraste suficiente entre texto y fondo.
- Estados visibles para hover, foco, activo y deshabilitado.
- Tamaños de objetivo adecuados para botones, toggles y menús.
- Cierre de modales mediante botón explícito y backdrop.
- Jerarquía visual clara entre títulos, subtítulos, métricas y contenido tabular.

### 4.3 Responsividad

El panel debe adaptarse a escritorio, tablet y móvil. La prioridad de diseño debe estar en escritorio administrativo, pero ninguna sección debe quedar inutilizable en pantallas pequeñas.

En pantallas reducidas:

- Las tablas pueden transformarse en listas estructuradas o permitir desplazamiento horizontal controlado.
- La navegación lateral puede contraerse.
- Los modales deben ajustarse al ancho disponible.
- Las tarjetas de métricas deben apilarse sin perder legibilidad.

## 5. Sección 1 — Dashboard

### 5.1 Propósito

El Dashboard debe ofrecer una lectura ejecutiva inmediata del estado comercial y operativo de AgentHub durante el mes actual.

### 5.2 Componentes Requeridos

La sección debe incluir cuatro tarjetas de métrica visibles en la parte superior:

1. Ingresos totales generados este mes.
2. Pérdida total atribuida a descuentos y cupones.
3. Número total de agentes activos en todos los clientes.
4. Número total de agentes actualmente marcados como fallando.

Cada tarjeta debe contener:

- Etiqueta de métrica.
- Valor principal destacado.
- Indicador visual asociado a la naturaleza de la métrica.
- Tratamiento visual consistente con el sistema de tema claro y oscuro.

### 5.3 Área de Actividad Semanal

Debajo de las tarjetas debe existir un área de marcador de posición para un gráfico de actividad semanal.

El marcador debe comunicar estructuralmente que el espacio está reservado para visualización analítica futura, sin requerir todavía datos reales ni implementación de librería de gráficos.

### Especificaciones Concretas del Dashboard

1. **Cuadrícula de métricas:** cuatro tarjetas en una cuadrícula responsive de $2 \times 2$ en escritorio y una sola columna en móvil; cada tarjeta contiene un icono, una etiqueta y un valor hardcodeado para ingresos del mes, descuentos, agentes activos y agentes fallando.
2. **Jerarquía cromática:** las tarjetas usan acentos diferenciados por tipo de métrica, una sombra sutil y un estado visual de alerta para agentes fallando, manteniendo equivalencia de contraste en modo claro y oscuro.
3. **Marcador de actividad:** debajo de las tarjetas existe un bloque de ancho completo con borde discontinuo, altura estable y etiqueta centrada que representa el gráfico de actividad semanal pendiente de implementación.

### 5.4 Criterios de Aceptación

- Las cuatro métricas deben estar visibles al ingresar al Dashboard en escritorio.
- La métrica de agentes fallando debe tener una jerarquía visual que facilite detectar riesgo operativo.
- El área de actividad semanal debe ubicarse debajo de las métricas y ocupar un bloque claramente diferenciado.
- El diseño debe conservar legibilidad en modo claro y oscuro.

## 6. Sección 2 — Gestión de Usuarios

### 6.1 Propósito

La sección de Gestión de usuarios debe permitir al administrador consultar usuarios registrados y ejecutar acciones individuales sobre cada registro.

### 6.2 Tabla de Usuarios

Debe presentarse una tabla con las siguientes columnas mínimas:

- Nombre.
- Email.
- Plan.
- Estado.
- Acciones.

El estado debe representarse con un badge o indicador visual. Los estados esperados pueden incluir activo, inactivo, suspendido o pendiente, según el modelo de datos futuro.

### 6.3 Dropdown de Acciones

Cada fila debe incluir un dropdown de acciones activado por un botón compacto representado visualmente como `⋮`.

El menú debe contener al menos:

- Ver detalle.
- Eliminar.

El dropdown debe aparecer junto al botón activador, cerrarse al seleccionar una opción y no debe bloquear la lectura del resto de la tabla.

### 6.4 Modal de Detalle de Usuario

Al seleccionar Ver detalle, debe abrirse un modal overlay con el registro completo del usuario.

El modal debe incluir:

- Nombre completo.
- Email.
- Plan contratado.
- Estado actual.
- Fecha de registro, si está disponible.
- Información administrativa adicional disponible en el modelo de datos.

El modal debe cerrarse mediante:

- Botón explícito de cierre.
- Clic sobre el backdrop.

### Especificaciones Concretas de Gestión de Usuarios

1. **Tabla de usuarios:** una tabla responsive muestra nombre, email, plan y estado; el estado se representa con un badge semántico y cada fila conserva una columna de acciones alineada a la derecha.
2. **Menú contextual:** el botón `⋮` abre un dropdown anclado a la fila con las opciones Ver detalle y Eliminar; solo un dropdown puede permanecer abierto y el menú se cierra al hacer clic fuera.
3. **Detalle en overlay:** Ver detalle abre un modal con nombre, email, plan, estado y fecha de registro; el modal incluye botón de cierre, backdrop clicable y desplazamiento interno para contenido extenso.

### 6.5 Criterios de Aceptación

- Todos los usuarios deben visualizarse en una estructura tabular clara.
- Cada fila debe tener un único punto de entrada para acciones contextuales.
- El modal debe mostrar más información que la tabla resumida.
- El cierre por botón y backdrop debe estar disponible.

## 7. Sección 3 — Gestión de Agentes

### 7.1 Propósito

La sección de Gestión de agentes debe permitir consultar agentes registrados, su propietario, su estado operativo y las skills asociadas a cada uno.

### 7.2 Listado de Agentes

Cada agente debe mostrar:

- Nombre del agente.
- Propietario.
- Estado actual.
- Lista de skills asociadas.
- Acciones contextuales.

Los estados requeridos son:

- Activo.
- Inactivo.
- Fallando.

Cada estado debe representarse visualmente mediante badge o indicador de color semántico.

### 7.3 Skills Colapsadas

La lista de skills de cada agente debe estar oculta por defecto.

Cada agente debe incluir un control expandible que permita revelar u ocultar sus skills. La transición entre estado colapsado y expandido debe ser suave y no debe provocar saltos visuales bruscos.

Cuando las skills estén visibles, deben mostrarse como una lista legible de capacidades asociadas al agente.

### 7.4 Dropdown de Acciones

Cada agente debe incluir un dropdown de acciones con al menos:

- Configurar.
- Eliminar.

### 7.5 Modal de Configuración de Agente

Al seleccionar Configurar, debe abrirse un modal con el prompt de sistema del agente.

El modal debe presentar:

- Nombre del agente.
- Propietario.
- Estado actual.
- Prompt de sistema completo o área destinada a mostrarlo.
- Acciones futuras de configuración, si el alcance del producto las incorpora después.

### Especificaciones Concretas de Gestión de Agentes

1. **Listado de agentes:** cada registro muestra nombre, propietario, badge de estado y un control expandible de skills dentro de una fila o tarjeta de altura estable.
2. **Skills colapsables:** las skills permanecen ocultas por defecto; activar el control de un agente revela únicamente sus skills en una lista vertical con transición suave y actualiza el indicador visual de expandido.
3. **Configuración contextual:** el dropdown de cada agente contiene Configurar y Eliminar; Configurar abre un modal que muestra nombre, propietario, estado y prompt de sistema completo sin abandonar la vista.

### 7.6 Criterios de Aceptación

- Las skills deben permanecer ocultas inicialmente.
- El control expandible debe revelar las skills del agente seleccionado sin afectar innecesariamente otros registros.
- Los estados activo, inactivo y fallando deben distinguirse visualmente.
- El modal de configuración debe mostrar claramente el prompt de sistema.

## 8. Sección 4 — Skills

### 8.1 Propósito

La sección Skills debe funcionar como catálogo administrativo de capacidades disponibles para los agentes de AgentHub.

En el contexto de AgentHub, una skill es una capacidad funcional adjuntable a un agente para ampliar su comportamiento operativo. Puede representar una integración, una herramienta, una competencia de análisis, una acción automatizada o una habilidad especializada que el agente puede utilizar durante su ejecución.

### 8.2 Catálogo de Skills

Cada skill debe mostrar:

- Nombre.
- Descripción breve.
- Número de agentes que la tienen habilitada actualmente.
- Acciones contextuales.

La sección debe incluir una explicación breve dentro del panel sobre el significado de una skill en AgentHub. Esta explicación debe estar ubicada cerca del encabezado de la sección y debe ayudar al administrador a interpretar el catálogo sin interrumpir el flujo operativo.

### Especificaciones Concretas de Skills

1. **Catálogo de skills:** cada skill aparece en una tarjeta o fila con nombre destacado, descripción breve y contador visible de agentes que la tienen habilitada.
2. **Panel explicativo:** junto al encabezado existe un bloque informativo que define una skill como capacidad funcional adjuntable a un agente, separado visualmente del listado para no confundirse con un registro.
3. **Acciones de skill:** el dropdown de cada skill contiene Ver detalle y Eliminar; Ver detalle abre un modal con descripción completa, agentes asociados, categoría y disponibilidad.

### 8.3 Dropdown de Acciones

Cada skill debe tener un dropdown de acciones con:

- Ver detalle.
- Eliminar.

### 8.4 Modal de Detalle de Skill

Al seleccionar Ver detalle, debe abrirse un modal con información ampliada de la skill.

El modal puede incluir:

- Nombre.
- Descripción completa.
- Cantidad de agentes asociados.
- Posible categoría funcional.
- Estado de disponibilidad, si aplica.

### 8.5 Criterios de Aceptación

- El catálogo debe ser escaneable y fácil de comparar.
- Cada skill debe comunicar utilidad y nivel de adopción.
- La explicación conceptual de skill debe estar presente dentro de la sección.
- Las acciones Ver detalle y Eliminar deben estar disponibles por skill.

## 9. Sección 5 — Contrataciones de Agentes

### 9.1 Propósito

La sección Contrataciones de agentes debe permitir consultar contratos de alquiler activos y pasados entre clientes y agentes disponibles en AgentHub.

### 9.2 Tabla de Contratos

Debe presentarse una tabla con las siguientes columnas mínimas:

- Cliente.
- Agente alquilado.
- Skills contratadas.
- Fechas del contrato.
- Importe total pagado.
- Acciones.

Las fechas del contrato deben permitir entender el intervalo de contratación, incluyendo inicio y fin cuando corresponda.

Las skills contratadas deben mostrarse en formato resumido dentro de la tabla para evitar saturación visual.

### Especificaciones Concretas de Contrataciones

1. **Tabla contractual:** cada fila muestra cliente, agente alquilado, skills resumidas, fechas de inicio y fin, importe total pagado y un control de acciones alineado.
2. **Estado temporal:** los contratos activos y pasados se distinguen mediante badge de estado y el rango de fechas se mantiene legible sin ocultar el importe total.
3. **Desglose financiero:** Ver detalle abre un modal con cliente, agente, fechas, estado, total pagado y una lista de skills contratadas donde cada skill tiene su precio individual y el total queda visualmente separado.

### 9.3 Dropdown de Acciones

Cada fila debe incluir un dropdown de acciones. Como mínimo debe incluir:

- Ver detalle.

Pueden incorporarse acciones futuras como renovar, cancelar, descargar recibo o auditar contrato, fuera del alcance obligatorio inicial.

### 9.4 Modal de Detalle de Contrato

Al seleccionar Ver detalle, debe abrirse un modal con el desglose completo del contrato.

El modal debe incluir:

- Cliente.
- Agente alquilado.
- Estado del contrato.
- Fecha de inicio.
- Fecha de finalización.
- Importe total pagado.
- Lista desglosada de skills contratadas.
- Precio individual de cada skill.
- Total calculado o resumen financiero del contrato.

### 9.5 Criterios de Aceptación

- La tabla debe mostrar contratos activos y pasados.
- El importe total pagado debe ser visible en cada fila.
- El modal debe incluir precios individuales por skill.
- El desglose del contrato debe permitir auditar la composición del importe total.

## 10. Sección 6 — Log de Errores

### 10.1 Propósito

El Log de errores debe permitir supervisar fallos de ejecución de agentes y actuar sobre incidentes operativos.

### 10.2 Registro de Errores

Cada entrada del log debe mostrar:

- Timestamp.
- Nombre del agente.
- Tipo de error.
- Descripción breve.
- Gravedad o categoría visual.
- Acciones contextuales.

### 10.3 Badges de Error

Los errores deben categorizarse visualmente por tipo o gravedad mediante badges con código de color.

Categorías recomendadas:

- Informativo.
- Advertencia.
- Error.
- Crítico.

También pueden existir tipos funcionales, como error de integración, timeout, fallo de autenticación, error de prompt, error de skill o excepción no controlada.

### Especificaciones Concretas del Log de Errores

1. **Registro de errores:** una tabla o lista densa muestra timestamp, agente, tipo, descripción breve y badge de gravedad, con orden visual que facilite localizar el incidente más reciente.
2. **Codificación semántica:** los badges diferencian Informativo, Advertencia, Error y Crítico mediante colores consistentes, texto legible y una señal adicional que no depende exclusivamente del color.
3. **Resolución y traza:** el dropdown contiene Ver detalle y Marcar como resuelto; Ver detalle abre un modal con la traza completa y Marcar como resuelto cambia de forma visible el estado del registro.

### 10.4 Dropdown de Acciones

Cada entrada debe incluir un dropdown de acciones con:

- Ver detalle.
- Marcar como resuelto.

### 10.5 Modal de Detalle de Error

Al seleccionar Ver detalle, debe abrirse un modal con la traza completa del error.

El modal debe incluir:

- Timestamp completo.
- Agente afectado.
- Tipo de error.
- Gravedad.
- Descripción breve.
- Traza completa del error.
- Estado de resolución.
- Información contextual disponible, como skill involucrada, cliente afectado o contrato relacionado.

### 10.6 Criterios de Aceptación

- Cada error debe ser legible como evento individual.
- La gravedad debe poder identificarse sin abrir el detalle.
- La acción Ver detalle debe mostrar la traza completa.
- La acción Marcar como resuelto debe estar disponible para cada entrada.

## 11. Modelo Visual de Estados

### 11.1 Estados de Usuario

Estados mínimos previstos:

- Activo.
- Inactivo.
- Suspendido.
- Pendiente.

### 11.2 Estados de Agente

Estados obligatorios:

- Activo.
- Inactivo.
- Fallando.

### 11.3 Estados de Contrato

Estados recomendados:

- Activo.
- Finalizado.
- Cancelado.
- Pendiente.

### 11.4 Estados de Error

Estados recomendados:

- Abierto.
- En revisión.
- Resuelto.

Gravedades recomendadas:

- Informativo.
- Advertencia.
- Error.
- Crítico.

## 12. Requisitos de Componentes Reutilizables

El panel debe construirse conceptualmente sobre un conjunto de componentes reutilizables. Cada componente debe conservar la misma estructura visual y comportamiento cuando se utilice en más de una sección.

- **Sidebar:** navegación lateral persistente con las seis rutas, indicador de sección activa y variante compacta para pantallas pequeñas.
- **Barra superior:** título contextual de la vista y controles globales, incluido el toggle de modo oscuro.
- **Tarjeta de métrica:** icono, etiqueta, valor, acento semántico y sombra sutil para las métricas del Dashboard.
- **Tabla de datos:** encabezados, filas, columna de acciones, estados vacíos y desplazamiento horizontal controlado en pantallas reducidas.
- **Badge:** etiqueta compacta para estados de usuarios, agentes, contratos y gravedad de errores.
- **Dropdown de acciones:** botón contextual, menú de opciones, cierre al seleccionar y cierre al hacer clic fuera.
- **Modal:** overlay de detalle o configuración con título, contenido desplazable, acción de cierre y cierre mediante backdrop.
- **Backdrop:** capa de separación visual que bloquea la interacción con el contenido de fondo mientras un modal está abierto.
- **Lista de skills colapsable:** control de expansión, lista de capacidades oculta por defecto, indicador de estado y transición suave.
- **Toggle de modo oscuro:** control global que alterna el tema de toda la interfaz y conserva la preferencia durante la sesión.
- **Marcador de gráfico:** bloque de ancho completo para representar la futura actividad semanal mediante borde discontinuo y etiqueta centrada.
- **Bloque explicativo:** superficie informativa reutilizable para describir conceptos operativos, como el significado de una skill.

Cada componente debe ser consistente en espaciado, jerarquía, tratamiento de borde, elevación visual, color y comportamiento en modo claro y oscuro.

## 13. Datos de Demostración Esperados

Para una primera versión estática o prototipo, se recomienda disponer de datos representativos para:

- Usuarios con diferentes planes y estados.
- Agentes con distintos propietarios y estados operativos.
- Skills con diferentes niveles de adopción.
- Contratos activos y pasados con importes variados.
- Errores con diferentes gravedades y tipos.

Los datos deben ser suficientemente diversos para validar visualmente tablas, badges, dropdowns, modales, textos largos y estados críticos.

## 14. Comportamientos Transversales

### 14.1 Dropdowns

Los dropdowns deben:

- Abrirse desde un botón contextual compacto.
- Mostrar acciones claramente etiquetadas.
- Cerrarse tras seleccionar una acción.
- Cerrarse al interactuar fuera del menú.
- Mantenerse alineados con la fila o entidad correspondiente.

### 14.2 Modales

Los modales deben:

- Bloquear visualmente el contenido de fondo mediante backdrop.
- Presentarse centrados o adaptados al viewport disponible.
- Mantener jerarquía clara entre título, contenido y acciones.
- Cerrarse mediante botón explícito.
- Cerrarse mediante clic en el backdrop.
- Ser compatibles con contenido extenso mediante desplazamiento interno cuando sea necesario.

### 14.3 Expansiones

Los controles expandibles deben:

- Comunicar claramente su estado abierto o cerrado.
- Usar transición suave.
- Revelar únicamente el contenido asociado a la entidad seleccionada.
- Evitar cambios bruscos que desorienten al administrador.

## 15. Criterios Generales de Aceptación

La entrega frontend futura se considera completa cuando cumple todas las condiciones siguientes:

1. El prototipo utiliza HTML, Tailwind CSS mediante CDN y JavaScript vanilla, sin frameworks ni backend.
2. El sidebar permanece disponible y permite acceder a las seis secciones requeridas, mostrando claramente la vista activa.
3. El Dashboard presenta cuatro tarjetas de métricas y un marcador de actividad semanal debajo de ellas.
4. La tabla de usuarios muestra nombre, email, plan, estado y acciones para cada registro.
5. Cada dropdown de acciones se abre desde su botón contextual, muestra las opciones requeridas, se cierra al elegir una opción y se cierra al hacer clic fuera.
6. Ver detalle de un usuario abre un modal con su registro completo.
7. Todo modal incluye un botón de cierre y se cierra también al hacer clic sobre el backdrop.
8. La vista de agentes muestra nombre, propietario, estado y skills asociadas, diferenciando activo, inactivo y fallando.
9. Las skills de cada agente están ocultas inicialmente y el control colapsable revela únicamente la lista seleccionada con una transición suave.
10. Configurar un agente abre un modal que presenta su prompt de sistema completo.
11. La vista Skills muestra nombre, descripción, contador de agentes asociados, explicación conceptual y acciones Ver detalle y Eliminar.
12. La vista Contrataciones muestra contratos activos y pasados con cliente, agente, skills, fechas e importe total.
13. El detalle de un contrato muestra cada skill contratada junto con su precio individual y el total del contrato.
14. El Log de errores muestra timestamp, agente, tipo, descripción y badges distinguibles para gravedad; Ver detalle muestra la traza completa y Marcar como resuelto actualiza el estado visual.
15. El toggle de modo oscuro alterna la interfaz completa, incluidos sidebar, barra superior, tablas, tarjetas, dropdowns, modales, badges y controles expandibles, mediante estilos compatibles con `dark:`.
16. El layout se mantiene utilizable en escritorio, tablet y móvil sin solapamientos ni pérdida de acceso a las acciones principales.
17. Los datos de demostración permiten visualizar estados variados, textos extensos, dropdowns abiertos, modales con contenido largo y registros en estado crítico.

## 16. Fuera de Alcance en Esta Fase

Esta fase no incluye:

- Implementación HTML.
- Implementación JavaScript o TypeScript.
- Conexión con backend.
- Persistencia real de datos.
- Autenticación.
- Autorización por roles.
- Integración con pasarelas de pago.
- Librerías reales de gráficos.
- Edición persistente de prompts de sistema.
- Eliminación real de usuarios, agentes, skills, contratos o errores.

Estas capacidades pueden definirse en fases posteriores como especificaciones técnicas de integración, modelo de datos, arquitectura de estado y contrato API.

## 17. Resultado Esperado

El resultado esperado es una base documental suficientemente precisa para construir un panel administrativo frontend de AgentHub con navegación clara, estructura modular, componentes reutilizables, estados visuales consistentes y comportamiento interactivo definido para dropdowns, modales, expansiones y cambio global de tema.
