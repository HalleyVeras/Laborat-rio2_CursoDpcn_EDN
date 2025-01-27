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
<img src="https://raw.githubusercontent.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/refs/heads/main/Prints/painel_digitar_ec2.jpg" width="400" alt="AWS Logo">-
- Cliquei em **"Lançar Instâncias"**.
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/Painel_ec2.jpg?raw=true" width="400" alt="AWS Logo">-
### 2. Selecionar a AMI:
<img src="https://raw.githubusercontent.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/refs/heads/main/Prints/nomeando_instance.jpg" width="400" alt="AWS Logo">-
- Escolhi a imagem **Amazon Linux 2** (elegível para a camada gratuita).
  
<img src="https://raw.githubusercontent.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/refs/heads/main/Prints/escolhendo_tipo_AMI.jpg" width="400" alt="AWS Logo">-
### 3. Escolher o Tipo de Instância:
<img src="https://raw.githubusercontent.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/refs/heads/main/Prints/Tipo_instance_t2micro.jpg" width="400" alt="AWS Logo">-


- Optei por **t2.micro**, também elegível para a camada gratuita.

### 4. Configurar o Par de Chaves:
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/create_new_pair_2.jpg?raw=true" width="400" alt="AWS Logo">-
- Cliquei em **"Criar novo par de chaves"**, salvei o arquivo `.pem` localmente e tomei cuidado com a permissão de acesso ao arquivo.

<img src="https://raw.githubusercontent.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/refs/heads/main/Prints/Tudo_configurado.jpg" width="400" alt="AWS Logo">-

---
## Etapa 3: Configurar o Volume EBS

### 1. Criar o Volume EBS:

- No console EC2, fui até a aba **"configure storage"**   
- Criei um volume de **8 GB**.
<img src="https://raw.githubusercontent.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/refs/heads/main/Prints/Adicionando_novo_volumeEBS.jpg" width="400" alt="AWS Logo">-
<img src="https://raw.githubusercontent.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/refs/heads/main/Prints/Instance_criada_sucesso.jpg" width="400" alt="AWS Logo">-
<img src="https://raw.githubusercontent.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/refs/heads/main/Prints/visualizando_instance.jpg" width="400" alt="AWS Logo">-

## Etapa 4: Conexão à Instância via SSH

Utilizei o **MobaXterm** para acessar a instância:
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/Iniciando_mobaxterm.jpg?raw=true" width="400" alt="AWS Logo">-
### 1. Configuração:

- No campo "Remote host", inseri o IP público da instância.
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/Inserindo_ippublic_minhaInstance.jpg?raw=true" width="400" alt="AWS Logo">-
- Configurei o "Specify username" para **ec2-user**.
- Selecionei a chave privada (`.pem`) em "Advanced SSH settings".
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/advanced_ssh_inserindo_chave_privada_2.jpg?raw=true" width="400" alt="AWS Logo">-

### 2. Conexão bem-sucedida:

- Consegui acessar o terminal da instância via SSH.
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/Console_ativado.jpg?raw=true" width="400" alt="AWS Logo">-

### 3. Identificar o Volume:

- Executei o comando `lsblk` e identifiquei o volume como **/dev/xvdf**.
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/inserindo_comando_lsblk.jpg?raw=true" width="400" alt="AWS Logo">-
### 4. Formatar o Volume:

- Rodei o comando: `sudo mkfs.ext4 /dev/xvdf`. 
- Isso formatou o volume com o sistema de arquivos ext4.
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/inserindo_comando_sudo.jpg?raw=true" width="400" alt="AWS Logo">-
### 5. Montar o Volume:

- Criei o diretório de montagem: `sudo mkdir /mnt/dados`.  
- Montei o volume com: `sudo mount /dev/xvdf /mnt/dados`.  
- Verifiquei a montagem com `lsblk` e confirmei que o volume estava acessível.
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/inserindo_comando_sudo_mk-mount.jpg?raw=true" width="400" alt="AWS Logo">-
### 6. Configuração de Montagem Automática:

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

<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/Create%20snapshot_volumeEbs.jpg?raw=true" width="400" alt="AWS Logo">-
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/criando_snapshot_volumeEBS.jpg?raw=true" width="400" alt="AWS Logo">-
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/Create%20snapshot_volumeEbs_sucess.jpg?raw=true" width="400" alt="AWS Logo">-
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Meu_snapshot.jpg?raw=true" width="400" alt="AWS Logo">-
### 2. Criar Política de Snapshot Automática:

- Acesse o **Gerenciador de Cópias Automáticas**.  
- Cliquei em **Criar Política**:  
  - Frequência: **Diariamente**  
  - Hora: **01:00 UTC**  
  - Período de retenção: **7 dias**  
- Salvei a política e testei a configuração.
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/Criando_politica_ciclodevidaEbs.jpg?raw=true" width="400" alt="AWS Logo">-
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/Criando_politica_ciclodevidaEbs_2.jpg?raw=true" width="400" alt="AWS Logo">-
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/Criando_politica_ciclodevidaEbs_3.jpg?raw=true" width="400" alt="AWS Logo">-
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/Criando_politica_ciclodevidaEbs_4.jpg?raw=true" width="400" alt="AWS Logo">-
<img src="https://github.com/HalleyVeras/Laborat-rio2_CursoDpcn_EDN/blob/main/Prints/Criando_politica_ciclodevidaEbs_5final.jpg?raw=true" width="400" alt="AWS Logo">-
---

## Conclusão

Ao final do exercício, consegui provisionar e configurar uma instância EC2 com armazenamento EBS adicional, formatado e montado corretamente. Também configurei snapshots automáticos, garantindo a segurança dos dados.

Esse processo me permitiu compreender melhor as práticas de administração de instâncias EC2 e volumes EBS, incluindo os aspectos de automação e boas práticas de backup.
