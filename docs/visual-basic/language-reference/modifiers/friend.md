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
ms.openlocfilehash: 18681935d0380f9be3970fdb5d17ffb089152f59
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819157"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="f9f29-102">Arkadaş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9f29-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="f9f29-103">Bir veya daha fazla bildirilmiş programlama öğesine, bildirimi içeren derlemede yalnızca erişilebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9f29-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9f29-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9f29-104">Remarks</span></span>  
 <span data-ttu-id="f9f29-105">Çoğu durumda, sınıflar ve yapılar yalnızca bunları bildiren bileşen tarafından tüm derleme tarafından kullanılacak gibi öğeleri programlama istersiniz.</span><span class="sxs-lookup"><span data-stu-id="f9f29-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="f9f29-106">Ancak, bunları (örneğin, uygulama özel ise) derleme dışındaki kod tarafından erişilebilmesi için istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9f29-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="f9f29-107">Bu şekilde bir öğe erişimi sınırlandırmak istiyorsanız, bunu kullanarak bildirebilirsiniz `Friend` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="f9f29-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="f9f29-108">Diğer sınıflar, yapılar ve aynı derlenmiş modüller kodda derleme tüm erişebilir `Friend` derlemeye öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f9f29-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="f9f29-109">`Friend` erişim, genellikle uygulamanın programlama öğeleri için tercih edilen düzeyi ve `Friend` varsayılan bir arabirim, bir modül, bir sınıf veya yapı düzeyi erişimdir.</span><span class="sxs-lookup"><span data-stu-id="f9f29-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="f9f29-110">Kullanabileceğiniz `Friend` modülü, arabirim veya ad alanı düzeyinde yalnızca.</span><span class="sxs-lookup"><span data-stu-id="f9f29-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="f9f29-111">Bu nedenle, bildirimi bağlamı bir `Friend` öğesi bir kaynak dosyası, bir ad alanı, bir arabirim, bir modül, bir sınıf veya yapı olmalıdır; bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="f9f29-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="f9f29-112">Ayrıca [Protected Friend](protected-friend.md) erişim değiştiricisi, bir sınıf üyesinin Bu sınıf, türetilen sınıflar ve sınıf tanımlanır aynı derleme içinde erişilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f9f29-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="f9f29-113">Sınıfı içinde ve türetilen sınıfların aynı derlemedeki bir üye erişimi kısıtlamak için kullandığınız [Protected Private](private-protected.md) erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="f9f29-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="f9f29-114">Bir karşılaştırması `Friend` ve diğer erişim değiştiricilerine bkz [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f9f29-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9f29-115">Başka bir derlemenin tüm türleri ve üyeleri olarak işaretlenmiş erişmesine izin veren bir arkadaş derleme olduğunu belirtebilirsiniz `Friend`.</span><span class="sxs-lookup"><span data-stu-id="f9f29-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="f9f29-116">Daha fazla bilgi için [arkadaş derlemeleri](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="f9f29-116">For more information, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9f29-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9f29-117">Example</span></span>  
 <span data-ttu-id="f9f29-118">Aşağıdaki sınıf kullandığı `Friend` diğer programlama öğelerinin belirli üyelere erişmek için aynı bütünleştirilmiş kod içinde değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="f9f29-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="f9f29-119">Kullanım</span><span class="sxs-lookup"><span data-stu-id="f9f29-119">Usage</span></span>  
 <span data-ttu-id="f9f29-120">Kullanabileceğiniz `Friend` şu bağlamlarda değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="f9f29-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="f9f29-121">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="f9f29-122">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="f9f29-123">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="f9f29-124">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="f9f29-125">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="f9f29-126">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="f9f29-127">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="f9f29-128">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="f9f29-129">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="f9f29-130">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="f9f29-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="f9f29-132">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="f9f29-133">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="f9f29-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f9f29-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9f29-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="f9f29-135">Public</span><span class="sxs-lookup"><span data-stu-id="f9f29-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="f9f29-136">Protected</span><span class="sxs-lookup"><span data-stu-id="f9f29-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="f9f29-137">Private</span><span class="sxs-lookup"><span data-stu-id="f9f29-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="f9f29-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="f9f29-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="f9f29-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="f9f29-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="f9f29-140">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="f9f29-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="f9f29-141">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f9f29-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="f9f29-142">Yapılar</span><span class="sxs-lookup"><span data-stu-id="f9f29-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="f9f29-143">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="f9f29-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
