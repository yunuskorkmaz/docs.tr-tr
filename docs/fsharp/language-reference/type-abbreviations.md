---
title: Tür Kısaltmaları
description: Kodun daha F# kolay okunmasını sağlamak için türe daha anlamlı bir ad vermek üzere tür kısaltmaları hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630208"
---
# <a name="type-abbreviations"></a>Tür Kısaltmaları

*Tür kısaltması* , bir tür için diğer ad veya alternatif addır.

## <a name="syntax"></a>Sözdizimi

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Açıklamalar

Kodun daha kolay okunmasını sağlamak için tür kısaltmalarını, bir türe daha anlamlı bir ad vermek için kullanabilirsiniz. Ayrıca, yazmak üzere çok daha fazla olan bir tür için kullanımı kolay bir ad oluşturmak üzere bunları da kullanabilirsiniz. Ek olarak, türü kullanan tüm kodları değiştirmeden temel bir türün değiştirilmesini kolaylaştırmak için tür kısaltmalarının de kullanabilirsiniz. Aşağıda basit bir tür kısaltması verilmiştir.

Tür kısaltmalarının erişilebilirliği varsayılan olarak `public`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Tür kısaltmaları, aşağıdaki kodda olduğu gibi genel parametreleri içerebilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

Önceki kodda, `Transform` herhangi bir türde tek bir bağımsız değişken alan ve aynı türde tek bir değer döndüren bir işlevi temsil eden bir tür kısaltmadır.

Tür kısaltmaları .NET Framework MSIL kodunda korunmaz. Bu nedenle, başka bir .NET Framework F# dilinden bir derlemeyi kullandığınızda, bir tür kısaltması için temel alınan tür adını kullanmanız gerekir.

Tür kısaltmaları, ölçü birimleri üzerinde de kullanılabilir. Daha fazla bilgi için bkz. [Ölçü birimleri](units-of-measure.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
