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
ms.openlocfilehash: 657f838b2959a5b6a7cef5ff18295a4ada709e9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392034"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="294ec-102">Geçersiz Kılmalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="294ec-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="294ec-103">Bir özellik veya yordamın, bir temel sınıftan devralınan aynı adlı özelliği veya yordamı geçersiz kıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="294ec-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="294ec-104">Kurallar</span><span class="sxs-lookup"><span data-stu-id="294ec-104">Rules</span></span>

- <span data-ttu-id="294ec-105">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="294ec-105">**Declaration Context.**</span></span> <span data-ttu-id="294ec-106">`Overrides`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="294ec-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="294ec-107">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="294ec-107">**Combined Modifiers.**</span></span> <span data-ttu-id="294ec-108">`Overrides` `Shadows` Aynı bildirimde veya ile birlikte belirtemezsiniz `Shared` .</span><span class="sxs-lookup"><span data-stu-id="294ec-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="294ec-109">Geçersiz kılan bir öğe örtük olarak geçersiz kılınabilir olduğundan, `Overridable` ile birleştiremezsiniz `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="294ec-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="294ec-110">**Imza eşleşiyor.**</span><span class="sxs-lookup"><span data-stu-id="294ec-110">**Matching Signatures.**</span></span> <span data-ttu-id="294ec-111">Bu bildirimin imzası, geçersiz kıldığından özelliğin veya yordamın *imzasıyla* tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="294ec-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="294ec-112">Bu, parametre listelerinin aynı sırada aynı veri türleriyle aynı sayıda parametreye sahip olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="294ec-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="294ec-113">İmzaya ek olarak, geçersiz kılma bildirimi de tam olarak aşağıdaki gibi eşleşmelidir:</span><span class="sxs-lookup"><span data-stu-id="294ec-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="294ec-114">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="294ec-114">The access level</span></span>

  - <span data-ttu-id="294ec-115">Varsa, dönüş türü</span><span class="sxs-lookup"><span data-stu-id="294ec-115">The return type, if any</span></span>

- <span data-ttu-id="294ec-116">**Genel Imzalar.**</span><span class="sxs-lookup"><span data-stu-id="294ec-116">**Generic Signatures.**</span></span> <span data-ttu-id="294ec-117">Genel yordam için imza, tür parametrelerinin sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="294ec-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="294ec-118">Bu nedenle, geçersiz kılma bildirimi aynı zamanda temel sınıf sürümüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="294ec-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="294ec-119">**Ek eşleşme.**</span><span class="sxs-lookup"><span data-stu-id="294ec-119">**Additional Matching.**</span></span> <span data-ttu-id="294ec-120">Bu bildirimin, temel sınıf sürümünün imzasını eşleştirmesinin yanı sıra aşağıdaki şekilde de eşleşmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="294ec-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="294ec-121">Erişim düzeyi değiştiricisi ( [genel](public.md)gibi)</span><span class="sxs-lookup"><span data-stu-id="294ec-121">Access-level modifier (such as [Public](public.md))</span></span>

  - <span data-ttu-id="294ec-122">Her parametrenin mekanizmasını geçirme ([ByVal](byval.md) veya [ByRef](byref.md))</span><span class="sxs-lookup"><span data-stu-id="294ec-122">Passing mechanism of each parameter ([ByVal](byval.md) or [ByRef](byref.md))</span></span>

  - <span data-ttu-id="294ec-123">Genel yordamın her tür parametresindeki kısıtlama listeleri</span><span class="sxs-lookup"><span data-stu-id="294ec-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="294ec-124">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="294ec-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="294ec-125">Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="294ec-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="294ec-126">Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="294ec-126">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="294ec-127">Kullanırsanız `Overrides` , derleyici `Overloads` kitaplık API 'Lerinizin C# ile daha kolay çalışmasını sağlamak için örtülü olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="294ec-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="294ec-128">`Overrides`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="294ec-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="294ec-129">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="294ec-129">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="294ec-130">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="294ec-130">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="294ec-131">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="294ec-131">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="294ec-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="294ec-132">See also</span></span>

- [<span data-ttu-id="294ec-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="294ec-133">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="294ec-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="294ec-134">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="294ec-135">Overridable</span><span class="sxs-lookup"><span data-stu-id="294ec-135">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="294ec-136">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="294ec-136">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="294ec-137">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="294ec-137">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="294ec-138">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="294ec-138">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="294ec-139">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="294ec-139">Type List</span></span>](../statements/type-list.md)
