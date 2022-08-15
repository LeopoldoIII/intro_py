# Pasos para ambientar PC Windows 10 para Ubuntu, WSL y VSC

## Paso #1 Habilitar el modo programador

Ir a Menú, Configuración,
Opción Actualización y Seguridad,
Opción Para Programadores,
Seleccionamos el Modo Programador.

## Paso #2 Activar Subsistema de Windows para Linux

Ir a Menú,
Panel de Control,
Opción Programas,
Opción Activar o desactivar las características de Windows,
Activar la casilla Subsistema de Windows para Linux,
Click en Aceptar.

Nos Solicitará Reiniciar el equipo.

## Paso #3 Abrir Línea de comando Ubuntu y creación de usuario

Presionamos al mismo tiempo Windows + R,
escribir cmd y dar enter,
escribir el siguiente comando y damos enter:
```
wsl --install -d Ubuntu
```

Esperamos a que instale Ubuntu

## Paso #4 Terminando la instalación de Ubuntu

Se abrirá Ubuntu y te mencionará que está instalandose.

Nos solicitará crear un nuevo UNIX Username, password y confirmación de password.

Para instalar los paquetes mas actuales de Ubuntu, escribimos y damos enter:

```
 sudo apt-get update
```

## Paso #5 Instalar versiones diferentes de Python con pyenv

Pyenv compila Python desde la fuente, lo que significa que necesitará compilar dependencias para usar pyenv.

Para ello usar el siguiente comando y damos enter:

```
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python-openssl
```

Teclear el siguiente comando para instalar plugins necesarios para pyenv:
```
curl https://pyenv.run | bash
```

Te mencionará que aún no se ha agregado "pyenv" al load path.
Tecleamos los siguientes comandos para exportar la ruta pyenv a .bashrc.:

```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n eval "$(pyenv init -)"\nfi' >> ~/.bashrc
```

Tecleamos los siguientes comandos para agregar pyenv al load path:

```
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

Reiniciamos la terminal con el comando 

```
exec "$SHELL"
```

Para verificar las diferentes versiones de Python 3.6 a 3.8

```
pyenv install --list | grep " 3\.[678]"
```

Verificamos que versión de python tenemos 
```
python3
exit()
``` 

Instalando Python ver 3.7.0 

```
pyenv install -v 3.7.0
```
Instalar una segunda versión de Python

```
pyenv install -v 3.8.0
```

Verificar versiones de python instaladas

```
ls ~/.pyenv/versions/
```

Otra forma de ver las versiones instaladas

```
pyenv versions
```

Remover alguna version de python instalada

```
rm -rf ~/.pyenv/versions/2.7.15
```

Ver que versión de Python está activa

```
python3 -V
```
Y para ver en que directorio se encuentra

```
which python3
```
Pyenv se inserta a si mismo en el path y, desde la perspectiva de el OS, es el ejecutable al que se llama. Para ver la ruta real, puede ejecutar lo siguiente:

```
pyenv which python
```

Para usar una versión de Python ya instalada se puede usar el comando GLOBAL:

```
pyenv global 3.7.0
```

## Paso #6 Instalar **Visual Studio Code**

Descargamos desde cualquier navegador en el siguiente enlace: https://code.visualstudio.com/

Una vez completada la instalación, vamos a File > Auto Save para que todo cambio lo guarde de manera automatica. 

Descargamos la extensión **Remote - WSL** para ligar el WSL a VSC desde la opción Extensions de lado izquierdo del programa.

Adicional para visualización de nuestro código en Python y Jupyter Notebooks (Para ir documentando nuestro código paso a paso) podemos descargar las extensiones: **Python, Jupyter**

Regrsamos a la línea de comando de Ubuntu y tecleamos lo siguiente para instalar las últimas actualizaciones de Ubuntu:

```
sudo apt-get update
```

Para agregar wget (para recuperar contenido de servidores web) y certificados CA (para permitir que las aplicaciones basadas en SSL verifiquen la autenticidad de las conexiones SSL), tecleamos lo siguiente:

```
sudo apt-get install wget ca-certificates
```

Una vez terminando estas actualizaciones tecleamos lo siguiente para abrir VSC con el WSL conectado:

```
code .
```

Ya en VSC, vamos a las extensiones e instalamos las mismas ahora para el WSL ligado.

## Paso #7 Crear una Jupyter Notebook

Creamos un nuevo archivo para código:
- Control + J para abrir terminal
- Tecleamos:

```
touch test.ipynb
```
Vamos a la Opción Explorer en la parte izquierda y damos click. Elegimos nuestro nuevo archivo para comenzar a editar.

Aquí podemos agregar código y markdowns para documentar paso a paso o explicar algún comando.

Espcribimos cualquier código sencillo para probar que funione el Jupyter Notebook y damos el botón ejecutar. 

Comenzará a instalar el complemento de la extensión.

Consultar *Commands_for_Git_GitHub.ipynb* para controlar versiones de tu archivos y subirlos a la plataforma GitHub.