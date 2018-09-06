---
title: Nesne İfadeleri (F#)
description: 'Türü adlı ek bir kod ve yeni, oluşturmak için gereken ek yükü önlemek istediğinizde F # nesne ifadeleri kullanmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 1a971044d680d3bf5a6fff38affdaf001d5403b4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865468"
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
