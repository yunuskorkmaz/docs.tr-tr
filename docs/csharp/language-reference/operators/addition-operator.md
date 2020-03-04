---
title: + ve + = işleçleri- C# başvuru
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
ms.openlocfilehash: c8452ab1f90bb2873a591b483b5432311a9f9b79
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239632"
---
# <a name="-and--operators-c-reference"></a>+ ve + = işleçleri (C# başvuru)

`+` ve `+=` işleçleri, yerleşik [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri, [dize](../builtin-types/reference-types.md#the-string-type) türü ve [temsilci](../builtin-types/reference-types.md#the-delegate-type) türleri tarafından desteklenir.

Aritmetik `+` işleci hakkında daha fazla bilgi için, [Aritmetik işleçler](arithmetic-operators.md) makalesinin [birli Plus ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [ek işleç +](arithmetic-operators.md#addition-operator-) bölümlerine bakın.

## <a name="string-concatenation"></a>Dize birleştirme

Bir veya her iki işlenen de [dize](../builtin-types/reference-types.md#the-string-type)türünde olduğunda, `+` işleci işlenenlerinin dize temsillerini birleştirir:

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

C# 6 ' dan başlayarak [dize ilişkilendirme](../tokens/interpolated.md) , dizeleri biçimlendirmek için daha kolay bir yol sağlar:

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Temsilci birleşimi

Aynı [temsilci](../builtin-types/reference-types.md#the-delegate-type) türünün işlenenleri için `+` işleci, çağrıldığında sol işlenen ve sonra sağ işleneni çağıran yeni bir temsilci örneği döndürür. İşlenenlerin herhangi biri `null`ise, `+` işleci başka bir işlenenin değerini döndürür (Bu da `null`olabilir). Aşağıdaki örnek, temsilcilerin `+` işleçle nasıl birleştirilebilme gösterir:

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

Temsilci kaldırma işlemini gerçekleştirmek için [`-` işlecini](subtraction-operator.md#delegate-removal)kullanın.

Temsilci türleri hakkında daha fazla bilgi için bkz. [Temsilciler](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>Toplama atama işleci + =

Gibi `+=` işlecini kullanan bir ifade

```csharp
x += y
```

eşdeğerdir

```csharp
x = x + y
```

`x` hariç, yalnızca bir kez değerlendirilir.

Aşağıdaki örnek `+=` işlecinin kullanımını gösterir:

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

Bir [olaya](../keywords/event.md)abone olduğunuzda bir olay işleyicisi yöntemi belirtmek için `+=` işlecini de kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: olaylara abone olma ve aboneliği kaldırma](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür `+` işlecini [aşırı](operator-overloading.md) yükleyebilir. İkili `+` işleci aşırı yüklendiğinde, `+=` işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür `+=` işlecini açıkça aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [birli Plus işleci](~/_csharplang/spec/expressions.md#unary-plus-operator) ve [ekleme işleci](~/_csharplang/spec/expressions.md#addition-operator) bölümlerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Birden çok dizeyi birleştirme](../../how-to/concatenate-multiple-strings.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Aritmetik işleçler](arithmetic-operators.md)
- [-ve-= işleçleri](subtraction-operator.md)
