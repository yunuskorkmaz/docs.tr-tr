---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: a5e9161132ba6d571daa30ce82e1bfb1dd2b064f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="public-visual-basic"></a><span data-ttu-id="b0d06-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0d06-102">Public (Visual Basic)</span></span>
<span data-ttu-id="b0d06-103">Bir veya daha fazla bildirilen programlama öğeleri hiçbir erişim kısıtlaması olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0d06-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0d06-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0d06-104">Remarks</span></span>  
 <span data-ttu-id="b0d06-105">Bir bileşeni ya da bir sınıf kitaplığı gibi bir bileşen kümesi yayımlıyorsanız programlama öğeleri ile derlemenizi çalıştığı herhangi bir kod tarafından erişilebilir olması için genellikle istiyor.</span><span class="sxs-lookup"><span data-stu-id="b0d06-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="b0d06-106">Bu tür bir öğe üzerinde sınırsız erişimi confer için ile bildirebilir `Public`.</span><span class="sxs-lookup"><span data-stu-id="b0d06-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="b0d06-107">Genel erişim bir programlama öğesi için normal düzeyi olduğunda erişimi sınırlamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b0d06-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="b0d06-108">Erişim düzeyi, bir öğenin bir arabirim, modülü, sınıf veya yapı içinde bildirilen Not Varsayılan olarak `Public` , aksi takdirde değil bildirirseniz.</span><span class="sxs-lookup"><span data-stu-id="b0d06-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b0d06-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="b0d06-109">Rules</span></span>  
  
-   <span data-ttu-id="b0d06-110">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="b0d06-110">**Declaration Context.**</span></span> <span data-ttu-id="b0d06-111">Kullanabileceğiniz `Public` yalnızca düzeyinde modül, arabirim veya ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b0d06-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="b0d06-112">Bu bildirimi bağlamının anlamına gelir bir `Public` öğesi bir kaynak dosya, ad alanı, arabirimi, modülü, sınıf veya yapı olmalıdır ve bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="b0d06-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="b0d06-113">Davranış</span><span class="sxs-lookup"><span data-stu-id="b0d06-113">Behavior</span></span>  
  
-   <span data-ttu-id="b0d06-114">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="b0d06-114">**Access Level.**</span></span> <span data-ttu-id="b0d06-115">Bir modül, sınıf veya yapı erişebilen tüm kod erişmek için kendi `Public` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b0d06-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
-   <span data-ttu-id="b0d06-116">**Varsayılan erişim.**</span><span class="sxs-lookup"><span data-stu-id="b0d06-116">**Default Access.**</span></span> <span data-ttu-id="b0d06-117">Yerel değişkenler bir yordam varsayılan genel erişim ve içindeki tüm erişim değiştiricileri üzerlerinde kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b0d06-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
-   <span data-ttu-id="b0d06-118">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="b0d06-118">**Access Modifiers.**</span></span> <span data-ttu-id="b0d06-119">Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*.</span><span class="sxs-lookup"><span data-stu-id="b0d06-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="b0d06-120">Erişim değiştiricileri karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b0d06-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="b0d06-121">`Public` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b0d06-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="b0d06-122">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="b0d06-123">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="b0d06-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="b0d06-125">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="b0d06-126">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="b0d06-127">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="b0d06-128">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="b0d06-129">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="b0d06-130">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="b0d06-131">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="b0d06-132">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="b0d06-133">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="b0d06-134">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="b0d06-135">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0d06-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b0d06-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b0d06-136">See Also</span></span>  
 [<span data-ttu-id="b0d06-137">Protected</span><span class="sxs-lookup"><span data-stu-id="b0d06-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="b0d06-138">Friend</span><span class="sxs-lookup"><span data-stu-id="b0d06-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="b0d06-139">Private</span><span class="sxs-lookup"><span data-stu-id="b0d06-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="b0d06-140">[Özel korumalı](private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="b0d06-140">[Private Protected](private-protected.md) </span></span>  
 <span data-ttu-id="b0d06-141">[Korumalı Friend](protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="b0d06-141">[Protected Friend](protected-friend.md) </span></span>  
 [<span data-ttu-id="b0d06-142">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="b0d06-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="b0d06-143">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b0d06-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="b0d06-144">Yapılar</span><span class="sxs-lookup"><span data-stu-id="b0d06-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="b0d06-145">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b0d06-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
