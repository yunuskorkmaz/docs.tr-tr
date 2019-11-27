---
title: MustOverride
ms.date: 07/20/2015
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
ms.openlocfilehash: dc6a153a604fd0e5cee9d7d46ebcd63294f33628
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351493"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="e159a-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e159a-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="e159a-103">Bir özellik veya yordamın bu sınıfta uygulanmadığını ve kullanılmadan önce türetilmiş bir sınıfta geçersiz kılınmasının gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e159a-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e159a-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e159a-104">Remarks</span></span>  
 <span data-ttu-id="e159a-105">Yalnızca bir özellik veya yordam bildirimi ifadesinde `MustOverride` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e159a-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="e159a-106">`MustOverride` belirten özellik veya yordam, bir sınıfın üyesi olmalıdır ve sınıfı [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)olarak işaretlenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e159a-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e159a-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="e159a-107">Rules</span></span>  
  
- <span data-ttu-id="e159a-108">**Tamamlanmamış bildirim.**</span><span class="sxs-lookup"><span data-stu-id="e159a-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="e159a-109">`MustOverride`belirttiğinizde, özellik veya yordam için `End Function`, `End Property`veya `End Sub` deyimde değil, ek kod satırı sağlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e159a-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="e159a-110">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="e159a-110">**Combined Modifiers.**</span></span> <span data-ttu-id="e159a-111">Aynı bildirimde `NotOverridable`, `Overridable`veya `Shared` birlikte `MustOverride` belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e159a-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="e159a-112">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="e159a-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="e159a-113">Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="e159a-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="e159a-114">Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e159a-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="e159a-115">**Alternatif terimler.**</span><span class="sxs-lookup"><span data-stu-id="e159a-115">**Alternate Terms.**</span></span> <span data-ttu-id="e159a-116">Bir geçersiz kılma haricinde kullanılamayan bir öğe bazen *saf sanal* öğe olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e159a-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="e159a-117">`MustOverride` değiştiricisi şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e159a-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e159a-118">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="e159a-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="e159a-119">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="e159a-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="e159a-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="e159a-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e159a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e159a-121">See also</span></span>

- [<span data-ttu-id="e159a-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e159a-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="e159a-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="e159a-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="e159a-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="e159a-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="e159a-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="e159a-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="e159a-126">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e159a-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="e159a-127">Visual Basic gölgeleme</span><span class="sxs-lookup"><span data-stu-id="e159a-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
