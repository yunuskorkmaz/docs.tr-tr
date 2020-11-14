---
title: Arabirimler
description: 'F # arabirimlerinin, diğer sınıfların uygulayan ilgili üye kümelerini nasıl belirttireceğinizi öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 0cef2932045dae401f5aa069107815543457ca4a
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557057"
---
# <a name="interfaces"></a><span data-ttu-id="c5ced-103">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="c5ced-103">Interfaces</span></span>

<span data-ttu-id="c5ced-104">*Arabirimler* , diğer sınıfların uygulayan ilgili üye kümelerini belirler.</span><span class="sxs-lookup"><span data-stu-id="c5ced-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5ced-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c5ced-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="c5ced-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5ced-106">Remarks</span></span>

<span data-ttu-id="c5ced-107">Arabirim bildirimleri, hiçbir üye uygulanmamalıdır hariç sınıf bildirimlerine benzer.</span><span class="sxs-lookup"><span data-stu-id="c5ced-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="c5ced-108">Bunun yerine, tüm Üyeler anahtar sözcüğüyle gösterildiği gibi soyuttur `abstract` .</span><span class="sxs-lookup"><span data-stu-id="c5ced-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="c5ced-109">Soyut yöntemler için bir yöntem gövdesi sağlamazsanız.</span><span class="sxs-lookup"><span data-stu-id="c5ced-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="c5ced-110">Ancak, anahtar sözcükle birlikte bir yöntem olarak üyenin ayrı bir tanımını da ekleyerek varsayılan bir uygulama sağlayabilirsiniz `default` .</span><span class="sxs-lookup"><span data-stu-id="c5ced-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="c5ced-111">Bunun yapılması, diğer .NET dillerinin temel sınıfında bir sanal yöntem oluşturmaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c5ced-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="c5ced-112">Bu tür bir sanal yöntem, arabirimini uygulayan sınıflarda geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="c5ced-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="c5ced-113">Arabirimler için varsayılan erişilebilirlik `public` .</span><span class="sxs-lookup"><span data-stu-id="c5ced-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="c5ced-114">İsteğe bağlı olarak, her yöntem parametresine normal F # söz dizimini kullanarak bir ad verebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5ced-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="c5ced-115">Yukarıdaki `ISprintable` örnekte, `Print` yönteminin adında tek bir parametresi vardır `string` `format` .</span><span class="sxs-lookup"><span data-stu-id="c5ced-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="c5ced-116">Arabirim uygulamak için iki yol vardır: nesne ifadelerini kullanarak ve sınıf türlerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="c5ced-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="c5ced-117">Her iki durumda da, sınıf türü veya nesne ifadesi, arabirimin soyut yöntemleri için yöntem gövdeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5ced-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="c5ced-118">Uygulamalar, arabirimini uygulayan her türe özeldir.</span><span class="sxs-lookup"><span data-stu-id="c5ced-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="c5ced-119">Bu nedenle, farklı türlerde arabirim yöntemleri birbirinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5ced-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="c5ced-120">`interface` `end` Basit sözdizimi kullandığınızda, tanımın başlangıcını ve bitişini işaretleyen anahtar sözcükler ve, isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5ced-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="c5ced-121">Bu anahtar sözcükleri kullanmıyorsanız, derleyici, kullandığınız yapıları çözümleyerek türün bir sınıf mı yoksa bir arabirim mi olduğunu çıkarmayın.</span><span class="sxs-lookup"><span data-stu-id="c5ced-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="c5ced-122">Bir üye tanımlayabilir veya diğer sınıf sözdizimini kullanırsanız, tür bir sınıf olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="c5ced-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="c5ced-123">.NET kodlama stili, tüm arabirimlerin sermaye olarak başlamadır `I` .</span><span class="sxs-lookup"><span data-stu-id="c5ced-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

<span data-ttu-id="c5ced-124">Birden çok parametreyi iki şekilde belirtebilirsiniz: F # stili ve. NET stili.</span><span class="sxs-lookup"><span data-stu-id="c5ced-124">You can specify multiple parameters in two ways: F#-style and .NET-style.</span></span> <span data-ttu-id="c5ced-125">Her ikisi de .NET tüketicileriyle aynı şekilde derlenir, ancak f # stili f # çağıranlarını F # stili parametre uygulaması ve ile kullanmak için zorlayacaktır. NET stili, F # çağıranlarını tupled bağımsız değişken uygulaması kullanacak şekilde zorlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="c5ced-125">Both will compile the same way for .NET consumers, but F#-style will force F# callers to use F#-style parameter application and .NET-style will force F# callers to use tupled argument application.</span></span>

