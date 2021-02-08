---
description: ': MustOverride (Visual Basic) hakkında daha fazla bilgi'
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
ms.openlocfilehash: df7200a7f7ec4bfda34765747d6318bc50a38dd1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774531"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="b6745-103">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6745-103">MustOverride (Visual Basic)</span></span>

<span data-ttu-id="b6745-104">Bir özellik veya yordamın bu sınıfta uygulanmadığını ve kullanılmadan önce türetilmiş bir sınıfta geçersiz kılınmasının gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6745-104">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6745-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6745-105">Remarks</span></span>  

 <span data-ttu-id="b6745-106">`MustOverride`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6745-106">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="b6745-107">Belirten özellik veya yordam `MustOverride` bir sınıfın üyesi olmalıdır ve sınıfı [MustInherit](mustinherit.md)olarak işaretlenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6745-107">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b6745-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="b6745-108">Rules</span></span>  
  
- <span data-ttu-id="b6745-109">**Tamamlanmamış bildirim.**</span><span class="sxs-lookup"><span data-stu-id="b6745-109">**Incomplete Declaration.**</span></span> <span data-ttu-id="b6745-110">Belirttiğinizde,, `MustOverride` `End Function` `End Property` veya deyimde değil, özellik veya yordam için ek kod satırı sağlayamazsınız `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="b6745-110">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="b6745-111">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="b6745-111">**Combined Modifiers.**</span></span> <span data-ttu-id="b6745-112">`MustOverride` `NotOverridable` Aynı bildirimde, veya ile birlikte belirtemezsiniz `Overridable` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="b6745-112">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="b6745-113">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="b6745-113">**Shadowing and Overriding.**</span></span> <span data-ttu-id="b6745-114">Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="b6745-114">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="b6745-115">Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b6745-115">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="b6745-116">**Alternatif terimler.**</span><span class="sxs-lookup"><span data-stu-id="b6745-116">**Alternate Terms.**</span></span> <span data-ttu-id="b6745-117">Bir geçersiz kılma haricinde kullanılamayan bir öğe bazen *saf sanal* öğe olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b6745-117">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="b6745-118">`MustOverride`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b6745-118">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="b6745-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="b6745-119">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="b6745-120">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="b6745-120">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="b6745-121">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="b6745-121">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b6745-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6745-122">See also</span></span>

- [<span data-ttu-id="b6745-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="b6745-123">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="b6745-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="b6745-124">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="b6745-125">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="b6745-125">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="b6745-126">MustInherit</span><span class="sxs-lookup"><span data-stu-id="b6745-126">MustInherit</span></span>](mustinherit.md)
- [<span data-ttu-id="b6745-127">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b6745-127">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="b6745-128">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="b6745-128">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
