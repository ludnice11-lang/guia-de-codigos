# Guia de Códigos da Ludnice

Anotações, comandos e aprendizados durante meus estudos em Desenvolvimento de Software.

---

## O q é cada coisa

- **Terminal (linha de comando)**: janela onde a gente dá ordens p/ o computador escrevendo, em vez de clicar. No Windows tem o PowerShell e o Prompt de Comando (cmd).
- **VS Code**: programa onde a gente escreve e edita os códigos. Já vem c/ terminal dentro.
- **Git**: programa q guarda o histórico das mudanças dos arquivos (os commits). Fica no computador.
- **GitHub**: site onde a gente guarda os projetos do Git na internet, p/ ver de qqr lugar e mostrar p/ outras pessoas.
- **Git Extensions**: programa c/ janelas e botões p/ usar o Git sem digitar os comandos.
- **Markdown**: jeito de formatar texto c/ símbolos simples (`#`, `**`, `-`). Arquivos `.md`, tipo esse README.
- **HTML5**: linguagem q monta o esqueleto da página (títulos, textos, listas, links). O 5 é a versão + nova.
- **CSS**: linguagem q deixa a página bonita (cores, tamanhos, espaços, posição).
- **JavaScript**: linguagem q dá ação p/ página (clicar num botão e algo acontecer, por ex).
- **TypeScript**: JavaScript c/ + regras, p/ achar erros antes. É o q o Angular usa.
- **Angular**: ferramenta p/ criar sites maiores, dividindo a página em pedaços (componentes).
- **Live Server**: extensão do VS Code q abre o site no navegador e atualiza sozinho qdo salva.
- **GitHub Pages**: parte do GitHub q coloca o site no ar, c/ um endereço p/ qqr pessoa abrir.
- **GitHub Actions (o robô)**: robô do GitHub q faz tarefas sozinho. No meu portfólio, td vez q dou `git push`, ele monta o site e publica no GitHub Pages. As ordens dele ficam no arquivo `.github/workflows/deploy.yml`. (Pq precisa dele: o navegador ñ entende Angular. Qdo o projeto é Angular e vai p/ o ar, ele tem q ser traduzido antes p/ HTML, CSS e JavaScript normais, c/ o `ng build`. O robô faz essa tradução e publica sozinho. Site só c/ HTML e CSS ñ precisa de tradução.)

### Arquivos de um projeto Angular

**Dentro de `src/app`** (o componente principal):

| Arquivo | Pra q serve |
| --- | --- |
| `app.html` | O conteúdo da página: títulos, textos, listas, links. É onde + escrevo. |
| `app.css` | O estilo **só** do `app.html`. |
| `app.ts` | O "cérebro" do componente: liga o `app.html` c/ o `app.css` e guarda as informações (tipo listas do `@for`). |
| `app.config.ts` | Configurações do projeto td. Quase nunca mexe. |
| `app.routes.ts` | As **rotas**: qual página aparece em cada endereço (ex: `/sobre`). Site de 1 página só deixa vazio. |
| `app.spec.ts` | **Testes**: código q confere se o componente funciona. Por enquanto pode ignorar. |

**Dentro de `src`:**

| Arquivo | Pra q serve |
| --- | --- |
| `index.html` | A página "casca". Tem a tag `<app-root>`, onde o Angular encaixa o componente. Quase nunca mexe. |
| `main.ts` | O botão de ligar: 1º arquivo q roda. Ñ mexe. |
| `styles.css` | Estilo da página **toda** (ex: fonte e fundo do `body`). |

> **Importante:** `styles.css` vale p/ td o site. `app.css` vale só p/ o `app.html`.

**Fora do `src`** (a raiz do projeto):

| Arquivo/pasta | Pra q serve |
| --- | --- |
| `package.json` | Lista dos pacotes do projeto e dos comandos, tipo o `npm start`. |
| `node_modules` | Pasta c/ td os pacotes baixados. Enorme, ñ vai p/ o GitHub. Ñ mexe. |
| `angular.json` | Configurações do Angular. |
| `tsconfig...json` | Configurações do TypeScript. |
| `public` | Arquivos q vão do jeito q tão p/ o site, tipo o ícone da aba (`favicon.ico`). |
| `dist` | O site já traduzido pelo `ng build`. |
| `.gitignore` | Lista do q o Git ignora (tipo o `node_modules`). |
| `.vscode`, `.editorconfig`, `.prettierrc` | Configurações do VS Code e de como organizar o código. |

