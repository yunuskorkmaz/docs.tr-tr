---
title: "Korumalı (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0cc7a0cb626a9ec8e2a0e47abc02e5268aed56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="protected-visual-basic"></a><span data-ttu-id="df184-102">Korumalı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df184-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="df184-103">Bir veya daha fazla bildirilen programlama öğeleri erişilebilir yalnızca kendi sınıfı içinde veya türetilmiş bir sınıf olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="df184-103">Specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df184-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df184-104">Remarks</span></span>  
 <span data-ttu-id="df184-105">Bazen bir sınıfında tanımlanan bir programlama öğesi hassas verileri veya kısıtlı kod içeren ve öğe erişimi sınırlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="df184-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="df184-106">Ancak, sınıf devralınabilir ise ve türetilen sınıflar hiyerarşisi beklediğiniz, onu bu türetilen sınıflar veri veya kod erişmek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="df184-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="df184-107">Böyle bir durumda öğesi temel sınıfını hem türetilen tüm sınıflardan erişilebilir olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="df184-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="df184-108">Bu şekilde bir öğeyi erişimi sınırlamak için ile bildirebilir `Protected`.</span><span class="sxs-lookup"><span data-stu-id="df184-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="df184-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="df184-109">Rules</span></span>  
  
-   <span data-ttu-id="df184-110">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="df184-110">**Declaration Context.**</span></span> <span data-ttu-id="df184-111">Kullanabileceğiniz `Protected` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="df184-111">You can use `Protected` only at class level.</span></span> <span data-ttu-id="df184-112">Bu bildirimi bağlamının anlamına gelir bir `Protected` öğesi bir sınıf olmalıdır ve bir kaynak dosyasını, ad alanı, arabirim, modülü, yapısı veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="df184-112">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
-   <span data-ttu-id="df184-113">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="df184-113">**Combined Modifiers.**</span></span> <span data-ttu-id="df184-114">Kullanabileceğiniz `Protected` değiştirici ile birlikte [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) aynı bildiriminde değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="df184-114">You can use the `Protected` modifier together with the [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modifier in the same declaration.</span></span> <span data-ttu-id="df184-115">Bu birleşim bildirilen öğeler aynı bütünleştirilmiş kodda, kendi sınıfından ve türetilmiş sınıflarından herhangi bir yerindeki erişilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="df184-115">This combination makes the declared elements accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="df184-116">Belirleyebileceğiniz `Protected Friend` sınıfları üyeleri yalnızca üzerinde.</span><span class="sxs-lookup"><span data-stu-id="df184-116">You can specify `Protected Friend` only on members of classes.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="df184-117">Davranış</span><span class="sxs-lookup"><span data-stu-id="df184-117">Behavior</span></span>  
  
-   <span data-ttu-id="df184-118">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="df184-118">**Access Level.**</span></span> <span data-ttu-id="df184-119">Bir sınıftaki tüm kod öğeleri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="df184-119">All code in a class can access its elements.</span></span> <span data-ttu-id="df184-120">Bir taban sınıftan türetilen herhangi bir sınıf kodda tüm erişebilir `Protected` öğeleri temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="df184-120">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="df184-121">Bu türetme tüm nesli için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="df184-121">This is true for all generations of derivation.</span></span> <span data-ttu-id="df184-122">Bu sınıf erişebilmesini anlamına gelir `Protected` öğeleri temel sınıfın temel sınıf ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="df184-122">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="df184-123">Korumalı Erişim, bir üst veya alt friend erişim değil.</span><span class="sxs-lookup"><span data-stu-id="df184-123">Protected access is not a superset or subset of friend access.</span></span>  
  
-   <span data-ttu-id="df184-124">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="df184-124">**Access Modifiers.**</span></span> <span data-ttu-id="df184-125">Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*.</span><span class="sxs-lookup"><span data-stu-id="df184-125">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="df184-126">Erişim değiştiricileri karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="df184-126">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="df184-127">`Protected` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="df184-127">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="df184-128">Class deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="df184-129">Const deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="df184-130">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="df184-131">Delegate deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="df184-132">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="df184-133">Enum deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="df184-134">Event deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="df184-135">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="df184-136">Interface deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="df184-137">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="df184-138">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="df184-139">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="df184-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="df184-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df184-140">See Also</span></span>  
 [<span data-ttu-id="df184-141">Ortak</span><span class="sxs-lookup"><span data-stu-id="df184-141">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="df184-142">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="df184-142">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="df184-143">Özel</span><span class="sxs-lookup"><span data-stu-id="df184-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="df184-144">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="df184-144">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="df184-145">Yordamları</span><span class="sxs-lookup"><span data-stu-id="df184-145">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="df184-146">Yapıları</span><span class="sxs-lookup"><span data-stu-id="df184-146">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="df184-147">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="df184-147">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
