---
title: Arabirimler
description: 'F # arabirimlerinin, diğer sınıfların uygulayan ilgili üye kümelerini nasıl belirttireceğinizi öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 36272b52fcff83e8e8a54ccc4e6ecd1252a91819
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558133"
---
# <a name="interfaces"></a>Arabirimler

*Arabirimler* , diğer sınıfların uygulayan ilgili üye kümelerini belirler.

## <a name="syntax"></a>Syntax

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

Arabirim bildirimleri, hiçbir üye uygulanmamalıdır hariç sınıf bildirimlerine benzer. Bunun yerine, tüm Üyeler anahtar sözcüğüyle gösterildiği gibi soyuttur `abstract` . Soyut yöntemler için bir yöntem gövdesi sağlamazsanız. Ancak, anahtar sözcükle birlikte bir yöntem olarak üyenin ayrı bir tanımını da ekleyerek varsayılan bir uygulama sağlayabilirsiniz `default` . Bunun yapılması, diğer .NET dillerinin temel sınıfında bir sanal yöntem oluşturmaya eşdeğerdir. Bu tür bir sanal yöntem, arabirimini uygulayan sınıflarda geçersiz kılınabilir.

Arabirimler için varsayılan erişilebilirlik `public` .

İsteğe bağlı olarak, her yöntem parametresine normal F # söz dizimini kullanarak bir ad verebilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

Yukarıdaki `ISprintable` örnekte, `Print` yönteminin adında tek bir parametresi vardır `string` `format` .

Arabirim uygulamak için iki yol vardır: nesne ifadelerini kullanarak ve sınıf türlerini kullanarak. Her iki durumda da, sınıf türü veya nesne ifadesi, arabirimin soyut yöntemleri için yöntem gövdeleri sağlar. Uygulamalar, arabirimini uygulayan her türe özeldir. Bu nedenle, farklı türlerde arabirim yöntemleri birbirinden farklı olabilir.

`interface` `end` Basit sözdizimi kullandığınızda, tanımın başlangıcını ve bitişini işaretleyen anahtar sözcükler ve, isteğe bağlıdır. Bu anahtar sözcükleri kullanmıyorsanız, derleyici, kullandığınız yapıları çözümleyerek türün bir sınıf mı yoksa bir arabirim mi olduğunu çıkarmayın. Bir üye tanımlayabilir veya diğer sınıf sözdizimini kullanırsanız, tür bir sınıf olarak yorumlanır.

.NET kodlama stili, tüm arabirimlerin sermaye olarak başlamadır `I` .

Birden çok parametreyi iki şekilde belirtebilirsiniz: F # stili ve. NET stili. Her ikisi de .NET tüketicileriyle aynı şekilde derlenir, ancak f # stili f # çağıranlarını F # stili parametre uygulaması ve ile kullanmak için zorlayacaktır. NET stili, F # çağıranlarını tupled bağımsız değişken uygulaması kullanacak şekilde zorlayacaktır.

```fsharp
type INumeric1 =
    abstract Add: x: int -> y: int -> int

type INumeric2 =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a>Sınıf türlerini kullanarak arabirimleri uygulama

`interface`Aşağıdaki kodda gösterildiği gibi anahtar sözcüğünü, arabirimin adını ve anahtar sözcüğünü kullanarak bir sınıf türünde bir veya daha fazla arabirim uygulayabilirsiniz `with` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Arabirim uygulamaları devralınır, bu nedenle türetilen sınıfların bunları yeniden uygulaması gerekmez.

## <a name="calling-interface-methods"></a>Arabirim yöntemlerini çağırma

Arabirim yöntemleri, arabirimi uygulayan türdeki herhangi bir nesne yerine yalnızca arabirim üzerinden çağrılabilir. Bu nedenle, `:>` `upcast` Bu yöntemleri çağırmak için işlecini veya işlecini kullanarak arabirim türüne yukarı atama yapmanız gerekebilir.

Türünde bir nesneniz olduğunda arabirim yöntemini çağırmak için `SomeClass` , aşağıdaki kodda gösterildiği gibi, nesneyi arabirim türüne yukarı atamalısınız.

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

- [F # dil başvurusu](index.md)
- [Nesne İfadeleri](object-expressions.md)
- [Sınıflar](classes.md)
