---
title: Özel (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 40b64b8d2b6306d458b7a9cc657c5b7dc4270eb2
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="private-visual-basic"></a><span data-ttu-id="2b65e-102">Özel (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b65e-102">Private (Visual Basic)</span></span>
<span data-ttu-id="2b65e-103">Bir veya daha fazla bildirilen programlama öğeleri dahil tüm kapsanan türleri içinde bildirim bağlamları içinde yalnızca erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b65e-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b65e-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b65e-104">Remarks</span></span>  
 <span data-ttu-id="2b65e-105">Bir programlama öğesi özel işlevsellikten temsil eder veya gizli verileri içeriyorsa, genellikle mümkün olduğunca kesinlikle erişimi sınırlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2b65e-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="2b65e-106">En fazla kısıtlama, yalnızca modül, sınıf veya erişmek için tanımlayan yapısı sağlayarak elde edin.</span><span class="sxs-lookup"><span data-stu-id="2b65e-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="2b65e-107">Bu şekilde bir öğeyi erişimi sınırlamak için ile bildirebilir `Private`.</span><span class="sxs-lookup"><span data-stu-id="2b65e-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="2b65e-108">Aynı zamanda [özel korumalı](private-protected.md) üyesi erişilebilir bir sınıftaki ve türetilmiş sınıflarının içeren derlemesinde bulunan yapar erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="2b65e-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="2b65e-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="2b65e-109">Rules</span></span>  

-   <span data-ttu-id="2b65e-110">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="2b65e-110">**Declaration Context.**</span></span> <span data-ttu-id="2b65e-111">Kullanabileceğiniz `Private` yalnızca modülü düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="2b65e-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="2b65e-112">Bu bildirimi bağlamının anlamına gelir bir `Private` öğesi bir modül, sınıf veya yapı olması ve kaynak dosyasını, ad alanı, arabirim veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="2b65e-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2b65e-113">Davranış</span><span class="sxs-lookup"><span data-stu-id="2b65e-113">Behavior</span></span>  
  
-   <span data-ttu-id="2b65e-114">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="2b65e-114">**Access Level.**</span></span> <span data-ttu-id="2b65e-115">Bildirimi bağlam içindeki tüm kodu erişmek için kendi `Private` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="2b65e-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="2b65e-116">Bu, iç içe bir sınıf veya numaralandırma atama deyimde gibi bir kapsanan türü içindeki kod içerir.</span><span class="sxs-lookup"><span data-stu-id="2b65e-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="2b65e-117">Bildirimi bağlamı dışında hiçbir kod erişmek için kendi `Private` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="2b65e-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="2b65e-118">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="2b65e-118">**Access Modifiers.**</span></span> <span data-ttu-id="2b65e-119">Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*.</span><span class="sxs-lookup"><span data-stu-id="2b65e-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="2b65e-120">Erişim değiştiricileri karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2b65e-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="2b65e-121">`Private` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2b65e-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2b65e-122">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="2b65e-123">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="2b65e-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="2b65e-125">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="2b65e-126">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="2b65e-127">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="2b65e-128">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="2b65e-129">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="2b65e-130">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="2b65e-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="2b65e-132">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="2b65e-133">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b65e-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2b65e-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b65e-134">See Also</span></span>  
 [<span data-ttu-id="2b65e-135">Public</span><span class="sxs-lookup"><span data-stu-id="2b65e-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="2b65e-136">Protected</span><span class="sxs-lookup"><span data-stu-id="2b65e-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="2b65e-137">Friend</span><span class="sxs-lookup"><span data-stu-id="2b65e-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 <span data-ttu-id="2b65e-138">[Özel korumalı](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="2b65e-138">[Private Protected](./private-protected.md) </span></span>  
 <span data-ttu-id="2b65e-139">[Arkadaş korumalı](./protected-friend.md)[erişim düzeyini Visual Basic'te    ](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="2b65e-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>  
 [<span data-ttu-id="2b65e-140">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="2b65e-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="2b65e-141">Yapılar</span><span class="sxs-lookup"><span data-stu-id="2b65e-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="2b65e-142">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="2b65e-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
