# Voiston Bridge — Vilar releases

Pacotes de release (.zip) da versão do Voiston Bridge para o Tasy HTML do Vilar Hospital de Olhos. Aqui não há código-fonte, só a hospedagem dos arquivos (o código fica no repositório privado `voiston-bridge`).

## Instalação em máquina nova

No PowerShell, com o usuário do Windows que vai usar o Bridge e internet até o github.com:

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Enum]::ToObject([Net.SecurityProtocolType], 3072); (New-Object Net.WebClient).DownloadFile('https://github.com/voiston-ai/voiston-bridge-releases-vilar/releases/latest/download/install.ps1', "$env:TEMP\install-bridge.ps1"); powershell -NoProfile -ExecutionPolicy Bypass -File "$env:TEMP\install-bridge.ps1" -Client Vilar
```

O script baixa a versão mais recente, instala em `%LOCALAPPDATA%\VoistonBridge\app`, liga o início automático e abre o Bridge. Quem já tem o Bridge se atualiza sozinho.

## Requisitos no Vilar

1. **Atalho do Tasy HTML com a flag** `--force-renderer-accessibility` (ex.: `chrome.exe --incognito --force-renderer-accessibility --app=<endereço do Tasy HTML>`). Sem ela o Chrome não expõe a página e o Bridge não lê o paciente. É preciso fechar e abrir o Tasy HTML pelo atalho para valer.
2. **FortiClient / firewall:** liberar o `VoistonBridge.exe` para HTTPS (443) em `api.voiston.ai`, `app.voiston.ai`, `identitytoolkit.googleapis.com` (login) e, para atualizar, `api.github.com`, `github.com` e `objects.githubusercontent.com`.
3. **Login do Voiston:** cada médico configura o login uma vez (botão direito no card > "Configurar login do Voiston"). A conta precisa ser do Vilar.
