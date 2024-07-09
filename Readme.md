# git Guide

En el presente informe, voy a realizar una guía básica y detallada sobre cómo utilizar las ramas de GitHub. En esta guía, vamos a profundizar en la comprensión del uso de git, explorando sus múltiples funcionalidades y beneficios. 

❓¿Qué es GitHub?

✅ GitHub es una plataforma de desarrollo colaborativo que utiliza el sistema de control de versiones Git. Permite a los desarrolladores trabajar juntos en proyectos, gestionar versiones de código, y realizar seguimientos de cambios de manera eficiente.

# Introducción

Estamos considerando que el lector ya tiene una cuenta de GitHub creada y debidamente configurada en la terminal de su computadora. Esto incluye haber registrado una cuenta en el sitio web de GitHub, haber confirmado su dirección de correo electrónico y haber instalado y configurado Git en su sistema. Además, se espera que el lector haya generado y añadido su clave SSH a su cuenta de GitHub para facilitar la autenticación segura y sin problemas al interactuar con los repositorios remotos.

# Paso 1: Creación del repositorio

Para este primer paso vamos a crear un repositorio vacio desde cero llamado [**GitHub-Guide](https://github.com/Defiant7426/GitHub-Guide):**

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled.png)

En este repositorio vamos a crear un archivo Python `example.py` con el siguiente contenido:

```python
# example.py
def greet():
    return "Hello, GitHub!"

if __name__ == "__main__":
    print(greet())
```

Este es un script sencillo donde  definimos una función `greet` que retorna un saludo. Si ejecutamos este archivo, la función `greet` se llamará y el mensaje "Hello, GitHub!" se imprimirá en la consola.

## Subimos el archivo al repositorio

Para subir el archivo al repositorio, primero asegúrate de estar en el directorio de tu proyecto en la terminal. Una vez creado el archivo y agregado en el directorio del proyecto escribimos el siguiente comando:

```python
git status
```

Aparecerá el siguiente mensaje:

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%201.png)

Esto significa que el archivo `example.py` ha sido creado pero aún no está siendo rastreado por Git. Para agregarlo, utilizamos el siguiente comando:

```bash
git add example.py
```

Esto preparará el archivo para el commit.

Si volvemos a escribir el comando de `git status` nos aparecerá el siguiente mensaje:

```python
KATANA@DESKTOP-MN7RMI8 MINGW64 ~/Desktop/git/Personal/GitHub-Guide (main)
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   example.py
```

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%202.png)

Esto significa que el archivo está listo para ser comiteado. El siguiente paso es realizar el commit con el siguiente comando:

```bash
git commit -m "Add example.py"
```

Este comando creará un commit con el mensaje "Add [example.py](http://example.py/)", guardando así los cambios en el historial del repositorio.

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%203.png)

El último paso para subir el archivo al repositorio remoto es utilizar el siguiente comando:

```bash
git push origin main
```

Este comando enviará los cambios al repositorio en GitHub, haciendo que `example.py` esté disponible en la rama principal.

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%204.png)

Al actualizar nuestro repositorio debemos de ver el archivo `example.py` 

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%205.png)

# Paso 2: Realizando varios commit sobre la misma rama

Vamos a agregarle una funcion a nuestro archivo `example.py`.Añadimos la siguiente función:

```python
def farewell():
    return "Goodbye, GitHub!"

if __name__ == "__main__":
    print(greet())
    print(farewell())

```

Al guardar los cambios veamos el estado de nuestro repositorio usando el comando `git status`

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%206.png)

## Realizando el primer commit

Veremos que `example.py` ha sido modificado. Para preparar estos cambios para el commit, usaremos nuevamente `git add example.py`. Posteriormente, realizamos el commit con `git commit -m "Add farewell function to example.py"`.

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%207.png)

Ahora vamos a crear otra función a nuestro archivo:

Añadimos la siguiente función:

```python
def ask_name():
    return "What is your name?"

if __name__ == "__main__":
    print(greet())
    print(farewell())
    print(ask_name())
```

Guardamos los cambios y verificamos el estado del repositorio con `git status`.

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%208.png)

## Realizando el segundo commit

