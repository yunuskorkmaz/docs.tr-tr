---
title: Tür Kısaltmaları (F#)
description: 'Bir tür, kodun okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için F # tür kısaltmaları hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 259cd6c84e22fc7c98e08255d3e0ded5b87af352
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "48842431"
---
# <a name="type-abbreviations"></a>Tür Kısaltmaları

A *türü kısaltması* bir diğer ad ya da bir tür için diğer ad.

## <a name="syntax"></a>Sözdizimi

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Açıklamalar

Tür kısaltmaları bir tür, kodun okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için kullanabilirsiniz. Ayrıca bunları aksi yazılmasına yarar yavaşlatan bir tür için kullanımı kolay bir ad oluşturmak için kullanabilirsiniz. Ayrıca, tür kısaltmaları türünü kullanan tüm kodunda değişiklik yapmadan bir temel türü değiştirme daha kolay hale getirmek için kullanabilirsiniz. Bir basit türü kısaltması verilmiştir.

Tür kısaltmaları erişilebilirliğini varsayılanları `public`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Tür kısaltmaları, aşağıdaki kodda gösterildiği gibi genel parametreler ekleyebilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

Önceki kodda, `Transform` herhangi bir türde tek bir bağımsız değişken alan bir işlev temsil eden bir tür kısaltması olduğundan ve aynı türde tek bir değer döndürür.

Tür kısaltmaları .NET Framework MSIL kodu korunmaz. Bu nedenle, bir F # derleme başka bir .NET Framework dilden kullandığınızda, temel alınan tür adı için bir tür kısaltması kullanmanız gerekir.

Tür kısaltmaları ölçü birimi üzerinde de kullanılabilir. Daha fazla bilgi için [ölçü](units-of-measure.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
