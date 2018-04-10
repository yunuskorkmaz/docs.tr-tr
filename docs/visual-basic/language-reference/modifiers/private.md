---
title: Özel (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07450c2a5443bf6bc147cad2cfc779072bfc363b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="private-visual-basic"></a><span data-ttu-id="ff28d-102">Özel (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff28d-102">Private (Visual Basic)</span></span>
<span data-ttu-id="ff28d-103">Bir veya daha fazla bildirilen programlama öğeleri dahil tüm kapsanan türleri içinde bildirim bağlamları içinde yalnızca erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff28d-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff28d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff28d-104">Remarks</span></span>  
 <span data-ttu-id="ff28d-105">Bir programlama öğesi özel işlevsellikten temsil eder veya gizli verileri içeriyorsa, genellikle mümkün olduğunca kesinlikle erişimi sınırlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="ff28d-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="ff28d-106">En fazla kısıtlama, yalnızca modül, sınıf veya erişmek için tanımlayan yapısı sağlayarak elde edin.</span><span class="sxs-lookup"><span data-stu-id="ff28d-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="ff28d-107">Bu şekilde bir öğeyi erişimi sınırlamak için ile bildirebilir `Private`.</span><span class="sxs-lookup"><span data-stu-id="ff28d-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ff28d-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="ff28d-108">Rules</span></span>  
  
-   <span data-ttu-id="ff28d-109">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="ff28d-109">**Declaration Context.**</span></span> <span data-ttu-id="ff28d-110">Kullanabileceğiniz `Private` yalnızca modülü düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="ff28d-110">You can use `Private` only at module level.</span></span> <span data-ttu-id="ff28d-111">Bu bildirimi bağlamının anlamına gelir bir `Private` öğesi bir modül, sınıf veya yapı olması ve kaynak dosyasını, ad alanı, arabirim veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="ff28d-111">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="ff28d-112">Davranış</span><span class="sxs-lookup"><span data-stu-id="ff28d-112">Behavior</span></span>  
  
-   <span data-ttu-id="ff28d-113">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="ff28d-113">**Access Level.**</span></span> <span data-ttu-id="ff28d-114">Bildirimi bağlam içindeki tüm kodu erişmek için kendi `Private` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ff28d-114">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="ff28d-115">Bu, iç içe bir sınıf veya numaralandırma atama deyimde gibi bir kapsanan türü içindeki kod içerir.</span><span class="sxs-lookup"><span data-stu-id="ff28d-115">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="ff28d-116">Bildirimi bağlamı dışında hiçbir kod erişmek için kendi `Private` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ff28d-116">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="ff28d-117">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="ff28d-117">**Access Modifiers.**</span></span> <span data-ttu-id="ff28d-118">Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*.</span><span class="sxs-lookup"><span data-stu-id="ff28d-118">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="ff28d-119">Erişim değiştiricileri karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ff28d-119">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="ff28d-120">`Private` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ff28d-120">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ff28d-121">Class deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="ff28d-122">Const deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="ff28d-123">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="ff28d-124">Delegate deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="ff28d-125">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="ff28d-126">Enum deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="ff28d-127">Event deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="ff28d-128">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="ff28d-129">Interface deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="ff28d-130">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="ff28d-131">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-131">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="ff28d-132">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="ff28d-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ff28d-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff28d-133">See Also</span></span>  
 [<span data-ttu-id="ff28d-134">Ortak</span><span class="sxs-lookup"><span data-stu-id="ff28d-134">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="ff28d-135">Korumalı</span><span class="sxs-lookup"><span data-stu-id="ff28d-135">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="ff28d-136">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="ff28d-136">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="ff28d-137">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="ff28d-137">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="ff28d-138">Yordamları</span><span class="sxs-lookup"><span data-stu-id="ff28d-138">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="ff28d-139">Yapıları</span><span class="sxs-lookup"><span data-stu-id="ff28d-139">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="ff28d-140">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="ff28d-140">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
