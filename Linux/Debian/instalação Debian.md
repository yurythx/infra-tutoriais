# 🖥️ Tutorial – Instalação do Debian Server (modo básico)

O **Debian** é uma das distribuições Linux mais estáveis e utilizadas em servidores.  
Este guia cobre a instalação padrão usando o **Debian netinst** ou a **ISO completa**.

---

## 1️⃣ Preparar o ambiente

### 1. Baixar a ISO
- Acesse: 👉 [https://www.debian.org/distrib/](https://www.debian.org/distrib/)  
- Escolha:
  - **netinst** → instalador mínimo (baixa pacotes da internet durante a instalação).
  - **ISO completa** → contém tudo no arquivo (ideal para ambientes sem internet).  
- Para **máquinas virtuais**, use a versão **amd64**.

### 2. Criar a mídia de instalação
- **Físico** → use **Rufus** ou **Balena Etcher** para gravar no pendrive.  
- **Virtual (Hyper-V, VirtualBox, VMware)** → basta apontar para a ISO.

---

## 2️⃣ Iniciar a instalação

1. Inicie o computador/VM pelo pendrive ou ISO.  
2. No menu inicial, escolha:
   - `Install` → modo texto (rápido).  
   - `Graphical Install` → modo gráfico (mais amigável).  

---

## 3️⃣ Configurar idioma, local e teclado

- **Language**: selecione `Português (Brasil)` ou outro de preferência.  
- **Location**: `Brasil` ou outro país.  
- **Keyboard layout**: geralmente `Português (Brasil ABNT2)`.  

---

## 4️⃣ Configurar rede

1. O instalador tentará obter **IP via DHCP** automaticamente.  
2. Defina:
   - **Hostname** → nome do servidor (ex: `srv-web01`).  
   - **Domain name** → se não tiver, pode deixar em branco.  

---

## 5️⃣ Criar usuários

- **Senha do root** → senha de administrador.  
- **Novo usuário** → nome e senha para a conta padrão.  

💡 **Dica de segurança**: use uma senha **diferente** da do root.  

---

## 6️⃣ Particionamento de disco

Opções mais comuns:  
- `Guided – use entire disk` → apaga tudo e instala o Debian.  
- `Guided – use entire disk with LVM` → **recomendado** para servidores (permite redimensionamento futuro).  
- `Manual` → para criar partições personalizadas.  

---

## 7️⃣ Configuração de pacotes

1. Escolha o **mirror (repositório Debian)** mais próximo da sua região.  
2. Se pedir **HTTP proxy**, deixe em branco (a menos que realmente utilize proxy na rede).  

---

## 8️⃣ Seleção de software

No menu **Software selection**:  
- **Desmarque** `Debian desktop environment` → para manter o servidor **sem interface gráfica**.  

---

## 9️⃣ Instalar o GRUB

1. Quando perguntar se deseja instalar o **GRUB boot loader**, selecione **Yes**.  
2. Escolha o disco principal (ex: `/dev/sda`).  

---

## 🔟 Finalizar instalação

- Remova o pendrive ou desconecte a ISO.  
- Reinicie o servidor.  
- Faça login com seu usuário ou root.  

---

## ✅ Pós-instalação recomendada

Após logar como **root**, execute:

```bash
# Atualizar sistema
apt update && apt upgrade -y

# Instalar pacotes úteis
apt install sudo vim curl wget net-tools htop -y

# Adicionar seu usuário ao grupo sudo
usermod -aG sudo seu_usuario

# Verificar se o SSH está rodando (caso tenha instalado o SSH server)
systemctl status ssh
