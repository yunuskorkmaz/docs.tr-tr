---
title: "Tür Kısaltmaları (F#)"
description: "Bir tür kodu okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için F # tür kısaltmaları hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 560af74f-935f-415c-af56-604cddb9da6b
ms.openlocfilehash: 235c0240fe89d203b9474dec2b3f91947f453cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
[F # dili başvurusu](index.md)

