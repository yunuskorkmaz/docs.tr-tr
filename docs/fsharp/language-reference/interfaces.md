---
title: Arabirimler (F#)
description: 'F # arabirimleri diğer sınıfları uygulayan ilgili üyelerinin kümeleri nasıl belirteceğinizi öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 6d7f8ee9ea17d2294933f88577c30a96975ae5d4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "47231446"
---
# <a name="interfaces"></a>Arabirimler

*Arabirimleri* diğer sınıfları uygulayan ilgili üyeleri kümesi belirtin.

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

Hiç üye uygulanan dışında sınıf bildirimleri arabirimi bildirimleri benzer. Bunun yerine, tüm üyeleri anahtar sözcüğü tarafından belirtildiği şekilde soyuttur `abstract`. Soyut metotlar için bir yöntem gövdesi sağlamaz. Ancak, ayrı bir üye tanımı ile birlikte bir iletişim yöntemi olarak da dahil olmak üzere tarafından varsayılan bir uygulama sağlayabilirsiniz `default` anahtar sözcüğü. Bunun yapılması, diğer .NET dillerinde taban sınıfında sanal bir yöntem oluşturmaya eşdeğerdir. Arabirimini uygulayan sınıflar sanal bir yöntem geçersiz kılınabilir.

Arabirimler için varsayılan erişilebilirlik, `public`.

İsteğe bağlı olarak, her bir yöntem parametresi normal F # söz dizimini kullanarak bir ad verebilirsiniz:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

Yukarıdaki içinde `ISprintable` örnek, `Print` yöntemi türünde tek bir parametreye sahip `string` adıyla `format`.

Arayüzleri uygulamak için iki yolu vardır: Nesne ifadeleri kullanarak ve sınıf türleri kullanarak. Her iki durumda da sınıfı türü veya nesne ifadesi metot gövdeleri arabirimi soyut yöntemlerini sağlar. Arabirimini uygulayan her tür için belirli uygulamalarıdır. Bu nedenle, farklı türlerde arabirim yöntemleri birbirinden farklı olabilir.

Anahtar sözcükler `interface` ve `end`, başlangıç ve bitiş tanımının işaretlemek, isteğe bağlı basit sözdizimi kullandığınızda. Bu anahtar sözcükler kullanmazsanız derleyici türü bir sınıf veya arabirim kullandığınız yapılarını analiz ederek olup olmadığını çıkarsamak çalışır. Bir üye veya diğer sınıfı sözdizimi kullanıyorsanız, türü bir sınıf olarak yorumlanır.

Tüm arabirimleri büyük harfle başlamak için kodlama stili .NET olan `I`.

## <a name="implementing-interfaces-by-using-class-types"></a>Sınıf türleri kullanarak arabirimleri uygulama

Kullanarak bir sınıf türünde bir veya daha fazla arabirim uygulayabilir `interface` anahtar sözcüğü, arabirimin adını ve `with` arabirimi tarafından üye tanımları, aşağıdaki kodda gösterildiği gibi anahtar sözcüğü.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Tüm türetilmiş sınıfları, bunları yeniden uygulayın gerekmez. Bu nedenle, arabirim uygulamalarına devralınır.

## <a name="calling-interface-methods"></a>Arabirim yöntemleri çağırma

Arabirim yöntemleri arabirimi uygulayan türün herhangi bir nesne üzerinden değil, yalnızca arabiriminden çağrılabilir. Bu nedenle, arabirim türüne yukarı çevrim kullanarak gerekebilir `:>` işleci veya `upcast` işleci bu yöntemleri çağırmak için.

Bir nesne türü olduğunda arabirim yöntemini çağırmak için `SomeClass`, aşağıdaki kodda gösterildiği gibi yukarı çevrim nesnesine bir arabirim türü olmalıdır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Alternatif bu upcasts nesne üzerinde bir yöntemi bildirmek için ve aşağıdaki örnekte olduğu gibi arabirim yöntemini çağırır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>Nesne ifadeleri kullanarak arabirimleri uygulama

Nesne ifadeleri, bir arabirim uygulamak için kısa bir yol sağlar. Bunlar, adlandırılmış bir tür oluşturmak zorunda değilsiniz ve ek yöntemleri olmadan arabirim yöntemleri destekleyen bir nesne yalnızca istediğinizde kullanışlıdır. Bir nesne ifadesi, aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>Devralma arabirimi

Arabirimleri, bir veya daha fazla temel Ara birimden devralınabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Nesne İfadeleri](object-expressions.md)
- [Sınıflar](classes.md)
