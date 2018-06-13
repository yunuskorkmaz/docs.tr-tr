---
title: Nesne İfadeleri (F#)
description: 'Ek kod ve yeni, oluşturmak için gerekli ek yükünü engellemek istediğinizde F # nesne ifadeleri kullanmayı türü adlı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: fed78e2be52838eedf55759b195696f1210a8a20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564397"
---
# <a name="object-expressions"></a>Nesne İfadeleri

Bir *nesne ifadesi* dinamik olarak oluşturulan, anonim nesne türü yeni bir örneğini oluşturan bir ifade bir varolan temel türü, arabirim veya arabirim kümesine dayalıdır.


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
Önceki sözdiziminde *typename* varolan bir sınıf veya arabirim türü temsil eder. *Tür parametreleri* isteğe bağlı genel tür parametreleri açıklar. *Bağımsız değişkenleri* Oluşturucu parametreleri gerektiren yalnızca sınıf türleri için kullanılır. *Üye tanımları* taban sınıf yöntemlerini, geçersiz kılmalar ya da bir taban sınıf veya arabirim soyut yöntemler uygulamaları.

Aşağıdaki örnek, birkaç farklı türde nesne ifadeleri gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a>Nesne ifadeleri kullanma
Türü adlı gerekli yeni bir oluşturmak için ek yükü ve ek kod engellemek istediğinizde nesne ifadeleri kullanın. Nesne ifadeleri bir programda oluşturulan türleri sayısını en aza indirmek için kullanırsanız, kod satırı sayısını azaltın ve türleri gereksiz artışı engelleyebilirsiniz. Yalnızca özel durumları işlemek için birçok türleri oluşturmak yerine, mevcut bir türle özelleştirir veya elinizdeki belirli çalışması için uygun bir uygulaması, bir arabirim sağlayan bir nesne ifadesi kullanabilirsiniz.


## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)
