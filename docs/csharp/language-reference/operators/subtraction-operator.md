---
title: '- ve -= işleçler - C# referans'
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 2017aade92e8d7ad2af7101a107122fa8d7b9e27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847657"
---
# <a name="--and---operators-c-reference"></a>- ve -= işleçleri (C# referansı)

Ve `-` `-=` işleçler yerleşik [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri ve [temsilci](../builtin-types/reference-types.md#the-delegate-type) türleri tarafından desteklenir.

Aritmetik `-` işleç hakkında bilgi için, [Aritmetik işleçleri](arithmetic-operators.md) makalesinin [Unary artı ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [Çıkarma işleci bölümlerine](arithmetic-operators.md#subtraction-operator--) bakın.

## <a name="delegate-removal"></a>Temsilci kaldırma

Aynı [temsilci](../builtin-types/reference-types.md#the-delegate-type) türündeki operandlar `-` için işleç aşağıdaki gibi hesaplanan bir temsilci örneği döndürür:

- Her iki operands null ve sağ operand invocation listesi sol operand çağırma listesiuygun bitişik alt listesi ise, operasyonun sonucu sağ operand'S kaldırarak elde edilen yeni bir çağırma listesi sol operand çağırma listesinden girişler. Sağ operand'ın listesi sol operand'ın listesinde birden çok bitişik alt listeyle eşleşiyorsa, yalnızca sağdaki en eşleşen alt liste kaldırılır. Kaldırma boş bir listeyle sonuçlanırsa, sonuç `null`.

  [!code-csharp-interactive[delegate removal](snippets/SubtractionOperator.cs#DelegateRemoval)]

- Sağ operand çağırma listesi sol operand çağırma listesi uygun bir bitişik alt listesi değilse, işlemin sonucu sol operand olduğunu. Örneğin, çok noktaya yayın temsilcisinin parçası olmayan bir temsilcinin kaldırılması hiçbir şey yapmaz ve değişmemiş çok noktaya yayın temsilcisiyle sonuçlanır.

  [!code-csharp-interactive[delegate removal with no effect](snippets/SubtractionOperator.cs#DelegateRemovalNoChange)]

  Önceki örnek, temsilci kaldırma temsilci örnekleri sırasında karşılaştırılabilen olduğunu da göstermektedir. Örneğin, özdeş [lambda ifadelerinin](../../programming-guide/statements-expressions-operators/lambda-expressions.md) değerlendirilmesinden üretilen temsilciler eşit değildir. Temsilci eşitliği hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Temsilci eşitliği işleçleri](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümüne bakın.

- Sol operand ise `null`, işlemin sonucudur. `null` Eğer sağ operand ise, `null`operasyonun sonucu sol operand olduğunu.

  [!code-csharp-interactive[delegate removal and null](snippets/SubtractionOperator.cs#DelegateRemovalAndNull)]

Temsilcileri birleştirmek için [ `+` işleci](addition-operator.md#delegate-combination)kullanın.

Temsilci türleri hakkında daha fazla bilgi [için, Bkz. Temsilciler.](../../programming-guide/delegates/index.md)

## <a name="subtraction-assignment-operator--"></a>Çıkarma atama sıcadı işleci -=

`-=` İşleç kullanarak bir ifade, gibi

```csharp
x -= y
```

eşdeğerdir

```csharp
x = x - y
```

`x` bunun dışında sadece bir kez değerlendirilir.

Aşağıdaki örnek, işleç `-=` kullanımını gösterir:

[!code-csharp-interactive[-= examples](snippets/SubtractionOperator.cs#SubtractAndAssign)]

Ayrıca, bir `-=` [olaydan](../keywords/event.md)aboneliğinizi kaldırdığınızda kaldırmak için bir olay işleyicisi yöntemini belirtmek için işleci de kullanırsınız. Daha fazla bilgi için [olaylara nasıl abone olunur ve bu etkinliklerden aboneliğinizi iptal edebilirsiniz.](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Kullanıcı tanımlı bir tür `-` operatörü [aşırı yükleyebilir.](operator-overloading.md) Bir ikili `-` işleç aşırı `-=` yüklendiğinde, işleç de örtülü olarak aşırı yüklenir. Kullanıcı tanımlı bir tür `-=` operatörü açıkça aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Unary eksi işleci](~/_csharplang/spec/expressions.md#unary-minus-operator) ve [Çıkarma işleci](~/_csharplang/spec/expressions.md#subtraction-operator) bölümlerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [+ ve += işleçleri](addition-operator.md)
