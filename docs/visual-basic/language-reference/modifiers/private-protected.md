---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: b7d9f81e41950b92c787e2e50fb94fe3d7c07559
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362235"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="c8ea1-102">Özel korumalı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8ea1-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="c8ea1-103">`Private Protected`Anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="c8ea1-104">Bir `Private Protected` üyeye, kapsayan sınıfındaki tüm üyeler tarafından erişilebilir ve ancak kapsayan sınıftan türetilmiş türler, ancak yalnızca kendi kapsayıcı derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="c8ea1-105">`Private Protected`Yalnızca sınıfların üyelerinde belirtebilirsiniz; `Private Protected` yapılar devralınamadığı için bir yapının üyelerine uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="c8ea1-106">`Private Protected`Erişim değiştiricisi Visual Basic 15,5 ve üzeri sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="c8ea1-107">Bunu kullanmak için, Visual Basic projesi ( \* . vbproj) dosyanıza aşağıdaki öğeyi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="c8ea1-108">Visual Basic 15,5 veya üzeri bir sürümü sisteminize yüklendiği sürece, Visual Basic derleyicinin en son sürümü tarafından desteklenen tüm dil özelliklerinden yararlanmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="c8ea1-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="c8ea1-109">Daha fazla bilgi için bkz. [Visual Basic dil sürümünü ayarlama](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="c8ea1-109">For more information see [setting the Visual Basic language version](../configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c8ea1-110">Visual Studio 'da F1 Yardımı ' nı seçmek, `private protected` [özel](private.md) veya [korumalı](protected.md)için yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="c8ea1-111">IDE, bileşik sözcük yerine imleç altında tek belirteci seçer.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="c8ea1-112">Kurallar</span><span class="sxs-lookup"><span data-stu-id="c8ea1-112">Rules</span></span>

- <span data-ttu-id="c8ea1-113">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="c8ea1-113">**Declaration Context.**</span></span> <span data-ttu-id="c8ea1-114">`Private Protected`Yalnızca sınıf düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="c8ea1-115">Yani bir öğe için bildirim bağlamı `Protected` bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="c8ea1-116">Davranış</span><span class="sxs-lookup"><span data-stu-id="c8ea1-116">Behavior</span></span>

- <span data-ttu-id="c8ea1-117">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="c8ea1-117">**Access Level.**</span></span> <span data-ttu-id="c8ea1-118">Bir sınıftaki tüm kod öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-118">All code in a class can access its elements.</span></span> <span data-ttu-id="c8ea1-119">Bir taban sınıftan türetilen ve aynı derlemede yer alan herhangi bir sınıftaki kod, `Private Protected` temel sınıfın tüm öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="c8ea1-120">Ancak, bir taban sınıftan türetilen ve farklı bir derlemede yer alan herhangi bir sınıftaki kod, temel sınıf `Private Protected` öğelerine erişemez.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="c8ea1-121">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="c8ea1-121">**Access Modifiers.**</span></span> <span data-ttu-id="c8ea1-122">Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="c8ea1-123">Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c8ea1-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="c8ea1-124">`Private Protected`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c8ea1-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="c8ea1-125">İç içe bir sınıfın [sınıf ekstresi](../statements/class-statement.md)</span><span class="sxs-lookup"><span data-stu-id="c8ea1-125">[Class Statement](../statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="c8ea1-126">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="c8ea1-126">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="c8ea1-127">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="c8ea1-127">Declare Statement</span></span>](../statements/declare-statement.md)

- <span data-ttu-id="c8ea1-128">Sınıf içinde iç içe bir temsilcinin [temsilci ekstresi](../statements/delegate-statement.md)</span><span class="sxs-lookup"><span data-stu-id="c8ea1-128">[Delegate Statement](../statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="c8ea1-129">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="c8ea1-129">Dim Statement</span></span>](../statements/dim-statement.md)

- <span data-ttu-id="c8ea1-130">Bir sınıfta iç içe geçmiş bir numaralandırmanın [enum bildirimi](../statements/enum-statement.md)</span><span class="sxs-lookup"><span data-stu-id="c8ea1-130">[Enum Statement](../statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="c8ea1-131">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="c8ea1-131">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="c8ea1-132">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="c8ea1-132">Function Statement</span></span>](../statements/function-statement.md)

- <span data-ttu-id="c8ea1-133">Bir sınıfta iç içe yerleştirilmiş bir arabirimin [arabirim ekstresi](../statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="c8ea1-133">[Interface Statement](../statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="c8ea1-134">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="c8ea1-134">Property Statement</span></span>](../statements/property-statement.md)

- <span data-ttu-id="c8ea1-135">Bir sınıfta iç içe yerleştirilmiş bir yapının [Yapı ekstresi](../statements/structure-statement.md)</span><span class="sxs-lookup"><span data-stu-id="c8ea1-135">[Structure Statement](../statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="c8ea1-136">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="c8ea1-136">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="c8ea1-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8ea1-137">See also</span></span>

- [<span data-ttu-id="c8ea1-138">Geneldir</span><span class="sxs-lookup"><span data-stu-id="c8ea1-138">Public</span></span>](public.md)
- [<span data-ttu-id="c8ea1-139">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="c8ea1-139">Protected</span></span>](protected.md)
- [<span data-ttu-id="c8ea1-140">Dost</span><span class="sxs-lookup"><span data-stu-id="c8ea1-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="c8ea1-141">Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c8ea1-141">Private</span></span>](private.md)
- [<span data-ttu-id="c8ea1-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="c8ea1-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="c8ea1-143">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="c8ea1-143">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="c8ea1-144">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c8ea1-144">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="c8ea1-145">Yapılar</span><span class="sxs-lookup"><span data-stu-id="c8ea1-145">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="c8ea1-146">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="c8ea1-146">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
