---
title: Nesne İfadeleri
description: Nasıl kullanacağınızı öğrenin F# yeni, oluşturmak için gerekli tür adlı ek bir kod ve ek yükü önlemek istediğinizde nesne ifadeleri.
ms.date: 05/16/2016
ms.openlocfilehash: cb15983543fde2459c589b3de2554575d73db686
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613927"
---
# <a name="object-expressions"></a>Nesne İfadeleri

Bir *ifade nesne* dinamik olarak oluşturulmuş, anonim nesne türü yeni bir örneğini oluşturan bir ifade bir var olan temel tür, arabirim veya arabirimleri kümesi bağlı.

## <a name="syntax"></a>Sözdizimi

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *typename* var olan bir sınıf veya arabirim türü temsil eder. *Tür parametreleri* isteğe bağlı bir genel tür parametreleri açıklar. *Bağımsız değişkenleri* Oluşturucu parametresi gerektiren yalnızca sınıf türleri için kullanılır. *Üye tanımları* taban sınıf yöntemlerini geçersiz kılmalarına ya da soyut yöntemler bir temel sınıf veya arabirim uygulamaları.

Aşağıdaki örnek, birkaç farklı türde nesne ifadeleri gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a>Nesne ifadeleri kullanma

Nesne ifadeleri, ek bir kod ve tür adında gereken yeni, ek yükü önlemek istediğinizde kullanın. Nesne ifadeleri bir programında oluşturulan türleri sayısını en aza indirmek için kullanırsanız, kod satırı sayısını azaltın ve türleri gereksiz çoğalan engelle. Yalnızca özel durumları işlemek için birçok türleri oluşturmak yerine var olan bir türü özelleştirir veya bir arabirimin uygun uygulama eldeki özel durum sağlayan bir nesne ifadesi kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)