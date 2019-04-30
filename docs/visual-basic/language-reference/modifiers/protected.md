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
ms.openlocfilehash: 88e13fcd03c6a10cf1450cec90f9ca60aedc3eb1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778722"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="6fc7b-102">Korumalı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fc7b-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="6fc7b-103">Bir veya daha fazla bildirilmiş programlama öğesine belirten bir üye erişim değiştiricisi erişilebilir sadece kendi sınıfı veya türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fc7b-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6fc7b-104">Remarks</span></span>  
 <span data-ttu-id="6fc7b-105">Bazen bir sınıfta bildirilen bir programlama öğesi hassas veriler ya da kısıtlı kodu içerir ve öğeye erişimi sınırlandırmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="6fc7b-106">Ancak, devralınabilir bir sınıftır ve türetilmiş sınıflarının bir hiyerarşi beklediğiniz, bunu bu türetilmiş sınıfları veri veya kod erişmek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="6fc7b-107">Böyle bir durumda, öğe temel sınıfını hem türetilen tüm sınıflardan erişilebilir olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="6fc7b-108">Bu şekilde bir öğe erişimi sınırlamak için onunla bildirebilirsiniz `Protected`.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="6fc7b-109">`Protected` Erişim değiştiricisi ile iki değiştirici birleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="6fc7b-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
> - <span data-ttu-id="6fc7b-110">[Protected Friend](protected-friend.md) değiştiricisi bir sınıf üyesi o sınıfın türetilmiş sınıflar ve sınıf tanımlanır aynı derleme içinde erişilebilir kılar.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="6fc7b-111">[Protected Private](private-protected.md) değiştiricisi yapar bir sınıf üyesinin erişilebilir derlemeyi içeren, kendi içinde ancak yalnızca türetilmiş türler tarafından.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="6fc7b-112">Kurallar</span><span class="sxs-lookup"><span data-stu-id="6fc7b-112">Rules</span></span>  
  
- <span data-ttu-id="6fc7b-113">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="6fc7b-113">**Declaration Context.**</span></span> <span data-ttu-id="6fc7b-114">Kullanabileceğiniz `Protected` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="6fc7b-115">Bildirim bağlamı başka bir deyişle bir `Protected` öğesi bir sınıf olması gerekir ve bir kaynak dosyası, ad alanı, arabirim, modülü, yapı veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="6fc7b-116">Davranış</span><span class="sxs-lookup"><span data-stu-id="6fc7b-116">Behavior</span></span>  
  
- <span data-ttu-id="6fc7b-117">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="6fc7b-117">**Access Level.**</span></span> <span data-ttu-id="6fc7b-118">Bir sınıftaki tüm kod öğelerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-118">All code in a class can access its elements.</span></span> <span data-ttu-id="6fc7b-119">Kodda bir taban sınıftan türetilen herhangi bir sınıfın tüm erişebilir `Protected` öğeleri temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="6fc7b-120">Bu türetme tüm nesiller boyunca geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="6fc7b-121">Bu sınıf erişebileceği anlamına gelir `Protected` temel sınıfın temel sınıf ve benzeri öğeleri.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="6fc7b-122">Korumalı Erişim, bir üst veya alt öğesine friend erişimi değil.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-122">Protected access is not a superset or subset of friend access.</span></span>  
  
- <span data-ttu-id="6fc7b-123">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="6fc7b-123">**Access Modifiers.**</span></span> <span data-ttu-id="6fc7b-124">Erişim düzeyini sağlayacaklarını anahtar sözcükleri adlı *erişim değiştiricilerine*.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="6fc7b-125">Erişim değiştiricileri bir karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6fc7b-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="6fc7b-126">`Protected` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="6fc7b-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6fc7b-127">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="6fc7b-128">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="6fc7b-129">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="6fc7b-130">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="6fc7b-131">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="6fc7b-132">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="6fc7b-133">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="6fc7b-134">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="6fc7b-135">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="6fc7b-136">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="6fc7b-137">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="6fc7b-138">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fc7b-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6fc7b-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fc7b-139">See also</span></span>

- [<span data-ttu-id="6fc7b-140">Public</span><span class="sxs-lookup"><span data-stu-id="6fc7b-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="6fc7b-141">Friend</span><span class="sxs-lookup"><span data-stu-id="6fc7b-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="6fc7b-142">Private</span><span class="sxs-lookup"><span data-stu-id="6fc7b-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="6fc7b-143">Private Protected</span><span class="sxs-lookup"><span data-stu-id="6fc7b-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="6fc7b-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="6fc7b-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="6fc7b-145">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="6fc7b-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="6fc7b-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="6fc7b-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="6fc7b-147">Yapılar</span><span class="sxs-lookup"><span data-stu-id="6fc7b-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6fc7b-148">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="6fc7b-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
