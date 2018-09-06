---
title: '%= İşleci (C# Başvurusu)'
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: c475517666bdadaa457dbb4188808b3a96fcdf0e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43738294"
---
# <a name="-operator-c-reference"></a>%= İşleci (C# Başvurusu)

Kalan atama işleci.

Bir ifade kullanarak `%=` işleci gibi  

```csharp
x %= y
```  

eşdeğerdir  

```csharp
x = x % y
```  

dışında `x` yalnızca bir kez değerlendirilir.
  
[Kalan işleci](remainder-operator.md) `%` tüm sayısal türler tarafından desteklenir ve işlenenleri bir bölme işleminden kalanı hesaplar.

Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [kalan işleci](remainder-operator.md) `%`, kalan atama işleci `%=` örtük olarak aşırı yüklendi.
  
Aşağıdaki örnek, kullanımını gösterir. `%=` işleci:

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
