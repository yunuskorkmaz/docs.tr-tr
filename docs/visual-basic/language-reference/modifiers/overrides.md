---
description: 'Hakkında daha fazla bilgi edinin: geçersiz kılmalar (Visual Basic)'
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
ms.openlocfilehash: d118bf4e366ff8f84806586dfc3977612ed6eff4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730453"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="f4b1e-103">Geçersiz Kılmalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4b1e-103">Overrides (Visual Basic)</span></span>

<span data-ttu-id="f4b1e-104">Bir özellik veya yordamın, bir temel sınıftan devralınan aynı adlı özelliği veya yordamı geçersiz kıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4b1e-104">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="f4b1e-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="f4b1e-105">Rules</span></span>

- <span data-ttu-id="f4b1e-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="f4b1e-106">**Declaration Context.**</span></span> <span data-ttu-id="f4b1e-107">`Overrides`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4b1e-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="f4b1e-108">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="f4b1e-108">**Combined Modifiers.**</span></span> <span data-ttu-id="f4b1e-109">`Overrides` `Shadows` Aynı bildirimde veya ile birlikte belirtemezsiniz `Shared` .</span><span class="sxs-lookup"><span data-stu-id="f4b1e-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="f4b1e-110">Geçersiz kılan bir öğe örtük olarak geçersiz kılınabilir olduğundan, `Overridable` ile birleştiremezsiniz `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="f4b1e-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="f4b1e-111">**Imza eşleşiyor.**</span><span class="sxs-lookup"><span data-stu-id="f4b1e-111">**Matching Signatures.**</span></span> <span data-ttu-id="f4b1e-112">Bu bildirimin imzası, geçersiz kıldığından özelliğin veya yordamın *imzasıyla* tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="f4b1e-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="f4b1e-113">Bu, parametre listelerinin aynı sırada aynı veri türleriyle aynı sayıda parametreye sahip olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f4b1e-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="f4b1e-114">İmzaya ek olarak, geçersiz kılma bildirimi de tam olarak aşağıdaki gibi eşleşmelidir:</span><span class="sxs-lookup"><span data-stu-id="f4b1e-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="f4b1e-115">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="f4b1e-115">The access level</span></span>

  - <span data-ttu-id="f4b1e-116">Varsa, dönüş türü</span><span class="sxs-lookup"><span data-stu-id="f4b1e-116">The return type, if any</span></span>

- <span data-ttu-id="f4b1e-117">**Genel Imzalar.**</span><span class="sxs-lookup"><span data-stu-id="f4b1e-117">**Generic Signatures.**</span></span> <span data-ttu-id="f4b1e-118">Genel yordam için imza, tür parametrelerinin sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="f4b1e-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="f4b1e-119">Bu nedenle, geçersiz kılma bildirimi aynı zamanda temel sınıf sürümüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="f4b1e-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="f4b1e-120">**Ek eşleşme.**</span><span class="sxs-lookup"><span data-stu-id="f4b1e-120">**Additional Matching.**</span></span> <span data-ttu-id="f4b1e-121">Bu bildirimin, temel sınıf sürümünün imzasını eşleştirmesinin yanı sıra aşağıdaki şekilde de eşleşmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="f4b1e-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="f4b1e-122">Erişim düzeyi değiştiricisi ( [genel](public.md)gibi)</span><span class="sxs-lookup"><span data-stu-id="f4b1e-122">Access-level modifier (such as [Public](public.md))</span></span>

  - <span data-ttu-id="f4b1e-123">Her parametrenin mekanizmasını geçirme ([ByVal](byval.md) veya [ByRef](byref.md))</span><span class="sxs-lookup"><span data-stu-id="f4b1e-123">Passing mechanism of each parameter ([ByVal](byval.md) or [ByRef](byref.md))</span></span>

  - <span data-ttu-id="f4b1e-124">Genel yordamın her tür parametresindeki kısıtlama listeleri</span><span class="sxs-lookup"><span data-stu-id="f4b1e-124">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="f4b1e-125">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="f4b1e-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="f4b1e-126">Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="f4b1e-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="f4b1e-127">Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f4b1e-127">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="f4b1e-128">Kullanırsanız `Overrides` , derleyici `Overloads` kitaplık API 'Lerinizin C# ile daha kolay çalışmasını sağlamak için örtülü olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="f4b1e-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="f4b1e-129">`Overrides`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f4b1e-129">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="f4b1e-130">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="f4b1e-130">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="f4b1e-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="f4b1e-131">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="f4b1e-132">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="f4b1e-132">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="f4b1e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4b1e-133">See also</span></span>

- [<span data-ttu-id="f4b1e-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="f4b1e-134">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="f4b1e-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="f4b1e-135">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="f4b1e-136">Overridable</span><span class="sxs-lookup"><span data-stu-id="f4b1e-136">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="f4b1e-137">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f4b1e-137">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="f4b1e-138">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="f4b1e-138">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="f4b1e-139">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="f4b1e-139">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="f4b1e-140">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="f4b1e-140">Type List</span></span>](../statements/type-list.md)
