---
title: Arkadaş (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: d906fc8ada19f22059da44acbd76dd07dacd4801
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234595"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="f879d-102">Arkadaş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f879d-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="f879d-103">Bir veya daha fazla bildirilen programlama öğeleri bildirimleri içeren bütünleştirilmiş kodun içinde yalnızca üzerinden erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f879d-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f879d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f879d-104">Remarks</span></span>  
 <span data-ttu-id="f879d-105">Çoğu durumda, sınıflar ve yapılar tüm derlemesi tarafından değil yalnızca bunları bildiren bileşen tarafından kullanılmak üzere gibi programlama istiyor.</span><span class="sxs-lookup"><span data-stu-id="f879d-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="f879d-106">Ancak, siz bunları (örneğin, uygulama özel ise) derleme dışına kodu tarafından erişilebilmesi için istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f879d-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="f879d-107">Bu şekilde bir öğeyi erişimi sınırlamak istiyorsanız, bunu kullanarak bildirebilirsiniz `Friend` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="f879d-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="f879d-108">Diğer sınıflar, yapılar ve aynı derlenmiş modüller kodda derleme tüm erişebilir `Friend` bu derleme öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f879d-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="f879d-109">`Friend` erişim, genellikle bir uygulama programlama öğeleri için tercih edilen düzeyi ve `Friend` varsayılan erişim bir arabirim, bir modül, bir sınıf veya bir yapı düzeyinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f879d-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="f879d-110">Kullanabileceğiniz `Friend` modül, arabirim veya ad alanı düzeyinde yalnızca.</span><span class="sxs-lookup"><span data-stu-id="f879d-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="f879d-111">Bu nedenle, bildirimi bağlamı için bir `Friend` kaynak dosyasını, bir ad alanı, bir arabirim, bir modül, bir sınıf veya bir yapı öğesi olması gerekir; bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="f879d-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="f879d-112">Aynı zamanda [Protected Friend](protected-friend.md) sınıf üyesine bir sınıftaki, türetilen sınıflar ve sınıf tanımlanır aynı bütünleştirilmiş erişilebilir hale getirir erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="f879d-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="f879d-113">Kendi sınıfı içinde ve aynı bütünleştirilmiş kodda türetilmiş sınıflardan üyeden erişimi kısıtlamak için kullandığınız [özel korumalı](private-protected.md) erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="f879d-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="f879d-114">Bir karşılaştırması `Friend` ve diğer değiştiricileri erişmek için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f879d-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f879d-115">Başka bir derleme tüm türleri ve olarak işaretlenmiş üyeleri erişmesine izin veren bir arkadaş derleme olduğunu belirtebilirsiniz `Friend`.</span><span class="sxs-lookup"><span data-stu-id="f879d-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="f879d-116">Daha fazla bilgi için bkz: [arkadaş derlemeleri](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="f879d-116">For more information, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f879d-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="f879d-117">Example</span></span>  
 <span data-ttu-id="f879d-118">Aşağıdaki sınıf kullanır `Friend` diğer programlama öğeleri belirli üyeleri erişmek için aynı bütünleştirilmiş kod içinde izin vermek için değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="f879d-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="f879d-119">Kullanım</span><span class="sxs-lookup"><span data-stu-id="f879d-119">Usage</span></span>  
 <span data-ttu-id="f879d-120">Kullanabileceğiniz `Friend` bu bağlamlarında değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="f879d-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="f879d-121">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="f879d-122">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="f879d-123">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="f879d-124">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="f879d-125">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="f879d-126">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="f879d-127">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="f879d-128">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="f879d-129">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="f879d-130">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="f879d-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="f879d-132">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="f879d-133">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="f879d-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f879d-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f879d-134">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="f879d-135">Public</span><span class="sxs-lookup"><span data-stu-id="f879d-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="f879d-136">Protected</span><span class="sxs-lookup"><span data-stu-id="f879d-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="f879d-137">Private</span><span class="sxs-lookup"><span data-stu-id="f879d-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="f879d-138">[Özel korumalı](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="f879d-138">[Private Protected](./private-protected.md) </span></span>  
 <span data-ttu-id="f879d-139">[Korumalı Friend](./protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="f879d-139">[Protected Friend](./protected-friend.md) </span></span>  
 [<span data-ttu-id="f879d-140">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="f879d-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="f879d-141">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f879d-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="f879d-142">Yapılar</span><span class="sxs-lookup"><span data-stu-id="f879d-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="f879d-143">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="f879d-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
