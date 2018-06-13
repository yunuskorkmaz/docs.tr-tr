---
title: 'Döngüler: while...do İfadesi (F#)'
description: 'Bkz: nasıl... sırada yapmak ifadesi, belirtilen test koşul doğru iken yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.'
ms.date: 05/16/2016
ms.openlocfilehash: e3198246e44bbb11b226f04da6795f3da22626e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562238"
---
# <a name="loops-whiledo-expression"></a>Döngüler: while...do İfadesi

`while...do` İfadesi, belirtilen test koşul doğru iken yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.


## <a name="syntax"></a>Sözdizimi

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Açıklamalar
*Test ifade* etkinleştirilmişse; değerlendirilir `true`, *gövde ifade* yürütülür ve test deyim yeniden değerlendirilir. *Gövde ifade* türünde olmalıdır `unit`. Test ifade ise `false`, yineleme sona erer.

Aşağıdaki örnek kullanımını göstermektedir `while...do` ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

Önceki kod çıkışı biri son 10'dur bir rastgele sayı 1 ve 20 arasında akışıdır.

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
Kullanabileceğiniz `while...do` sequence ifadeleri ve diğer hesaplama ifadeleri özelleştirilmiş bir sürümünü durumda içinde `while...do` ifade kullanılır. Daha fazla bilgi için bkz: [sıraları](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [hesaplama ifadeleri](computation-expressions.md).


## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Döngüler: `for...in` ifade](loops-for-in-expression.md)

[Döngüler: `for...to` ifade](loops-for-to-expression.md)
