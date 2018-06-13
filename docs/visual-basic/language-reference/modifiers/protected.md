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
ms.openlocfilehash: 5f279ed0a33840bb1f2321c17a1ffba412837c07
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234763"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="d4d70-102">Korumalı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4d70-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="d4d70-103">Bir veya daha fazla programlama öğeleri bildirilen belirten bir üye erişim değiştiricisi erişilebilir yalnızca kendi sınıfı içinde veya türetilmiş bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="d4d70-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4d70-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4d70-104">Remarks</span></span>  
 <span data-ttu-id="d4d70-105">Bazen bir sınıfında tanımlanan bir programlama öğesi hassas verileri veya kısıtlı kod içeren ve öğe erişimi sınırlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="d4d70-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="d4d70-106">Ancak, sınıf devralınabilir ise ve türetilen sınıflar hiyerarşisi beklediğiniz, onu bu türetilen sınıflar veri veya kod erişmek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4d70-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="d4d70-107">Böyle bir durumda öğesi temel sınıfını hem türetilen tüm sınıflardan erişilebilir olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="d4d70-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="d4d70-108">Bu şekilde bir öğeyi erişimi sınırlamak için ile bildirebilir `Protected`.</span><span class="sxs-lookup"><span data-stu-id="d4d70-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="d4d70-109">`Protected` Erişim değiştiricisi ile iki değiştiricileri birleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="d4d70-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
> - <span data-ttu-id="d4d70-110">[Protected Friend](protected-friend.md) değiştiricisi sınıf üyesine sınıftaki, türetilen sınıflar ve sınıf tanımlanır aynı bütünleştirilmiş erişilebilir kılar.</span><span class="sxs-lookup"><span data-stu-id="d4d70-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="d4d70-111">[Özel korumalı](private-protected.md) değiştiricisi yapar sınıf üyesine erişilebilir, ancak yalnızca kendi içeren derleme içinde türetilen türlerden.</span><span class="sxs-lookup"><span data-stu-id="d4d70-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="d4d70-112">Kurallar</span><span class="sxs-lookup"><span data-stu-id="d4d70-112">Rules</span></span>  
  
-   <span data-ttu-id="d4d70-113">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="d4d70-113">**Declaration Context.**</span></span> <span data-ttu-id="d4d70-114">Kullanabileceğiniz `Protected` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="d4d70-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="d4d70-115">Bu bildirimi bağlamının anlamına gelir bir `Protected` öğesi bir sınıf olmalıdır ve bir kaynak dosyasını, ad alanı, arabirim, modülü, yapısı veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="d4d70-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="d4d70-116">Davranış</span><span class="sxs-lookup"><span data-stu-id="d4d70-116">Behavior</span></span>  
  
-   <span data-ttu-id="d4d70-117">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="d4d70-117">**Access Level.**</span></span> <span data-ttu-id="d4d70-118">Bir sınıftaki tüm kod öğeleri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="d4d70-118">All code in a class can access its elements.</span></span> <span data-ttu-id="d4d70-119">Bir taban sınıftan türetilen herhangi bir sınıf kodda tüm erişebilir `Protected` öğeleri temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="d4d70-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="d4d70-120">Bu türetme tüm nesli için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d4d70-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="d4d70-121">Bu sınıf erişebilmesini anlamına gelir `Protected` öğeleri temel sınıfın temel sınıf ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="d4d70-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="d4d70-122">Korumalı Erişim, bir üst veya alt friend erişim değil.</span><span class="sxs-lookup"><span data-stu-id="d4d70-122">Protected access is not a superset or subset of friend access.</span></span>  
  
-   <span data-ttu-id="d4d70-123">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="d4d70-123">**Access Modifiers.**</span></span> <span data-ttu-id="d4d70-124">Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*.</span><span class="sxs-lookup"><span data-stu-id="d4d70-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="d4d70-125">Erişim değiştiricileri karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d4d70-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="d4d70-126">`Protected` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d4d70-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d4d70-127">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="d4d70-128">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="d4d70-129">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="d4d70-130">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="d4d70-131">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="d4d70-132">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="d4d70-133">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="d4d70-134">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="d4d70-135">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="d4d70-136">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="d4d70-137">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="d4d70-138">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4d70-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d4d70-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4d70-139">See Also</span></span>  
 [<span data-ttu-id="d4d70-140">Public</span><span class="sxs-lookup"><span data-stu-id="d4d70-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="d4d70-141">Friend</span><span class="sxs-lookup"><span data-stu-id="d4d70-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="d4d70-142">Private</span><span class="sxs-lookup"><span data-stu-id="d4d70-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="d4d70-143">[Özel korumalı](private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="d4d70-143">[Private Protected](private-protected.md) </span></span>  
 <span data-ttu-id="d4d70-144">[Korumalı Friend](protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="d4d70-144">[Protected Friend](protected-friend.md) </span></span>  
 [<span data-ttu-id="d4d70-145">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="d4d70-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="d4d70-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d4d70-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="d4d70-147">Yapılar</span><span class="sxs-lookup"><span data-stu-id="d4d70-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="d4d70-148">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="d4d70-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
