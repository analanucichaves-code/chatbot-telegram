# Weather Bot com N8N

Este projeto implementa um bot de Telegram que consulta a API OpenWeather para retornar informações meteorológicas de uma cidade informada pelo usuário.

O workflow foi desenvolvido utilizando a ferramenta **N8N**.

---

# Como funciona

O bot recebe o nome de uma cidade via Telegram, consulta a API OpenWeather e retorna as informações meteorológicas atuais.

Fluxo da automação:

Telegram Trigger → HTTP Request (OpenWeather API) → IF → resposta ao usuário

---

# Tratamento de erro

O workflow possui tratamento de erro para cidades inválidas.

Após a chamada da API OpenWeather, o fluxo verifica se o campo `weather[0].main` existe na resposta.

- Se existir, significa que a cidade foi encontrada e o bot retorna as informações meteorológicas.
- Caso contrário, o fluxo segue pelo branch **FALSE** do nó IF e envia uma mensagem informando que a cidade não foi encontrada.

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

Não encontrei essa cidade. Tente novamente com o nome correto.

---

# Arquivo do workflow

O workflow pode ser importado no N8N utilizando o arquivo:

`workflow.json`

---

# Tecnologias utilizadas

- N8N
- Telegram Bot API
- OpenWeather API
