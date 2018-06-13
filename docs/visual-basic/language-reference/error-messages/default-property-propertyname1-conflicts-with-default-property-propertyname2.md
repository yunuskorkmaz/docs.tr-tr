---
title: Varsayılan özellik &#39; &lt;propertyname1&gt; &#39; varsayılan özellik çakışıyor &#39; &lt;propertyname2&gt; &#39; içinde &#39; &lt;classname&gt; &#39;ve bildirilmelidir &#39;gölgeleri&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: b305f7a59a9865ebeb6b6f53607757b719fb4d41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586630"
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="99a71-102">Varsayılan özellik &#39; &lt;propertyname1&gt; &#39; varsayılan özellik çakışıyor &#39; &lt;propertyname2&gt; &#39; içinde &#39; &lt;classname&gt; &#39;ve bildirilmelidir &#39;gölgeleri&#39;</span><span class="sxs-lookup"><span data-stu-id="99a71-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="99a71-103">Taban sınıf içinde tanımlanmış bir özellik aynı ada sahip bir özellik bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="99a71-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="99a71-104">Bu durumda, bu sınıfın özelliğinde temel sınıf özelliği gölge.</span><span class="sxs-lookup"><span data-stu-id="99a71-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="99a71-105">Bu ileti bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="99a71-105">This message is a warning.</span></span> <span data-ttu-id="99a71-106">`Shadows` Varsayılan olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="99a71-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="99a71-107">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="99a71-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="99a71-108">**Hata Kimliği:** BC40007</span><span class="sxs-lookup"><span data-stu-id="99a71-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="99a71-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="99a71-109">To correct this error</span></span>  
  
-   <span data-ttu-id="99a71-110">Ekleme `Shadows` anahtar sözcük bildirimi ya da değişiklik özelliğinin adı bildirilen.</span><span class="sxs-lookup"><span data-stu-id="99a71-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99a71-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99a71-111">See Also</span></span>  
 [<span data-ttu-id="99a71-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="99a71-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="99a71-113">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="99a71-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
