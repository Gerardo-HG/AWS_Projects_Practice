# Configurar Alarmas de Facturación en AWS con CloudWatch y SNS

En este ejercicio práctico, configuraremos tres alarmas de facturación en **AWS** utilizando **Amazon CloudWatch** y **Amazon SNS**. Estas alarmas te notificarán por correo electrónico cuando tus gastos estimados superen los umbrales de **$5**, **$25** y **$100** USD.

## Prerrequisitos

- Una cuenta de AWS activa.
- Tener habilitadas las métricas de facturación (Billing Metrics) en la consola de AWS. Generalmente, están activadas por defecto en la región `us-east-1`. Si no, ve a la consola de **Billing** > **Billing Preferences** y habilita "Receive Billing Alerts".

## Servicios Clave

- **Amazon CloudWatch**: El servicio de monitorización y observabilidad de AWS.
- **Amazon SNS**: Servicio de mensajería para notificaciones *pub/sub*.

### 1. Navegar a CloudWatch

1. Inicia sesión en la **Consola de AWS**.
2. Asegúrate de estar en la región **N. Virginia** (`us-east-1`), ya que las métricas de facturación solo residen aquí.
3. Busca y selecciona **CloudWatch**.

### 2. Crear un Tema de SNS (Canal de Notificación)

*Si ya tienes un tema de SNS configurado, omite este paso.*

1. Ve a la consola de **SNS** (busca "SNS" en la barra de búsqueda de AWS).
2. En el menú lateral, selecciona **Temas** y haz clic en **Crear tema**.
3. Introduce un nombre para el tema (ej. `MisAlarmasDeFacturacion`).
4. Selecciona el tipo **Estándar** (o FIFO si necesitas orden estricto).
5. Haz clic en **Crear tema**.
6. Una vez creado, ve a **Suscripciones** en el menú lateral, haz clic en **Crear suscripción**.
7. Selecciona el tema que acabas de crear.
8. En "Protocolo", elige **Correo electrónico** (Email).
9. Introduce tu dirección de correo electrónico.
10. Haz clic en **Crear suscripción**.
11. **Importante**: Revisa tu bandeja de entrada y **confirma la suscripción** haciendo clic en el enlace del correo de AWS.

### 3. Crear las Alarmas de Facturación

1. Regresa a la consola de **CloudWatch**.
2. En el menú lateral, ve a **Métricas** y busca la categoría **Billing** (Facturación).
3. Selecciona **Total Estimated Charges** (Cargos estimados totales) en la divisa **USD**.
4. Marca la casilla para la métrica `EstimatedCharges` y haz clic en **Acciones** > **Crear alarma**.
5. Configura la alarma:
    - **Métrica**: Confirma que es `EstimatedCharges | USD`.
    - **Condiciones**:
        - Define el umbral: Selecciona **Estático**.
        - "Siempre que EstimatedCharges sea...": Selecciona **Mayor o igual que**.
        - Valor del umbral: Introduce el valor objetivo (**5**, **25** o **100**).
    - **Configurar acciones**:
        - En "Tema de SNS", selecciona el tema que creaste anteriormente (ej. `MisAlarmasDeFacturacion`).
6. Haz clic en **Siguiente** (dos veces).
7. Introduce un nombre para la alarma (ej. `Alarma-Facturacion-5USD`, `Alarma-Facturacion-25USD`, etc.).
8. Haz clic en **Crear alarma**.

Repite el paso 3 para los otros dos umbrales de facturación. ¡Listo! Ya tienes configuradas tus alarmas de gastos básicos en AWS.

## Resultado Esperado

![Imagen 1](CloudWatch_1.png)

![Imagen 2](CloudWatch_2.png)

![Imagen 3](CloudWatch_3.png)

