---
title: Arabirimler (F#)
description: "F # arabirimleri diğer sınıflar uygulayan ilgili üye kümesi nasıl belirteceğinizi öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a082459-17d4-45cf-9153-0b7550a154ec
ms.openlocfilehash: d7c95e5f5cc0bc6c7f6393af990427ac491c5b79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="interfaces"></a><span data-ttu-id="77a6d-104">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="77a6d-104">Interfaces</span></span>

<span data-ttu-id="77a6d-105">*Arabirimleri* diğer sınıflar uygulayan ilgili üye kümesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="77a6d-105">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="77a6d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77a6d-106">Syntax</span></span>

```fsharp
// Interface declaration:
[ attributes ]
type interface-name =
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

## <a name="remarks"></a><span data-ttu-id="77a6d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77a6d-107">Remarks</span></span>
<span data-ttu-id="77a6d-108">Hiçbir üye uygulanan dışında arabirim bildirimleri sınıf bildirimleri benzer.</span><span class="sxs-lookup"><span data-stu-id="77a6d-108">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="77a6d-109">Bunun yerine, tüm üyeleri anahtar sözcüğüyle belirtildiği gibi Özet, `abstract`.</span><span class="sxs-lookup"><span data-stu-id="77a6d-109">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="77a6d-110">Soyut yöntemler için bir yöntem gövdesi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="77a6d-110">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="77a6d-111">Ayrıca ayrı bir üye tanımı ile birlikte bir yöntem olarak ekleyerek bir varsayılan uygulama ancak sağlayabilir `default` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="77a6d-111">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="77a6d-112">Bunun yapılması, sanal bir yöntem diğer .NET dilleri temel sınıf oluşturmak için eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="77a6d-112">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="77a6d-113">Arabirimini uygulayan sınıflar sanal bir yöntem geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="77a6d-113">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="77a6d-114">İsteğe bağlı olarak, her yöntem parametresi normal F # sözdizimi kullanılarak bir ad verebilir:</span><span class="sxs-lookup"><span data-stu-id="77a6d-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="77a6d-115">Yukarıdaki içinde `ISprintable` örnek, `Print` yöntemi sahip tek bir parametre türü `string` adıyla `format`.</span><span class="sxs-lookup"><span data-stu-id="77a6d-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="77a6d-116">Arabirimlerini iki yolu vardır: object ifadelerini kullanarak ve sınıf türleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="77a6d-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="77a6d-117">Her iki durumda da sınıf türü ya da nesne deyim yöntem gövdeleri için arabiriminin Özet yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="77a6d-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="77a6d-118">Arabirimini uygulayan her türü için belirli uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="77a6d-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="77a6d-119">Bu nedenle, farklı türlerde arabirim yöntemleri birbirinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="77a6d-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="77a6d-120">Anahtar sözcükler `interface` ve `end`, başlangıç ve bitiş tanımının işaretlemek isteğe bağlı basit sözdizimini kullandığınızda.</span><span class="sxs-lookup"><span data-stu-id="77a6d-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="77a6d-121">Bu anahtar sözcükler kullanmayın türü bir sınıf veya arabirim kullandığınız yapıları çözümleyerek olup olmadığını anlamak derleyici çalışır.</span><span class="sxs-lookup"><span data-stu-id="77a6d-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="77a6d-122">Bir üye tanımlayın veya diğer sınıf söz dizimini kullanın, türü bir sınıf olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="77a6d-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="77a6d-123">Tüm arabirimler büyük harfle başlamak için stil kodlama .NET olduğu `I`.</span><span class="sxs-lookup"><span data-stu-id="77a6d-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>


## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="77a6d-124">Sınıf türleri kullanarak arabirimler uygulama</span><span class="sxs-lookup"><span data-stu-id="77a6d-124">Implementing Interfaces by Using Class Types</span></span>
<span data-ttu-id="77a6d-125">Kullanarak bir sınıf türünün bir veya daha fazla arabirimleri uygulayabilir `interface` anahtar sözcüğü, arabirimin adını ve `with` arabirim üye tanımları tarafından aşağıdaki kodda gösterildiği gibi anahtar sözcüğünü,.</span><span class="sxs-lookup"><span data-stu-id="77a6d-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="77a6d-126">Türetilen tüm sınıflar, bunları yeniden uygulamalı gerekmez. böylece arabirim uygulamaları devralınır.</span><span class="sxs-lookup"><span data-stu-id="77a6d-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>


## <a name="calling-interface-methods"></a><span data-ttu-id="77a6d-127">Arama Arabirim yöntemleri</span><span class="sxs-lookup"><span data-stu-id="77a6d-127">Calling Interface Methods</span></span>
<span data-ttu-id="77a6d-128">Arabirimini uygulayan türünde herhangi bir nesne üzerinden değil, yalnızca arabiriminden arabirim yöntemleri çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="77a6d-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="77a6d-129">Böylece, arabirim türüne yukarı çevrim kullanarak gerekebilir `:>` işleci veya `upcast` bu yöntemleri çağırmak için işleci.</span><span class="sxs-lookup"><span data-stu-id="77a6d-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="77a6d-130">Nesne türüne sahip olduğunda arabirim yöntemini çağırmak için `SomeClass`, aşağıdaki kodda gösterildiği gibi yukarı çevrim arabirim türü nesneye gerekir.</span><span class="sxs-lookup"><span data-stu-id="77a6d-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="77a6d-131">Alternatif bir yöntem bir nesne üzerinde bu upcasts bildirmektir ve aşağıdaki örnekteki gibi arabirim yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="77a6d-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="77a6d-132">Nesne ifadeleri kullanarak arabirimler uygulama</span><span class="sxs-lookup"><span data-stu-id="77a6d-132">Implementing Interfaces by Using Object Expressions</span></span>
<span data-ttu-id="77a6d-133">Nesne ifadeleri bir arabirim için kısa bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="77a6d-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="77a6d-134">Bunlar, adlandırılmış bir tür oluşturmak zorunda değildir ve yalnızca ek yöntemleri olmadan arabirim yöntemleri destekleyen bir nesne istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="77a6d-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="77a6d-135">Aşağıdaki kodda bir nesne ifadesi gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="77a6d-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a><span data-ttu-id="77a6d-136">Arabirim devralma</span><span class="sxs-lookup"><span data-stu-id="77a6d-136">Interface Inheritance</span></span>
<span data-ttu-id="77a6d-137">Bir veya daha fazla temel arabirimlerinden arabirimleri devralabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77a6d-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a><span data-ttu-id="77a6d-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77a6d-138">See Also</span></span>
[<span data-ttu-id="77a6d-139">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="77a6d-139">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="77a6d-140">Nesne ifadeleri</span><span class="sxs-lookup"><span data-stu-id="77a6d-140">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="77a6d-141">Sınıfları</span><span class="sxs-lookup"><span data-stu-id="77a6d-141">Classes</span></span>](classes.md)
