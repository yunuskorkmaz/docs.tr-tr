---
title: "'<attributename>' özniteliği bir defadan fazla uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: f2f4dc428a247275f9919c4a8b6e6944a558eef0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968234"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="96bb1-102">'\<AttributeName > ' özniteliği birden çok kez uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="96bb1-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="96bb1-103">Özniteliği yalnızca bir kez uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="96bb1-103">The attribute can only be applied once.</span></span> <span data-ttu-id="96bb1-104">`AttributeUsage` özniteliği bir özniteliğin birden çok kez uygulanıp uygulanamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="96bb1-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="96bb1-105">**Hata kimliği:** BC30663</span><span class="sxs-lookup"><span data-stu-id="96bb1-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="96bb1-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="96bb1-106">To correct this error</span></span>  
  
1. <span data-ttu-id="96bb1-107">Özniteliğin yalnızca bir kez uygulandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="96bb1-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="96bb1-108">Geliştirdiğiniz özel öznitelikler kullanıyorsanız, aşağıdaki örnekte olduğu gibi, `AttributeUsage` özniteliğini birden çok öznitelik kullanımına izin verecek şekilde değiştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="96bb1-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96bb1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96bb1-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="96bb1-110">Özel Öznitelikler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="96bb1-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="96bb1-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="96bb1-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
