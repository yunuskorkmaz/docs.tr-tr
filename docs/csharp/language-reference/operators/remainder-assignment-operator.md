---
title: '%= İşleci (C# Başvurusu)'
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: ab3a6a8d5cbfeb4d527ca1f9c233ddfaba3d35ff
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188722"
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
  
[Kalan işleci](remainder-operator.md) `%` işlenenleri bir bölme işleminden kalanı hesaplar. Tüm sayısal türler tarafından desteklenir.

Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [kalan işleci](remainder-operator.md) `%`, kalan atama işleci `%=` örtük olarak aşırı yüklendi.
  
Aşağıdaki örnek, kullanımını gösterir. `%=` işleci:

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
