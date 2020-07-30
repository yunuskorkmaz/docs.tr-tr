---
title: Açık arabirim uygulama-C# Programlama Kılavuzu
description: Bir sınıf, C# ' de aynı imzaya sahip bir üye içeren arabirimler uygulayabilir. Açık uygulama, bir arabirime özgü bir sınıf üyesi oluşturur.
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: a6ec328c08d1da84a11431d9400a094df8c72223
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303094"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="b51ce-104">Açık Arabirim Uygulaması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b51ce-104">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="b51ce-105">Bir [sınıf](../../language-reference/keywords/class.md) , aynı imzaya sahip bir üye içeren iki arabirim uygularsa, bu üyeyi sınıfında uygulamak, her iki arabirimin de uygulama olarak bu üyeyi kullanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b51ce-105">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="b51ce-106">Aşağıdaki örnekte, tüm çağrıları `Paint` aynı yöntemi çağırmak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="b51ce-106">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="b51ce-107">Bu ilk örnek, türleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="b51ce-107">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="b51ce-108">Aşağıdaki örnek yöntemleri çağırır:</span><span class="sxs-lookup"><span data-stu-id="b51ce-108">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="b51ce-109">İki arabirim üyesi aynı işlevi gerçekleştirmezseniz, arabirimlerin bir veya her ikisinin yanlış bir uygulamasına yol açar.</span><span class="sxs-lookup"><span data-stu-id="b51ce-109">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="b51ce-110">Yalnızca arabirim aracılığıyla çağrılan ve bu arabirime özgü olan bir sınıf üyesi oluşturarak, bir arabirim üyesini açıkça uygulamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b51ce-110">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="b51ce-111">Sınıf üyesini arabirimin adı ve nokta ile adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b51ce-111">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="b51ce-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b51ce-112">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="b51ce-113">Sınıf üyesi `IControl.Paint` yalnızca arabirim aracılığıyla kullanılabilir `IControl` ve `ISurface.Paint` yalnızca ile kullanılabilir `ISurface` .</span><span class="sxs-lookup"><span data-stu-id="b51ce-113">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="b51ce-114">Her iki yöntem uygulaması ayrı değildir ve doğrudan sınıfta kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b51ce-114">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="b51ce-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b51ce-115">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="b51ce-116">Açık uygulama, her biri bir özellik ve bir yöntem gibi aynı ada sahip farklı Üyeler bildiren iki arabirimin da bulunduğu durumları çözümlemek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b51ce-116">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="b51ce-117">Her iki arabirimi de uygulamak için bir sınıf, bir `P` derleyici hatasından kaçınmak için özellik veya yöntem ya da her ikisi için açık uygulamayı kullanmalıdır `P` .</span><span class="sxs-lookup"><span data-stu-id="b51ce-117">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="b51ce-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b51ce-118">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="b51ce-119">[C# 8,0](../../whats-new/csharp-8.md#default-interface-methods)' den başlayarak, bir arabirimde bildirildiği Üyeler için bir uygulama tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b51ce-119">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="b51ce-120">Bir sınıf bir arabirimden bir yöntem uygulamasını devralırsa, bu yönteme yalnızca arabirim türünün bir başvurusuyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b51ce-120">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="b51ce-121">Devralınan üye, ortak arabirimin parçası olarak görünmez.</span><span class="sxs-lookup"><span data-stu-id="b51ce-121">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="b51ce-122">Aşağıdaki örnek, bir arabirim yöntemi için varsayılan uygulamayı tanımlar:</span><span class="sxs-lookup"><span data-stu-id="b51ce-122">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="b51ce-123">Aşağıdaki örnek varsayılan uygulamayı çağırır:</span><span class="sxs-lookup"><span data-stu-id="b51ce-123">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="b51ce-124">Arabirimi uygulayan herhangi bir sınıf, `IControl` `Paint` genel bir yöntem olarak ya da açık bir arabirim uygulamasıyla varsayılan yöntemi geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="b51ce-124">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="b51ce-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b51ce-125">See also</span></span>

- [<span data-ttu-id="b51ce-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b51ce-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b51ce-127">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="b51ce-127">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="b51ce-128">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b51ce-128">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="b51ce-129">Devralma</span><span class="sxs-lookup"><span data-stu-id="b51ce-129">Inheritance</span></span>](../classes-and-structs/inheritance.md)
