---
title: Açık Arabirim Uygulaması (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 7494f7d6a3897d56419f9d3aa96668fd9dab5f35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331597"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="3746a-102">Açık Arabirim Uygulaması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3746a-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="3746a-103">Varsa bir [sınıfı](../../../csharp/language-reference/keywords/class.md) bu üye sınıfını uygulama bu üye olarak kendi uygulaması kullanmak her iki arabirimde neden olmaz üyesi aynı imzayla içeren iki arabirimlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="3746a-103">If a [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="3746a-104">Aşağıdaki örnekte, tüm çağrıları `Paint` aynı yöntemini çağırma.</span><span class="sxs-lookup"><span data-stu-id="3746a-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 <span data-ttu-id="3746a-105">İki [arabirimi](../../../csharp/language-reference/keywords/interface.md) üyeleri aynı işlevi gerçekleştirmez, ancak bu birini veya her ikisini arabirimler yanlış uygulaması için yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="3746a-105">If the two [interface](../../../csharp/language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="3746a-106">Arabirim üyesini açıkça uygulama mümkündür — bir sınıf üyesi oluşturmayı yalnızca arabirimi aracılığıyla çağrılır ve bu arabirim için özeldir.</span><span class="sxs-lookup"><span data-stu-id="3746a-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="3746a-107">Bu sınıf üyesi süre ve arabirim adı ile adlandırma tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3746a-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="3746a-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3746a-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 <span data-ttu-id="3746a-109">Sınıf üyesi `IControl.Paint` aracılığıyla yalnızca kullanılabilir `IControl` arabirimi ve `ISurface.Paint` aracılığıyla yalnızca kullanılabilir `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="3746a-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="3746a-110">Her iki yöntem uygulamalarını ayrıdır ve ikisi sınıfında doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3746a-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="3746a-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3746a-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 <span data-ttu-id="3746a-112">Açık uygulama burada iki arabirim aynı adlı bir özellik ve yöntemi gibi farklı üyeleri bildirme durumları çözümlemek için de kullanılır:</span><span class="sxs-lookup"><span data-stu-id="3746a-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 <span data-ttu-id="3746a-113">Her iki arabirimde uygulamak için bir sınıf derleyici hatası önlemek için açık uygulama P özelliği veya yöntemi P için veya her ikisini de kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3746a-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="3746a-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3746a-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3746a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3746a-115">See Also</span></span>  
 [<span data-ttu-id="3746a-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3746a-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3746a-117">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="3746a-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="3746a-118">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="3746a-118">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="3746a-119">Devralma</span><span class="sxs-lookup"><span data-stu-id="3746a-119">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
