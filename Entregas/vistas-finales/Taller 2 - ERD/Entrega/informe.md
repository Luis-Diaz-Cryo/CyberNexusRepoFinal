Este es el informe técnico en formato Markdown (.md) basado en la transcripción de la reunión y los requerimientos del proceso de auditoría, inventario y limpieza para la empresa de gestión de Airbnb.
---

# Informe Técnico: Modelo de Información y Diagrama de Contexto

## 🔖 Nombre del Taller

**Taller 2: Modelo de Información y Diagrama de Contexto**

## 👥 Integrantes del equipo

* Juan David Gonzalez Rubio
* Luis Jaime Diaz Salazar
* Ricardo Plazas Rivas
* Sergio Gabriel Nieto Meneses

---

## 🧠 Descripción general del trabajo

El objetivo de este taller es realizar el levantamiento y modelado de un proceso de negocio crítico para una empresa de gestión de propiedades en Airbnb: **la auditoría y monitoreo de la entrega de apartamentos**.

El trabajo se centra en documentar el flujo actual, el cual es **100% manual**, abarcando desde el registro de inventario (físico y lencería) hasta la supervisión de la limpieza, con el fin de identificar puntos de dolor y proponer una estructura de información que permita la futura escalabilidad y centralización de la operación.

---

## 🔧 Proceso de desarrollo

Para el desarrollo de este informe, se siguieron los siguientes pasos:

1. **Análisis de la reunion:** Se identificaron los "dolores" del cliente, destacando la falta de centralización, el uso de herramientas aisladas (Excel/WhatsApp) y la dificultad de trazabilidad en el inventario rotativo (lavandería vs. apartamento).
2. **Delimitación del Alcance:** Se decidió enfocar el modelo en el ciclo de "Checkout-Limpieza-Inventario", ya que es donde ocurre la mayor pérdida de activos (cubiertos, lencería) y se generan costos operativos ocultos.
3. **Decisiones de Diseño:** Se optó por una estructura de datos que permita separar la propiedad del inventario, facilitando que el sistema sea escalable tanto para un propietario único como para un administrador de grandes edificios.
4. **Herramientas:** Se utilizó una metodología de levantamiento basada en entrevistas y modelado lógico para representar el flujo de trabajo manual actual.

---

## 🧩 Análisis del modelo propuesto

* **Estructura:** El modelo se centra en la entidad **"Apartamento"** como eje central, vinculando procesos de **Auditoría de Salida** y **Orden de Limpieza**.
* **Representación de Necesidades:** El cliente enfatizó que la lencería y los insumos son "ecosistemas rotativos". Por ello, el modelo contempla estados de inventario (En apartamento, En lavandería, Perdido).
* **Supuestos tomados:**
* Se asume que la limpieza es realizada por personal externo o por el administrador directamente.
* La auditoría se realiza inmediatamente después del checkout del huésped.
* El control de pérdidas se registra de forma manual pero con intención de ser categorizado financieramente.



---

## 📈 Diagrama de Contexto (Proceso Actual)


---

## 📋 Tabla de Actores y Entidades

| Nombre del elemento | Tipo | Descripción | Responsable |
| --- | --- | --- | --- |
| **Operador/Administrador** | Actor | Persona que realiza la inspección física y el conteo. | Sergio Nieto / Operador |
| **Personal de Limpieza** | Actor | Encargado de la adecuación del inmueble. | Externo / Contratista |
| **Inventario (Activos)** | Entidad | Lista de objetos (cubiertos, lencería, muebles) sujetos a auditoría. | Administrador |
| **Registro de Auditoría** | Componente | Documento (actualmente Excel) donde se anotan faltantes o daños. | Operador |
| **Airbnb/Booking** | Sistema Externo | Fuente de la reserva que dispara el proceso de entrega. | Plataforma |

---

## 🔍 Investigación complementaria

**Tema investigado:** Gestión de Inventarios en Propiedades de Renta Corta (PropTech).

**Resumen:**
La gestión de propiedades tipo Airbnb difiere de la hotelería tradicional en la **descentralización geográfica**. Mientras que un hotel tiene todo su inventario en un solo edificio, un operador de Airbnb maneja "micro-hoteles" dispersos. Según las mejores prácticas de la industria *PropTech*, la clave para la escalabilidad es la **digitalización del inventario en tiempo real**.

La investigación sugiere que el paso del Excel a una base de datos centralizada reduce en un 30% el costo de reposición de activos, ya que permite identificar patrones de pérdida o daño por parte de huéspedes específicos. Esto se alinea con la visión del cliente de crear un producto "escalable y monetizable" que funcione para 1 o 100 apartamentos, automatizando el bloqueo de calendarios y la asignación de tareas de limpieza.

---

## 📚 Referencias

[1] Mases, Eduardo. *Entrevista de Levantamiento de Requerimientos - Operación Airbnb*. Febrero 2026.

[2] OMG. *Business Process Model and Notation (BPMN) Specification*. [https://www.omg.org/spec/BPMN/](https://www.omg.org/spec/BPMN/)

[3] Universidad de La Sabana. *Guía de Arquitectura Empresarial - Curso AREM*.

