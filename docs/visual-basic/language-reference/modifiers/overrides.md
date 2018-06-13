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
ms.openlocfilehash: 81118b9e97f320bffdbb58e5e1a2859052c4cee5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602536"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="c19f4-102">Geçersiz Kılmalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c19f4-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="c19f4-103">Bir özellik veya yordam aynı adlı bir özellik ya da bir taban sınıftan devralınan yordamı kıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c19f4-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c19f4-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c19f4-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c19f4-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="c19f4-105">Rules</span></span>  
  
-   <span data-ttu-id="c19f4-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="c19f4-106">**Declaration Context.**</span></span> <span data-ttu-id="c19f4-107">Kullanabileceğiniz `Overrides` yalnızca bir özellik veya yordam bildirimi deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="c19f4-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="c19f4-108">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="c19f4-108">**Combined Modifiers.**</span></span> <span data-ttu-id="c19f4-109">Belirtemeyeceğiniz `Overrides` ile birlikte `Shadows` veya `Shared` aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="c19f4-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="c19f4-110">Bir geçersiz kılma öğesi örtülü olarak geçersiz kılınabilir olduğundan birleştiremez `Overridable` ile `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="c19f4-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="c19f4-111">**Eşleşen imzalar.**</span><span class="sxs-lookup"><span data-stu-id="c19f4-111">**Matching Signatures.**</span></span> <span data-ttu-id="c19f4-112">Bu bildirim imzası tam olarak eşleşmelidir *imza* özelliği ya da bu geçersiz kılmaları yordamı.</span><span class="sxs-lookup"><span data-stu-id="c19f4-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="c19f4-113">Başka bir deyişle, aynı veri türleriyle aynı sırada parametreleri aynı sayıda parametre listeleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c19f4-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="c19f4-114">İmza yanı sıra geçersiz kılma bildirimi de tam olarak aşağıdaki eşleşmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="c19f4-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="c19f4-115">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="c19f4-115">The access level</span></span>  
  
    -   <span data-ttu-id="c19f4-116">Dönüş türü, varsa</span><span class="sxs-lookup"><span data-stu-id="c19f4-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="c19f4-117">**Genel imzalar.**</span><span class="sxs-lookup"><span data-stu-id="c19f4-117">**Generic Signatures.**</span></span> <span data-ttu-id="c19f4-118">Genel bir yordam için imza türü parametre sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="c19f4-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="c19f4-119">Bu nedenle, geçersiz kılma bildirimi de o açısından taban sınıf sürümle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c19f4-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="c19f4-120">**Ek eşleşen.**</span><span class="sxs-lookup"><span data-stu-id="c19f4-120">**Additional Matching.**</span></span> <span data-ttu-id="c19f4-121">Taban sınıfı sürüm imzası eşleştirmeye ek olarak, bu bildirim ayrıca, aşağıdaki yönden eşleşmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="c19f4-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="c19f4-122">Erişim düzeyi değiştiricisi (gibi [ortak](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="c19f4-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="c19f4-123">Her bir parametreyi mekanizması geçirme ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="c19f4-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="c19f4-124">Her bir genel yordam tür parametresinin kısıtlaması listeler</span><span class="sxs-lookup"><span data-stu-id="c19f4-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="c19f4-125">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="c19f4-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="c19f4-126">Hem gölgeleme ve geçersiz kılma devralınan bir öğeyi yeniden tanımlamanız, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="c19f4-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="c19f4-127">Daha fazla bilgi için bkz: [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="c19f4-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="c19f4-128">Kullanırsanız `Overrides`, derleyici örtük olarak ekler `Overloads` kitaplığınızın API'leri iş böylece C# ile daha kolay.</span><span class="sxs-lookup"><span data-stu-id="c19f4-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="c19f4-129">`Overrides` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c19f4-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c19f4-130">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="c19f4-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="c19f4-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="c19f4-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="c19f4-132">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="c19f4-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c19f4-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c19f4-133">See Also</span></span>  
 [<span data-ttu-id="c19f4-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="c19f4-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="c19f4-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="c19f4-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="c19f4-136">Overridable</span><span class="sxs-lookup"><span data-stu-id="c19f4-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="c19f4-137">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c19f4-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="c19f4-138">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="c19f4-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="c19f4-139">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="c19f4-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="c19f4-140">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="c19f4-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
