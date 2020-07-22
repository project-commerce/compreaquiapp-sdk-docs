## CompreAqui®App SDK

O CompreAquiApp SDK possibilita a você criar uma experiência simples de compra do seu produto, encontrando o fornecedor mais próximo e mais barato ao seu consumidor.

## Instalação

Copie e instale nossa tag script logo antes do fechamento da tag `<body>` ou dentro do `<head>` de sua página.

```html
<script src="https://app.compreaquiapp.com.br/injector.js"></script>
```

## Utilização

Nosso script irá injetar em sua aplicação um novo objeto global, chamado CompreAquiAppSDK, o qual pode ser acessado diretamente pelo nome da váriavel ou através do objeto window.

### Registre sua empresa

```html
<script>
    CompreAquiAppSDK.init('1234');
</script>
```

### Adicione produtos ao carrinho

```html
<script>
    CompreAquiAppSDK.addProduct('7894904015108');
</script>
```

### Registrando o CEP do cliente

```html
<script>
    CompreAquiAppSDK
        .setCEP('00000-000')
        .then(success => {
            if (success) {
                return alert('CEP registrado!');
            }
            alert('CEP não encontrado!');
        });
</script>
```

## SDK API

| Método | Descrição | Retorno | Descrição retorno |
|--|--|--|--|
| init(customer: string) | Adiciona as permissões da sua empresa ao carrinho | void |  |
| openCart() | Abre o carrinho do usuário de forma programática | void | |
| getCEP() | Recupera o CEP registrado na sessão do usuário | string | CEP |
| setCEP(cep: string) | Registra o CEP do usuário na sessão para recuperação de preços próximos | Promise\<string\> | Retorna uma promessa com o CEP registrado. |
| addProduct(cep: string) | Adiciona um produto ao carrinho | Promise\<boolean\> | Retorna uma promessa para controle se o produto foi adicionado ao carrinho ou não |
| addRecipe(idRecipe: string) | Adiciona uma receita ao carrinho | Promise\<boolean\> | Retorna uma promessa para controle se o produto foi adicionado ao carrinho ou não |
| requestCEP() | Solicita o CEP ao usuário com nossa pop up padrão | Promise\<boolean\> | Retorna uma promessa para controle se o CEP foi registrado ou não |

Obs.: Caso um dos métodos de interação com a API de preço como `CompreAquiAppSDK.addProduct` ou `CompreAquiAppSDK.addRecipe` e o CEP não tenham sido registrados na sessão, será realizado o `CompreAquiAppSDK.requestCEP` para captura do mesmo.
