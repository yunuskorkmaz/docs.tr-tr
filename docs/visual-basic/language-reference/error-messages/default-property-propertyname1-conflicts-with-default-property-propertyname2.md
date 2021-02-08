---
description: "Hakkında daha fazla bilgi edinin: BC40007: ' ' varsayılan özelliği ' ' <propertyname1> içinde ' ' varsayılan özelliği ile çakışıyor <propertyname2> ve bu nedenle, <classname> ' Shadows ' olarak bildirilmelidir"
title: "'<propertyname1>' varsayılan özelliği, '<propertyname2>' içindeki '<classname>' varsayılan özelliğiyle çakıştığından, 'Shadows' olarak bildirilmemelidir"
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 8ec7e36da18bbf8dda35e1a521d64268d14b7b26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796645"
---
# <a name="bc40007-default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="2cab4-103">BC40007: ' ' varsayılan özelliği, \<propertyname1> ' ' içindeki ' ' varsayılan özelliğiyle çakışıyor \<propertyname2> ve bu \<classname> nedenle ' Shadows ' olarak bildirilmelidir</span><span class="sxs-lookup"><span data-stu-id="2cab4-103">BC40007: Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>

<span data-ttu-id="2cab4-104">Bir özellik, temel sınıfta tanımlanan bir özellik ile aynı adla bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2cab4-104">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="2cab4-105">Bu durumda, bu sınıftaki özelliğin temel sınıf özelliğini gölgelemelidir.</span><span class="sxs-lookup"><span data-stu-id="2cab4-105">In this situation, the property in this class should shadow the base class property.</span></span>

 <span data-ttu-id="2cab4-106">Bu ileti bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="2cab4-106">This message is a warning.</span></span> <span data-ttu-id="2cab4-107">`Shadows` Varsayılan olarak varsayılır.</span><span class="sxs-lookup"><span data-stu-id="2cab4-107">`Shadows` is assumed by default.</span></span> <span data-ttu-id="2cab4-108">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2cab4-108">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="2cab4-109">**Hata kimliği:** BC40007</span><span class="sxs-lookup"><span data-stu-id="2cab4-109">**Error ID:** BC40007</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2cab4-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2cab4-110">To correct this error</span></span>

- <span data-ttu-id="2cab4-111">`Shadows`Bildirime anahtar sözcüğü ekleyin veya belirtilen özelliğin adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2cab4-111">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cab4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cab4-112">See also</span></span>

- [<span data-ttu-id="2cab4-113">Shadows</span><span class="sxs-lookup"><span data-stu-id="2cab4-113">Shadows</span></span>](../modifiers/shadows.md)
- [<span data-ttu-id="2cab4-114">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="2cab4-114">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
