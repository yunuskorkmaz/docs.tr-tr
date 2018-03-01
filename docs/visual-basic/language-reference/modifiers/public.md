---
title: Public (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6cd70adf6ec31c56f39d0443d320dd1b00b00d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="public-visual-basic"></a><span data-ttu-id="651c8-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="651c8-102">Public (Visual Basic)</span></span>
<span data-ttu-id="651c8-103">Bir veya daha fazla bildirilen programlama öğeleri hiçbir erişim kısıtlaması olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="651c8-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="651c8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="651c8-104">Remarks</span></span>  
 <span data-ttu-id="651c8-105">Bir bileşeni ya da bir sınıf kitaplığı gibi bir bileşen kümesi yayımlıyorsanız programlama öğeleri ile derlemenizi çalıştığı herhangi bir kod tarafından erişilebilir olması için genellikle istiyor.</span><span class="sxs-lookup"><span data-stu-id="651c8-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="651c8-106">Bu tür bir öğe üzerinde sınırsız erişimi confer için ile bildirebilir `Public`.</span><span class="sxs-lookup"><span data-stu-id="651c8-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="651c8-107">Genel erişim bir programlama öğesi için normal düzeyi olduğunda erişimi sınırlamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="651c8-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="651c8-108">Erişim düzeyi, bir öğenin bir arabirim, modülü, sınıf veya yapı içinde bildirilen Not Varsayılan olarak `Public` , aksi takdirde değil bildirirseniz.</span><span class="sxs-lookup"><span data-stu-id="651c8-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="651c8-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="651c8-109">Rules</span></span>  
  
-   <span data-ttu-id="651c8-110">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="651c8-110">**Declaration Context.**</span></span> <span data-ttu-id="651c8-111">Kullanabileceğiniz `Public` yalnızca düzeyinde modül, arabirim veya ad alanı.</span><span class="sxs-lookup"><span data-stu-id="651c8-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="651c8-112">Bu bildirimi bağlamının anlamına gelir bir `Public` öğesi bir kaynak dosya, ad alanı, arabirimi, modülü, sınıf veya yapı olmalıdır ve bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="651c8-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="651c8-113">Davranış</span><span class="sxs-lookup"><span data-stu-id="651c8-113">Behavior</span></span>  
  
-   <span data-ttu-id="651c8-114">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="651c8-114">**Access Level.**</span></span> <span data-ttu-id="651c8-115">Bir modül, sınıf veya yapı erişebilen tüm kod erişmek için kendi `Public` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="651c8-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
-   <span data-ttu-id="651c8-116">**Varsayılan erişim.**</span><span class="sxs-lookup"><span data-stu-id="651c8-116">**Default Access.**</span></span> <span data-ttu-id="651c8-117">Yerel değişkenler bir yordam varsayılan genel erişim ve içindeki tüm erişim değiştiricileri üzerlerinde kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="651c8-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
-   <span data-ttu-id="651c8-118">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="651c8-118">**Access Modifiers.**</span></span> <span data-ttu-id="651c8-119">Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*.</span><span class="sxs-lookup"><span data-stu-id="651c8-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="651c8-120">Erişim değiştiricileri karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="651c8-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="651c8-121">`Public` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="651c8-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="651c8-122">Class deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="651c8-123">Const deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="651c8-124">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="651c8-125">Delegate deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="651c8-126">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="651c8-127">Enum deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="651c8-128">Event deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="651c8-129">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="651c8-130">Interface deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="651c8-131">Module deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="651c8-132">Operator deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="651c8-133">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="651c8-134">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="651c8-135">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="651c8-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="651c8-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="651c8-136">See Also</span></span>  
 [<span data-ttu-id="651c8-137">Korumalı</span><span class="sxs-lookup"><span data-stu-id="651c8-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="651c8-138">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="651c8-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="651c8-139">Özel</span><span class="sxs-lookup"><span data-stu-id="651c8-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="651c8-140">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="651c8-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="651c8-141">Yordamları</span><span class="sxs-lookup"><span data-stu-id="651c8-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="651c8-142">Yapıları</span><span class="sxs-lookup"><span data-stu-id="651c8-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="651c8-143">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="651c8-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
