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
ms.openlocfilehash: dcbabde8464dd8a0ce5fad24d7d72b1e780270d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392125"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="2d7ef-102">Geçersiz Kılınabilir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d7ef-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="2d7ef-103">Bir özellik veya yordamın, türetilmiş bir sınıftaki aynı adlı bir özellik veya yordam tarafından geçersiz kılınabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d7ef-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d7ef-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d7ef-104">Remarks</span></span>  
 <span data-ttu-id="2d7ef-105">Değiştirici, bir `Overridable` sınıftaki özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="2d7ef-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="2d7ef-106">[NotOverridable](notoverridable.md) değiştiricisi bir özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="2d7ef-106">The [NotOverridable](notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="2d7ef-107">Daha fazla bilgi için bkz. [Devralma Temelleri](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="2d7ef-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="2d7ef-108">`Overridable`Veya `NotOverridable` değiştiricisi belirtilmemişse, varsayılan ayar, özelliğin veya metodun bir temel sınıf özelliğini veya yöntemini geçersiz kıldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2d7ef-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="2d7ef-109">Özellik veya yöntem bir temel sınıf özelliğini veya yöntemini geçersiz kılıyorsa, varsayılan ayar olur `Overridable` ; Aksi takdirde, olur `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="2d7ef-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="2d7ef-110">Devralınan bir öğeyi yeniden tanımlamak için gölge veya geçersiz kılabilirsiniz, ancak iki yaklaşım arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="2d7ef-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="2d7ef-111">Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2d7ef-111">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="2d7ef-112">Geçersiz kılınabilen bir öğe bazen *sanal* öğe olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2d7ef-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="2d7ef-113">Geçersiz kılınırsa, ancak olması gerekmez, bazen *somut* öğe olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2d7ef-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="2d7ef-114">`Overridable`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d7ef-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="2d7ef-115">Birleşik değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="2d7ef-115">Combined Modifiers</span></span>  
 <span data-ttu-id="2d7ef-116">`Overridable` `NotOverridable` Bir yöntem için veya belirtemezsiniz `Private` .</span><span class="sxs-lookup"><span data-stu-id="2d7ef-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="2d7ef-117">`Overridable` `MustOverride` Aynı bildirimde, veya ile birlikte belirtemezsiniz `NotOverridable` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="2d7ef-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="2d7ef-118">Geçersiz kılan bir öğe örtük olarak geçersiz kılınabilir olduğundan, `Overridable` ile birleştiremezsiniz `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="2d7ef-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="2d7ef-119">Kullanım</span><span class="sxs-lookup"><span data-stu-id="2d7ef-119">Usage</span></span>  
 <span data-ttu-id="2d7ef-120">`Overridable`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2d7ef-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2d7ef-121">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d7ef-121">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="2d7ef-122">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d7ef-122">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="2d7ef-123">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d7ef-123">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d7ef-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d7ef-124">See also</span></span>

- [<span data-ttu-id="2d7ef-125">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="2d7ef-125">Modifiers</span></span>](index.md)
- [<span data-ttu-id="2d7ef-126">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="2d7ef-126">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="2d7ef-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="2d7ef-127">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="2d7ef-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="2d7ef-128">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="2d7ef-129">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="2d7ef-129">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="2d7ef-130">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="2d7ef-130">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="2d7ef-131">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="2d7ef-131">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
