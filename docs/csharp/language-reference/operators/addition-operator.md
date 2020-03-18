---
title: + ve += işleçleri - C# referansı
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
ms.openlocfilehash: cafd07f4b4aefdcc4b43750d61c155fe3d65aa46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399303"
---
# <a name="-and--operators-c-reference"></a>+ ve += işleçleri (C# referansı)

Ve `+` `+=` işleçler yerleşik [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri, [dize](../builtin-types/reference-types.md#the-string-type) türü ve [temsilci](../builtin-types/reference-types.md#the-delegate-type) türleri tarafından desteklenir.

Aritmetik `+` işleç hakkında bilgi için, [Aritmetik işleçleri](arithmetic-operators.md) makalesinin [Unary artı ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [Ek işleci +](arithmetic-operators.md#addition-operator-) bölümlerine bakın.

## <a name="string-concatenation"></a>Dize concatenation

Bir veya her iki operands tip `+` [dize](../builtin-types/reference-types.md#the-string-type)olduğunda, işleç onun operands dize gösterimleri concatenates:

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

C# 6 ile başlayarak, [string enterpolasyonu](../tokens/interpolated.md) dizeleri biçimlendirmek için daha uygun bir yol sağlar:

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Temsilci kombinasyonu

Aynı [temsilci](../builtin-types/reference-types.md#the-delegate-type) türündeki operandlar `+` için, işleç çağrıldığı zaman sol operand'ı çağıran ve sonra sağ operand'ı çağıran yeni bir temsilci örneği döndürür. Operands herhangi biri `null`ise, `+` operatör başka bir operand değerini döndürür (aynı zamanda olabilir). `null` Aşağıdaki örnek, temsilcilerin `+` işleçle nasıl birleştirilebileceğini gösterir:

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

Temsilci kaldırma gerçekleştirmek için [ `-` işleci](subtraction-operator.md#delegate-removal)kullanın.

Temsilci türleri hakkında daha fazla bilgi [için, Bkz. Temsilciler.](../../programming-guide/delegates/index.md)

## <a name="addition-assignment-operator-"></a>Ek atama işleci +=

`+=` İşleç kullanarak bir ifade, gibi

```csharp
x += y
```

eşdeğerdir

```csharp
x = x + y
```

`x` bunun dışında sadece bir kez değerlendirilir.

Aşağıdaki örnek, işleç `+=` kullanımını gösterir:

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

Ayrıca, bir `+=` [olaya](../keywords/event.md)abone olduğunuzda bir olay işleyicisi yöntemini belirtmek için işleci de kullanırsınız. Daha fazla bilgi için [bkz: Etkinliklere abone](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)olun ve abonelikten çıkın.

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Kullanıcı tanımlı bir tür `+` operatörü [aşırı yükleyebilir.](operator-overloading.md) Bir ikili `+` işleç aşırı `+=` yüklendiğinde, işleç de örtülü olarak aşırı yüklenir. Kullanıcı tanımlı bir tür `+=` operatörü açıkça aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Unary artı operatörü](~/_csharplang/spec/expressions.md#unary-plus-operator) ve Ek [işleci](~/_csharplang/spec/expressions.md#addition-operator) bölümlerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Birden çok dize nasıl işlenir?](../../how-to/concatenate-multiple-strings.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [- ve -= operatörler](subtraction-operator.md)