Veremos que `example.py` ha sido nuevamente modificado. Para preparar estos cambios para el commit, usaremos `git add example.py`. Posteriormente, realizamos el commit con `git commit -m "Add ask_name function to example.py"`.

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%209.png)

Si usamos otra vez el comando de `git status` entonces la salida es la siguiente:

```python
KATANA@DESKTOP-MN7RMI8 MINGW64 ~/Desktop/git/Personal/GitHub-Guide (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

Esto significa que tenemos dos commits en nuestra rama principal que aún no han sido empujados al repositorio remoto. 

## Revisamos los logs del repositorio

Usamos el comando `git log`. Este comando mostrará un historial de los commits realizados, permitiéndonos ver detalles como el autor, la fecha y el mensaje de cada commit.

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2010.png)

En esta salida se lee desde abajo hacia arriba. Cada commit tiene su hash, el autor, la fecha en que se subió al repositorio y el mensaje que le dimos en cada commit.

## Creamos otro archivo en el mismo directorio

Vamos a crear un archivo llamado `info.txt` y le añadimos el siguiente contenido:

```
Este es un archivo de información adicional para el proyecto GitHub Guide.
```

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2011.png)

Luego seguimos los mismos pasos: `git add info.txt`, `git commit -m "Add info.txt"`

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2012.png)

# Paso 3: Regresando a un commit anterior

Veamos los logs que se crearon en nuestro repositorio:

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2013.png)

Para regresar a un commit anterior, podemos usar el comando `git checkout`. Por ejemplo, si queremos regresar al commit con el mensaje "Add farewell function to [example.py](http://example.py/)", usamos el siguiente comando:

```bash
git checkout 4adfd5ce4b3503ccad7b2a3155d0ca1f98f064a8
```

<aside>
💡 Notamos que cada vez que cambiamos de commit, también se refleja en nuestro directorio local. Esto es útil cuando queramos deshacer desde un punto de inflexión de un commit.

</aside>

Nos saldra el siguiente mensaje:

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2014.png)

Ahora vamos a hacer que el commit actual sea nuestra cabecera.

```bash
git checkout HEAD
```

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2015.png)

Si queremos regresar desde despues de que info.txt fue creado podemos hacer:

```python
git checkout f1ff929024d8663088e21b0d47f659ab8839736e
```

El hash `f1ff929024d8663088e21b0d47f659ab8839736e` es del commit cuando se agrego el archivo `info.txt` . Ahora vamos a al commit  `c2f1a096a56cd3b996558552e29d5056eff67a63` Y vamos a hacer un push hacia nuestro repositorio:

```bash
git checkout c2f1a096a56cd3b996558552e29d5056eff67a63
git push origin main
```

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2016.png)

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2017.png)

Como vemos, el comando empujó todos los commits, pero nuestra intención era que solo empujara los commits hasta el commit actual. Como queremos que se empuje todo hasta nuestro commit actual y elimine los commits posteriores a el entonces hacemos:

```bash
git push --force origin c2f1a096a56cd3b996558552e29d5056eff67a63:main

```

Este comando forzará el empuje y alineará el historial del repositorio remoto con el commit especificado, eliminando los commits posteriores.

## Eliminando un commit

Rara vez vamos a eliminar un commit pero puede suceder, para lograr ello solo hariamos:

```python
git reset --hard f1ff929
```

Si bien es cierto este comando puede eliminar el comit especificado y los posteriores. Este comando funciona tanto para adelante como para atrás, pues puede “eliminar” o recuperar una vez eliminado el commit especificado

# Paso 4: Uso del tag

Para crear un tag en Git, usamos el siguiente comando:

```bash
git tag -a v1.0 -m "Versión inicial del proyecto"
```

Esto creará un tag anotado con el mensaje "Versión inicial del proyecto". Podemos listar los tags creados usando el comando:

```python
git tag
```

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2018.png)

Podemos dirigirnos hacia esta tag usando el `checkout`

```python
git checkout v1.0
```

## Cuidado con las referencias del log

En el paso anterior, creamos una etiqueta con el nombre `v1.0`. Al ejecutar el comando `git checkout v1.0`, nos llevó a la versión del commit donde agregamos la etiqueta con ese nombre. Pero antes de hacer eso, creamos un archivo [`example2.py`](http://example2.py/). Entonces, el commit con la etiqueta `v1.0` es nuestro penúltimo commit, no el último. Si ejecutamos el comando `git log`, veremos lo siguiente:

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2019.png)

Estamos notando que tanto el repositorio remoto como el head se encuentan en el commit con tag `v1.0` pero no esta el ultimo commit ¿A donde se fue?

A pesar de no aparecer el ultimo commit se encuentra ahi, para dirigirnos a el solo hacemos:

```python
git checkout 9f81613
```

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2020.png)

Esta imagen es interesante. Trataremos de explicar lo que ocurre. A pesar de que el commit `9f816113` sea el último, notamos que en `origin/main` se encuentra el commit del `tag: v1.0`. Esto sucede porque en nuestro repositorio remoto, el main está justo donde se encuentra nuestro local, mientras que en nuestra máquina local tenemos un head que todavía no hemos pusheado.

Para solucionar esto podemos ejecutar los siguientes comandos:

```python
git checkout main
git rebase 9f81613 
```

Esto alineará nuestro repositorio local con el commit más reciente. Luego, podemos hacer un push para que nuestro repositorio remoto también esté actualizado:

```bash
git push origin main
```

Si ejecutamos `git log` ahora la salida sera:

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2021.png)

## Pushear un tag

Para enviar un tag al repositorio remoto, usamos el siguiente comando:

```bash
git push origin v1.0

