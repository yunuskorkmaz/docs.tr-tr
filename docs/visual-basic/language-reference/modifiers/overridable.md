---
title: "Geçersiz Kılınabilir (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7d5dd33f8591be1b4305e954e55e035882626c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="d8d5b-102">Geçersiz Kılınabilir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8d5b-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="d8d5b-103">Aynı adlı bir özellik veya türetilmiş bir sınıf yordamda bir özellik veya yordam kılınabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8d5b-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8d5b-104">Remarks</span></span>  
 <span data-ttu-id="d8d5b-105">`Overridable` Türetilen bir sınıfta geçersiz kılınmak üzere bir sınıftaki değiştiricisi sağlayan bir özellik veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="d8d5b-106">[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) değiştiricisi engelleyen bir özellik veya yöntem türetilen bir sınıfta geçersiz kılındı.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="d8d5b-107">Daha fazla bilgi için bkz: [devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="d8d5b-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="d8d5b-108">Varsa `Overridable` veya `NotOverridable` değiştiricisi belirtilmezse, varsayılan ayar olup özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılmaları üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="d8d5b-109">Özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılar, varsayılan ayardır `Overridable`; Aksi takdirde, bu `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="d8d5b-110">Gölge veya devralınan bir öğeyi yeniden tanımlamak için geçersiz kılar, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="d8d5b-111">Daha fazla bilgi için bkz: [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="d8d5b-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="d8d5b-112">Geçersiz kılınabilir bir öğe, bazen olarak adlandırılır bir *sanal* öğesi.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="d8d5b-113">Geçersiz kılınabilir ancak olması gerekmez, bazen de denir bir *somut* öğesi.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="d8d5b-114">Kullanabileceğiniz `Overridable` yalnızca bir özellik veya yordam bildirimi deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="d8d5b-115">Birleşik değiştirici</span><span class="sxs-lookup"><span data-stu-id="d8d5b-115">Combined Modifiers</span></span>  
 <span data-ttu-id="d8d5b-116">Belirtemeyeceğiniz `Overridable` veya `NotOverridable` için bir `Private` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="d8d5b-117">Belirtemeyeceğiniz `Overridable` ile birlikte `MustOverride`, `NotOverridable`, veya `Shared` aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="d8d5b-118">Bir geçersiz kılma öğesi örtülü olarak geçersiz kılınabilir olduğundan birleştiremez `Overridable` ile `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="d8d5b-119">Kullanım</span><span class="sxs-lookup"><span data-stu-id="d8d5b-119">Usage</span></span>  
 <span data-ttu-id="d8d5b-120">`Overridable` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d8d5b-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d8d5b-121">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="d8d5b-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="d8d5b-122">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="d8d5b-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="d8d5b-123">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="d8d5b-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d8d5b-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8d5b-124">See Also</span></span>  
 [<span data-ttu-id="d8d5b-125">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="d8d5b-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)  
 [<span data-ttu-id="d8d5b-126">Devralma temelleri</span><span class="sxs-lookup"><span data-stu-id="d8d5b-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="d8d5b-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="d8d5b-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="d8d5b-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="d8d5b-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="d8d5b-129">Geçersiz kılmaları</span><span class="sxs-lookup"><span data-stu-id="d8d5b-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="d8d5b-130">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="d8d5b-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="d8d5b-131">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="d8d5b-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
