---
title: "Arkadaş (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df0e8ad1990fe7a1aa495e1794c942813cffb5bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="friend-visual-basic"></a><span data-ttu-id="06191-102">Arkadaş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06191-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="06191-103">Bir veya daha fazla bildirilen programlama öğeleri bildirimleri içeren bütünleştirilmiş kodun içinde yalnızca üzerinden erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="06191-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06191-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06191-104">Remarks</span></span>  
 <span data-ttu-id="06191-105">Çoğu durumda, sınıflar ve yapılar tüm derlemesi tarafından değil yalnızca bunları bildiren bileşen tarafından kullanılmak üzere gibi programlama istiyor.</span><span class="sxs-lookup"><span data-stu-id="06191-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="06191-106">Ancak, siz bunları (örneğin, uygulama özel ise) derleme dışına kodu tarafından erişilebilmesi için istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06191-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="06191-107">Bu şekilde bir öğeyi erişimi sınırlamak istiyorsanız, bunu kullanarak bildirebilirsiniz `Friend` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="06191-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="06191-108">Diğer sınıflar, yapılar ve aynı derlenmiş modüller kodda derleme tüm erişebilir `Friend` bu derleme öğeleri.</span><span class="sxs-lookup"><span data-stu-id="06191-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="06191-109">`Friend`erişim, genellikle bir uygulama programlama öğeleri için tercih edilen düzeyi ve `Friend` varsayılan erişim bir arabirim, bir modül, bir sınıf veya bir yapı düzeyinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="06191-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="06191-110">Kullanabileceğiniz `Friend` modül, arabirim veya ad alanı düzeyinde yalnızca.</span><span class="sxs-lookup"><span data-stu-id="06191-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="06191-111">Bu nedenle, bildirimi bağlamı için bir `Friend` kaynak dosyasını, bir ad alanı, bir arabirim, bir modül, bir sınıf veya bir yapı öğesi olması gerekir; bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="06191-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  
  
 <span data-ttu-id="06191-112">Kullanabileceğiniz `Friend` değiştirici ile birlikte [korumalı](../../../visual-basic/language-reference/modifiers/protected.md) aynı bildiriminde değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="06191-112">You can use the `Friend` modifier in conjunction with the [Protected](../../../visual-basic/language-reference/modifiers/protected.md) modifier in the same declaration.</span></span> <span data-ttu-id="06191-113">Bu birleşim her ikisi de confers `Friend` erişim ve bildirilen öğelerde aynı bütünleştirilmiş kodda, kendi sınıfından ve türetilmiş sınıflarından herhangi bir yerindeki erişilebilir olması için Korumalı Erişim.</span><span class="sxs-lookup"><span data-stu-id="06191-113">This combination confers both `Friend` access and protected access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="06191-114">Belirleyebileceğiniz `Protected Friend` sınıfları üyeleri yalnızca üzerinde.</span><span class="sxs-lookup"><span data-stu-id="06191-114">You can specify `Protected Friend` only on members of classes.</span></span>  
  
 <span data-ttu-id="06191-115">Bir karşılaştırması `Friend` ve diğer değiştiricileri erişmek için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="06191-115">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06191-116">Başka bir derleme tüm türleri ve olarak işaretlenmiş üyeleri erişmesine izin veren bir arkadaş derleme olduğunu belirtebilirsiniz `Friend`.</span><span class="sxs-lookup"><span data-stu-id="06191-116">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="06191-117">Daha fazla bilgi için bkz: [arkadaş derlemeleri](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="06191-117">For more information, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06191-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="06191-118">Example</span></span>  
 <span data-ttu-id="06191-119">Aşağıdaki sınıf kullanır `Friend` diğer programlama öğeleri belirli üyeleri erişmek için aynı bütünleştirilmiş kod içinde izin vermek için değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="06191-119">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="06191-120">Kullanım</span><span class="sxs-lookup"><span data-stu-id="06191-120">Usage</span></span>  
 <span data-ttu-id="06191-121">Kullanabileceğiniz `Friend` bu bağlamlarında değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="06191-121">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="06191-122">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="06191-123">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="06191-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="06191-125">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="06191-126">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="06191-127">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="06191-128">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="06191-129">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="06191-130">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="06191-131">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="06191-132">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-132">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="06191-133">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-133">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="06191-134">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="06191-134">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="06191-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06191-135">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="06191-136">Public</span><span class="sxs-lookup"><span data-stu-id="06191-136">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="06191-137">Protected</span><span class="sxs-lookup"><span data-stu-id="06191-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="06191-138">Private</span><span class="sxs-lookup"><span data-stu-id="06191-138">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="06191-139">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="06191-139">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="06191-140">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="06191-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="06191-141">Yapılar</span><span class="sxs-lookup"><span data-stu-id="06191-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="06191-142">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="06191-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
