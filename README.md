# 


# curso-git-udemy

---
 
## Avisos paroquiais!

A trilha de aprendizado a seguir está disponível para o desenvolvimento das aulas na plataforma udemy para o curso de como controlar a versão do seu projeto utilizando Git e Github.

Fique por dentro 

[Curso com desconto!](https://www.udemy.com/course/git-controle-de-versao/?referralCode=FD1BFEB99BF453504B3F)

[Canal do Discord - Vamos papear!](https://discord.gg/zd5U7s4Y)

## Trilha
 
##### Configurações Iniciais

 
```bash
$ git config --global user.name "Fulano de Tal"
$ git config --global user.email fulanodetal@exemplo.br
```

##### Repositórios Remotos
Um branch remoto no Git é uma referência a um branch (ramificação) do repositório remoto. Quando você clona um repositório Git, o Git automaticamente cria um branch remoto padrão para acompanhar o branch principal (geralmente chamado de "master" ou "main") do repositório remoto.

###### Visualizando repositórios remotos
```bash
 git remote -v
```
###### Adicionar um repositório remoto
```bash
git remote add origin https://github.com/user/repo.git
```
 
###### Remover um repositorio remoto
```bash
git remote remove <nome_do_repositorio>
```
###### Enviar para um repositório remoto
```bash
git push <remote> <local branch>:<remote branch>

```

Por exemplo, para criar um novo branch remoto chamado "feature-branch" e enviar as alterações do seu branch local atual para esse branch remoto, você pode usar o seguinte comando:

```bash
git push -u <remote> HEAD:feature-branch
```
O sinalizador -u configura o novo branch remoto como o branch de acompanhamento padrão para o branch local. Isso significa que, no futuro, quando você executar o comando git push sem especificar o branch remoto e o branch local, o Git saberá qual branch remoto e local usar com base no branch de acompanhamento padrão.