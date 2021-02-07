---
description: 'Daha fazla bilgi edinin: özel (Visual Basic)'
title: Özel
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 20dcd943856e20ccb1b7cb5c0603fa5f313d2421
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700955"
---
# <a name="private-visual-basic"></a><span data-ttu-id="a911c-103">Özel (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a911c-103">Private (Visual Basic)</span></span>

<span data-ttu-id="a911c-104">Bir ya da daha fazla bildirilmemiş programlama öğesine, içerilen türlerin dahil olduğu gibi yalnızca kendi bildirim bağlamlarından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a911c-104">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a911c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a911c-105">Remarks</span></span>  

 <span data-ttu-id="a911c-106">Bir programlama öğesi özel işlevselliği gösteriyorsa veya gizli veriler içeriyorsa, genellikle erişimi mümkün olduğunca kesin bir şekilde sınırlandırmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="a911c-106">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="a911c-107">Yalnızca ona erişmek için onu tanımlayan modüle, sınıfa veya yapıya izin vererek en yüksek kısıtlamayı elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="a911c-107">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="a911c-108">Bu şekilde bir öğeye erişimi sınırlandırmak için, ile bildirimini yapabilirsiniz `Private` .</span><span class="sxs-lookup"><span data-stu-id="a911c-108">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="a911c-109">Ayrıca, bir üyeyi bu sınıftan ve kapsayan derlemede bulunan türetilmiş sınıflardan erişilebilir hale getiren [özel korumalı](private-protected.md) erişim değiştiricisini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a911c-109">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="a911c-110">Kurallar</span><span class="sxs-lookup"><span data-stu-id="a911c-110">Rules</span></span>  

- <span data-ttu-id="a911c-111">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="a911c-111">**Declaration Context.**</span></span> <span data-ttu-id="a911c-112">`Private`Yalnızca modül düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a911c-112">You can use `Private` only at module level.</span></span> <span data-ttu-id="a911c-113">Bu, bir öğe için bildirim bağlamının `Private` bir modül, sınıf veya yapı olması ve kaynak dosya, ad alanı, arabirim veya yordam olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a911c-113">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="a911c-114">Davranış</span><span class="sxs-lookup"><span data-stu-id="a911c-114">Behavior</span></span>  
  
- <span data-ttu-id="a911c-115">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="a911c-115">**Access Level.**</span></span> <span data-ttu-id="a911c-116">Bir bildirim bağlamı içindeki tüm kod `Private` öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="a911c-116">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="a911c-117">Bu, iç içe geçmiş bir sınıf veya bir Numaralandırmadaki atama ifadesi gibi içerilen bir tür içindeki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="a911c-117">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="a911c-118">Bildirim bağlamı dışında hiçbir kod `Private` öğelerine erişemez.</span><span class="sxs-lookup"><span data-stu-id="a911c-118">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="a911c-119">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="a911c-119">**Access Modifiers.**</span></span> <span data-ttu-id="a911c-120">Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri* denir.</span><span class="sxs-lookup"><span data-stu-id="a911c-120">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="a911c-121">Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a911c-121">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="a911c-122">`Private`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a911c-122">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="a911c-123">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="a911c-123">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="a911c-124">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="a911c-124">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="a911c-125">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="a911c-125">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="a911c-126">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="a911c-126">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="a911c-127">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="a911c-127">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="a911c-128">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="a911c-128">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="a911c-129">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="a911c-129">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="a911c-130">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="a911c-130">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="a911c-131">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="a911c-131">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="a911c-132">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="a911c-132">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="a911c-133">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="a911c-133">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="a911c-134">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="a911c-134">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a911c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a911c-135">See also</span></span>

- [<span data-ttu-id="a911c-136">Genel</span><span class="sxs-lookup"><span data-stu-id="a911c-136">Public</span></span>](public.md)
- [<span data-ttu-id="a911c-137">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="a911c-137">Protected</span></span>](protected.md)
- [<span data-ttu-id="a911c-138">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="a911c-138">Friend</span></span>](friend.md)
- [<span data-ttu-id="a911c-139">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="a911c-139">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="a911c-140">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="a911c-140">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="a911c-141">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a911c-141">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="a911c-142">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a911c-142">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="a911c-143">Yapılar</span><span class="sxs-lookup"><span data-stu-id="a911c-143">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a911c-144">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="a911c-144">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
