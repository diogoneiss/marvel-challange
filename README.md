# Desafio Marvel
Lista os eventos de eventos do universo marvel.

Eventos são grandes alterações na storyline do universo.

# Tecnologias utilizadas
- SwiftUI
- KingFisher: Para carregamento e cache das imagens
- Alamofire: Para realizar os requets

# API
https://developer.marvel.com

Documentação do endpoint 
https://developer.marvel.com/docs#!/public/getEventsCollection_get_18

## Autorizacao
A autorização é feita com parametros de url 
- `apikey`: chave-publica 
- `ts`: timestamp 
- `hash`: hash mds do `ts` + `chavePrivada` + `chavePublica`


Exemplo de chamada:
https://gateway.marvel.com/v1/public/events?apikey=2dd999c3ed11ed12eb9a4fd38444b3a4&hash=2188b52c39d8c951a28828615e66e288&limit=20&offset=0&ts=4700981356936724908

# Arquitetura

## Service
O protocolo `Service` define os endpoints disponiveis para consumo

Implementações concreta `MarvelService`. Permite a implementação de um __Servico de mock__

### TypeAlias
Definem em um local os tipos a serem utilizados no service
`EventsType` - Tipo do evento
`EventsHandler` - Tipo do retorno 

### MarvelService

#### MarvelService::fetchApi
Function genérica para realizar os requests para endpoints da `https://gateway.marvel.com/v1/public`

Params: 
- endpoint: Endereco de endpoint
- parameters: Parametros, se existentes
- type: Typo de retorno
- completionHandler: Handler de retorno


## Views

### HomeView::body
Foi utilizada somente uma `LazyVGrid` com numero de colunas dinâmico para fazer a visualização entre lista e grid.

## ViewModel

`HomeViewModel` é responsável por fazer o load inicial e carregar as páginas subsequentes quando necessário
