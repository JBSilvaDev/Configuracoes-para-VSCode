# Comandos personalizados do PowerShell
```ps1
# Minhas funcoes
function meuip(){  
  Get-NetIPAddress -AddressFamily IPv4 | Select-Object InterfaceAlias, IPAddress, PrefixLength
}
function n-venv(){  
  "Execultando: virtualenv venv"
  virtualenv venv
}
function at-venv(){  
  "Execultando: venv/Scritps/activate"
  venv/Scripts/activate
}
function pmr(){  
  "Execultando: python manage.py runserver"
  python manage.py runserver
}
function freeze-install(){  
  "Execultando: pip install -r requirements.txt"
  pip install -r requirements.txt
}

function django-tables(){
  "Execultando: python manage.py makemigrations"
  python manage.py makemigrations
  "Execultando: python manage.py migrate"
  python manage.py migrate
}

function django-start(){ 
  "Iniciando requerimentos django para projetos ja criados" 
  n-venv
  at-venv
  freeze-install
  django-tables
  pmr
}

```