# Manual de Instalación de Samba en Ubuntu Server 24.04.4 (Adaptado a Hotel)

## 1. Requisitos Previos

- Ubuntu Server 24.04.4 actualizado
- Usuario con privilegios `sudo`
- OpenLDAP instalado (opcional si se desea integración de usuarios centralizada)
- Apache, MySQL, PHP (si se integra con otros servicios)

Actualizar sistema:

```bash
sudo apt update && sudo apt upgrade -y
```

Instalar dependencias:

```bash
sudo apt install samba smbclient cifs-utils -y
```

---

## 2. Crear Carpetas Compartidas por Departamento

Se simula la estructura de un hotel según organigrama:

```bash
sudo mkdir -p /srv/samba/recepcion
sudo mkdir -p /srv/samba/administracion
sudo mkdir -p /srv/samba/mantenimiento
sudo mkdir -p /srv/samba/direccion
```

Asignar permisos básicos (propietario: root, grupo: correspondiente al departamento):

```bash
sudo groupadd Recepcion
sudo groupadd Administracion
sudo groupadd Mantenimiento
sudo groupadd Direccion

sudo chown :Recepcion /srv/samba/recepcion
sudo chown :Administracion /srv/samba/administracion
sudo chown :Mantenimiento /srv/samba/mantenimiento
sudo chown :Direccion /srv/samba/direccion

sudo chmod 770 /srv/samba/recepcion
sudo chmod 770 /srv/samba/administracion
sudo chmod 770 /srv/samba/mantenimiento
sudo chmod 770 /srv/samba/direccion
```

---

## 3. Configuración Principal de Samba

Editar archivo de configuración:

Archivo: `/etc/samba/smb.conf`

```ini
[global]
   workgroup = HOTEL
   server string = Servidor Hotel
   security = user
   map to guest = Bad User
   dns proxy = no

# Comparticiones por departamentos
[Recepcion]
   path = /srv/samba/recepcion
   browsable = yes
   writable = yes
   valid users = @Recepcion
   create mask = 0660
   directory mask = 0770

[Administracion]
   path = /srv/samba/administracion
   browsable = yes
   writable = yes
   valid users = @Administracion
   create mask = 0660
   directory mask = 0770

[Mantenimiento]
   path = /srv/samba/mantenimiento
   browsable = yes
   writable = yes
   valid users = @Mantenimiento
   create mask = 0660
   directory mask = 0770

[Direccion]
   path = /srv/samba/direccion
   browsable = yes
   writable = yes
   valid users = @Direccion
   create mask = 0660
   directory mask = 0770
```

---

## 4. Crear Usuarios Samba

Si se integran usuarios locales:

```bash
sudo useradd -M -s /sbin/nologin jgomez
sudo useradd -M -s /sbin/nologin mperez

sudo passwd jgomez
sudo passwd mperez
```

Asignar usuarios a grupos de departamentos:

```bash
sudo usermod -aG Recepcion jgomez
sudo usermod -aG Administracion mperez
```

Añadir usuarios a Samba:

```bash
sudo smbpasswd -a jgomez
sudo smbpasswd -a mperez
sudo smbpasswd -e jgomez
sudo smbpasswd -e mperez
```

---

## 5. Reiniciar Samba y Comprobar Estado

```bash
sudo systemctl restart smbd nmbd
sudo systemctl status smbd
```

---

## 6. Acceso desde Clientes

Desde un cliente Windows o Linux:

```
\\IP_SERVIDOR\Recepcion
\\IP_SERVIDOR\Administracion
\\IP_SERVIDOR\Mantenimiento
\\IP_SERVIDOR\Direccion
```

- Usuario y contraseña según departamento
- Permisos restringidos según grupo

---

## 7. Integración Opcional con LDAP

Si se desea integración con OpenLDAP:

1. Instalar soporte:

```bash
sudo apt install libnss-ldap libpam-ldap smbldap-tools -y
```

2. Configurar Samba para autenticación LDAP:

Archivo: `/etc/samba/smb.conf` → sección `[global]`:

```ini
security = user
passdb backend = ldapsam:ldap://127.0.0.1
ldap admin dn = cn=admin,dc=hotel,dc=local
ldap suffix = dc=hotel,dc=local
ldap user suffix = ou=Users
ldap group suffix = ou=Groups
```

3. Reiniciar servicios:

```bash
sudo systemctl restart smbd nmbd
```

---

## 8. Archivos y Directorios Importantes

- `/etc/samba/smb.conf` → Configuración principal
- `/srv/samba/` → Carpetas compartidas
- `/var/log/samba/` → Logs de Samba
- `/etc/samba/smbpasswd` → Usuarios locales de Samba

---

## 9. Verificaciones

- Acceso a cada carpeta según grupo
- Permisos de lectura/escritura correctos
- Clientes Windows/Linux pueden conectarse
- Logs libres de errores

---

## 10. Notas de Seguridad

- Limitar acceso solo a red interna
- Usar grupos para permisos por departamento
- Actualizar Samba regularmente
- Integrar autenticación LDAP para entornos empresariales
