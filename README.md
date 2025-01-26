<div align="center" style="font-family: Arial, sans-serif; font-size: 20px; line-height: 1.5;">

# 🌟 **Curso Dpcn-EDN** 🌟
# 🌟 Solutions Architect Associate  🌟

###
<a href="https://escoladanuvem.org"><a href="https://aws.amazon.com/pt/?nc2=h_lg">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/Amazon_Web_Services_Logo.svg/2560px-Amazon_Web_Services_Logo.svg.png" width="180" alt="AWS Logo">
</a>
<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSVS48VeIElXRoqXfCQ4uD0Ct9D5i9jDNLvbw&s" width="80" alt="AWS Logo">- <img src="https://cdn.worldvectorlogo.com/logos/amazon-elastic-block-store-1.svg" width="80" alt="AWS Logo">- 
    <img src="https://github.com/HalleyVeras/Escola_da_Nuvem/blob/main/Documentos/download%20(4)_processed.png?raw=true" width="210" alt="Second Image">
</a>
</div>

# Laboratório 2 : Amazon Ec2 e Armazenamento EBS

**Turma:** Dpcn 07  
**Aluno:** Halley Veras  
**Objetivo:** Trabalhar com instâncias EC2 e volumes EBS, aprendendo a criar, configurar e gerenciar esses recursos.  
**Cenário:** Provisionar um servidor web simples na AWS com armazenamento adicional e configurar backups automáticos.

---

## Etapa 1: Selecionar a Região AWS

Escolhi a região **us-east-1 (Norte da Virgínia)**, considerando a baixa latência e maior disponibilidade de serviços.

---

## Etapa 2: Criação da Instância EC2

### 1. Acessar o console EC2:

- Naveguei até o console do Amazon EC2.  
- Cliquei em **"Lançar Instâncias"**.

### 2. Selecionar a AMI:

- Escolhi a imagem **Amazon Linux 2** (elegível para a camada gratuita).

### 3. Escolher o Tipo de Instância:

- Optei por **t2.micro**, também elegível para a camada gratuita.

### 4. Configurar o Par de Chaves:

- Cliquei em **"Criar novo par de chaves"**, salvei o arquivo `.pem` localmente e tomei cuidado com a permissão de acesso ao arquivo.

---

## Etapa 3: Conexão à Instância via SSH

Utilizei o **MobaXterm** para acessar a instância:

### 1. Configuração:

- No campo "Remote host", inseri o IP público da instância.  
- Configurei o "Specify username" para **ec2-user**.  
- Selecionei a chave privada (`.pem`) em "Advanced SSH settings".

### 2. Conexão bem-sucedida:

- Consegui acessar o terminal da instância via SSH.

---

## Etapa 4: Adicionar e Configurar o Volume EBS

### 1. Criar o Volume EBS:

- No console EC2, fui até a aba **"Volumes"** em **Elastic Block Store**.  
- Criei um volume de **8 GB**.  
- Anexei o volume à instância EC2.

### 2. Identificar o Volume:

- Executei o comando `lsblk` e identifiquei o volume como **/dev/xvdf**.

### 3. Formatar o Volume:

- Rodei o comando: `sudo mkfs.ext4 /dev/xvdf`.  
- Isso formatou o volume com o sistema de arquivos ext4.

### 4. Montar o Volume:

- Criei o diretório de montagem: `sudo mkdir /mnt/dados`.  
- Montei o volume com: `sudo mount /dev/xvdf /mnt/dados`.  
- Verifiquei a montagem com `lsblk` e confirmei que o volume estava acessível.

### 5. Configuração de Montagem Automática:

- Editei o arquivo `/etc/fstab` para garantir que o volume fosse montado automaticamente em reinicializações.

---

## Etapa 5: Configuração de Backups

### 1. Criar Snapshot Manual:

- Naveguei até **Volumes** no console EC2.  
- Selecionei o volume anexado.  
- Cliquei em **Ações > Criar Snapshot**.  
- Nomeei o snapshot como **"Snapshot Inicial - Volume Dados"**.  
- Adicionei tags para organização:  
  - **Chave:** Backup  
  - **Valor:** Automático

### 2. Criar Política de Snapshot Automática:

- Acesse o **Gerenciador de Cópias Automáticas**.  
- Cliquei em **Criar Política**:  
  - Frequência: **Diariamente**  
  - Hora: **01:00 UTC**  
  - Período de retenção: **7 dias**  
- Salvei a política e testei a configuração.

---

## Conclusão

Ao final do exercício, consegui provisionar e configurar uma instância EC2 com armazenamento EBS adicional, formatado e montado corretamente. Também configurei snapshots automáticos, garantindo a segurança dos dados.

Esse processo me permitiu compreender melhor as práticas de administração de instâncias EC2 e volumes EBS, incluindo os aspectos de automação e boas práticas de backup.
