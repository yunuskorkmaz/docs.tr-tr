---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6fc5fb006b36cda1b6ad0e128604bc3bb427fd94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="52a4a-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52a4a-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="52a4a-103">Türetilen bir sınıfta bir özellik veya yordam kılınamaz belirtir.</span><span class="sxs-lookup"><span data-stu-id="52a4a-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52a4a-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52a4a-104">Remarks</span></span>  
 <span data-ttu-id="52a4a-105">`NotOverridable` Değiştiricisi engelleyen bir özellik veya yöntem türetilen bir sınıfta geçersiz kılındı.</span><span class="sxs-lookup"><span data-stu-id="52a4a-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="52a4a-106">[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) türetilen bir sınıfta geçersiz kılınmak üzere bir sınıftaki değiştiricisi sağlayan bir özellik veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="52a4a-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="52a4a-107">Daha fazla bilgi için bkz: [devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="52a4a-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="52a4a-108">Varsa `Overridable` veya `NotOverridable` değiştiricisi belirtilmezse, varsayılan ayar olup özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılmaları üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="52a4a-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="52a4a-109">Özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılar, varsayılan ayardır `Overridable`; Aksi takdirde, bu `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="52a4a-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="52a4a-110">Geçersiz kılınamaz bir öğe adlandırılan bir *korumalı* öğesi.</span><span class="sxs-lookup"><span data-stu-id="52a4a-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="52a4a-111">Kullanabileceğiniz `NotOverridable` yalnızca bir özellik veya yordam bildirimi deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="52a4a-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="52a4a-112">Belirleyebileceğiniz `NotOverridable` yalnızca bir özellik veya başka bir özellik veya yordam, diğer bir deyişle, yalnızca birlikte içinde geçersiz kılmaları yordamı üzerinde `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="52a4a-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="52a4a-113">Birleşik değiştirici</span><span class="sxs-lookup"><span data-stu-id="52a4a-113">Combined Modifiers</span></span>  
 <span data-ttu-id="52a4a-114">Belirtemeyeceğiniz `Overridable` veya `NotOverridable` için bir `Private` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="52a4a-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="52a4a-115">Belirtemeyeceğiniz `NotOverridable` ile birlikte `MustOverride`, `Overridable`, veya `Shared` aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="52a4a-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="52a4a-116">Kullanım</span><span class="sxs-lookup"><span data-stu-id="52a4a-116">Usage</span></span>  
 <span data-ttu-id="52a4a-117">`NotOverridable` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="52a4a-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="52a4a-118">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="52a4a-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="52a4a-119">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="52a4a-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="52a4a-120">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="52a4a-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="52a4a-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52a4a-121">See Also</span></span>  
 [<span data-ttu-id="52a4a-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="52a4a-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)  
 [<span data-ttu-id="52a4a-123">Devralma temelleri</span><span class="sxs-lookup"><span data-stu-id="52a4a-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="52a4a-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="52a4a-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="52a4a-125">Geçersiz kılınabilir</span><span class="sxs-lookup"><span data-stu-id="52a4a-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="52a4a-126">Geçersiz kılmaları</span><span class="sxs-lookup"><span data-stu-id="52a4a-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="52a4a-127">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="52a4a-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="52a4a-128">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="52a4a-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
