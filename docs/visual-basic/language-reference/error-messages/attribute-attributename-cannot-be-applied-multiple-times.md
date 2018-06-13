---
title: Öznitelik &#39; &lt;attributename&gt; &#39; birden çok kez uygulanamaz
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: df97a4e391406661db98eb1c958c0e12e45b6c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584865"
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="aca28-102">Öznitelik &#39; &lt;attributename&gt; &#39; birden çok kez uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="aca28-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="aca28-103">Öznitelik yalnızca bir kez uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="aca28-103">The attribute can only be applied once.</span></span> <span data-ttu-id="aca28-104">`AttributeUsage` Özniteliği, özniteliğin birden çok kez uygulanabilir olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="aca28-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="aca28-105">**Hata Kimliği:** BC30663</span><span class="sxs-lookup"><span data-stu-id="aca28-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aca28-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="aca28-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="aca28-107">Öznitelik yalnızca bir kez uygulanır emin olun.</span><span class="sxs-lookup"><span data-stu-id="aca28-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="aca28-108">Özel öznitelikler, geliştirilmiş kullanıyorsanız, değiştirmeyi göz önünde bulundurun kendi `AttributeUsage` özniteliği birden çok öznitelik kullanımı, aşağıdaki örnek olarak izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="aca28-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aca28-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aca28-109">See Also</span></span>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="aca28-110">Özel Öznitelikler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aca28-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="aca28-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="aca28-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
