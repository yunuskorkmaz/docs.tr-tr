---
title: Özel
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 524f03e77e075bef08a1b41b563985de41baacb6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404816"
---
# <a name="private-visual-basic"></a><span data-ttu-id="cbbbf-102">Özel (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbbbf-102">Private (Visual Basic)</span></span>
<span data-ttu-id="cbbbf-103">Bir ya da daha fazla bildirilmemiş programlama öğesine, içerilen türlerin dahil olduğu gibi yalnızca kendi bildirim bağlamlarından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbbbf-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbbbf-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbbbf-104">Remarks</span></span>  
 <span data-ttu-id="cbbbf-105">Bir programlama öğesi özel işlevselliği gösteriyorsa veya gizli veriler içeriyorsa, genellikle erişimi mümkün olduğunca kesin bir şekilde sınırlandırmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="cbbbf-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="cbbbf-106">Yalnızca ona erişmek için onu tanımlayan modüle, sınıfa veya yapıya izin vererek en yüksek kısıtlamayı elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="cbbbf-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="cbbbf-107">Bu şekilde bir öğeye erişimi sınırlandırmak için, ile bildirimini yapabilirsiniz `Private` .</span><span class="sxs-lookup"><span data-stu-id="cbbbf-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="cbbbf-108">Ayrıca, bir üyeyi bu sınıftan ve kapsayan derlemede bulunan türetilmiş sınıflardan erişilebilir hale getiren [özel korumalı](private-protected.md) erişim değiştiricisini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbbbf-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="cbbbf-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="cbbbf-109">Rules</span></span>  

- <span data-ttu-id="cbbbf-110">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="cbbbf-110">**Declaration Context.**</span></span> <span data-ttu-id="cbbbf-111">`Private`Yalnızca modül düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbbbf-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="cbbbf-112">Bu, bir öğe için bildirim bağlamının `Private` bir modül, sınıf veya yapı olması ve kaynak dosya, ad alanı, arabirim veya yordam olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cbbbf-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="cbbbf-113">Davranış</span><span class="sxs-lookup"><span data-stu-id="cbbbf-113">Behavior</span></span>  
  
- <span data-ttu-id="cbbbf-114">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="cbbbf-114">**Access Level.**</span></span> <span data-ttu-id="cbbbf-115">Bir bildirim bağlamı içindeki tüm kod `Private` öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="cbbbf-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="cbbbf-116">Bu, iç içe geçmiş bir sınıf veya bir Numaralandırmadaki atama ifadesi gibi içerilen bir tür içindeki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="cbbbf-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="cbbbf-117">Bildirim bağlamı dışında hiçbir kod `Private` öğelerine erişemez.</span><span class="sxs-lookup"><span data-stu-id="cbbbf-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="cbbbf-118">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="cbbbf-118">**Access Modifiers.**</span></span> <span data-ttu-id="cbbbf-119">Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir.</span><span class="sxs-lookup"><span data-stu-id="cbbbf-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="cbbbf-120">Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cbbbf-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="cbbbf-121">`Private`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="cbbbf-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="cbbbf-122">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbbf-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="cbbbf-123">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbbf-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="cbbbf-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbbf-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="cbbbf-125">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbbf-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="cbbbf-126">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbbf-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="cbbbf-127">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbbf-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="cbbbf-128">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbbf-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="cbbbf-129">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbbf-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="cbbbf-130">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbbf-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="cbbbf-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbbf-131">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="cbbbf-132">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="cbbbf-132">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="cbbbf-133">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbbf-133">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cbbbf-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbbbf-134">See also</span></span>

- [<span data-ttu-id="cbbbf-135">Geneldir</span><span class="sxs-lookup"><span data-stu-id="cbbbf-135">Public</span></span>](public.md)
- [<span data-ttu-id="cbbbf-136">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="cbbbf-136">Protected</span></span>](protected.md)
- [<span data-ttu-id="cbbbf-137">Dost</span><span class="sxs-lookup"><span data-stu-id="cbbbf-137">Friend</span></span>](friend.md)
- [<span data-ttu-id="cbbbf-138">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="cbbbf-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="cbbbf-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="cbbbf-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="cbbbf-140">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="cbbbf-140">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="cbbbf-141">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cbbbf-141">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="cbbbf-142">Yapılar</span><span class="sxs-lookup"><span data-stu-id="cbbbf-142">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="cbbbf-143">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="cbbbf-143">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
