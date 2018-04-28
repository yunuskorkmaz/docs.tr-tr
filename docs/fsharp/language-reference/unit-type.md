---
title: Birim Türü (F#)
description: "Nasıl F # 'birimi' türü genellikle herhangi bir değer gerekli ya da istenen burada bir değer dili sözdizimi tarafından gerekli yer tutmak için kullanılan öğrenin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1a8c8f74e31c5426a9fb6a7143e9d2ac9a7104c0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="unit-type"></a>Birim Türü

`unit` Türüdür belirli bir değere; olmadığını gösteren bir tür `unit` türüne sahip başka bir değer yok veya gerekli olduğunda bir yer tutucu olarak davranan yalnızca tek bir değer.


## <a name="syntax"></a>Sözdizimi

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Açıklamalar
Her F # ifadesi bir değerde hesaplanmalıdır. İlgi türü değeri olan bir değer oluşturmaz ifadeler için `unit` kullanılır. `unit` Türü benzer `void` C# ve C++ gibi dillerde türü.

`unit` Türü tek bir değer içeriyor ve bu değeri belirtecin tarafından gösterilen `()`.

Değeri `unit` türü genellikle kullanılan F bir değer dili sözdizimi tarafından gerektiğinde, ancak hiçbir değer gerekli ya da istenen yer tutacak programlama # '. Bir örnek dönüş değeri olabilir bir `printf` işlevi. Çünkü önemli eylemleri `printf` işlemi ortaya işlevinde Gerçek bir değer döndürüleceğini işlevi yok. Bu nedenle, dönüş değeri türünde `unit`.

Bazı yapıları beklediğiniz bir `unit` değeri. Örneğin, bir `do` bağlama veya en üst düzeyinde bir modülün herhangi bir kod için değerlendirilecek beklenmektedir bir `unit` değeri. Derleyici bir uyarı bildirir, bir `do` bağlama veya kod en üst düzeyinde bir modülün bir sonuç üretir dışında `unit` , aşağıdaki örnekte gösterildiği gibi kullanılmaz değeri.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Bu uyarı, işlevsel programlama özelliğidir; Diğer .NET programlama dilleri görünmez. İşlevler herhangi yan etkileri olmayan tamamen işlevsel bir programda son dönen değer işlev çağrısı yalnızca sonucudur. Sonuç göz ardı edilir, bu nedenle, bu olası bir programlama hatası değildir. F # tamamen işlevsel bir programlama dili olmamasına rağmen işlevsel programlama stili mümkün olduğunca izlemek için iyi bir uygulamadır.

## <a name="see-also"></a>Ayrıca Bkz.
[İlkel](primitive-types.md)

[F# Dili Başvurusu](index.md)
