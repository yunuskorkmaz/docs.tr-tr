---
title: Açık arabirim uygulama- C# Programlama Kılavuzu
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: c6f1f849e0d4e831802b4c9b8b4bc3887363a34c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628156"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="0a568-102">Açık Arabirim Uygulaması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0a568-102">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="0a568-103">Bir [sınıf](../../language-reference/keywords/class.md) , aynı imzaya sahip bir üye içeren iki arabirim uygularsa, bu üyeyi sınıfında uygulamak, her iki arabirimin de uygulama olarak bu üyeyi kullanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0a568-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="0a568-104">Aşağıdaki örnekte, `Paint` için tüm çağrılar aynı yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="0a568-104">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="0a568-105">Bu ilk örnek, türleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="0a568-105">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="0a568-106">Aşağıdaki örnek yöntemleri çağırır:</span><span class="sxs-lookup"><span data-stu-id="0a568-106">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="0a568-107">İki arabirim üyesi aynı işlevi gerçekleştirmezseniz, arabirimlerin bir veya her ikisinin yanlış bir uygulamasına yol açar.</span><span class="sxs-lookup"><span data-stu-id="0a568-107">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="0a568-108">Yalnızca arabirim aracılığıyla çağrılan ve bu arabirime özgü olan bir sınıf üyesi oluşturarak, bir arabirim üyesini açıkça uygulamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0a568-108">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="0a568-109">Sınıf üyesini arabirimin adı ve nokta ile adlandırın.</span><span class="sxs-lookup"><span data-stu-id="0a568-109">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="0a568-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0a568-110">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="0a568-111">Sınıf üyesi `IControl.Paint` yalnızca `IControl` arabirimi aracılığıyla kullanılabilir ve `ISurface.Paint` yalnızca `ISurface`ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a568-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="0a568-112">Her iki yöntem uygulaması ayrı değildir ve doğrudan sınıfta kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0a568-112">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="0a568-113">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0a568-113">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="0a568-114">Açık uygulama, her biri bir özellik ve bir yöntem gibi aynı ada sahip farklı Üyeler bildiren iki arabirimin da bulunduğu durumları çözümlemek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a568-114">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="0a568-115">Her iki arabirimi de uygulamak için bir sınıfın bir derleyici hatasından kaçınmak için özellik `P`veya yöntem `P`ya da her ikisi için açık uygulamayı kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a568-115">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="0a568-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0a568-116">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="0a568-117">Bir sınıf bir arabirimden bir yöntem uygulamasını devralırsa, bu yönteme yalnızca arabirim türünün bir başvurusuyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0a568-117">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="0a568-118">Devralınan üye, ortak arabirimin parçası olarak görünmez.</span><span class="sxs-lookup"><span data-stu-id="0a568-118">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="0a568-119">Aşağıdaki örnek, bir arabirim yöntemi için varsayılan uygulamayı tanımlar:</span><span class="sxs-lookup"><span data-stu-id="0a568-119">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="0a568-120">Aşağıdaki örnek varsayılan uygulamayı çağırır:</span><span class="sxs-lookup"><span data-stu-id="0a568-120">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="0a568-121">`IControl` arabirimini uygulayan herhangi bir sınıf, genel bir yöntem olarak ya da açık bir arabirim uygulamasıyla varsayılan `Paint` yöntemini geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a568-121">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a568-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a568-122">See also</span></span>

- [<span data-ttu-id="0a568-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0a568-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0a568-124">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="0a568-124">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="0a568-125">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="0a568-125">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="0a568-126">Devralma</span><span class="sxs-lookup"><span data-stu-id="0a568-126">Inheritance</span></span>](../classes-and-structs/inheritance.md)
