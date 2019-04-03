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
ms.openlocfilehash: 9eb19bf5e89b12a32cae28b2c087570acc10f3ad
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826593"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="489a9-102">Geçersiz Kılmalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="489a9-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="489a9-103">Bir özelliğin ya da yordamın bir aynı adlı bir özellik ya da bir temel sınıftan devralınan yordamın kıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="489a9-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="489a9-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="489a9-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="489a9-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="489a9-105">Rules</span></span>  
  
-   <span data-ttu-id="489a9-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="489a9-106">**Declaration Context.**</span></span> <span data-ttu-id="489a9-107">Kullanabileceğiniz `Overrides` yalnızca bir özellik veya yordamı bildirim deyiminde.</span><span class="sxs-lookup"><span data-stu-id="489a9-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="489a9-108">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="489a9-108">**Combined Modifiers.**</span></span> <span data-ttu-id="489a9-109">Belirtemezsiniz `Overrides` ile birlikte `Shadows` veya `Shared` aynı bildirimde.</span><span class="sxs-lookup"><span data-stu-id="489a9-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="489a9-110">Bir geçersiz kılma öğesi örtük olarak geçersiz kılınabilir olduğundan birleştiremezsiniz `Overridable` ile `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="489a9-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="489a9-111">**Eşleşen imzalar.**</span><span class="sxs-lookup"><span data-stu-id="489a9-111">**Matching Signatures.**</span></span> <span data-ttu-id="489a9-112">Bu bildirim imzası tam olarak eşleşmelidir *imza* özellik ya da onu geçersiz kılar yordamı.</span><span class="sxs-lookup"><span data-stu-id="489a9-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="489a9-113">Başka bir deyişle, aynı sırayla, aynı veri türleriyle parametreleri aynı sayıda parametre listeleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="489a9-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="489a9-114">İmza ek olarak, geçersiz kılma bildirimi de tam olarak şu eşleşmelidir:</span><span class="sxs-lookup"><span data-stu-id="489a9-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="489a9-115">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="489a9-115">The access level</span></span>  
  
    -   <span data-ttu-id="489a9-116">Dönüş türü, varsa</span><span class="sxs-lookup"><span data-stu-id="489a9-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="489a9-117">**Genel imzalar.**</span><span class="sxs-lookup"><span data-stu-id="489a9-117">**Generic Signatures.**</span></span> <span data-ttu-id="489a9-118">Genel bir yordam için imza türü parametre sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="489a9-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="489a9-119">Bu nedenle, geçersiz kılma bildirimi de bu açısından temel sınıftaki sürümün eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="489a9-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="489a9-120">**Ek eşleştirme.**</span><span class="sxs-lookup"><span data-stu-id="489a9-120">**Additional Matching.**</span></span> <span data-ttu-id="489a9-121">Temel sınıftaki sürümün imzası eşleşen ek olarak, bu bildirimi Ayrıca, şu açılardan eşleşmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="489a9-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="489a9-122">Erişim düzeyi değiştirici (gibi [genel](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="489a9-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="489a9-123">Her parametre mekanizması geçirme ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="489a9-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="489a9-124">Genel bir yordam üzerinde her tür parametresi kısıtlaması listeler</span><span class="sxs-lookup"><span data-stu-id="489a9-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="489a9-125">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="489a9-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="489a9-126">Devralınan bir öğe hem gölgeleme ve geçersiz kılma bulunabileceğini, ancak iki yaklaşım arasında önemli farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="489a9-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="489a9-127">Daha fazla bilgi için [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="489a9-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="489a9-128">Kullanırsanız `Overrides`, derleyicinin dolaylı olarak ekler `Overloads` kitaplığınızı API'leri ile çalışmak üzere C# daha kolay.</span><span class="sxs-lookup"><span data-stu-id="489a9-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="489a9-129">`Overrides` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="489a9-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="489a9-130">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="489a9-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="489a9-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="489a9-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="489a9-132">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="489a9-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="489a9-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="489a9-133">See also</span></span>

- [<span data-ttu-id="489a9-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="489a9-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="489a9-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="489a9-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="489a9-136">Overridable</span><span class="sxs-lookup"><span data-stu-id="489a9-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="489a9-137">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="489a9-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="489a9-138">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="489a9-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="489a9-139">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="489a9-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="489a9-140">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="489a9-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
