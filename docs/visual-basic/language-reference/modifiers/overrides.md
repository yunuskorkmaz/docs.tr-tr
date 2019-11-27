---
title: Geçersiz Kılmalar
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
ms.openlocfilehash: 04f1cb27d6a8366c2dd13f8fdc1d975d382f1cfd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351382"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="7d08e-102">Geçersiz Kılmalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d08e-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="7d08e-103">Bir özellik veya yordamın, bir temel sınıftan devralınan aynı adlı özelliği veya yordamı geçersiz kıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d08e-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="7d08e-104">Kurallar</span><span class="sxs-lookup"><span data-stu-id="7d08e-104">Rules</span></span>

- <span data-ttu-id="7d08e-105">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="7d08e-105">**Declaration Context.**</span></span> <span data-ttu-id="7d08e-106">Yalnızca bir özellik veya yordam bildirimi ifadesinde `Overrides` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d08e-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="7d08e-107">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="7d08e-107">**Combined Modifiers.**</span></span> <span data-ttu-id="7d08e-108">Aynı bildirimde `Shadows` veya `Shared` birlikte `Overrides` belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d08e-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="7d08e-109">Geçersiz kılan bir öğe örtük olarak geçersiz kılınabilir olduğundan, `Overrides``Overridable` birleştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d08e-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="7d08e-110">**Imza eşleşiyor.**</span><span class="sxs-lookup"><span data-stu-id="7d08e-110">**Matching Signatures.**</span></span> <span data-ttu-id="7d08e-111">Bu bildirimin imzası, geçersiz kıldığından özelliğin veya yordamın *imzasıyla* tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7d08e-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="7d08e-112">Bu, parametre listelerinin aynı sırada aynı veri türleriyle aynı sayıda parametreye sahip olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7d08e-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="7d08e-113">İmzaya ek olarak, geçersiz kılma bildirimi de tam olarak aşağıdaki gibi eşleşmelidir:</span><span class="sxs-lookup"><span data-stu-id="7d08e-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="7d08e-114">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="7d08e-114">The access level</span></span>

  - <span data-ttu-id="7d08e-115">Varsa, dönüş türü</span><span class="sxs-lookup"><span data-stu-id="7d08e-115">The return type, if any</span></span>

- <span data-ttu-id="7d08e-116">**Genel Imzalar.**</span><span class="sxs-lookup"><span data-stu-id="7d08e-116">**Generic Signatures.**</span></span> <span data-ttu-id="7d08e-117">Genel yordam için imza, tür parametrelerinin sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="7d08e-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="7d08e-118">Bu nedenle, geçersiz kılma bildirimi aynı zamanda temel sınıf sürümüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7d08e-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="7d08e-119">**Ek eşleşme.**</span><span class="sxs-lookup"><span data-stu-id="7d08e-119">**Additional Matching.**</span></span> <span data-ttu-id="7d08e-120">Bu bildirimin, temel sınıf sürümünün imzasını eşleştirmesinin yanı sıra aşağıdaki şekilde de eşleşmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="7d08e-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="7d08e-121">Erişim düzeyi değiştiricisi ( [genel](../../../visual-basic/language-reference/modifiers/public.md)gibi)</span><span class="sxs-lookup"><span data-stu-id="7d08e-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>

  - <span data-ttu-id="7d08e-122">Her parametrenin mekanizmasını geçirme ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="7d08e-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>

  - <span data-ttu-id="7d08e-123">Genel yordamın her tür parametresindeki kısıtlama listeleri</span><span class="sxs-lookup"><span data-stu-id="7d08e-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="7d08e-124">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="7d08e-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="7d08e-125">Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="7d08e-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="7d08e-126">Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7d08e-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="7d08e-127">`Overrides`kullanırsanız, derleyici kitaplık API 'lerinizin C# daha kolay bir şekilde çalışması için `Overloads` dolaylı olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="7d08e-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="7d08e-128">`Overrides` değiştiricisi şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7d08e-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="7d08e-129">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="7d08e-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="7d08e-130">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="7d08e-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="7d08e-131">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="7d08e-131">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="7d08e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d08e-132">See also</span></span>

- [<span data-ttu-id="7d08e-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="7d08e-133">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="7d08e-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="7d08e-134">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="7d08e-135">Overridable</span><span class="sxs-lookup"><span data-stu-id="7d08e-135">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="7d08e-136">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="7d08e-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="7d08e-137">Visual Basic gölgeleme</span><span class="sxs-lookup"><span data-stu-id="7d08e-137">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="7d08e-138">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="7d08e-138">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="7d08e-139">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="7d08e-139">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
