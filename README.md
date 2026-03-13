Projeto desenvolvido desafio 2 FTR.

# Weather Bot com n8n

Este projeto implementa um bot de Telegram que consulta a API OpenWeather para retornar informações meteorológicas de uma cidade informada pelo usuário.

O workflow foi desenvolvido utilizando a ferramenta n8n.

---

# Configuração necessária

Para executar o workflow corretamente no n8n, é necessário configurar os seguintes itens:

## Variáveis de ambiente

- `OPENWEATHER_API_KEY`: chave da API do OpenWeather

## Credenciais

- Credencial do Telegram configurada no node Telegram do workflow

---

# Como funciona

O bot recebe o nome de uma cidade via Telegram, consulta a API OpenWeather e retorna as informações meteorológicas atuais.

O bot retorna temperatura, umidade e a **condição do clima** (ex.: nublado, céu limpo, chuva), com tratamento para cidade inválida.

Fluxo da automação:

Telegram Trigger → Sanitização da entrada → HTTP Request (OpenWeather API) → IF → resposta ao usuário

---

# Tratamento de erro

O workflow possui tratamento de erro para cidades inválidas.

Após a chamada da API OpenWeather, o fluxo verifica se a resposta contém informações válidas de clima.

- Se a cidade for encontrada, o bot retorna temperatura, umidade e condição do clima.
- Caso a cidade não exista, o fluxo segue pelo branch **FALSE** do nó IF e envia uma mensagem informando que a cidade não foi encontrada.

Isso garante que o usuário receba uma resposta adequada mesmo quando a cidade informada não existir.

---

# Exemplo de uso

Entrada válida no Telegram:

Rio de Janeiro

Resposta do bot:

Clima em Rio de Janeiro  
Temperatura: XX°C  
Umidade: XX%  
Condição: nublado  

---

Entrada inválida:

asdfghjkl

Resposta do bot:

Cidade não encontrada. Tente novamente com o nome correto.

---

## Demonstração

### Consulta válida

![Cidade válida](cidade_valida.png)

### Consulta inválida

![Cidade inválida](cidade_invalida.png)

---

# Arquivo do workflow

O workflow pode ser importado no n8n utilizando o arquivo:

workflow-chatbot-telegramv2.json
---

# Tecnologias utilizadas

- n8n
- Telegram Bot API
- OpenWeather API
