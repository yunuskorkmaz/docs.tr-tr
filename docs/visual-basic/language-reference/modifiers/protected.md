---
title: Korumalı (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 86758c68f0f3bfe214a695f656d3924eadd27e31
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642680"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="777bd-102">Korumalı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="777bd-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="777bd-103">Bir veya daha fazla bildirilmiş programlama öğesine belirten bir üye erişim değiştiricisi erişilebilir sadece kendi sınıfı veya türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="777bd-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="777bd-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="777bd-104">Remarks</span></span>  
 <span data-ttu-id="777bd-105">Bazen bir sınıfta bildirilen bir programlama öğesi hassas veriler ya da kısıtlı kodu içerir ve öğeye erişimi sınırlandırmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="777bd-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="777bd-106">Ancak, devralınabilir bir sınıftır ve türetilmiş sınıflarının bir hiyerarşi beklediğiniz, bunu bu türetilmiş sınıfları veri veya kod erişmek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="777bd-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="777bd-107">Böyle bir durumda, öğe temel sınıfını hem türetilen tüm sınıflardan erişilebilir olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="777bd-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="777bd-108">Bu şekilde bir öğe erişimi sınırlamak için onunla bildirebilirsiniz `Protected`.</span><span class="sxs-lookup"><span data-stu-id="777bd-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="777bd-109">`Protected` Erişim değiştiricisi ile iki değiştirici birleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="777bd-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
> - <span data-ttu-id="777bd-110">[Protected Friend](protected-friend.md) değiştiricisi bir sınıf üyesi o sınıfın türetilmiş sınıflar ve sınıf tanımlanır aynı derleme içinde erişilebilir kılar.</span><span class="sxs-lookup"><span data-stu-id="777bd-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="777bd-111">[Protected Private](private-protected.md) değiştiricisi yapar bir sınıf üyesinin erişilebilir derlemeyi içeren, kendi içinde ancak yalnızca türetilmiş türler tarafından.</span><span class="sxs-lookup"><span data-stu-id="777bd-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="777bd-112">Kurallar</span><span class="sxs-lookup"><span data-stu-id="777bd-112">Rules</span></span>  
  
- <span data-ttu-id="777bd-113">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="777bd-113">**Declaration Context.**</span></span> <span data-ttu-id="777bd-114">Kullanabileceğiniz `Protected` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="777bd-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="777bd-115">Bildirim bağlamı başka bir deyişle bir `Protected` öğesi bir sınıf olması gerekir ve bir kaynak dosyası, ad alanı, arabirim, modülü, yapı veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="777bd-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="777bd-116">Davranış</span><span class="sxs-lookup"><span data-stu-id="777bd-116">Behavior</span></span>  
  
- <span data-ttu-id="777bd-117">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="777bd-117">**Access Level.**</span></span> <span data-ttu-id="777bd-118">Bir sınıftaki tüm kod öğelerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="777bd-118">All code in a class can access its elements.</span></span> <span data-ttu-id="777bd-119">Kodda bir taban sınıftan türetilen herhangi bir sınıfın tüm erişebilir `Protected` öğeleri temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="777bd-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="777bd-120">Bu türetme tüm nesiller boyunca geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="777bd-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="777bd-121">Bu sınıf erişebileceği anlamına gelir `Protected` temel sınıfın temel sınıf ve benzeri öğeleri.</span><span class="sxs-lookup"><span data-stu-id="777bd-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="777bd-122">Korumalı Erişim, bir üst veya alt öğesine friend erişimi değil.</span><span class="sxs-lookup"><span data-stu-id="777bd-122">Protected access is not a superset or subset of friend access.</span></span>  
  
- <span data-ttu-id="777bd-123">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="777bd-123">**Access Modifiers.**</span></span> <span data-ttu-id="777bd-124">Erişim düzeyini sağlayacaklarını anahtar sözcükleri adlı *erişim değiştiricilerine*.</span><span class="sxs-lookup"><span data-stu-id="777bd-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="777bd-125">Erişim değiştiricileri bir karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="777bd-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="777bd-126">`Protected` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="777bd-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="777bd-127">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="777bd-128">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="777bd-129">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="777bd-130">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="777bd-131">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="777bd-132">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="777bd-133">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="777bd-134">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="777bd-135">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="777bd-136">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="777bd-137">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="777bd-138">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="777bd-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="777bd-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="777bd-139">See also</span></span>

- [<span data-ttu-id="777bd-140">Public</span><span class="sxs-lookup"><span data-stu-id="777bd-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="777bd-141">Friend</span><span class="sxs-lookup"><span data-stu-id="777bd-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="777bd-142">Private</span><span class="sxs-lookup"><span data-stu-id="777bd-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="777bd-143">Private Protected</span><span class="sxs-lookup"><span data-stu-id="777bd-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="777bd-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="777bd-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="777bd-145">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="777bd-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="777bd-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="777bd-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="777bd-147">Yapılar</span><span class="sxs-lookup"><span data-stu-id="777bd-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="777bd-148">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="777bd-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
