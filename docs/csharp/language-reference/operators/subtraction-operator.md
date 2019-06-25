---
title: '- ve-= operators - C# başvurusu'
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
ms.openlocfilehash: 7c9863134cb2a12072954bb283c7828abece3adb
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347906"
---
# <a name="--and---operators-c-reference"></a>- ve-= işleçleri (C# Başvurusu)

`-` İşleci yerleşik sayısal türler tarafından desteklenir ve [temsilci](../keywords/delegate.md) türleri.

Aritmetik hakkında bilgi için `-` işleci bkz [birli artı ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [çıkarma işleci -](arithmetic-operators.md#subtraction-operator--) bölümlerini [aritmetikişleçler](arithmetic-operators.md) makalesi.

## <a name="delegate-removal"></a>Temsilci kaldırma

Aynı işlenenleri için [temsilci](../keywords/delegate.md) türü `-` işleci aşağıdaki gibi hesaplanır bir temsilci örneği döndürür:

- Her iki işlenen de null olmayan ve çağırma listesi sağ işlenenin çağırma listenin sol işlenenin uygun bitişik alt liste ise, işlemin sonucunu, sağ işlenen 's kaldırarak alınan yeni çağırma listesidir Sol işlenenin çağırma listeden girdileri. Sol işlenen 's listesinde birden çok bitişik alt listelerin atamada sağ işlenen 's listesiyle eşleşen yalnızca en sağdaki eşleşen alt liste kaldırılır. Kaldırma işlemi boş bir liste sonuçlanırsa sonucudur `null`.

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- Sağ işlenen çağırma listesi çağırma listenin sol işlenenin uygun bitişik alt liste değilse, işlemin sonucunu sol işlenen ' dir. Örneğin, çok noktaya yayın temsilci bir parçası olmayan bir temsilci kaldırma hiçbir şey yapmaz ve değişmeden çok noktaya yayın Temsilcide sonuçlanır.

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  Yukarıdaki örnekte, temsilci sırasında temizleme temsilci örneklerini karşılaştırılır de gösterir. Örneğin, özdeş bir değerlendirmesinden gelen üretilen Temsilciler [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md) eşit değildir. Temsilci eşitlik hakkında daha fazla bilgi için bkz: [temsilci eşitlik işleçleri](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

- Sol işlenen `null`, işlem sonucu `null`. Sağ işlenen `null`, sol işlenen işleminin sonucudur.

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

Temsilciler birleştirmek için kullanın [ `+` işleci](addition-operator.md#delegate-combination).

Temsilci türleri hakkında daha fazla bilgi için bkz: [Temsilciler](../../programming-guide/delegates/index.md).

## <a name="subtraction-assignment-operator--"></a>Çıkarma atama işleci-=

Bir ifade kullanarak `-=` işleci gibi

```csharp
x -= y
```

eşdeğerdir

```csharp
x = x - y
```

dışında `x` yalnızca bir kez değerlendirilir.
  
Aşağıdaki örnek, kullanımını gösterir. `-=` işleci:

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

Ayrıca `-=` abonelikten çıkma kaldırmak için bir olay işleyicisi yöntemi belirtmek için işleci bir [olay](../keywords/event.md). Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği olaylardan](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `-` işleci. Bir ikili olduğunda `-` işleci aşırı yüklenmiş, `-=` işleci örtük olarak aşırı yüklenmiş, ayrıca. Kullanıcı tanımlı bir türe açıkça aşırı yüklenemez `-=` işleci.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [birli eksi işleci](~/_csharplang/spec/expressions.md#unary-minus-operator) ve [çıkarma işleci](~/_csharplang/spec/expressions.md#subtraction-operator) bölümlerini [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- [Temsilciler](../../programming-guide/delegates/index.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Aritmetik işleçler](arithmetic-operators.md)
- [+ ve += işleçleri](addition-operator.md)
