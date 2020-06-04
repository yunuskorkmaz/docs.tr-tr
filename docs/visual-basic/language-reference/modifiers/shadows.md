---
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
ms.openlocfilehash: 7aed6bec21bd484cca019b061bd5915de13a9eb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402713"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="830e6-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="830e6-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="830e6-103">Bir temel sınıfta, belirtilen bir programlama öğesinin, aynı adlı bir öğeyi yeniden bildirdiğini ve daha fazla yüklenmiş öğeler kümesini gizlediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="830e6-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="830e6-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="830e6-104">Remarks</span></span>

<span data-ttu-id="830e6-105">Gölgeleme için ana amaç ( *ada göre gizleme*olarak da bilinir), sınıf üyelerinizin tanımını korur.</span><span class="sxs-lookup"><span data-stu-id="830e6-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="830e6-106">Temel sınıf, zaten tanımlamış olduğunuz adla aynı ada sahip bir öğe oluşturan bir değişikliği olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="830e6-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="830e6-107">Bu durumda, değiştirici, `Shadows` sınıfınızın içindeki başvuruyu, yeni temel sınıf öğesi yerine tanımladığınız üyeye çözümlenmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="830e6-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="830e6-108">Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="830e6-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="830e6-109">Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="830e6-109">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="830e6-110">Kurallar</span><span class="sxs-lookup"><span data-stu-id="830e6-110">Rules</span></span>

- <span data-ttu-id="830e6-111">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="830e6-111">**Declaration Context.**</span></span> <span data-ttu-id="830e6-112">`Shadows`Yalnızca sınıf düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="830e6-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="830e6-113">Yani bir öğe için bildirim bağlamı `Shadows` bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="830e6-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="830e6-114">Tek bir bildirim ifadesinde yalnızca bir gölgeleme öğesi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="830e6-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="830e6-115">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="830e6-115">**Combined Modifiers.**</span></span> <span data-ttu-id="830e6-116">`Shadows` `Overloads` Aynı bildirimde, veya ile birlikte belirtemezsiniz `Overrides` `Static` .</span><span class="sxs-lookup"><span data-stu-id="830e6-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="830e6-117">**Öğe türleri.**</span><span class="sxs-lookup"><span data-stu-id="830e6-117">**Element Types.**</span></span> <span data-ttu-id="830e6-118">Herhangi bir tür tanımlanmış öğeyi başka bir tür ile gölgelendirebilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="830e6-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="830e6-119">Bir özelliği veya yordamı başka bir özellik veya yordamla gölgelendirebiliyorsanız, parametrelerin ve dönüş türünün temel sınıf özelliği veya yordamındakilerle eşleşmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="830e6-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="830e6-120">**Erişme.**</span><span class="sxs-lookup"><span data-stu-id="830e6-120">**Accessing.**</span></span> <span data-ttu-id="830e6-121">Temel sınıftaki gölgelendirilmiş öğe, normalde onu gölgelendirilebilen türetilmiş sınıfın içinden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="830e6-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="830e6-122">Ancak aşağıdaki noktalar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="830e6-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="830e6-123">Gölgeleme öğesine başvuran koddan erişilebilir değilse, başvuru gölgelendirilmiş öğe olarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="830e6-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="830e6-124">Örneğin, bir öğe bir `Private` temel sınıf öğesini gölerse, öğesine erişim izni olmayan kod, `Private` bunun yerine temel sınıf öğesine erişir.</span><span class="sxs-lookup"><span data-stu-id="830e6-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="830e6-125">Bir öğeyi gölgelendiriseniz, taban sınıfının türüyle belirtilen bir nesne aracılığıyla gölgelendirilmiş öğeye erişmeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="830e6-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="830e6-126">Ayrıca, üzerinden de erişebilirsiniz `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="830e6-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="830e6-127">`Shadows`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="830e6-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="830e6-128">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="830e6-128">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="830e6-129">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="830e6-129">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="830e6-130">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="830e6-130">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="830e6-131">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="830e6-131">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="830e6-132">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="830e6-132">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="830e6-133">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="830e6-133">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="830e6-134">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="830e6-134">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="830e6-135">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="830e6-135">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="830e6-136">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="830e6-136">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="830e6-137">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="830e6-137">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="830e6-138">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="830e6-138">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="830e6-139">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="830e6-139">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="830e6-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="830e6-140">See also</span></span>

- [<span data-ttu-id="830e6-141">Shared</span><span class="sxs-lookup"><span data-stu-id="830e6-141">Shared</span></span>](shared.md)
- [<span data-ttu-id="830e6-142">Se</span><span class="sxs-lookup"><span data-stu-id="830e6-142">Static</span></span>](static.md)
- [<span data-ttu-id="830e6-143">Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="830e6-143">Private</span></span>](private.md)
- [<span data-ttu-id="830e6-144">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="830e6-144">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="830e6-145">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="830e6-145">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="830e6-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="830e6-146">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="830e6-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="830e6-147">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="830e6-148">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="830e6-148">Overloads</span></span>](overloads.md)
- [<span data-ttu-id="830e6-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="830e6-149">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="830e6-150">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="830e6-150">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="830e6-151">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="830e6-151">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
