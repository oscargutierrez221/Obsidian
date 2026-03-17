# Introducción a repositorios
## ¿Qué son los Repositorios?
Un **repositorio** es como una carpeta especial que guarda todo el historial de cambios de tu proyecto. Imagina que es un álbum de fotos donde cada foto representa una versión diferente de tu código. Puedes ver cómo era tu proyecto hace una semana, un mes o un año, y si algo se rompe, puedes volver atrás en el tiempo.

## ¿Qué es Git?
**Git** es un sistema de control de versiones distribuido. En palabras simples:
- Es una herramienta que instalas en tu computadora
- Te permite guardar "fotografías" (llamadas *commits*) de tu código en diferentes momentos
- Puedes trabajar en diferentes versiones de tu proyecto al mismo tiempo (usando *ramas* o *branches*)
- Si cometes un error, puedes volver a una versión anterior
- Facilita el trabajo en equipo, ya que varias personas pueden trabajar en el mismo proyecto sin pisarse

**Analogía:** Git es como tener un botón de "guardar" super poderoso que no solo guarda tu trabajo actual, sino que también recuerda todas las versiones anteriores.

## ¿Qué es GitHub?
**GitHub** es una plataforma en la nube (un sitio web) donde puedes:
- Subir tus repositorios de Git para tenerlos respaldados en Internet
- Compartir tu código con otras personas
- Colaborar en proyectos de código abierto
- Mostrar tu portafolio de proyectos a empleadores

**Analogía:** Si Git es tu álbum de fotos personal, GitHub es como Instagram o Google Photos donde subes ese álbum para compartirlo, respaldarlo y colaborar con otros.

### Diferencia clave:
- **Git** = La herramienta (software en tu computadora)
- **GitHub** = El servicio en la nube (sitio web)
---
## Comandos Básicos de Git

A continuación, una tabla con los comandos esenciales para crear un repositorio y subirlo a GitHub:

| Comando                       | Descripción                                                                   | Cuándo usarlo                                                            |
| ----------------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| `git init`                    | Inicializa un nuevo repositorio Git en la carpeta actual                      | Al comenzar un nuevo proyecto                                            |
| `git clone <url>`             | Descarga un repositorio existente desde GitHub                                | Para trabajar en un proyecto que ya existe en GitHub                     |
| `git status`                  | Muestra el estado actual de los archivos (modificados, sin seguimiento, etc.) | Para ver qué archivos han cambiado                                       |
| `git add <archivo>`           | Agrega un archivo específico al área de preparación                           | Antes de hacer commit de cambios específicos                             |
| `git add .`                   | Agrega todos los archivos modificados al área de preparación                  | Cuando quieres guardar todos los cambios                                 |
| `git commit -m "mensaje"`     | Guarda los cambios con un mensaje descriptivo                                 | Después de `git add`, para crear un punto de guardado                    |
| `git remote add origin <url>` | Conecta tu repositorio local con uno en GitHub                                | La primera vez que vinculas tu proyecto con GitHub                       |
| `git push -u origin main`     | Sube tus cambios a GitHub (primera vez)                                       | Para enviar tu código a GitHub por primera vez                           |
| `git push`                    | Sube los cambios al repositorio remoto                                        | Cada vez que quieras actualizar GitHub con tus cambios                   |
| `git pull`                    | Descarga los cambios del repositorio remoto                                   | Para actualizar tu copia local con cambios de otros                      |
| `git branch`                  | Muestra las ramas disponibles                                                 | Para ver en qué rama estás trabajando                                    |
| `git checkout -b <nombre>`    | Crea y cambia a una nueva rama                                                | Para trabajar en una nueva funcionalidad sin afectar el código principal |

---
## Flujo Básico: Crear y Subir un Repositorio a GitHub

### Paso 1: Crear el repositorio en GitHub
1. Ve a [github.com](https://github.com) y crea una cuenta si no tienes
2. Haz clic en el botón **"+"** → **"New repository"**
3. Dale un nombre a tu repositorio
4. Haz clic en **"Create repository"**
### Paso 2: En tu computadora (terminal/consola)

```bash
# 1. Navega a la carpeta de tu proyecto
cd ruta/de/tu/proyecto

# 2. Inicializa Git
git init

# 3. Agrega todos los archivos
git add .

# 4. Haz tu primer commit
git commit -m "Primer commit"

# 5. Conecta con GitHub (reemplaza con tu URL)
git remote add origin https://github.com/tu-usuario/tu-repositorio.git

# 6. Sube los archivos a GitHub
git push -u origin main

```

### Paso 3: Para cambios futuros

```bash
# 1. Agrega los archivos modificados
git add .

# 2. Haz commit con un mensaje descriptivo
git commit -m "Descripción de los cambios"

# 3. Sube a GitHub
git push
```

---
## Consejos Importantes
- **Mensajes de commit claros:** Escribe mensajes que expliquen QUÉ cambiaste y POR QUÉ
- ✅ Bueno: `"Agrega validación de email en el formulario de registro"`
- ❌ Malo: `"cambios"` o `"fix"`
- **Commits frecuentes:** Haz commits pequeños y frecuentes en lugar de uno grande al final del día
- **Archivo .gitignore:** Crea un archivo `.gitignore` para evitar subir archivos innecesarios (como contraseñas, archivos temporales, etc.)