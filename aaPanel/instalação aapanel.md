

Passo a passo – Instalar e configurar aaPanel no Ubuntu Server

## 1) Baixar SEMPRE a versão mais recente (free) do aaPanel
1. Abra o navegador e acesse: [https://www.aapanel.com/](https://www.aapanel.com/)  
2. No topo do site, clique em **Install** ou **Download** (o nome pode variar).  
3. Você será levado para a página com os comandos oficiais de instalação.  

> 💡 **Dica**: sempre use o site oficial para copiar o comando mais recente (evite tutoriais terceiros).

---

## 2) Escolher seu sistema operacional
1. Na página de download, selecione a aba do seu SO:  
   - Ubuntu/Debian  
   - CentOS/RHEL (ou derivados)  
2. Copie o comando de instalação exibido na seção **Free (gratuito)**.  

⚠️ O site pode mostrar comandos diferentes conforme a versão do SO — copie exatamente o que aparecer lá.

---

## 3) Preparar o servidor (Ubuntu/Debian – recomendado)
Conecte via SSH (ex.: PuTTY) e rode:  
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y wget curl unzip
4) Executar o instalador oficial
Cole no terminal o comando copiado do site (o mais atual) e execute.
Ele vai:

Baixar o script oficial

Instalar o painel

Exibir a URL de acesso, usuário e senha

⚠️ Não use comandos de blogs aleatórios; só do site oficial.

5) Anotar as credenciais e acessar o painel
Ao final, o instalador mostra algo como:


aaPanel: http://SEU_IP:8888/xxxxx
username: abc123
password: xyz456
Anote todos os dados.

No navegador, acesse a URL indicada.

Faça login.

6) Liberar a porta do painel (se necessário)
No servidor (Ubuntu/Debian):

sudo ufw allow 8888/tcp
sudo ufw reload
Depois, acesse de novo a URL do painel.

7) Primeiras configurações recomendadas
Dentro do aaPanel:

Mudar a porta do painel:

Settings → Change panel port → ex.: 8822.

Ativar SSL no painel:

Settings → Let’s Encrypt (se for expor na internet).

Escolher a pilha LAMP (Apache) ou LNMP (Nginx):

One-Click → escolha conforme sua necessidade.

8) Utilizando os comandos internos do aaPanel (bt)
O aaPanel possui um utilitário interno (bt) para gerenciar o painel via terminal.
Alguns comandos úteis:

Alterar usuário do painel

bt 5


Alterar senha do painel

bt 6


Exibir as configurações atuais do painel

bt 14

9) Como garantir que você SEMPRE terá a versão mais nova
Marque como favorito a página de Download/Install do site oficial.

Sempre volte nela e copie o comando de instalação de lá antes de instalar em um novo servidor.

Evite “colar comando antigo” guardado — a página oficial é a fonte mais atual.

🔧 Extras úteis (opcional)
Verificar OS/arquitetura:

lsb_release -a || cat /etc/os-release
uname -m


