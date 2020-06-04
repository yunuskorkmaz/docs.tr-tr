---
title: Ortak
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35332e50227cdef6386362df17c10b5b2cdaa689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415355"
---
# <a name="public-visual-basic"></a><span data-ttu-id="69996-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69996-102">Public (Visual Basic)</span></span>
<span data-ttu-id="69996-103">Bir veya daha fazla tanımlanmış programlama öğesinin erişim kısıtlaması olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="69996-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69996-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69996-104">Remarks</span></span>  
 <span data-ttu-id="69996-105">Sınıf kitaplığı gibi bir bileşeni veya bileşen kümesini yayınlıyorsanız, genellikle programlama öğelerine derlemele birlikte çalışan herhangi bir kod tarafından erişilebilmesini istersiniz.</span><span class="sxs-lookup"><span data-stu-id="69996-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="69996-106">Bir öğe üzerinde sınırsız erişim sağlamak için, ile bildirimini yapabilirsiniz `Public` .</span><span class="sxs-lookup"><span data-stu-id="69996-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="69996-107">Genel erişim, bir programlama öğesi için erişimi sınırlandırmanıza gerek olmadığında normal düzeydir.</span><span class="sxs-lookup"><span data-stu-id="69996-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="69996-108">Bir arabirim, modül, sınıf veya yapı içinde belirtilen bir öğenin erişim düzeyinin, aksi belirtilmedikçe, varsayılan olarak olduğunu unutmayın `Public` .</span><span class="sxs-lookup"><span data-stu-id="69996-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="69996-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="69996-109">Rules</span></span>  
  
- <span data-ttu-id="69996-110">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="69996-110">**Declaration Context.**</span></span> <span data-ttu-id="69996-111">`Public`Yalnızca modül, arabirim veya ad alanı düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69996-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="69996-112">Bu, bir öğe için bildirim bağlamının `Public` bir kaynak dosya, ad alanı, arabirim, modül, sınıf veya yapı olması gerektiği anlamına gelir ve bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="69996-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="69996-113">Davranış</span><span class="sxs-lookup"><span data-stu-id="69996-113">Behavior</span></span>  
  
- <span data-ttu-id="69996-114">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="69996-114">**Access Level.**</span></span> <span data-ttu-id="69996-115">Bir modüle, sınıfa veya yapıya erişebilen tüm kodlar `Public` öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="69996-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="69996-116">**Varsayılan erişim.**</span><span class="sxs-lookup"><span data-stu-id="69996-116">**Default Access.**</span></span> <span data-ttu-id="69996-117">Bir yordamın içindeki yerel değişkenler, genel erişim için varsayılan olarak kullanılır ve bunlara herhangi bir erişim değiştiricisi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="69996-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="69996-118">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="69996-118">**Access Modifiers.**</span></span> <span data-ttu-id="69996-119">Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir.</span><span class="sxs-lookup"><span data-stu-id="69996-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="69996-120">Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="69996-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="69996-121">`Public`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="69996-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="69996-122">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="69996-123">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="69996-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="69996-125">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="69996-126">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="69996-127">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="69996-128">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="69996-129">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="69996-130">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="69996-131">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-131">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="69996-132">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-132">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 [<span data-ttu-id="69996-133">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-133">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="69996-134">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="69996-134">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="69996-135">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="69996-135">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="69996-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69996-136">See also</span></span>

- [<span data-ttu-id="69996-137">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="69996-137">Protected</span></span>](protected.md)
- [<span data-ttu-id="69996-138">Dost</span><span class="sxs-lookup"><span data-stu-id="69996-138">Friend</span></span>](friend.md)
- [<span data-ttu-id="69996-139">Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="69996-139">Private</span></span>](private.md)
- [<span data-ttu-id="69996-140">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="69996-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="69996-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="69996-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="69996-142">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="69996-142">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="69996-143">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="69996-143">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="69996-144">Yapılar</span><span class="sxs-lookup"><span data-stu-id="69996-144">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="69996-145">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="69996-145">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
