---
title: "'<attributename>' özniteliği bir defadan fazla uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 14145f165adf5ccd20298a70ca5596488b488b0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409965"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="42dd8-102">'\<attributename>' özniteliği bir defadan fazla uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="42dd8-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="42dd8-103">Özniteliği yalnızca bir kez uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="42dd8-103">The attribute can only be applied once.</span></span> <span data-ttu-id="42dd8-104">`AttributeUsage`Özniteliği bir özniteliğin birden çok kez uygulanıp uygulanamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="42dd8-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="42dd8-105">**Hata kimliği:** BC30663</span><span class="sxs-lookup"><span data-stu-id="42dd8-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="42dd8-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="42dd8-106">To correct this error</span></span>  
  
1. <span data-ttu-id="42dd8-107">Özniteliğin yalnızca bir kez uygulandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="42dd8-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="42dd8-108">Geliştirdiğiniz özel öznitelikleri kullanıyorsanız, `AttributeUsage` Aşağıdaki örnekte olduğu gibi, özniteliğini birden çok öznitelik kullanımına izin verecek şekilde değiştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="42dd8-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42dd8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42dd8-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="42dd8-110">Özel Öznitelikler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="42dd8-110">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="42dd8-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="42dd8-111">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
