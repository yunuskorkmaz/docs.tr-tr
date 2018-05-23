---
title: Korumalı özel (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="b72f4-102">Korumalı özel (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b72f4-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="b72f4-103">`Private Protected` Anahtar sözcüğü birleşimi olan bir üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="b72f4-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="b72f4-104">A `Private Protected` üyesidir içeren sınıfındaki tüm üyeleri tarafından yanı sıra içeren sınıfından türetilen tür tarafından erişilebilir, ancak yalnızca kendi içeren bütünleştirilmiş kodunda bulunursa.</span><span class="sxs-lookup"><span data-stu-id="b72f4-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span> 

<span data-ttu-id="b72f4-105">Belirleyebileceğiniz `Private Protected` yalnızca sınıfları; üyelerinde uygulayamazsınız `Private Protected` bir yapı üyelerine yapıları devraldığından.</span><span class="sxs-lookup"><span data-stu-id="b72f4-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="b72f4-106">`Private Protected` Erişim değiştiricisi Visual Basic 15,5 tarafından ve sonraki sürümlerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b72f4-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="b72f4-107">Kullanmak için aşağıdaki öğeyi, Visual Basic proje (\*.vbproj) dosyasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b72f4-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="b72f4-108">Visual Basic 15,5 sürece veya üzeri, sisteminizde yüklü gibi Visual Basic derleyici en son sürümü tarafından desteklenen tüm dil özellikleri yararlanmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="b72f4-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="b72f4-109">Visual Studio'da F1 Yardımı seçme `private protected` ya da Yardım sağlar [özel](private.md) veya [korumalı](protected.md).</span><span class="sxs-lookup"><span data-stu-id="b72f4-109">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="b72f4-110">IDE bileşik word yerine imleci altında tek belirteç seçer.</span><span class="sxs-lookup"><span data-stu-id="b72f4-110">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="b72f4-111">Kurallar</span><span class="sxs-lookup"><span data-stu-id="b72f4-111">Rules</span></span>

- <span data-ttu-id="b72f4-112">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="b72f4-112">**Declaration Context.**</span></span> <span data-ttu-id="b72f4-113">Kullanabileceğiniz `Private Protected` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="b72f4-113">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="b72f4-114">Bu bildirimi bağlamının anlamına gelir bir `Protected` öğesi bir sınıf olmalıdır ve bir kaynak dosyasını, ad alanı, arabirim, modülü, yapısı veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="b72f4-114">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="b72f4-115">Davranış</span><span class="sxs-lookup"><span data-stu-id="b72f4-115">Behavior</span></span>

- <span data-ttu-id="b72f4-116">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="b72f4-116">**Access Level.**</span></span> <span data-ttu-id="b72f4-117">Bir sınıftaki tüm kod öğeleri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="b72f4-117">All code in a class can access its elements.</span></span> <span data-ttu-id="b72f4-118">Bir taban sınıftan türeyen ve aynı bütünleştirilmiş kodda yer alan herhangi bir sınıf kodda tüm erişebilir `Private Protected` öğeleri temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="b72f4-118">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="b72f4-119">Ancak, bir taban sınıftan türeyen ve farklı bir derlemede bulunan herhangi bir sınıf kodda temel sınıfı erişemiyor `Private Protected` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b72f4-119">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="b72f4-120">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="b72f4-120">**Access Modifiers.**</span></span> <span data-ttu-id="b72f4-121">Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*.</span><span class="sxs-lookup"><span data-stu-id="b72f4-121">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="b72f4-122">Erişim değiştiricileri karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b72f4-122">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>
  
 <span data-ttu-id="b72f4-123">`Private Protected` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b72f4-123">The `Private Protected` modifier can be used in these contexts:</span></span>  
  
 <span data-ttu-id="b72f4-124">[Sınıf bildirimi](../../../visual-basic/language-reference/statements/class-statement.md) iç içe bir sınıf</span><span class="sxs-lookup"><span data-stu-id="b72f4-124">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>  
  
 [<span data-ttu-id="b72f4-125">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="b72f4-125">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="b72f4-126">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="b72f4-126">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="b72f4-127">[Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) temsilcisi iç içe bir sınıf</span><span class="sxs-lookup"><span data-stu-id="b72f4-127">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>  
  
 [<span data-ttu-id="b72f4-128">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="b72f4-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 <span data-ttu-id="b72f4-129">[Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md) bir eumeration iç içe bir sınıf</span><span class="sxs-lookup"><span data-stu-id="b72f4-129">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an eumeration nested in a class</span></span> 
  
 [<span data-ttu-id="b72f4-130">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="b72f4-130">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="b72f4-131">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="b72f4-131">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 <span data-ttu-id="b72f4-132">[İnterface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md) bir arabiriminin iç içe bir sınıf</span><span class="sxs-lookup"><span data-stu-id="b72f4-132">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span> 
  
 [<span data-ttu-id="b72f4-133">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="b72f4-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 <span data-ttu-id="b72f4-134">[Yapı deyimi](../../../visual-basic/language-reference/statements/structure-statement.md) yapısını iç içe bir sınıf</span><span class="sxs-lookup"><span data-stu-id="b72f4-134">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span> 
  
 [<span data-ttu-id="b72f4-135">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="b72f4-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b72f4-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b72f4-136">See Also</span></span>

[<span data-ttu-id="b72f4-137">Public</span><span class="sxs-lookup"><span data-stu-id="b72f4-137">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="b72f4-138">Protected</span><span class="sxs-lookup"><span data-stu-id="b72f4-138">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="b72f4-139">[Arkadaş](friend.md) </span><span class="sxs-lookup"><span data-stu-id="b72f4-139">[Friend](friend.md) </span></span>  
[<span data-ttu-id="b72f4-140">Private</span><span class="sxs-lookup"><span data-stu-id="b72f4-140">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="b72f4-141">[Korumalı Friend](./protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="b72f4-141">[Protected Friend](./protected-friend.md) </span></span>  
[<span data-ttu-id="b72f4-142">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="b72f4-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="b72f4-143">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b72f4-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="b72f4-144">Yapılar</span><span class="sxs-lookup"><span data-stu-id="b72f4-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="b72f4-145">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b72f4-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
