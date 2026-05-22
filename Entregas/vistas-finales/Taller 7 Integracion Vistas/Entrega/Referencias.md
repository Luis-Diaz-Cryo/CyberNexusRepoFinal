# Referencias y ejemplos usados

## 1. Repositorio del taller

- Repositorio base del Taller 7: `AREM-Taller_7_Integracion_Vistas`. Se usó como guía para cumplir la estructura esperada: `Entrega/tablero-integrado-cliente.drawio`, `Entrega/Informe.md` y `Entrega/Referencias.md`.

## 2. Repositorio del cliente real

- Repositorio del proyecto del equipo CyberNexus: `CyberNexusRepoFinal`. Se usó como base de los entregables previos del cliente real, especialmente las vistas finales, la ficha de caracterización, reflexiones y resumen ejecutivo.

## 3. Repositorio de la primera parte

- Repositorio `Taller7IntegraciondeVistas`. Se usó como referencia de estructura y estilo para mantener consistencia con el trabajo realizado en la primera parte del taller.

## 4. Ejemplos reales y buenas prácticas de documentación de arquitectura

### C4 Model

El modelo C4 propone documentar arquitectura mediante diferentes niveles de abstracción, como contexto, contenedores, componentes y código. Para este taller se tomó como referencia la idea de separar el sistema por niveles y audiencias, aunque el tablero se adaptó a las vistas solicitadas por el curso: negocio, información, aplicaciones, infraestructura y seguridad.

Referencia: https://c4model.com/

### TOGAF

TOGAF se tomó como referencia porque plantea la arquitectura empresarial como un conjunto organizado de artefactos, estándares, repositorios y vistas. Esto ayuda a justificar que las vistas no deben verse como diagramas aislados, sino como piezas conectadas dentro de una arquitectura empresarial.

Referencia: https://www.opengroup.org/togaf

### Azure Architecture Center

El Centro de Arquitectura de Azure se usó como ejemplo de documentación real que combina diagramas, decisiones tecnológicas, patrones y guías de arquitectura. Aunque el proyecto del cliente no necesariamente usa Azure, el ejemplo sirve para entender cómo una arquitectura debe conectar infraestructura, aplicaciones, seguridad y operación.

Referencia: https://learn.microsoft.com/es-es/azure/architecture/

### Airbnb y gestión de alojamientos

Airbnb se usó como referencia del contexto del negocio, ya que el cliente opera en el área de renta de alojamientos de corta estancia. La arquitectura propuesta se adaptó a una empresa pequeña que administra reservas, propiedades, clientes y pagos, no a una plataforma global como Airbnb.

Referencia: https://www.airbnb.com.co/

## 5. Aprendizajes aplicados

- Separar las vistas facilita explicar la arquitectura a personas técnicas y no técnicas.
- La vista de negocio debe dirigir las decisiones de aplicaciones e infraestructura.
- La información debe centralizarse para evitar errores derivados del uso manual de Excel.
- La seguridad debe considerarse desde el diseño, incluso en empresas pequeñas.
- La arquitectura debe permitir crecimiento gradual y no depender de una implementación demasiado compleja desde el inicio.
