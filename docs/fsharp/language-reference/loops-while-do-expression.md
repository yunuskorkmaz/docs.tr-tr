---
title: 'Döngüler: while...do İfadesi (F#)'
description: 'Bkz: nasıl sırada... yapmak ifadesi belirtilen test koşulu true olduğu sürece, yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.'
ms.date: 05/16/2016
ms.openlocfilehash: 43e2098ad6c7f103babc2471aebe987040feb989
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127283"
---
# <a name="loops-whiledo-expression"></a>Döngüler: while...do İfadesi

`while...do` İfadesi belirtilen test koşulu true olduğu sürece, yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Açıklamalar

*Test ifade* ise; değerlendirilir `true`, *gövde ifadesi* yürütülür ve test ifade tekrar değerlendirilir. *Gövde ifadesi* türüne sahip olmalıdır `unit`. Test ifade ise `false`, yineleme sona erer.

Aşağıdaki örnek, kullanımını gösterir `while...do` ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

Önceki kodun çıktısı biri son 10'dur bir rastgele sayı 1 ile 20 arasında akışıdır.

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> Kullanabileceğiniz `while...do` sequence ifadeleri ve diğer hesaplama ifadeleri, özelleştirilmiş bir sürümünü durumda `while...do` ifade kullanılır. Daha fazla bilgi için [dizileri](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [hesaplama ifadeleri](computation-expressions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Döngüler: `for...in` İfade](loops-for-in-expression.md)
- [Döngüler: `for...to` İfade](loops-for-to-expression.md)
