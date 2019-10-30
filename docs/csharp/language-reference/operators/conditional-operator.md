---
title: '?: operator- C# Reference'
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 7397c5b2b2278f487a98b029b00924d3151913db
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036301"
---
# <a name="-operator-c-reference"></a>?: işleç (C# başvuru)

Üçlü işleç olarak da bilinen koşullu operatör `?:`, Boolean ifadesinin `true` veya `false`olarak değerlendirildiğine bağlı olarak bir Boole ifadesi değerlendirir ve iki ifadeden birinin sonucunu döndürür. 7,2 ile C# başlayarak, [koşullu başvuru ifadesi](#conditional-ref-expression) iki ifadeden birinin sonucuna başvuruyu döndürür.

Koşullu işlecin sözdizimi şöyledir:

```csharp
condition ? consequent : alternative
```

`condition` ifadesi `true` veya `false`olarak değerlendirilmelidir. `condition` `true`değerlendirilirse, `consequent` ifadesi değerlendirilir ve sonucu işlemin sonucu olur. `condition` `false`değerlendirilirse, `alternative` ifadesi değerlendirilir ve sonucu işlemin sonucu olur. Yalnızca `consequent` veya `alternative` değerlendirilir.

`consequent` ve `alternative` türü aynı olmalıdır veya bir türden diğerine örtük bir dönüştürme olmalıdır.

Koşullu operatör doğru ilişkilendirilebilir, diğer bir deyişle, formun bir ifadesi

```csharp
a ? b : c ? d : e
```

şöyle değerlendirilir

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> Koşullu işlecin nasıl değerlendirildiğini anımsamak için aşağıdaki anımsatıcı cihazı kullanabilirsiniz:
>
> ```text
> is this condition true ? yes : no
> ```

Aşağıdaki örnek, koşullu işlecin kullanımını gösterir:

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Koşullu başvuru ifadesi

7,2 ' C# den başlayarak, iki ifadeden birinin sonucuna başvuruyu döndürmek için koşullu başvuru ifadesini kullanabilirsiniz. Bu başvuruyu bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkenine atayabilir veya bir [Başvuru dönüş değeri](../keywords/ref.md#reference-return-values) veya [`ref` yöntemi parametresi](../keywords/ref.md#passing-an-argument-by-reference)olarak kullanabilirsiniz.

Koşullu başvuru ifadesi için sözdizimi aşağıdaki gibidir:

```csharp
condition ? ref consequent : ref alternative
```

Özgün koşullu operatör gibi, koşullu başvuru ifadesi iki ifadeden yalnızca birini değerlendirir: `consequent` ya da `alternative`.

Koşullu başvuru ifadesi durumunda `consequent` ve `alternative` türü aynı olmalıdır.

Aşağıdaki örnek, koşullu başvuru ifadesinin kullanımını gösterir:

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Koşullu işleç ve bir `if..else` ekstresi

[İf-else](../keywords/if-else.md) ifadesinin yerine koşullu işlecin kullanılması, bir değeri hesaplamak için koşullu olarak bir değer hesaplamanız gerektiğinde daha kısa kod oluşmasına neden olacaktır. Aşağıdaki örnek, bir tamsayıyı negatif veya negatif olmayan olarak sınıflandırmanın iki yolunu göstermektedir:

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür, koşullu işleci aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [koşullu işleç](~/_csharplang/spec/expressions.md#conditional-operator) bölümüne bakın.

Koşullu başvuru ifadesi hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [if-else beyanı](../keywords/if-else.md)
- [?. '? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)
- [?? ve?? = işleçleri](null-coalescing-operator.md)
- [ref anahtar sözcüğü](../keywords/ref.md)
