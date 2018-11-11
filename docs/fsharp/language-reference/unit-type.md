---
title: Birim Türü (F#)
description: Nasıl F# 'unit' türü genellikle burada herhangi bir değer gerekli ya da istenen dili sözdizimi tarafından bir değer gereklidir yerde tutmak için kullanılan bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: c3dfa5f63c25a1e8abc0f75b905c129b311479af
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "44204662"
---
# <a name="unit-type"></a>Birim Türü

`unit` Türüdür; belirli bir değer devamsızlık gösteren bir türün `unit` türüne sahip başka bir değer yok veya gerekli olduğunda, bir yer tutucu olarak görev yapar yalnızca tek bir değer.

## <a name="syntax"></a>Sözdizimi

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Açıklamalar

Her F# ifadesi bir değer olarak değerlendirilmesi gerekir. İlgi, değer türünde bir değer oluşturmaz ifadeler `unit` kullanılır. `unit` Türü benzer `void` C# ve C++ gibi dillerde türü.

`unit` Tek bir değer türüne sahip ve bu değer belirteci tarafından belirtilen `()`.

Değerini `unit` türü genellikle kullanılan bir değer, dili sözdizimi tarafından gerekli olduğu durumlarda, ancak hiçbir değer gerekli ya da istenen bir yerde tutmak için programlama içinde F#. Dönüş değeri bir örnek olabilir bir `printf` işlevi. Çünkü önemli eylemleri `printf` işlemi meydana işlevde harcanan, gerçek bir değer döndürmek işlev yok. Bu nedenle, dönüş değeri türünde `unit`.

Bazı yapıları beklediğiniz bir `unit` değeri. Örneğin, bir `do` bağlama veya en üst düzeyde bir modülün herhangi bir kod için değerlendirilecek beklenmektedir bir `unit` değeri. Derleyici bir uyarı bildirir, bir `do` bağlamanız veya kodunuz en üst düzeyde bir modülün bir sonuç üretir dışında `unit` , aşağıdaki örnekte gösterildiği gibi kullanılmayan değer.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Bu uyarı, işlevsel programlama özelliğidir; Diğer .NET programlama dillerinin görünmüyor. İşlevler tüm yan etkileri de yoktur tamamen işlevsel bir programda son dönüş değeri bir işlev çağrısı yalnızca sonucudur. Bu nedenle sonuç göz ardı edilir olduğunda, olası bir programlama hatası gereklidir. F# tamamen işlevsel bir programlama dili olmamasına karşın, işlevsel programlama stil mümkün olduğunca izlemek için iyi bir uygulamadır.

## <a name="see-also"></a>Ayrıca bkz.

- [Temel](primitive-types.md)
- [F# Dili Başvurusu](index.md)
