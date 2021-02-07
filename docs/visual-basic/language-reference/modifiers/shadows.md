---
description: 'Daha fazla bilgi edinin: gölgeler (Visual Basic)'
title: Shadows
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
ms.openlocfilehash: 4a455a78c36e15db977936b81c22e7a5b03d107e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700851"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="99b78-103">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99b78-103">Shadows (Visual Basic)</span></span>

<span data-ttu-id="99b78-104">Bir temel sınıfta, belirtilen bir programlama öğesinin, aynı adlı bir öğeyi yeniden bildirdiğini ve daha fazla yüklenmiş öğeler kümesini gizlediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="99b78-104">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="99b78-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99b78-105">Remarks</span></span>

<span data-ttu-id="99b78-106">Gölgeleme için ana amaç ( *ada göre gizleme* olarak da bilinir), sınıf üyelerinizin tanımını korur.</span><span class="sxs-lookup"><span data-stu-id="99b78-106">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="99b78-107">Temel sınıf, zaten tanımlamış olduğunuz adla aynı ada sahip bir öğe oluşturan bir değişikliği olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="99b78-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="99b78-108">Bu durumda, değiştirici, `Shadows` sınıfınızın içindeki başvuruyu, yeni temel sınıf öğesi yerine tanımladığınız üyeye çözümlenmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="99b78-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="99b78-109">Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="99b78-109">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="99b78-110">Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="99b78-110">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="99b78-111">Kurallar</span><span class="sxs-lookup"><span data-stu-id="99b78-111">Rules</span></span>

- <span data-ttu-id="99b78-112">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="99b78-112">**Declaration Context.**</span></span> <span data-ttu-id="99b78-113">`Shadows`Yalnızca sınıf düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99b78-113">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="99b78-114">Yani bir öğe için bildirim bağlamı `Shadows` bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="99b78-114">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="99b78-115">Tek bir bildirim ifadesinde yalnızca bir gölgeleme öğesi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99b78-115">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="99b78-116">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="99b78-116">**Combined Modifiers.**</span></span> <span data-ttu-id="99b78-117">`Shadows` `Overloads` Aynı bildirimde, veya ile birlikte belirtemezsiniz `Overrides` `Static` .</span><span class="sxs-lookup"><span data-stu-id="99b78-117">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="99b78-118">**Öğe türleri.**</span><span class="sxs-lookup"><span data-stu-id="99b78-118">**Element Types.**</span></span> <span data-ttu-id="99b78-119">Herhangi bir tür tanımlanmış öğeyi başka bir tür ile gölgelendirebilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="99b78-119">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="99b78-120">Bir özelliği veya yordamı başka bir özellik veya yordamla gölgelendirebiliyorsanız, parametrelerin ve dönüş türünün temel sınıf özelliği veya yordamındakilerle eşleşmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="99b78-120">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="99b78-121">**Erişme.**</span><span class="sxs-lookup"><span data-stu-id="99b78-121">**Accessing.**</span></span> <span data-ttu-id="99b78-122">Temel sınıftaki gölgelendirilmiş öğe, normalde onu gölgelendirilebilen türetilmiş sınıfın içinden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="99b78-122">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="99b78-123">Ancak aşağıdaki noktalar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="99b78-123">However, the following considerations apply.</span></span>

  - <span data-ttu-id="99b78-124">Gölgeleme öğesine başvuran koddan erişilebilir değilse, başvuru gölgelendirilmiş öğe olarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="99b78-124">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="99b78-125">Örneğin, bir öğe bir `Private` temel sınıf öğesini gölerse, öğesine erişim izni olmayan kod, `Private` bunun yerine temel sınıf öğesine erişir.</span><span class="sxs-lookup"><span data-stu-id="99b78-125">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="99b78-126">Bir öğeyi gölgelendiriseniz, taban sınıfının türüyle belirtilen bir nesne aracılığıyla gölgelendirilmiş öğeye erişmeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99b78-126">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="99b78-127">Ayrıca, üzerinden de erişebilirsiniz `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="99b78-127">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="99b78-128">`Shadows`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="99b78-128">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="99b78-129">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="99b78-129">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="99b78-130">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="99b78-130">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="99b78-131">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="99b78-131">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="99b78-132">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="99b78-132">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="99b78-133">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="99b78-133">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="99b78-134">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="99b78-134">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="99b78-135">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="99b78-135">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="99b78-136">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="99b78-136">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="99b78-137">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="99b78-137">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="99b78-138">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="99b78-138">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="99b78-139">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="99b78-139">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="99b78-140">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="99b78-140">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="99b78-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99b78-141">See also</span></span>

- [<span data-ttu-id="99b78-142">Paylaşılan</span><span class="sxs-lookup"><span data-stu-id="99b78-142">Shared</span></span>](shared.md)
- [<span data-ttu-id="99b78-143">Static</span><span class="sxs-lookup"><span data-stu-id="99b78-143">Static</span></span>](static.md)
- [<span data-ttu-id="99b78-144">Özel</span><span class="sxs-lookup"><span data-stu-id="99b78-144">Private</span></span>](private.md)
- [<span data-ttu-id="99b78-145">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="99b78-145">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="99b78-146">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="99b78-146">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="99b78-147">MustOverride</span><span class="sxs-lookup"><span data-stu-id="99b78-147">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="99b78-148">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="99b78-148">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="99b78-149">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="99b78-149">Overloads</span></span>](overloads.md)
- [<span data-ttu-id="99b78-150">Overridable</span><span class="sxs-lookup"><span data-stu-id="99b78-150">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="99b78-151">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="99b78-151">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="99b78-152">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="99b78-152">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