```

Este comando empujará la etiqueta `v1.0` al repositorio remoto, haciendo que esté disponible junto con el historial del proyecto.

Tambien podemos usar el comando

```python
git push --force origin v1.0
```

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2022.png)

# Paso 5: Rama o Branch de git

Las ramas en Git son fundamentales para el desarrollo colaborativo, ya que permiten trabajar en funciones o correcciones de forma aislada. 

❓ ¿Qué significa “crear una rama”?

✅ Crear una rama significa hacer una copia del proyecto en su estado actual para trabajar en ella sin afectar la rama principal. Esto permite desarrollar nuevas características o corregir errores de manera aislada antes de fusionar los cambios con la rama principal.

## Creando una rama

Supongamos que estamos trabajando en un proyecto web y quiero agregar una nueva funcionalidad a mi página, por ejemplo, crear el login. Entonces, creamos la rama para poder trabajar con este comando:

```python
git branch login
```

## Cambiar entre ramas

Para cambiar a la nueva rama, utilizamos el comando:

```bash
git switch login
```

Esto nos permite trabajar en la funcionalidad de login sin afectar la rama principal. Si ejecutamos el comando `git log` la salida es la siguiente:

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2023.png)

La cabecera se movió con el main hacia la rama login.

❓¿Que significa trabajar ahora en la rama login?

✅ Trabajar en la rama login significa que cualquier cambio que hagamos se aplicará solo a esta rama, permitiendo desarrollar y probar la nueva funcionalidad de login de manera segura y aislada. Esto nos protege de posibles errores o conflictos en la rama principal mientras la nueva característica está en desarrollo.

Suponiendo que terminamos de desarrollar nuestro login en esta rama, para ello creamos un archivo [`login.py`](http://login.py) en nuestro directorio de trabajo con el siguiente contenido:

```python
print("login")
```

Ahora podemos seguir los pasos que aprendimos:

```bash
git status
git add .
git commit -m "Add login"
```

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2024.png)

El nuevo commit tiene un id de `f5a8c3e` y se encuentra en la rama login (independientemente a main)

Si cambiamos de rama de nuevo a la main entonces:

```bash
git switch main
```

Veremos que el archivo `login.py` no estará presente, ya que pertenece solo a la rama `login`.

Vamos a realizar un cambio desde la rama main de cualquier archivo, entonces realizamos los mismo pasos anteriores para crear un nuevo commit pero ahora desde la main

```bash
git status
git add .
git commit -m "Add login"
```

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2025.png)

Regresamos a la rama login y verificamos que los cambios realizados en `main` no afectan a `login`. Esto confirma que cada rama puede evolucionar de manera independiente.

## Git merge

❓¿Para que queremos hacer un marge entre dos ramas?

✅ Hacer un merge permite unificar el trabajo de diferentes ramas, asegurando que las nuevas funcionalidades o correcciones desarrolladas en una rama se integren correctamente en la rama principal.

Para combinar los cambios de una rama en otra, utilizamos el comando `git merge`. Primero, nos aseguramos de estar en la rama donde queremos fusionar los cambios:

```bash
git switch login
git merge main
```

Esto integrará los cambios de la rama `main` en la rama `login`. Al ejecutar el marge aparecera el siguiente mensaje:

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2026.png)

Esto confirma que la rama `login` ahora incluye los cambios realizados en `main`. Si cambiamos nuevamente a `main`, veremos que los cambios de `login` no se reflejan hasta que hagamos un merge en la dirección opuesta.

Podemos apretar la tecla `Esc` y luego escribir `:!q` o `:wq` para salir de la consola de vim. 

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2027.png)

El merge fue un éxito, así es cuando no hay conflictos entre ramas y ambas se pueden integrar entre sí.

## Resolución de conflictos en Git

A veces, cuando se intenta fusionar dos ramas, puede haber conflictos si las mismas líneas de código han sido modificadas en ambas ramas. Git nos notificará de estos conflictos y nos permitirá resolverlos manualmente. Para resolver un conflicto, editamos los archivos afectados, solucionamos las diferencias y luego usamos `git add` y `git commit` para completar la fusión.

Vamos a editar el mismo archivo tanto en la rama login como en la rama main, para ello alteramos de alguna forma el archivo [`example3.py`](http://example3.py) y lo comitiamos en la rama login

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2028.png)

Ahora vamos a hacer lo mismo en la rama main, pero con una implementacion diferente en [`exaple3.py`](http://exaple3.py) 

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2029.png)

Ahora si nos vamos a la rama login y queremos hacer merge de nuevo nos saldra el siguiente mensaje:

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2030.png)

El archivo `example3.py` tiene conflictos que necesitan ser resueltos manualmente. Para resolver el conflicto, abrimos el archivo en un editor de texto, buscamos las secciones marcadas por Git y elegimos qué cambios mantener. Después de resolver los conflictos, guardamos el archivo, usamos `git add example3.py` y luego `git commit` para completar la fusión.

Al abrir el archivo `example3.py` Notamos lo siguiente

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2031.png)

Aquí Git nos está especificando que las líneas HEAD son las nuestras y que se encuentran en login, mientras que las líneas de abajo son del main. Esto sucede cuando alteramos la misma línea del mismo archivo en diferentes ramas. Supongamos que queremos quedarnos con el cambio del main en ese archivo. Entonces, alteramos el archivo de esta manera:

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2032.png)

Ahora vamos a realizar un nuevo comit con los cambios pertinentes

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2033.png)

## Git stash

El comando `git stash` permite guardar temporalmente los cambios no confirmados en el área de trabajo para poder trabajar en otra cosa y luego recuperarlos. Por ejemplo, si necesitamos cambiar de rama pero no queremos perder los cambios actuales, usamos `git stash` para almacenarlos.

Por ejemplo, si estamos trabajando en la rama login y tenemos un código incompleto con errores, pero a la vez queremos movernos entre ramas por alguna razón, si intentamos hacer eso sin realizar un commit antes, Git nos avisará de esta manera:

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2034.png)

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2035.png)

Para guardar los cambios sin comitear, usamos el comando `git stash`:

```bash
git stash

```

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2036.png)

Luego podemos cambiar de rama libremente y recuperar los cambios más tarde con `git stash pop`.

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2037.png)

También es posible eliminar el stash de la siguiente manera:

```bash
git stash drop
```

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2038.png)

## Reintegración de ramas en Git

### git diff

Para comparar los cambios entre dos ramas, usamos el comando `git diff`. Por ejemplo, para ver las diferencias entre la rama `main` y la rama `login`, ejecutamos:

```bash
git diff login
```

Esto nos mostrará las diferencias línea por línea entre las dos ramas.

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2039.png)

Podemos entonces hacer el marge:

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2040.png)

## Eliminar una rama

Para eliminar una rama que ya no necesitamos, usamos el comando:

```bash
git branch -d login

```

Esto eliminará la rama `login` si ya ha sido fusionada con otra rama principal. Si queremos forzar la eliminación de una rama que no ha sido fusionada, usamos `git branch -D login`.

![Untitled](git%20Guide%200a82823b1913487c837302901d12b506/Untitled%2041.png)