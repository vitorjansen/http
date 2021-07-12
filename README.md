# HTTP (Hypertext Transfer Protocol)

> Objetivo: Este protocolo foi designado para estabelecer as regras de comunicação entre o Cliente e o Servidor.

***

## HTTPS

É a versão segura do HTTP, sua principal funcionalidade é evitar que os dados sejam enviados em texto puro para o servidor.

Para garantir a identidade do dominínio, existem instituições que emitem o ***Certicado Digital***, que é a assinatura da segurança do site.

Os sites seguros não enviam dados sensíveis em textos puros, para isso existem as chaves públicas e privadas. A primeira é guardada pelo Certificado Digital e a segunda armazenada no servidor.

**Criptografia e Descriptografia**

Os dados são criptografados pela chave pública para serem enviados e ao chegar no servidor são descriptografados pela chave privada. Essa método é chamado de ***criptografia assimétrica***

O método acima é mais lento, por depender de uma resoluçao matemática para equivaler as chaves, por isso é usado apenas na primeira autentição. Então, após o primeiro acesso é gerado uma chave secundária para ser reaproveitada nas requisições seguintes. Diferente do primeiro método aqui a chave secudária é a mesma tanto no cliente quanto no servidor, agilizando o processo. Este método é chamado de ***criptografia simétrica***

***

## Endereços

As URL's seguem o seguinte padrão:

`protocolo://dominio:porta/caminho/recurso`

O **domínio** é o nome de um site na web que representa um IP de um servidor. O ***DNS (Domain Name System)*** é o sistema reponsável por traduzir o domínio para um endereço IP no momento da pesquisa.

As **portas**, em geral, são padrões e conhecidas pelo navegador, por isso são omitidas ao escrevermos uma URL.
- Porta padrão HTTP: 80
- Porta padrão HTTPS: 443

Os **recursos** é aquilo que queremos acessar. Para chegar a um recursos por vezes é necessário passar por algum **caminho**.

***

## Request e Response

> ***Request:** É a requisição enviada sempre do cliente ao servidor. A comunicação sempre inicia no lado do cliente.*
> 
> ***Response:** É a resposta do servidor para a requisição.*

As requisições são **stateless**, isso significa que elas não guardam os estados da sessão. Em outras palavras, toda requisição deve ser feita com todas as informações necessárias.

Entretanto para um usuário não precisar ficar sempre se autenticando há o recurso dos **cookies**, que são pequenos arquivos de texto (criados pela aplicação e armazenados no navegador) utilizados para guardar as informações necessárias, como Session ID (autenticação), preferências de usuário (modo escuro na página) etc.

**Sessão HTTP:** Tempo em que o cliente permanece ativo no sistema. Finalizada quando o usuário desloga ou fecha a página.

***

## Status Code (Códigos de resposta)

São códigos utilizado na comunicação para informar que tipo de resposta está sendo retornada.

Classes dos códigos

| Número | Descrição                 |
| :---   | :------                   |
| 1XX    | Informação                |
| 2XX    | Sucesso                   |
| 3XX    | Redirecionamento          |
| 4XX    | Erro no lado do cliente   |
| 5XX    | Erro no lado do servidor  |

[Lista Completa de Status Codes](https://www.w3schools.com/tags/ref_httpmessages.asp)

***

## Métodos HTTP

São as ações que podem ser enviadas pelo protocolo.

| Nome     | Descrição                                      |
| :-----   | :---------                                     |
| `GET`    | Receber dados (params na URL)                  |
| `POST`   | Submeter dados (params no corpo da requisição) |
| `PUT`    | Atualizar um recurso                           |
| `DELETE` | Remover um recurso                             |

***

## Envio de parâmetros na URL

Os parâmetros enviados na URL, seguem o seguinte padrão:

`?nome_do_parametro=valor&nome_do_outro_param=valor`

Em que: 

`?` Representa o início dos argumentos.

`=` Atribui um valor a um parâmetro.

`&` Concatena mais de um parâmetro.

***

## REST (Representational State Transfer)

**Arquitetura**

Recurso

O recurso é o serviço com o qual as aplicações interagem. Em sistemas REST, as URIs devem conter apenas substantivos.

Operação

São as ações dos métodos como GET, POST, PUT, DELETE etc. Representam a ação que será realizada no recurso.

Representação

É o formato da reposta enviada pelo servidor. Exemplos: JSON, XML e HTML.

***

# HTTP2

O HTTP2 veio da necessidade dos clientes de dispositivos móveis para trafegar os dados mais rapidamente. As redes mobile raramente são de alta qualidade, por isso o HTTP2 possui diversas tecnologias de compactação das requisições.

O HTTP2 também implementa por padrões, algumas camadas de segurança, são elas:

- TLS: Acaba sendo obrigatório porque os browsers só suportam o HTTPS nesta versão
- Dados Binários: Os dados são trafegados em binário e não mais em texto puro.
- GZIP: É uma tecnologia especializada em comprimir as RESPOSTAS das comunicações HTTP/2.
- HPACK: É uma tecnologia especializada em comprimir os HEADERS das comunicações HTTP/2.

***Headers Stateful***

No HTTP/2 os cabeçalhos são stateful, isso significa que ele armazena os dados das requisições feitas para ser reutilizado nas próximas. Isso ajuda a diminuir o tráfego na rede, pois headers que já foram enviados uma vez não precisam ser reenviados.

***Server Push***

Este conceito também usado para ganhar performance, permite que o servidor se antecipe às requisições do cliente, podendo empurrar os recursos necessários de uma página antes de serem solicitados, caso seja identificado que serão necessários. Isso diminui o gasto de tempo entre requisição e resposta de todos os recursos.

***Multiplexação***

Torna o envio de requisição e reposta **paralelo**. Deste modo, é possível fazer várias requisições antes mesmo de receber suas repostas, os retornos chegam depois conforme os servidores forem processando-os.