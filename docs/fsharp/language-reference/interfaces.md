---
title: Arabirimler (F#)
description: 'F # arabirimleri diğer sınıflar uygulayan ilgili üye kümesi nasıl belirteceğinizi öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 54ae8a2840ce26814be25f08c3ed02e12df6b7c0
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058907"
---
# <a name="interfaces"></a>Arabirimler

*Arabirimleri* diğer sınıflar uygulayan ilgili üye kümesi belirtin.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>Açıklamalar
Hiçbir üye uygulanan dışında arabirim bildirimleri sınıf bildirimleri benzer. Bunun yerine, tüm üyeleri anahtar sözcüğüyle belirtildiği gibi Özet, `abstract`. Soyut yöntemler için bir yöntem gövdesi sağlamaz. Ayrıca ayrı bir üye tanımı ile birlikte bir yöntem olarak ekleyerek bir varsayılan uygulama ancak sağlayabilir `default` anahtar sözcüğü. Bunun yapılması, sanal bir yöntem diğer .NET dilleri temel sınıf oluşturmak için eşdeğerdir. Arabirimini uygulayan sınıflar sanal bir yöntem geçersiz kılınabilir.

Arabirimleri için varsayılan erişilebilirlik olduğu `public`.

İsteğe bağlı olarak, her yöntem parametresi normal F # sözdizimi kullanılarak bir ad verebilir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

Yukarıdaki içinde `ISprintable` örnek, `Print` yöntemi sahip tek bir parametre türü `string` adıyla `format`.

Arabirimlerini iki yolu vardır: object ifadelerini kullanarak ve sınıf türleri kullanarak. Her iki durumda da sınıf türü ya da nesne deyim yöntem gövdeleri için arabiriminin Özet yöntemleri sağlar. Arabirimini uygulayan her türü için belirli uygulamalarıdır. Bu nedenle, farklı türlerde arabirim yöntemleri birbirinden farklı olabilir.

Anahtar sözcükler `interface` ve `end`, başlangıç ve bitiş tanımının işaretlemek isteğe bağlı basit sözdizimini kullandığınızda. Bu anahtar sözcükler kullanmayın türü bir sınıf veya arabirim kullandığınız yapıları çözümleyerek olup olmadığını anlamak derleyici çalışır. Bir üye tanımlayın veya diğer sınıf söz dizimini kullanın, türü bir sınıf olarak yorumlanır.

Tüm arabirimler büyük harfle başlamak için stil kodlama .NET olduğu `I`.


## <a name="implementing-interfaces-by-using-class-types"></a>Sınıf türleri kullanarak arabirimler uygulama
Kullanarak bir sınıf türünün bir veya daha fazla arabirimleri uygulayabilir `interface` anahtar sözcüğü, arabirimin adını ve `with` arabirim üye tanımları tarafından aşağıdaki kodda gösterildiği gibi anahtar sözcüğünü,.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Türetilen tüm sınıflar, bunları yeniden uygulamalı gerekmez. böylece arabirim uygulamaları devralınır.


## <a name="calling-interface-methods"></a>Arama Arabirim yöntemleri
Arabirimini uygulayan türünde herhangi bir nesne üzerinden değil, yalnızca arabiriminden arabirim yöntemleri çağrılamaz. Böylece, arabirim türüne yukarı çevrim kullanarak gerekebilir `:>` işleci veya `upcast` bu yöntemleri çağırmak için işleci.

Nesne türüne sahip olduğunda arabirim yöntemini çağırmak için `SomeClass`, aşağıdaki kodda gösterildiği gibi yukarı çevrim arabirim türü nesneye gerekir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Alternatif bir yöntem bir nesne üzerinde bu upcasts bildirmektir ve aşağıdaki örnekteki gibi arabirim yöntemini çağırır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a>Nesne ifadeleri kullanarak arabirimler uygulama
Nesne ifadeleri bir arabirim için kısa bir yol sağlar. Bunlar, adlandırılmış bir tür oluşturmak zorunda değildir ve yalnızca ek yöntemleri olmadan arabirim yöntemleri destekleyen bir nesne istediğinizde kullanışlıdır. Aşağıdaki kodda bir nesne ifadesi gösterilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a>Arabirim devralma
Bir veya daha fazla temel arabirimlerinden arabirimleri devralabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Nesne İfadeleri](object-expressions.md)

[Sınıflar](classes.md)
