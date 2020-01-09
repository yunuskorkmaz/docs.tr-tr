---
title: Özel
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 0c855c4e08b365b4cb75ab062d2ec304a79612ab
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347912"
---
# <a name="private-visual-basic"></a><span data-ttu-id="b2805-102">Özel (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2805-102">Private (Visual Basic)</span></span>
<span data-ttu-id="b2805-103">Bir ya da daha fazla bildirilmemiş programlama öğesine, içerilen türlerin dahil olduğu gibi yalnızca kendi bildirim bağlamlarından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2805-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2805-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2805-104">Remarks</span></span>  
 <span data-ttu-id="b2805-105">Bir programlama öğesi özel işlevselliği gösteriyorsa veya gizli veriler içeriyorsa, genellikle erişimi mümkün olduğunca kesin bir şekilde sınırlandırmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b2805-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="b2805-106">Yalnızca ona erişmek için onu tanımlayan modüle, sınıfa veya yapıya izin vererek en yüksek kısıtlamayı elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="b2805-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="b2805-107">Bu şekilde bir öğeye erişimi sınırlandırmak için, `Private`ile bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2805-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="b2805-108">Ayrıca, bir üyeyi bu sınıftan ve kapsayan derlemede bulunan türetilmiş sınıflardan erişilebilir hale getiren [özel korumalı](private-protected.md) erişim değiştiricisini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2805-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="b2805-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="b2805-109">Rules</span></span>  

- <span data-ttu-id="b2805-110">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="b2805-110">**Declaration Context.**</span></span> <span data-ttu-id="b2805-111">Yalnızca modül düzeyinde `Private` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2805-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="b2805-112">Bu, bir `Private` öğesi için bildirim bağlamının bir modül, sınıf veya yapı olması ve bir kaynak dosya, ad alanı, arabirim ya da yordam olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b2805-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="b2805-113">Davranış</span><span class="sxs-lookup"><span data-stu-id="b2805-113">Behavior</span></span>  
  
- <span data-ttu-id="b2805-114">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="b2805-114">**Access Level.**</span></span> <span data-ttu-id="b2805-115">Bir bildirim bağlamı içindeki tüm kod `Private` öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="b2805-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="b2805-116">Bu, iç içe geçmiş bir sınıf veya bir Numaralandırmadaki atama ifadesi gibi içerilen bir tür içindeki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="b2805-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="b2805-117">Bildirim bağlamı dışında hiçbir kod, `Private` öğelerine erişemez.</span><span class="sxs-lookup"><span data-stu-id="b2805-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="b2805-118">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="b2805-118">**Access Modifiers.**</span></span> <span data-ttu-id="b2805-119">Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir.</span><span class="sxs-lookup"><span data-stu-id="b2805-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="b2805-120">Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b2805-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="b2805-121">`Private` değiştiricisi şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b2805-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="b2805-122">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="b2805-123">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="b2805-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="b2805-125">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="b2805-126">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="b2805-127">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="b2805-128">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="b2805-129">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="b2805-130">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="b2805-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="b2805-132">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="b2805-133">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2805-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b2805-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2805-134">See also</span></span>

- [<span data-ttu-id="b2805-135">Public</span><span class="sxs-lookup"><span data-stu-id="b2805-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="b2805-136">Protected</span><span class="sxs-lookup"><span data-stu-id="b2805-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="b2805-137">Friend</span><span class="sxs-lookup"><span data-stu-id="b2805-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="b2805-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="b2805-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="b2805-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="b2805-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="b2805-140">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="b2805-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="b2805-141">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b2805-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="b2805-142">Yapılar</span><span class="sxs-lookup"><span data-stu-id="b2805-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="b2805-143">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b2805-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
