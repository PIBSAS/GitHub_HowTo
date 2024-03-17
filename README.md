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

## Verificar que git esta instalado, preguntando su versión:
```bash
git --version
```

## Si te da error, no está instalada, la instalas:
```bash
sudo apt install -y git wget curl
```

## Bajas GitHub Credential Manager para que guarde tu usuario y password y no vuelva a pedirlo:

### Obtener la última versión desde la API de GitHub automaticamente:
```bash
latest=$(curl -s "https://api.github.com/repos/git-ecosystem/git-credential-manager/releases/latest" | grep '"tag_name":' | sed -E 's/.*"([^"]+)".*/\1/')
```

#### Eliminar el prefijo 'v' del número de versión:
```bash
version=$(echo "$latest" | sed 's/v//')
```

#### Construir el enlace de descarga:
```bash
link="https://github.com/git-ecosystem/git-credential-manager/releases/download/${latest}/gcm-linux_amd64.${version}.deb"
```

#### Descargar el archivo .deb:
```bash
wget "$link"
```
#### Lo instalas:
```bash
sudo dpkg -i *.deb
```

#### Borras el deb, ya no lo necesitas:
```bash
rm gcm*.deb
```

<p style="text-align: center;">Vas a tu github en la web y creas un repositorio sin readme. 
Una vez creado vas a tu perfil a la foto arriba a la derecha, elegis settings -> Developer Settings(a la izquierda abajo de todo) -> Personal access tokens -> Tokens(classic) -> Generate new token -> Generate New token(classic)-> En Note escribis algo ejemmplo Repos desde PC, en Expiration elegis 30 dias o no expiration o lo que te parezca, tildas public_repo -> Elegis Generate Token(el botón verde abajo) -> Copias el Token y enviatelo por mail o guardalo en algun lado lo necesitas como password.
</p>

## Volves a la terminal de linux:

### Creas la carpeta de tu repo, nombrandola como se te antoje, pero lo lógico es nombrarla como se llamará tu repo:
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
##### Aca pones tu usuario y el mail, asi solo copias y pegas las otras lineas:
```bash
$USER="jaimito"
```

```bash
$MAIL="mail@gmail.com"
```
## Configuras tus credenciales:
```bash
git config --global user.email ${MAIL}
```
```bash
git config --global user.name ${USER}
```
```bash
git config --global --replace-all credential.helper store
```

## Indicas a Git donde esta tu repo en la web:
```bash
git remote add origin https://github.com/TU_USUARIO/EL_NOMBRE_QUE_PUSISTE_A_TU_REPO.git
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
TU_USUARIO
```


Y te va a paedir el password, que en realidad es el Token que creaste, lo pegas, no se ve nada asi que talvez debas intentar un par de veces repitiendo el comando, una vez que pegas le das a enter y empieza a subir el/los archivos, a la vez se va a guardar en la pc tus credenciales y ya no te las pedira.

## Desde ahora en adelante, solo haras esto si estas en la misma repo:
```bash
git add .
git commit -m "Subiendo cosas"
git push -u origin main
```


y nada mas, bueh obvio crear, copiar y pegar archivos y carpetas que quieras guardar.

## Y si vas a crear una nueva repo, repetiras solo estos pasos:
Crear el repo en la web.
Crear directorio con el nombre de la repo nueva y moverte a esa carpeta, iniciar git, agregar la url a la nueva repo, indicar el branch main.

```bash
mkdir nuevarepo
cd nuevarepo
git init
git remote add origin https://github.com/TU_USUARIO/EL_NOMBRE_QUE_PUSISTE_A_TU_REPO.git
git branch -M main
```

##Crear o meterle cosas a la carpeta y hacer add, commit y push a la nueva repo:
```bash
git add .
git commit -m "Subiendo cosas"
git push -u origin main
```

## Y cuando hagas cambios via web, luego debes traerlos al pc con:
```bash
git pull origin main
```

Listo
