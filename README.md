# CardCursos Flexbox

Projeto front-end desenvolvido para demonstrar a criação de uma grade de cards de cursos de tecnologia utilizando HTML5, CSS3 e Flexbox.

A página apresenta seis cards com imagens, descrição textual e um link de acesso. O layout se adapta a diferentes tamanhos de tela por meio de Flexbox e media queries.

## Objetivos do projeto

- Praticar a estruturação semântica de uma página HTML.
- Aplicar Flexbox para organizar elementos em linhas e colunas.
- Criar uma grade de cards responsiva.
- Trabalhar com larguras calculadas usando a função `calc()`.
- Utilizar imagens locais dentro de componentes reutilizáveis.
- Ajustar a quantidade de cards por linha conforme a largura da tela.

## Tecnologias utilizadas

- **HTML5:** estrutura e conteúdo da página.
- **CSS3:** estilos, espaçamentos, bordas, sombras e responsividade.
- **Flexbox:** organização dos cards e distribuição dos elementos.
- **Media queries:** adaptação do layout para tablets e celulares.

O projeto não utiliza JavaScript, bibliotecas externas, frameworks ou gerenciadores de pacotes.

## Estrutura de arquivos

```text
CardCursos_Flexbox/
├── index.html
├── index.css
├── README.md
└── assets/
    ├── apache.jpg
    ├── apache.png
    ├── css3.png
    ├── html5.png
    ├── jquery.png
    ├── unity.jpg
    ├── unity.png
    ├── xamarin.jpg
    └── xamarin.png
```

### `index.html`

Contém a estrutura principal da página:

- Define o idioma, a codificação e a configuração da viewport.
- Importa o arquivo `index.css`.
- Organiza os cards dentro de uma seção com a classe `.wrapper`.
- Representa cada curso com um elemento semântico `<article>`.
- Exibe a imagem, a descrição e o link de cada card.

Os cursos atualmente apresentados são:

1. HTML5
2. CSS3
3. Apache
4. jQuery
5. Unity
6. Xamarin

### `index.css`

Contém toda a apresentação visual do projeto:

- Remove margens e espaçamentos padrão do navegador.
- Define o modelo de dimensionamento com `box-sizing: border-box`.
- Configura o container Flexbox principal.
- Define o tamanho, a borda e a sombra dos cards.
- Mantém as descrições com alturas mais equilibradas usando `flex-grow`.
- Controla o tamanho das imagens.
- Aplica regras específicas para telas menores.

### `assets/`

Armazena as imagens exibidas nos cards. Os arquivos podem ser substituídos por outras imagens, desde que os caminhos correspondentes no HTML também sejam atualizados.

## Como o layout funciona

A seção `.wrapper` é o container dos cards:

```css
.wrapper {
    display: flex;
    flex-wrap: wrap;
    max-width: 900px;
    width: 100%;
    margin: 50px auto;
}
```

- `display: flex` transforma a seção em um container Flexbox.
- `flex-wrap: wrap` permite que os cards passem para a linha seguinte quando não houver espaço suficiente.
- `max-width: 900px` limita a largura máxima do conteúdo.
- `width: 100%` permite que o container ocupe o espaço disponível em telas menores.
- `margin: 50px auto` centraliza horizontalmente o container e adiciona espaço acima e abaixo.

Cada card ocupa aproximadamente um terço da largura do container em telas grandes:

```css
.card {
    width: calc(100% / 3 - 20px);
    margin: 10px;
}
```

O valor de `20px` desconta as margens laterais do card. Assim, três cards podem ocupar a mesma linha sem ultrapassar a largura do wrapper.

## Responsividade

O projeto possui três faixas principais de adaptação:

### Telas grandes

Acima de `768px`, são exibidos até três cards por linha.

### Tablets e telas médias

Até `768px`, cada card passa a ocupar metade da largura disponível:

```css
.card {
    width: calc(100% / 2 - 20px);
}
```

O resultado esperado é de dois cards por linha.

### Celulares

Até `425px`, cada card ocupa praticamente toda a largura:

```css
.card {
    width: calc(100% - 20px);
}
```

O resultado esperado é de um card por linha.

### Telas muito pequenas

Até `320px`, as margens laterais são removidas e a borda e a sombra são simplificadas para aproveitar melhor o espaço reduzido.

## Imagens dos cards

A altura das imagens é calculada proporcionalmente à largura do card. A propriedade `object-fit: cover` faz com que a imagem preencha sua área sem distorção, podendo cortar pequenas partes nas bordas.

```css
.card_img img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
```

## Como executar

Como este é um projeto estático, não é necessário instalar dependências.

### Opção 1: abrir diretamente

1. Abra a pasta do projeto.
2. Abra o arquivo `index.html` em um navegador.

### Opção 2: usar um servidor local

Se o VS Code tiver a extensão Live Server instalada:

1. Abra `index.html`.
2. Clique com o botão direito no arquivo.
3. Selecione **Open with Live Server**.

Usar um servidor local é útil para visualizar as alterações automaticamente enquanto o CSS e o HTML são editados.

## Como personalizar

### Alterar o texto de um card

Edite o conteúdo do elemento `<p>` dentro de `.card_descricao` no arquivo `index.html`.

### Alterar uma imagem

Substitua o caminho do atributo `src`:

```html
<img src="./assets/nova-imagem.png" alt="Descrição da imagem">
```

O texto do atributo `alt` deve descrever a imagem para melhorar a acessibilidade.

### Adicionar um novo card

Copie um elemento `<article class="card">`, altere a imagem, o texto e o link, e mantenha a nova cópia dentro de `.wrapper`.

### Alterar a quantidade de cards por linha

A quantidade pode ser modificada ajustando a propriedade `width` de `.card` e os breakpoints das media queries.

## Possíveis melhorias

- Substituir os textos demonstrativos por descrições reais dos cursos.
- Adicionar títulos para cada curso.
- Criar páginas ou destinos reais para os links `Ver mais`.
- Adicionar estados visuais para `:hover` e `:focus`.
- Melhorar a acessibilidade com títulos, foco visível e navegação por teclado.
- Centralizar os cards com `justify-content: center` caso a última linha precise ficar centralizada.
- Adicionar um cabeçalho e uma identidade visual para a página.

## Licença

Este projeto é destinado a fins educacionais e de prática de HTML e CSS.
