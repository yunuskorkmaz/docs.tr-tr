---
title: '?: Operator - C# başvurusu'
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
ms.openlocfilehash: c3c875cf5b8d1b5e69cd76cb0ee4df0a989a35a0
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202905"
---
# <a name="-operator-c-reference"></a>?: İşleci (C# Başvurusu)

Koşullu işleç `?:`Üçlü koşullu işleç, yaygın olarak bilinen bir Boole ifadesini değerlendirir ve bir Boole ifadesi mi değerlendiren bağlı olarak iki ifadenin değerlendirme sonucu döndürür `true` veya `false`. İle başlayarak C# 7.2, [ref koşullu ifadesi](#conditional-ref-expression) başvuru iki ifadeden birini sonucunu döndürür.

Koşullu işlecin sözdizimi aşağıdaki gibidir:

```csharp
condition ? consequence : alternative
```

`condition` İfade gerekir değerlendirmek için `true` veya `false`. Varsa `condition` değerlendiren `true`, `consequence` ifade değerlendirilir ve sonuç işleminin sonucu haline gelir. Varsa `condition` değerlendiren `false`, `alternative` ifade değerlendirilir ve sonuç işleminin sonucu haline gelir. Yalnızca `consequence` veya `alternative` değerlendirilir.

Türünü `consequence` ve `alternative` aynı veya orada bir türden diğerine örtülü bir dönüştürme diğerine olmalıdır olması gerekir.

Koşullu işleç sağla ilişkilendirilebilir, diğer bir deyişle, bir ifade formu

```csharp
a ? b : c ? d : e
```

olarak değerlendirilir

```csharp
a ? b : (c ? d : e)
```

Aşağıdaki örnek, koşullu işlecinin kullanımını gösterir:

[!code-csharp[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Ref koşullu ifadesi

İle başlayarak C# 7.2, iki ifadeden birini sonucu başvuru döndürmek için koşullu ref ifadesini kullanabilirsiniz. Bu başvuru atayabilirsiniz bir [ref yerel](../keywords/ref.md#ref-locals) veya [salt okunur yerel başvuru](../keywords/ref.md#ref-readonly-locals) değişkeni veya olarak bir [başvuru dönüş değeri](../keywords/ref.md#reference-return-values) veya farklı bir [ `ref` yöntemi parametre](../keywords/ref.md#passing-an-argument-by-reference).

Ref koşullu ifadesi sözdizimi aşağıdaki gibidir:

```csharp
condition ? ref consequence : ref alternative
```

Ref koşullu ifadesi iki ifadeden yalnızca biri özgün koşullu işleç gibi değerlendirilir: ya da `consequence` veya `alternative`.

Ref koşullu ifadenin türü söz konusu olduğunda `consequence` ve `alternative` aynı olmalıdır.

Aşağıdaki örnek, ref koşullu ifadesi kullanımını göstermektedir:

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

Daha fazla bilgi için [özellik teklif Not](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md).

## <a name="conditional-operator-and-an-ifelse-statement"></a>Koşullu işleç ve bir `if..else` deyimi

Üzerinde koşullu işlecinin kullanımı bir [if-else](../keywords/if-else.md) deyimi neden olabilir durumlarda daha kısa kodu koşullu olarak bir değeri hesaplamak gerektiğinde. Aşağıdaki örnek, negatif veya negatif olmayan tamsayı sınıflandırmak için iki yolunu gösterir:

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>İşleç overloadability

Koşullu işleç aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [koşullu işleç](~/_csharplang/spec/expressions.md#conditional-operator) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [if-else deyimi](../keywords/if-else.md)
- [?. and ?[] İşleçleri](null-conditional-operators.md)
- [?? İşleç](null-coalescing-operator.md)
- [ref anahtar sözcüğü](../keywords/ref.md)
