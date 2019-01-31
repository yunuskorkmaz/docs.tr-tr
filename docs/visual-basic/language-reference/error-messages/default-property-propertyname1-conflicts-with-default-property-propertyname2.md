---
title: "'<propertyname1>' varsayılan özelliği, '<propertyname2>' içindeki '<classname>' varsayılan özelliğiyle çakıştığından, 'Shadows' olarak bildirilmemelidir"
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: bc75b01532ffb112622d7f9bc837490c627883b3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270416"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="a5fa3-102">Varsayılan özellik '\<propertyname1 >' varsayılan özelliğiyle çakışıyor '\<propertyname2 >', '\<SınıfAdı >' ve 'Shadows' olarak bildirilmemelidir</span><span class="sxs-lookup"><span data-stu-id="a5fa3-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="a5fa3-103">Temel sınıfta tanımlanan bir özellik olarak aynı ada sahip bir özellik bildirildi.</span><span class="sxs-lookup"><span data-stu-id="a5fa3-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="a5fa3-104">Bu durumda, bu sınıf özelliği temel sınıf özelliğini gölge.</span><span class="sxs-lookup"><span data-stu-id="a5fa3-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="a5fa3-105">Bu ileti bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="a5fa3-105">This message is a warning.</span></span> <span data-ttu-id="a5fa3-106">`Shadows` Varsayılan olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a5fa3-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="a5fa3-107">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz. [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a5fa3-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="a5fa3-108">**Hata Kimliği:** BC40007</span><span class="sxs-lookup"><span data-stu-id="a5fa3-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a5fa3-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a5fa3-109">To correct this error</span></span>  
  
-   <span data-ttu-id="a5fa3-110">Ekleme `Shadows` anahtar sözcüğü bildirimi ya da değişiklik özelliğin adı bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="a5fa3-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fa3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5fa3-111">See also</span></span>
- [<span data-ttu-id="a5fa3-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="a5fa3-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="a5fa3-113">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="a5fa3-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
