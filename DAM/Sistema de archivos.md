# 🧱  1 – Exploración del sistema de archivos
🎯 Objetivos

Conocer la estructura de directorios del sistema.

Buscar archivos, analizar espacio y permisos.

### Ejercicio Básico

Mostrar el directorio actual:

pwd


📘 Muestra la ruta completa donde te encuentras.

Listar los archivos con detalles:

ls -l


📘 Incluye permisos, propietario, tamaño y fecha.

Incluir archivos ocultos:

ls -la


Moverte a /etc y regresar a tu home:

cd /etc
ls
cd ~

### Ejercicio Avanzado

Ver estructura de carpetas hasta dos niveles:

tree -L 2 /


Buscar archivos de configuración:

find /etc -type f -name "*.conf"


Buscar archivos mayores de 100 MB:

sudo find / -type f -size +100M 2>/dev/null


Mostrar los 10 archivos más grandes:

sudo du -ah / | sort -rh | head -n 10


Ver permisos y propietarios de /var/log:

ls -lh /var/log


✅ Solución explicada:

find busca de forma recursiva por tipo y criterio.

du y sort ayudan a detectar qué consume más espacio.

2>/dev/null evita mostrar errores de permiso.




### Práctica: Comandos básicos de administración y gestión en Linux

### Objetivo

Aprender y practicar el uso de comandos esenciales para la administración, búsqueda, creación y gestión de archivos en sistemas Linux.

---

### 🧱 Requisitos previos

- Tener acceso a una terminal Linux (o WSL en Windows).
- Conocer los conceptos básicos de directorios y permisos.
- Acceso a usuario con privilegios de `sudo`.

---

### 🧩 Parte 1: Consultar ayuda y conocer el usuario actual

### 🔹 1. `man` — Manual de ayuda
Muestra el manual de cualquier comando.

```bash
man ls
```
Tareas:

Consulta el manual de grep.

Usa q para salir del manual.

Busca dentro del manual con /palabra.

💡 Tip: También puedes usar --help, por ejemplo:

```bash

ls --help
```
🔹 2. whoami — Mostrar el usuario actual
```bash

whoami
```
Tareas:

Muestra tu nombre de usuario actual.

Ejecuta el mismo comando con sudo whoami y observa la diferencia.

### Parte 2: Administración básica y control de comandos

🔹 3. sudo — Ejecutar como superusuario
```bash

sudo apt update
```
Tareas:

Intenta ejecutar un comando con sudo.

Observa cuándo pide contraseña.

Usa sudo -l para ver qué comandos puedes ejecutar como superusuario.

⚠️ Advertencia: Usa sudo con precaución. Puede modificar o borrar archivos del sistema.

🔹 4. history — Ver historial de comandos
```bash

history
```
Tareas:

Observa los últimos 10 comandos que ejecutaste.

Repite un comando con !n (por ejemplo, !15 ejecuta el número 15 del historial).

💡 Extra: Borra tu historial con:

```bash

history -c
```
🔹 5. clear — Limpiar la terminal
```bash

clear
```
o simplemente:

```bash
Ctrl + L
```
Tareas:

Limpia la pantalla después de listar muchos comandos.

### Parte 3: Archivos y texto
🔹 6. echo — Mostrar texto o variables
```bash

echo "Hola Mundo"
```
Tareas:

Crea un archivo nuevo con texto dentro:

```bash

echo "Mi primer archivo en Linux" > mensaje.txt
```
Agrega texto sin borrar el contenido:

```bash

echo "Línea añadida" >> mensaje.txt
```
🔹 7. touch — Crear archivos vacíos o actualizar fechas
```bash

touch notas.txt
```
Tareas:

Crea 3 archivos: a.txt, b.txt, c.txt.

Verifica su fecha de modificación con ls -l.

🔹 8. find — Buscar archivos
```bash

find /home -name "*.txt"
```
Tareas:

Busca todos los archivos .txt en tu directorio actual.

Busca un archivo por nombre exacto:

```bash

find . -name "notas.txt"
```
Busca por tipo:

```bash

find . -type d
```
🔹 9. grep — Buscar texto dentro de archivos
```bash

grep "Linux" mensaje.txt
```
Tareas:

Busca una palabra dentro de varios archivos:

```bash

grep "Hola" *.txt
```
Usa -i para ignorar mayúsculas/minúsculas.

Usa -r para buscar recursivamente en subdirectorios.

### 🧩 Parte 4: Lectura y visualización de archivos
🔹 10. head — Ver las primeras líneas de un archivo
```bash

head mensaje.txt
```
Tareas:

Muestra las primeras 5 líneas:

```bash

head -n 5 mensaje.txt
```
🔹 11. tail — Ver las últimas líneas de un archivo
```bash

tail mensaje.txt
```
Tareas:

Muestra las últimas 10 líneas:

```bash

tail -n 10 mensaje.txt
```
Observa un archivo en tiempo real (útil para logs):

```bash

tail -f /var/log/syslog
```
### 🧩 Parte 5: Espacio en disco y permisos
🔹 12. df — Mostrar uso del disco
```bash

df -h
```
Tareas:

Observa los sistemas de archivos montados.

Identifica el espacio libre y ocupado.

💡 Usa la opción -h para ver los tamaños en formato legible (MB/GB).

🔹 13. du — Mostrar uso de espacio por directorio
```bash

du -h --max-depth=1
```
Tareas:

Ejecuta du -sh * para ver el tamaño de cada carpeta.

Encuentra la carpeta que más ocupa espacio.

🔹 14. chmod — Cambiar permisos de archivos
```bash

chmod 755 script.sh
```
Tareas:

Crea un archivo prueba.sh y dale permiso de ejecución:

```bash

touch prueba.sh
chmod +x prueba.sh
```
Quita permiso de lectura:

```bash

chmod -r prueba.sh
```
Comprueba los permisos con ls -l.

💡 Ejemplo de permisos:

ini

r = read (leer)
w = write (escribir)
x = execute (ejecutar)

### 🧠 Desafío final
Crea un archivo llamado reporte.txt con información del sistema:

```bash

echo "Usuario: $(whoami)" > reporte.txt
df -h >> reporte.txt
du -sh * >> reporte.txt
```
Busca la palabra “home” dentro del archivo con grep.

Muestra solo las primeras 10 líneas con head.


Con estos comandos dominarás la gestión básica de archivos, permisos y análisis del sistema en Linux. 🚀