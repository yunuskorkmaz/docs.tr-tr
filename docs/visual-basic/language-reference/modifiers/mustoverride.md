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
ms.openlocfilehash: 5dabd90d29bc41d017436876af24a67fa87e8e17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599876"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="24cc8-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24cc8-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="24cc8-103">Bir özellik veya yordam bu sınıfta uygulanmadı ve kullanılabilmesi için türetilen bir sınıfta geçersiz kılınmalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="24cc8-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24cc8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24cc8-104">Remarks</span></span>  
 <span data-ttu-id="24cc8-105">Kullanabileceğiniz `MustOverride` yalnızca bir özellik veya yordam bildirimi deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="24cc8-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="24cc8-106">Özellik veya belirtir yordamı `MustOverride` bir sınıf üyesi olması gerekir ve sınıf işaretlenmelidir [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="24cc8-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="24cc8-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="24cc8-107">Rules</span></span>  
  
-   <span data-ttu-id="24cc8-108">**Tamamlanmamış bildirimi.**</span><span class="sxs-lookup"><span data-stu-id="24cc8-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="24cc8-109">Belirttiğinizde `MustOverride`, özellik veya yordam, kodun ek satırları değil sağlamazsanız bile `End Function`, `End Property`, veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="24cc8-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="24cc8-110">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="24cc8-110">**Combined Modifiers.**</span></span> <span data-ttu-id="24cc8-111">Belirtemeyeceğiniz `MustOverride` ile birlikte `NotOverridable`, `Overridable`, veya `Shared` aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="24cc8-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
-   <span data-ttu-id="24cc8-112">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="24cc8-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="24cc8-113">Hem gölgeleme ve geçersiz kılma devralınan bir öğeyi yeniden tanımlamanız, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="24cc8-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="24cc8-114">Daha fazla bilgi için bkz: [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="24cc8-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
-   <span data-ttu-id="24cc8-115">**Diğer koşulları.**</span><span class="sxs-lookup"><span data-stu-id="24cc8-115">**Alternate Terms.**</span></span> <span data-ttu-id="24cc8-116">Geçersiz kılma dışında kullanılamaz bir öğe adlandırılan bir *saf sanal* öğesi.</span><span class="sxs-lookup"><span data-stu-id="24cc8-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="24cc8-117">`MustOverride` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="24cc8-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="24cc8-118">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="24cc8-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="24cc8-119">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="24cc8-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="24cc8-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="24cc8-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="24cc8-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24cc8-121">See Also</span></span>  
 [<span data-ttu-id="24cc8-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="24cc8-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="24cc8-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="24cc8-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="24cc8-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="24cc8-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="24cc8-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="24cc8-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="24cc8-126">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="24cc8-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="24cc8-127">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="24cc8-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
