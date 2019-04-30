---
title: Tür Kısaltmaları
description: Hakkında bilgi edinin F# bir tür, kodun okunmasını kolaylaştırmak için daha anlamlı bir ad vermek için kısaltmalar yazın.
ms.date: 05/16/2016
ms.openlocfilehash: 0deaef789367aad413e5a537bf7164034e1275c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683346"
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

Tür kısaltmaları .NET Framework MSIL kodu korunmaz. Bu nedenle, kullandığınızda bir F# derleme başka bir .NET Framework dilinden türü kısaltması için temel alınan tür adı kullanmanız gerekir.

Tür kısaltmaları ölçü birimi üzerinde de kullanılabilir. Daha fazla bilgi için [ölçü](units-of-measure.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)