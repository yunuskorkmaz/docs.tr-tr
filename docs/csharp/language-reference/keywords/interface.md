---
title: "interface (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: interface_CSharpKeyword
helpviewer_keywords: interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aba9ee66a90216066a47f22e251182caad465818
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="interface-c-reference"></a><span data-ttu-id="815fe-102">interface (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="815fe-102">interface (C# Reference)</span></span>
<span data-ttu-id="815fe-103">Bir arabirim yalnızca imzalarını içerir [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md), [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [olayları](../../../csharp/programming-guide/events/index.md) veya [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="815fe-103">An interface contains only the signatures of [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [events](../../../csharp/programming-guide/events/index.md) or [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="815fe-104">Ara birimi uygulayan bir sınıfın veya yapının, ara birim tanımında belirtilen ara birim üyelerini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="815fe-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="815fe-105">Aşağıdaki örnekte `ImplementationClass` sınıfının, parametresi olmayan ve `SampleMethod`'i döndüren `void` adlı bir yöntemi uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="815fe-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>  
  
 <span data-ttu-id="815fe-106">Daha fazla bilgi ve örnekler için bkz: [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="815fe-106">For more information and examples, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="815fe-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="815fe-107">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 <span data-ttu-id="815fe-108">Ara birim, bir ad alanının veya bir sınıfın üyesi olabilir ve aşağıdaki üyelerin imzalarını içerebilir:</span><span class="sxs-lookup"><span data-stu-id="815fe-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>  
  
-   [<span data-ttu-id="815fe-109">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="815fe-109">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="815fe-110">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="815fe-110">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="815fe-111">Dizin oluşturucular</span><span class="sxs-lookup"><span data-stu-id="815fe-111">Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="815fe-112">Olayları</span><span class="sxs-lookup"><span data-stu-id="815fe-112">Events</span></span>](../../../csharp/language-reference/keywords/event.md)  
  
 <span data-ttu-id="815fe-113">Bir ara birim, bir veya daha fazla temel ara birimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="815fe-113">An interface can inherit from one or more base interfaces.</span></span>  
  
 <span data-ttu-id="815fe-114">Bir temel tür listesi temel bir sınıfı ve ara birimleri içerdiğinde, temel sınıfın listede ilk sırada olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="815fe-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>  
  
 <span data-ttu-id="815fe-115">Bir ara birimi uygulayan bir sınıf, o ara birimin üyelerini açıkça uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="815fe-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="815fe-116">Açıkça uygulanan bir üyeye, bir sınıfın örneği üzerinden erişilemez, yalnızca ara birimin bir örneği üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="815fe-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>  
  
 <span data-ttu-id="815fe-117">Daha fazla ayrıntı ve açık arabirim uygulaması üzerinde kod örnekleri için bkz: [açık arabirim uygulaması](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="815fe-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="815fe-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="815fe-118">Example</span></span>  
 <span data-ttu-id="815fe-119">Aşağıdaki örnek, ara birim uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="815fe-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="815fe-120">Bu örnekte, ara birim özellik bildirimini, sınıf ise uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="815fe-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="815fe-121">`IPoint` öğesini uygulayan bir sınıfın herhangi bir örneği `x` ve `y` tamsayı özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="815fe-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="815fe-122">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="815fe-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="815fe-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="815fe-123">See Also</span></span>  
 [<span data-ttu-id="815fe-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="815fe-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="815fe-125">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="815fe-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="815fe-126">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="815fe-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="815fe-127">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="815fe-127">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="815fe-128">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="815fe-128">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="815fe-129">Özellikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="815fe-129">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="815fe-130">Dizin oluşturucular kullanma</span><span class="sxs-lookup"><span data-stu-id="815fe-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [<span data-ttu-id="815fe-131">sınıfı</span><span class="sxs-lookup"><span data-stu-id="815fe-131">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="815fe-132">yapısı</span><span class="sxs-lookup"><span data-stu-id="815fe-132">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
 [<span data-ttu-id="815fe-133">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="815fe-133">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
