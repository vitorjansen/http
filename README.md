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

