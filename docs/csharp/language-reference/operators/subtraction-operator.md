---
title: '- ve-= işleçleri- C# başvuru'
ms.custom: seodec18
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
ms.openlocfilehash: cf642fcac7233d27f2ed9052829c145038e93419
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038880"
---
# <a name="--and---operators-c-reference"></a>-ve-= işleçleri (C# başvuru)

`-` ve `-=` işleçleri, yerleşik [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri ve [temsilci](../builtin-types/reference-types.md#the-delegate-type) türleri tarafından desteklenir.

Aritmetik `-` işleci hakkında daha fazla bilgi için, [Aritmetik işleçler](arithmetic-operators.md) makalesinin [birli Plus ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [çıkarma işleci](arithmetic-operators.md#subtraction-operator--) bölümlerine bakın.

## <a name="delegate-removal"></a>Temsilci kaldırma

Aynı [temsilci](../builtin-types/reference-types.md#the-delegate-type) türünün işlenenleri için `-` işleci aşağıdaki şekilde hesaplanan bir temsilci örneği döndürür:

- Her iki işlenen de null değilse ve sağ işlenenin çağırma listesi, sol işlenenin çağırma listesinin uygun bir bitişik alt listesi ise, işlemin sonucu sağ işlenen tarafından alınan yeni bir çağırma listesidir. sol işlenenin çağırma listesinden girişler. Sağ işlenenin listesi sol işlenenin listesindeki birden çok bitişik alt listeyle eşleşiyorsa, yalnızca en sağdaki eşleme alt listesi kaldırılır. Kaldırma işlemi boş bir liste ile sonuçlanırsa sonuç `null`.

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- Sağ işlenenin çağırma listesi, sol işlenenin çağırma listesinin uygun bir bitişik alt listesi değilse, işlemin sonucu sol işlenenin bir sonucudur. Örneğin, çok noktaya yayın temsilcisinin parçası olmayan bir temsilciyi kaldırmak, hiçbir şey yapmaz ve değişmeyen çok noktaya yayın temsilcisine neden olur.

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  Yukarıdaki örnek ayrıca temsilci kaldırma temsilci örneklerinin karşılaştırıldığı gösterilmektedir. Örneğin, aynı [lambda ifadelerinin](../../programming-guide/statements-expressions-operators/lambda-expressions.md) değerlendirmesinden üretilen temsilciler eşit değildir. Temsilci eşitliği hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md), [eşitlik işleçleri temsilcisi](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümüne bakın.

- Sol işlenen `null`, işlemin sonucu `null`. Sağ işlenen `null`, işlemin sonucu sol işlenenin bir sonucudur.

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

Temsilcileri birleştirmek için [`+` işlecini](addition-operator.md#delegate-combination)kullanın.

Temsilci türleri hakkında daha fazla bilgi için bkz. [Temsilciler](../../programming-guide/delegates/index.md).

## <a name="subtraction-assignment-operator--"></a>Çıkarma atama işleci-=

Gibi `-=` işlecini kullanan bir ifade

```csharp
x -= y
```

eşdeğerdir

```csharp
x = x - y
```

`x` yalnızca bir kez değerlendirilir.

Aşağıdaki örnek `-=` işlecinin kullanımını gösterir:

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

Bir [olaydan](../keywords/event.md)abonelik kaldırdığınızda kaldırılacak olay işleyicisi yöntemini belirtmek için `-=` işlecini de kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: olaylara abone olma ve aboneliği kaldırma](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür `-` işlecini [aşırı](operator-overloading.md) yükleyebilir. İkili `-` işleci aşırı yüklendiğinde, `-=` işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür `-=` işlecini açıkça aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [birli eksi işleci](~/_csharplang/spec/expressions.md#unary-minus-operator) ve [çıkarma işleci](~/_csharplang/spec/expressions.md#subtraction-operator) bölümlerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Aritmetik işleçler](arithmetic-operators.md)
- [+ ve + = işleçleri](addition-operator.md)
