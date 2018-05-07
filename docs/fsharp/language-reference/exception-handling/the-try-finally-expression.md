---
title: 'Özel Durumlar: try...finally İfadesi (F#)'
description: "Bilgi nasıl F # ' try... finally' ifadesi, bir kod bloğu bir özel durum oluşturursa bile temizleme kodu yürütme olanak tanır."
ms.date: 05/16/2016
ms.openlocfilehash: a5fdec7b3986fc9a85c34b08d20dc31947c92b2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-the-tryfinally-expression"></a>Özel Durumlar: try...finally İfadesi

`try...finally` İfade kod bloğu bir özel durum oluşturursa bile temizleme kodu yürütme olanak sağlar.


## <a name="syntax"></a>Sözdizimi

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Açıklamalar
`try...finally` İfade kod yürütmek için kullanılabilir *İfade2* olup bir özel durum yürütülmesi sırasında oluşturulan bağımsız olarak önceki sözdiziminde *İfade1*.

Türü *İfade2* tüm ifadenin değerine katılmadığı bir özel durum meydana gelmez, döndürülen türü son değeri *İfade1*. Bir özel durum oluştuğunda, bu değer döndürülür ve sonraki eşleşen özel durum işleyici çağrı yığını kurmak için denetim akışı aktarır. Hiçbir özel durum işleyicisi bulunursa, program sonlandırır. Eşleşen bir işleyici kodu yürütülen veya program sonlandırır, kodda önce `finally` şube gerçekleştirilir.

Aşağıdaki kod kullanımını gösteren `try...finally` ifade.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

Konsola çıktı aşağıdaki gibidir.

```
Closing stream
Exception handled.
```

Çıktısını görebileceğiniz gibi dış özel durumun işlendiğini önce akış kapatıldı ve dosya `test.txt` metni içeren `test1`, arabellek atılmış ve özel durum transfer olsa bile diske yazılan gösterir Dış özel durum işleyici denetler.

Unutmayın `try...with` yapıdır gelen ayrı bir yapı `try...finally` oluşturun. Bu nedenle, kodunuzun her ikisi de gerektiriyorsa bir `with` bloğu ve `finally` bloğu, aşağıdaki kod örneğinde olduğu gibi iki yapıları iç içe gerekir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

Hesaplama ifadeleri bağlamında sequence ifadeleri ve zaman uyumsuz iş akışları dahil olmak üzere **try... finally** ifadeleri, özel bir uygulama olabilir. Daha fazla bilgi için bkz: [hesaplama ifadeleri](../computation-expressions.md).


## <a name="see-also"></a>Ayrıca Bkz.
[Özel Durum İşleme](index.md)

[Özel durumlar: `try...with` ifade](the-try-with-expression.md)
