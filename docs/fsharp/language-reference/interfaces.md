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
# <a name="interfaces"></a><span data-ttu-id="1bfb8-103">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="1bfb8-103">Interfaces</span></span>

<span data-ttu-id="1bfb8-104">*Arabirimler* , diğer sınıfların uygulayan ilgili üye kümelerini belirler.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="1bfb8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bfb8-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="1bfb8-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bfb8-106">Remarks</span></span>

<span data-ttu-id="1bfb8-107">Arabirim bildirimleri, hiçbir üye uygulanmamalıdır hariç sınıf bildirimlerine benzer.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="1bfb8-108">Bunun yerine, tüm Üyeler anahtar sözcüğüyle `abstract`gösterildiği gibi soyuttur.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="1bfb8-109">Soyut yöntemler için bir yöntem gövdesi sağlamazsanız.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="1bfb8-110">Ancak, `default` anahtar sözcükle birlikte bir yöntem olarak üyenin ayrı bir tanımını da ekleyerek varsayılan bir uygulama sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="1bfb8-111">Bunun yapılması, diğer .NET dillerinin temel sınıfında bir sanal yöntem oluşturmaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="1bfb8-112">Bu tür bir sanal yöntem, arabirimini uygulayan sınıflarda geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="1bfb8-113">Arabirimler için varsayılan erişilebilirlik `public`.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="1bfb8-114">İsteğe bağlı olarak, her yöntem parametresine normal F# sözdizimi kullanarak bir ad verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1bfb8-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="1bfb8-115">Yukarıdaki `ISprintable` örnekte `Print` , yönteminin adında `string` tek`format`bir parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="1bfb8-116">Arabirim uygulamak için iki yol vardır: nesne ifadelerini kullanarak ve sınıf türlerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="1bfb8-117">Her iki durumda da, sınıf türü veya nesne ifadesi, arabirimin soyut yöntemleri için yöntem gövdeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="1bfb8-118">Uygulamalar, arabirimini uygulayan her türe özeldir.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="1bfb8-119">Bu nedenle, farklı türlerde arabirim yöntemleri birbirinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="1bfb8-120">Basit sözdizimi `interface` kullandığınızda `end`, tanımın başlangıcını ve bitişini işaretleyen anahtar sözcükler ve, isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="1bfb8-121">Bu anahtar sözcükleri kullanmıyorsanız, derleyici, kullandığınız yapıları çözümleyerek türün bir sınıf mı yoksa bir arabirim mi olduğunu çıkarmayın.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="1bfb8-122">Bir üye tanımlayabilir veya diğer sınıf sözdizimini kullanırsanız, tür bir sınıf olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="1bfb8-123">.NET kodlama stili, tüm arabirimlerin sermaye `I`olarak başlamadır.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="1bfb8-124">Sınıf türlerini kullanarak arabirimleri uygulama</span><span class="sxs-lookup"><span data-stu-id="1bfb8-124">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="1bfb8-125">Aşağıdaki kodda gösterildiği gibi `interface` anahtar sözcüğünü, arabirimin adını `with` ve anahtar sözcüğünü kullanarak bir sınıf türünde bir veya daha fazla arabirim uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="1bfb8-126">Arabirim uygulamaları devralınır, bu nedenle türetilen sınıfların bunları yeniden uygulaması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="1bfb8-127">Arabirim yöntemlerini çağırma</span><span class="sxs-lookup"><span data-stu-id="1bfb8-127">Calling Interface Methods</span></span>

<span data-ttu-id="1bfb8-128">Arabirim yöntemleri, arabirimi uygulayan türdeki herhangi bir nesne yerine yalnızca arabirim üzerinden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="1bfb8-129">Bu nedenle, bu yöntemleri çağırmak için `:>` işlecini `upcast` veya işlecini kullanarak arabirim türüne yukarı atama yapmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="1bfb8-130">Türünde `SomeClass`bir nesneniz olduğunda arabirim yöntemini çağırmak için, aşağıdaki kodda gösterildiği gibi, nesneyi arabirim türüne yukarı atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="1bfb8-131">Alternatif olarak, aşağıdaki örnekte olduğu gibi, ve arabirim yöntemini çağıran nesne üzerinde bir yöntemi bildirmenin bir alternatifi.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="1bfb8-132">Nesne Ifadeleri kullanarak arabirimleri uygulama</span><span class="sxs-lookup"><span data-stu-id="1bfb8-132">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="1bfb8-133">Nesne ifadeleri, arabirim uygulamak için kısa bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="1bfb8-134">Adlandırılmış bir tür oluşturmanız gerekmeden ve yalnızca arabirim yöntemlerini destekleyen bir nesne istediğinizde, ek yöntemler olmadan bu yöntemler faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="1bfb8-135">Bir nesne ifadesi aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="1bfb8-136">Arabirim devralma</span><span class="sxs-lookup"><span data-stu-id="1bfb8-136">Interface Inheritance</span></span>

<span data-ttu-id="1bfb8-137">Arabirimler, bir veya daha fazla taban arabiriminden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a><span data-ttu-id="1bfb8-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-138">See also</span></span>

- [<span data-ttu-id="1bfb8-139">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1bfb8-139">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1bfb8-140">Nesne İfadeleri</span><span class="sxs-lookup"><span data-stu-id="1bfb8-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="1bfb8-141">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="1bfb8-141">Classes</span></span>](classes.md)
