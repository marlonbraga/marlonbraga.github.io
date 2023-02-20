---
layout: post
title: Fazendo Pull Requests elegantes
lang: pt-br
ref: 10
date: 2023-02-16 15:09:00
description: O que devemos escrever na descrição de nosso PR?
tags: formatting code
categories: sample-posts
disqus_comments: true
---2023-02-16-elegant-pull-request.md

A revisão de código alheio pode ser uma tarefa ingrata. Principalmente quando contém uma bíblia de alterações significativas e arriscadas.

Porém, se ainda houver amor no seu coração, há uma forma de facilitar a vida da infeliz criatura que terá de revisar essa quantidade quase infinita de mudanças em um código, que diga-se de passagem, não foi escrito por ele. 
pode-se optar criar um bom Reademe que o ajude nessa tarefa.
~Faça Pull Requests pequenos~
Faça uma decrição relevante de seu Pull Request.

O que seria revante colocar em uma descrição de PR?


## Objetivo
Por que foi necessário criar esse PR?
Que problemas ele resolve?
- Print se tiver uma interface gráfica
- Link da estória de usuário/requisito funcional/caso de uso 

Ex.: 

```
O objetivo dessas alterações é a refatoração da classe `GameService` .
Mais especificamente, o método `SaveGame`.
```

## Decisões de design
Mas por quê precisava criar uma classe nova em vez de usar a existente?
Por quê separar um trecho de código de uma classe?
Precisava mesmo de tanta interface assim?
Porque essas classes novas estão nesse diretório e não na pasta raiz?

Não. Os revisores de código não são adivinhos. A decisões de design de código não são óbvias e não seria elegante deixar ele gastar tempo tentando decifrar escolhas que você poderia escrever com poucos caracteres.
O que é relevante é o seguinte:

- Quais Interfacesm classes ou métodos foram aleterados/criados
- Qual foi o objetivo em realizar cada alteração?
- Quais descições foram tomadas
- Qual o  princípio de design que foi considerado para tomar essa decisão? SOLID?

Um diagrama de classes básico, pode economizar um tempo precioso se quiser realmente que entendam o que você fez.

Ex.:

> Para permitir a criação de testes unitários, foi necessário adequar a classe ao princípio de Inversão de controle (SOLID).
> Todas as chamadas ao contexto do banco de dados foi removida da classe service para novas classes de DAO `CreatureRepository` ,  `PlayersRepository`, `ExperiencePointsRepository`. A classe `DungeonBuilderService` passa a depender de suas abstrações possibilitando o  desacoplamento necessário para realização de testes unitários.

 ![Diagrama de clases](/assets/img/2023-02-16-pull-request-elegante/class-diagram.png)

## Métricas de Qualidade de código
Dê segurança ao revisor de você se importou manter seu código manutenível em vez de sair bagunçando tudo só para entregar a tarefa mais rápido.

Os fatos não se importam com a opinião de ninguém.
Métricas dizem os fatos e atropelam a opinião de seus revisores mais implicantes. É uma forma de contornar a objeção relacionadas a "estilo de escrita". Afinal de contas, deve-se sacrificar nosso índice de manutenibilidade do código por causa de um capricho do revisor?
Será que preferências estéticas tem tanta importância quando a uma queda no acoplamento na classe tal ou um método que nasceu com baixa complexidade cognitiva?
Obs.: (Se seu código estiver ferindo nenhum acordo ou padrão pré-estabelecido pelo time, não é uma questão de opinião. Você deve altera-lo sim)

Um print do Code Analyser do Visual Studio é bem-vindo. Mas uma tabela simples serve.

Ex.:

> Código resultante demonstrou maior legibilidade.  
> 	- Aumento de Índice de manutenabilidade *(de 24 para 51)*  
> 	- Diminuição de Acoplamento de Classes *(de 16 para 10)*  
> 	- Redução de Complexidade ciclomática *(de 47 para 5)*  
> 	- Redução de linhas de código *(de 133 para 35)*  
>
>  Parte dessa melhora se deu por causa da *extração de método* criando o `ConverterModelParaEntidade()`.

| **MÉTRICA**                | **INDICADOR** | **COMPARATIVO** |
| -------------------------- |:-------------:|:---------------:|
| Índice de Manutenibilidade | 51            | + 27%           |
| Complexidade Ciclimática   | 5             | - 42%           | 
| Acoplamento de Classes     | 0             | - 6%            |
| Linhas de código           | 35            | - 98            |

![Code_metrics](/assets/img/2023-02-16-pull-request-elegante/code-metrics.png)

Para um profissional de código, é melhor ser reconhecido pela qualidade do meu trabalho do que a velocidade com a que entrego. Essa é uma ótima forma de mostrar.

## Testes
Sim. É necessário saber se isso está funcionando e se está quebrando algo.
Executar testes automatizados são úteis para mostrar que você fez o mínimo esperado de você. Mas uma análise mais detalhada pode dar um panomora geral sobre a qualidade especificamente do que você fez.
Algumas informações importantes são:
- Quantos testes automatizados foram criados
- Qual é a porcentagem da cobertura de código alterado
- Quantos fluxos de código estão sendo testados
- Variação de Performance
- Quais testes manuais foram executados

Ex.:
>  - 2 novos testes unitário criados
>  - Cobertura de todos os fluxos de código do método em questão (2/2)
>  - 100% de cobertura de código no método em questão
>  - Aumento de cobetura de código em métodos relacionados
	
![code-coverage](/assets/img/2023-02-16-pull-request-elegante/code-coverage.png)


## Integração
As vezes a alteração não é com o código mas com a alteração em si e o quanto isso pode afetar a estabilidade do sitema em funcionamento.

- Impacta outras áreas
- Impacta sistemas já em funcionamento?
- Há alguma configuração no sistema aser feita?

---


## Template de PR:

```
O objetivo dessas alterações é __________.

### **📐Decisões de design**
Para permitir a criação de testes unitários, foi necessário adequar a classe ao princípio de **Inversão de controle (SOLID)** .
Todas as chamadas ao contexto do banco de dados foi removida da classe service para novas classes DAO `______` , `______`, `______`. A classe `ResgatesAgendadosService` passa a depender de suas abstrações possibilitando desacoplamento necessário para realização de testes unitários.

![Diagrama de clases](image.jpg)

# 🌡️Qualidade de código
Código resultante demonstrou maior legibilidade.  
	- Aumento de Índice de manutenabilidade  
	- Diminuição de Acoplamento de Classes  
	- Redução de Complexidade ciclomática  
	- Redução de linhas de código  
Parte dessa melhora se deu por causa da *extração de método* criando o ` ______()`.

![Code_metrics](image.png)  
| **MÉTRICA**                | **INDICADOR** | **EVOLUÇÃO** |
| -------------------------- |:-------------:|:------------:|
| Complexidade Cognitiva     | 10%           | + 100%       |
| Complexidade Ciclimática   | 1             | + 100%       | 
| Profundidade de herança    | 0             | - 100%       |
| Índice de Manutenibilidade | 100           | + 100%       |
| Acoplamento de Classes     | 0             | - 100%       |
| Linhas de código           | 1000          | + 100%       |

# 🧪Testes Automatizados
  - ___ novos testes unitários criados
  - Cobertura de todos os fluxos de código do método em questão (___/___)
  - ___% de cobertura de código no método em questão
  - Aumento de cobetura de código em métodos relacionados
	
![testes](image.png)

Cobertura
![code-cov](image.png)

```