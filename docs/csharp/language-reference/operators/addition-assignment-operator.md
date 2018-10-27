---
title: += İşleci (C# Başvurusu)
ms.date: 10/22/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ee335e3e2e7d352d4e26b802bad2b08a05c666ab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
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

Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [Toplama işleci](addition-operator.md) `+`, toplama atama işleci `+=` örtük olarak aşırı yüklendi.

Ayrıca `+=` a abone olduğunuzda bir olay işleyicisi yöntemi belirtmek için işleci bir [olay](../keywords/event.md). Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği, olaylarından](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

Aşağıdaki örnek, kullanımını gösterir. `+=` işleci:

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Temsilciler](../../programming-guide/delegates/index.md)
