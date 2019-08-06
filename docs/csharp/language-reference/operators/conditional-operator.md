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
ms.openlocfilehash: 923591634599a6bbac74d43b105f4e46b492fa1a
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796470"
---
# <a name="-operator-c-reference"></a>?: işleç (C# başvuru)

Genellikle Üçlü koşullu `?:`işleç olarak bilinen koşullu operatör, bir Boole ifadesi değerlendirir ve Boolean ifadesinin değerlendirilip `true` değerlendirilmediğine bağlı olarak iki ifadeden birini değerlendirme sonucunu döndürür. veya `false`. 7,2 ile C# başlayarak, [koşullu başvuru ifadesi](#conditional-ref-expression) iki ifadeden birinin sonucuna başvuruyu döndürür.

Koşullu işlecin sözdizimi şöyledir:

```csharp
condition ? consequent : alternative
```

`condition` İfade `true` veya olarak`false`değerlendirilmelidir. , `condition` Olarak `true`değerlendirilirse ,`consequent` ifade değerlendirilir ve sonucu işlemin sonucu olur. , `condition` Olarak `false`değerlendirilirse ,`alternative` ifade değerlendirilir ve sonucu işlemin sonucu olur. Yalnızca `consequent` veya`alternative` değerlendirilir.

`consequent` Ve`alternative` türü aynı olmalıdır veya bir türden diğerine örtük bir dönüştürme olmalıdır.

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

7,2 ' C# den başlayarak, iki ifadeden birinin sonucuna başvuruyu döndürmek için koşullu başvuru ifadesini kullanabilirsiniz. Bu başvuruyu bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkenine atayabilir veya bir [Başvuru dönüş değeri](../keywords/ref.md#reference-return-values) ya da bir [ `ref` yöntem parametresi](../keywords/ref.md#passing-an-argument-by-reference)olarak kullanabilirsiniz.

Koşullu başvuru ifadesi için sözdizimi aşağıdaki gibidir:

```csharp
condition ? ref consequent : ref alternative
```

Özgün Koşul operatörü gibi, koşullu başvuru ifadesi iki ifadeden yalnızca birini değerlendirir: ya `consequent` `alternative`da.

Koşullu başvuru ifadesi söz konusu olduğunda, `consequent` ve `alternative` türü aynı olmalıdır.

Aşağıdaki örnek, koşullu başvuru ifadesinin kullanımını gösterir:

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

Daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="conditional-operator-and-an-ifelse-statement"></a>Koşullu işleç ve bir `if..else` ifade

[İf-else](../keywords/if-else.md) ifadesinin üzerinde koşullu işlecin kullanılması, bir değeri hesaplamak için koşullu olarak bir değer hesaplamanız gerektiğinde daha kısa kod oluşmasına neden olacaktır. Aşağıdaki örnek, bir tamsayıyı negatif veya negatif olmayan olarak sınıflandırmanın iki yolunu göstermektedir:

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Operatör overloadability

Koşullu işleç aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [koşullu işleç](~/_csharplang/spec/expressions.md#conditional-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [if-else beyanı](../keywords/if-else.md)
- [?. ve ?[] işleçleri](member-access-operators.md#null-conditional-operators--and-)
- [?? işlecinde](null-coalescing-operator.md)
- [ref anahtar sözcüğü](../keywords/ref.md)
