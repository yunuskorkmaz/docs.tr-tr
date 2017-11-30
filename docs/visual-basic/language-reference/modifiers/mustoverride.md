---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a2f7bdba4b01bd307e0c52802509669f772b5eb5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="4ea5f-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ea5f-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="4ea5f-103">Bir özellik veya yordam bu sınıfta uygulanmadı ve kullanılabilmesi için türetilen bir sınıfta geçersiz kılınmalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ea5f-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ea5f-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ea5f-104">Remarks</span></span>  
 <span data-ttu-id="4ea5f-105">Kullanabileceğiniz `MustOverride` yalnızca bir özellik veya yordam bildirimi deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="4ea5f-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="4ea5f-106">Özellik veya belirtir yordamı `MustOverride` bir sınıf üyesi olması gerekir ve sınıf işaretlenmelidir [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="4ea5f-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4ea5f-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="4ea5f-107">Rules</span></span>  
  
-   <span data-ttu-id="4ea5f-108">**Tamamlanmamış bildirimi.**</span><span class="sxs-lookup"><span data-stu-id="4ea5f-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="4ea5f-109">Belirttiğinizde `MustOverride`, özellik veya yordam, kodun ek satırları değil sağlamazsanız bile `End Function`, `End Property`, veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4ea5f-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="4ea5f-110">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="4ea5f-110">**Combined Modifiers.**</span></span> <span data-ttu-id="4ea5f-111">Belirtemeyeceğiniz `MustOverride` ile birlikte `NotOverridable`, `Overridable`, veya `Shared` aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="4ea5f-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
-   <span data-ttu-id="4ea5f-112">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="4ea5f-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="4ea5f-113">Hem gölgeleme ve geçersiz kılma devralınan bir öğeyi yeniden tanımlamanız, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="4ea5f-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="4ea5f-114">Daha fazla bilgi için bkz: [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="4ea5f-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
-   <span data-ttu-id="4ea5f-115">**Diğer koşulları.**</span><span class="sxs-lookup"><span data-stu-id="4ea5f-115">**Alternate Terms.**</span></span> <span data-ttu-id="4ea5f-116">Geçersiz kılma dışında kullanılamaz bir öğe adlandırılan bir *saf sanal* öğesi.</span><span class="sxs-lookup"><span data-stu-id="4ea5f-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="4ea5f-117">`MustOverride` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4ea5f-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="4ea5f-118">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="4ea5f-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="4ea5f-119">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="4ea5f-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="4ea5f-120">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="4ea5f-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4ea5f-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ea5f-121">See Also</span></span>  
 [<span data-ttu-id="4ea5f-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="4ea5f-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="4ea5f-123">Geçersiz kılınabilir</span><span class="sxs-lookup"><span data-stu-id="4ea5f-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="4ea5f-124">Geçersiz kılmaları</span><span class="sxs-lookup"><span data-stu-id="4ea5f-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="4ea5f-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="4ea5f-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="4ea5f-126">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4ea5f-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="4ea5f-127">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="4ea5f-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
