---
layout: post
title: Plugins gratuitos para VS 2022
lang: pt-br
ref: 11
date: 2023-03-01 22:00:00
description: Mais produtividade com VisualStudio 22 sem pagar mais
tags: formatting code
categories: sample-posts
disqus_comments: true
---

O Visual Studio 2022 está excelente. Mas ele pode ganhar recursos muito interessantes quando se adiciona plugins nele. 

O plugin mais completo e famoso que temos é o [ReSharper](https://www.jetbrains.com/pt-br/resharper/). Porém não é a escolha mais... econômica.

Aqui estão 3 escolhas para de plugins gratuitos para quem não quer abrir mão da produtividade mas é ~~mão-fechada~~ simpático a ideia de economizar.

# FineCodeCoverage
Você faz testes automatizados? Bom trabalho. Mas sabe dizer o quanto de seu código está coberto por testes e quais são as linhas que estão desprotegidas?

Com esse plugin você pode verificar a cobertura de código de cada classe e método diretamente pelo VS22.

O [FineCodeCoverage](https://marketplace.visualstudio.com/items?itemName=FortuneNgwenya.FineCodeCoverage) também indica no editor se a linha de código está coberta ou não por algum teste. A cor da barra colorida ao lado esquerdo da numeração da linha, indica seu status de cobertura.
 - verde: linha coberta por teste
 - vermelho: linha não coberta por teste
 - amarelo: linha parcialmente coberta por teste

 > Marketplace: [FineCodeCoverage](https://marketplace.visualstudio.com/items?itemName=FortuneNgwenya.FineCodeCoverage)  
 > GitHub: [Repository](https://github.com/FortuneN/FineCodeCoverage)

![coveraged-line](/assets/img/2023-03-01-plugin-free-vs22/coveraged-line.png)
![coveraged-percentage](/assets/img/2023-03-01-plugin-free-vs22/coveraged-percentage.png)

# CodeMaintainability 2022
O Visual Studio realiza verificação da qualidade do seu código através do `Analyser > Calculate Code Metrics`.
Porém, com o [CodeMaintainability 2022](https://marketplace.visualstudio.com/items?itemName=ognjen-babic.CodeMaintainability2022) permite essa visualização diretamente no editor. Exibindo na assinatura de cada método seu **índice de manutenibilidade** e um ícone com a indicação da "saúde" de seu código.

Ao clicar no indicador do índice, é exibido outras medições da qualidade de código referente aquele método.

![code-maintenability](/assets/img/2023-03-01-plugin-free-vs22/code-maintenability.png)

Só faltou a métrica de **complexidade cognitiva** para ficar completo.

 > Marketplace: [CodeMaintainability 2022](https://marketplace.visualstudio.com/items?itemName=ognjen-babic.CodeMaintainability2022)  


# CodeMaid
O Visual Studio é capaz de fazer algumas sugestões de refatoração no seu código. O plugin [CodeMaid](https://marketplace.visualstudio.com/items?itemName=SteveCadwallader.CodeMaidVS2022) aumenta o repertório nativo da IDE e possibilita uma gama maior de refatorações para deixar seu código mias limpo e simples.

Além disso, o plugin também conta com recursos como:
- Detecção de *code smells*
- Limpeza geral de código
- Configuração de regras de limpeza
- Spades: Tela de estrutura de classes
- Barra de carregamento de build

 > Marketplace: [CodeMaid](https://marketplace.visualstudio.com/items?itemName=SteveCadwallader.CodeMaidVS2022)  
 > GitHub: [Repository](https://github.com/codecadwallader/codemaid)

## Recursos Variados
![code-manutenability](/assets/img/2023-03-01-plugin-free-vs22/codemaid-menu.png)
## Barra de carregamento de build:
![code-manutenability](/assets/img/2023-03-01-plugin-free-vs22/codemaid-buildbar.png)
## Spades - Estrutura de classe
![code-manutenability](/assets/img/2023-03-01-plugin-free-vs22/codemaid-spades.png)
## Configuração de opções e regras
![code-manutenability](/assets/img/2023-03-01-plugin-free-vs22/codemaid-options.png)



