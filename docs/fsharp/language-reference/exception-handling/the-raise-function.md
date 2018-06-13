---
title: 'Özel Durumlar: raise İşlevi (F#)'
description: "F # 'Yükselt' işlevi bir hata veya olağanüstü koşulu oluştu belirtmek için nasıl kullanıldığını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: bad18bfbccd738a12e16a0e026ade22e96d4cfcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564772"
---
# <a name="exceptions-the-raise-function"></a>Özel Durumlar: raise İşlevi

`raise` İşlevi bir hata veya olağanüstü koşulu oluştu belirtmek için kullanılır. Hata hakkında bilgi bir özel durum nesnesi yakalanır.


## <a name="syntax"></a>Sözdizimi

```fsharp
raise (expression)
```

## <a name="remarks"></a>Açıklamalar
`raise` İşlevi bir özel durum nesnesi oluşturur ve işlem geriye doğru izleme yığını başlatır. Diğer bir .NET dilinde olduğu gibi bu işlemin aynı nedenle davranış yığın unwinding işlem ortak dil çalışma zamanı tarafından (CLR) yönetilir. Yığın unwinding oluşturulan özel durum ile eşleşen bir özel durum işleyici için bir arama işlemidir. Geçerli aramayı başlatır `try...with` varsa ifade. Her desende `with` blok denetlenir, sırayla. Eşleşen bir özel durum işleyici bulunduğunda, özel durum işlenen olarak kabul edilir; Aksi takdirde, yığın unwound ve `with` çağrı zincirine yukarı blokları eşleşen bir işleyici bulunana kadar denetlenir. Tüm `finally` yığın unwinds olarak çağrı zincirine karşılaşılan blokları sırada da çalıştırılır.

`raise` Fonksiyonudur denk `throw` C# veya C++. Kullanım `reraise` aynı özel durum çağrı zincirine yukarı yaymak için bir catch işleyicisi.

Aşağıdaki kod örnekleri kullanımını göstermek `raise` bir özel durum oluşturmak için işlev.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise` İşlevi de kullanılabilir .NET özel durumlarını yükseltmek için aşağıdaki örnekte gösterildiği gibi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[Özel Durum İşleme](index.md)

[Özel Durum Türleri](exception-types.md)

[Özel durumlar: `try...with` ifade](the-try-with-expression.md)

[Özel durumlar: `try...finally` ifade](the-try-finally-expression.md)

[Özel durumlar: `failwith` işlevi](the-failwith-function.md)

[Özel durumlar: `invalidArg` işlevi](the-invalidArg-function.md)
