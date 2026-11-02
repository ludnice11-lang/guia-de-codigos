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

### Abrir a pasta atual no VS Code

```bash
code .
```

Abre no VS Code a pasta em que o terminal está atualmente.

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

---

## 🌱 Git

O Git guarda o histórico das mudanças dos arquivos.

commit são "fotos" das atualizações. Cada vez que dá commit, ele fica com a ultima foto. Mas guarda todas as mudanças como uma espécie de histórico. fica tudo guardado no computador e se der push fica também no gitHub.

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

