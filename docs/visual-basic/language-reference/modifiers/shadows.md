---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb767c372cc05d61d569227af8eef0dc3c67489b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="df919-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df919-102">Shadows (Visual Basic)</span></span>
<span data-ttu-id="df919-103">Bildirilen bir programlama öğesi redeclares ve bir aynı adlı öğesi ya da bir taban sınıf içinde aşırı yüklenmiş öğelerin gizler belirtir.</span><span class="sxs-lookup"><span data-stu-id="df919-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df919-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df919-104">Remarks</span></span>  
 <span data-ttu-id="df919-105">Gölgeleme ana amacı (olarak da bilinen olduğu *adıyla gizleme*) sınıf üyeleri tanımını korumak için.</span><span class="sxs-lookup"><span data-stu-id="df919-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="df919-106">Taban sınıf, bir önceden tanımlamış aynı ada sahip bir öğe oluşturan bir değişiklik uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="df919-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="df919-107">Bu durumda, `Shadows` değiştiricisi zorlar başvuran üyesine çözümlenmesi sınıfınız üzerinden tanımlanmış, yerine yeni bir temel sınıf öğesi için.</span><span class="sxs-lookup"><span data-stu-id="df919-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
 <span data-ttu-id="df919-108">Hem gölgeleme ve geçersiz kılma devralınan bir öğeyi yeniden tanımlamanız, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="df919-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="df919-109">Daha fazla bilgi için bkz: [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="df919-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="df919-110">Kurallar</span><span class="sxs-lookup"><span data-stu-id="df919-110">Rules</span></span>  
  
-   <span data-ttu-id="df919-111">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="df919-111">**Declaration Context.**</span></span> <span data-ttu-id="df919-112">Kullanabileceğiniz `Shadows` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="df919-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="df919-113">Bu bildirimi bağlamının anlamına gelir bir `Shadows` öğesi bir sınıf olmalıdır ve bir kaynak dosyasını, ad alanı, arabirim, modülü, yapısı veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="df919-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
     <span data-ttu-id="df919-114">Bir tek bildirimi deyimde yalnızca bir gölgeleme öğesi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df919-114">You can declare only one shadowing element in a single declaration statement.</span></span>  
  
-   <span data-ttu-id="df919-115">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="df919-115">**Combined Modifiers.**</span></span> <span data-ttu-id="df919-116">Belirtemeyeceğiniz `Shadows` ile birlikte `Overloads`, `Overrides`, veya `Static` aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="df919-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="df919-117">**Öğe türleri.**</span><span class="sxs-lookup"><span data-stu-id="df919-117">**Element Types.**</span></span> <span data-ttu-id="df919-118">Bildirilen öğe herhangi bir tür başka herhangi bir tür ile gölge.</span><span class="sxs-lookup"><span data-stu-id="df919-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="df919-119">Bir özellik veya başka bir özellik veya yordam yordamla gölge, parametreler ve dönüş türü taban sınıf özelliği veya yordam eşleştiğinden gerekmez.</span><span class="sxs-lookup"><span data-stu-id="df919-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>  
  
-   <span data-ttu-id="df919-120">**Erişme.**</span><span class="sxs-lookup"><span data-stu-id="df919-120">**Accessing.**</span></span> <span data-ttu-id="df919-121">Taban sınıfı gölgeli öğesinde da shadows türetilmiş sınıf içinde normalde gelen kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="df919-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="df919-122">Ancak, aşağıdaki maddeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="df919-122">However, the following considerations apply.</span></span>  
  
    -   <span data-ttu-id="df919-123">Gölgeleme öğesi kendisine başvuran kod erişilebilir durumda değilse, başvuru gölgeli öğesine çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="df919-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="df919-124">Örneğin, varsa bir `Private` öğesi shadows erişim izni yok kod bir temel sınıf öğesi `Private` öğe temel sınıf öğesi yerine erişir.</span><span class="sxs-lookup"><span data-stu-id="df919-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>  
  
    -   <span data-ttu-id="df919-125">Bir öğenin gölge, gölgeli öğe temel sınıf türü ile bildirilmedi nesnesi aracılığıyla erişmeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df919-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="df919-126">Üzerinden de erişebilirsiniz `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="df919-126">You can also access it through `MyBase`.</span></span>  
  
 <span data-ttu-id="df919-127">`Shadows` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="df919-127">The `Shadows` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="df919-128">Class deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="df919-129">Const deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="df919-130">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="df919-131">Delegate deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="df919-132">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="df919-133">Enum deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="df919-134">Event deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="df919-135">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="df919-136">Interface deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="df919-137">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="df919-138">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="df919-139">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="df919-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="df919-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df919-140">See Also</span></span>  
 [<span data-ttu-id="df919-141">Paylaşılan</span><span class="sxs-lookup"><span data-stu-id="df919-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="df919-142">Statik</span><span class="sxs-lookup"><span data-stu-id="df919-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="df919-143">Özel</span><span class="sxs-lookup"><span data-stu-id="df919-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="df919-144">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="df919-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="df919-145">Devralma temelleri</span><span class="sxs-lookup"><span data-stu-id="df919-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="df919-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="df919-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="df919-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="df919-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="df919-148">Aşırı yüklemeler</span><span class="sxs-lookup"><span data-stu-id="df919-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="df919-149">Geçersiz kılınabilir</span><span class="sxs-lookup"><span data-stu-id="df919-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="df919-150">Geçersiz kılmaları</span><span class="sxs-lookup"><span data-stu-id="df919-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="df919-151">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="df919-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
