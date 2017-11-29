---
title: "Özel Durumlar: raise İşlevi (F#)"
description: "F # 'Yükselt' işlevi bir hata veya olağanüstü koşulu oluştu belirtmek için nasıl kullanıldığını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b00da469-4789-4cdd-9f77-7a2e29f28637
ms.openlocfilehash: dc524a06d075b982a6aa1fd266769bfc7d883517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
[Özel durum işleme](index.md)

[Özel durum türleri](exception-types.md)

[Özel durumlar: `try...with` ifade](the-try-with-expression.md)

[Özel durumlar: `try...finally` ifade](the-try-finally-expression.md)

[Özel durumlar: `failwith` işlevi](the-failwith-function.md)

[Özel durumlar: `invalidArg` işlevi](the-invalidArg-function.md)
