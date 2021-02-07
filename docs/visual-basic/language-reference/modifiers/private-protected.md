---
description: 'Daha fazla bilgi edinin: özel korumalı (Visual Basic)'
title: Private Protected
ms.date: 05/10/2018
f1_keywords:
- vb.PrivateProtected
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: eb521ace77cd16f4904657cbdc035575e98e98fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700968"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="41bcd-103">Özel korumalı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41bcd-103">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="41bcd-104">`Private Protected`Anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="41bcd-104">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="41bcd-105">Bir `Private Protected` üyeye, kapsayan sınıfındaki tüm üyeler tarafından erişilebilir ve ancak kapsayan sınıftan türetilmiş türler, ancak yalnızca kendi kapsayıcı derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="41bcd-105">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="41bcd-106">`Private Protected`Yalnızca sınıfların üyelerinde belirtebilirsiniz; `Private Protected` yapılar devralınamadığı için bir yapının üyelerine uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="41bcd-106">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="41bcd-107">`Private Protected`Erişim değiştiricisi Visual Basic 15,5 ve üzeri sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="41bcd-107">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="41bcd-108">Bunu kullanmak için, Visual Basic projesi ( \* . vbproj) dosyanıza aşağıdaki öğeyi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41bcd-108">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="41bcd-109">Visual Basic 15,5 veya üzeri bir sürümü sisteminize yüklendiği sürece, Visual Basic derleyicinin en son sürümü tarafından desteklenen tüm dil özelliklerinden yararlanmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="41bcd-109">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="41bcd-110">Daha fazla bilgi için bkz. [Visual Basic dil sürümünü ayarlama](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="41bcd-110">For more information see [setting the Visual Basic language version](../configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="41bcd-111">Visual Studio 'da F1 Yardımı ' nı seçmek, `private protected` [özel](private.md) veya [korumalı](protected.md)için yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="41bcd-111">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="41bcd-112">IDE, bileşik sözcük yerine imleç altında tek belirteci seçer.</span><span class="sxs-lookup"><span data-stu-id="41bcd-112">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="41bcd-113">Kurallar</span><span class="sxs-lookup"><span data-stu-id="41bcd-113">Rules</span></span>

- <span data-ttu-id="41bcd-114">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="41bcd-114">**Declaration Context.**</span></span> <span data-ttu-id="41bcd-115">`Private Protected`Yalnızca sınıf düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41bcd-115">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="41bcd-116">Yani bir öğe için bildirim bağlamı `Protected` bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="41bcd-116">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="41bcd-117">Davranış</span><span class="sxs-lookup"><span data-stu-id="41bcd-117">Behavior</span></span>

- <span data-ttu-id="41bcd-118">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="41bcd-118">**Access Level.**</span></span> <span data-ttu-id="41bcd-119">Bir sınıftaki tüm kod öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="41bcd-119">All code in a class can access its elements.</span></span> <span data-ttu-id="41bcd-120">Bir taban sınıftan türetilen ve aynı derlemede yer alan herhangi bir sınıftaki kod, `Private Protected` temel sınıfın tüm öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="41bcd-120">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="41bcd-121">Ancak, bir taban sınıftan türetilen ve farklı bir derlemede yer alan herhangi bir sınıftaki kod, temel sınıf `Private Protected` öğelerine erişemez.</span><span class="sxs-lookup"><span data-stu-id="41bcd-121">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="41bcd-122">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="41bcd-122">**Access Modifiers.**</span></span> <span data-ttu-id="41bcd-123">Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri* denir.</span><span class="sxs-lookup"><span data-stu-id="41bcd-123">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="41bcd-124">Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="41bcd-124">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="41bcd-125">`Private Protected`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="41bcd-125">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="41bcd-126">İç içe bir sınıfın [sınıf ekstresi](../statements/class-statement.md)</span><span class="sxs-lookup"><span data-stu-id="41bcd-126">[Class Statement](../statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="41bcd-127">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="41bcd-127">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="41bcd-128">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="41bcd-128">Declare Statement</span></span>](../statements/declare-statement.md)

- <span data-ttu-id="41bcd-129">Sınıf içinde iç içe bir temsilcinin [temsilci ekstresi](../statements/delegate-statement.md)</span><span class="sxs-lookup"><span data-stu-id="41bcd-129">[Delegate Statement](../statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="41bcd-130">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="41bcd-130">Dim Statement</span></span>](../statements/dim-statement.md)

- <span data-ttu-id="41bcd-131">Bir sınıfta iç içe geçmiş bir numaralandırmanın [enum bildirimi](../statements/enum-statement.md)</span><span class="sxs-lookup"><span data-stu-id="41bcd-131">[Enum Statement](../statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="41bcd-132">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="41bcd-132">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="41bcd-133">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="41bcd-133">Function Statement</span></span>](../statements/function-statement.md)

- <span data-ttu-id="41bcd-134">Bir sınıfta iç içe yerleştirilmiş bir arabirimin [arabirim ekstresi](../statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="41bcd-134">[Interface Statement](../statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="41bcd-135">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="41bcd-135">Property Statement</span></span>](../statements/property-statement.md)

- <span data-ttu-id="41bcd-136">Bir sınıfta iç içe yerleştirilmiş bir yapının [Yapı ekstresi](../statements/structure-statement.md)</span><span class="sxs-lookup"><span data-stu-id="41bcd-136">[Structure Statement](../statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="41bcd-137">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="41bcd-137">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="41bcd-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41bcd-138">See also</span></span>

- [<span data-ttu-id="41bcd-139">Genel</span><span class="sxs-lookup"><span data-stu-id="41bcd-139">Public</span></span>](public.md)
- [<span data-ttu-id="41bcd-140">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="41bcd-140">Protected</span></span>](protected.md)
- [<span data-ttu-id="41bcd-141">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="41bcd-141">Friend</span></span>](friend.md)
- [<span data-ttu-id="41bcd-142">Özel</span><span class="sxs-lookup"><span data-stu-id="41bcd-142">Private</span></span>](private.md)
- [<span data-ttu-id="41bcd-143">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="41bcd-143">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="41bcd-144">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="41bcd-144">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="41bcd-145">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="41bcd-145">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="41bcd-146">Yapılar</span><span class="sxs-lookup"><span data-stu-id="41bcd-146">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="41bcd-147">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="41bcd-147">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
