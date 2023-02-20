---
layout: post
title: Legibilidade em testes unitários
lang: pt-br
ref: 4
date: 2023-02-04 15:09:00
description: Dicas para aumentar a legibilidade de testes unitários
tags: test code
categories: sample-posts
disqus_comments: true
---

## Pra quê legibilidade e testes?

O teste unitário é mais do que uma validação automática do código. Ele também serve como documentação mostrando o que se deve e o que não se deve esperar do comportamento do método.

Por isso é especialmente interessante que o código fique **legível**.

Além disso, os testes unitário também são código. Portanto também estão suscetíveis a manutenção. Essa manutenção deve ser tão simples e rápida como qualquer outro pedaço de código da solução.


## Nomenclatura
Nomes importam em testes também.
Durante a suíte de execução de testes, é o nome do método de teste que será exibido ao lado de uma mensagem de aprovação ou reprovação.

 ![Suíte de Tests](/assets/img/2023-02-04-legibilidade-em-testes/execution_suit_tests.png)

A maneira mais legível de se nomear um teste é através do padrão Given/When/Then (Dado/Quando/Então)

Sendo que 
`Dado` é uma precondição.
`Quando` é uma ação.
`Então` é um resultado esperado.

Ex:
```c#
[fact]
void ContaBancaria_Transferencia_SaldoEhReduzido(){
    //...
}
```

Não é necessário entrar em detalhes demais. Esse é o nome do teste. Se quiserem saber detalhes, que leiam o código dele.

## Limpeza de teste

> O que torna um teste limpo? Três coisas: legibilidade, legibilidade e legibilidade. (...) O que torna os testes legíveis? O mesmo que torna todos os códigos legíveis: clareza, simplicidade e conscistência de expressão. Num teste você quer dizer muito com o mínimo de expressões possíveis.  
>  
> -- Uncle Bob, Clean Code

### Uma afirmação por teste
Testes que chegam a uma única conclusão são mais fáceis de serem entendidos.

### Um único conceito por teste
Um teste para cada especificação de exemplo. Não queremos métodos longos que saiam testando várias coisas uma após a outra.



## Estrutura de código
Apesar de ser intuitivo, o padrão AAA (Arrange-Act-Assert) continua sendo uma ótima forma de organização dentro do método de teste.
A ideia é que o trecho de código de `preparação do teste` seja separada do trecho de `realização do teste` do trecho de `verificação do teste`.
Na prática, o codificador sabe aonde tudo está sem nem mesmo começar a ler o código.

```c#
// arranque
var repositorio = Substitute.For<IClienteRepositorio>();
var cliente = new Cliente(repositorio);
// ação
cliente.Salvar();
// assertiva
mock.Received.AlgumMetodo();
```

Para mais detalhes sobre o padrão AAA, ,eu sugiro esse artigo aqui: <a href="https://medium.com/@pablodarde/o-padr%C3%A3o-triple-a-arrange-act-assert-741e2a94cf88">O Padrão Triple A (Arrange, Act, Assert)</a>


## Ferramentas

Há algumas ferramentas que podem ajudar a alcançar a legibilidade desejada.

- <a href="https://www.nuget.org/packages/NSubstitute">NSustitute</a>
- <a href="https://www.nuget.org/packages/FluentAssertions">FluentAssetion</a>

### NSustitute
**NSustitute** é uma alternativa ao **Moq**. 
Com ele, a leitura e a escrita de códigos mais comuns se aproxima da linguagem natural. O Moq é uma boa ferramenta de Mock em vários pontos. Mas a legibilidade do teste, não é uma delas.

Enquanto o Moq faz uso de operação lambda para as situações mais simples, um mock escrito com NSubstitute se aproxima mais na linguagem natual.

```c#
//❌com Moq
mockUser.Setup(foo => foo.Address.Street).Returns(street);
mock.Setup(x => x.SearchById(It.IsAny<int>())).Returns((int i) => userList.Skip(1).Take(1).First());
mock.Setup(x => x.SearchById(2)).Returns((int i) => userList.First());

//✔️com NSubstitute
mockUser.Address.Street.Returns(street);
mock.SearchById(Arg.Any<int>()).Returns(userList.Skip(1).Take(1).First());
mock.SearchById(2).Returns(userList.First());
```

### FluentAssetion
**FluentAssetion** é uma alternativa ao **System.Assert**. 
Esse package segue a mesma ideia da anterior. Porém voltada para a fase de Assert do teste.

O destaque está no nome dos métodos. Quando combinados, a leitura fica fluída exatamente como leria uma regra de negócio em inglês.

```c#
//❌com Assert
string actual = "ABCDEFGHI";
Assert.Contains("EF", actual);
Assert.StartsWith("EF", actual);
Assert.AreEqual(9, actual.Length);

//✔️com FluentAssetion
string actual = "ABCDEFGHI";
actual.Should().StartWith("AB").And.EndWith("HI").And.Contain("EF").And.HaveLength(9);
```


Package Manager
```
NuGet\Install-Package NSubstitute -Version 4.4.0
NuGet\Install-Package NSubstitute.Analyzers.CSharp -Version 1.0.16
NuGet\Install-Package FluentAssertions -Version 6.9.0

```

## Por que não usar o SpecFlow?

É como diz o ditado:
>"Para quem só sabe usar martelo, todo problema é um prego."

SpecFlow é uma ferramenta muito interessante e útil.
Porém, ela é produtiva quando usada para o fim da qual foi criada. Quando foge disso, ela atrapalha mais do que ajuda.

SpecFlow é uma ferramenta de BDD. Essa, consiste em realizar especificação por exemplos com **Gherkin**, uma linguagem comum a QA, Desenvolvedor e PO. Isso é muito útil em um *teste End-To-End* e até em um *teste de Integração*. Mas o teste unitário é feito e mantido apenas pelo Desenvolvedor. Por isso, é necessário que a linguagem de um teste unitário seja mais técnica. Usar o **Gherkin** para descrever a funcionalidade em uma linguagem técnica é mais improdutivo do que usar os testes tradicionais.

Mas vamos falar mais do **BDD+Specflow** em outra oportunidade.

A ideia é que, por hora, deixemos o SpecFlow de fora dos nossos testes unitário.















