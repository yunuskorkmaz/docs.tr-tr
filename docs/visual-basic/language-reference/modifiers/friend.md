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
ms.openlocfilehash: 3e30267c8aa11ce97b3b3064ff0954378dab57af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959810"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="ab440-102">Arkadaş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab440-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="ab440-103">Bir veya daha fazla tanımlanmış programlama öğesine, yalnızca bildirimini içeren derlemenin içinden erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab440-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab440-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab440-104">Remarks</span></span>  
 <span data-ttu-id="ab440-105">Çoğu durumda, sınıflar ve yapılar gibi programlama öğelerinin, yalnızca bunları bildiren bileşen tarafından değil, tüm derleme tarafından kullanılmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="ab440-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="ab440-106">Ancak, bunların derleme dışındaki kod tarafından erişilebilmesini istemeyebilirsiniz (örneğin, uygulama özel ise).</span><span class="sxs-lookup"><span data-stu-id="ab440-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="ab440-107">Bu şekilde bir öğeye erişimi sınırlandırmak istiyorsanız, `Friend` değiştiricisini kullanarak bunu bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab440-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="ab440-108">Aynı derlemeye derlenen diğer sınıf, yapı ve modüllerindeki kod, bu derlemedeki tüm `Friend` öğelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="ab440-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="ab440-109">`Friend`erişim genellikle bir uygulamanın programlama öğeleri için tercih edilen düzeydir ve `Friend` bir arabirimin, modülün, sınıfın veya yapının varsayılan erişim düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="ab440-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="ab440-110">Yalnızca modül, `Friend` arabirim veya ad alanı düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab440-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="ab440-111">Bu nedenle, bir `Friend` öğe için bildirim bağlamı bir kaynak dosyası, bir ad alanı, arabirim, bir modül, sınıf veya yapı olmalıdır; bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="ab440-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="ab440-112">Ayrıca, bir sınıf üyesini bu sınıftan, türetilmiş sınıflardan ve sınıfın tanımlandığı aynı derlemeden erişilebilir hale getiren [Protected Friend](protected-friend.md) erişim değiştiricisini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab440-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="ab440-113">Bir üyenin sınıfından ve aynı derlemede bulunan türetilmiş sınıflardan erişimi kısıtlamak için, [özel korumalı](private-protected.md) erişim değiştiricisini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ab440-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="ab440-114">`Friend` Ve diğer erişim değiştiricilerine ilişkin bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ab440-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab440-115">Başka bir derlemenin, olarak `Friend`işaretlenen tüm türlere ve üyelere erişmesine izin veren bir Friend derlemesi olduğunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab440-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="ab440-116">Daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ab440-116">For more information, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab440-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab440-117">Example</span></span>  
 <span data-ttu-id="ab440-118">Aşağıdaki sınıf, aynı derleme `Friend` içindeki diğer programlama öğelerinin belirli üyelere erişmesine izin vermek için değiştiricisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab440-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="ab440-119">Kullanım</span><span class="sxs-lookup"><span data-stu-id="ab440-119">Usage</span></span>  
 <span data-ttu-id="ab440-120">`Friend` Değiştiricisini şu bağlamlarda kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ab440-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="ab440-121">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="ab440-122">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="ab440-123">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="ab440-124">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="ab440-125">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="ab440-126">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="ab440-127">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="ab440-128">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="ab440-129">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="ab440-130">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="ab440-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="ab440-132">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="ab440-133">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab440-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ab440-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab440-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="ab440-135">Public</span><span class="sxs-lookup"><span data-stu-id="ab440-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="ab440-136">Protected</span><span class="sxs-lookup"><span data-stu-id="ab440-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="ab440-137">Private</span><span class="sxs-lookup"><span data-stu-id="ab440-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="ab440-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="ab440-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="ab440-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="ab440-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="ab440-140">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="ab440-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="ab440-141">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ab440-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="ab440-142">Yapılar</span><span class="sxs-lookup"><span data-stu-id="ab440-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ab440-143">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="ab440-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
