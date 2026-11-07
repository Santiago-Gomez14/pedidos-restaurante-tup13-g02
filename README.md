# Pedidos de un restaurante

Proyecto final de Programación 2 · UTN FRLP · TUP13, Grupo 2 · Proyecto 17.

El objetivo del sistema es registrar los pedidos de platos de las mesas de un restaurante. El proyecto se desarrolla con Python y Django.

## Apps y entidades

| App | Entidad | Datos principales |
| --- | --- | --- |
| `mesas` | `Mesa` | Número y capacidad |
| `platos` | `Plato` | Nombre, categoría y precio |
| `pedidos` | `Pedido` | Mesa, plato, cantidad y estado |

Cada pedido referencia una mesa y un plato. El alcance incluye alta, listado, detalle, modificación y baja de mesas y platos, y alta, listado y detalle de pedidos.

## Reglas de negocio

- La cantidad pedida debe ser mayor que cero.
- Una mesa cerrada no puede recibir pedidos.
- Los estados de un pedido deben seguir un orden fijo.

## Preparación del entorno en Windows

Usamos **Python 3.14.7** y **Django 5.2.19**. Para seguir estos pasos necesitás Git, PowerShell y Visual Studio Code.

### 1. Clonar y abrir el repositorio

Desde PowerShell, ubicado en la carpeta donde querés guardar el proyecto:

```powershell
git clone https://github.com/Santiago-Gomez14/pedidos-restaurante-tup13-g02.git
cd .\pedidos-restaurante-tup13-g02
code .
```

Si ya lo clonaste, abrí tu copia en VS Code. Si `code .` no se reconoce, abrí la carpeta desde **Archivo → Abrir carpeta**.

### 2. Verificar Python y crear el entorno virtual

En la terminal de PowerShell de VS Code, ejecutá:

```powershell
python --version
```

El resultado esperado es `Python 3.14.7`. Si todavía no existe `.venv` dentro del proyecto, crealo:

```powershell
python -m venv .venv
```

Cada integrante tiene su propio entorno virtual.

### 3. Instalar las dependencias

Desde la carpeta que contiene `requerimientos.txt`, ejecutá:

```powershell
.\.venv\Scripts\python.exe -m pip install -r requerimientos.txt
```

`pip` lee el archivo e instala la versión de Django indicada junto con sus dependencias. El comando usa directamente el Python de `.venv`.

### 4. Verificar las versiones

```powershell
.\.venv\Scripts\python.exe --version
.\.venv\Scripts\python.exe -m django --version
```

Los resultados esperados son `Python 3.14.7` y `5.2.19`, respectivamente.

## Trabajo con Git

Cada integrante trabaja en una rama con su nombre y apellido, en minúsculas,
sin espacios y separados por un guion. Por ejemplo, `santiago-gomez`.

### Crear tu rama por primera vez

Después de clonar el repositorio y antes de editar archivos, ejecutá:

```powershell
git switch main
git pull --ff-only
git switch -c nombre-apellido
git branch --show-current
```

Reemplazá `nombre-apellido` por tus datos. Los dos primeros comandos
te ubican en `main` y la actualizan con los cambios de GitHub. El tercero
crea tu rama y te cambia a ella. El último confirma en qué rama estás.

Si tu rama ya existe en tu computadora, entrá con `git switch nombre-apellido`.

### Compartir tus cambios

Después de hacer el primer commit en tu rama, subila a GitHub:

```powershell
git push -u origin nombre-apellido
```

Cuando el cambio esté listo para revisar, abrí un pull request desde tu rama
hacia `main`.

## Ejecutar el proyecto

Una vez que `manage.py` esté incorporado al repositorio, ejecutá estos comandos desde la carpeta que lo contiene:

```powershell
.\.venv\Scripts\python.exe manage.py migrate
.\.venv\Scripts\python.exe manage.py runserver
```

`migrate` aplica las migraciones a la base de datos local. `runserver` inicia el servidor de desarrollo. Abrí `http://127.0.0.1:8000/` en el navegador. Para detener el servidor, presioná `Ctrl + C` en la terminal.

## Ejecutar las pruebas

Cuando los tests estén incorporados, ejecutá desde la carpeta de `manage.py`:

```powershell
.\.venv\Scripts\python.exe manage.py test
```