---
title: Öznitelik &#39; &lt;attributename&gt; &#39; birden çok kez uygulanamaz
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 6609ce299799bc3c4b78d48478e99e4d4101dd72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565169"
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="6bb45-102">Öznitelik &#39; &lt;attributename&gt; &#39; birden çok kez uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="6bb45-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="6bb45-103">Öznitelik yalnızca bir kez uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="6bb45-103">The attribute can only be applied once.</span></span> <span data-ttu-id="6bb45-104">`AttributeUsage` Özniteliği bir öznitelik birden çok kez uygulanabilir olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="6bb45-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="6bb45-105">**Hata Kimliği:** BC30663</span><span class="sxs-lookup"><span data-stu-id="6bb45-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6bb45-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6bb45-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="6bb45-107">Öznitelik yalnızca bir kez uygulanır emin olun.</span><span class="sxs-lookup"><span data-stu-id="6bb45-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="6bb45-108">Geliştirdiğiniz özel öznitelikler kullanıyorsanız, değiştirmeyi göz önünde bulundurun, `AttributeUsage` birden çok öznitelik kullanımı, aşağıdaki örnek olarak izin vermek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6bb45-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bb45-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bb45-109">See also</span></span>
- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="6bb45-110">Özel Öznitelikler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6bb45-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="6bb45-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="6bb45-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
