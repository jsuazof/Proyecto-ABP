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
![Diagrama Cloud](https://miro.medium.com/v2/resize:fit:1400/1*5qOFfDnY5sQNJn0hD3QoBg.png)  
- **Componentes**:  
  - Frontend: CDN + Almacenamiento estático.  
  - Backend: Contenedores en EKS/AKS/GKE.  
  - Autenticación: Cognito (AWS) / Firebase (GCP).  
- [Ver Diagrama Detallado](/docs/architecture_diagram.drawio).  

### 3. 🔍 **Análisis de Casos**  
- **Caso Retail (Falabella/Ripley)**: [Ver PDF](/docs/caso_retail_chile.pdf).  
- **Caso Startup Tech**: [Ver Markdown](/docs/caso_startup_tech.md).  

### 4. 📊 **Presentación Final**  
- Resumen ejecutivo, desafíos y lecciones aprendidas.  
- [Slides en PDF](/presentation/proyecto_cloud.pdf).  

---

## 🚀 **Cómo Usar Este Repositorio**  
1. **Explorar Documentación**:  
   - La carpeta `/docs` contiene toda la teoría y decisiones técnicas.  
2. **Ver Diagramas**:  
   - Editar con [Draw.io](https://draw.io) (archivos `.drawio`).  
3. **Revisar Análisis**:  
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

