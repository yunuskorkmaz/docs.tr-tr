---
title: Geçersiz Kılmalar (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 7fff91d993743574d13030aa3d5cc1e462e76838
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751033"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="060b3-102">Geçersiz Kılmalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="060b3-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="060b3-103">Bir özelliğin ya da yordamın bir aynı adlı bir özellik ya da bir temel sınıftan devralınan yordamın kıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="060b3-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="060b3-104">Kurallar</span><span class="sxs-lookup"><span data-stu-id="060b3-104">Rules</span></span>

- <span data-ttu-id="060b3-105">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="060b3-105">**Declaration Context.**</span></span> <span data-ttu-id="060b3-106">Kullanabileceğiniz `Overrides` yalnızca bir özellik veya yordamı bildirim deyiminde.</span><span class="sxs-lookup"><span data-stu-id="060b3-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="060b3-107">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="060b3-107">**Combined Modifiers.**</span></span> <span data-ttu-id="060b3-108">Belirtemezsiniz `Overrides` ile birlikte `Shadows` veya `Shared` aynı bildirimde.</span><span class="sxs-lookup"><span data-stu-id="060b3-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="060b3-109">Bir geçersiz kılma öğesi örtük olarak geçersiz kılınabilir olduğundan birleştiremezsiniz `Overridable` ile `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="060b3-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="060b3-110">**Eşleşen imzalar.**</span><span class="sxs-lookup"><span data-stu-id="060b3-110">**Matching Signatures.**</span></span> <span data-ttu-id="060b3-111">Bu bildirim imzası tam olarak eşleşmelidir *imza* özellik ya da onu geçersiz kılar yordamı.</span><span class="sxs-lookup"><span data-stu-id="060b3-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="060b3-112">Başka bir deyişle, aynı sırayla, aynı veri türleriyle parametreleri aynı sayıda parametre listeleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="060b3-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="060b3-113">İmza ek olarak, geçersiz kılma bildirimi de tam olarak şu eşleşmelidir:</span><span class="sxs-lookup"><span data-stu-id="060b3-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="060b3-114">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="060b3-114">The access level</span></span>

  - <span data-ttu-id="060b3-115">Dönüş türü, varsa</span><span class="sxs-lookup"><span data-stu-id="060b3-115">The return type, if any</span></span>

- <span data-ttu-id="060b3-116">**Genel imzalar.**</span><span class="sxs-lookup"><span data-stu-id="060b3-116">**Generic Signatures.**</span></span> <span data-ttu-id="060b3-117">Genel bir yordam için imza türü parametre sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="060b3-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="060b3-118">Bu nedenle, geçersiz kılma bildirimi de bu açısından temel sınıftaki sürümün eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="060b3-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="060b3-119">**Ek eşleştirme.**</span><span class="sxs-lookup"><span data-stu-id="060b3-119">**Additional Matching.**</span></span> <span data-ttu-id="060b3-120">Temel sınıftaki sürümün imzası eşleşen ek olarak, bu bildirimi Ayrıca, şu açılardan eşleşmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="060b3-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="060b3-121">Erişim düzeyi değiştirici (gibi [genel](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="060b3-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>

  - <span data-ttu-id="060b3-122">Her parametre mekanizması geçirme ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="060b3-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>

  - <span data-ttu-id="060b3-123">Genel bir yordam üzerinde her tür parametresi kısıtlaması listeler</span><span class="sxs-lookup"><span data-stu-id="060b3-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="060b3-124">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="060b3-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="060b3-125">Devralınan bir öğe hem gölgeleme ve geçersiz kılma bulunabileceğini, ancak iki yaklaşım arasında önemli farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="060b3-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="060b3-126">Daha fazla bilgi için [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="060b3-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="060b3-127">Kullanırsanız `Overrides`, derleyicinin dolaylı olarak ekler `Overloads` kitaplığınızı API'leri ile çalışmak üzere C# daha kolay.</span><span class="sxs-lookup"><span data-stu-id="060b3-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="060b3-128">`Overrides` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="060b3-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="060b3-129">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="060b3-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="060b3-130">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="060b3-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="060b3-131">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="060b3-131">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="060b3-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="060b3-132">See also</span></span>

- [<span data-ttu-id="060b3-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="060b3-133">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="060b3-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="060b3-134">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="060b3-135">Overridable</span><span class="sxs-lookup"><span data-stu-id="060b3-135">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="060b3-136">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="060b3-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="060b3-137">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="060b3-137">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="060b3-138">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="060b3-138">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="060b3-139">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="060b3-139">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
