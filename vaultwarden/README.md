#  Vaultwarden (alternativa ligera a Bitwarden)

Vaultwarden es un servidor de contraseñas seguro y eficiente que se ejecuta en contenedores Docker. Es ideal para uso personal o como bóveda de credenciales compartidas dentro de equipos técnicos.

Carpeta: `vaultwarden/`

Incluye:

- `docker-compose.yml`
- `.env.example` (para variables sensibles)
- Instrucciones de despliegue
- Buenas prácticas mínimas de seguridad

###  Despliegue rápido

1. Clona el repositorio:

```
git clone https://github.com/rittercortez/devops-toolkit.git
cd devops-toolkit/vaultwarden
```

2. Crea el archivo `.env` a partir del ejemplo:

```
cp .env.example .env
```

3. Genera un token de administrador seguro (opcional pero recomendado):

```
argon2 "tu_contraseña_segura" -id -e
```

**Importante:** Reemplaza el primer `$` por `$$` al colocarlo en `.env`:

```
ADMIN_TOKEN=$$argon2id...
```

4. Levanta el contenedor:

```
docker-compose up -d
```

5. Accede a Vaultwarden en tu navegador: `http://localhost:8080`

---

### Uso en producción

Si deseas usarlo en producción:

- Coloca Vaultwarden detrás de un proxy reverso como Apache2 o NGINX.
- Configura HTTPS con Let's Encrypt o certificados propios.
- Usa almacenamiento persistente y backup de la carpeta `/data`.

Cada entorno de producción puede variar, así que no se incluye una configuración fija de proxy.

---
