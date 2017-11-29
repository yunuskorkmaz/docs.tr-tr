---
title: "Açık Arabirim Uygulaması (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b746a69484b73a4212c729e02a1256ee1c83ea41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="e55f2-102">Açık Arabirim Uygulaması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e55f2-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="e55f2-103">Varsa bir [sınıfı](../../../csharp/language-reference/keywords/class.md) bu üye sınıfını uygulama bu üye olarak kendi uygulaması kullanmak her iki arabirimde neden olmaz üyesi aynı imzayla içeren iki arabirimlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="e55f2-103">If a [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="e55f2-104">Aşağıdaki örnekte, tüm çağrıları `Paint` aynı yöntemini çağırma.</span><span class="sxs-lookup"><span data-stu-id="e55f2-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 <span data-ttu-id="e55f2-105">İki [arabirimi](../../../csharp/language-reference/keywords/interface.md) üyeleri aynı işlevi gerçekleştirmez, ancak bu birini veya her ikisini arabirimler yanlış uygulaması için yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="e55f2-105">If the two [interface](../../../csharp/language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="e55f2-106">Arabirim üyesini açıkça uygulama mümkündür — bir sınıf üyesi oluşturmayı yalnızca arabirimi aracılığıyla çağrılır ve bu arabirim için özeldir.</span><span class="sxs-lookup"><span data-stu-id="e55f2-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="e55f2-107">Bu sınıf üyesi süre ve arabirim adı ile adlandırma tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e55f2-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="e55f2-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e55f2-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 <span data-ttu-id="e55f2-109">Sınıf üyesi `IControl.Paint` aracılığıyla yalnızca kullanılabilir `IControl` arabirimi ve `ISurface.Paint` aracılığıyla yalnızca kullanılabilir `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="e55f2-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="e55f2-110">Her iki yöntem uygulamalarını ayrıdır ve ikisi sınıfında doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e55f2-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="e55f2-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e55f2-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 <span data-ttu-id="e55f2-112">Açık uygulama burada iki arabirim aynı adlı bir özellik ve yöntemi gibi farklı üyeleri bildirme durumları çözümlemek için de kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e55f2-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 <span data-ttu-id="e55f2-113">Her iki arabirimde uygulamak için bir sınıf derleyici hatası önlemek için açık uygulama P özelliği veya yöntemi P için veya her ikisini de kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e55f2-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="e55f2-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e55f2-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e55f2-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e55f2-115">See Also</span></span>  
 [<span data-ttu-id="e55f2-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e55f2-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e55f2-117">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="e55f2-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="e55f2-118">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e55f2-118">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="e55f2-119">Devralma</span><span class="sxs-lookup"><span data-stu-id="e55f2-119">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
