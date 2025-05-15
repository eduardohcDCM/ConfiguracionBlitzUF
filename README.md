![Banner](https://raw.githubusercontent.com/eduardohcDCM/ConfiguracionBlitzUF/refs/heads/main/assets/banner.png)


## 1. Objetivo

Este manual tiene como finalidad ayudarte a configurar tu dominio para que puedas utilizar **Blitz** como tu plataforma de e-commerce.

Esta configuración mantiene tu dominio como punto de acceso visible, pero todo el contenido y la lógica de negocio son gestionados por Blitz.

---

## 2. Requisitos para la conexión

Para que el equipo de **Blitz** pueda establecer correctamente la conexión con tu dominio, se deben seguir los siguientes pasos:

1. **Elegir un dominio o subdominio**: Puedes usar tu dominio principal o crear un subdominio.
2. **Apuntar el dominio a la IP de Blitz**: Debes crear un registro **A** en tu DNS que apunte a la IP de Blitz.
3. **Enviar un correo al equipo de Blitz**: Debes enviar un correo con la siguiente información:
   - Número de cliente.
   - Dominio o subdominio elegido.
   - Archivos del certificado SSL, comprimidos en un archivo `.zip` o `.rar`.
4. **Esperar confirmación del equipo de Blitz**: El equipo validará el contenido y el certificado. Si todo está correcto, se confirmará la conexión. En caso de errores, se te notificará para su corrección.

> [!IMPORTANT]  
> Esta es la IP a la que debes apuntar tu dominio o subdominio: `200.52.87.143`

> [!NOTE]  
> Envía la información solicitada a los correos disponibles en [Contacto](#6-contacto)

---

## 3. Requisitos técnicos del certificado SSL

El certificado SSL es fundamental para establecer una conexión segura entre tu dominio y Blitz. Asegúrate de cumplir con los siguientes requisitos:

- Archivo del certificado en formato `.crt` o `.pem`.
- Archivo de clave privada en formato `.key`.
- Emitido por una autoridad certificadora reconocida.
- Validez mínima de un año.
- Coincidencia exacta del nombre común (CN) con el dominio o subdominio configurado.

> [!WARNING]  
> Evita certificados autofirmados, mal emitidos o temporales (como los de Let's Encrypt).

### Ejemplo de estructura de los archivos del certificado

**Archivo .crt:**
```plaintext
-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----
```

**Archivo .key:**
```plaintext
-----BEGIN PRIVATE KEY-----
...
-----END PRIVATE KEY-----
```

---

## 4. Cómo apuntar el DNS a Blitz

Para apuntar tu dominio a Blitz, debes modificar el registro **A** en el panel de administración de DNS de tu proveedor de dominio. Aquí te explicamos cómo hacerlo:

1. Accede al panel DNS de tu proveedor de dominio.
2. Busca el registro **A** para el dominio o subdominio (por ejemplo, `tudominio.com` o `tienda.tudominio.com`).
3. Asigna como destino la siguiente IP: **200.52.87.143**.
4. Guarda los cambios y espera a que se propaguen.

Tu registro A debería verse así:

| Nombre | TTL  | Tipo | Registro       |
|--------|------|------|----------------|
| tudominio.com | 3600 | A    | 200.52.87.143 |

### 4.1 Verifiacion de DNS
Es importante que verifiques lo siguiente:

1. Debes tener un único registro A asociado al nombre de tu dominio o al símbolo @. Este registro debe apuntar a la IP de Blitz
2. No debes tener registros AAAA asociados al nombre de tu dominio ni al símbolo @, ya que actualmente no contamos con soporte para IPv6.
   

---

## 5. Preguntas y casos frecuentes

### 5.1. ¿Qué hacer si tu proveedor de SSL no te proporciona los archivos?

Si tu proveedor de SSL no te proporciona los archivos `.crt` y `.key`, no será posible establecer la conexión. En este caso, puedes considerar las siguientes opciones:

1. **Contactar a tu proveedor de SSL**: Pregunta si pueden proporcionarte los archivos necesarios.
2. **Cambiar de proveedor de SSL**: Busca un proveedor que ofrezca los archivos `.crt` y `.key` necesarios para la conexión.

> [!WARNING]  
> La mayoría de nuestros clientes utilizan **GoDaddy** como proveedor de SSL. Sin embargo, la elección del proveedor es responsabilidad del cliente. Asegúrate de que el proveedor que elijas cumpla con los requisitos técnicos mencionados anteriormente.

---

### 5.2. Mi proveedor de SSL requiere un .csr

El archivo `.csr` (Certificate Signing Request) es un archivo que contiene información sobre tu dominio y tu empresa. Se utiliza para solicitar un certificado SSL a una autoridad certificadora.  
En caso de que tu proveedor de SSL te pida un archivo `.csr`, puedes solicitarlo a nuestro equipo a través de los correos electrónicos de contacto.  
Se requiere enviar la siguiente información:

- Nombre de la empresa.
- Nombre del dominio o subdominio.
- Ciudad.
- Estado.
- País.
- Correo electrónico.

Una vez que recibas el archivo `.csr`, se recomienda que lo verifiques para asegurarte de que la información es correcta.  
Puedes hacerlo utilizando herramientas en línea como [CSR Decoder](https://www.sslshopper.com/csr-decoder.html).

> [!WARNING]  
> El nombre del dominio o subdominio debe coincidir exactamente con el que se utilizará para la conexión con Blitz.

---

### 5.3. Mi proveedor de SSL me pide agregar un registro TXT

Algunos proveedores de SSL requieren que agregues un registro TXT a tu DNS para verificar la propiedad del dominio antes de emitir el certificado. Si este es el caso, sigue estos pasos:

1. Accede al panel de administración de DNS de tu proveedor de dominio.
2. Crea un nuevo registro TXT.
3. Asigna el nombre y valor proporcionados por tu proveedor de SSL.
4. Guarda los cambios y espera a que se propaguen.
5. Una vez que el registro TXT esté activo, tu proveedor de SSL podrá verificar la propiedad del dominio y emitir el certificado.

> [!WARNING]  
> Verifica la documentación de tu proveedor de SSL para obtener instrucciones específicas sobre cómo agregar el registro TXT.

### 5.4. ¿Qué hacer si ya usas tu dominio principal?

Si tu dominio principal ya está en uso, puedes crear un **subdominio** para conectar con Blitz sin afectar tu sitio actual.

Ejemplos:
- `shop.midominio.com`
- `tienda.midominio.com`

Esto te permite usar Blitz de forma paralela a tu página web actual.

> [!NOTE]  
> Dependiendo de tu proveedor de dominio, puedes crear subdominios desde el panel de administración de DNS. En todo caso, se recomienda verificar la documentación de tu proveedor.

---

### 5.5. ¿Qué hacer si no tienes acceso al DNS?

Si no tienes acceso al DNS, puedes solicitar a tu proveedor de dominio que realice la configuración por ti. Proporciónales la IP de Blitz y pídeles que creen o editen el registro A correspondiente.

> [!NOTE]  
> Después de hacer los cambios, la propagación DNS puede tardar entre **15 minutos y 24 horas**.

Puedes verificar si el cambio ya está activo usando herramientas como:
- [dnschecker.org](https://dnschecker.org)

---

### 5.6. Mi dominio no resuelve en www
Si tu dominio funciona correctamente en tudominio.com pero no al usar www.tudominio.com, necesitas agregar un registro CNAME en el panel de DNS de tu proveedor.

1. Accede al panel de administración de DNS de tu proveedor de dominio.
2. Verifica si tienes un registro A con valo www o www.tudominio.com, si existe elmininalo.
3. Crea un nuevo registro CNAME y configuralo de la siguiente manera:
   
| Nombre | TTL  | Tipo | Registro       |
|--------|------|------|----------------|
| www | 3600 | CNAME   | tudominio.com |

> [!NOTE]  
> Recuerda sustituir los valores de ejemplo "tudominio.com" y/o "www.tudominio.com" por el valor real del dominio que haz adquirido.

---

## 6. Contacto

Si necesitas asesoría, puedes solicitar una conferencia con el equipo de Blitz a través de los siguientes correos electrónicos:

- Sistemas: [eduardo.hernandez@dcm.com.mx, robertoo@dcm.com.mx, sisweb01@dcm.com.mx]
- Administración: [arturo.martinez@dcm.com.mx, coord.mercadotecnia@dcm.com.mx, programador.uix@dcm.com.mx], tel: 55-5262-5700 ext: [2315, 2601, 2615]

