---
title: Özel korumalı (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: fea43558ac0fe8181f2786b69f2621346d446b2e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920503"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="db327-102">Özel korumalı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db327-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="db327-103">`Private Protected` Anahtar sözcüğü bir üye erişim değiştiricisi oluşur.</span><span class="sxs-lookup"><span data-stu-id="db327-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="db327-104">A `Private Protected` üye olduğu tüm üyelerini içeren sınıfındaki yanı sıra içeren sınıfından türetilen türler tarafından erişilebilir, ancak yalnızca içeren, derlemesi içinde bulunan.</span><span class="sxs-lookup"><span data-stu-id="db327-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="db327-105">Belirtebileceğiniz `Private Protected` yalnızca; sınıfların üyeleri üzerinde uygulayamazsınız `Private Protected` bir yapının üyelerine yapıları devraldığından.</span><span class="sxs-lookup"><span data-stu-id="db327-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="db327-106">`Private Protected` Erişim değiştiricisi, Visual Basic 15.5 ve sonraki sürümlerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="db327-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="db327-107">Bunu kullanmak için aşağıdaki öğeyi Visual Basic projenize ekleyebilirsiniz (\*.vbproj) dosya.</span><span class="sxs-lookup"><span data-stu-id="db327-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="db327-108">Sisteminizde sürece Visual Basic 15.5 veya üzeri yüklü olduğu, en son sürümü Visual Basic derleyicisi tarafından desteklenen dil özellikleri yararlanmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="db327-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="db327-109">Daha fazla bilgi için [Visual Basic dil sürümü ayarını](../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="db327-109">For more information see [setting the Visual Basic language version](../../language-reference/configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="db327-110">Visual Studio'da F1 Yardımı seçme `private protected` ya da Yardım sağlayan [özel](private.md) veya [korumalı](protected.md).</span><span class="sxs-lookup"><span data-stu-id="db327-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="db327-111">IDE bileşik sözcüğü yerine imleç altında tek belirteç seçer.</span><span class="sxs-lookup"><span data-stu-id="db327-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="db327-112">Kurallar</span><span class="sxs-lookup"><span data-stu-id="db327-112">Rules</span></span>

- <span data-ttu-id="db327-113">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="db327-113">**Declaration Context.**</span></span> <span data-ttu-id="db327-114">Kullanabileceğiniz `Private Protected` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="db327-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="db327-115">Bildirim bağlamı başka bir deyişle bir `Protected` öğesi bir sınıf olması gerekir ve bir kaynak dosyası, ad alanı, arabirim, modülü, yapı veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="db327-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="db327-116">Davranış</span><span class="sxs-lookup"><span data-stu-id="db327-116">Behavior</span></span>

- <span data-ttu-id="db327-117">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="db327-117">**Access Level.**</span></span> <span data-ttu-id="db327-118">Bir sınıftaki tüm kod öğelerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db327-118">All code in a class can access its elements.</span></span> <span data-ttu-id="db327-119">Kod, bir taban sınıftan türetilen ve aynı bütünleştirilmiş kodda yer alan herhangi bir sınıf içinde tüm erişebilir `Private Protected` öğeleri temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="db327-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="db327-120">Ancak, kod bir taban sınıftan türetilen ve farklı bir derlemede yer alan herhangi bir sınıf içinde temel sınıf erişemez `Private Protected` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="db327-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="db327-121">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="db327-121">**Access Modifiers.**</span></span> <span data-ttu-id="db327-122">Erişim düzeyini sağlayacaklarını anahtar sözcükleri adlı *erişim değiştiricilerine*.</span><span class="sxs-lookup"><span data-stu-id="db327-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="db327-123">Erişim değiştiricileri bir karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="db327-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="db327-124">`Private Protected` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="db327-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="db327-125">[Sınıf bildirimi](../../../visual-basic/language-reference/statements/class-statement.md) iç içe geçmiş bir sınıfı</span><span class="sxs-lookup"><span data-stu-id="db327-125">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="db327-126">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="db327-126">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="db327-127">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="db327-127">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- <span data-ttu-id="db327-128">[Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) temsilcisi, bir sınıf içinde iç içe geçmiş</span><span class="sxs-lookup"><span data-stu-id="db327-128">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="db327-129">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="db327-129">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- <span data-ttu-id="db327-130">[Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md) sabit listesi, bir sınıf içinde iç içe geçmiş</span><span class="sxs-lookup"><span data-stu-id="db327-130">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="db327-131">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="db327-131">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="db327-132">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="db327-132">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- <span data-ttu-id="db327-133">[İnterface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md) bir arabiriminin, bir sınıf içinde iç içe geçmiş</span><span class="sxs-lookup"><span data-stu-id="db327-133">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="db327-134">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="db327-134">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- <span data-ttu-id="db327-135">[Yapı bildirimi](../../../visual-basic/language-reference/statements/structure-statement.md) yapısını, bir sınıf içinde iç içe geçmiş</span><span class="sxs-lookup"><span data-stu-id="db327-135">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="db327-136">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="db327-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="db327-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db327-137">See also</span></span>

- [<span data-ttu-id="db327-138">Public</span><span class="sxs-lookup"><span data-stu-id="db327-138">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="db327-139">Protected</span><span class="sxs-lookup"><span data-stu-id="db327-139">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="db327-140">Friend</span><span class="sxs-lookup"><span data-stu-id="db327-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="db327-141">Private</span><span class="sxs-lookup"><span data-stu-id="db327-141">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="db327-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="db327-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="db327-143">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="db327-143">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="db327-144">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="db327-144">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="db327-145">Yapılar</span><span class="sxs-lookup"><span data-stu-id="db327-145">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="db327-146">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="db327-146">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
