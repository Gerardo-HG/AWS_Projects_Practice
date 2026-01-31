
# Lanzar un sitio web "Hola Mundo" en Internet con AWS

En este ejercicio práctico, desplegaremos un sitio web estático básico en **AWS** utilizando una instancia de **Amazon EC2**. 
Este proyecto te permitirá entender cómo lanzar un servidor en la nube y configurar las reglas de acceso para que sea visible desde cualquier lugar del mundo.

## Prerrequisitos

- Una cuenta de AWS activa.
- Par de claves (Key Pair) creado para acceso SSH.
- Navegador web para verificar la conectividad.
- Conocimientos básicos de la terminal de Linux.

## Servicios Clave

- **Amazon EC2**: Servicio que proporciona capacidad de cómputo escalable en la nube (el servidor).
- **Security Groups**: Firewall virtual que controla el tráfico entrante y saliente de la instancia.
- **Apache/Nginx**: Software de servidor web para entregar el contenido HTML.

### 1. Navegar a EC2

1. Inicia sesión en la [Consola de AWS](https://aws.amazon.com).
2. Asegúrate de estar en la región preferida (ej. `us-east-1` - N. Virginia).
3. Busca y selecciona **EC2** en el panel de servicios.

### 3. Lanzar la Instancia de Servidor Web

Vamos a configurar y lanzar la instancia para alojar nuestro "Hola Mundo".

1. En el panel de EC2, haz clic en **Launch Instance** (Lanzar instancia).
2. **Nombre**: Introduce `Hola-Mundo-Webserver`.
3. **Application and OS Images (AMI)**: Selecciona **Amazon Linux 2023** (apta para la capa gratuita).
4. **Instance Type**: Elige `t2.micro` (o `t3.micro` según disponibilidad).
5. **Key pair**: Selecciona tu par de llaves existente para acceso seguro.

#### 3.1. Configuración de Red y Seguridad

Es crucial permitir el tráfico web para que el sitio sea accesible.

1. **Network settings**:
    - Selecciona **Create security group**.
    - Marca la casilla **Allow HTTP traffic from the internet** (Puerto 80).
    - (Opcional) Marca **Allow SSH traffic** solo desde tu IP para mayor seguridad.

#### 3.2. Instalación Automática (User Data)

Para que el sitio funcione al arrancar, usaremos un script de inicio:

1. Despliega **Advanced details** al final de la página.
2. En el cuadro **User data**, pega el siguiente script:
   ```bash
   #!/bin/bash
   yum update -y
   yum install -y httpd
   systemctl start httpd
   systemctl enable httpd
   echo "<h1>Hola Mundo desde AWS - Servidor Activo</h1>" > /var/www/html/index.html

#### 3.3 Revisar y Lanzar

1. Revisar que el número de instancia sea 1.
2. Hacer click en **Launch Instance**
3. Esperar a que el estado de la instancia cambie a **Running**

#### 4. Verificación del sitio

1. Seleccionar la instancia en la consola gráfica de EC2.
2. Copiar la Public IPv4 address o el Public IPv4 DNS
3. Pegarlo en la barra de direcciones de tu navegador

¡Listo! Ya tienes tu primer sitio web funcionando en la infraestructura global de AWS.
