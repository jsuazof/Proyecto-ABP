### 📝 **Informe de Pruebas**  
**Proyecto: Sistema de Reservas en la Nube**  

---

#### **1. Pruebas Unitarias**  
**Objetivo**: Verificar funcionalidad de componentes individuales.  

| **Módulo**       | **Cobertura** | **Resultados**                     | **Problemas/Soluciones**                |  
|------------------|--------------|------------------------------------|-----------------------------------------|  
| API Reservas     | 95%          | 58/60 tests OK                     | Error en validación de fechas: Corregido con regex mejorado |  
| Autenticación    | 90%          | 42/45 tests OK                     | Falso positivo en JWT expirado: Actualizado mock de tiempo |  
| Base de Datos    | 88%          | 35/40 tests OK                     | Deadlock en transacciones: Añadido retry automático |  

**Herramientas**:  
- Jest (Node.js) / Pytest (Python)  
- Cobertura: `nyc` (JavaScript) / `pytest-cov` (Python)  

---

#### **2. Pruebas de Carga**  
**Objetivo**: Evaluar rendimiento bajo tráfico alto.  

| **Escenario**          | **Usuarios Concurrentes** | **Latencia Promedio** | **Errores** | **Solución**                |  
|------------------------|--------------------------|-----------------------|-------------|-----------------------------|  
| Reservas simultáneas   | 1,000                    | 320 ms                | 2% (HTTP 500)| Ajustado autoescalado EC2   |  
| Consulta de disponibilidad | 5,000               | 150 ms                | 0.1%        | Cache Redis añadido         |  
| Pico CyberDay          | 10,000                   | 700 ms (pico)         | 5%          | Pre-calentamiento Lambda    |  

**Herramientas**:  
- Locust (Python) / Artillery (JavaScript)  
- Monitorización: AWS CloudWatch / Prometheus  

---

#### **3. Problemas Críticos Resueltos**  
1. **Timeout en API**:  
   - *Causa*: Límite de 10 segundos en ALB.  
   - *Solución*: Optimización de queries SQL + aumento a 30 segundos.  

2. **Concurrencia en Redis**:  
   - *Causa*: Race condition al actualizar cache.  
   - *Solución*: Implementado `WATCH` + transacciones.  

---



