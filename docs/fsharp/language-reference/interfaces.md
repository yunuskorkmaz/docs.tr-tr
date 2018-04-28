---
title: Arabirimler (F#)
description: 'F # arabirimleri diğer sınıflar uygulayan ilgili üye kümesi nasıl belirteceğinizi öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: fa299a7e37d4e1e3800a02bf5a77831db9146daf
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="interfaces"></a><span data-ttu-id="3f829-103">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="3f829-103">Interfaces</span></span>

<span data-ttu-id="3f829-104">*Arabirimleri* diğer sınıflar uygulayan ilgili üye kümesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="3f829-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="3f829-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f829-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="3f829-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f829-106">Remarks</span></span>
<span data-ttu-id="3f829-107">Hiçbir üye uygulanan dışında arabirim bildirimleri sınıf bildirimleri benzer.</span><span class="sxs-lookup"><span data-stu-id="3f829-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="3f829-108">Bunun yerine, tüm üyeleri anahtar sözcüğüyle belirtildiği gibi Özet, `abstract`.</span><span class="sxs-lookup"><span data-stu-id="3f829-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="3f829-109">Soyut yöntemler için bir yöntem gövdesi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="3f829-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="3f829-110">Ayrıca ayrı bir üye tanımı ile birlikte bir yöntem olarak ekleyerek bir varsayılan uygulama ancak sağlayabilir `default` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="3f829-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="3f829-111">Bunun yapılması, sanal bir yöntem diğer .NET dilleri temel sınıf oluşturmak için eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="3f829-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="3f829-112">Arabirimini uygulayan sınıflar sanal bir yöntem geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="3f829-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="3f829-113">İsteğe bağlı olarak, her yöntem parametresi normal F # sözdizimi kullanılarak bir ad verebilir:</span><span class="sxs-lookup"><span data-stu-id="3f829-113">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="3f829-114">Yukarıdaki içinde `ISprintable` örnek, `Print` yöntemi sahip tek bir parametre türü `string` adıyla `format`.</span><span class="sxs-lookup"><span data-stu-id="3f829-114">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="3f829-115">Arabirimlerini iki yolu vardır: object ifadelerini kullanarak ve sınıf türleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3f829-115">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="3f829-116">Her iki durumda da sınıf türü ya da nesne deyim yöntem gövdeleri için arabiriminin Özet yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f829-116">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="3f829-117">Arabirimini uygulayan her türü için belirli uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="3f829-117">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="3f829-118">Bu nedenle, farklı türlerde arabirim yöntemleri birbirinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f829-118">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="3f829-119">Anahtar sözcükler `interface` ve `end`, başlangıç ve bitiş tanımının işaretlemek isteğe bağlı basit sözdizimini kullandığınızda.</span><span class="sxs-lookup"><span data-stu-id="3f829-119">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="3f829-120">Bu anahtar sözcükler kullanmayın türü bir sınıf veya arabirim kullandığınız yapıları çözümleyerek olup olmadığını anlamak derleyici çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f829-120">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="3f829-121">Bir üye tanımlayın veya diğer sınıf söz dizimini kullanın, türü bir sınıf olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="3f829-121">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="3f829-122">Tüm arabirimler büyük harfle başlamak için stil kodlama .NET olduğu `I`.</span><span class="sxs-lookup"><span data-stu-id="3f829-122">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>


## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="3f829-123">Sınıf türleri kullanarak arabirimler uygulama</span><span class="sxs-lookup"><span data-stu-id="3f829-123">Implementing Interfaces by Using Class Types</span></span>
<span data-ttu-id="3f829-124">Kullanarak bir sınıf türünün bir veya daha fazla arabirimleri uygulayabilir `interface` anahtar sözcüğü, arabirimin adını ve `with` arabirim üye tanımları tarafından aşağıdaki kodda gösterildiği gibi anahtar sözcüğünü,.</span><span class="sxs-lookup"><span data-stu-id="3f829-124">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="3f829-125">Türetilen tüm sınıflar, bunları yeniden uygulamalı gerekmez. böylece arabirim uygulamaları devralınır.</span><span class="sxs-lookup"><span data-stu-id="3f829-125">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>


## <a name="calling-interface-methods"></a><span data-ttu-id="3f829-126">Arama Arabirim yöntemleri</span><span class="sxs-lookup"><span data-stu-id="3f829-126">Calling Interface Methods</span></span>
<span data-ttu-id="3f829-127">Arabirimini uygulayan türünde herhangi bir nesne üzerinden değil, yalnızca arabiriminden arabirim yöntemleri çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="3f829-127">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="3f829-128">Böylece, arabirim türüne yukarı çevrim kullanarak gerekebilir `:>` işleci veya `upcast` bu yöntemleri çağırmak için işleci.</span><span class="sxs-lookup"><span data-stu-id="3f829-128">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="3f829-129">Nesne türüne sahip olduğunda arabirim yöntemini çağırmak için `SomeClass`, aşağıdaki kodda gösterildiği gibi yukarı çevrim arabirim türü nesneye gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f829-129">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="3f829-130">Alternatif bir yöntem bir nesne üzerinde bu upcasts bildirmektir ve aşağıdaki örnekteki gibi arabirim yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="3f829-130">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="3f829-131">Nesne ifadeleri kullanarak arabirimler uygulama</span><span class="sxs-lookup"><span data-stu-id="3f829-131">Implementing Interfaces by Using Object Expressions</span></span>
<span data-ttu-id="3f829-132">Nesne ifadeleri bir arabirim için kısa bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f829-132">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="3f829-133">Bunlar, adlandırılmış bir tür oluşturmak zorunda değildir ve yalnızca ek yöntemleri olmadan arabirim yöntemleri destekleyen bir nesne istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="3f829-133">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="3f829-134">Aşağıdaki kodda bir nesne ifadesi gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3f829-134">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a><span data-ttu-id="3f829-135">Arabirim devralma</span><span class="sxs-lookup"><span data-stu-id="3f829-135">Interface Inheritance</span></span>
<span data-ttu-id="3f829-136">Bir veya daha fazla temel arabirimlerinden arabirimleri devralabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f829-136">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a><span data-ttu-id="3f829-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f829-137">See Also</span></span>
[<span data-ttu-id="3f829-138">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3f829-138">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="3f829-139">Nesne İfadeleri</span><span class="sxs-lookup"><span data-stu-id="3f829-139">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="3f829-140">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="3f829-140">Classes</span></span>](classes.md)