> No dia a dia, quase sempre mexo só em 3: `app.html`, `app.css` e `styles.css`.

---

## Terminal e Navegação

### Ver em qual pasta estou

```bash
pwd
```

Mostra o caminho completo da pasta onde o terminal está agora (vem do inglês *print working directory*, "mostrar a pasta de trabalho").

### Ver arquivos e pastas

```bash
dir
```

Lista os arquivos e pastas existentes no local atual. O comando `ls` faz a mesma coisa.

### Entrar em uma pasta

```bash
cd nome-da-pasta
```

Exemplo:

```bash
cd exerciciodeavaliacao
```

### Voltar para a pasta anterior

```bash
cd ..
```

Volta um nível na estrutura de pastas.

### Criar uma pasta nova

```bash
mkdir nome-da-pasta
```

Cria uma pasta nova no local onde o terminal está.

### Criar um arquivo novo

```bash
ni nome-do-arquivo.txt
```

Cria um arquivo vazio na pasta q vc tá (`ni` = *New Item*, "novo item"). Funciona no PowerShell, q é o terminal do Windows. No Git Bash é `touch nome-do-arquivo.txt`.

### Apagar um arquivo

```bash
del nome-do-arquivo.txt
```

Apaga o arquivo. Cuidado: ñ vai p/ lixeira, some de vez!

### Limpar a tela do terminal

```bash
cls
```

Limpa td q tá escrito na tela. Os arquivos ñ são apagados. O `clear` faz a msm coisa.

> **Truques do teclado no terminal**
>
> - **Tab**: começa a digitar o nome da pasta ou arquivo e aperta `Tab`, o terminal completa sozinho.
> - **Seta p/ cima ↑**: mostra os comandos q vc já usou, p/ ñ ter q escrever td de novo.
> - **Ctrl + C**: para um comando q travou ou tá demorando.

### Abrir a pasta atual no VS Code

```bash
code .
```

Abre no VS Code a pasta em que o terminal está atualmente.

### Criar um projeto Angular

```bash
ng new nome-do-projeto
```

Cria a pasta do projeto já c/ td do Angular dentro.

> **Importante:** 1º cria o projeto c/ `ng new` no terminal, dps entra na pasta (`cd nome-do-projeto`) e abre no VS Code (`code .`). Se abrir uma pasta vazia no VS Code antes, ela ñ vira Angular sozinha.

---

## Ver o site no navegador

### Projeto só c/ HTML e CSS: Live Server

Clica c/ o botão direito no `index.html` e escolhe **Open with Live Server**, ou clica em **Go Live** lá embaixo no VS Code.

> **Importante:** o Live Server ñ funciona c/ Angular, pq o navegador ñ entende Angular sem a tradução.

### Projeto Angular: npm start

```bash
npm start
```

Roda o Angular e deixa o site no endereço `http://localhost:4200`. Dps aperta **o** e **Enter** q o site abre no navegador.

> Funciona em qqr terminal (CMD, PowerShell ou o do VS Code), mas o terminal tem q estar dentro da pasta do projeto. P/ parar: `Ctrl + C`.

---

## Git

O Git guarda o histórico das mudanças dos arquivos.

commit são "fotos" das atualizações. Cada vez que dá commit, ele fica com a ultima foto. Mas guarda todas as mudanças como uma espécie de histórico. fica tudo guardado no computador e se der push fica também no gitHub.

### Começar a usar o Git em uma pasta

```bash
git init
```

Transforma a pasta num **repositório** (pasta q o Git fica de olho). Só precisa fazer 1 vez por projeto.

### Copiar um projeto do GitHub para o computador

```bash
git clone endereço-do-repositório
```

Exemplo:

```bash
git clone https://github.com/usuario/nome-do-projeto.git
```

Baixa o projeto todo, c/ o histórico de commits. O endereço tá no botão verde **Code** do GitHub.

### Ver o que mudou

```bash
git status
```

Mostra os arquivos q foram modificados, criados e apagados.

### Preparar os arquivos para o commit

```bash
git add .
```

Separa os arquivos alterados p/ entrarem no próximo commit. 


Isso: `.` significa: "tudo desta pasta".

### Salvar um commit

