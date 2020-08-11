---
title: '- ve-= işleçleri-C# başvurusu'
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
ms.openlocfilehash: c126837309b5fe3495a5e9e6af589892670b62c3
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063087"
---
# <a name="--and---operators-c-reference"></a>-ve-= işleçleri (C# Başvurusu)

`-`Ve `-=` işleçleri, yerleşik [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri ve [temsilci](../builtin-types/reference-types.md#the-delegate-type) türleri tarafından desteklenir.

Aritmetik operatör hakkında daha fazla bilgi için `-` , [Aritmetik Işleçler](arithmetic-operators.md) makalesinin [birli Plus ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [çıkarma işleci](arithmetic-operators.md#subtraction-operator--) bölümlerine bakın.

## <a name="delegate-removal"></a>Temsilci kaldırma

Aynı [temsilci](../builtin-types/reference-types.md#the-delegate-type) türünün işlenenleri için, `-` işleç aşağıdaki şekilde hesaplanan bir temsilci örneği döndürür:

- Her iki işlenen de null değilse ve sağ işlenenin çağırma listesi, sol işlenenin çağırma listesinin uygun bir bitişik alt listesi ise, işlemin sonucu, sol işlenenin çağırma listesinden sağ işlenen girişlerin kaldırılması yoluyla elde edilen yeni bir çağırma listesidir ve. Sağ işlenenin listesi sol işlenenin listesindeki birden çok bitişik alt listeyle eşleşiyorsa, yalnızca en sağdaki eşleme alt listesi kaldırılır. Kaldırma işlemi boş bir liste ile sonuçlanırsa sonuç olur `null` .

  [!code-csharp-interactive[delegate removal](snippets/shared/SubtractionOperator.cs#DelegateRemoval)]

- Sağ işlenenin çağırma listesi, sol işlenenin çağırma listesinin uygun bir bitişik alt listesi değilse, işlemin sonucu sol işlenenin bir sonucudur. Örneğin, çok noktaya yayın temsilcisinin parçası olmayan bir temsilciyi kaldırmak, hiçbir şey yapmaz ve değişmeyen çok noktaya yayın temsilcisine neden olur.

  [!code-csharp-interactive[delegate removal with no effect](snippets/shared/SubtractionOperator.cs#DelegateRemovalNoChange)]

  Yukarıdaki örnek ayrıca temsilci kaldırma temsilci örneklerinin karşılaştırıldığı gösterilmektedir. Örneğin, aynı [lambda ifadelerinin](lambda-expressions.md) değerlendirmesinden üretilen temsilciler eşit değildir. Temsilci eşitliği hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md), [eşitlik işleçleri temsilcisi](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümüne bakın.

- Sol işlenen ise `null` işlemin sonucu olur `null` . Sağ işlenen ise, `null` işlemin sonucu sol işlenenin bir sonucudur.

  [!code-csharp-interactive[delegate removal and null](snippets/shared/SubtractionOperator.cs#DelegateRemovalAndNull)]

Temsilcileri birleştirmek için [ `+` işlecini](addition-operator.md#delegate-combination)kullanın.

Temsilci türleri hakkında daha fazla bilgi için bkz. [Temsilciler](../../programming-guide/delegates/index.md).

## <a name="subtraction-assignment-operator--"></a>Çıkarma atama işleci-=

İşlecini kullanan bir ifade `-=` , örneğin

```csharp
x -= y
```

eşdeğerdir

```csharp
x = x - y
```

hariç `x` yalnızca bir kez değerlendirilir.

Aşağıdaki örnek işlecinin kullanımını gösterir `-=` :

[!code-csharp-interactive[-= examples](snippets/shared/SubtractionOperator.cs#SubtractAndAssign)]

Ayrıca, `-=` bir [olaydan](../keywords/event.md)abonelik aboneliğini kaldırdığınızda kaldırılacak olay işleyicisi yöntemini belirtmek için işlecini de kullanabilirsiniz. Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür işleci [aşırı](operator-overloading.md) yükleyebilir `-` . İkili `-` işleç aşırı yüklendiğinde, `-=` işleci de örtük olarak aşırı yüklenmiştir. Kullanıcı tanımlı bir tür işleci açıkça aşırı yüklenemez `-=` .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [birli eksi işleci](~/_csharplang/spec/expressions.md#unary-minus-operator) ve [çıkarma işleci](~/_csharplang/spec/expressions.md#subtraction-operator) bölümlerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [+ ve + = işleçleri](addition-operator.md)
