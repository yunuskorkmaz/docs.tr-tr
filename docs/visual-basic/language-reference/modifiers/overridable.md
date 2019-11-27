---
title: Overridable
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
ms.openlocfilehash: 9c639665fd92a56de6fb6e5147cda873ef457b45
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351396"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="5726d-102">Geçersiz Kılınabilir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5726d-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="5726d-103">Bir özellik veya yordamın, türetilmiş bir sınıftaki aynı adlı bir özellik veya yordam tarafından geçersiz kılınabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5726d-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5726d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5726d-104">Remarks</span></span>  
 <span data-ttu-id="5726d-105">`Overridable` değiştiricisi, bir sınıftaki özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5726d-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="5726d-106">[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) değiştiricisi bir özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="5726d-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="5726d-107">Daha fazla bilgi için bkz. [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="5726d-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="5726d-108">`Overridable` veya `NotOverridable` değiştiricisi belirtilmemişse, varsayılan ayar, özelliğin veya metodun bir temel sınıf özelliğini veya yöntemini geçersiz kıldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5726d-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="5726d-109">Özellik veya yöntem bir temel sınıf özelliğini veya yöntemini geçersiz kılıyorsa, varsayılan ayar `Overridable`; Aksi takdirde, `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="5726d-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="5726d-110">Devralınan bir öğeyi yeniden tanımlamak için gölge veya geçersiz kılabilirsiniz, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="5726d-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="5726d-111">Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5726d-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="5726d-112">Geçersiz kılınabilen bir öğe bazen *sanal* öğe olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5726d-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="5726d-113">Geçersiz kılınırsa, ancak olması gerekmez, bazen *somut* öğe olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5726d-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="5726d-114">Yalnızca bir özellik veya yordam bildirimi ifadesinde `Overridable` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5726d-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="5726d-115">Birleşik değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="5726d-115">Combined Modifiers</span></span>  
 <span data-ttu-id="5726d-116">`Private` yöntemi için `Overridable` veya `NotOverridable` belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5726d-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="5726d-117">Aynı bildirimde `MustOverride`, `NotOverridable`veya `Shared` birlikte `Overridable` belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5726d-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="5726d-118">Geçersiz kılan bir öğe örtük olarak geçersiz kılınabilir olduğundan, `Overrides``Overridable` birleştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5726d-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="5726d-119">Kullanım</span><span class="sxs-lookup"><span data-stu-id="5726d-119">Usage</span></span>  
 <span data-ttu-id="5726d-120">`Overridable` değiştiricisi şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="5726d-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="5726d-121">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="5726d-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="5726d-122">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="5726d-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="5726d-123">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="5726d-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5726d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5726d-124">See also</span></span>

- [<span data-ttu-id="5726d-125">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="5726d-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="5726d-126">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="5726d-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="5726d-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="5726d-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="5726d-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="5726d-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="5726d-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="5726d-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="5726d-130">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="5726d-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="5726d-131">Visual Basic gölgeleme</span><span class="sxs-lookup"><span data-stu-id="5726d-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
