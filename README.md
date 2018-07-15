# ArquiteturaBackEndApiGateway
Projeto criado como resulução do exercício 06 da aula 06 da disciplina Arquitetura de Backend e Microsserviços do curso de pós-graduação de Arquitetura de Softwares Distribuídos e, requisitado pelo professor Marco Mendes.

Este projeto tem como objetivo servir como um gateway para todas as api's criadas anteriormente.
[ArquiteturaBackEndApiLivraria](https://github.com/otavioreis/ArquiteturaBackEndApiLivraria)<br />
[ArquiteturaBackEndApiAuditoria](https://github.com/otavioreis/ArquiteturaBackEndApiAuditoria)<br />
[ArquiteturaBackEndApiAutenticacao](https://github.com/otavioreis/ArquiteturaBackEndApiAutenticacao)<br />
[ArquiteturaBackEndApiPagamento](https://github.com/otavioreis/ArquiteturaBackEndApiPagamento)<br />

O projeto foi desenvolvido utilizando c# juntamente com ASP.NET Core 2.0

## Grupo
**_MATEUS SORIANO_** <br />
**_OTÁVIO AUGUSTO DE QUEIROZ REIS_**

## Informações adicionais do projeto

**URL configurada para o projeto - Ambiente de Desenvolvimento**<br />
http://localhost:55000</br></br>

Seguindo as API's existentes, criamos um caminho (folder) para cada API.

### DESENHO DO GATEWAY:
http://localhost:55000/apilivraria/<br />
http://localhost:55000/apiauditoria/<br />
http://localhost:55000/apiautenticacao/<br />
http://localhost:55000/apipagamento/<br />

Sendo que os links para acesso continuam os mesmos, ou seja, se na api de livraria o endereço era http://localhost:56223/v1/public/livros/3982ecc0-5e96-4aec-8f61-5712f0d090d6 este passará a ser http://localhost:55000/apilivraria/v1/public/livros/3982ecc0-5e96-4aec-8f61-5712f0d090d6


**Json de configuração com todas as rotas ocelot.json**
```json
{
  "ReRoutes": [
    //ApiLivraria

    //Livros
    //private
    {
      "DownstreamPathTemplate": "/v1/private/Livros",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/apilivraria/v1/private/Livros",
      "UpstreamHttpMethod": [ "Post" ]
    },
    //public
    {
      "DownstreamPathTemplate": "/v1/public/Livros",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/apilivraria/v1/public/Livros",
      "UpstreamHttpMethod": [ "Get" ]
    },
    {
      "DownstreamPathTemplate": "/v1/public/Livros/{id}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/apilivraria/v1/public/Livros/{id}",
      "UpstreamHttpMethod": [ "Get" ]
    },
    {
      "DownstreamPathTemplate": "/v1/public/Livros/{id}/comentario/{valor}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/apilivraria/v1/public/Livros/{id}/comentario/{valor}",
      "UpstreamHttpMethod": [ "Post" ]
    },
    {
      "DownstreamPathTemplate": "/v1/public/Livros/autor/{valor}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/apilivraria/v1/public/Livros/autor/{valor}",
      "UpstreamHttpMethod": [ "Get" ]
    },
    {
      "DownstreamPathTemplate": "/v1/public/Livros/isbn/{valor}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/apilivraria/v1/public/Livros/isbn/{valor}",
      "UpstreamHttpMethod": [ "Get" ]
    },
    {
      "DownstreamPathTemplate": "/v1/public/Livros/nome/{valor}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/apilivraria/v1/public/Livros/nome/{valor}",
      "UpstreamHttpMethod": [ "Get" ]
    },
    {
      "DownstreamPathTemplate": "/v1/public/Livros/carrinho/{sessionId}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/apilivraria/v1/public/Livros/carrinho/{sessionId}",
      "UpstreamHttpMethod": [ "Get" ]
    },
    {
      "DownstreamPathTemplate": "/v1/public/Livros/carrinho/{sessionId}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/apilivraria/v1/public/Livros/carrinho/{sessionId}",
      "UpstreamHttpMethod": [ "Post" ]
    },
    {
      "DownstreamPathTemplate": "/apilivraria/v1/public/Livros/{id}/carrinho/{sessionId}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/v1/public/Livros/{id}/carrinho/{sessionId}",
      "UpstreamHttpMethod": [ "Delete" ]
    },

    //Pedidos
    {
      "DownstreamPathTemplate": "/v1/public/Pedidos/{sessionId}/{numeroCartao}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/apilivraria/v1/public/Pedidos/{sessionId}/{numeroCartao}",
      "UpstreamHttpMethod": [ "Post" ]
    },
    {
      "DownstreamPathTemplate": "/v1/public/Pedidos/{idPedido}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 56223
        }
      ],
      "UpstreamPathTemplate": "/apilivraria/v1/public/Pedidos/{idPedido}",
      "UpstreamHttpMethod": [ "Delete" ]
    },

    //ApiAutenticação
    //public
    {
      "DownstreamPathTemplate": "/v1/public/Autenticacao",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 60000
        }
      ],
      "UpstreamPathTemplate": "/apiautenticacao/v1/public/Autenticacao",
      "UpstreamHttpMethod": [ "Post" ]
    },

    //ApiAuditoria
    //private
    {
      "DownstreamPathTemplate": "/v1/private/Auditoria",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 61000
        }
      ],
      "UpstreamPathTemplate": "/apiauditoria/v1/private/Auditoria",
      "UpstreamHttpMethod": [ "Get" ]
    },
    {
      "DownstreamPathTemplate": "/v1/private/Auditoria",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 61000
        }
      ],
      "UpstreamPathTemplate": "/apiauditoria/v1/private/Auditoria",
      "UpstreamHttpMethod": [ "Post" ]
    },

    //ApiPagamento
    //public
    {
      "DownstreamPathTemplate": "/v1/private/Pagamento",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 62000
        }
      ],
      "UpstreamPathTemplate": "/apipagamento/v1/private/Pagamento",
      "UpstreamHttpMethod": [ "Post" ]
    }


  ],
  "GlobalConfiguration": {
    "RequestIdKey": "OcRequestId",
    "AdministrationPath": "/administration"
  }
}
```
