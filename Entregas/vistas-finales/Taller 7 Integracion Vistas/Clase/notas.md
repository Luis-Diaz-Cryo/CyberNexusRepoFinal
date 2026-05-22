
# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller

**Taller – Integración de Vistas de Arquitectura**

---

## 👥 Integrantes del equipo

Equipo CyberNexus

---

## 🧠 Descripción general del trabajo

Documentación arquitectónica de un sistema de e-commerce farmacéutico analizado desde las 5 vistas del modelo de arquitectura empresarial (negocio, información, aplicaciones, infraestructura y seguridad), con dos casos de uso detallados: el proceso de compra end-to-end y el sistema de rastreo de entregas en tiempo real.

## 🔧 Vistas del Caso FarmApp

<img width="482" height="612" alt="image" src="https://github.com/user-attachments/assets/14d75f12-dfb3-4839-93f0-73e4f8a487d7" />

## 🧩 Relaciones Claves entre Capas

1. **Negocio**

   * Negocio → Aplicaciones: cada proceso de negocio (compra, prescripción, despacho) tiene una o más apps que lo ejecutan. El proceso de compra vive en la App móvil y el E-commerce; el despacho, en el sistema POS y la red logística.
   
2. **Información**

   * Información → Aplicaciones: las entidades de datos son compartidas. Cliente es consumida por el CRM y la App; Pedido por el POS y el E-commerce; Producto por inventario y todas las interfaces. Aquí está la sincronización más crítica de FarmApp.

3. **Aplicaciones**

   * Aplicaciones → Infraestructura: las apps corren sobre servidores regionales (para baja latencia en tiendas físicas) y la nube híbrida (para escalar pedidos online). La BD replicada garantiza que el inventario sea consistente entre el POS físico y el canal digital.
     
4. **Seguridad**

   * Seguridad (transversal): no es una capa aislada — atraviesa todas. El cifrado protege los datos de Cliente y Prescripción; el RBAC controla qué rol (farmacéutico, repartidor, administrador) accede a qué app; el monitoreo de fraude opera sobre las transacciones de pago en tiempo real.
