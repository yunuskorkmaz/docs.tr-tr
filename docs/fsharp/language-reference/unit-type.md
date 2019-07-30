---
title: Birim Türü
description: F# ' Unit ' türünün, hiçbir değer gerekmediği veya istenmiyorsa dil söz konusu olduğunda bir değerin gerekli olduğu yeri tutmak için genellikle nasıl kullanıldığını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 4e586702324565b8dcd4f6c7e11a0e1754f89c58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630166"
---
# <a name="unit-type"></a>Birim Türü

Tür, belirli bir değerin yokluğunu gösteren bir türdür `unit` ; tür, başka bir değer yoksa veya gerektiğinde yer tutucu görevi gören tek bir değere sahiptir. `unit`

## <a name="syntax"></a>Sözdizimi

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Açıklamalar

Her F# ifade bir değer olarak değerlendirilmelidir. İlgilendiğiniz bir değer üretmeyen ifadeler için, türünün `unit` değeri kullanılır. Tür, `void` ve C++gibi C# dillerdeki türe benzer. `unit`

Türün tek bir değeri vardır ve bu değer belirteç `()`tarafından belirtilir. `unit`

`unit` Türün değeri, genellikle bir değerin dil sözdizimi için F# gerekli olduğu yeri tutmak için programlama sırasında kullanılır, ancak hiçbir değer gerekli veya istenmez. Bir `printf` işlevin dönüş değeri bir örnek olabilir. `printf` İşlemin önemli eylemleri işlevde gerçekleştiğinden, işlevin gerçek bir değer döndürmesi gerekmez. Bu nedenle, dönüş değeri türündedir `unit`.

Bazı yapılar bir `unit` değer bekler. Örneğin, `do` bir modülün en üst düzeyindeki bir bağlamanın veya kodun bir `unit` değer değerlendirmesi beklenir. Bir modülün en üst düzeyindeki bir `do` bağlama veya kod, aşağıdaki örnekte gösterildiği gibi kullanılmayan `unit` değerden farklı bir sonuç üretirse, derleyici bir uyarı bildirir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Bu uyarı, işlevsel programlama 'nin bir özelliğidir; diğer .NET programlama dillerinde görünmez. Tamamen işlevsel bir programda, işlevleri yan etkileri olmayan, son dönüş değeri bir işlev çağrısının tek sonucudur. Bu nedenle, sonuç yoksayılırsa, olası bir programlama hatasıdır. Tamamen F# işlevsel programlama dili olmasa da, mümkün olan her durumda işlevsel programlama stilini izlemek iyi bir uygulamadır.

## <a name="see-also"></a>Ayrıca bkz.

- [Eleman](primitive-types.md)
- [F# Dili Başvurusu](index.md)
