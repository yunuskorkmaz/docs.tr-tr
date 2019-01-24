---
title: Varsayılan özellik &#39; &lt;propertyname1&gt; &#39; varsayılan özelliğiyle çakışıyor &#39; &lt;propertyname2&gt; &#39; içinde &#39; &lt;classname&gt; &#39;ve olarak bildirilmemelidir &#39;gölge&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 3099467fa3c5a162c13c9235fb8d55375953ba3a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521432"
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="c251d-102">Varsayılan özellik &#39; &lt;propertyname1&gt; &#39; varsayılan özelliğiyle çakışıyor &#39; &lt;propertyname2&gt; &#39; içinde &#39; &lt;classname&gt; &#39;ve olarak bildirilmemelidir &#39;gölge&#39;</span><span class="sxs-lookup"><span data-stu-id="c251d-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="c251d-103">Temel sınıfta tanımlanan bir özellik olarak aynı ada sahip bir özellik bildirildi.</span><span class="sxs-lookup"><span data-stu-id="c251d-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="c251d-104">Bu durumda, bu sınıf özelliği temel sınıf özelliğini gölge.</span><span class="sxs-lookup"><span data-stu-id="c251d-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="c251d-105">Bu ileti bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="c251d-105">This message is a warning.</span></span> <span data-ttu-id="c251d-106">`Shadows` Varsayılan olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c251d-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="c251d-107">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz. [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c251d-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c251d-108">**Hata Kimliği:** BC40007</span><span class="sxs-lookup"><span data-stu-id="c251d-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c251d-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c251d-109">To correct this error</span></span>  
  
-   <span data-ttu-id="c251d-110">Ekleme `Shadows` anahtar sözcüğü bildirimi ya da değişiklik özelliğin adı bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c251d-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c251d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c251d-111">See also</span></span>
- [<span data-ttu-id="c251d-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="c251d-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="c251d-113">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="c251d-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
