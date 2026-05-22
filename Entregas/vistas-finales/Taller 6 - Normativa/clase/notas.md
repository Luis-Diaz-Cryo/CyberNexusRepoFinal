# Notas de Clase — Taller 6: Checklist de Cumplimiento Normativo
**Caso base:** GobData — Portal de Trámites Ciudadanos  
**Fecha:** Marzo 2026  
**Curso:** Arquitectura Empresarial — Universidad de La Sabana

---

## 1. Contexto del Sistema Evaluado

**GobData** es un portal estatal de atención digital donde los ciudadanos gestionan documentos, certificados, peticiones y notificaciones. El sistema:

- Procesa datos sensibles: números de identificación, historial clínico, direcciones, antecedentes.
- Integra múltiples entidades públicas (salud, impuestos, derechos civiles).
- Requiere autenticación, trazabilidad y auditoría de acciones.
- Está sujeto a normativas nacionales e internacionales.

---

## 2. Normativas Aplicadas

| Normativa | Ámbito | Aspectos clave evaluados |
|---|---|---|
| **Ley 1581 de 2012** (Habeas Data) | Colombia | Consentimiento, derechos ARCOP, retención, operadores |
| **ISO/IEC 27001** | Internacional | Seguridad de la información, control de acceso, auditoría |
| **Decreto 1377 de 2013** | Colombia | Reglamentación de la Ley 1581, aviso de privacidad |
| **Ley 1266 de 2008** | Colombia | Habeas Data financiero y crediticio |

---

## 3. Resumen del Checklist Diligenciado

Se evaluaron **25 criterios** distribuidos en **8 categorías**:

| Categoría | Criterios | ✅ Cumple | ⚠️ Parcial | ❌ No Cumple |
|---|---|---|---|---|
| Consentimiento Informado | 4 | 2 | 1 | 1 |
| Derechos del Titular | 3 | 1 | 1 | 1 |
| Seguridad de la Información | 5 | 2 | 2 | 1 |
| Control de Acceso y Roles | 4 | 3 | 1 | 0 |
| Retención y Eliminación | 3 | 0 | 2 | 1 |
| Gestión de Terceros | 2 | 0 | 1 | 1 |
| Auditoría y Trazabilidad | 3 | 2 | 1 | 0 |
| Notificación de Incidentes | 2 | 0 | 1 | 1 |
| **TOTAL** | **26** | **10** | **10** | **6** |

**Porcentaje de cumplimiento pleno:** ~38%  
**Criterios con algún nivel de cumplimiento (✅ + ⚠️):** ~77%

---

## 4. Hallazgos Más Relevantes

### 🔴 Brechas Críticas (Prioridad Alta)

1. **Menores de edad sin protección diferenciada**  
   No existe validación de edad ni flujo para autorización de representante legal. Incumple directamente el Art. 7 de la Ley 1581. Riesgo legal alto.

2. **Backups sin cifrado**  
   Los datos en bases primarias están cifrados (AES-256), pero los respaldos en almacenamiento secundario no. Un robo o pérdida física expone datos sensibles sin protección.

3. **Sin pentesting en 12+ meses**  
   El último informe de vulnerabilidades tiene 18 meses de antigüedad. Vulnerabilidades no detectadas pueden comprometer datos de miles de ciudadanos.

4. **30% de proveedores sin contratos actualizados**  
   La Ley 1581 (Art. 25) exige contratos escritos con operadores externos. La responsabilidad es solidaria ante un incidente.

5. **Sin proceso automatizado de eliminación de datos**  
   La supresión de datos vencidos es manual y sin evidencia verificable, lo que genera acumulación ilegal de datos fuera del plazo de retención.

6. **Sin notificaciones al titular ante cambios de política**  
   El ciudadano no es informado automáticamente cuando cambian las condiciones del tratamiento de sus datos.

### 🟡 Brechas Moderadas (Prioridad Media)

- Módulo de Derechos ARCOP incompleto (falta cancelación y portabilidad).
- Sin evaluación formal de seguridad a proveedores críticos.
- Riesgo de re-identificación en datasets estadísticos publicados.
- Procedimiento de notificación a SIC sin plazos definidos ni plantilla.
- Auditorías internas sin seguimiento formal a hallazgos anteriores.

---

## 5. Lo que Funciona Bien ✅

- TLS 1.3 en todos los endpoints — cifrado en tránsito correcto.
- Política de contraseñas robusta con bloqueo por intentos fallidos.
- Separación de funciones entre administradores y auditores.
- Registro de logs de acceso con identificación de usuario y timestamp.
- DPO (Oficial de Protección de Datos) designado formalmente.
- Tiempos de respuesta a solicitudes dentro del plazo legal (promedio 8 días).
- Aviso de privacidad con finalidades específicas disponible públicamente.

---

## 6. Reflexiones del Equipo

### ¿Por qué es importante el cumplimiento en GobData?

- Maneja datos de **todos los ciudadanos**, no solo clientes voluntarios.
- La confianza ciudadana en el Estado depende de que sus datos estén protegidos.
- Las sanciones de la SIC pueden llegar hasta **2.000 SMMLV** por incumplimiento grave.
- Un incidente de seguridad tiene impacto político, reputacional y legal simultáneamente.

### Principio de Mínimo Privilegio en Sistemas Públicos

La separación de roles en GobData (Ciudadano / Funcionario / Supervisor / Administrador / Auditor) es un ejemplo de buena práctica. Sin embargo, la recertificación manual cada 6 meses es insuficiente para un sistema con alta rotación de funcionarios públicos.

### Datos Sensibles = Responsabilidad Diferenciada

El historial médico, los antecedentes judiciales y los datos de identidad son categorías especiales bajo el Art. 5 de la Ley 1581. Su tratamiento requiere consentimiento explícito, cifrado reforzado y retención mínima. GobData debe tener políticas diferenciadas por tipo de dato, no una política general.

---

## 7. Preguntas para Discusión en Clase

1. ¿Cómo debería GobData gestionar el consentimiento cuando el ciudadano **no puede negarse** a entregar sus datos para un trámite obligatorio (ej. renovación de cédula)?

2. ¿Qué ocurre si un proveedor externo (operador de datos) sufre una brecha? ¿Quién responde ante el ciudadano: el operador o el responsable (GobData)?

3. ¿Debería un portal estatal exigir **MFA** a todos sus usuarios, incluso a ciudadanos mayores con baja alfabetización digital?

4. ¿Cuál es la diferencia práctica entre **anonimización** y **seudonimización** y por qué importa para los reportes estadísticos de GobData?

---

## 8. Referencias Rápidas

- Ley 1581 de 2012: <https://www.funcionpublica.gov.co/eva/gestornormativo/norma.php?i=49981>
- Decreto 1377 de 2013: <https://www.sic.gov.co/decreto-1377-de-2013>
- ISO/IEC 27001:2022 (resumen SIC): <https://www.sic.gov.co/proteccion-de-datos-personales>
- Superintendencia de Industria y Comercio: <https://www.sic.gov.co>
- Guía de implementación Ley 1581 (SIC): <https://www.sic.gov.co/guias-cartillas-proteccion-datos>
