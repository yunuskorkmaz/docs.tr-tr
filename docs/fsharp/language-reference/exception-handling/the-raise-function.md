---
title: 'Özel Durumlar: raise İşlevi'
description: Bilgi nasıl F# 'raise' işlevi, bir hata veya olağanüstü bir koşul oluştu belirtmek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 9e2515ad7b85c1025bc3aa0aa2a6929a8d35436d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641960"
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
- [Özel Durumlar: `try...with` İfadesi](the-try-with-expression.md)
- [Özel Durumlar: `try...finally` İfadesi](the-try-finally-expression.md)
- [Özel Durumlar: `failwith` İşlevi](the-failwith-function.md)
- [Özel Durumlar: `invalidArg` İşlevi](the-invalidArg-function.md)
