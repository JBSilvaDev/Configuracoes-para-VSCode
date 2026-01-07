# Configs

[VsCode](./VsCode.md)

# Funcoes com atalhos para shell
## Windows
- Exemplo de função powershell
  - Para este exemplo uso o comando de verificar ips na maquina
- Comando padrão
```ps
Get-NetIPAddress -AddressFamily IPv4 | Select-Object InterfaceAlias, IPAddress, PrefixLength
```
- Para criar uma função pra este comando usar
  ```ps
  code $PROFILE
  ```
   - Um arquivo .ps1 ira abrir no vsCode
   - Neste arquivo criar a função como abaixo
      ```ps1
      function meuip(){  
      Get-NetIPAddress -AddressFamily IPv4 | Select-Object InterfaceAlias, IPAddress, PrefixLength
      }
      ```
- Agora basta usar no powershell o comando `meuip` que ira obter o mesmo retorno do comando completo

## Mac
- Exemplo de alias no zsh
  - Para este exemplo uso o comando de verificar ips na maquina
- Comando padrão
  ```bash
  ifconfig | grep "inet " | awk '{print $1, $2, $4}'
  ```
- Para criar o alias no mac basta setar uma variavel do tipo alias no arquivo de configuração de variaveis de ambiente
  ```
  alias meuip="ifconfig | grep 'inet ' | awk '{print $1, $2, $4}'"
  ```
- Agora basta usar no powershell o comando `meuip` que ira obter o mesmo retorno do comando completo


***
```ps1
$MaximumHistoryCount = 2000

# Import-Module posh-git
# Import-Module PSReadLine
# Import-Module Get-ChildItemColor
# Import-Module Terminal-Icons
# Import-Module DockerCompletion



# Configuração tema
## Melhores:
  # material
  # spaceship
  # Usar Get-PoshThemes para ver mais opcoes
    # Alterar o nomeDoTema.omp.json na linha abaixo
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH/material.omp.json" | Invoke-Expression

# Uses tab for autocompletion
Set-PSReadLineKeyHandler -Key Tab -Function MenuComplete

# History definitions
$HistoryFilePath = Join-Path ([Environment]::GetFolderPath('UserProfile')) .ps_history
Register-EngineEvent PowerShell.Exiting -Action { Get-History | Export-Clixml $HistoryFilePath } | out-null
if (Test-path $HistoryFilePath) { Import-Clixml $HistoryFilePath | Add-History }

Set-PSReadLineOption -HistorySearchCursorMovesToEnd
Set-PSReadlineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadlineKeyHandler -Key DownArrow -Function HistorySearchForward

Set-PSReadLineOption -ShowToolTips
Set-PSReadLineOption -PredictionSource History

# Aliases
Set-Alias which Get-Command
Set-Alias open Invoke-Item

function ll() { Get-ChildItem | Format-Table }
function la() { Get-ChildItem | Format-Wide }
function lb() { Get-ChildItem | Format-List }

Set-Alias ls la
Set-Alias l lb

# Aliases Functions

function profile() { code $PROFILE }
function edh() { code "$HOME\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt" }
function eds() { code "$HOME\AppData\Local\oh-my-posh\spaceship.omp.json" }

# Compute file hashes - useful for checking successful downloads
function md5    { Get-FileHash -Algorithm MD5 $args }
function sha1   { Get-FileHash -Algorithm SHA1 $args }
function sha256 { Get-FileHash -Algorithm SHA256 $args }

function tail { Get-Content $args -Tail 30 -Wait }

function take {
  New-Item -ItemType directory $args
  Set-Location "$args"
}
```
Minhas funções [aqui](./Python-Profile/README.md)
