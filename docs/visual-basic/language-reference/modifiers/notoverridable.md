---
title: NotOverridable
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
ms.openlocfilehash: 463dd2454aafebf11554fb7bacdb73724c3130d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392164"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="75a85-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75a85-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="75a85-103">Bir özelliğin veya yordamın türetilmiş bir sınıfta geçersiz kılınamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="75a85-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75a85-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75a85-104">Remarks</span></span>  
 <span data-ttu-id="75a85-105">`NotOverridable`Değiştirici bir özelliğin veya metodun türetilmiş bir sınıfta geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="75a85-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="75a85-106">[Geçersiz kılınabilir](overridable.md) değiştirici, bir sınıftaki özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="75a85-106">The [Overridable](overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="75a85-107">Daha fazla bilgi için bkz. [Devralma Temelleri](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="75a85-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="75a85-108">`Overridable`Veya `NotOverridable` değiştiricisi belirtilmemişse, varsayılan ayar, özelliğin veya metodun bir temel sınıf özelliğini veya yöntemini geçersiz kıldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="75a85-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="75a85-109">Özellik veya yöntem bir temel sınıf özelliğini veya yöntemini geçersiz kılıyorsa, varsayılan ayar olur `Overridable` ; Aksi takdirde, olur `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="75a85-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="75a85-110">Geçersiz kılınamayan bir öğe, bazen *Sealed* öğesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="75a85-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="75a85-111">`NotOverridable`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75a85-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="75a85-112">Yalnızca bir özellik veya `NotOverridable` yordamı geçersiz kılan bir özellik ya da yordam üzerinde yalnızca ile birlikte bir özelliği belirtebilirsiniz `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="75a85-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="75a85-113">Birleşik değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="75a85-113">Combined Modifiers</span></span>  
 <span data-ttu-id="75a85-114">`Overridable` `NotOverridable` Bir yöntem için veya belirtemezsiniz `Private` .</span><span class="sxs-lookup"><span data-stu-id="75a85-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="75a85-115">`NotOverridable` `MustOverride` Aynı bildirimde, veya ile birlikte belirtemezsiniz `Overridable` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="75a85-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="75a85-116">Kullanım</span><span class="sxs-lookup"><span data-stu-id="75a85-116">Usage</span></span>  
 <span data-ttu-id="75a85-117">`NotOverridable`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="75a85-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="75a85-118">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="75a85-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="75a85-119">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="75a85-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="75a85-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="75a85-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="75a85-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75a85-121">See also</span></span>

- [<span data-ttu-id="75a85-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="75a85-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="75a85-123">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="75a85-123">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="75a85-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="75a85-124">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="75a85-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="75a85-125">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="75a85-126">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="75a85-126">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="75a85-127">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="75a85-127">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="75a85-128">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="75a85-128">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
