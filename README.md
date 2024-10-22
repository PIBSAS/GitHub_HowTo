<h1 align="center">GitHub HowTo</h1>
<hr>


## Actualizar la repo de linux:

```bash
sudo apt update 
```

## Instalar las actualizaciones:
```bash
sudo apt upgrade -y
```

## Instalas por si no están en tu distribución Linux:
```bash
sudo apt install -y git gh wget curl
```

## Creas un Tokken Classic para realizar el login
<p style="text-align: center;">Vas a tu github en la web y creas un repositorio sin readme. 
Una vez creado vas a tu perfil a la foto arriba a la derecha, elegis <b>Settings</b> -> <b>Developer Settings</b>(A la izquierda abajo de todo) -> <b>Personal Access Tokens</b> -> <b>Tokens(classic)</b> -> <b>Generate new token</b> -> <b>Generate New token(classic)</b> -> En Note escribis algo, ejemplo: Repos desde PC, en <b>Expiration</b> elegis 30 dias o no expiration o lo que te parezca, tildas <b>public_repo</b> -> Elegis <b>Generate Token</b>(el botón verde abajo) -> Copias el Token y enviatelo por mail o guardalo en algun lado lo necesitas como password.
</p>

## Volves a la terminal de linux:

```bash
gh auth login
? What account do you want to log into? GitHub.com
? What is your preferred protocol for Git operations? HTTPS
? Authenticate Git with your GitHub credentials? Yes
? How would you like to authenticate GitHub CLI? Login with a web browser

! First copy your one-time code: 432A-ABC4
Press Enter to open github.com in your browser... (Aca en realidad debemos presionar ctrl+ left click para que se abra el enlace y pegar el codigo generado)
```
## Tras esto podremos clonar, crear, hacer pull request, actions, workflows, issues. Pero para agregar contenido y hacer push aun usaremos git, asi también para nuestras credenciales.
# Con GH (Requiere haber configurado usuario y correo, agregado a los pasos para simplicidad):
```bash
U="PIBSAS"
M="correo@gmail.com"
git config --global user.email ${M}
git config --global user.name ${U}
git config --global --replace-all credential.helper store
gh repo create NOMBRE_REPO --public NOMBRE_REPO
gh repo clone ${USER}/NOMBRE_REPO
cd NOMBRE_REPO
echo "# REPO creada desde la compu con gh" > README.md
git add .
git commit -m "Primer commit: añadir README.md"
git push -u origin main

```
- Te dirá que haz clonado un repo vacio, al clonar, pero luego haces un echo y lo guardas a lo entrecomillado en un archivo y lo subes a esa repo, puedes abrir el navegador y encontrar este repo creado desde tu pc.

# Con GIT
### Creas la carpeta de tu repo, nombrandola como se te antoje, pero lo lógico es nombrarla tal cual se llamará tu repo:
```bash
mkdir unrepo
```

### Cambiarte al Directorio creado:
```bash
cd unrepo
```

## Iniciar git:
```bash
git init
```
##### Aca pones tu usuario,el mail de github, y el nombre de tu repo.git, asi solo copias y pegas las otras lineas:
```bash
U="PIBSAS"
```

```bash
M="correo@gmail.com"
```

```bash
REPO="unrepo"
```

## Configuras tus credenciales:
```bash
git config --global user.email ${M}
```
```bash
git config --global user.name ${U}
```
```bash
git config --global --replace-all credential.helper store
```

## Indicas a Git donde esta tu repo en la web:
```bash
git remote add origin https://github.com/${U}/${REPO}.git
```

## Indicas que es la rama(branch) principal(main):
```bash
git branch -M main
```

## Ahora creas un archivo de ejemplo, cuando hagas otra repo ya directamente copias los archivos y carpetas que quieras que esten en tu repo, esto es solo de ejemplo:
```bash
touch unejemplo.txt
```

## Como agregaste algo nuevo,tenias la carpeta sin nada(estas dentro de la carpeta que creaste), debes indicarle a Git que se fije que agregaste cosas:
```bash
git add .
```

## Luego le decis que haces un commit(como haces en la web para subir el archivo):
```bash
git commit -m "Estas subiendo algo"
```

Te va a devolver todo lo que este listo para subir, en este caso solo el txt.

## Ahora para subirlo vas a empujarlos de tu pc a la web con git push:
```bash
git push -u origin main
```

## Te va a pedir el nombre de tu usuario:
```bash
${U}
```