```fsharp
type INumeric1 =
    abstract Add: x: int -> y: int -> int

type INumeric2 =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="c5ced-126">Sınıf türlerini kullanarak arabirimleri uygulama</span><span class="sxs-lookup"><span data-stu-id="c5ced-126">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="c5ced-127">`interface`Aşağıdaki kodda gösterildiği gibi anahtar sözcüğünü, arabirimin adını ve anahtar sözcüğünü kullanarak bir sınıf türünde bir veya daha fazla arabirim uygulayabilirsiniz `with` .</span><span class="sxs-lookup"><span data-stu-id="c5ced-127">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="c5ced-128">Arabirim uygulamaları devralınır, bu nedenle türetilen sınıfların bunları yeniden uygulaması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c5ced-128">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="c5ced-129">Arabirim yöntemlerini çağırma</span><span class="sxs-lookup"><span data-stu-id="c5ced-129">Calling Interface Methods</span></span>

<span data-ttu-id="c5ced-130">Arabirim yöntemleri, arabirimi uygulayan türdeki herhangi bir nesne yerine yalnızca arabirim üzerinden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5ced-130">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="c5ced-131">Bu nedenle, `:>` `upcast` Bu yöntemleri çağırmak için işlecini veya işlecini kullanarak arabirim türüne yukarı atama yapmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c5ced-131">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="c5ced-132">Türünde bir nesneniz olduğunda arabirim yöntemini çağırmak için `SomeClass` , aşağıdaki kodda gösterildiği gibi, nesneyi arabirim türüne yukarı atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="c5ced-132">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="c5ced-133">Alternatif olarak, aşağıdaki örnekte olduğu gibi, ve arabirim yöntemini çağıran nesne üzerinde bir yöntemi bildirmenin bir alternatifi.</span><span class="sxs-lookup"><span data-stu-id="c5ced-133">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="c5ced-134">Nesne Ifadeleri kullanarak arabirimleri uygulama</span><span class="sxs-lookup"><span data-stu-id="c5ced-134">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="c5ced-135">Nesne ifadeleri, arabirim uygulamak için kısa bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5ced-135">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="c5ced-136">Adlandırılmış bir tür oluşturmanız gerekmeden ve yalnızca arabirim yöntemlerini destekleyen bir nesne istediğinizde, ek yöntemler olmadan bu yöntemler faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5ced-136">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="c5ced-137">Bir nesne ifadesi aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c5ced-137">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="c5ced-138">Arabirim devralma</span><span class="sxs-lookup"><span data-stu-id="c5ced-138">Interface Inheritance</span></span>

<span data-ttu-id="c5ced-139">Arabirimler, bir veya daha fazla taban arabiriminden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="c5ced-139">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="implementing-interfaces-with-default-implementations"></a><span data-ttu-id="c5ced-140">Varsayılan uygulamalarla arabirimleri uygulama</span><span class="sxs-lookup"><span data-stu-id="c5ced-140">Implementing interfaces with default implementations</span></span>

<span data-ttu-id="c5ced-141">C#, varsayılan uygulamalarla arabirim tanımlamayı destekler, örneğin:</span><span class="sxs-lookup"><span data-stu-id="c5ced-141">C# supports defining interfaces with default implementations, like so:</span></span>

```csharp
using System;

namespace CSharp
{
    public interface MyDim
    {
        public int Z => 0;
    }
}
```

<span data-ttu-id="c5ced-142">Bunlar F # ' dan doğrudan tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="c5ced-142">These are directly consumable from F#:</span></span>

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn $"DIM from C#: %d{md.Z}"

// You can also implement it via an object expression
let md' = { new MyDim }
printfn $"DIM from C# but via Object Expression: %d{md'.Z}"
```

<span data-ttu-id="c5ced-143">`override`Herhangi bir sanal üyeyi geçersiz kılmak gibi, ile varsayılan bir uygulamayı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5ced-143">You can override a default implementation with `override`, like overriding any virtual member.</span></span>

<span data-ttu-id="c5ced-144">Varsayılan bir uygulamasına sahip olmayan bir arabirimdeki tüm üyelerin açıkça uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5ced-144">Any members in an interface that do not have a default implementation must still be explicitly implemented.</span></span>

## <a name="implementing-the-same-interface-at-different-generic-instantiations"></a><span data-ttu-id="c5ced-145">Farklı genel örneklerde aynı arabirimi uygulama</span><span class="sxs-lookup"><span data-stu-id="c5ced-145">Implementing the same interface at different generic instantiations</span></span>

<span data-ttu-id="c5ced-146">F #, farklı genel örneklerde aynı arabirimi aynı şekilde uygulamayı destekler:</span><span class="sxs-lookup"><span data-stu-id="c5ced-146">F# supports implementing the same interface at different generic instantiations like so:</span></span>

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

## <a name="see-also"></a><span data-ttu-id="c5ced-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5ced-147">See also</span></span>

- [<span data-ttu-id="c5ced-148">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="c5ced-148">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c5ced-149">Nesne İfadeleri</span><span class="sxs-lookup"><span data-stu-id="c5ced-149">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="c5ced-150">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="c5ced-150">Classes</span></span>](classes.md)
