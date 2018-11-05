---
title: Arabirimler (F#)
description: F# arabirimleri diğer sınıfları uygulayan ilgili üyelerinin kümeleri nasıl belirteceğinizi öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 6d7f8ee9ea17d2294933f88577c30a96975ae5d4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "47231446"
---
# <a name="interfaces"></a><span data-ttu-id="48735-103">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="48735-103">Interfaces</span></span>

<span data-ttu-id="48735-104">*Arabirimleri* diğer sınıfları uygulayan ilgili üyeleri kümesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="48735-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="48735-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48735-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="48735-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48735-106">Remarks</span></span>

<span data-ttu-id="48735-107">Hiç üye uygulanan dışında sınıf bildirimleri arabirimi bildirimleri benzer.</span><span class="sxs-lookup"><span data-stu-id="48735-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="48735-108">Bunun yerine, tüm üyeleri anahtar sözcüğü tarafından belirtildiği şekilde soyuttur `abstract`.</span><span class="sxs-lookup"><span data-stu-id="48735-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="48735-109">Soyut metotlar için bir yöntem gövdesi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="48735-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="48735-110">Ancak, ayrı bir üye tanımı ile birlikte bir iletişim yöntemi olarak da dahil olmak üzere tarafından varsayılan bir uygulama sağlayabilirsiniz `default` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="48735-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="48735-111">Bunun yapılması, diğer .NET dillerinde taban sınıfında sanal bir yöntem oluşturmaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="48735-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="48735-112">Arabirimini uygulayan sınıflar sanal bir yöntem geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="48735-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="48735-113">Arabirimler için varsayılan erişilebilirlik, `public`.</span><span class="sxs-lookup"><span data-stu-id="48735-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="48735-114">İsteğe bağlı olarak, her bir yöntem parametresi normal F# söz dizimini kullanarak bir ad verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="48735-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="48735-115">Yukarıdaki içinde `ISprintable` örnek, `Print` yöntemi türünde tek bir parametreye sahip `string` adıyla `format`.</span><span class="sxs-lookup"><span data-stu-id="48735-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="48735-116">Arayüzleri uygulamak için iki yolu vardır: Nesne ifadeleri kullanarak ve sınıf türleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="48735-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="48735-117">Her iki durumda da sınıfı türü veya nesne ifadesi metot gövdeleri arabirimi soyut yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="48735-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="48735-118">Arabirimini uygulayan her tür için belirli uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="48735-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="48735-119">Bu nedenle, farklı türlerde arabirim yöntemleri birbirinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="48735-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="48735-120">Anahtar sözcükler `interface` ve `end`, başlangıç ve bitiş tanımının işaretlemek, isteğe bağlı basit sözdizimi kullandığınızda.</span><span class="sxs-lookup"><span data-stu-id="48735-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="48735-121">Bu anahtar sözcükler kullanmazsanız derleyici türü bir sınıf veya arabirim kullandığınız yapılarını analiz ederek olup olmadığını çıkarsamak çalışır.</span><span class="sxs-lookup"><span data-stu-id="48735-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="48735-122">Bir üye veya diğer sınıfı sözdizimi kullanıyorsanız, türü bir sınıf olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="48735-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="48735-123">Tüm arabirimleri büyük harfle başlamak için kodlama stili .NET olan `I`.</span><span class="sxs-lookup"><span data-stu-id="48735-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="48735-124">Sınıf türleri kullanarak arabirimleri uygulama</span><span class="sxs-lookup"><span data-stu-id="48735-124">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="48735-125">Kullanarak bir sınıf türünde bir veya daha fazla arabirim uygulayabilir `interface` anahtar sözcüğü, arabirimin adını ve `with` arabirimi tarafından üye tanımları, aşağıdaki kodda gösterildiği gibi anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="48735-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="48735-126">Tüm türetilmiş sınıfları, bunları yeniden uygulayın gerekmez. Bu nedenle, arabirim uygulamalarına devralınır.</span><span class="sxs-lookup"><span data-stu-id="48735-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="48735-127">Arabirim yöntemleri çağırma</span><span class="sxs-lookup"><span data-stu-id="48735-127">Calling Interface Methods</span></span>

<span data-ttu-id="48735-128">Arabirim yöntemleri arabirimi uygulayan türün herhangi bir nesne üzerinden değil, yalnızca arabiriminden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="48735-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="48735-129">Bu nedenle, arabirim türüne yukarı çevrim kullanarak gerekebilir `:>` işleci veya `upcast` işleci bu yöntemleri çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="48735-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="48735-130">Bir nesne türü olduğunda arabirim yöntemini çağırmak için `SomeClass`, aşağıdaki kodda gösterildiği gibi yukarı çevrim nesnesine bir arabirim türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48735-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="48735-131">Alternatif bu upcasts nesne üzerinde bir yöntemi bildirmek için ve aşağıdaki örnekte olduğu gibi arabirim yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="48735-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="48735-132">Nesne ifadeleri kullanarak arabirimleri uygulama</span><span class="sxs-lookup"><span data-stu-id="48735-132">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="48735-133">Nesne ifadeleri, bir arabirim uygulamak için kısa bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="48735-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="48735-134">Bunlar, adlandırılmış bir tür oluşturmak zorunda değilsiniz ve ek yöntemleri olmadan arabirim yöntemleri destekleyen bir nesne yalnızca istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="48735-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="48735-135">Bir nesne ifadesi, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="48735-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="48735-136">Devralma arabirimi</span><span class="sxs-lookup"><span data-stu-id="48735-136">Interface Inheritance</span></span>

<span data-ttu-id="48735-137">Arabirimleri, bir veya daha fazla temel Ara birimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="48735-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a><span data-ttu-id="48735-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48735-138">See also</span></span>

- [<span data-ttu-id="48735-139">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="48735-139">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="48735-140">Nesne İfadeleri</span><span class="sxs-lookup"><span data-stu-id="48735-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="48735-141">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="48735-141">Classes</span></span>](classes.md)