## Te va a paedir el password:
- Que en realidad es el Token que creaste, lo pegas, no se ve nada, asi que talvez, debas intentar un par de veces repitiendo el comando, una vez que pegas le das a ``enter`` y empieza a subir el/los archivos, a la vez se va a guardar en la pc tus credenciales y ya no te las pedirá.

## Desde ahora en adelante, solo haras esto si estas en la misma repo:
```bash
git add .
git commit -m "Subiendo cosas"
git push -u origin main
```

y nada mas, bueh obvio crear, copiar y pegar archivos y carpetas que quieras guardar.

## Y si vas a crear una nueva repo, repetiras solo estos pasos:
- Crear el repo en la web.
- Crear directorio con el nombre de la repo nueva y moverte a esa carpeta
- Iniciar git
- Agregar la url a la nueva repo
- Indicar el branch main.

```bash
mkdir nuevarepo
cd nuevarepo
git init
git remote add origin https://github.com/${U}/${REPO}.git
git branch -M main
```

## Crear o meterle cosas a la carpeta y hacer add, commit y push a la nueva repo:
```bash
git add .
git commit -m "Subiendo cosas"
git push -u origin main
```

## Y cuando hagas cambios via web, luego debes traerlos al pc con:
```bash
git pull origin main
```

# Partiendo de una clonación:
```bash
git clone https://github.com/${U}/${REPO}.git
cd repoCLONADA
git init
git branch -M main
```

## Crear o meterle cosas a la carpeta y hacer add, commit y push a la nueva repo:
```bash
git add .
git commit -m "Subiendo cosas"
git push -u origin main
```

Listo

# Todo de una hasta el pedido de usuario y Token:
- Cambiar ``PIBSAS`` por tu usuario, ``TU_MAIL`` por tu correo y ``unrepo`` por el nombre del repositorio que creaste.

```bash
sudo apt update && sudo apt upgrade -y && sudo apt install -y git wget curl && mkdir otro && cd otro && git init && U="PIBSAS" && M="TU_MAIL@gmail.com" && REPO="unrepo" && git config --global user.email ${M} && git config --global user.name ${U} && git config --global --replace-all credential.helper store && git remote add origin https://github.com/${U}/${REPO}.git && git branch -M main && touch unejemplo.txt && git add . && git commit -m "Estas subiendo algo" && git push -u origin main
```
###### Luego ingresas:
```bash
${U}
```
y el Token.

# Git Large File System:

- Instalamos la extensión:
```bash
sudo apt install git-lfs
```

- Vamos al repositorio en la PC e inicializamos Git LFS, esto se realiza una sola vez por cuenta:
```bash
git lfs install
```

- Indicamos la extensión del archivo que es mayor a 50MB, ejemplo un archivo .PUP (si tenes distintas extensiones, repetis para cada extensión):
```bash
 git lfs track "*.PUP"
```
- Recomiendan subir el .gitattributes al GitHub asi que:
```bash
git add .gitattributes
git commit -m "Track *.PUP files with Git LFS"
git push -u origin main
```
- Luego son los pasos de siempre, pero al hacer el add si tenes archivos con la misma extensión que no necesitan usar Git LFS, entonces indicas ruta completa y extension:
```bash
git add .
git commit -m "Subiendo cosas"
git push -u origin main
```

- Ejemplo:
```bash
git add carpeta/archivo.PUP
git commit -m "Subiendo cosas"
git push -u origin main
```

- Para ver los archivos en Git LFS:
```bash
git lfs ls-files
```

# Si fallan las credenciales:

------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## [Se Puede saltear esto]Bajas GitHub Credential Manager para que guarde tu usuario y password y no vuelva a pedirlo:

- ### Obtener la última versión desde la API de GitHub automaticamente:
  - ```bash
    latest=$(curl -s "https://api.github.com/repos/git-ecosystem/git-credential-manager/releases/latest" | grep '"tag_name":' | sed -E 's/.*"([^"]+)".*/\1/')
    ```

- #### Eliminar el prefijo 'v' del número de versión:
  - ```bash
    version=$(echo "$latest" | sed 's/v//')
    ```

- #### Construir el enlace de descarga:
  - ```bash
    link="https://github.com/git-ecosystem/git-credential-manager/releases/download/${latest}/gcm-linux_amd64.${version}.deb"
    ```

- #### Descargar el archivo .deb:
  - ```bash
    wget "$link"
    ```
- #### Lo instalas:
  - ```bash
    sudo dpkg -i *.deb
    ```

- #### Borras el deb, ya no lo necesitas:
  - ```bash
    rm gcm*.deb
    ```
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
