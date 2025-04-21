## 1. Flujo general de conexión (explicación sencilla)

Este manual tiene como finalidad ayudarte a configurar tu dominio para que puedas utilizar **Blitz** como tu plataforma de e-commerce.

Esta configuración mantiene tu dominio como punto de acceso visible, pero todo el contenido y la lógica de negocio son gestionados por Blitz.

---

## 2. Requisitos para la conexión

Para que el equipo de **DCM** pueda establecer correctamente la conexión con tu dominio, se deben seguir los siguientes pasos:

1. **Elegir un dominio o subdominio**: Puedes usar tu dominio principal o crear un subdominio.
2. **Apuntar el dominio a la IP de Blitz**: Debes crear un registro A en tu DNS que apunte a la IP de Blitz.
3. **Enviar un correo al equipo de Blitz**: Debes enviar un correo con la siguiente información:
   - Número de cliente.
   - Dominio o subdominio elegido.
   - Archivos del certificado SSL, comprimidos en un archivo `.zip` o `.rar`.
4. **Esperar confirmación del equipo de Blitz**: El equipo validará el contenido y el certificado. Si todo está correcto, se confirmará la conexión. En caso de errores, se te notificará para su corrección.

> [!IMPORTANT]  
> Esta es la IP a la que debes apuntar tu dominio o subdominio: `200.52.87.143`

---

## 3. Requisitos técnicos del certificado SSL

El certificado SSL es fundamental para establecer una conexión segura entre tu dominio y Blitz. Asegúrate de cumplir con los siguientes requisitos:

- Certificado SSL válido y activo.
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
2. Crea o edita el registro **A**.
3. Busca el registro **A** para el dominio o subdominio (por ejemplo, `tudominio.com` o `tienda.tudominio.com`).
4. Asigna como destino la siguiente IP: **200.52.87.143**.
5. Guarda los cambios y espera a que se propaguen.

Tu registro A debería verse así:

| Nombre | TTL  | Tipo | Registro |
|--------|------|------|----------|
| tudominio.com | 3600 | A    | 200.52.87.143 |

---

## 5. ¿Qué hacer si ya usas tu dominio principal?

Si tu dominio principal ya está en uso, puedes crear un **subdominio** para conectar con Blitz sin afectar tu sitio actual.

Ejemplos:
- `shop.midominio.com`
- `tienda.midominio.com`

Esto te permite usar Blitz de forma paralela a tu página web actual.
>[!NOTE]
>Dependiendo de tu proveedor de dominio, puedes crear subdominios desde el panel de administración de DNS. En todo caso, se recomienda verificar la documentación de tu proveedor.

---

## 6. ¿Qué hacer si no tienes acceso al DNS?

Si no tienes acceso al DNS, puedes solicitar a tu proveedor de dominio que realice la configuración por ti. Proporciónales la IP de Blitz y pídeles que creen o editen el registro A correspondiente.

> [!NOTE]  
> Después de hacer los cambios, la propagación DNS puede tardar entre **15 minutos y 24 horas**.

Puedes verificar si el cambio ya está activo usando herramientas como:
- [dnschecker.org](https://dnschecker.org)

---

## 7. ¿Necesitas ayuda?

Si necesitas asesoría técnica, puedes comunicarte con nosotros:

- Correo: [correo@ejemplo.com]  
- Teléfono: [número de contacto]

