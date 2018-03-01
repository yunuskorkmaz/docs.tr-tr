---
title: "Varsayılan özellik &#39; &lt;propertyname1&gt;&#39; varsayılan özellik &#39; çakışıyor&lt; propertyName2&gt;&#39; &#39;&lt; ClassName&gt;&#39; ve bildirilmelidir &#39; Gölgeleri &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af92c06f6d07b6ea64a05b9043547a46e3679111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="5ea33-102">Varsayılan özellik &#39; &lt;propertyname1&gt;&#39; varsayılan özellik &#39; çakışıyor&lt; propertyName2&gt;&#39; &#39;&lt; ClassName&gt;&#39; ve bildirilmelidir &#39; Gölgeleri &#39;</span><span class="sxs-lookup"><span data-stu-id="5ea33-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="5ea33-103">Taban sınıf içinde tanımlanmış bir özellik aynı ada sahip bir özellik bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="5ea33-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="5ea33-104">Bu durumda, bu sınıfın özelliğinde temel sınıf özelliği gölge.</span><span class="sxs-lookup"><span data-stu-id="5ea33-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="5ea33-105">Bu ileti bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="5ea33-105">This message is a warning.</span></span> <span data-ttu-id="5ea33-106">`Shadows`Varsayılan olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5ea33-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="5ea33-107">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5ea33-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5ea33-108">**Hata Kimliği:** BC40007</span><span class="sxs-lookup"><span data-stu-id="5ea33-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5ea33-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5ea33-109">To correct this error</span></span>  
  
-   <span data-ttu-id="5ea33-110">Ekleme `Shadows` anahtar sözcük bildirimi ya da değişiklik özelliğinin adı bildirilen.</span><span class="sxs-lookup"><span data-stu-id="5ea33-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea33-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ea33-111">See Also</span></span>  
 [<span data-ttu-id="5ea33-112">Gölgeleri</span><span class="sxs-lookup"><span data-stu-id="5ea33-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="5ea33-113">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="5ea33-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
