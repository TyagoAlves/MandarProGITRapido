# 🚀 Automação de Git com PowerShell

![PowerShell](https://img.shields.io/badge/PowerShell-5.1+-blue)
![Git](https://img.shields.io/badge/Git-Automation-green)
![GitHub](https://img.shields.io/badge/GitHub-Ready-orange)

Script PowerShell para automatizar o processo de commit e push para o GitHub em um único comando.

## 📋 Índice

- [Visão Geral](#-visão-geral)
- [Pré-requisitos](#-pré-requisitos)
- [Como Usar](#-como-usar)
- [Funcionalidades](#-funcionalidades)
- [Parâmetros](#-parâmetros)
- [Exemplos](#-exemplos)
- [Dicas de Git](#-dicas-de-git)
- [Solução de Problemas](#-solução-de-problemas)

## 🔍 Visão Geral

O script `manda-pro-git.ps1` automatiza o fluxo de trabalho comum do Git, combinando vários comandos em uma única operação. Ele executa:

1. Verificação do status do repositório
2. Adição de todos os arquivos modificados
3. Commit com mensagem personalizada
4. Pull para sincronizar com o repositório remoto
5. Push das alterações para o GitHub

## 📋 Pré-requisitos

- **PowerShell** 5.1 ou superior
- **Git** instalado e configurado
- **Repositório Git** inicializado com um remote configurado
- **Permissões** para executar scripts PowerShell

## 🚀 Como Usar

1. **Salve o script** em seu repositório Git local
2. **Abra o PowerShell** na pasta do repositório
3. **Execute o script**:

```powershell
# Com mensagem de commit padrão
.\manda-pro-git.ps1

# Com mensagem de commit personalizada
.\manda-pro-git.ps1 "Sua mensagem de commit aqui"
```

## ✨ Funcionalidades

### Status do Repositório
```powershell
# Mostra status antes de tudo
Write-Host "Status do repositório:" -ForegroundColor Cyan
& git status
```
Exibe o status atual do repositório, mostrando arquivos modificados, adicionados ou removidos.

### Adição de Arquivos
```powershell
# Adiciona todos os arquivos
Write-Host "Adicionando arquivos..." -ForegroundColor Yellow
& git add .
```
Adiciona todos os arquivos modificados ao staging area para serem incluídos no próximo commit.

### Commit das Alterações
```powershell
# Faz commit
Write-Host "Realizando commit..." -ForegroundColor Yellow
& git commit "$msg"
```
Cria um commit com todos os arquivos no staging area, usando a mensagem fornecida ou a mensagem padrão.

### Sincronização com o Repositório Remoto
```powershell
# Faz pull antes do push para evitar conflitos
Write-Host "Sincronizando com o GitHub (git pull)..." -ForegroundColor Yellow
& git pull origin main --allow-unrelated-histories
```
Sincroniza o repositório local com o remoto antes de enviar as alterações, evitando conflitos.

### Envio para o GitHub
```powershell
# Faz push para o repositório remoto
Write-Host "Enviando para o GitHub..." -ForegroundColor Green
& git push
```
Envia todos os commits locais para o repositório remoto no GitHub.

## 🔧 Parâmetros

| Parâmetro | Descrição | Padrão |
|-----------|-----------|--------|
| `-msg` | Mensagem de commit personalizada | "Alterações automáticas" |

## 📝 Exemplos

### Commit com Mensagem Padrão
```powershell
.\manda-pro-git.ps1
```
Resultado: Commit com a mensagem "Alterações automáticas"

### Commit com Mensagem Personalizada
```powershell
.\manda-pro-git.ps1 "Corrigido bug na função de login"
```
Resultado: Commit com a mensagem "Corrigido bug na função de login"

## 📚 Dicas de Git

O script inclui dicas úteis sobre operações comuns com branches:

```
Dicas rápidas de branches:
Criar novo branch: git checkout -b nome-do-branch
Trocar de branch: git checkout main
Mesclar branch: git merge nome-do-branch
Enviar branch: git push -u origin nome-do-branch
```

## ❓ Solução de Problemas

### Erro ao Enviar para o GitHub
Se ocorrer um erro durante o push, o script exibirá uma mensagem de erro:

```powershell
if ($LASTEXITCODE -eq 0) {
    Write-Host "Pronto! Alterações salvas e enviadas para o GitHub." -ForegroundColor Green
} else {
    Write-Host "Ocorreu um erro ao enviar para o GitHub. Tente rodar novamente ou verifique conflitos." -ForegroundColor Red
}
```

### Possíveis Soluções
- Verifique sua conexão com a internet
- Confirme que você tem permissão para push no repositório
- Resolva conflitos de merge manualmente se necessário
- Verifique se o branch remoto existe
