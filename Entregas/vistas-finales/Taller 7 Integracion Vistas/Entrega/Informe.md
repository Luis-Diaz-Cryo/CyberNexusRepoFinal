# Taller 7 - Parte 2: Aplicación al Cliente Real

## Integración de Vistas de Arquitectura

**Equipo:** CyberNexus  
**Cliente real:** Eduardo García, dueño de la empresa  
**Organización:** Proyectos e Inversiones GT S.A.S  
**Tipo de negocio:** Renta de Airbnb / administración de alojamientos de corta estancia  
**Ubicación principal:** Bogotá  
**Tecnología actual principal:** Excel  
**Fecha base de caracterización:** 21/02/2026

---

## 1. Contexto del cliente real

Proyectos e Inversiones GT S.A.S es una empresa orientada a la administración de alojamientos de corta estancia tipo Airbnb. Actualmente no cuenta con empleados formales, pero maneja una base de aproximadamente 22 clientes fijos y en aumento. Su operación depende principalmente de Excel para registrar reservas, clientes, pagos, disponibilidad, información de apartamentos y seguimiento básico de la operación.

El problema principal identificado es que el negocio depende de procesos manuales y archivos dispersos. Esto puede funcionar en una etapa pequeña, pero se vuelve riesgoso cuando crece el número de clientes, reservas y propiedades. Por esta razón, la integración de vistas arquitectónicas permite visualizar cómo el negocio puede pasar de una operación basada en Excel a una solución más estructurada, segura y escalable.

---

## 2. Vistas integradas del cliente

La arquitectura se organizó en cinco vistas principales: negocio, información, aplicaciones, infraestructura y seguridad. La idea es que cada vista responda una pregunta distinta, pero todas se conecten dentro de una misma narrativa.

### 2.1 Vista de negocio

La vista de negocio representa los procesos principales que generan valor para el cliente:

- Registro y actualización de propiedades disponibles.
- Gestión de reservas.
- Registro de huéspedes o clientes.
- Control de pagos y estados de reserva.
- Coordinación de entrada y salida del huésped.
- Seguimiento de limpieza, mantenimiento o novedades.
- Reporte de ingresos y ocupación.

Esta vista es la base de toda la arquitectura porque muestra qué necesita operar el negocio. La decisión clave fue tomar la operación real actual, basada en Excel, y convertirla en un flujo más claro: cliente consulta disponibilidad, se registra reserva, se confirma pago, se actualiza disponibilidad, se coordina estadía y se generan reportes.

### 2.2 Vista de información

La vista de información define los datos principales que debe manejar el sistema. Las entidades más importantes son:

- **Cliente/Huésped:** persona que realiza o usa la reserva.
- **Propiedad/Alojamiento:** apartamento, casa o espacio disponible para renta.
- **Reserva:** relación entre un cliente, una propiedad y unas fechas específicas.
- **Pago:** valor, estado, fecha y método de pago.
- **Disponibilidad:** calendario de ocupación por propiedad.
- **Mantenimiento/Novedad:** problemas reportados, limpieza o tareas pendientes.
- **Reporte:** indicadores de ocupación, ingresos y desempeño.

La decisión clave fue separar la información en entidades independientes. En Excel normalmente muchos de estos datos pueden quedar mezclados en una misma tabla, pero en una arquitectura más coherente se deben diferenciar para evitar duplicados, errores de actualización y pérdida de trazabilidad.

### 2.3 Vista de aplicaciones

La vista de aplicaciones plantea los módulos o componentes funcionales que soportan los procesos del negocio:

- **Módulo de gestión de propiedades:** permite registrar y actualizar alojamientos.
- **Módulo de reservas:** controla fechas, estados y disponibilidad.
- **Módulo de clientes:** centraliza información de huéspedes.
- **Módulo de pagos:** registra pagos recibidos, pendientes o cancelados.
- **Módulo de reportes:** resume ingresos, ocupación y desempeño.
- **Módulo administrativo:** gestiona usuarios, permisos y configuración.

La decisión clave fue no pensar en una aplicación demasiado grande desde el inicio, sino en módulos pequeños conectados. Esto permite que la empresa pueda empezar con una solución simple y luego escalarla a medida que crezca.

### 2.4 Vista de infraestructura

La vista de infraestructura representa dónde funcionaría la solución tecnológica. Dado que el cliente actualmente usa Excel y no cuenta con un equipo técnico interno, la propuesta más coherente es una infraestructura ligera y en la nube:

- Aplicación web accesible desde navegador.
- Base de datos centralizada para reemplazar archivos dispersos.
- Almacenamiento en la nube para soportes o documentos.
- Backups automáticos.
- Acceso desde computador o celular.
- Posible integración futura con plataformas externas de reservas.

La decisión clave fue evitar una infraestructura local compleja. Para una empresa pequeña, una solución web con servicios en la nube reduce costos iniciales, facilita el acceso remoto y permite crecer sin comprar servidores físicos.

### 2.5 Vista de seguridad

La vista de seguridad se enfoca en proteger datos personales, pagos, reservas y acceso administrativo. Los controles principales son:

- Autenticación de usuarios.
- Roles y permisos, por ejemplo administrador y operador.
- Respaldo periódico de información.
- Control de acceso a datos sensibles de clientes.
- Registro de cambios importantes.
- Protección de archivos y documentos.
- Buenas prácticas de contraseñas.

La decisión clave fue incluir seguridad desde el diseño y no como algo adicional. Aunque el negocio sea pequeño, maneja información de clientes, fechas de estadía, pagos e ingresos, por lo que necesita controles mínimos para evitar pérdida de información o acceso no autorizado.

