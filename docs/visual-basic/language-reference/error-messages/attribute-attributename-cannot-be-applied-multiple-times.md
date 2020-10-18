---
title: "'<attributename>' özniteliği bir defadan fazla uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 27cbe6d0043179c4a5d52baae06bad805f9d1d3a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162667"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="1cd60-102">BC30663: ' \<attributename> ' özniteliği birden çok kez uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="1cd60-102">BC30663: Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="1cd60-103">Özniteliği yalnızca bir kez uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1cd60-103">The attribute can only be applied once.</span></span> <span data-ttu-id="1cd60-104">`AttributeUsage`Özniteliği bir özniteliğin birden çok kez uygulanıp uygulanamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="1cd60-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>

 <span data-ttu-id="1cd60-105">**Hata kimliği:** BC30663</span><span class="sxs-lookup"><span data-stu-id="1cd60-105">**Error ID:** BC30663</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1cd60-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1cd60-106">To correct this error</span></span>

1. <span data-ttu-id="1cd60-107">Özniteliğin yalnızca bir kez uygulandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="1cd60-107">Make sure the attribute is only applied once.</span></span>

2. <span data-ttu-id="1cd60-108">Geliştirdiğiniz özel öznitelikleri kullanıyorsanız, `AttributeUsage` Aşağıdaki örnekte olduğu gibi, özniteliğini birden çok öznitelik kullanımına izin verecek şekilde değiştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="1cd60-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a><span data-ttu-id="1cd60-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cd60-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="1cd60-110">Özel Öznitelikler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1cd60-110">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="1cd60-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="1cd60-111">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
