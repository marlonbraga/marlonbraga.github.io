---
layout: post
title: Padrão de código
lang: pt-br
ref: 3
date: 2023-01-31 15:09:00
description: Possível orientação de código para times
tags: code
categories: sample-posts
disqus_comments: true
---
### <img src="https://cdn-icons-png.flaticon.com/512/6132/6132221.png" width="20" height="20"> Back-End

#### Nomenclatura

Elemento           | Classe Gramatical | Regra          | Exemplo
------------------ |------------------ |--------------- | -------------
Classe             | Substantivo       | PascalCase     | `Produto`
Interface          | Substantivo       | `I`+PascalCase | `IProduto`
Método             | Verbo             | PascalCase     | `ListarTickers`
Propriedade        | -                 | PascalCase     | `Ticker`
Variáveis publicas | -                 | camelCase      | `idProduto`
Variáveis privadas | -                 | `_`+camelCase  | `_recebimentoTotal`
Constantes         | -                 | PascalCase     | `TituloDePagina`

#### Formatação

##### Identação & Espaçamento

```
{
    diasUteis++; // ✅ 4 espaços
diasUteis++;     // ❌ sem espaços 
  diasUteis++;   // ❌ 2 espaços
}
```
#####   

Cada linha devera conter apenas uma instrução de código  
❌  
```
i++; contador++; _recebimentoTotal=0;  
```

✅  
```
i++;  
contador++;  
_recebimentoTotal=0;  
```

#### Regras gerais
- Tipo numérico de valores monetários deve ser `decimal`   
✅ `private decimal faturamentoAnual;`  
❌ `private double faturamentoAnual;`  
❌ `private float faturamentoAnual;`  
- Toda `Exception` deve ser logada.

#### Performance
- Evite o uso de `ToList()`, ele faz com que todos os registros sejam carregados em memória. Prefira retornos `IQueryable` e `IEnumerable`, e só leve para memória quando necessário.
- Libere os recursos que tomar, usando `Using` nas classes `IDisposable` (Exemplo: `sqlConnetion`). Prefira o `using` ao `try/finally`.
- Utilize `early return` ao invés de múltiplos IFs aninhados.

#### Testes automatizados
- Os testes automatizados devem ser fáceis de ler, curtos e testar apenas uma coisa. Use o padrão `Arrange/Act/Assert`.