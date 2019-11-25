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
ms.openlocfilehash: e9a423fa69ad1dcd8c1d4a5b7085e5b5da548f93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351270"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="614f0-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="614f0-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="614f0-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span><span class="sxs-lookup"><span data-stu-id="614f0-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="614f0-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="614f0-104">Remarks</span></span>

<span data-ttu-id="614f0-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span><span class="sxs-lookup"><span data-stu-id="614f0-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="614f0-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span><span class="sxs-lookup"><span data-stu-id="614f0-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="614f0-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span><span class="sxs-lookup"><span data-stu-id="614f0-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="614f0-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span><span class="sxs-lookup"><span data-stu-id="614f0-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="614f0-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="614f0-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="614f0-110">Kurallar</span><span class="sxs-lookup"><span data-stu-id="614f0-110">Rules</span></span>

- <span data-ttu-id="614f0-111">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="614f0-111">**Declaration Context.**</span></span> <span data-ttu-id="614f0-112">You can use `Shadows` only at class level.</span><span class="sxs-lookup"><span data-stu-id="614f0-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="614f0-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span><span class="sxs-lookup"><span data-stu-id="614f0-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="614f0-114">You can declare only one shadowing element in a single declaration statement.</span><span class="sxs-lookup"><span data-stu-id="614f0-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="614f0-115">**Combined Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="614f0-115">**Combined Modifiers.**</span></span> <span data-ttu-id="614f0-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="614f0-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="614f0-117">**Element Types.**</span><span class="sxs-lookup"><span data-stu-id="614f0-117">**Element Types.**</span></span> <span data-ttu-id="614f0-118">You can shadow any kind of declared element with any other kind.</span><span class="sxs-lookup"><span data-stu-id="614f0-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="614f0-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span><span class="sxs-lookup"><span data-stu-id="614f0-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="614f0-120">**Accessing.**</span><span class="sxs-lookup"><span data-stu-id="614f0-120">**Accessing.**</span></span> <span data-ttu-id="614f0-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span><span class="sxs-lookup"><span data-stu-id="614f0-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="614f0-122">However, the following considerations apply.</span><span class="sxs-lookup"><span data-stu-id="614f0-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="614f0-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span><span class="sxs-lookup"><span data-stu-id="614f0-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="614f0-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span><span class="sxs-lookup"><span data-stu-id="614f0-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="614f0-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span><span class="sxs-lookup"><span data-stu-id="614f0-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="614f0-126">You can also access it through `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="614f0-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="614f0-127">The `Shadows` modifier can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="614f0-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="614f0-128">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="614f0-129">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="614f0-130">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="614f0-131">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="614f0-132">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- [<span data-ttu-id="614f0-133">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)

- [<span data-ttu-id="614f0-134">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="614f0-135">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="614f0-136">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)

- [<span data-ttu-id="614f0-137">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="614f0-138">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

- [<span data-ttu-id="614f0-139">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="614f0-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="614f0-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="614f0-140">See also</span></span>

- [<span data-ttu-id="614f0-141">Shared</span><span class="sxs-lookup"><span data-stu-id="614f0-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="614f0-142">Static</span><span class="sxs-lookup"><span data-stu-id="614f0-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="614f0-143">Private</span><span class="sxs-lookup"><span data-stu-id="614f0-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="614f0-144">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="614f0-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="614f0-145">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="614f0-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="614f0-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="614f0-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="614f0-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="614f0-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="614f0-148">Overloads</span><span class="sxs-lookup"><span data-stu-id="614f0-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="614f0-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="614f0-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="614f0-150">Overrides</span><span class="sxs-lookup"><span data-stu-id="614f0-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="614f0-151">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="614f0-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
