# Crear una instancia de Base de Datos Amazon RDS (MySQL)

En este ejercicio práctico, configuraremos tres presupuestos de costes en **AWS** utilizando **AWS Budgets**. 
Estos presupuestos te ayudarán a monitorizar tus gastos estimados y te notificarán por correo electrónico cuando superes
los umbrales definidos.

## Prerrequisitos

- Una cuenta de AWS activa
- Conocimientos básicos de VPC (Virtual Private Cloud) y Grupos de Seguridad
- Un cliente SQL instalado (como MySQL WorkBench or DBeaver) para probar la conexión

## Servicios Clave

- **Amazon RDS (Relational Database Service):** Servicio que facilita la configuración, el funcionamiento y el escalado de bases de datos relacionales en la nube.
- **Amazon VPC:** Entorno de red aislado donde se desplegará la base de datos
- **AWS Secrets Manager / KMS:** Para la gestión segura de credenciales


### 1. Navegar a Amazon RDS

1. Inicia sesión en la Consola de AWS
2. Asegurarse de estar en la región 'us-east-1' - N. Virginia.

### 2. Crear el Grupo de Seguridad 

Antes de crear la base de datos, necesitamos un "escudo" que permita el tráfico entrante y saliente.

1. Ve a la consola de EC2 -> **Security Groups**
2. Crea un grupo llamado **rds-mysql-sg**
3. Agrega una Regla de Entrada (Inbound Rule):
   - Type: MySQL/Aurora (Puerto 3306)
   - Source: Tu dirección IP (MyIP) para mayor seguridad

### 3. Crear la instancia de Base de Datos

Sigue los siguientes pasos para lanzar la instancia de MySQL:

1. En el panel de RDS, click en **Create database**
2. Choose a database creation method: Selecciona **Standard create**
3. Engine options: Selecciona **MySQL**
4. Templates: Elegir **Free Tier** (Capa gratuita)

### 3.1 Configuración de Ajustes (Settings)

1. DB instance identifier: **mydb**
2. Credential Settings:
  - Master username: admin
  - Master password: Crea una contraseña segura y guárdala

### 3.2 Configuración de instancia y almacenamiento

1. DB Instance class: Dejar el valor por defecto (db.t3g.micro o db.t4.micro)
2. Storage:
   - Storage type: General Purpose SSD (gp3)
   - Allocated storage: 20 GiB
   - Desactivar la opción "Enable storage autoscalling" para este ejercicio si quieres control total del coste
  
### 3.3 Conectividad y Red

1. Connectivity:
   - VPC: Seleccionar la vpc predeterminada
   - Public access: Selecionar Yes
   - VPC security group: Elegir **rds-mysql-sg**
   - Availability Zone: No preference
  
### 3.4 Configuración Adicional

1. Despliega **Additional configuration**:
   - Initial database name: **mydatabase**
   - Backup: Desactivar "Enable automated backups"
   - Encryption: Asegurarse de que el cifrado esté habilitado
  
### 4. Revisión y Creación

1. Desplazarse hasta el final y revisar que el coste estimado es $0 (capa gratuita seleccionada)
2. Haz clic en **Create database**

Nota: La creación de la base de datos puede tardar entre 5 y 10 minutos. El estado cambiará a **Creating** a **Available**

![Instancia de RDS MySQL](RDS_1.png)

!(RDS_2.png)


¡Listo! Ya tienes configurados tus tres presupuestos de gastos en AWS.

## Resultado Esperado
