---
title: 'Özel Durumlar: raise İşlevi'
description: F# ' Raise ' işlevinin bir hata veya sıra koşulunun oluştuğunu göstermek için nasıl kullanıldığını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630294"
---
# <a name="exceptions-the-raise-function"></a>Özel Durumlar: raise İşlevi

`raise` İşlevi, bir hata veya sıra koşulunun oluştuğunu göstermek için kullanılır. Hata hakkındaki bilgiler bir özel durum nesnesi içinde yakalanır.

## <a name="syntax"></a>Sözdizimi

```fsharp
raise (expression)
```

## <a name="remarks"></a>Açıklamalar

`raise` İşlevi bir özel durum nesnesi oluşturur ve bir yığın geri sarma işlemini başlatır. Yığın geriye doğru izleme işlemi, ortak dil çalışma zamanı (CLR) tarafından yönetilir, bu nedenle bu işlemin davranışı diğer herhangi bir .NET dilinde olduğu gibi aynıdır. Yığın geri sarma işlemi, oluşturulan özel durumla eşleşen bir özel durum işleyicisi aramasından oluşur. Arama, varsa geçerli `try...with` ifadede başlar. `with` Bloktaki her bir düzen sırasıyla denetlenir. Eşleşen bir özel durum işleyicisi bulunduğunda, özel durum işlenmiş olarak kabul edilir; Aksi takdirde, yığın engellenir ve `with` blok bir işleyici bulunana kadar çağrı zinciri denetlenir. Çağrı `finally` zincirinde karşılaşılan tüm bloklar yığın olarak yığın olarak da yürütülür.

İşlevi veya C++' de ' C# nin `throw` eşdeğeridir. `raise` Aynı `reraise` özel durumu çağrı zincirine yaymak için bir catch işleyicisinde kullanın.

Aşağıdaki kod örnekleri, bir özel durum oluşturmak için `raise` işlevinin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise` İşlev, aşağıdaki örnekte gösterildiği gibi .NET özel durumlarını yükseltmek için de kullanılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel Durum Türleri](exception-types.md)
- [Özel Durumlar: `try...with` İfade](the-try-with-expression.md)
- [Özel Durumlar: `try...finally` İfade](the-try-finally-expression.md)
- [Özel Durumlar: `failwith` İşlevi](the-failwith-function.md)
- [Özel Durumlar: `invalidArg` İşlevi](the-invalidArg-function.md)
