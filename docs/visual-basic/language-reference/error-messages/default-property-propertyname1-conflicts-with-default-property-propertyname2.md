---
title: "'<propertyname1>' varsayılan özelliği, '<propertyname2>' içindeki '<classname>' varsayılan özelliğiyle çakıştığından, 'Shadows' olarak bildirilmemelidir"
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 37f98ce8120d5861552819690f9d5f22c9959a0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409731"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="e9516-102">'\<propertyname1>' varsayılan özelliği, '\<propertyname2>' içindeki '\<classname>' varsayılan özelliğiyle çakıştığından, 'Shadows' olarak bildirilmemelidir</span><span class="sxs-lookup"><span data-stu-id="e9516-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="e9516-103">Bir özellik, temel sınıfta tanımlanan bir özellik ile aynı adla bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e9516-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="e9516-104">Bu durumda, bu sınıftaki özelliğin temel sınıf özelliğini gölgelemelidir.</span><span class="sxs-lookup"><span data-stu-id="e9516-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="e9516-105">Bu ileti bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="e9516-105">This message is a warning.</span></span> <span data-ttu-id="e9516-106">`Shadows`Varsayılan olarak varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e9516-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="e9516-107">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e9516-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e9516-108">**Hata kimliği:** BC40007</span><span class="sxs-lookup"><span data-stu-id="e9516-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9516-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e9516-109">To correct this error</span></span>  
  
- <span data-ttu-id="e9516-110">`Shadows`Bildirime anahtar sözcüğü ekleyin veya belirtilen özelliğin adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e9516-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9516-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9516-111">See also</span></span>

- [<span data-ttu-id="e9516-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="e9516-112">Shadows</span></span>](../modifiers/shadows.md)
- [<span data-ttu-id="e9516-113">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="e9516-113">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
