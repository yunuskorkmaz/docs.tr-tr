---
title: Açık arabirim uygulama-C# Programlama Kılavuzu
description: Bir sınıf, C# ' de aynı imzaya sahip bir üye içeren arabirimler uygulayabilir. Açık uygulama, bir arabirime özgü bir sınıf üyesi oluşturur.
ms.date: 03/24/2021
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.openlocfilehash: 2ca7e8a10c009b01b43e0c09d25d2dd99cbee2ec
ms.sourcegitcommit: 80f38cb67bd02f51d5722fa13d0ea207e3b14a8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2021
ms.locfileid: "105610869"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="92c2b-104">Açık Arabirim Uygulaması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="92c2b-104">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="92c2b-105">Bir [sınıf](../../language-reference/keywords/class.md) , aynı imzaya sahip bir üye içeren iki arabirim uygularsa, bu üyeyi sınıfında uygulamak, her iki arabirimin de uygulama olarak bu üyeyi kullanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="92c2b-105">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="92c2b-106">Aşağıdaki örnekte, tüm çağrıları `Paint` aynı yöntemi çağırmak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="92c2b-106">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="92c2b-107">Bu ilk örnek, türleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="92c2b-107">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="92c2b-108">Aşağıdaki örnek yöntemleri çağırır:</span><span class="sxs-lookup"><span data-stu-id="92c2b-108">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="92c2b-109">Ancak aynı uygulamanın her iki arabirim için de çağrılması istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92c2b-109">But you might not want the same implementation to be called for both interfaces.</span></span> <span data-ttu-id="92c2b-110">Hangi arabirimin kullanımda olduğuna bağlı olarak farklı bir uygulama çağırmak için, açıkça bir arabirim üyesi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92c2b-110">To call a different implementation depending on which interface is in use, you can implement an interface member explicitly.</span></span> <span data-ttu-id="92c2b-111">Açık arabirim uygulama, yalnızca belirtilen arabirim aracılığıyla çağrılan bir sınıf üyesidir.</span><span class="sxs-lookup"><span data-stu-id="92c2b-111">An explicit interface implementation is a class member that is only called through the specified interface.</span></span> <span data-ttu-id="92c2b-112">Sınıf üyesini, arabirimin adı ve bir nokta ile önek olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="92c2b-112">Name the class member by prefixing it with the name of the interface and a period.</span></span> <span data-ttu-id="92c2b-113">Örnek:</span><span class="sxs-lookup"><span data-stu-id="92c2b-113">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="92c2b-114">Sınıf üyesi `IControl.Paint` yalnızca arabirim aracılığıyla kullanılabilir `IControl` ve `ISurface.Paint` yalnızca ile kullanılabilir `ISurface` .</span><span class="sxs-lookup"><span data-stu-id="92c2b-114">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="92c2b-115">Her iki yöntem uygulaması ayrı değildir ve doğrudan sınıfta kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="92c2b-115">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="92c2b-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="92c2b-116">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="92c2b-117">Açık uygulama, her biri bir özellik ve bir yöntem gibi aynı ada sahip farklı Üyeler bildiren iki arabirimin da bulunduğu durumları çözümlemek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="92c2b-117">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="92c2b-118">Her iki arabirimi de uygulamak için bir sınıf, bir `P` derleyici hatasından kaçınmak için özellik veya yöntem ya da her ikisi için açık uygulamayı kullanmalıdır `P` .</span><span class="sxs-lookup"><span data-stu-id="92c2b-118">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="92c2b-119">Örnek:</span><span class="sxs-lookup"><span data-stu-id="92c2b-119">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="92c2b-120">Açık arabirim uygulamasında tanımlı olduğu türün bir üyesi olarak erişilebilir olmadığından, bir erişim değiştiricisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="92c2b-120">An explicit interface implementation doesn't have an access modifier since it isn't accessible as a member of the type it's defined in.</span></span> <span data-ttu-id="92c2b-121">Bunun yerine, yalnızca arabirimin bir örneği aracılığıyla çağrıldığında erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="92c2b-121">Instead, it's only accessible when called through an instance of the interface.</span></span> <span data-ttu-id="92c2b-122">Açık arabirim uygulamaları için bir erişim değiştiricisi belirtirseniz, derleyici hatası [CS0106](../../language-reference/compiler-messages/cs0106.md)alırsınız.</span><span class="sxs-lookup"><span data-stu-id="92c2b-122">If you specify an access modifier for an explicit interface implementation, you get compiler error [CS0106](../../language-reference/compiler-messages/cs0106.md).</span></span> <span data-ttu-id="92c2b-123">Daha fazla bilgi için bkz. [ `interface` (C# Başvurusu)](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="92c2b-123">For more information, see [`interface` (C# Reference)](../../language-reference/keywords/interface.md).</span></span>

<span data-ttu-id="92c2b-124">[C# 8,0](../../whats-new/csharp-8.md#default-interface-methods)' den başlayarak, bir arabirimde bildirildiği Üyeler için bir uygulama tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92c2b-124">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="92c2b-125">Bir sınıf bir arabirimden bir yöntem uygulamasını devralırsa, bu yönteme yalnızca arabirim türünün bir başvurusuyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="92c2b-125">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="92c2b-126">Devralınan üye, ortak arabirimin parçası olarak görünmez.</span><span class="sxs-lookup"><span data-stu-id="92c2b-126">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="92c2b-127">Aşağıdaki örnek, bir arabirim yöntemi için varsayılan uygulamayı tanımlar:</span><span class="sxs-lookup"><span data-stu-id="92c2b-127">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="92c2b-128">Aşağıdaki örnek varsayılan uygulamayı çağırır:</span><span class="sxs-lookup"><span data-stu-id="92c2b-128">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="92c2b-129">Arabirimi uygulayan herhangi bir sınıf, `IControl` `Paint` genel bir yöntem olarak ya da açık bir arabirim uygulamasıyla varsayılan yöntemi geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="92c2b-129">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="92c2b-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92c2b-130">See also</span></span>

- [<span data-ttu-id="92c2b-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="92c2b-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="92c2b-132">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="92c2b-132">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="92c2b-133">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="92c2b-133">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="92c2b-134">Devralma</span><span class="sxs-lookup"><span data-stu-id="92c2b-134">Inheritance</span></span>](../classes-and-structs/inheritance.md)
