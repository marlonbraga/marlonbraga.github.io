---
layout: post
title: GIT com Visual Studio
date: 2020-09-12 00:00:00 +0300
description: Guia de uso do GIT com Visual Studio para quem tem medo do terminal. # Add post description (optional)
img: software.jpg # Add image post (optional)
tags: [Git, Visual Studio] # add tag
---

## Organização do repositório 
A organização do repositório se dará por 3 branches principais. MAIN/MASTER,  HML e DEV.

### MAIN / MASTER (produção) 
• Guarda uma cópia estável e exatamente igual ao do projeto em servidor de  produção. 
• Guarda apenas o histórico de atualizações do código-fonte de produção. 
• Branch é atualizado por versão de HML.

### HML (homologação) 
• Guarda uma cópia exatamente igual ao do projeto em servidor de  homologação. 
• Guarda apenas o histórico de atualizações do código-fonte de homologação. 
• Branch é atualizado por versão de DEV.

### DEV (Desenvolvimento) 
• Guarda o histórico de inclusões e atualizações de funcionalidades. 
• Branch é atualizado por versões dos Branches de Funcionalidades. 


## Padrões de práticas


FUNCIONALIDADES 
Os commits são feitos em branches criadas especificamente para uma  funcionalidade. Facilitando o  isolamento de alterações, e  portanto, dificultando conflitos entre  alterações simultâneas entre mais  de um desenvolvedor. 
As funcionalidades são  
desenvolvidas simultaneamente por  vários desenvolvedores. Cada  funcionalidade na sua própria  branch. Ao finaliza-la, é mesclada  ao branch DEV. Assim, resolve-se  possíveis conflitos de mescla  apenas no momento de finalizar  funcionalidades e não a cada  commit de outro desenvolvedor. 
MERGE LOCAL 
Não se sobe branch de  
funcionalidade para o repositório. 
O ideal é criar a branch de  
funcionalidade em ambiente local e  ao finalizar, mesclar (fazer marge) a  branch DEV localmente e só então,  
subir as atualizações da branch DEV para origin/DEV. 
A exceção se dá quando há mais  de um desenvolvedor atualizando a  mesma branch de funcionalidade.


## Clonar projeto 
##### Clonar um repositório remoto significa fazer uma cópia dele para sua máquina. 

No Azure: 
1. Selecione o projeto 
2. Selecione o repositório que quer clonar para seu computador 3. Clique em [Clone] 
4. Selecione a opção SSH 
5. Copie o endereço do repositório




Branches Criar novo branch 
DEV 
DEV FUNC_<nome> 

No Visual Studio: 
1. Clique em [Git] 
2. Clique em [Novo Branch] 3. Defina o nome do seu branch 
(desenvolvimento)
(desenvolvimento) 

4. Defina a que branch remoto ela  
vai se associar. 
Ao associar um branch local com um  
remoto, é permitida a atualização de  
branches remotos. Para atualizar o  
branch origin/DEV, por exemplo, é  
necessário criar um branch DEV local  
e dar um push através dele.


## Branches
#### Alternar entre branches 

Ao alternar entre branches, pode-se gerar um commit na branch desejável. Assim como atualizar algum branch remoto associado a ele. 
Por exemplo, se estou no branch master mas quer atualizar o branch DEV,  primeiro tenho que alternar  para a branch DEV para  depois dar um push. 
Se estou no branch DEV  mas quero gerar um  
commit num branch de  funcionalidade, primeiro  tenho que alternar para a  branch de funcionalidade  para depois dar um commit. 
Para alternar branch: 1. Clique sobre o nome  no branch atual 
2. Selecione o branch desejado 
Linha de comando: 
Pode-se verificar o branch atual pela barra  inferior no Visual Studio



## Commit 
Diferentemente do SVN, o comando de commit do git só atualiza a  sua cópia local de repositório. Ou seja, nenhum outro integrante da  equipe poderá ver as alterações. Para quem veio do SVN, é  recomendado dar o comando push logo após dar um commit. 
Alterações locais 
No Visual Studio: 
1. Clique em [Git] 
2. Clique em [Commit ou Stash] 
3. Digite uma descrição clara 
4. Verifique os arquivos que você  
quer que sejam ‘commitados’.  
Caso queira excluir algum, basta  
clicar nele e escolher a opção  
“desfazer mudanças”. Os  
arquivos selecionados sairão da  
sua lista de ‘commitados’ 
5. Em seguida, clique em  
[Commitar] logo abaixo da caixa  
de texto 




