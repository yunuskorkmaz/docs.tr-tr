---
title: Geçersiz Kılınabilir (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 91a1cedc66fd66e336b6e7976ad87ad638cb43c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053905"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="940ae-102">Geçersiz Kılınabilir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="940ae-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="940ae-103">Aynı adlı bir özellik ya da yordam türetilen bir sınıfta bir özellik veya yordamı kılınabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="940ae-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="940ae-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="940ae-104">Remarks</span></span>  
 <span data-ttu-id="940ae-105">`Overridable` Türetilen bir sınıfta geçersiz kılınacak sınıfında değiştiricisi sağlayan bir özellik veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="940ae-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="940ae-106">[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) değiştiricisi engelleyen bir özellik veya yöntem türetilmiş sınıf içinde geçersiz kılındı.</span><span class="sxs-lookup"><span data-stu-id="940ae-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="940ae-107">Daha fazla bilgi için [devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="940ae-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="940ae-108">Varsa `Overridable` veya `NotOverridable` değiştiricisi belirtilmezse, varsayılan ayar olup özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılar üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="940ae-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="940ae-109">Bir temel sınıf özelliği veya yöntemi özelliği veya yöntemi geçersiz kılar, varsayılan ayardır `Overridable`; Aksi takdirde bu `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="940ae-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="940ae-110">Gölge veya devralınan bir öğeyi yeniden tanımlamak için geçersiz kılar, ancak iki yaklaşım arasında önemli farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="940ae-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="940ae-111">Daha fazla bilgi için [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="940ae-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="940ae-112">Geçersiz kılınabilir bir öğe, bazen olarak adlandırılır bir *sanal* öğesi.</span><span class="sxs-lookup"><span data-stu-id="940ae-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="940ae-113">Geçersiz kılınabilir ancak olması gerekmez, bazen de denir bir *somut* öğesi.</span><span class="sxs-lookup"><span data-stu-id="940ae-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="940ae-114">Kullanabileceğiniz `Overridable` yalnızca bir özellik veya yordamı bildirim deyiminde.</span><span class="sxs-lookup"><span data-stu-id="940ae-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="940ae-115">Birleşik değiştirici</span><span class="sxs-lookup"><span data-stu-id="940ae-115">Combined Modifiers</span></span>  
 <span data-ttu-id="940ae-116">Belirtemezsiniz `Overridable` veya `NotOverridable` için bir `Private` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="940ae-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="940ae-117">Belirtemezsiniz `Overridable` ile birlikte `MustOverride`, `NotOverridable`, veya `Shared` aynı bildirimde.</span><span class="sxs-lookup"><span data-stu-id="940ae-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="940ae-118">Bir geçersiz kılma öğesi örtük olarak geçersiz kılınabilir olduğundan birleştiremezsiniz `Overridable` ile `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="940ae-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="940ae-119">Kullanım</span><span class="sxs-lookup"><span data-stu-id="940ae-119">Usage</span></span>  
 <span data-ttu-id="940ae-120">`Overridable` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="940ae-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="940ae-121">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="940ae-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="940ae-122">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="940ae-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="940ae-123">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="940ae-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="940ae-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="940ae-124">See also</span></span>

- [<span data-ttu-id="940ae-125">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="940ae-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="940ae-126">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="940ae-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="940ae-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="940ae-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="940ae-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="940ae-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="940ae-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="940ae-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="940ae-130">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="940ae-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="940ae-131">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="940ae-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
