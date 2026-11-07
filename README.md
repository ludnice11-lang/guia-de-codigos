# 📚 Guia de Códigos da Ludnice

Anotações, comandos e aprendizados durante meus estudos em Desenvolvimento de Software.

---

## 💻 Terminal e Navegação

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

Apaga o arquivo. ⚠️ Cuidado: ñ vai p/ lixeira, some de vez!

### Limpar a tela do terminal

```bash
cls
```

Limpa td q tá escrito na tela. Os arquivos ñ são apagados. O `clear` faz a msm coisa.

> 💡 **Truques do teclado no terminal**
>
> - **Tab**: começa a digitar o nome da pasta ou arquivo e aperta `Tab`, o terminal completa sozinho.
> - **Seta p/ cima ↑**: mostra os comandos q vc já usou, p/ ñ ter q escrever td de novo.
> - **Ctrl + C**: para um comando q travou ou tá demorando.

### Abrir a pasta atual no VS Code

```bash
code .
```

Abre no VS Code a pasta em que o terminal está atualmente.

---

## 🌱 Git

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

> 💡 Se a lista for grande e o terminal "travar" c/ um `:` no final, aperta **q** p/ sair.

> 🔁 **Resumo do dia a dia**
>
> ```bash
> git status
> git add .
> git commit -m "o que eu mudei"
> git push
> ```

---

## 📝 Markdown

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

## ⌨️ Atalhos do VS Code

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

> 💡 Dependendo do teclado, uns atalhos (tipo o do comentário e o do terminal) mudam. P/ ver os seus: `Ctrl + K` e dps `Ctrl + S`, abre a lista c/ td.

> 💡 **Observação sobre o VS Code**
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