## Commit 
É possível visualizar os commits em gráfico. Commits parecem  separados em 2 grupos: “Outgoing” e “Histórico local” 
FUNC_<nome> 
No Visual Studio: 
1. Clique em [Git] 
2. Clique em [Gerenciar branches] ou [Exibir Histórico]
Commits apenas em  
repositório local 
Commits em repositório  
local e remoto 

## Commit Boas práticas de commit 
Nomes significativos 
• Cada commit representa uma demanda 
• Use a descrição para explicar O QUÊ e POR QUÊ e não COMO • Separe o assunto do corpo com uma linha em branco • Limite a linha de assunto a 50 caracteres 
• Coloque a linha de assunto em maiúscula 
• Não termine a linha de assunto com um ponto 
• Use o modo imperativo na linha de assunto 
• Envolva o corpo do texto da descrição em 72 caracteres 


Essas práticas aumentam a  
legibilidade e entendimento  
do desenvolvedor


mais sobre isso: boas práticas em git 


## Navegar por commits 
As vezes se faz necessário atualizar o código na máquina para  uma versão anterior. Para isso, é necessário um branch auxiliar  temporário. 
FUNC_<nome> 
Passo 1: Primeiro escolhe um commit para navegar; 
Passo 2: Depois crie um branch para “marcar” aquele commit 
Passo 3: Então, alterne para o novo branch criado. 

Voltando para versão mais recente: 1. Clique em [Git] 
2. Clique em [Gerenciar branches] ou [Exibir Histórico] 3. Clique em branch com versão mais atual 4. Clique em [Checkout] para alternar branch 5. Clique no branch temporário 
6. Clique em [Excluir] 
Voltando para versão mais recente: 1. Clique em [Git] 
2. Clique em [Gerenciar branches] 3. Clique em branch com versão mais atual 4. Clique em [Checkout] para alternar branch 5. Clique no branch temporário 
6. Clique em [Excluir]



## Desfazer commits 
Em casos de haver realizado um commit errado, é  possível desfaze-lo por “reset”. 
FUNC_<nome>
No Visual Studio: 
1. Clique em [Git] 
2. Clique em [Exibir Histórico] 
3. Clique no branch desejado 
4. Clique em [Redefinir] 
Então todos os commits posteriores  
serão excluídos 


## Atualizar cópia local (Pull) 
Pull é uma atualização do repositório local a partir do remoto. Deixa seu branch igual a versão equivalente dela em repositório remoto. 

Fazer Pull no Visual Studio: 
1. Clique em [Git] 
2. Clique em [Realizar Pull] 
Use o Pull antes de subir 
Antes de subir alterações para o repositório remoto, é importante deixar a branch local igual a sua equivalente remoto para cuidar de uma  possível resolução de conflitos localmente. 
- Passo 1: Pull de DEV 
- Passo 2: Merge de FUNC em DEV - Passo 3: Push de DEV

## Enviar ao repositório (Push) Atualiza o repositório remoto a partir da cópia local. 
1. Certifique-se de que está no branch correto 
2. Clique na seta na barra inferior 


a quantidade de commits que  ainda não foram enviados para o  repositório remoto. 
Nesse exemplo, os demais  participantes do projeto não  conseguem ver nem acessar os  últimos 19 commits realizados. 

Após um push, o número de commits não  
enviados é zerado e seus commits estarão 
disponíveis para todos os integrantes do projeto


## Merge (mesclar branches) 
O merge junta as funcionalidades novas contidas  no branch de Funcionalidade com as  funcionalidades antigas já contidas DEV. 
Após um Merge, pode-se excluir o branch de  funcionalidade. 

No Visual Studio: 
1. Clique em [Git] 
2. Clique em [Gerenciar Branches] 3. Clique no branch desejado 4. Clique em [Mesclar <branch de  funcionalidade> em DEV]


## Conflitos 
Geralmente os Merges são feitos para adicionar arquivos e  linhas de código a arquivos. O próprio GIT cuida de juntar as duas versões nesses casos. Mas quando há alteração em  
uma linha de código, o GIT não sabe qual linha deve manter  ou descartar; Nesse caso, o merge não é realizado até que se  resolve esse conflito entre versões 
DEV 
(desenvolvimento) 
FUNC_<nome> 
Resolver conflitos entre arquivos (jeito simples): - Clique em [Resolver Conflitos] 
- Clique no botão direito no arquivo em 


Resolver conflitos entre linhas (jeito tradicional): 
Verifique as linhas em conflito. (A esquerda a versão da funcionalidade a entrar; a direita a  versão da branch atual; em baixo o resultado do merge) 
- Escolha entre as linhas com conflito, qual é a versão de cada uma que será considerada.  Visualize o resultado final no editor de texto abaixo 
- Clique em [Aceitar Mesclagem] 
