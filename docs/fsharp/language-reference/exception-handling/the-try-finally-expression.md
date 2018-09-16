---
title: 'Özel Durumlar: try...finally İfadesi (F#)'
description: "Bilgi nasıl F # ' try... finally' ifadesi, bir kod bloğu bir özel durum oluşturursa bile temizleme kodu yürütme olanak tanır."
ms.date: 05/16/2016
ms.openlocfilehash: 546a6b0619de6f51044600dc1ead73c6d5211299
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45683128"
---
# <a name="exceptions-the-tryfinally-expression"></a>Özel Durumlar: try...finally İfadesi

`try...finally` İfade bir kod bloğu bir özel durum oluşturursa bile temizleme kodu yürütme olanak sağlar.

## <a name="syntax"></a>Sözdizimi

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Açıklamalar

`try...finally` İfade, kodda yürütülecek kullanılabilir *expression2* yürütülmesi sırasında bir özel durum olup oluşturulan bağımsız olarak yukarıdaki söz diziminde *İfade1*.

Türünü *expression2* tüm ifadenin değerine katılmadığı bir özel durum oluşmaz, döndürülen tür son değer *İfade1*. Bir özel durum oluştuğunda hiçbir değer döndürülmez ve çağrı yığınına sonraki eşleşen özel durum işleyicisine denetim akışını aktarır. Hiçbir özel durum işleyicisi bulunursa, program sona erer. Eşleşen bir işleyici içinde kod yürütülür veya program sona erer, kodda önce `finally` dal yürütülür.

Aşağıdaki kod kullanımını gösterir `try...finally` ifade.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

Konsola çıktı aşağıdaki gibidir.

```
Closing stream
Exception handled.
```

Dıştaki özel durum işlenmiş önce çıktısı görebileceğiniz gibi akış kapatıldı ve dosya `test.txt` metni içeren `test1`, arabellek Temizlenen ve özel durum aktarılan olsa bile diske yazılan gösterir dıştaki özel durum işleyicisine denetler.

Unutmayın `try...with` yapıdır öğesinden ayrı bir yapısı `try...finally` oluşturun. Bu nedenle, kodunuzu hem gerektiriyorsa bir `with` blok ve `finally` blok, aşağıdaki kod örneğinde olduğu gibi iki yapılarını iç içe zorunda.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

Hesaplama ifadeleri bağlamında, dizi ifadeleri ve zaman uyumsuz iş akışları dahil olmak üzere **try... finally** ifadeleri, özel bir uygulama olabilir. Daha fazla bilgi için [hesaplama ifadeleri](../computation-expressions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel durumlar: `try...with` ifadesi](the-try-with-expression.md)
