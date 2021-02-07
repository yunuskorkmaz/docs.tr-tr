---
description: 'Daha fazla bilgi: geçersiz kılınabilir (Visual Basic)'
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
ms.openlocfilehash: acbbd715113c836a3fb7f8a88bf74307c38ac682
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730505"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="4f31c-103">Geçersiz Kılınabilir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f31c-103">Overridable (Visual Basic)</span></span>

<span data-ttu-id="4f31c-104">Bir özellik veya yordamın, türetilmiş bir sınıftaki aynı adlı bir özellik veya yordam tarafından geçersiz kılınabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f31c-104">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f31c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f31c-105">Remarks</span></span>  

 <span data-ttu-id="4f31c-106">Değiştirici, bir `Overridable` sınıftaki özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="4f31c-106">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="4f31c-107">[NotOverridable](notoverridable.md) değiştiricisi bir özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="4f31c-107">The [NotOverridable](notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="4f31c-108">Daha fazla bilgi için bkz. [Devralma Temelleri](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="4f31c-108">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="4f31c-109">`Overridable`Veya `NotOverridable` değiştiricisi belirtilmemişse, varsayılan ayar, özelliğin veya metodun bir temel sınıf özelliğini veya yöntemini geçersiz kıldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4f31c-109">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="4f31c-110">Özellik veya yöntem bir temel sınıf özelliğini veya yöntemini geçersiz kılıyorsa, varsayılan ayar olur `Overridable` ; Aksi takdirde, olur `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="4f31c-110">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="4f31c-111">Devralınan bir öğeyi yeniden tanımlamak için gölge veya geçersiz kılabilirsiniz, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="4f31c-111">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="4f31c-112">Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4f31c-112">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="4f31c-113">Geçersiz kılınabilen bir öğe bazen *sanal* öğe olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4f31c-113">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="4f31c-114">Geçersiz kılınırsa, ancak olması gerekmez, bazen *somut* öğe olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4f31c-114">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="4f31c-115">`Overridable`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f31c-115">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="4f31c-116">Birleşik değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="4f31c-116">Combined Modifiers</span></span>  

 <span data-ttu-id="4f31c-117">`Overridable` `NotOverridable` Bir yöntem için veya belirtemezsiniz `Private` .</span><span class="sxs-lookup"><span data-stu-id="4f31c-117">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="4f31c-118">`Overridable` `MustOverride` Aynı bildirimde, veya ile birlikte belirtemezsiniz `NotOverridable` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="4f31c-118">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="4f31c-119">Geçersiz kılan bir öğe örtük olarak geçersiz kılınabilir olduğundan, `Overridable` ile birleştiremezsiniz `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="4f31c-119">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="4f31c-120">Kullanım</span><span class="sxs-lookup"><span data-stu-id="4f31c-120">Usage</span></span>  

 <span data-ttu-id="4f31c-121">`Overridable`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4f31c-121">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="4f31c-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f31c-122">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="4f31c-123">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f31c-123">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="4f31c-124">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f31c-124">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4f31c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f31c-125">See also</span></span>

- [<span data-ttu-id="4f31c-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="4f31c-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="4f31c-127">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="4f31c-127">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="4f31c-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="4f31c-128">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="4f31c-129">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="4f31c-129">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="4f31c-130">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="4f31c-130">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="4f31c-131">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4f31c-131">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="4f31c-132">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="4f31c-132">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
