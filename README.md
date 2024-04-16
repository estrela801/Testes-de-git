# Testes-de-git
Repositório destinado ao aprendizado de comandos git

~~~bash
git config --global core.editor "code --wait"
~~~

O comando acima define o Visual Studio Code como editor padrão das mensagens de commit.

~~~bash
git commit --allow-empty
~~~

O parâmetro `--allow-empty` permite a criação de um commit vazio, para fins de testes e prática do Git. 

~~~bash 
git commit -a
~~~

O parâmetro `-a` adiciona todos os arquivos modificados ou não ignorados ao commit atual.


~~~bash
git checkout -b novoBranch
~~~

O parâmetro `-b` alterna para `novoBranch` criando o branch. o mesmo acontece com o comando `git switch` com o parâmetro `-c`.


~~~bash
git branch -D nomeBranch
git push --delete origin nomeBranch
~~~

Para apagar um branch é preciso primeiro apaga-lo localmente usando `git branch -D nomeBranch`, logo após, para apaga-lo no remoto use `git push --delete origin nomeBranch`.


~~~bash
git log --graph --oneline
~~~

O comando `log` exibe o histórico de commits em detalhes. Com as flags `--graph` e `--oneline` exibe o hitórico em um formato mais compreensível, através de um grafo (grafo?)

### Rebase interativo 

Para alterar o autor de um commit, você pode utilizar o rebase interativo e o comando `commit --amend`

**Antes, porém**, verifique se o editor de mensagens do commit está configurado para o editor do próprio VS Code.
~~~bash 
git rebase -i <referenciaCommit>
~~~
A referência do commit deve ser sempre o commit anterior ao commit que deve ser alterado

No editor de commits, altere a instrução do commit desejado de `pick` para `edit`. Em seguida grave e feche o editor.

O rebase fará uma pausa para que você altere as informações do autor.

~~~bash
git commit --amend --reset-author --no-edit
~~~

Caso você queira especificar o autor, utilze a flag `--autor="Nome do Autor <email@autor>"`, nesse exato formato.

Caso seu commit seja vazio, acrescente ainda a flag `allow-empty`.

Após o reparo do commit, continue o processo do rebase com o comando abaixo.

~~~bash
git rebase --continue
~~~

Finalmente, **confira o novo hitórico localmente** e envie ao repositório remoto **forçadamente**.