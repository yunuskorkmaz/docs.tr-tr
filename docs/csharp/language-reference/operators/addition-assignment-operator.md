---
title: += İşleci (C# Başvurusu)
ms.date: 10/29/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ac9330e283cb58ae4e0ee7b644aa2c22bdf64c46
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50192037"
---
# <a name="-operator-c-reference"></a>+= İşleci (C# Başvurusu)

Toplama atama işleci.

Bir ifade kullanarak `+=` işleci gibi

```csharp
x += y
```

eşdeğerdir

```csharp
x = x + y
```

dışında `x` yalnızca bir kez değerlendirilir.
  
Sayısal türlerin [Toplama işleci](addition-operator.md) `+` işlenenleri toplamını hesaplar. Bir veya iki işlenenin türü ise [dize](../keywords/string.md), işlenenleri dize temsillerini art arda ekler. Temsilci türleri için `+` işleci işlenenleri birleşimi olan yeni bir temsilci örneği döndürür.

Ayrıca `+=` a abone olduğunuzda bir olay işleyicisi yöntemi belirtmek için işleci bir [olay](../keywords/event.md). Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği, olaylarından](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

Aşağıdaki örnek, kullanımını gösterir. `+=` işleci:

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [Toplama işleci](addition-operator.md) `+`, toplama atama işleci `+=` örtük olarak aşırı yüklendi. Kullanıcı tanımlı bir tür toplama atama işleci açıkça aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) ve [olay ataması](~/_csharplang/spec/expressions.md#event-assignment) bölümlerini [ C# dil belirtimi](../language-specification/index.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Temsilciler](../../programming-guide/delegates/index.md)
