---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: c314db90a1a0f89613e20897387bdec8ec534837
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834146"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="1319f-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1319f-102">Shadows (Visual Basic)</span></span>
<span data-ttu-id="1319f-103">Bildirilmiş bir programlama öğesinin redeclares ve bir aynı adlı bir öğe veya taban sınıfında aşırı yüklenmiş bir öğe kümesini gizler belirtir.</span><span class="sxs-lookup"><span data-stu-id="1319f-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1319f-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1319f-104">Remarks</span></span>  
 <span data-ttu-id="1319f-105">Gölgeleme ana amacı (olarak da bilinen olduğu *adına göre gizleme*), sınıf üyelerinin tanımına korumak için.</span><span class="sxs-lookup"><span data-stu-id="1319f-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="1319f-106">Temel sınıf olarak zaten tanımlanmış aynı ada sahip bir öğe oluşturan bir değişiklik uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1319f-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="1319f-107">Böyle bir durumda `Shadows` değiştiricisi zorlar başvuruyor, sınıf üyesine çözümlenmesi aracılığıyla tanımlanmış, yerine yeni bir temel sınıf öğe için.</span><span class="sxs-lookup"><span data-stu-id="1319f-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
 <span data-ttu-id="1319f-108">Devralınan bir öğe hem gölgeleme ve geçersiz kılma bulunabileceğini, ancak iki yaklaşım arasında önemli farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="1319f-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="1319f-109">Daha fazla bilgi için [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="1319f-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1319f-110">Kurallar</span><span class="sxs-lookup"><span data-stu-id="1319f-110">Rules</span></span>  
  
-   <span data-ttu-id="1319f-111">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="1319f-111">**Declaration Context.**</span></span> <span data-ttu-id="1319f-112">Kullanabileceğiniz `Shadows` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="1319f-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="1319f-113">Bildirim bağlamı başka bir deyişle bir `Shadows` öğesi bir sınıf olması gerekir ve bir kaynak dosyası, ad alanı, arabirim, modülü, yapı veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="1319f-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
     <span data-ttu-id="1319f-114">Bir tek bir bildirim deyiminde yalnızca bir gölgeleme öğesi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1319f-114">You can declare only one shadowing element in a single declaration statement.</span></span>  
  
-   <span data-ttu-id="1319f-115">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="1319f-115">**Combined Modifiers.**</span></span> <span data-ttu-id="1319f-116">Belirtemezsiniz `Shadows` ile birlikte `Overloads`, `Overrides`, veya `Static` aynı bildirimde.</span><span class="sxs-lookup"><span data-stu-id="1319f-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="1319f-117">**Öğe türleri.**</span><span class="sxs-lookup"><span data-stu-id="1319f-117">**Element Types.**</span></span> <span data-ttu-id="1319f-118">Bildirilen öğe herhangi bir türden başka bir tür ile gölge.</span><span class="sxs-lookup"><span data-stu-id="1319f-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="1319f-119">Bir özellik ya da başka bir özellik ya da yordamın yordamla gölge, parametreler ve dönüş türü temel sınıfın özellik veya yordamı içindeki alanlarla eşleşmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1319f-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>  
  
-   <span data-ttu-id="1319f-120">**Erişme.**</span><span class="sxs-lookup"><span data-stu-id="1319f-120">**Accessing.**</span></span> <span data-ttu-id="1319f-121">Gölgeli öğe temel sınıfta bu gölgeleri türetilmiş sınıf içinde normalde gelen kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="1319f-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="1319f-122">Ancak, aşağıdaki maddeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1319f-122">However, the following considerations apply.</span></span>  
  
    -   <span data-ttu-id="1319f-123">Gölgeleme öğesi kendisine başvuran koddan erişilebilir durumda değilse, başvuruyu gölgeli öğesine çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="1319f-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="1319f-124">Örneğin, bir `Private` öğesi bir temel sınıf öğesi, erişim iznine sahip olmayan kod gölgeliyor `Private` öğe temel sınıf öğe yerine erişir.</span><span class="sxs-lookup"><span data-stu-id="1319f-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>  
  
    -   <span data-ttu-id="1319f-125">Bir öğe gölge, gölgeli öğe türü temel sınıfı ile bildirilen bir nesne üzerinden erişmeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1319f-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="1319f-126">Üzerinden de erişebilirsiniz `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="1319f-126">You can also access it through `MyBase`.</span></span>  
  
 <span data-ttu-id="1319f-127">`Shadows` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1319f-127">The `Shadows` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1319f-128">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="1319f-129">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="1319f-130">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="1319f-131">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="1319f-132">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="1319f-133">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="1319f-134">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="1319f-135">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="1319f-136">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="1319f-137">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="1319f-138">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="1319f-139">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="1319f-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1319f-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1319f-140">See also</span></span>

- [<span data-ttu-id="1319f-141">Shared</span><span class="sxs-lookup"><span data-stu-id="1319f-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="1319f-142">Static</span><span class="sxs-lookup"><span data-stu-id="1319f-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="1319f-143">Private</span><span class="sxs-lookup"><span data-stu-id="1319f-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="1319f-144">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="1319f-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="1319f-145">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="1319f-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="1319f-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="1319f-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="1319f-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="1319f-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="1319f-148">Overloads</span><span class="sxs-lookup"><span data-stu-id="1319f-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="1319f-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="1319f-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="1319f-150">Overrides</span><span class="sxs-lookup"><span data-stu-id="1319f-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="1319f-151">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="1319f-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
