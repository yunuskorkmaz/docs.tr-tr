---
title: 'Özel Durumlar: raise İşlevi'
description: Bilgi nasıl F# 'raise' işlevi, bir hata veya olağanüstü bir koşul oluştu belirtmek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 87773ead7773c62a325c7e7ff105c729e10dd69c
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610157"
---
# <a name="exceptions-the-raise-function"></a>Özel Durumlar: raise İşlevi

`raise` İşlevi, bir hata veya olağanüstü bir koşul oluştu belirtmek için kullanılır. Hata hakkındaki bilgileri, bir özel durum nesnesine yakalanır.

## <a name="syntax"></a>Sözdizimi

```fsharp
raise (expression)
```

## <a name="remarks"></a>Açıklamalar

`raise` İşlev bir özel durum nesnesi oluşturur ve bir yığın geriye doğru işlem başlatır. Diğer bir .NET dilinde olduğu gibi bu işlemin davranışını aynı olacak şekilde yığın geriye doğru işlem ortak dil çalışma (CLR) tarafından yönetilir. Yığın geriye doğru işlem oluşturulan özel durum ile eşleşen bir özel durum işleyici için bir aramadır. Geçerli aramayı başlatır `try...with` varsa ifade. Her desende `with` blok seçiliyse, sırasıyla. Eşleşen bir özel durum işleyici bulunduğunda, özel durumu işlenmiş olarak değerlendirilir. Aksi takdirde, yığın geriye doğru çözülür ve `with` çağrı zincirine'kurmak blokları eşleşen bir işleyici bulunana kadar denetlenir. Tüm `finally` gibi yığın geriye doğru alır ve çağrı zincirine karşılaşılan blokları sırayla da çalıştırılır.

`raise` İşlev, denk `throw` C# veya C++. Kullanım `reraise` aynı özel durum çağrı zincirine'kurmak yayılması bir catch işleyicisi.

Aşağıdaki kod örnekleri kullanımını gösteren `raise` işlev bir özel durum oluşturur.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise` İşlevi de kullanılabilir .NET özel durumları, yükseltmek için aşağıdaki örnekte gösterildiği gibi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel Durum Türleri](exception-types.md)
- [Özel durumlar: `try...with` İfadesi](the-try-with-expression.md)
- [Özel durumlar: `try...finally` İfadesi](the-try-finally-expression.md)
- [Özel durumlar: `failwith` İşlevi](the-failwith-function.md)
- [Özel durumlar: `invalidArg` İşlevi](the-invalidArg-function.md)