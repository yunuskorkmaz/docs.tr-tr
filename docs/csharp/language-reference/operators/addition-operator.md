---
title: + ve += operators - C# başvurusu
ms.custom: seodec18
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: fdcacd1b312c1e0c0314cb66adaf1ae53b1afae4
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758427"
---
# <a name="-and--operators-c-reference"></a>+ ve += işleçleri (C# Başvurusu)

`+` İşleci yerleşik sayısal türler tarafından desteklenen [dize](../keywords/string.md) türü ve [temsilci](../keywords/delegate.md) türleri.

Aritmetik hakkında bilgi için `+` işleci bkz [birli artı ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [Toplama işleci +](arithmetic-operators.md#addition-operator-) bölümlerini [aritmetik işleçler](arithmetic-operators.md)makalesi.

## <a name="string-concatenation"></a>Dize birleştirme

Bir veya iki işlenenin türünde olduğunda [dize](../keywords/string.md), `+` işleci, işlenenleri dize temsillerini art arda ekler:

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

İle başlayarak C# 6, [dize ilişkilendirme](../tokens/interpolated.md) biçim dizeleri için daha kolay bir yol sağlar:

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Temsilci birleşimi

Aynı işlenenleri için [temsilci](../keywords/delegate.md) türü `+` işleci döndüren yeni bir temsilci örneği, çağrılır, birinci işlenenin çağırır ve ardından ikinci işlenenin çağırır. İşlenenden ise `null`, `+` işleci, başka bir işlenenin değerini döndürür (Ayrıca olabilen `null`). Aşağıdaki örnek, temsilciler ne birleştirilebilir gösterir `+` işleci:

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

Temsilci kaldırma gerçekleştirmek için [ `-` işleci](subtraction-operator.md#delegate-removal).

Temsilci türleri hakkında daha fazla bilgi için bkz: [Temsilciler](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>Toplama atama işleci +=

Bir ifade kullanarak `+=` işleci gibi

```csharp
x += y
```

eşdeğerdir

```csharp
x = x + y
```

dışında `x` yalnızca bir kez değerlendirilir.
  
Aşağıdaki örnek, kullanımını gösterir. `+=` işleci:

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

Ayrıca `+=` a abone olduğunuzda bir olay işleyicisi yöntemi belirtmek için işleci bir [olay](../keywords/event.md). Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği olaylardan](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `+` işleci. Bir ikili olduğunda `+` işleci aşırı yüklenmiş, `+=` işleci örtük olarak aşırı yüklenmiş, ayrıca. Kullanıcı tanımlı bir türe açıkça aşırı yüklenemez `+=` işleci.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [birli artı işleci](~/_csharplang/spec/expressions.md#unary-plus-operator) ve [Toplama işleci](~/_csharplang/spec/expressions.md#addition-operator) bölümlerini [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [Dize ilişkilendirme](../tokens/interpolated.md)
- [Nasıl yapılır: birden çok dizeyi birleştirme](../../how-to/concatenate-multiple-strings.md)
- [Temsilciler](../../programming-guide/delegates/index.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Checked ve unchecked](../keywords/checked-and-unchecked.md)
- [Aritmetik işleçler](arithmetic-operators.md)
- [- ve-= işleçleri](subtraction-operator.md)
