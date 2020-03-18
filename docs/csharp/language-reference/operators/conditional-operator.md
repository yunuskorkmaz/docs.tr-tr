---
title: '?: operatör - C# referansı'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 1a17ba092d4228ba909c8774a2f7e15c2c50cfdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399520"
---
# <a name="-operator-c-reference"></a>?: işleç (C# referansı)

Koşullu işleç `?:`, üçüncül koşullu işleç olarak da bilinir, boolean ifadesini değerlendirir ve Boolean ifadesinin değerlendirip değerlendirmediğine `true` bağlı `false`olarak iki ifadeden birinin sonucunu döndürür.

Koşullu işleç için sözdizimi aşağıdaki gibidir:

```csharp
condition ? consequent : alternative
```

İfade `condition` yi `true` değerlendirmeli `false`veya . Değerlendiriliyorsa, `condition` `consequent` ifade değerlendirilir ve sonucu işlemin sonucu olur. `true` Değerlendiriliyorsa, `condition` `alternative` ifade değerlendirilir ve sonucu işlemin sonucu olur. `false` Yalnızca `consequent` `alternative` veya değerlendirilir.

Türü `consequent` ve `alternative` aynı olmalıdır veya bir tür diğerine örtülü bir dönüştürme olmalıdır.

Koşullu işleç sağ-bağşdırıcı, yani formun bir ifadesidir

```csharp
a ? b : c ? d : e
```

olarak değerlendirilir

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> Koşullu işleç nasıl değerlendirildiğini hatırlamak için aşağıdaki mnemonik cihazı kullanabilirsiniz:
>
> ```text
> is this condition true ? yes : no
> ```

Aşağıdaki örnek, koşullu işleç kullanımını gösterir:

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Koşullu ref ekspresyonu

C# 7.2 ile başlayarak, koşullu [ref](../keywords/ref.md#ref-locals) ekspresyonu ile koşullu olarak yerel veya [ref reisi yerel](../keywords/ref.md#ref-readonly-locals) değişken atanabilir. Koşullu ref ifadesini [referans döndürme değeri](../keywords/ref.md#reference-return-values) olarak veya [ `ref` yöntem bağımsız değişkeni](../keywords/ref.md#passing-an-argument-by-reference)olarak da kullanabilirsiniz.

Koşullu ref ifadesinin sözdizimi aşağıdaki gibidir:

```csharp
condition ? ref consequent : ref alternative
```

Özgün koşullu işleç gibi, koşullu ref ifadesi de iki ifadeden yalnızca birini değerlendirir: ya `consequent` da `alternative`.

Koşullu ref ekspresyonu durumunda, türü `consequent` `alternative` ve aynı olmalıdır.

Aşağıdaki örnek, koşullu ref ifadesinin kullanımını gösterir:

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Koşullu işleç `if..else` ve deyim

[If-else](../keywords/if-else.md) deyimi yerine koşullu işlecinin kullanılması, bir değeri hesaplamak için koşullu olarak ihtiyaç duyduğunuz durumlarda daha kısa koda neden olabilir. Aşağıdaki örnek, bir karşıcıyı negatif veya negatif olmayan olarak sınıflandırmanın iki yolunu gösterir:

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Kullanıcı tanımlı bir tür koşullu işleç aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Koşullu işleci](~/_csharplang/spec/expressions.md#conditional-operator) bölümüne bakın.

Koşullu ref ifadesi hakkında daha fazla bilgi için [özellik teklif notuna](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [if-else deyimi](../keywords/if-else.md)
- [?. Ve? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)
- [?? Ve?? = operatörler](null-coalescing-operator.md)
- [ref anahtar kelime](../keywords/ref.md)
