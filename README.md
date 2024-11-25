# Informe Final del Proyecto: Pruebas de la Nueva Funcionalidad en la API de Urban.Grocers

## **Descripción del Proyecto**
El equipo de desarrollo ha actualizado la API de **Urban.Grocers** añadiendo funcionalidades para trabajar con kits y servicios de entrega. Este proyecto consistió en diseñar, ejecutar y documentar pruebas para validar estos nuevos endpoints.

---

## **Objetivos**
1. Analizar los requisitos y estudiar la documentación de la API.
2. Diseñar listas de comprobación para cubrir todos los casos de prueba relevantes.
3. Probar los endpoints utilizando **Postman** y reportar errores en **Jira**.
4. Proveer un informe detallado sobre el estado de la funcionalidad probada.

---

## **Requisitos del Proyecto**

### **1. Endpoint: Agregar Comestibles a un Kit**
- **Endpoint:** `POST /api/v1/kits/{id}/products`
- **Funcionalidad:** Permite agregar productos a un kit.
- **Validaciones:**
  - La longitud de la lista de productos no debe superar los **30 productos**.
  - Si se supera el límite, devuelve un **400 Bad Request**.

### **2. Endpoint: Comprobar Disponibilidad y Precio de Entrega**
- **Endpoint:** `POST /order-and-go/v1/delivery`
- **Funcionalidad:** Determina si el servicio de entrega "Order and Go" está disponible y calcula el precio de entrega.
- **Validaciones:**
  - Verificar la disponibilidad de entrega para ubicaciones específicas.
  - Calcular el precio según los parámetros enviados.

---

## **Lista de Comprobación**

### **1. Endpoint: Agregar Comestibles a un Kit**
#### **Casos de Prueba Positivos**
1. Agregar un producto válido a un kit existente.
2. Agregar múltiples productos (≤ 30) y verificar respuesta `200 OK`.
3. Validar que los productos agregados aparecen en el kit.

#### **Casos de Prueba Negativos**
1. Intentar agregar más de 30 productos al kit (debe devolver `400 Bad Request`).
2. Enviar un producto con un ID no válido.
3. Usar un ID de kit inexistente (debe devolver `404 Not Found`).

---

### **2. Endpoint: Servicios de Entrega**
#### **Casos de Prueba Positivos**
1. Solicitar disponibilidad para una ubicación válida.
2. Calcular el precio de entrega para distancias corta y larga.
3. Validar que el precio se calcula correctamente.

#### **Casos de Prueba Negativos**
1. Omitir parámetros obligatorios (e.g., dirección).
2. Probar una ubicación sin cobertura (debe devolver `404 Not Found`).
3. Enviar datos mal formados y validar el error `400 Bad Request`.

---

## **Ejecución de Pruebas**

### **Herramientas Utilizadas**
- **Postman:** Para la ejecución y validación de las solicitudes.
- **Jira:** Para documentar y rastrear los errores encontrados.

### **Resultados**
#### **Endpoint: Agregar Comestibles a un Kit**
- **Total de pruebas ejecutadas:** 6
- **Pruebas exitosas:** 5
- **Errores detectados:** 1
  - **Error:** El endpoint devuelve `400 Bad Request` al intentar agregar exactamente 30 productos, lo que contradice los requisitos.

#### **Endpoint: Servicios de Entrega**
- **Total de pruebas ejecutadas:** 6
- **Pruebas exitosas:** 6
- **Errores detectados:** 0

---

## **Errores Detectados**
1. **Descripción:** El endpoint `POST /api/v1/kits/{id}/products` devuelve un error `400 Bad Request` cuando se agregan exactamente 30 productos.
   - **Impacto:** Genera confusión para los usuarios y posibles fallos en la integración.
   - **Reporte:** Documentado en **Jira** con pasos para reproducir, capturas de pantalla y detalles técnicos.

---

## **Conclusión**
- **Endpoint de servicios de entrega:** Funciona según lo especificado y pasó todas las pruebas.
- **Endpoint de agregar productos a un kit:** Presenta un error crítico en la validación del límite máximo de productos.
---
**Enlace a los reportes finales:** [[Ver Informe Final](https://drive.google.com/drive/folders/1J0AvXbDwNH6IiZjEOU0rlFckExRoFhGS?usp=sharing)](#)
---

## **Recomendaciones**
1. Corregir el comportamiento del endpoint `POST /api/v1/kits/{id}/products` para manejar correctamente el límite de 30 productos.
2. Repetir las pruebas una vez solucionados los errores reportados.
3. Automatizar pruebas críticas con herramientas como Newman para garantizar estabilidad en futuras versiones.


---

**Equipo QA de Urban.Grocers**  





