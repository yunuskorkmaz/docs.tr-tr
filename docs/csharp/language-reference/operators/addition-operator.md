---
description: + ve + = işleçleri-C# başvurusu
title: + ve + = işleçleri-C# başvurusu
ms.date: 04/23/2020
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
ms.openlocfilehash: 00ba020939694d901afdbf5f5f93b584363d2cc7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141861"
---
# <a name="-and--operators-c-reference"></a>+ ve + = işleçleri (C# Başvurusu)

`+`Ve `+=` işleçleri yerleşik [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri, [dize](../builtin-types/reference-types.md#the-string-type) türü ve [temsilci](../builtin-types/reference-types.md#the-delegate-type) türleri tarafından desteklenir.

Aritmetik operatör hakkında daha fazla bilgi için `+` , [Aritmetik Işleçler](arithmetic-operators.md) makalesinin [birli Plus ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [ek işleç +](arithmetic-operators.md#addition-operator-) bölümlerine bakın.

## <a name="string-concatenation"></a>Dize birleştirme

Bir veya her iki işlenen de [dize](../builtin-types/reference-types.md#the-string-type)türünde olduğunda işleç, `+` işlenenlerinin dize temsillerini birleştirir (öğesinin dize temsili `null` boş bir dizedir):

[!code-csharp-interactive[string concatenation](snippets/shared/AdditionOperator.cs#AddStrings)]

C# 6 ' dan itibaren [dize ilişkilendirme](../tokens/interpolated.md) , dizeleri biçimlendirmek için daha kolay bir yol sağlar:

[!code-csharp-interactive[string interpolation](snippets/shared/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Temsilci birleşimi

Aynı [temsilci](../builtin-types/reference-types.md#the-delegate-type) türünün işlenenleri için, `+` işleci çağrıldığında, sol taraftaki işleneni çağırır ve sonra sağ işleneni çağıran yeni bir temsilci örneği döndürür. İşlenenleri varsa `null` , `+` işleç başka bir işlenenin değerini (de olabilir `null` ) döndürür. Aşağıdaki örnek, temsilcilerin işleçle nasıl birleştirilebilme gösterir `+` :

[!code-csharp-interactive[delegate combination](snippets/shared/AdditionOperator.cs#AddDelegates)]

Temsilci kaldırma işlemini gerçekleştirmek için [ `-` işlecini](subtraction-operator.md#delegate-removal)kullanın.

Temsilci türleri hakkında daha fazla bilgi için bkz. [Temsilciler](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>Toplama atama işleci + =

İşlecini kullanan bir ifade `+=` , örneğin

```csharp
x += y
```

eşdeğerdir

```csharp
x = x + y
```

hariç `x` yalnızca bir kez değerlendirilir.

Aşağıdaki örnek işlecinin kullanımını gösterir `+=` :

[!code-csharp-interactive[+= examples](snippets/shared/AdditionOperator.cs#AddAndAssign)]

`+=`Bir [olaya](../keywords/event.md)abone olduğunuzda bir olay işleyicisi yöntemi belirtmek için işlecini de kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: olaylara abone olma ve aboneliği kaldırma](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür işleci [aşırı](operator-overloading.md) yükleyebilir `+` . İkili `+` işleç aşırı yüklendiğinde, `+=` işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür işleci açıkça aşırı yüklenemez `+=` .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [birli Plus işleci](~/_csharplang/spec/expressions.md#unary-plus-operator) ve [ekleme işleci](~/_csharplang/spec/expressions.md#addition-operator) bölümlerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [Birden çok dizeyi birleştirme](../../how-to/concatenate-multiple-strings.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [-ve-= işleçleri](subtraction-operator.md)
