---
title: "'<attributename>' özniteliği bir defadan fazla uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 62e84d174e4e218472eda9b7c08ed677e0140438
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278713"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="a6dc9-102">Öznitelik '\<attributename >' birden çok kez uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="a6dc9-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>
<span data-ttu-id="a6dc9-103">Öznitelik yalnızca bir kez uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a6dc9-103">The attribute can only be applied once.</span></span> <span data-ttu-id="a6dc9-104">`AttributeUsage` Özniteliği bir öznitelik birden çok kez uygulanabilir olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a6dc9-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="a6dc9-105">**Hata Kimliği:** BC30663</span><span class="sxs-lookup"><span data-stu-id="a6dc9-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a6dc9-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a6dc9-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="a6dc9-107">Öznitelik yalnızca bir kez uygulanır emin olun.</span><span class="sxs-lookup"><span data-stu-id="a6dc9-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="a6dc9-108">Geliştirdiğiniz özel öznitelikler kullanıyorsanız, değiştirmeyi göz önünde bulundurun, `AttributeUsage` birden çok öznitelik kullanımı, aşağıdaki örnek olarak izin vermek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a6dc9-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6dc9-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6dc9-109">See also</span></span>
- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="a6dc9-110">Özel Öznitelikler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a6dc9-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="a6dc9-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="a6dc9-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
