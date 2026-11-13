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
- **GitHub Pages**: parte do GitHub q coloca o site no ar, c/ um endereço p/ qqr pessoa abrir.
- **GitHub Actions (o robô)**: robô do GitHub q faz tarefas sozinho. No meu portfólio, td vez q dou `git push`, ele monta o site e publica no GitHub Pages. As ordens dele ficam no arquivo `.github/workflows/deploy.yml`. (Pq precisa dele: o navegador ñ entende Angular. Qdo o projeto é Angular e vai p/ o ar, ele tem q ser traduzido antes p/ HTML, CSS e JavaScript normais, c/ o `ng build`. O robô faz essa tradução e publica sozinho. Site só c/ HTML e CSS ñ precisa de tradução.)

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

> No Angular, o `styles.css` vale p/ página td e o `app.css` só p/ o `app.html`.

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

