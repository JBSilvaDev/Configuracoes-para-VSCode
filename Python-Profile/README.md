# Comandos personalizados do PowerShell

```ps1
# Minhas funcoes
function meuip(){  
  Get-NetIPAddress -AddressFamily IPv4 | Select-Object InterfaceAlias, IPAddress, PrefixLength
}
function new-venv(){  
  "Execultando: virtualenv venv"
  pip install virtualenv
  virtualenv venv
  ative-venv
}
function ative-venv(){  
  "Execultando: venv/Scritps/activate"
  venv/Scripts/activate
}
function freeze-save(){  
  "Execultando: pip freeze > requirements.txt"
  pip freeze > requirements.txt
}
function freeze-install(){  
  "Execultando: pip install -r requirements.txt"
  pip install -r requirements.txt
}
# Comandos DJANGO
function django-init(){
  "Executando: django-admin startproject setup ."
  django-admin startproject setup .
}
function django-app($appName){
  "Executando: django-admin startapp $appName"
  django-admin startapp $appName
}

function pmr(){  
  "Execultando: python manage.py runserver"
  python manage.py runserver
}
function django-tables(){
  "Execultando: python manage.py makemigrations"
  python manage.py makemigrations
  "Execultando: python manage.py migrate"
  python manage.py migrate
}

```
# Configurações
Basta copiar e colar o settings.json para a pasta de configuração de usuario do vsCode
# Extenções
Basta copiar e colar o extensions.json para a pasta de confifuração do usuario do vsCode\
Talvez seja necessario alteração do path de usuario