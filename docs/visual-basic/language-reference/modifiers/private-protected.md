---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 265141f77f4a61a61414a07214830feaa8a1ab05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351341"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="2d285-102">Özel korumalı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d285-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="2d285-103">`Private Protected` anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="2d285-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="2d285-104">`Private Protected` üyeye, kapsayan sınıftaki tüm üyeler tarafından ve kapsayan sınıftan türetilmiş türler tarafından erişilebilir, ancak yalnızca kendi kapsayıcı derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2d285-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="2d285-105">Yalnızca sınıfların üyelerinde `Private Protected` belirtebilirsiniz; yapılar devralınamadığı için `Private Protected` bir yapının üyelerine uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2d285-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="2d285-106">`Private Protected` erişim değiştiricisi Visual Basic 15,5 ve üzeri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2d285-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="2d285-107">Bunu kullanmak için, Visual Basic projesi (\*. vbproj) dosyanıza aşağıdaki öğeyi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d285-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="2d285-108">Visual Basic 15,5 veya üzeri bir sürümü sisteminize yüklendiği sürece, Visual Basic derleyicinin en son sürümü tarafından desteklenen tüm dil özelliklerinden yararlanmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="2d285-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="2d285-109">Daha fazla bilgi için bkz. [Visual Basic dil sürümünü ayarlama](../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="2d285-109">For more information see [setting the Visual Basic language version](../../language-reference/configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2d285-110">Visual Studio 'da F1 Yardımı ' nı seçmek `private protected` [özel](private.md) veya [korumalı](protected.md)yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d285-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="2d285-111">IDE, bileşik sözcük yerine imleç altında tek belirteci seçer.</span><span class="sxs-lookup"><span data-stu-id="2d285-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="2d285-112">Kurallar</span><span class="sxs-lookup"><span data-stu-id="2d285-112">Rules</span></span>

- <span data-ttu-id="2d285-113">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="2d285-113">**Declaration Context.**</span></span> <span data-ttu-id="2d285-114">`Private Protected` yalnızca sınıf düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d285-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="2d285-115">Yani, bir `Protected` öğesi için bildirim bağlamı bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="2d285-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="2d285-116">Davranış</span><span class="sxs-lookup"><span data-stu-id="2d285-116">Behavior</span></span>

- <span data-ttu-id="2d285-117">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="2d285-117">**Access Level.**</span></span> <span data-ttu-id="2d285-118">Bir sınıftaki tüm kod öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="2d285-118">All code in a class can access its elements.</span></span> <span data-ttu-id="2d285-119">Bir taban sınıftan türetilen ve aynı derlemede yer alan herhangi bir sınıftaki kod, temel sınıfın tüm `Private Protected` öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="2d285-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="2d285-120">Ancak, bir taban sınıftan türetilen ve farklı bir derlemede yer alan herhangi bir sınıftaki kod, temel sınıfa `Private Protected` öğelerine erişemez.</span><span class="sxs-lookup"><span data-stu-id="2d285-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="2d285-121">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="2d285-121">**Access Modifiers.**</span></span> <span data-ttu-id="2d285-122">Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir.</span><span class="sxs-lookup"><span data-stu-id="2d285-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="2d285-123">Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2d285-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="2d285-124">`Private Protected` değiştiricisi şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2d285-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="2d285-125">İç içe bir sınıfın [sınıf ekstresi](../../../visual-basic/language-reference/statements/class-statement.md)</span><span class="sxs-lookup"><span data-stu-id="2d285-125">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="2d285-126">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d285-126">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="2d285-127">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d285-127">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- <span data-ttu-id="2d285-128">Sınıf içinde iç içe bir temsilcinin [temsilci ekstresi](../../../visual-basic/language-reference/statements/delegate-statement.md)</span><span class="sxs-lookup"><span data-stu-id="2d285-128">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="2d285-129">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d285-129">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- <span data-ttu-id="2d285-130">Bir sınıfta iç içe geçmiş bir numaralandırmanın [enum bildirimi](../../../visual-basic/language-reference/statements/enum-statement.md)</span><span class="sxs-lookup"><span data-stu-id="2d285-130">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="2d285-131">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d285-131">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="2d285-132">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d285-132">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- <span data-ttu-id="2d285-133">Bir sınıfta iç içe yerleştirilmiş bir arabirimin [arabirim ekstresi](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="2d285-133">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="2d285-134">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d285-134">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- <span data-ttu-id="2d285-135">Bir sınıfta iç içe yerleştirilmiş bir yapının [Yapı ekstresi](../../../visual-basic/language-reference/statements/structure-statement.md)</span><span class="sxs-lookup"><span data-stu-id="2d285-135">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="2d285-136">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d285-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="2d285-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d285-137">See also</span></span>

- [<span data-ttu-id="2d285-138">Public</span><span class="sxs-lookup"><span data-stu-id="2d285-138">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="2d285-139">Protected</span><span class="sxs-lookup"><span data-stu-id="2d285-139">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="2d285-140">Friend</span><span class="sxs-lookup"><span data-stu-id="2d285-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="2d285-141">Private</span><span class="sxs-lookup"><span data-stu-id="2d285-141">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="2d285-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="2d285-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="2d285-143">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="2d285-143">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="2d285-144">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="2d285-144">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="2d285-145">Yapılar</span><span class="sxs-lookup"><span data-stu-id="2d285-145">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="2d285-146">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="2d285-146">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
