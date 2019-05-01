---
title: MustOverride (Visual Basic)
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
ms.openlocfilehash: 0ddd7d0d2a57afc02aa7483ba5e83b65c48af534
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920763"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="4220f-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4220f-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="4220f-103">Bir özelliğin ya da yordamın bu sınıfta uygulanmadığını ve kullanmadan önce türetilmiş bir sınıfta geçersiz kılınması belirtir.</span><span class="sxs-lookup"><span data-stu-id="4220f-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4220f-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4220f-104">Remarks</span></span>  
 <span data-ttu-id="4220f-105">Kullanabileceğiniz `MustOverride` yalnızca bir özellik veya yordamı bildirim deyiminde.</span><span class="sxs-lookup"><span data-stu-id="4220f-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="4220f-106">Özellik veya yordamı belirten `MustOverride` bir sınıf üyesi olması gerekir ve sınıf işaretlenmelidir [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="4220f-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4220f-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="4220f-107">Rules</span></span>  
  
- <span data-ttu-id="4220f-108">**Tamamlanmamış bildirimi.**</span><span class="sxs-lookup"><span data-stu-id="4220f-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="4220f-109">Belirttiğinizde `MustOverride`, özellik veya yordam, kodun ek satırları değil vermezsiniz bile `End Function`, `End Property`, veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4220f-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="4220f-110">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="4220f-110">**Combined Modifiers.**</span></span> <span data-ttu-id="4220f-111">Belirtemezsiniz `MustOverride` ile birlikte `NotOverridable`, `Overridable`, veya `Shared` aynı bildirimde.</span><span class="sxs-lookup"><span data-stu-id="4220f-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="4220f-112">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="4220f-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="4220f-113">Devralınan bir öğe hem gölgeleme ve geçersiz kılma bulunabileceğini, ancak iki yaklaşım arasında önemli farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="4220f-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="4220f-114">Daha fazla bilgi için [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="4220f-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="4220f-115">**Diğer koşullar.**</span><span class="sxs-lookup"><span data-stu-id="4220f-115">**Alternate Terms.**</span></span> <span data-ttu-id="4220f-116">Dışında bir geçersiz kılma kullanılamaz bir öğe adlandırılan bir *saf sanal* öğesi.</span><span class="sxs-lookup"><span data-stu-id="4220f-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="4220f-117">`MustOverride` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4220f-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="4220f-118">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="4220f-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="4220f-119">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="4220f-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="4220f-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="4220f-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4220f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4220f-121">See also</span></span>

- [<span data-ttu-id="4220f-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="4220f-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="4220f-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="4220f-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="4220f-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="4220f-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="4220f-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="4220f-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="4220f-126">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="4220f-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="4220f-127">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="4220f-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
