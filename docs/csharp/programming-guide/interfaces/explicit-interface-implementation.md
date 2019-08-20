---
title: Açık arabirim uygulama- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 498c45ff1c5837f5dcb0d4a80d0e3bb249abd694
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589223"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="126d0-102">Açık Arabirim Uygulaması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="126d0-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="126d0-103">Bir [sınıf](../../language-reference/keywords/class.md) , aynı imzaya sahip bir üye içeren iki arabirim uygularsa, bu üyeyi sınıfında uygulamak, her iki arabirimin de uygulama olarak bu üyeyi kullanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="126d0-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="126d0-104">Aşağıdaki örnekte, tüm çağrıları aynı yöntemi çağırmak için `Paint` çağırır.</span><span class="sxs-lookup"><span data-stu-id="126d0-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#39)]  
  
 <span data-ttu-id="126d0-105">İki [arabirim](../../language-reference/keywords/interface.md) üyesi aynı işlevi gerçekleştirmez, ancak bu, arabirimlerin bir veya her ikisinin yanlış bir uygulamasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="126d0-105">If the two [interface](../../language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="126d0-106">Yalnızca arabirim aracılığıyla çağrılan ve bu arabirime özgü olan bir sınıf üyesi oluşturarak, bir arabirim üyesini açıkça uygulamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="126d0-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="126d0-107">Bu, sınıf üyesini arabirim adı ve nokta ile adlandırarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="126d0-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="126d0-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="126d0-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 <span data-ttu-id="126d0-109">Sınıf üyesi `IControl.Paint` yalnızca `IControl` arabirim aracılığıyla kullanılabilir ve `ISurface.Paint` yalnızca ile `ISurface`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="126d0-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="126d0-110">Her iki yöntem uygulaması ayrı değildir ve doğrudan sınıfta kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="126d0-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="126d0-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="126d0-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#41)]  
  
 <span data-ttu-id="126d0-112">Açık uygulama, her biri bir özellik ve bir yöntem gibi aynı ada sahip farklı Üyeler bildiren iki arabirimin da bulunduğu durumları çözümlemek için de kullanılır:</span><span class="sxs-lookup"><span data-stu-id="126d0-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 <span data-ttu-id="126d0-113">Her iki arabirimi de uygulamak için bir sınıf, derleyici hatasından kaçınmak için P ya da Yöntem P ya da her ikisi için açık uygulamayı kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="126d0-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="126d0-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="126d0-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a><span data-ttu-id="126d0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="126d0-115">See also</span></span>

- [<span data-ttu-id="126d0-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="126d0-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="126d0-117">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="126d0-117">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="126d0-118">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="126d0-118">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="126d0-119">Devralma</span><span class="sxs-lookup"><span data-stu-id="126d0-119">Inheritance</span></span>](../classes-and-structs/inheritance.md)
