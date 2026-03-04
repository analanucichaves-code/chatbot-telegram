# Telegram Weather Chatbot (n8n)

Este projeto implementa um chatbot no Telegram que retorna informações de clima para uma cidade utilizando a API do OpenWeather e o n8n para automação.

## Tecnologias utilizadas

* n8n
* Telegram Bot API
* OpenWeather API

## Como funciona

O usuário envia o nome de uma cidade no Telegram e o bot retorna:

* Temperatura
* Umidade
* Condição do clima
* Informação se está chovendo ou não

O fluxo no n8n realiza:

1. Recebe mensagem do Telegram
2. Extrai o nome da cidade
3. Consulta a API do OpenWeather
4. Verifica se está chovendo
5. Retorna a resposta formatada ao usuário

## Configuração

Para executar este projeto, é necessário configurar duas credenciais:

### OPENWEATHER_API_KEY

Crie uma conta em:

https://openweathermap.org/api

e obtenha sua chave de API.

### TELEGRAM_BOT_TOKEN

Crie um bot no Telegram usando o BotFather:

https://t.me/BotFather

Após criar o bot, copie o token gerado.

## Como importar o workflow no n8n

1. Abra o n8n
2. Clique em **Import Workflow**
3. Selecione o arquivo `workflow-chatbot-telegram.json`
4. Configure as credenciais do Telegram
5. Configure a variável `OPENWEATHER_API_KEY`

## Como testar o chatbot

1. Execute o workflow no n8n
2. Abra o Telegram
3. Envie o nome de uma cidade para o bot

Exemplo:

rio de janeiro

Resposta esperada:

☀️ Não está chovendo em Rio de Janeiro

🌡 Temperatura: 27°C
💧 Umidade: 73%

☁️ Clima: broken clouds

## Observações

Este repositório não inclui tokens ou credenciais reais por motivos de segurança.
