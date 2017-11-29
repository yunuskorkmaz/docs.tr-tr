---
title: "Geçersiz Kılmalar (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1bee6a6235b87a7e20f087a73bef76e0fc7bf124
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="8f11e-102">Geçersiz Kılmalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f11e-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="8f11e-103">Bir özellik veya yordam aynı adlı bir özellik ya da bir taban sınıftan devralınan yordamı kıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f11e-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f11e-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f11e-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="8f11e-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="8f11e-105">Rules</span></span>  
  
-   <span data-ttu-id="8f11e-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="8f11e-106">**Declaration Context.**</span></span> <span data-ttu-id="8f11e-107">Kullanabileceğiniz `Overrides` yalnızca bir özellik veya yordam bildirimi deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="8f11e-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="8f11e-108">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="8f11e-108">**Combined Modifiers.**</span></span> <span data-ttu-id="8f11e-109">Belirtemeyeceğiniz `Overrides` ile birlikte `Shadows` veya `Shared` aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="8f11e-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="8f11e-110">Bir geçersiz kılma öğesi örtülü olarak geçersiz kılınabilir olduğundan birleştiremez `Overridable` ile `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="8f11e-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="8f11e-111">**Eşleşen imzalar.**</span><span class="sxs-lookup"><span data-stu-id="8f11e-111">**Matching Signatures.**</span></span> <span data-ttu-id="8f11e-112">Bu bildirim imzası tam olarak eşleşmelidir *imza* özelliği ya da bu geçersiz kılmaları yordamı.</span><span class="sxs-lookup"><span data-stu-id="8f11e-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="8f11e-113">Başka bir deyişle, aynı veri türleriyle aynı sırada parametreleri aynı sayıda parametre listeleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f11e-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="8f11e-114">İmza yanı sıra geçersiz kılma bildirimi de tam olarak aşağıdaki eşleşmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="8f11e-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="8f11e-115">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="8f11e-115">The access level</span></span>  
  
    -   <span data-ttu-id="8f11e-116">Dönüş türü, varsa</span><span class="sxs-lookup"><span data-stu-id="8f11e-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="8f11e-117">**Genel imzalar.**</span><span class="sxs-lookup"><span data-stu-id="8f11e-117">**Generic Signatures.**</span></span> <span data-ttu-id="8f11e-118">Genel bir yordam için imza türü parametre sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="8f11e-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="8f11e-119">Bu nedenle, geçersiz kılma bildirimi de o açısından taban sınıf sürümle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f11e-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="8f11e-120">**Ek eşleşen.**</span><span class="sxs-lookup"><span data-stu-id="8f11e-120">**Additional Matching.**</span></span> <span data-ttu-id="8f11e-121">Taban sınıfı sürüm imzası eşleştirmeye ek olarak, bu bildirim ayrıca, aşağıdaki yönden eşleşmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="8f11e-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="8f11e-122">Erişim düzeyi değiştiricisi (gibi [ortak](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="8f11e-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="8f11e-123">Her bir parametreyi mekanizması geçirme ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="8f11e-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="8f11e-124">Her bir genel yordam tür parametresinin kısıtlaması listeler</span><span class="sxs-lookup"><span data-stu-id="8f11e-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="8f11e-125">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="8f11e-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="8f11e-126">Hem gölgeleme ve geçersiz kılma devralınan bir öğeyi yeniden tanımlamanız, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="8f11e-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="8f11e-127">Daha fazla bilgi için bkz: [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="8f11e-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="8f11e-128">Kullanırsanız `Overrides`, derleyici örtük olarak ekler `Overloads` kitaplığınızın API'leri iş böylece C# ile daha kolay.</span><span class="sxs-lookup"><span data-stu-id="8f11e-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="8f11e-129">`Overrides` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="8f11e-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="8f11e-130">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="8f11e-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="8f11e-131">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="8f11e-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="8f11e-132">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="8f11e-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8f11e-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f11e-133">See Also</span></span>  
 [<span data-ttu-id="8f11e-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="8f11e-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="8f11e-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="8f11e-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="8f11e-136">Geçersiz kılınabilir</span><span class="sxs-lookup"><span data-stu-id="8f11e-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="8f11e-137">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="8f11e-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="8f11e-138">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="8f11e-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="8f11e-139">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="8f11e-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="8f11e-140">Tür listesi</span><span class="sxs-lookup"><span data-stu-id="8f11e-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