---

## 3. Cómo se articulan las vistas entre sí

Las vistas se articulan siguiendo una cadena lógica:

1. **El negocio define la necesidad:** Proyectos e Inversiones GT S.A.S necesita administrar reservas, clientes, propiedades, pagos y reportes.
2. **La información estructura esa necesidad:** los procesos del negocio se traducen en entidades como Cliente, Propiedad, Reserva, Pago y Reporte.
3. **Las aplicaciones automatizan los procesos:** cada módulo funcional usa esas entidades para reducir el trabajo manual que hoy se realiza en Excel.
4. **La infraestructura soporta la operación:** la aplicación y la base de datos se alojan en una plataforma accesible, preferiblemente en la nube.
5. **La seguridad protege la arquitectura:** los controles de acceso, respaldo y permisos permiten que la solución sea confiable.

La integración demuestra que ninguna vista funciona aislada. Por ejemplo, el proceso de reserva en la vista de negocio necesita datos de cliente y propiedad en la vista de información; luego requiere un módulo de reservas en la vista de aplicaciones; ese módulo necesita una base de datos en la vista de infraestructura; y finalmente debe estar protegido mediante roles y control de acceso en la vista de seguridad.

---

## 4. Decisiones clave de arquitectura

### 4.1 Centralizar la información

La primera decisión importante fue proponer una base de datos centralizada. Esto responde al problema actual de depender de Excel, donde es fácil duplicar información, cometer errores de edición o perder trazabilidad.

### 4.2 Diseñar por módulos

La segunda decisión fue dividir la solución en módulos: propiedades, reservas, clientes, pagos y reportes. Esta división hace que la arquitectura sea más fácil de entender, mantener y ampliar.

### 4.3 Priorizar una solución web

La tercera decisión fue plantear una solución web porque el cliente necesita acceso flexible y no parece contar con infraestructura propia. Una aplicación web permite que el dueño consulte información desde diferentes dispositivos sin depender de un único archivo local.

### 4.4 Mantener seguridad básica desde el inicio

La cuarta decisión fue incorporar autenticación, permisos y respaldos desde la primera versión. Esto es importante porque la empresa maneja datos personales y financieros.

### 4.5 Permitir crecimiento futuro

La quinta decisión fue dejar abierta la posibilidad de integraciones futuras con plataformas de reserva, pasarelas de pago o herramientas de análisis. Aunque el estado actual puede iniciar simple, la arquitectura no debe bloquear el crecimiento.

---

## 5. Reflexión crítica sobre la coherencia de la arquitectura

La arquitectura propuesta es coherente porque parte de una necesidad real: organizar una operación de renta de Airbnb que actualmente depende de Excel. La solución no propone tecnología innecesariamente compleja, sino una evolución lógica desde archivos manuales hacia una plataforma centralizada.

La principal fortaleza de la arquitectura es que conecta directamente los procesos del negocio con los datos y módulos necesarios. El flujo de reservas, pagos y reportes se entiende de forma clara, y cada vista tiene una función específica. Además, la propuesta reconoce que el cliente es una empresa pequeña, por lo que la infraestructura debe ser liviana, de bajo costo y fácil de administrar.

Sin embargo, también existen riesgos. El primero es que si el cliente no cambia sus hábitos de registro y control, una aplicación nueva podría terminar replicando los errores del Excel. El segundo riesgo es la calidad de los datos: si la información inicial de clientes, propiedades o reservas está incompleta, la migración puede generar inconsistencias. El tercer riesgo es que la seguridad sea subestimada por tratarse de un negocio pequeño, aunque en realidad maneja información sensible.

En conclusión, la arquitectura es consistente siempre que se implemente de forma gradual. La primera fase debería enfocarse en centralizar propiedades, clientes y reservas. Luego se podrían agregar pagos, reportes avanzados e integraciones externas. De esta forma, la arquitectura mantiene coherencia entre lo que el negocio necesita hoy y lo que podría necesitar en el futuro.

---

## 6. Relación con entregables previos

Los entregables previos del cliente se integran dentro del tablero final de la siguiente forma:

| Entregable previo | Vista donde se integra | Uso dentro de la arquitectura |
|---|---|---|
| Ficha de caracterización | Negocio | Define cliente, contexto, tecnología actual y necesidades reales. |
| Procesos/BPMN | Negocio | Permite representar el flujo de reservas, pagos y operación. |
| Modelo de datos/ERD | Información | Organiza entidades como Cliente, Propiedad, Reserva y Pago. |
| Vista de aplicaciones | Aplicaciones | Define módulos funcionales necesarios para automatizar el negocio. |
| Vista de infraestructura | Infraestructura | Explica dónde se ejecutan la aplicación, base de datos y respaldos. |
| Vista de seguridad | Seguridad | Define accesos, permisos, protección de datos y respaldo. |
| Riesgos y gobierno | Transversal | Ayuda a evaluar coherencia, control, mantenimiento y evolución. |

---

## 7. Conclusión

La integración de vistas para Proyectos e Inversiones GT S.A.S permite ver la arquitectura como una historia completa: el negocio necesita controlar reservas y clientes; esos procesos requieren información ordenada; la información se administra mediante módulos de aplicación; los módulos se ejecutan sobre infraestructura en la nube; y todo debe protegerse con controles de seguridad.

La propuesta es adecuada para una empresa pequeña en crecimiento porque no intenta reemplazar todo de una vez, sino organizar el paso desde Excel hacia una solución digital más confiable. La arquitectura final también permite justificar mejor las decisiones técnicas tomadas durante el curso y mostrar cómo cada entregable previo aporta a una visión empresarial integrada.
