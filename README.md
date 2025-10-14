# 🔐 Ataques de Força Bruta em Formulários Web com Medusa

Este projeto documenta, de forma teórica e prática, como ataques de força bruta podem ser realizados contra formulários de login em aplicações web utilizando a ferramenta **Medusa**. O objetivo é educacional: demonstrar a metodologia, ferramentas e medidas de mitigação para conscientização e defesa.

> ⚠️ **Aviso Legal:** Este projeto é apenas para fins educacionais e deve ser utilizado exclusivamente em ambientes controlados e autorizados. Nunca realize testes sem permissão explícita.

---

## 📌 Objetivos

- Demonstrar como simular ataques de força bruta com Medusa.
- Explicar como identificar formulários vulneráveis.
- Apresentar boas práticas de mitigação.
- Compartilhar wordlists e scripts de exemplo.

---

## 🧰 Ferramentas Utilizadas

- **Kali Linux** (máquina atacante)
- **Medusa** – ferramenta de força bruta rápida e modular
- **DVWA (Damn Vulnerable Web Application)** – ambiente web vulnerável
- **Burp Suite** – interceptação e análise de requisições HTTP
- **Wordlists** – listas de usuários e senhas comuns

---

## 🧪 Metodologia

### 1. Identificação do Formulário

- A aplicação DVWA possui um formulário de login acessível em `/dvwa/login.php`.
- Parâmetros identificados via Burp Suite:
  - `username`
  - `password`
  - Resposta de falha: `"Login failed"`

### 2. Comando Medusa Simulado

```bash
medusa -h 192.168.56.102 -U wordlists/usernames.txt -P wordlists/common_passwords.txt -M http \
  -m DIR:/dvwa/login.php -m FORM:"username=^USER^&password=^PASS^:Login failed"
