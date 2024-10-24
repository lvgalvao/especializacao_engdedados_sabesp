## **Repositório Único do Projeto da Sabesp**

Este repositório tem como objetivo centralizar todas as informações e recursos do projeto da **Sabesp**, incluindo código-fonte, documentação e materiais complementares. Ele servirá como o ponto de referência único para garantir a organização e facilitar o acesso a todas as etapas do projeto.

---

### **Calendário de Aulas do Projeto Sabesp**

| Aula          | Data       | Conteúdo                                   |
|---------------|------------|--------------------------------------------|
| Aula 1        | 23/10/2024 | Boas-vindas e configuração inicial         |
| Aula 2        | 24/10/2024 | Configuração e preparação do ambiente      |
| Aula 3        | 30/10/2024 | Git                                        |
| Aula 4        | 31/10/2024 | Github                                     |
| Aula 5        | 06/11/2024 | Python                         |
| Aula 6        | 07/11/2024 | Python                       |
| Aula 7        | 13/11/2024 | Python                        |
| Aula 8        | 14/11/2024 | Python                        |
| Aula 9        | 20/11/2024 | Python                        |
| Aula 10       | 21/11/2024 | Python                        |

---

### **Observações:**

- As aulas ocorrerão **sempre às quartas e quintas-feiras** ás 10h00 até 12h00.
- O cronograma será atualizado ao longo do projeto com mais detalhes e temas específicos.

---

Com esta estrutura, garantimos um acompanhamento claro das atividades, facilitando o alinhamento entre todos os participantes.Aqui está uma estrutura completa, incluindo a instalação do **Ubuntu** através da **Microsoft Store**, caso ele ainda não esteja instalado, além dos passos para configurar o WSL2, Docker e Git.

---

## 1. **Verificar e Instalar o Ubuntu no Windows**

Se você não tem o **Ubuntu** instalado, siga estas instruções:

1. **Abra a Microsoft Store**:
   - Clique no menu Iniciar e abra a **Microsoft Store**.
   - Pesquise por "Ubuntu".

2. **Escolha e Instale o Ubuntu**:
   - Selecione uma das versões disponíveis, como **Ubuntu 22.04 LTS** ou **Ubuntu 20.04 LTS**.
   - Clique em **Instalar** e aguarde a conclusão.

3. **Abrir o Ubuntu pela Primeira Vez**:
   - Após instalar, clique em **Abrir** na própria Microsoft Store ou no menu Iniciar.
   - Complete a configuração inicial, criando um **nome de usuário** e uma **senha**.

---

## 2. **Habilitar WSL2 no Windows**

Abra o **PowerShell como Administrador** e execute os seguintes comandos para habilitar o WSL e a plataforma de virtualização:

```powershell
# Habilitar o WSL (Windows Subsystem for Linux)
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

# Habilitar a Plataforma de Máquina Virtual (necessário para WSL2)
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

# Reinicie o computador para aplicar as mudanças.
```

Após a reinicialização, defina o WSL2 como versão padrão:

```powershell
wsl --set-default-version 2
```

---

## 3. **Verificar Distribuições Instaladas e Configurar WSL2**

Após instalar o Ubuntu, execute:

```powershell
# Verificar as distribuições e suas versões
wsl --list --verbose

# Definir o Ubuntu como WSL2 (caso não esteja configurado)
wsl --set-version Ubuntu 2
```

Se for necessário remover alguma distribuição antiga:

```powershell
# Remover uma distribuição registrada
wsl --unregister <nome-da-distribuicao>
```

---

## 4. **Configurar o Docker no WSL (Ubuntu)**

Agora que o Ubuntu está instalado e configurado como WSL2, abra o terminal **Ubuntu** e siga estas etapas para instalar o Docker.

### **Passo 1: Atualizar Pacotes Existentes**
```bash
sudo apt-get update
```

### **Passo 2: Instalar Dependências**
```bash
sudo apt-get install -y ca-certificates curl gnupg lsb-release
```

### **Passo 3: Adicionar Chave GPG e Repositório Docker**
```bash
sudo mkdir -m 0755 -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### **Passo 4: Instalar Docker e Plugins**
```bash
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

---

## 5. **Verificar e Testar Docker**

Para garantir que o Docker foi instalado corretamente, execute:

```bash
docker --version
docker run hello-world
```

Se necessário, adicione seu usuário ao grupo do Docker:

```bash
sudo usermod -aG docker $USER
```

---

## 6. **Instalar o Git no Ubuntu (WSL)**

Se você precisa do Git, instale-o com o seguinte comando:

```bash
sudo apt-get install -y git
```

Verifique se o Git foi instalado corretamente:

```bash
git --version
```

---

Com esses passos, você terá o **WSL2**, **Ubuntu**, **Docker** e **Git** instalados e prontos para uso no seu ambiente Windows.