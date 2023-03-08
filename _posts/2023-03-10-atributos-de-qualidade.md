---
layout: post
title: Atributos de Qualidade
lang: pt-br
ref: 5
date: 2023-03-10 10:00:00
description: Características da Arquitetura Definidas
tags: archtecture
categories: sample-posts
disqus_comments: true
---

## Operacional
| **TERMO**                | **DEFINIÇÃO**                                                                                                                                                                                                                                    |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Disponibilidade            | Quanto tempo o sistema precisará estar disponível (se 24 horas por dia, 7 dias por semana, as etapas precisam estar em vigor para permitir que o sistema esteja funcionando rapidamente em caso de falha).                                     |
| Continuidade               | Capacidade de recuperação de desastres.                                                                                                                                                                                                        |
| Desempenho                 | Inclui teste de estresse, análise de pico, análise da frequência das funções usadas, capacidade necessária e tempos de resposta. A aceitação do desempenho às vezes requer um exercício próprio, levando meses para ser concluído.             |
| Recuperabilidade           | Requisitos de continuidade de negócios (por exemplo, em caso de desastre, com que rapidez o sistema deve estar online novamente?). Isso afetará a estratégia de backup e os requisitos para hardware duplicado.                                |
| Confiabilidade/segurança   | Avalie se o sistema precisa ser à prova de falhas ou se é de missão crítica de uma forma que afeta vidas. Se falhar, custará à empresa grandes somas de dinheiro?                                                                              |
| Robustez                   | Capacidade de lidar com condições de erro e limite durante a execução se a conexão com a Internet cair ou se houver uma queda de energia ou falha de hardware.                                                                                 |
| Escalabilidade             | Capacidade do sistema de executar e operar à medida que o número de usuários ou solicitações aumenta.                                                                                                                                          |


## Estrutural
| **TERMO**                | **DEFINIÇÃO**                                                                                                                                                                                                                                    |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configurabilidade          | Capacidade para os usuários finais alterarem facilmente aspectos da configuração do software (através de interfaces utilizáveis).                                                                                                              |
| Extensibilidade            | Quão importante é conectar novas peças de funcionalidade.                                                                                                                                                                                      |
| Instalabilidade            | Facilidade de instalação do sistema em todas as plataformas necessárias.                                                                                                                                                                       |
| Alavancagem/reutilização   | Capacidade de alavancar componentes comuns em vários produtos.                                                                                                                                                                                 |
| Localização                | Suporte para vários idiomas em telas de entrada/consulta em campos de dados; em relatórios, requisitos de caracteres multibyte e unidades de medida ou moedas.                                                                                 |
| Manutenibilidade           | Quão fácil é aplicar as mudanças e aprimorar o sistema?                                                                                                                                                                                        |
| Portabilidade              | O sistema precisa rodar em mais de uma plataforma? (Por exemplo, o front-end precisa ser executado no Oracle, bem como no SAP DB?                                                                                                              |
| Capacidade de atualização  | Capacidade de atualizar fácil/rapidamente de uma versão anterior deste aplicativo/solução para uma versão mais recente em servidores e clientes.                                                                                               |


## Cross-Cutting
| **TERMO**                | **DEFINIÇÃO**                                                                                                                                                                                                                                    |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Acessibilidade             | Acesso a todos os seus usuários, incluindo aqueles com deficiências como daltonismo ou perda auditiva.                                                                                                                                         |
| Arquivabilidade            | Os dados precisarão ser arquivados ou excluídos após um período de tempo? (Por exemplo, contas de clientes devem ser excluídas após três meses ou marcadas como obsoletas e arquivadas em um banco de dados secundário para acesso futuro.)    |
| Autenticação               | Requisitos de segurança para garantir que os usuários sejam quem dizem ser.                                                                                                                                                                    |
| Autorização                | Requisitos de segurança para garantir que os usuários possam acessar apenas determinadas funções dentro do aplicativo (por caso de uso, subsistema, página da Web, regra de negócios, nível de campo, etc.).                                   |
| Jurídico                   | Em quais restrições legislativas o sistema está operando (proteção de dados, Sarbanes Oxley, GDPR, etc.)? Quais direitos de reserva a empresa exige? Quaisquer regulamentos sobre a forma como o aplicativo deve ser construído ou implantado? |
| Privacidade                | Capacidade de ocultar transações de funcionários internos da empresa (transações criptografadas para que nem DBAs e arquitetos de rede possam vê-las).                                                                                         |
| Segurança                  | Os dados precisam ser criptografados no banco de dados? Criptografado para comunicação de rede entre sistemas internos? Que tipo de autenticação precisa estar em vigor para acesso de usuário remoto?                                         |
| Suportabilidade            | Qual nível de suporte técnico é necessário para o aplicativo? Que nível de registro e outros recursos são necessários para depurar erros no sistema?                                                                                           |
| Usabilidade/atingibilidade | Nível de treinamento necessário para que os usuários alcancem seus objetivos com o aplicativo/solução. Os requisitos de usabilidade precisam ser tratados tão seriamente quanto qualquer                                                       |
