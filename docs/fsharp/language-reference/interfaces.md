---
title: Arabirimler
description: Arabirimlerin diğer F# sınıfların uygulayan ilgili üye kümelerini nasıl belirttireceğinizi öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 8f054a668ad0fbc2453a45883e8052471280eca3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627653"
---
# <a name="interfaces"></a>Arabirimler

*Arabirimler* , diğer sınıfların uygulayan ilgili üye kümelerini belirler.

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

Arabirim bildirimleri, hiçbir üye uygulanmamalıdır hariç sınıf bildirimlerine benzer. Bunun yerine, tüm Üyeler anahtar sözcüğüyle `abstract`gösterildiği gibi soyuttur. Soyut yöntemler için bir yöntem gövdesi sağlamazsanız. Ancak, `default` anahtar sözcükle birlikte bir yöntem olarak üyenin ayrı bir tanımını da ekleyerek varsayılan bir uygulama sağlayabilirsiniz. Bunun yapılması, diğer .NET dillerinin temel sınıfında bir sanal yöntem oluşturmaya eşdeğerdir. Bu tür bir sanal yöntem, arabirimini uygulayan sınıflarda geçersiz kılınabilir.

Arabirimler için varsayılan erişilebilirlik `public`.

İsteğe bağlı olarak, her yöntem parametresine normal F# sözdizimi kullanarak bir ad verebilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

Yukarıdaki `ISprintable` örnekte `Print` , yönteminin adında `string` tek`format`bir parametresi vardır.

Arabirim uygulamak için iki yol vardır: nesne ifadelerini kullanarak ve sınıf türlerini kullanarak. Her iki durumda da, sınıf türü veya nesne ifadesi, arabirimin soyut yöntemleri için yöntem gövdeleri sağlar. Uygulamalar, arabirimini uygulayan her türe özeldir. Bu nedenle, farklı türlerde arabirim yöntemleri birbirinden farklı olabilir.

Basit sözdizimi `interface` kullandığınızda `end`, tanımın başlangıcını ve bitişini işaretleyen anahtar sözcükler ve, isteğe bağlıdır. Bu anahtar sözcükleri kullanmıyorsanız, derleyici, kullandığınız yapıları çözümleyerek türün bir sınıf mı yoksa bir arabirim mi olduğunu çıkarmayın. Bir üye tanımlayabilir veya diğer sınıf sözdizimini kullanırsanız, tür bir sınıf olarak yorumlanır.

.NET kodlama stili, tüm arabirimlerin sermaye `I`olarak başlamadır.

## <a name="implementing-interfaces-by-using-class-types"></a>Sınıf türlerini kullanarak arabirimleri uygulama

Aşağıdaki kodda gösterildiği gibi `interface` anahtar sözcüğünü, arabirimin adını `with` ve anahtar sözcüğünü kullanarak bir sınıf türünde bir veya daha fazla arabirim uygulayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Arabirim uygulamaları devralınır, bu nedenle türetilen sınıfların bunları yeniden uygulaması gerekmez.

## <a name="calling-interface-methods"></a>Arabirim yöntemlerini çağırma

Arabirim yöntemleri, arabirimi uygulayan türdeki herhangi bir nesne yerine yalnızca arabirim üzerinden çağrılabilir. Bu nedenle, bu yöntemleri çağırmak için `:>` işlecini `upcast` veya işlecini kullanarak arabirim türüne yukarı atama yapmanız gerekebilir.

Türünde `SomeClass`bir nesneniz olduğunda arabirim yöntemini çağırmak için, aşağıdaki kodda gösterildiği gibi, nesneyi arabirim türüne yukarı atamalısınız.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Alternatif olarak, aşağıdaki örnekte olduğu gibi, ve arabirim yöntemini çağıran nesne üzerinde bir yöntemi bildirmenin bir alternatifi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>Nesne Ifadeleri kullanarak arabirimleri uygulama

Nesne ifadeleri, arabirim uygulamak için kısa bir yol sağlar. Adlandırılmış bir tür oluşturmanız gerekmeden ve yalnızca arabirim yöntemlerini destekleyen bir nesne istediğinizde, ek yöntemler olmadan bu yöntemler faydalıdır. Bir nesne ifadesi aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>Arabirim devralma

Arabirimler, bir veya daha fazla taban arabiriminden devralınabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Nesne İfadeleri](object-expressions.md)
- [Sınıflar](classes.md)
