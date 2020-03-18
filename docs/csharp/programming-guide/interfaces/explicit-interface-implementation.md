---
title: Açık Arayüz Uygulaması - C# Programlama Kılavuzu
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167679"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="87f93-102">Açık Arabirim Uygulaması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="87f93-102">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="87f93-103">Bir [sınıf](../../language-reference/keywords/class.md) aynı imzaya sahip bir üye içeren iki arabirim uygularsa, bu üyenin sınıfta uygulanması her iki arabirimin de bu üyeyi uygulama olarak kullanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="87f93-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="87f93-104">Aşağıdaki örnekte, tüm çağrıları `Paint` aynı yöntemi çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="87f93-104">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="87f93-105">Bu ilk örnek türleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="87f93-105">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="87f93-106">Aşağıdaki örnek yöntemleri çağırır:</span><span class="sxs-lookup"><span data-stu-id="87f93-106">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="87f93-107">İki arabirim üyesi aynı işlevi yerine getirmediğinde, arabirimlerin birinden veya her ikisinin yanlış uygulanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="87f93-107">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="87f93-108">Bir arabirim üyesini açıkça uygulamak mümkündür-yalnızca arabirim üzerinden çağrılan ve bu arabirime özgü bir sınıf üyesi oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="87f93-108">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="87f93-109">Arabirimin adı ve bir nokta ile sınıf üyesi adı.</span><span class="sxs-lookup"><span data-stu-id="87f93-109">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="87f93-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="87f93-110">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="87f93-111">Sınıf üyesi `IControl.Paint` yalnızca `IControl` arabirim üzerinden `ISurface.Paint` kullanılabilir ve `ISurface`yalnızca .</span><span class="sxs-lookup"><span data-stu-id="87f93-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="87f93-112">Her iki yöntem uygulamaları ayrıdır ve ikisi de doğrudan sınıfta kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="87f93-112">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="87f93-113">Örnek:</span><span class="sxs-lookup"><span data-stu-id="87f93-113">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="87f93-114">Açık uygulama, her biri bir özellik ve yöntem gibi aynı adı taşıyan farklı üyeleri beyan eden iki arabirimin bulunduğu durumları çözmek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87f93-114">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="87f93-115">Her iki arabirimi de uygulamak için, derleyici `P`hatasını önlemek `P`için bir sınıfın özellik veya yöntem veya her ikisi için açık uygulama kullanması zorunludur.</span><span class="sxs-lookup"><span data-stu-id="87f93-115">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="87f93-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="87f93-116">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="87f93-117">[C# 8.0](../../whats-new/csharp-8.md#default-interface-methods)ile başlayarak, arabirimde bildirilen üyeler için bir uygulama tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87f93-117">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="87f93-118">Bir sınıf bir arabirimden bir yöntem uygulaması devralıyorsa, bu yönteme yalnızca arabirim türünün başvurusu yla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="87f93-118">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="87f93-119">Devralınan üye ortak arabirimin bir parçası olarak görünmez.</span><span class="sxs-lookup"><span data-stu-id="87f93-119">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="87f93-120">Aşağıdaki örnek, arabirim yöntemi için varsayılan bir uygulama tanımlar:</span><span class="sxs-lookup"><span data-stu-id="87f93-120">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="87f93-121">Aşağıdaki örnek temerrüt uygulamasını çağırır:</span><span class="sxs-lookup"><span data-stu-id="87f93-121">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="87f93-122">`IControl` Arabirimi uygulayan herhangi bir sınıf, `Paint` genel bir yöntem olarak veya açık arabirim uygulaması olarak varsayılan yöntemi geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="87f93-122">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="87f93-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87f93-123">See also</span></span>

- [<span data-ttu-id="87f93-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="87f93-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="87f93-125">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="87f93-125">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="87f93-126">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="87f93-126">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="87f93-127">Devralma</span><span class="sxs-lookup"><span data-stu-id="87f93-127">Inheritance</span></span>](../classes-and-structs/inheritance.md)
