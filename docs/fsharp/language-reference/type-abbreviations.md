---
title: Tür Kısaltmaları (F#)
description: 'Bir tür kodu okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için F # tür kısaltmaları hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: cd0b2365aecc5d5b73df95a4b94ae4dd8327446d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="type-abbreviations"></a>Tür Kısaltmaları

A *türü kısaltması* bir diğer ad veya bir tür için diğer ad.

## <a name="syntax"></a>Sözdizimi

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a>Açıklamalar
Tür kısaltmaları türü kodu okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için kullanabilirsiniz. Ayrıca bunları aksi yazamadı sıkıcı bir tür için kullanımı kolay bir ad oluşturmak için kullanabilirsiniz. Ayrıca, temel alınan tür türü kullanan tüm kodu değiştirmeden değiştirmek kolaylaştırmak için tür kısaltmaları kullanabilirsiniz. Bir basit tür kısaltması verilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Tür kısaltmaları aşağıdaki kodu olduğu gibi genel parametreler içerebilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

Önceki kod `Transform` herhangi bir türde tek bir bağımsız değişken bir işlevi temsil eden bir tür kısaltması olduğu ve aynı türde tek bir değer döndürür.

Tür kısaltmaları .NET Framework MSIL kodda korunmaz. Bu nedenle, F # bütünleştirilmiş başka bir .NET Framework dilden kullandığınızda, bir tür kısaltması için temel alınan tür adını kullanmanız gerekir.

Tür kısaltmaları ölçü üzerinde de kullanılabilir. Daha fazla bilgi için bkz: [ölçü](units-of-measure.md).


## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

