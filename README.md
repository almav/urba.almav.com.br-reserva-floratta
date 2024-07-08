# Almav Mapas Interativos API

Este repositório contém exemplos e documentação para utilizar a API do Mapa Interativo da Almav.

![almav Mapa Interativo](https://raw.githubusercontent.com/almav/urba.almav.com.br-reserva-floratta/main/assets/images/screen01.png)

**Chave da API:** `c3bcfb0b-b0df-45ba-a63c-1c7d7521e48a`

**Demonstração:**

- Tela inteira (index.html): 
  - https://urba.almav.com.br/reserva-floratta/

- Website DIV (exemplo02.html):
  - https://urba.almav.com.br/reserva-floratta/exemplo02.html
  
- Aviso de rolagem da página (exemplo03.html):
  - https://urba.almav.com.br/reserva-floratta/exemplo03.html
  - 
- Mapa em perspectiva (exemplo04.html):
  - https://urba.almav.com.br/reserva-floratta/exemplo04.html
  
- Off-line (offline/index.html):
  - https://urba.almav.com.br/reserva-floratta/offline
  - Acesse a página do mapa interativo em um local onde você tenha conexão com a internet.
  - Deixe a página carregar completamente. Isso inclui todos os elementos do mapa e os dados associados. Navegue pelo mapa para garantir que todas as áreas que você deseja visualizar estejam carregadas.
  - Nossa aplicação utiliza uma tecnologia chamada "Service Worker" para armazenar os dados do mapa no seu dispositivo. Isso permite que você acesse o mapa mesmo sem conexão com a internet. Uma vez que a página tenha sido carregada completamente, o Service Worker armazenará automaticamente os dados necessários para o uso offline.
  - **Importante:** Acesse a versão online do mapa regularmente para garantir que você tenha os dados mais recentes armazenados para uso offline.
  - Mapa Não Carrega Offline:
    - Verifique se você acessou a versão online do mapa e permitiu que ele carregasse completamente enquanto estava conectado à internet.
    - Certifique-se de que o Service Worker está ativo no seu navegador. Em navegadores como o Chrome, você pode verificar isso nas configurações de "Ferramentas do Desenvolvedor".
  - Instalar o Webapp (Opcional):
    - Alguns navegadores modernos, como o Google Chrome, oferecem a opção de instalar o webapp diretamente no seu dispositivo. Você verá um botão de instalação na barra de endereços ou um prompt perguntando se deseja "Adicionar à tela inicial".
    - ![alt text](https://raw.githubusercontent.com/almav/urba.almav.com.br-reserva-floratta/main/assets/images/instalar.png)

## Exemplo de Uso

1. Crie regras CSS para uso do mapa.

```html
    <style>
        body {
            margin: 0;
            padding: 0;
            background-color: #333;
            overflow: hidden;
        }

        html,
        body,
        #map {
            height: 100%; /* IMPORTANTE: definir a altura do elemento */ 
        }

        #map {
            position: absolute;
            top: 0;
            bottom: 0;
            width: 100%;
        }
    </style>
```

2. Crie uma função `initMap` para inicializar o mapa.

 ```html
    <script>
        /*
            Inicializar o mapa
            -------------------
            * A função `initMap` será executada após o carregamento do mapa.
            * O parâmetro da url `callback` é o nome da função que será 
            executada após o carregamento do mapa. 
            Por exemplo: `callback=initMap`.
        */
        function initMap() {
            // Criar o objeto do mapa e definir o ID `map` como destino
            map = new almav.maps.Map(document.getElementById('map'), {
                fitBounds: true, // Ajustar o zoom para os limites dos elementos
                showButtonsZoom: true, // mostra botões de zoom in e zoom out
            });
        }

    </script>
```

3. Crie um elemento HTML para exibir o mapa.
   
```html
    <!-- Esse é o elemento que receberá o mapa -->
    <div id="map"></div>
```

4. Crie o script do mapa com chave de API e nome da função de callback.

```html
    <!-- Importante -->
    <!-- key: é a chave de API -->
    <!-- callback: é o nome da função que será executada após o carregamento do mapa -->
    <script
        src="https://maps.app.almav.com/apiv1/js/almav-initmap.js?key=c3bcfb0b-b0df-45ba-a63c-1c7d7521e48a&callback=initMap"
        defer></script>
```


## Resumo

1. **Incluir Metadados e Configurações Básicas:**
   - Configure os metadados no `<head>` da sua página HTML, incluindo charset, viewport, descrições e ícones.

2. **Estilizar a Página:**
   - Defina o estilo básico para o corpo e o mapa. Certifique-se de que o elemento `#map` tenha largura e altura definida.

3. **Inicializar o Mapa:**
   - Crie uma função `initMap` para inicializar o mapa. Esta função será chamada quando o script do mapa for carregado.
   - Use a função `almav.maps.Map` para criar o mapa e configure-o conforme necessário (ex.: ajuste de zoom, botões de zoom).

4. **Carregar o Script do Mapa:**
   - Inclua o script da API do Almav Mapas Interativos no final do corpo do documento. Use a chave de API e a função de callback configuradas.

## Observações

- Certifique-se de que a chave de API (`key`) e o nome da função de callback (`callback`) estejam corretos na URL do script.
- Adapte os estilos e configurações do mapa conforme as necessidades do seu projeto.

## Dependências

- [MapLibre GL JS](https://maplibre.org/) para renderização de Mapas Interativos e a API personalizada da Almav para configurações específicas do mapa.
- [PhotoSwipe](https://github.com/dimsemenov/PhotoSwipe) para exibir imagens e galerias.

Todas as dependências são instaladas automicamente com a API. Você não vai precisar instalar manualmente ou incluir arquivos adicionais.

Para mais informações, acesse [https://almav.com/](https://almav.com/).

## Requisitos do Mapa Interativo

1. **Compatibilidade com ES Modules:**
   - A API do Mapa Interativo da Almav utiliza módulos ES (ES Modules). Certifique-se de que o ambiente onde a aplicação será executada seja compatível com ES Modules. Navegadores modernos como Google Chrome, Mozilla Firefox, Microsoft Edge e Safari oferecem suporte completo para ES Modules.

2. **Suporte a WebGL:**
   - A renderização do mapa depende do suporte a WebGL. Verifique se o navegador utilizado oferece suporte a WebGL. Caso contrário, o mapa não poderá ser exibido. Navegadores modernos, incluindo Google Chrome, Mozilla Firefox, Microsoft Edge e Safari, geralmente oferecem suporte a WebGL. Para verificar se o navegador é compatível, você pode acessar [get.webgl.org](https://get.webgl.org/).

3. **Execução Fora de Iframes:**
   - O mapa não deve ser executado dentro de iframes. Isso ocorre porque a API necessita acessar o sinal de GPS do dispositivo para funcionalidades de geolocalização, e a execução dentro de um iframe pode impedir o acesso a esse sinal. Portanto, a página que contém o mapa deve ser carregada diretamente no navegador e não embutida em outra página através de um iframe.

### Compatibilidade com Navegadores Modernos

- **Google Chrome:** A partir da versão 61, o Chrome oferece suporte completo para ES Modules e WebGL.
- **Mozilla Firefox:** A partir da versão 60, o Firefox oferece suporte completo para ES Modules e WebGL.
- **Microsoft Edge:** A partir da versão 16, o Edge oferece suporte completo para ES Modules e WebGL.
- **Safari:** A partir da versão 10.1, o Safari oferece suporte completo para ES Modules e WebGL.

Certifique-se de que os usuários do mapa estejam utilizando versões atualizadas desses navegadores para garantir a melhor experiência e funcionalidade completa.