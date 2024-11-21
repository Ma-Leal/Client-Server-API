# Client-Server-API

Este projeto implementa dois sistemas em Go (`client.go` e `server.go`) que trabalham juntos para consultar a cotação do dólar e registrar os dados em um banco de dados SQLite. O `client.go` solicita a cotação ao `server.go`, que consome uma API externa e registra os dados no banco. 

## Requisitos

### Client (`client.go`)
- [x] Realizar uma requisição HTTP para o servidor (`server.go`) solicitando a cotação do dólar.
- [x] Utilizar o `package context` com um timeout máximo de **300ms** para receber o resultado do servidor.
- [x] Receber do servidor apenas o valor atual do câmbio (campo `bid` do JSON).
- [x] Registrar a cotação recebida em um arquivo chamado `cotacao.txt` no formato: Dólar: {valor}
- [x] Registrar nos logs caso o timeout seja atingido.

### Server (`server.go`)
- [x] Disponibilizar um endpoint HTTP `/cotacao` na porta **8080**.
- [x] Consumir a API de cotação no endereço: https://economia.awesomeapi.com.br/json/last/USD-BRL
- [x] Utilizar o `package context` com um timeout máximo de **200ms** para realizar a consulta na API.
- [x] Registrar no banco de dados SQLite cada cotação recebida.  
- Timeout máximo de **10ms** para persistência dos dados.
- [x] Retornar para o cliente um JSON