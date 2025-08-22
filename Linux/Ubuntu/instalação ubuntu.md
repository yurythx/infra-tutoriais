# Tutorial – Instalação do Ubuntu Server

O **Ubuntu Server** é uma das distribuições Linux mais populares para servidores.  
Possui suporte longo (**LTS** – Long Term Support), com atualizações por 5 anos, além de grande comunidade e fácil manutenção.  
Este guia cobre a instalação padrão usando a **ISO do Ubuntu Server**.  

---

## 1️⃣ Preparar o ambiente

### 1. Baixar a ISO
- Acesse: [https://ubuntu.com/download/server](https://ubuntu.com/download/server)  
- Escolha sempre a versão **LTS** (ex: 24.04 LTS).  

### 2. Criar mídia de instalação
- **Servidor físico:** grave a ISO em um pendrive usando **Rufus** ou **Balena Etcher**.  
- **Máquina virtual (VM):** basta apontar para a ISO (Hyper-V, VirtualBox, VMware, Proxmox, etc.).  

---

## 2️⃣ Iniciar a instalação

1. Inicialize o computador/VM pelo **pendrive** ou **ISO**.  
2. No menu inicial, escolha:  
   - `Install Ubuntu Server`.  

---

## 3️⃣ Configurações iniciais

### Idioma, Localização e Teclado
- **Idioma:** Português (Brasil) ou outro de preferência.  
- **Localização:** Brasil (ou seu país).  
- **Teclado:** Português (Brasil ABNT2).  

---

## 4️⃣ Configurar rede

1. O instalador tentará obter IP via **DHCP** automaticamente.  
2. Caso queira IP fixo, configure manualmente (recomendado para servidores).  
3. Defina o **Hostname** (exemplo: `srv-web01`).  

---

## 5️⃣ Particionamento de disco

Opções disponíveis:  
- **Use entire disk:** apaga todo o disco e cria partições automáticas.  
- **Use LVM (recomendado):** permite redimensionar volumes futuramente.  
- **Manual:** para configurações avançadas (RAID, múltiplos discos, etc.).  

---

## 6️⃣ Criar usuário

- Informe o **nome do administrador** e **senha**.  
- O **root não é habilitado por padrão**.  
- Use `sudo` para executar comandos administrativos.  

---

## 7️⃣ Finalizar instalação

1. O sistema será instalado.  
2. Quando solicitado, remova o pendrive/ISO.  
3. Reinicie o servidor e faça login com o usuário criado.  

---

## ✅ Pós-instalação recomendada

Após logar no servidor:  

```bash
# Atualizar sistema
sudo apt update && sudo apt upgrade -y

# Instalar pacotes úteis
sudo apt install vim curl wget net-tools htop -y

# Confirmar que o SSH está rodando
sudo systemctl status ssh
