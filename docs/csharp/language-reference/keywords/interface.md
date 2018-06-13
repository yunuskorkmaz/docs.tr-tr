---
title: interface (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 0320b1e287f8c7a3eb7751b68b40120f74e8f61c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266548"
---
# <a name="interface-c-reference"></a><span data-ttu-id="fc442-102">interface (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fc442-102">interface (C# Reference)</span></span>
<span data-ttu-id="fc442-103">Bir arabirim yalnızca imzalarını içerir [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md), [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [olayları](../../../csharp/programming-guide/events/index.md) veya [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="fc442-103">An interface contains only the signatures of [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [events](../../../csharp/programming-guide/events/index.md) or [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="fc442-104">Ara birimi uygulayan bir sınıfın veya yapının, ara birim tanımında belirtilen ara birim üyelerini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc442-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="fc442-105">Aşağıdaki örnekte `ImplementationClass` sınıfının, parametresi olmayan ve `SampleMethod`'i döndüren `void` adlı bir yöntemi uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc442-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>  
  
 <span data-ttu-id="fc442-106">Daha fazla bilgi ve örnekler için bkz: [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="fc442-106">For more information and examples, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc442-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc442-107">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 <span data-ttu-id="fc442-108">Ara birim, bir ad alanının veya bir sınıfın üyesi olabilir ve aşağıdaki üyelerin imzalarını içerebilir:</span><span class="sxs-lookup"><span data-stu-id="fc442-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>  
  
-   [<span data-ttu-id="fc442-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fc442-109">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="fc442-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="fc442-110">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="fc442-111">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="fc442-111">Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="fc442-112">Olaylar</span><span class="sxs-lookup"><span data-stu-id="fc442-112">Events</span></span>](../../../csharp/language-reference/keywords/event.md)  
  
 <span data-ttu-id="fc442-113">Bir ara birim, bir veya daha fazla temel ara birimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="fc442-113">An interface can inherit from one or more base interfaces.</span></span>  
  
 <span data-ttu-id="fc442-114">Bir temel tür listesi temel bir sınıfı ve ara birimleri içerdiğinde, temel sınıfın listede ilk sırada olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc442-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>  
  
 <span data-ttu-id="fc442-115">Bir ara birimi uygulayan bir sınıf, o ara birimin üyelerini açıkça uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="fc442-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="fc442-116">Açıkça uygulanan bir üyeye, bir sınıfın örneği üzerinden erişilemez, yalnızca ara birimin bir örneği üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="fc442-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>  
  
 <span data-ttu-id="fc442-117">Daha fazla ayrıntı ve açık arabirim uygulaması üzerinde kod örnekleri için bkz: [açık arabirim uygulaması](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="fc442-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc442-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc442-118">Example</span></span>  
 <span data-ttu-id="fc442-119">Aşağıdaki örnek, ara birim uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc442-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="fc442-120">Bu örnekte, ara birim özellik bildirimini, sınıf ise uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="fc442-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="fc442-121">`IPoint` öğesini uygulayan bir sınıfın herhangi bir örneği `x` ve `y` tamsayı özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fc442-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="fc442-122">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="fc442-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fc442-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc442-123">See Also</span></span>  
 [<span data-ttu-id="fc442-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fc442-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fc442-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fc442-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fc442-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fc442-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="fc442-127">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="fc442-127">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="fc442-128">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="fc442-128">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="fc442-129">Özellikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="fc442-129">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="fc442-130">Dizin Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="fc442-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [<span data-ttu-id="fc442-131">class</span><span class="sxs-lookup"><span data-stu-id="fc442-131">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="fc442-132">struct</span><span class="sxs-lookup"><span data-stu-id="fc442-132">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
 [<span data-ttu-id="fc442-133">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="fc442-133">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
