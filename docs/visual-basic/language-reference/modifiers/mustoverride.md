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
ms.openlocfilehash: 1b20108a2d42e82c0af7598fde8d60a08fea28ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396200"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="6b482-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b482-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="6b482-103">Bir özellik veya yordamın bu sınıfta uygulanmadığını ve kullanılmadan önce türetilmiş bir sınıfta geçersiz kılınmasının gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b482-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b482-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b482-104">Remarks</span></span>  
 <span data-ttu-id="6b482-105">`MustOverride`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b482-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="6b482-106">Belirten özellik veya yordam `MustOverride` bir sınıfın üyesi olmalıdır ve sınıfı [MustInherit](mustinherit.md)olarak işaretlenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b482-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6b482-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="6b482-107">Rules</span></span>  
  
- <span data-ttu-id="6b482-108">**Tamamlanmamış bildirim.**</span><span class="sxs-lookup"><span data-stu-id="6b482-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="6b482-109">Belirttiğinizde,, `MustOverride` `End Function` `End Property` veya deyimde değil, özellik veya yordam için ek kod satırı sağlayamazsınız `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="6b482-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="6b482-110">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="6b482-110">**Combined Modifiers.**</span></span> <span data-ttu-id="6b482-111">`MustOverride` `NotOverridable` Aynı bildirimde, veya ile birlikte belirtemezsiniz `Overridable` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="6b482-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="6b482-112">**Gölgeleme ve geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="6b482-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="6b482-113">Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="6b482-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="6b482-114">Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6b482-114">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="6b482-115">**Alternatif terimler.**</span><span class="sxs-lookup"><span data-stu-id="6b482-115">**Alternate Terms.**</span></span> <span data-ttu-id="6b482-116">Bir geçersiz kılma haricinde kullanılamayan bir öğe bazen *saf sanal* öğe olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6b482-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="6b482-117">`MustOverride`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="6b482-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6b482-118">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="6b482-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="6b482-119">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="6b482-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="6b482-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="6b482-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b482-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b482-121">See also</span></span>

- [<span data-ttu-id="6b482-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="6b482-122">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="6b482-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="6b482-123">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="6b482-124">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="6b482-124">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="6b482-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="6b482-125">MustInherit</span></span>](mustinherit.md)
- [<span data-ttu-id="6b482-126">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="6b482-126">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="6b482-127">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="6b482-127">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
