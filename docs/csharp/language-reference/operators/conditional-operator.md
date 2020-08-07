---
title: '?: operator-C# başvurusu'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: fcde0476935108122d7f7e825d701e48952873f6
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916850"
---
# <a name="-operator-c-reference"></a>?: işleci (C# Başvurusu)

Üçlü işleç olarak da bilinen koşullu operatör, Boole ifadesi `?:` değerlendirir ve Boolean ifadesinin veya olarak değerlendirildiğine bağlı olarak iki deyimden birinin sonucunu döndürür `true` `false` .

Koşullu işlecin sözdizimi şöyledir:

```csharp
condition ? consequent : alternative
```

`condition`İfade veya olarak değerlendirilmelidir `true` `false` . `condition`, Olarak değerlendirilirse `true` , `consequent` ifade değerlendirilir ve sonucu işlemin sonucu olur. `condition`, Olarak değerlendirilirse `false` , `alternative` ifade değerlendirilir ve sonucu işlemin sonucu olur. Yalnızca `consequent` veya `alternative` değerlendirilir.

`consequent`Ve türü aynı olmalıdır `alternative` veya bir türden diğerine örtük bir dönüştürme olmalıdır.

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

[!code-csharp-interactive[non ref conditional](snippets/shared/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Koşullu başvuru ifadesi

C# 7,2 ile başlayarak, bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkeni koşullu başvuru ifadesiyle koşullu olarak atanabilir. Koşullu başvuru ifadesini [Başvuru dönüş değeri](../keywords/ref.md#reference-return-values) veya [ `ref` Yöntem bağımsız değişkeni](../keywords/ref.md#passing-an-argument-by-reference)olarak da kullanabilirsiniz.

Koşullu başvuru ifadesi için sözdizimi aşağıdaki gibidir:

```csharp
condition ? ref consequent : ref alternative
```

Özgün Koşul operatörü gibi, koşullu başvuru ifadesi iki ifadeden yalnızca birini değerlendirir: `consequent` ya da `alternative` .

Koşullu başvuru ifadesi söz konusu olduğunda, `consequent` ve türü `alternative` aynı olmalıdır.

Aşağıdaki örnek, koşullu başvuru ifadesinin kullanımını gösterir:

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Koşullu işleç ve bir `if..else` ifade

[İf-else](../keywords/if-else.md) ifadesinin yerine koşullu işlecin kullanılması, bir değeri hesaplamak için koşullu olarak bir değer hesaplamanız gerektiğinde daha kısa kod oluşmasına neden olacaktır. Aşağıdaki örnek, bir tamsayıyı negatif veya negatif olmayan olarak sınıflandırmanın iki yolunu göstermektedir:

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür, koşullu işleci aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [koşullu işleç](~/_csharplang/spec/expressions.md#conditional-operator) bölümüne bakın.

Koşullu başvuru ifadesi hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [if-else deyimi](../keywords/if-else.md)
- [?. '? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)
- [?? ve?? = işleçleri](null-coalescing-operator.md)
- [ref anahtar sözcüğü](../keywords/ref.md)
