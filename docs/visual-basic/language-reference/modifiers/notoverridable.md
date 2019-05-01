---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: 41c08a48fdb7501081e887fb5cf9f99c334c72ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920659"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="bbad3-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbad3-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="bbad3-103">Türetilen bir sınıfta bir özellik veya yordamı kılınamaz belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbad3-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbad3-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbad3-104">Remarks</span></span>  
 <span data-ttu-id="bbad3-105">`NotOverridable` Değiştiricisi engelleyen bir özellik veya yöntem türetilmiş sınıf içinde geçersiz kılındı.</span><span class="sxs-lookup"><span data-stu-id="bbad3-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="bbad3-106">[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) türetilen bir sınıfta geçersiz kılınacak sınıfında değiştiricisi sağlayan bir özellik veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="bbad3-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="bbad3-107">Daha fazla bilgi için [devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="bbad3-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="bbad3-108">Varsa `Overridable` veya `NotOverridable` değiştiricisi belirtilmezse, varsayılan ayar olup özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılar üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bbad3-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="bbad3-109">Bir temel sınıf özelliği veya yöntemi özelliği veya yöntemi geçersiz kılar, varsayılan ayardır `Overridable`; Aksi takdirde bu `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="bbad3-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="bbad3-110">Geçersiz kılınamaz öğenin adlandırılan bir *korumalı* öğesi.</span><span class="sxs-lookup"><span data-stu-id="bbad3-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="bbad3-111">Kullanabileceğiniz `NotOverridable` yalnızca bir özellik veya yordamı bildirim deyiminde.</span><span class="sxs-lookup"><span data-stu-id="bbad3-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="bbad3-112">Belirtebileceğiniz `NotOverridable` yalnızca üzerinde bir özelliği ya da başka bir özellik ya da yordamın, diğer bir deyişle, yalnızca içinde birlikte geçersiz kılan yordamın `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="bbad3-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="bbad3-113">Birleşik değiştirici</span><span class="sxs-lookup"><span data-stu-id="bbad3-113">Combined Modifiers</span></span>  
 <span data-ttu-id="bbad3-114">Belirtemezsiniz `Overridable` veya `NotOverridable` için bir `Private` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bbad3-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="bbad3-115">Belirtemezsiniz `NotOverridable` ile birlikte `MustOverride`, `Overridable`, veya `Shared` aynı bildirimde.</span><span class="sxs-lookup"><span data-stu-id="bbad3-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="bbad3-116">Kullanım</span><span class="sxs-lookup"><span data-stu-id="bbad3-116">Usage</span></span>  
 <span data-ttu-id="bbad3-117">`NotOverridable` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="bbad3-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="bbad3-118">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="bbad3-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="bbad3-119">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="bbad3-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="bbad3-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="bbad3-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="bbad3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbad3-121">See also</span></span>

- [<span data-ttu-id="bbad3-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="bbad3-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="bbad3-123">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="bbad3-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="bbad3-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="bbad3-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="bbad3-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="bbad3-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="bbad3-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="bbad3-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="bbad3-127">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="bbad3-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="bbad3-128">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="bbad3-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
