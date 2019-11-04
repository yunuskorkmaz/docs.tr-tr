---
title: Birim Türü
description: F# ' Unit ' türünün, hiçbir değer gerekmediği veya istenmiyorsa dil söz konusu olduğunda bir değerin gerekli olduğu yeri tutmak için genellikle nasıl kullanıldığını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: a5960fb05af50486a78345d10a5ad913e65729e3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424026"
---
# <a name="unit-type"></a>Birim Türü

`unit` türü, belirli bir değerin yokluğunu gösteren bir türdür; `unit` türü, başka bir değer yoksa veya gerekli olmadığında yer tutucu olarak davranan yalnızca tek bir değere sahiptir.

## <a name="syntax"></a>Sözdizimi

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Açıklamalar

Her F# ifade bir değer olarak değerlendirilmelidir. İlgi çekici bir değer üretmeyen ifadeler için `unit` türündeki değer kullanılır. `unit` türü, ve C# C++gibi dillerde `void` türüne benzer.

`unit` türünün tek bir değeri vardır ve bu değer belirteç `()`tarafından belirtilir.

`unit` türünün değeri, genellikle bir değerin dil sözdizimi için F# gerekli olduğu yeri tutmak için programlama sırasında kullanılır, ancak hiçbir değer gerekli veya istenmez. Örnek bir `printf` işlevinin dönüş değeri olabilir. `printf` işleminin önemli eylemleri işlevde gerçekleştiğinden, işlevin gerçek bir değer döndürmesi gerekmez. Bu nedenle, dönüş değeri `unit`türündedir.

Bazı yapılar bir `unit` değeri bekler. Örneğin, bir modülün en üst düzeyindeki bir `do` bağlama veya herhangi bir kod `unit` bir değere değerlendirmesi beklenir. Bir modülün en üst düzeyindeki bir `do` bağlama veya kod, aşağıdaki örnekte gösterildiği gibi kullanılmayan `unit` değerinden başka bir sonuç üretirse, derleyici bir uyarı bildirir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Bu uyarı, işlevsel programlama 'nin bir özelliğidir; diğer .NET programlama dillerinde görünmez. Tamamen işlevsel bir programda, işlevleri yan etkileri olmayan, son dönüş değeri bir işlev çağrısının tek sonucudur. Bu nedenle, sonuç yoksayılırsa, olası bir programlama hatasıdır. Tamamen F# işlevsel programlama dili olmasa da, mümkün olan her durumda işlevsel programlama stilini izlemek iyi bir uygulamadır.

## <a name="see-also"></a>Ayrıca bkz.

- [Eleman](basic-types.md)
- [F# Dili Başvurusu](index.md)
