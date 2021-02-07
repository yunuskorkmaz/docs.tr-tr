---
description: 'Daha fazla bilgi edinin: Public (Visual Basic)'
title: Genel
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 1083ca877cf99917291523fe10f6561784ff06a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700929"
---
# <a name="public-visual-basic"></a><span data-ttu-id="a98d5-103">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a98d5-103">Public (Visual Basic)</span></span>

<span data-ttu-id="a98d5-104">Bir veya daha fazla tanımlanmış programlama öğesinin erişim kısıtlaması olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a98d5-104">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a98d5-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a98d5-105">Remarks</span></span>  

 <span data-ttu-id="a98d5-106">Sınıf kitaplığı gibi bir bileşeni veya bileşen kümesini yayınlıyorsanız, genellikle programlama öğelerine derlemele birlikte çalışan herhangi bir kod tarafından erişilebilmesini istersiniz.</span><span class="sxs-lookup"><span data-stu-id="a98d5-106">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="a98d5-107">Bir öğe üzerinde sınırsız erişim sağlamak için, ile bildirimini yapabilirsiniz `Public` .</span><span class="sxs-lookup"><span data-stu-id="a98d5-107">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="a98d5-108">Genel erişim, bir programlama öğesi için erişimi sınırlandırmanıza gerek olmadığında normal düzeydir.</span><span class="sxs-lookup"><span data-stu-id="a98d5-108">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="a98d5-109">Bir arabirim, modül, sınıf veya yapı içinde belirtilen bir öğenin erişim düzeyinin, aksi belirtilmedikçe, varsayılan olarak olduğunu unutmayın `Public` .</span><span class="sxs-lookup"><span data-stu-id="a98d5-109">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a98d5-110">Kurallar</span><span class="sxs-lookup"><span data-stu-id="a98d5-110">Rules</span></span>  
  
- <span data-ttu-id="a98d5-111">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="a98d5-111">**Declaration Context.**</span></span> <span data-ttu-id="a98d5-112">`Public`Yalnızca modül, arabirim veya ad alanı düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a98d5-112">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="a98d5-113">Bu, bir öğe için bildirim bağlamının `Public` bir kaynak dosya, ad alanı, arabirim, modül, sınıf veya yapı olması gerektiği anlamına gelir ve bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="a98d5-113">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="a98d5-114">Davranış</span><span class="sxs-lookup"><span data-stu-id="a98d5-114">Behavior</span></span>  
  
- <span data-ttu-id="a98d5-115">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="a98d5-115">**Access Level.**</span></span> <span data-ttu-id="a98d5-116">Bir modüle, sınıfa veya yapıya erişebilen tüm kodlar `Public` öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="a98d5-116">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="a98d5-117">**Varsayılan erişim.**</span><span class="sxs-lookup"><span data-stu-id="a98d5-117">**Default Access.**</span></span> <span data-ttu-id="a98d5-118">Bir yordamın içindeki yerel değişkenler, genel erişim için varsayılan olarak kullanılır ve bunlara herhangi bir erişim değiştiricisi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a98d5-118">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="a98d5-119">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="a98d5-119">**Access Modifiers.**</span></span> <span data-ttu-id="a98d5-120">Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri* denir.</span><span class="sxs-lookup"><span data-stu-id="a98d5-120">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="a98d5-121">Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a98d5-121">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="a98d5-122">`Public`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a98d5-122">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="a98d5-123">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-123">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="a98d5-124">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-124">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="a98d5-125">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-125">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="a98d5-126">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-126">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="a98d5-127">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-127">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="a98d5-128">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-128">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="a98d5-129">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-129">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="a98d5-130">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-130">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="a98d5-131">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-131">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="a98d5-132">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-132">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="a98d5-133">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-133">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 [<span data-ttu-id="a98d5-134">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-134">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="a98d5-135">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="a98d5-135">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="a98d5-136">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="a98d5-136">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a98d5-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a98d5-137">See also</span></span>

- [<span data-ttu-id="a98d5-138">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="a98d5-138">Protected</span></span>](protected.md)
- [<span data-ttu-id="a98d5-139">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="a98d5-139">Friend</span></span>](friend.md)
- [<span data-ttu-id="a98d5-140">Özel</span><span class="sxs-lookup"><span data-stu-id="a98d5-140">Private</span></span>](private.md)
- [<span data-ttu-id="a98d5-141">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="a98d5-141">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="a98d5-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="a98d5-142">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="a98d5-143">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a98d5-143">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="a98d5-144">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a98d5-144">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="a98d5-145">Yapılar</span><span class="sxs-lookup"><span data-stu-id="a98d5-145">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a98d5-146">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="a98d5-146">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
