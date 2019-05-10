---
title: Özel (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: ddb2d165de330758f58fbbcb5872e820e639808f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642794"
---
# <a name="private-visual-basic"></a><span data-ttu-id="faf6e-102">Özel (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="faf6e-102">Private (Visual Basic)</span></span>
<span data-ttu-id="faf6e-103">Bir veya daha fazla bildirilmiş programlama öğesine yalnızca gelen içinde kapsanan tüm türleri dahil olmak üzere bildirim bağlamları içinde erişilebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="faf6e-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faf6e-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="faf6e-104">Remarks</span></span>  
 <span data-ttu-id="faf6e-105">Bir programlama öğesi özel işlevleri temsil eder ya da gizli veriler içeren, genellikle erişimi mümkün olduğunca kesinlikle sınırlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="faf6e-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="faf6e-106">En fazla sınırlama, yalnızca modül, sınıf veya ona erişmek için tanımladığı yapısı sağlayarak elde edin.</span><span class="sxs-lookup"><span data-stu-id="faf6e-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="faf6e-107">Bu şekilde bir öğe erişimi sınırlamak için onunla bildirebilirsiniz `Private`.</span><span class="sxs-lookup"><span data-stu-id="faf6e-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="faf6e-108">Ayrıca [Protected Private](private-protected.md) erişim değiştiricisi, üye erişilebilir bir sınıftaki ve türetilen sınıflar, kapsayan bir derlemede yer sağlar.</span><span class="sxs-lookup"><span data-stu-id="faf6e-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="faf6e-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="faf6e-109">Rules</span></span>  

- <span data-ttu-id="faf6e-110">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="faf6e-110">**Declaration Context.**</span></span> <span data-ttu-id="faf6e-111">Kullanabileceğiniz `Private` yalnızca Modül düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="faf6e-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="faf6e-112">Bildirim bağlamı başka bir deyişle bir `Private` öğesi bir modül, sınıf veya yapı olmalıdır ve bir kaynak dosyası, ad alanı, arabirim ya da yordamın olamaz.</span><span class="sxs-lookup"><span data-stu-id="faf6e-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="faf6e-113">Davranış</span><span class="sxs-lookup"><span data-stu-id="faf6e-113">Behavior</span></span>  
  
- <span data-ttu-id="faf6e-114">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="faf6e-114">**Access Level.**</span></span> <span data-ttu-id="faf6e-115">Bildirim bağlam içinde tüm kod erişip kendi `Private` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="faf6e-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="faf6e-116">Bu, iç içe geçmiş bir sınıf veya bir sabit listesi içindeki bir atama ifadesi gibi bağımsız bir tür içindeki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="faf6e-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="faf6e-117">Bildirim bağlamı dışında hiçbir kod erişip kendi `Private` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="faf6e-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="faf6e-118">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="faf6e-118">**Access Modifiers.**</span></span> <span data-ttu-id="faf6e-119">Erişim düzeyini sağlayacaklarını anahtar sözcükleri adlı *erişim değiştiricilerine*.</span><span class="sxs-lookup"><span data-stu-id="faf6e-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="faf6e-120">Erişim değiştiricileri bir karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="faf6e-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="faf6e-121">`Private` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="faf6e-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="faf6e-122">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="faf6e-123">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="faf6e-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="faf6e-125">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="faf6e-126">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="faf6e-127">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="faf6e-128">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="faf6e-129">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="faf6e-130">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="faf6e-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="faf6e-132">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="faf6e-133">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="faf6e-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="faf6e-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faf6e-134">See also</span></span>

- [<span data-ttu-id="faf6e-135">Public</span><span class="sxs-lookup"><span data-stu-id="faf6e-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="faf6e-136">Protected</span><span class="sxs-lookup"><span data-stu-id="faf6e-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="faf6e-137">Friend</span><span class="sxs-lookup"><span data-stu-id="faf6e-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="faf6e-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="faf6e-138">Private Protected</span></span>](./private-protected.md)
- <span data-ttu-id="faf6e-139">[Korumalı Friend](./protected-friend.md)[erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="faf6e-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>
- [<span data-ttu-id="faf6e-140">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="faf6e-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="faf6e-141">Yapılar</span><span class="sxs-lookup"><span data-stu-id="faf6e-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="faf6e-142">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="faf6e-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
