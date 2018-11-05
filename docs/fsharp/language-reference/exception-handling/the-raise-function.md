---
title: 'Özel Durumlar: raise İşlevi (F#)'
description: "F # 'raise' işlevi bir hata veya olağanüstü bir koşul oluştu belirtmek için nasıl kullanıldığını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 537d274659d29404380bfdd56310ac267372bb98
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43778265"
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
- [Özel durumlar: `try...with` ifadesi](the-try-with-expression.md)
- [Özel durumlar: `try...finally` ifadesi](the-try-finally-expression.md)
- [Özel durumlar: `failwith` işlevi](the-failwith-function.md)
- [Özel durumlar: `invalidArg` işlevi](the-invalidArg-function.md)
