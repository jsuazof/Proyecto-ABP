**Diagrama de arquitectura cloud completo con todas las capas**, diseñado para mostrar el flujo de datos, componentes críticos y decisiones técnicas en detalle:

```mermaid
%%{init: {'theme': 'neutral', 'fontFamily': 'Arial', 'gantt': {'barHeight': 20}}}%%
graph TD
    %% Clientes
    A[Cliente Web] --> B[CloudFront]
    A2[Cliente Móvil] --> B
    A3[IoT Device] --> IOT[AWS IoT]
  
    %% Entrega de Contenido
    B --> C[S3]
    B --> D[ALB]
  
    %% Cómputo
    D --> E1[EC2 AZ1]
    D --> E2[EC2 AZ2]
  
    %% Bases de Datos
    E1 --> F[RDS]
    E2 --> F
    E1 --> G[Redis]
  
    %% Procesamiento
    E1 --> H[Lambda]
    H --> J[SQS]
  
    %% Seguridad
    B --> N[WAF]
    D --> N
  
    %% Estilos
    class A,A2,A3 fill:#2ecc71,color:white
    class B,C,D fill:#3498db,color:white
    class E1,E2 fill:#e74c3c,color:white
    class F,G fill:#9b59b6,color:white
    class H,J fill:#f39c12,color:black
    class N fill:#e67e22,color:white
    class IOT fill:#1abc9c,color:white
```

```mermaid

graph TD
    subgraph "Capa de Clientes"
    A[Web] --> B[CloudFront]
    A2[Móvil] --> B
    end
  
    subgraph "Capa de Seguridad"
    B --> WAF
    end
```

---

### **Desglose por Capas Técnicas**:

#### **1. Capa de Clientes** 🏃‍♂️

- **Web/Móvil**: Acceso via HTTPS (TLS 1.3).
- **IoT**: Protocolo MQTT seguro con AWS IoT Core.
- *Decisión*: Terminación SSL en CloudFront para reducir carga en backend.

#### **2. Capa de Entrega** 🌐

- **CloudFront**: Cachea contenido en 300+ Edge Locations.
- **ALB**: Enrutamiento basado en rutas (path-based routing).
- *Decisión*: ALB sobre NLB para soportar WebSockets.

#### **3. Capa de Aplicación** 🖥️

- **EC2 Auto Scaling**: Escalado basado en métricas custom (ej: conexiones activas).
- **Lambda**: Timeout configurado a 15 mins (máximo para procesos async).
- *Decisión*: Redis sobre Memcached por persistencia opcional.

#### **4. Capa de Datos** 🗃️

- **RDS**: Backups automáticos con PITR (Point-in-Time Recovery).
- **S3 Storage Classes**: Standard (acceso frecuente) + Glacier (archivo).
- *Decisión*: Multi-AZ con failover automático (<30 segundos).

#### **5. Capa de Seguridad** 🔐

- **WAF**: Reglas contra OWASP Top 10 (SQLi, XSS).
- **KMS**: Claves gestionadas por AWS (AWS-Managed Keys).
- *Decisión*: IAM Roles en lugar de credenciales estáticas.

#### **6. Capa de Monitoreo** 📊

- **CloudWatch Alarms**: Umbrales para CPU (>80%), errores 5xx (>1%).
- **Auto Recovery**: Reinicio automático de instancias EC2 fallidas.
- *Decisión*: SNS para notificaciones multi-canal (Slack + SMS).

---

### **Flujo Crítico (Ejemplo: Proceso de Pago)**:

```mermaid
sequenceDiagram
    Cliente->>+CloudFront: POST /checkout
    CloudFront->>+ALB: Forward request
    ALB->>+EC2: Procesar pago
    EC2->>+RDS: Registrar transacción
    EC2->>+SQS: Encolar email de confirmación
    Lambda->>+SQS: Consumir cola
    Lambda->>+SES: Enviar email
```

---
