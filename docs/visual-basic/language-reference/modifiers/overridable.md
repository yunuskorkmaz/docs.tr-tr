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
ms.openlocfilehash: 4844bf7f3ecf23335715b950a96be15e54ebc601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603775"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="b8e1c-102">Geçersiz Kılınabilir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8e1c-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="b8e1c-103">Aynı adlı bir özellik veya türetilmiş bir sınıf yordamda bir özellik veya yordam kılınabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8e1c-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8e1c-104">Remarks</span></span>  
 <span data-ttu-id="b8e1c-105">`Overridable` Türetilen bir sınıfta geçersiz kılınmak üzere bir sınıftaki değiştiricisi sağlayan bir özellik veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="b8e1c-106">[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) değiştiricisi engelleyen bir özellik veya yöntem türetilen bir sınıfta geçersiz kılındı.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="b8e1c-107">Daha fazla bilgi için bkz: [devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="b8e1c-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="b8e1c-108">Varsa `Overridable` veya `NotOverridable` değiştiricisi belirtilmezse, varsayılan ayar olup özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılmaları üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="b8e1c-109">Özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılar, varsayılan ayardır `Overridable`; Aksi takdirde, bu `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="b8e1c-110">Gölge veya devralınan bir öğeyi yeniden tanımlamak için geçersiz kılar, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="b8e1c-111">Daha fazla bilgi için bkz: [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="b8e1c-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="b8e1c-112">Geçersiz kılınabilir bir öğe, bazen olarak adlandırılır bir *sanal* öğesi.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="b8e1c-113">Geçersiz kılınabilir ancak olması gerekmez, bazen de denir bir *somut* öğesi.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="b8e1c-114">Kullanabileceğiniz `Overridable` yalnızca bir özellik veya yordam bildirimi deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="b8e1c-115">Birleşik değiştirici</span><span class="sxs-lookup"><span data-stu-id="b8e1c-115">Combined Modifiers</span></span>  
 <span data-ttu-id="b8e1c-116">Belirtemeyeceğiniz `Overridable` veya `NotOverridable` için bir `Private` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="b8e1c-117">Belirtemeyeceğiniz `Overridable` ile birlikte `MustOverride`, `NotOverridable`, veya `Shared` aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="b8e1c-118">Bir geçersiz kılma öğesi örtülü olarak geçersiz kılınabilir olduğundan birleştiremez `Overridable` ile `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="b8e1c-119">Kullanım</span><span class="sxs-lookup"><span data-stu-id="b8e1c-119">Usage</span></span>  
 <span data-ttu-id="b8e1c-120">`Overridable` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b8e1c-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="b8e1c-121">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="b8e1c-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="b8e1c-122">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="b8e1c-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="b8e1c-123">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="b8e1c-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b8e1c-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-124">See Also</span></span>  
 [<span data-ttu-id="b8e1c-125">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="b8e1c-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)  
 [<span data-ttu-id="b8e1c-126">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="b8e1c-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="b8e1c-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="b8e1c-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="b8e1c-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="b8e1c-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="b8e1c-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="b8e1c-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="b8e1c-130">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="b8e1c-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="b8e1c-131">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="b8e1c-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
