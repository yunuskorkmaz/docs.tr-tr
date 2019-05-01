---
title: Birim Türü
description: Bilgi nasıl F# 'unit' türü genellikle burada bir değer gereklidir dili sözdizimi tarafından hiçbir değer gereken veya istediğiniz yerde tutmak için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: f1866ff12f36f4f8d3eaa1275551c42fc4ade216
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982533"
---
# <a name="unit-type"></a>Birim Türü

`unit` Türüdür; belirli bir değer devamsızlık gösteren bir türün `unit` türüne sahip başka bir değer yok veya gerekli olduğunda, bir yer tutucu olarak görev yapar yalnızca tek bir değer.

## <a name="syntax"></a>Sözdizimi

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Açıklamalar

Her F# ifadeyi değerlendirmek için bir değer gerekir. İlgi, değer türünde bir değer oluşturmaz ifadeler `unit` kullanılır. `unit` Türü benzer `void` C# ve C++ gibi dillerde türü.

`unit` Tek bir değer türüne sahip ve bu değer belirteci tarafından belirtilen `()`.

Değerini `unit` türü kullanılan genellikle F# programlama dili sözdizimi tarafından bir değer gerektiğinde, ancak hiçbir değer gerekli ya da istenen bir yerde tutmak için. Dönüş değeri bir örnek olabilir bir `printf` işlevi. Çünkü önemli eylemleri `printf` işlemi meydana işlevde harcanan, gerçek bir değer döndürmek işlev yok. Bu nedenle, dönüş değeri türünde `unit`.

Bazı yapıları beklediğiniz bir `unit` değeri. Örneğin, bir `do` bağlama veya en üst düzeyde bir modülün herhangi bir kod için değerlendirilecek beklenmektedir bir `unit` değeri. Derleyici bir uyarı bildirir, bir `do` bağlamanız veya kodunuz en üst düzeyde bir modülün bir sonuç üretir dışında `unit` , aşağıdaki örnekte gösterildiği gibi kullanılmayan değer.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Bu uyarı, işlevsel programlama özelliğidir; Diğer .NET programlama dillerinin görünmüyor. İşlevler tüm yan etkileri de yoktur tamamen işlevsel bir programda son dönüş değeri bir işlev çağrısı yalnızca sonucudur. Bu nedenle sonuç göz ardı edilir olduğunda, olası bir programlama hatası gereklidir. Ancak F# tamamen işlevsel değil programlama dili, işlevsel programlama stil mümkün olduğunca izlemek için yararlı olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Temel](primitive-types.md)
- [F# Dili Başvurusu](index.md)