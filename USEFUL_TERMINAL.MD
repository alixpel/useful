# USEFUL TERMINAL COMMANDS


## tree

Tout :
tree /F

1 folder spé:
tree "C:\MonDossier" /F

Sauvegarder le tree :
tree "C:\Users\AlixPelletier\projects\adt-parser" /F > arborescence.txt

Exclure folder :

Get-ChildItem "C:\Users\AlixPelletier\projects\adt-parser" -Recurse |
Where-Object { $_.FullName -notmatch '\\.venv\\' } |
Format-Table FullName -AutoSize

Get-ChildItem -Recurse |
Where-Object {
    $_.FullName -notmatch '\\.venv\\' -and
    $_.FullName -notmatch '\\__pycache__\\'
	$_.FullName -notmatch '\\documentation.txt\\'
} |
Select-Object FullName


## Connexion

Test-NetConnection vhefgdseci.sap.eiffage.com -Port 22

Ping ...




## SSH

### créer : 
ssh-keygen -t ed25519 -C "alix.pelletier@viseo.com"

### initialiser:
ssh -T git@gitlab.viseo.com
yes

### Git:
git@gitlab.viseo.com:<groupe>/<projet>.git
git clone --branch ma-branche git@gitlab.viseo.com:groupe/projet.git
ex: git clone --branch dev git@gitlab.viseo.com:saptech/tool/python/adt-parser.git

git config --global user.email "alix.pelletier@viseo.com"
git config --global user.name "Alix Pelletier"


## Python:

### Créer l'env:
python -m venv .venv

### Activer l'env :
`.\.venv\Scripts\Activate.ps1`

### Dépendances :
`python -m pip install beautifulsoup4 requests snakemd lxml`


## Github Copilot

### Auth
`omp auth-broker login github-copilot`
`$env:NODE_TLS_REJECT_UNAUTHORIZED="0"` et `omp auth-broker login github-copilot`
