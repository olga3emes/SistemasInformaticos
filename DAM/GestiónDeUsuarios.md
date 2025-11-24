# 🧭 Guía Completa de Administración de Usuarios, Grupos y Permisos en Linux


### 🧑‍💻 1. Crear un usuario

```bash
sudo adduser juan
```
Esto crea:

  -  El usuario juan

  -  Su carpeta personal /home/juan

  -  Su grupo primario juan

   - También puedes usar useradd de forma más básica:

```bash

sudo useradd -m -s /bin/bash juan
sudo passwd juan
```
###  👥 2. Crear un grupo nuevo
```bash
sudo groupadd desarrolladores
```
Verifica que se haya creado:

```bash
getent group desarrolladores
```
### ➕ 3. Agregar un usuario a un grupo
```bash
sudo usermod -aG desarrolladores juan
```
⚠️ Usa -aG para agregar sin eliminar grupos existentes.
Comprobar los grupos a los que pertenece:

```bash
groups juan
```


### 🗑️ 4. Eliminar usuario o grupo
Eliminar un usuario sin borrar su carpeta personal:

```bash
sudo deluser juan
```
Eliminar también su carpeta /home:

```bash
sudo deluser --remove-home juan
```
Eliminar un grupo:

```bash
sudo groupdel desarrolladores
```
### 🔐 5. Asignar o cambiar contraseñas
```bash
sudo passwd juan
```
### ⚙️ 6. Ver información detallada
Información del usuario:

```bash
id juan
```
Información de un grupo:

```bash
getent group desarrolladores
```
### 📁 7. Permisos de archivos y directorios
Cada archivo/directorio tiene tres tipos de permisos para tres categorías de usuarios:

Categoría	Descripción
u --> Usuario propietario
g -->	Grupo propietario
o -->	Otros usuarios

Tipos de permiso:

Permiso	Archivos	Directorios
r	Leer	Listar contenido
w	Modificar	Crear o eliminar archivos
x	Ejecutar	Entrar al directorio

### 🔍 8. Ver permisos de un archivo
```bash
ls -l
```
Ejemplo:

```bash
-rw-r--r-- 1 juan desarrolladores 1234 oct 10 archivo.txt
```
Interpretación:

rw- → usuario puede leer y escribir

r-- → grupo puede leer

r-- → otros solo leen

### ✏️ 9. Cambiar propietario o grupo de un archivo
Cambiar propietario:

```bash
sudo chown juan archivo.txt
```
Cambiar grupo:

```bash
sudo chgrp desarrolladores archivo.txt
```
Cambiar ambos:

```bash
sudo chown juan:desarrolladores archivo.txt
```
### 🧮 10. Cambiar permisos
Modo simbólico
```bash
chmod u+rwx archivo.txt   # Dar permisos al usuario
chmod g-w archivo.txt     # Quitar escritura al grupo
chmod o-r archivo.txt     # Quitar lectura a otros
```
Modo numérico

Permiso	Valor
r	4
w	2
x	1

Ejemplo:

```bash
chmod 750 archivo.txt
```
Significa:

- 7 (4+2+1) → usuario: rwx

- 5 (4+1) → grupo: r-x

- 0 → otros: sin acceso

### 📂 11. Permisos recursivos
Aplicar permisos a todos los archivos y subcarpetas:

```bash
chmod -R 750 /ruta/a/carpeta
chown -R juan:desarrolladores /ruta/a/carpeta
```
### 🏷️ 12. Permisos especiales (avanzado)
🔹 setgid (mantener grupo en nuevas carpetas)
```bash
chmod g+s /proyectos
```
Verás una s en los permisos:

drwxr-sr-x
🔹 setuid
Permite que un programa se ejecute con los privilegios del propietario.

🔹 Sticky bit (típico en /tmp)
Solo el propietario puede borrar sus archivos:

```bash
chmod +t /carpeta_compartida
```
Permisos se verán como drwxrwxrwt.

### 🧰 13. Ejemplo práctico completo
```bash
# Crear grupo y usuario
sudo groupadd seguridad
sudo adduser ana

# Añadir usuario al grupo
sudo usermod -aG seguridad ana

# Crear carpeta y asignar propietario y permisos
sudo mkdir /seguridad
sudo chown root:seguridad /seguridad
sudo chmod 770 /seguridad

# Activar herencia de grupo
sudo chmod g+s /seguridad

# Verificar
ls -ld /seguridad
```
Resultado esperado:

```bash
drwxrws--- 2 root seguridad 4096 oct 10 /seguridad
```
Solo root y los usuarios del grupo seguridad pueden acceder.