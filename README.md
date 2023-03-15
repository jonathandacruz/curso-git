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

 
 

```bash
git push -u <remote> HEAD:feature-branch
```
O sinalizador -u configura o novo branch remoto como o branch de acompanhamento padrão para o branch local. Isso significa que, no futuro, quando você executar o comando git push sem especificar o branch remoto e o branch local, o Git saberá qual branch remoto e local usar com base no branch de acompanhamento padrão.