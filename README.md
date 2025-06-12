# 📚 Proyecto ABP - Arquitectura Cloud  
**Sistema de Reservas en la Nube** *(Marco Teórico)*  

---

## 📌 Descripción  
Este repositorio contiene la **documentación técnica, diagramas y análisis** para diseñar una arquitectura cloud escalable que soporte un sistema de reservas, enfocado en proveedores como AWS, Azure y GCP.  

---

## �️ **Entregables**  

### 1. 📄 **Documentación Técnica**  
- **Servicios Cloud Utilizados**:  
  - **Cómputo**: EC2 (AWS), App Service (Azure), Compute Engine (GCP).  
  - **Almacenamiento**: S3 (AWS), Blob Storage (Azure), Cloud Storage (GCP).  
  - **Bases de Datos**: RDS (AWS), Azure SQL (Azure), Cloud SQL (GCP).  
- **Tecnologías**: Microservicios, Kubernetes, CI/CD.  
- [Ver Documentación Completa](/docs/Codigo_Fuente_(Estructura_Teorica).md).  

### 2. 📐 **Diagrama de Arquitectura**  
- **Componentes**:  
  - Frontend: CDN + Almacenamiento estático.  
  - Backend: Contenedores en EKS/AKS/GKE.  
  - Autenticación: Cognito (AWS) / Firebase (GCP).  
- [Ver Diagrama Detallado](/docs/Diagrama_de_Arquitectura.md).  

### 3. 🔍 **Informe de Pruebas**  
- **Informe de pruebas unitarias y cargas realizadas, incluye resultados obtenidos y   resolucion de problemas.**: [Ver Informe](/docs/Informe_de_pruebas.md).  


### 4. 📊 **Presentación Final**  
- Resumen ejecutivo, desafíos y lecciones aprendidas.  
- [Slides en PDF](/presentation/proyecto_cloud.pdf).  

---

## 🚀 **Cómo Usar Este Repositorio**  
1. **Explorar Documentación**:  
   - La carpeta `/docs` contiene toda la teoría y decisiones técnicas.  
2. **Revisar Análisis**:  
   - Comparativas de proveedores cloud en `/docs/casos`.  

---

## 🛠️ **Tecnologías y Herramientas**  
| Categoría       | Herramientas |  
|----------------|-------------|  
| **Cloud**      | AWS, Azure, GCP |  
| **Diagramas**  | Draw.io, Lucidchart |  
| **Documentación** | Markdown, PDF |  

---

## 📜 **Licencia**  
Este proyecto está bajo licencia [MIT](/LICENSE).  

---

