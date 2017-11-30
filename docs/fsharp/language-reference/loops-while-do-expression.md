---
title: "Döngüler: while...do İfadesi (F#)"
description: "Bkz. nasıl while... yapmak ifadesi, belirtilen test koşul doğru iken yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 6a186d75dcda383764949c2cd3b09bc9e3d1080a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
[F # dili başvurusu](index.md)

[Döngüler: `for...in` ifade](loops-for-in-expression.md)

[Döngüler: `for...to` ifade](loops-for-to-expression.md)