```bash
git commit -m "mensagem explicando a mudança"
```

Cria o commit. O `-m` serve para escrever a atualização. 

### Enviar para o GitHub

```bash
git push
```

Envia commits do computador para o GitHub.

### Trazer as novidades do GitHub

```bash
git pull
```

É o contrário do `push`: traz p/ o computador os commits q tão no GitHub e vc ainda ñ tem (ex: qdo edita algo direto no site).

### Ver o histórico de commits

```bash
git log --oneline
```

Mostra os commits q já fiz, 1 por linha, do + novo p/ o + antigo. Sem o `--oneline` aparece + coisa (autor, data...).

> Se a lista for grande e o terminal "travar" c/ um `:` no final, aperta **q** p/ sair.

> **Resumo do dia a dia**
>
> ```bash
> git status
> git add .
> git commit -m "o que eu mudei"
> git push
> ```

---

## Markdown

Markdown é um jeito de deixar o texto formatado (tipo esse README) usando uns símbolos simples. Os arquivos terminam em `.md`.

### Títulos

```markdown
# Título grande
## Título médio
### Título pequeno
```

Qto + `#`, menor o título.

### Negrito e itálico

```markdown
**texto em negrito**
*texto em itálico*
```

### Listas

```markdown
- item com bolinha
- outro item

1. item numerado
2. outro item
```

### Código

````markdown
Um comando no meio da frase: `git status`

Um bloco de código:

```bash
git status
```
````

