# Monitorización y gestión de procesos en Linux

## 🎯 Objetivo

Aprender a **identificar, monitorizar y gestionar procesos** en un sistema Linux utilizando los comandos:
- `ps`
- `top`
- `htop`
- `pstree`

---

## 🧱 Requisitos previos

- Sistema Linux (o WSL en Windows / terminal en macOS).
- Acceso a la terminal.
- Permisos de usuario y, opcionalmente, de superusuario (`sudo`).

---

## 🚀 Parte 1: Visualizar procesos con `ps`

### 🔹 1. Ver todos los procesos del usuario actual
```bash
ps
```

**Preguntas:**
- ¿Cuántos procesos aparecen?
- ¿Qué columnas muestra por defecto?

---

### 🔹 2. Ver todos los procesos del sistema
```bash
ps -e
```
o bien:
```bash
ps aux
```

**Tareas:**
- Identifica el **PID** del proceso de tu terminal (usa `tty` si lo necesitas).
- Localiza el **proceso del navegador o editor de texto** que estás usando.

---

### 🔹 3. Filtrar por nombre de proceso
```bash
ps -e | grep bash
```

**Tareas:**
- Busca todos los procesos relacionados con `ssh`, `python` o `chrome`.
- Explica qué significa cada columna (PID, TTY, TIME, CMD).

---

## ⚙️ Parte 2: Supervisar procesos en tiempo real con `top`

### 🔹 1. Ejecutar el comando
```bash
top
```

**Tareas:**
- Identifica el **proceso con más uso de CPU**.
- Cambia el orden para ver procesos con más **uso de memoria** (`Shift + M`).
- Cambia la frecuencia de actualización a 2 segundos (`d` y escribe `2`).

---

### 🔹 2. Finalizar un proceso desde `top`
1. Pulsa `k`
2. Introduce el **PID** de un proceso (por ejemplo, uno que no sea crítico).
3. Confirma con `Enter`.

**Pregunta:**  
¿Qué señal (signal) se envía por defecto? ¿Cuál se usaría para forzar la terminación?

---

## 💡 Parte 3: Supervisar con interfaz mejorada usando `htop`

### 🔹 1. Abrir `htop`
```bash
htop
```

**Tareas:**
- Ordena los procesos por **CPU**, **MEM**, y **TIME+**.
- Usa las **flechas de dirección** para navegar.
- Filtra procesos escribiendo `/` y el nombre del proceso.

### 🔹 2. Gestionar procesos desde `htop`
- Selecciona un proceso.
- Pulsa `F9` para **terminarlo**.
- Pulsa `F4` para **filtrar**.
- Pulsa `F2` para **personalizar columnas**.

**Explora:**  
- ¿Qué ventajas tiene `htop` frente a `top`?

---

## 🌳 Parte 4: Visualizar jerarquía con `pstree`

### 🔹 1. Ver la jerarquía completa
```bash
pstree
```

### 🔹 2. Mostrar PIDs
```bash
pstree -p
```

### 🔹 3. Mostrar solo procesos de tu usuario
```bash
pstree $USER
```

**Tareas:**
- Identifica qué procesos son hijos de tu shell (`bash` o `zsh`).
- ¿Qué ocurre si cierras un proceso padre?

---

## 🔧 Parte 5: Práctica combinada

1. Abre varios programas (navegador, editor, terminales).  
2. Usa `ps`, `top`, `htop` y `pstree` para:
   - Ver cuántos procesos están activos.
   - Identificar sus relaciones (padre/hijo).
   - Monitorizar consumo de CPU/memoria.
   - Finalizar un proceso controladamente.

---

## 🧠 Desafío extra

1. Lanza un proceso en segundo plano:
   ```bash
   sleep 500 &
   ```
2. Localízalo con `ps`, `htop` o `pstree`.
3. Termínalo usando `kill` con su **PID**.

---

## 🏁 Conclusiones

- `ps` → Muestra **instantánea estática** de procesos.  
- `top` → **Monitoriza en tiempo real**.  
- `htop` → Versión interactiva y visual de `top`.  
- `pstree` → Muestra **relaciones jerárquicas** entre procesos.  