1 crase de cada lado (`` ` ``) é p/ pouco código. 3 crases é p/ um bloco. A palavra dps das crases (`bash`) diz qual é a linguagem, aí o VS Code colore.

### Tabela

```markdown
| Arquivo | Pra q serve |
| --- | --- |
| app.html | O conteúdo da página |
| app.css | O estilo do app.html |
```

Fica assim:

| Arquivo | Pra q serve |
| --- | --- |
| app.html | O conteúdo da página |
| app.css | O estilo do app.html |

- **1ª linha**: os títulos das colunas. Cada `|` separa uma coluna da outra.
- **2ª linha**: `| --- | --- |` avisa q ali começa a tabela. 1 `---` p/ cada coluna.
- **Dali p/ baixo**: cada linha é uma linha da tabela.

> **Regras:** td linha tem q ter o msm nº de colunas. Ñ precisa alinhar os `|`. Os quadrados ñ são escritos, o VS Code e o GitHub desenham sozinhos qdo vê formatado (`Ctrl + Shift + V`).

### Outras coisas úteis

```markdown
> Isto vira uma caixa de citação / observação

---  (linha separadora)

[texto do link](https://www.github.com)
```

---

## HTML

HTML é o "esqueleto" da página: diz o q aparece (títulos, textos, listas, links...). Cada coisa fica dentro de uma **tag**, q abre `<tag>` e fecha `</tag>`.

### Comentário

```html
<!-- isto é um comentário, ñ aparece na página -->
```

### Títulos (h1 até h6)

```html
<h1>Título + importante</h1>
<h2>Subtítulo</h2>
<h6>Título - importante</h6>
```

O `h1` é o maior e + importante, o `h6` é o menor.

### Parágrafo

```html
<p>Olá! Sou um parágrafo</p>
```

### Formatação de texto

```html
<strong>negrito</strong>
<em>itálico</em>
<u>sublinhado</u>
texto <br> outra linha
```

- `strong` = negrito
- `em` = itálico
- `u` = sublinhado
- `br` = quebra de linha. Ñ precisa fechar!

> Dá p/ colocar uma tag dentro da outra: `<strong>Olá <em>Marisa</em></strong>` fica negrito e itálico ao msm tempo.

### Listas

```html
<!-- lista c/ bolinha -->
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
</ul>

<!-- lista numerada -->
<ol>
    <li>Item 1</li>
    <li>Item 2</li>
</ol>
```

- `ul` = *unordered list*, lista ñ ordenada (bolinha)
- `ol` = *ordered list*, lista ordenada (número)
- `li` = *list item*, cada item da lista

### Links

```html
<a href="https://www.google.com" target="_blank" rel="noopener noreferrer">Visitar Google</a>
```

- `href` = endereço p/ onde o link vai
- `target="_blank"` = abre numa aba nova
- `rel="noopener noreferrer"` = proteção p/ qdo abre em aba nova (sempre usar junto c/ o `_blank`)

### Link p/ voltar ao topo

```html
<header id="topo">...</header>

<a href="#topo">Voltar ao início</a>
```

O `#` + o `id` faz o link pular p/ aquela parte da msm página.

### Div

```html
<div class="main">
    <div class="esquerdo">...</div>
    <div class="direita">...</div>
</div>
```

`div` é uma "caixa" p/ agrupar coisas. Qdo uma div tá dentro da outra, a de fora é a **pai** e as de dentro são as **filhas**.

### Tags semânticas

São tags q já dizem pelo nome o q aquela parte é:

```html
<header>cabeçalho, sempre em cima</header>

<main>
    <section>uma parte do conteúdo</section>
    <section>outra parte</section>
</main>

<footer>rodapé, final da página</footer>
```

- `header` = cabeçalho
- `main` = conteúdo principal (só 1 por página)
- `section` = uma seção/parte do conteúdo
- `footer` = rodapé

### class e id

```html
<h1 class="titulo">Ludnice Machado</h1>
<header id="topo">...</header>
```

São "apelidos" p/ achar a tag no CSS (ou no link, no caso do `id`).

- `class` = pode repetir em várias tags
- `id` = único, só 1 tag na página pode ter

> O nome da `class` ñ pode começar c/ número (tipo `class="01"`), pq o CSS ñ consegue achar. Usa `class="caixa1"`.

### O head (configurações da página)

O q fica no `head` ñ aparece na tela, são informações p/ o navegador, o Google e o WhatsApp.

```html
<head>
    <meta charset="UTF-8">   <!-- deixa usar acentos e ç -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">   <!-- site certinho no cel -->
    <title>Ludnice | Criação de Sites</title>   <!-- texto da aba -->
    <meta name="description" content="Criação de sites em Portugal e no Brasil.">   <!-- texto q aparece no Google -->
    <link rel="icon" href="favicon.svg">        <!-- iconezinho da aba (favicon) -->
    <link rel="stylesheet" href="style.css">    <!-- liga o CSS -->
</head>
```

> Sem o `viewport`, no cel o site aparece minúsculo, como se fosse no computador.

### Prévia ao compartilhar (WhatsApp, Facebook...)

```html
<meta property="og:title" content="Precisa de um site? Eu faço!">
<meta property="og:description" content="Sites bonitos e modernos.">
<meta property="og:image" content="https://ludnice.pt/previa.jpg">
<meta property="og:url" content="https://ludnice.pt/">
```

É o "cartãozinho" c/ título, texto e imagem q aparece qdo manda o link.

> A imagem tem q ter o endereço completo, c/ `https://`, senão o WhatsApp ñ acha.

### Imagem

```html
<img src="imagens/servico-site.jpg" alt="Portátil a mostrar um site">
```

- `src` = onde tá a imagem
- `alt` = descrição da imagem, p/ qm usa leitor de tela e p/ qdo ela ñ carrega. Ñ precisa fechar!

### span

```html
<h1>Precisa de um site? <span class="destaque">Eu faço!</span></h1>
```

É tipo a `div`, mas p/ um pedacinho de texto, sem pular linha. Bom p/ pintar só uma parte de outra cor.

### Menu (nav)

```html
<nav class="menu">
    <a href="#sobre">Sobre</a>
    <a href="#precos">Preços</a>
</nav>
```

`nav` = tag semântica do menu. Cada link pula p/ seção c/ aquele `id`.

### Botão

```html
<button id="botao-menu" aria-label="Abrir menu">☰</button>
```

`aria-label` = descreve o botão p/ qm usa leitor de tela, qdo ele só tem um símbolo.

### Pergunta q abre e fecha (details)

```html
<details>
    <summary>O site funciona no telemóvel?</summary>
    <p>Sim! Funciona no cel e no computador.</p>
</details>
```

- `summary` = o q aparece sempre (a pergunta)
- o resto só aparece qdo clica. Ñ precisa de JavaScript!

### Lista de termos (dl)

```html
<dl>
    <dt>Domínio</dt>
    <dd>Pode demorar até 48 horas.</dd>
</dl>
```

- `dl` = a lista
- `dt` = o termo (o título)
- `dd` = a explicação dele

### Formulário

```html
<form id="formulario">
    <label for="campo-nome">O seu nome</label>
    <input type="text" id="campo-nome" placeholder="Ex.: Maria" required>

    <label for="campo-tipo">Tipo de site</label>
    <select id="campo-tipo">
        <option>Site institucional</option>
        <option>Landing page</option>
    </select>

    <label for="campo-ideia">A sua ideia</label>
    <textarea id="campo-ideia" rows="4"></textarea>

    <button type="submit">Enviar</button>
</form>
```

- `form` = o formulário td
- `label` = o texto q explica o campo. O `for` liga ele ao campo c/ o msm `id`
- `input` = campo de 1 linha. Ñ precisa fechar!
- `placeholder` = texto clarinho de exemplo, some qdo a pessoa escreve
- `required` = obrigatório, o navegador ñ deixa enviar vazio
- `select` + `option` = caixinha de escolher
- `textarea` = caixa grande, p/ várias linhas (`rows` = qtas linhas)
- `type="submit"` = o botão q envia o formulário

---

## CSS

CSS é a "roupa" da página: cores, tamanhos, espaços, posição...

### Comentário

```css
/* isto é um comentário no CSS */
```

### Como escreve

```css
seletor {
    propriedade: valor;
}
```

O **seletor** diz QUEM vai mudar, a **propriedade** diz O Q muda e o **valor** diz COMO fica. Td linha termina c/ `;`.

### Seletores

```css
h1 { }           /* td h1 da página */
.titulo { }      /* qm tem class="titulo" (c/ ponto) */
#topo { }        /* qm tem id="topo" (c/ #) */
footer p { }     /* só os p q tão dentro do footer */
h1, h2, p { }    /* vários de uma vez, separados por vírgula */
```

### Cores

```css
color: white;                          /* cor da letra */
background-color: rgb(8, 150, 197);    /* cor do fundo */
background-color: rgba(38, 17, 147, 0.75);
```

- `rgb` = mistura de vermelho, verde e azul (de 0 a 255)
- `rgba` = igual, mas o último nº é a transparência (0 = invisível, 1 = normal)

### Texto

```css
text-align: center;               /* centraliza */
font-size: 20px;                  /* tamanho da letra */
font-family: Arial, sans-serif;   /* tipo da letra */
text-decoration: none;            /* tira o sublinhado (bom p/ links) */
text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);  /* sombra na letra */
```

### Espaços

```css
padding: 20px;       /* espaço p/ DENTRO da caixa */
margin: 20px;        /* espaço p/ FORA da caixa */
margin: 20px auto;   /* 20px em cima e embaixo + centraliza na horizontal */
```

> `padding: 10px 20px;` = 10px em cima e embaixo, 20px dos lados.

### Caixa (bordas, sombra, tamanho)

```css
border-radius: 15px;                      /* arredonda os cantos */
border-top: 3px solid rgb(55, 23, 218);   /* linha só em cima */
box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);  /* sombra em volta da caixa */
max-width: 700px;       /* largura máxima */
width: fit-content;     /* largura do tamanho do conteúdo */
min-height: 15vh;       /* altura mínima */
```

`vh` = % da altura da tela. `100vh` = a tela inteira, `15vh` = 15% dela.

### display

```css
display: block;          /* ocupa a linha toda */
display: inline-block;   /* fica na linha, mas aceita largura */
```

### Imagem de fundo

```css
background-image: url("assets/fundo.jpeg");   /* qual imagem */
background-size: cover;                       /* cobre a tela td */
background-position: center;                  /* centraliza */
background-repeat: no-repeat;                 /* ñ repete a imagem */
```

### Efeito ao passar o mouse (hover)

```css
.botao-topo {
    cursor: pointer;     /* mãozinha */
    transition: 0.3s;    /* muda devagar, em 0.3 segundos */
}

.botao-topo:hover {
    background-color: rgba(38, 17, 147, 0.75);
    color: white;
}
```

O `:hover` só vale qdo o mouse tá em cima.

### Animação

```css
/* 1º cria a animação e dá um nome */
@keyframes aparecer {
    from {
        opacity: 0;                    /* começa invisível */
        transform: translateY(-50px);  /* começa + p/ cima */
    }
    to {
        opacity: 1;                    /* fica visível */
        transform: translateY(0);      /* volta p/ o lugar */
    }
}

/* 2º usa a animação */
.titulo {
    animation: aparecer 2s ease;   /* nome, tempo, jeito */
}
```

- `from` = como começa
- `to` = como termina

### Cor c/ #

```css
color: #d9f07a;   /* verde-limão */
```

Outro jeito de escrever cor, c/ `#` + 6 letras/nºs. O VS Code mostra um quadradinho c/ a cor do lado.

### Variáveis de cor (:root)

```css
/* guarda as cores lá em cima, c/ um nome */
:root {
    --cor-principal: #d9f07a;
    --cor-fundo: #13202e;
}

/* usa a cor pelo nome c/ o var() */
body {
    background: var(--cor-fundo);
}

h2 {
    color: var(--cor-principal);
}
```

O nome tem q começar c/ `--`. Se quiser mudar a cor do site td, é só mudar no `:root`.

### Ajustes gerais (o *)

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;   /* rola devagar qdo clica no menu */
}
```

- `*` = td as tags da página
- `margin: 0` e `padding: 0` = tira os espaços q o navegador coloca sozinho
- `box-sizing: border-box` = o `padding` e a borda ficam **dentro** da largura, ñ aumentam a caixa

> Costuma ir lá no começo do CSS.

### Fonte baixada (@font-face)

```css
/* ensina a fonte nova p/ o navegador */
@font-face {
    font-family: "DM Sans";                      /* nome q vou usar */
    src: url("fontes/dm-sans.woff2") format("woff2");   /* onde tá o arquivo */
}

/* usa a fonte */
body {
    font-family: "DM Sans", Arial, sans-serif;
}
```

O arquivo da fonte fica na pasta do site. As fontes dps da `,` são reserva, se a 1ª ñ carregar.

### Medidas: rem e line-height

```css
font-size: 1.3rem;   /* 1rem = tamanho normal da letra (16px). 2rem = o dobro */
line-height: 1.6;    /* espaço entre as linhas do texto */
```

> O `rem` é melhor q `px` p/ letra, pq respeita qdo a pessoa aumenta a letra no cel.

### Flex (lado a lado)

```css
.menu {
    display: flex;              /* coloca os filhos lado a lado */
    justify-content: center;    /* centraliza na horizontal */
    align-items: center;        /* centraliza na vertical */
    flex-wrap: wrap;            /* se ñ couber, passa p/ linha de baixo */
    gap: 1rem;                  /* espaço entre eles */
}
```

- `justify-content: space-between` = 1 na ponta esquerda e outro na direita

> O `display: flex` vai na caixa **pai**, e quem fica lado a lado são as **filhas**.

### Grid (colunas)

```css
.cartoes {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1.5rem;
}
```

Cria colunas sozinho: cada uma c/ no mínimo 220px. Se a tela for pequena (cel), fica tipo 1 embaixo da outra.

### Posição (position) e z-index

```css
.cabecalho {
    position: sticky;   /* gruda no topo qdo rola a página */
    top: 0;
    z-index: 10;        /* fica por cima das outras coisas */
}
```

- `sticky` = gruda qdo chega no topo
- `fixed` = fica parado na tela, msm rolando
- `z-index` = qual fica na frente. Nº maior = + na frente. `-1` = vai p/ trás de td

### Enfeite c/ ::before

```css
/* tracinho verde em cima de cada h2 */
.secao h2::before {
    content: "";           /* obrigatório, msm vazio */
    display: block;
    width: 50px;
    height: 5px;
    background: var(--cor-principal);
}
```

`::before` cria uma "camada" extra antes do conteúdo da tag, sem mexer no HTML. Tem tb o `::after`, depois.

### Esconder: display none

```css
.botao-menu {
    display: none;   /* some da página */
}
```

### Versão do cel (@media)

```css
@media (max-width: 600px) {
    /* td aqui dentro só vale qdo a tela tem até 600px (cel) */
    .botao-menu {
        display: block;   /* no cel o ☰ aparece */
    }
}
```

> O `@media` fica lá no final do CSS, p/ ganhar das regras de cima.

> No Angular, o `styles.css` vale p/ página td e o `app.css` só p/ o `app.html`.

---

## JavaScript

JavaScript é o q dá ação p/ página. O arquivo termina em `.js` e é ligado no final do `body`:

```html
<script src="script.js"></script>
```

> Fica no final do `body` p/ página carregar 1º e o script rodar dps.

### Console

É uma parte do navegador onde aparecem as mensagens do `console.log()` e os erros do código. P/ abrir: **F12** e clica na aba **Console**, ou `Ctrl + Shift + J` q já abre direto nele.

```javascript
console.log("Olá");   // mostra "Olá" no Console
```

### Comentário

```javascript
// comentário de 1 linha
/* comentário de
   várias linhas */
```

### Variáveis

Variável é um espaço p/ guardar um valor.

```javascript
let nome = "Ludnice";   // texto vai c/ aspas
let idade = 36;         // nº vai sem aspas
let estudando = true;   // true (verdadeiro) ou false (falso)
```

- `let` = cria a variável
- `=` = guarda o valor dentro dela

### Juntar textos

```javascript
console.log("Olá, meu nome é " + nome + " e tenho " + idade + " anos.");
```

O `+` junta os textos c/ as variáveis. Atenção c/ os espaços dentro das aspas!

### Comparações

| Sinal | Quer dizer |
| --- | --- |
| `>` | maior q |
| `<` | menor q |
| `>=` | maior ou igual |
| `<=` | menor ou igual |
| `===` | igual |
| `!==` | diferente |

### if / else (decisões)

```javascript
if (idade >= 18) {
    console.log("maior de idade");
} else {
    console.log("menor de idade");
}
```

Se o q tá no `( )` for verdade, roda o 1º `{ }`. Se ñ, roda o do `else`.

### else if (várias opções)

```javascript
if (idade < 12) {
    console.log("criança");
} else if (idade < 18) {
    console.log("adolescente");
} else if (idade < 60) {
    console.log("adulta");
} else {
    console.log("idosa");
}
```

Testa de cima p/ baixo e para no 1º q for verdade. O `else` é qdo nenhum deu certo.

### Funções

Função é um bloco de código c/ nome. Escreve 1 vez e usa qtas vezes quiser.

```javascript
// cria a função
function saudar(pessoa) {
    console.log("Olá, " + pessoa + "!");
}

// chama a função (manda rodar)
saudar("Ludnice");
saudar("Maria");
saudar(nome);   // tb dá p/ mandar uma variável
```

- `function` = cria a função
- `pessoa` = **parâmetro**, recebe o valor q vai no `( )` qdo chama a função
- O q tá no `{ }` só roda qdo a função é chamada

### Mudar o texto da página

```html
<p id="mensagem"></p>
```

```javascript
document.getElementById("mensagem").textContent = "Olá, meu nome é " + nome;
```

- `document` = a página
- `getElementById("mensagem")` = pega a tag c/ `id="mensagem"`
- `textContent` = o texto q fica dentro dela

### Botão q faz algo qdo clica

```html
<button id="botao">Clique aqui</button>
```

```javascript
function mudarTexto() {
    document.getElementById("mensagem").textContent = "Vc clicou no botão!";
}

document.getElementById("botao").addEventListener("click", mudarTexto);
```

`addEventListener` = fica "escutando". Qdo der `"click"` no botão, roda a função `mudarTexto`.

> Na última linha a função vai **sem** `()`. C/ `()` ela roda na hr, antes do clique.

### Arrays (listas)

Array é uma lista de valores numa variável só.

```javascript
let frutas = ["maçã", "banana", "uva", "laranja"];

console.log(frutas[0]);       // maçã
console.log(frutas[2]);       // uva
console.log(frutas.length);   // 4 (qtos itens tem)
```

> A contagem começa do **0**! O 1º item é o `[0]`.

### Laço for...of (repetição)

Repete o msm código p/ cada item do array.

```javascript
for (let fruta of frutas) {
    console.log("Eu gosto de " + fruta);
}
```

Lê assim: "p/ cada `fruta` da lista `frutas`, faz o q tá no `{ }`". A cada volta, `fruta` guarda um item diferente.

### Mostrar a lista na página

```html
<ul id="lista-frutas"></ul>
```

```javascript
let lista = document.getElementById("lista-frutas");   // pega a ul vazia

for (let fruta of frutas) {
    let item = document.createElement("li");   // cria um li (ainda fora da página)
    item.textContent = fruta;                  // coloca o nome da fruta nele
    lista.appendChild(item);                   // põe o li dentro da ul, agora aparece!
}
```

---

## TypeScript e Angular

O Angular usa **TypeScript** (arquivos `.ts`), q é o JavaScript c/ + regras. Por enquanto só vi o arquivo q liga as peças.

### O componente (app.ts)

```typescript
import { Component } from '@angular/core';   // traz o Component do Angular

@Component({
  selector: 'app-root',      // nome da tag q mostra esse componente
  templateUrl: './app.html', // qual HTML ele usa
  styleUrl: './app.css'      // qual CSS ele usa
})
export class App {           // export = deixa outros arquivos usarem
}
```

**Componente** = um pedaço da página c/ o HTML, o CSS e o TS dele juntos.

> Comentário no TypeScript/JavaScript é c/ `//` (1 linha) ou `/* */` (várias linhas).

### Criar um componente novo

```bash
ng generate component component/tag-listas
```

Cria a pasta `component/tag-listas` dentro do `src/app`, c/ 4 arquivos: `.html`, `.css`, `.ts` e `.spec.ts` (o de testes). Dá p/ escrever curto: `ng g c component/tag-listas`.

> O terminal tem q estar dentro da pasta do projeto. O componente novo já vem escrito "tag-listas works!" no HTML, é só p/ mostrar q funcionou.

### Usar o componente na página

1º no `app.ts`, importa o componente e coloca ele no `imports`:

```typescript
import { TagListas } from './component/tag-listas/tag-listas';   // traz o componente

@Component({
  imports: [RouterOutlet, TagListas],   // avisa q o app vai usar ele
  selector: 'app-root',
  ...
})
```

Dps no `app.html`, coloca a tag c/ o nome do `selector` dele:

```html
<app-tag-listas></app-tag-listas>
```

> O nome muda de jeito: a pasta é `tag-listas`, a classe no `.ts` é `TagListas` (junto e c/ letra grande) e a tag é `app-tag-listas`.

### Tipos de variável (TypeScript)

No TypeScript a gente diz o **tipo** da variável, o q ela pode guardar. Dentro da `class` ñ usa `let`.

```typescript
export class TagListas {
  nome: string = 'Ludnice';                        // texto, c/ aspas simples ou duplas
  numero: number = 42;                             // nº
  estudando: boolean = true;                       // true ou false
  arquivos: string[] = ['app.html', 'app.css'];    // array (lista) de textos
}
```

| Tipo | O q guarda |
| --- | --- |
| `string` | texto |
| `number` | nº |
| `boolean` | `true` (verdadeiro) ou `false` (falso) |
| `string[]` | lista de textos (o `[]` quer dizer lista) |

> Se tentar guardar um nº numa variável `string`, o VS Code já avisa o erro. É p/ isso q serve o TypeScript.

### constructor e this

```typescript
export class TagListas {
  nome: string = 'Ludnice';

  constructor() {
    console.log("minha variável: ", this.nome);
  }
}
```

- `constructor` = roda sozinho qdo o componente aparece na página
- `this.` = "deste componente". P/ usar uma variável da classe tem q colocar o `this.` antes
- No `console.log`, a `,` separa o texto da variável (mostra os 2 c/ espaço no meio)

---

## Atalhos do VS Code

| Atalho | O que faz |
| --- | --- |
| `Ctrl + S` | Salvar |
| `Ctrl + Z` | Desfazer |
| `Ctrl + Y` | Refazer (desfaz o desfazer kkk) |
| `Ctrl + /` | Deixa a linha como comentário (ou tira) |
| `` Ctrl + ` `` (crase) | Abre/fecha o terminal no VS Code |
| `Ctrl + P` | Procura e abre arquivo pelo nome |
| `Ctrl + F` | Procura uma palavra no arquivo |
| `Alt + ↑` ou `Alt + ↓` | Sobe ou desce a linha |
| `Ctrl + Shift + V` | Ver o Markdown formatado |

> Dependendo do teclado, uns atalhos (tipo o do comentário e o do terminal) mudam. P/ ver os seus: `Ctrl + K` e dps `Ctrl + S`, abre a lista c/ td.

> **Observação sobre o VS Code**
>
> Quando aparece a letra **M** ao lado de um arquivo, significa **Modified (Modificado)**. Isso indica que o arquivo foi alterado e essas alterações ainda não foram registradas em um novo commit.
>
> Para visualizar como um arquivo `README.md` ficará formatado, use:
>
> ```text
> Ctrl + Shift + V
> ```
>
> Esse atalho abre a pré-visualização do Markdown no VS Code.

