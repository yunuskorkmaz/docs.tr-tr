---
description: "Şu konuda daha fazla bilgi edinin: BC30663: ' <attributename> ' özniteliği birden çok kez uygulanamaz"
title: "'<attributename>' özniteliği bir defadan fazla uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 84b77111a7401eb6f30eb7cd167f4b5689f33e77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797152"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="09323-103">BC30663: ' \<attributename> ' özniteliği birden çok kez uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="09323-103">BC30663: Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="09323-104">Özniteliği yalnızca bir kez uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="09323-104">The attribute can only be applied once.</span></span> <span data-ttu-id="09323-105">`AttributeUsage`Özniteliği bir özniteliğin birden çok kez uygulanıp uygulanamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="09323-105">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>

 <span data-ttu-id="09323-106">**Hata kimliği:** BC30663</span><span class="sxs-lookup"><span data-stu-id="09323-106">**Error ID:** BC30663</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="09323-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="09323-107">To correct this error</span></span>

1. <span data-ttu-id="09323-108">Özniteliğin yalnızca bir kez uygulandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="09323-108">Make sure the attribute is only applied once.</span></span>

2. <span data-ttu-id="09323-109">Geliştirdiğiniz özel öznitelikleri kullanıyorsanız, `AttributeUsage` Aşağıdaki örnekte olduğu gibi, özniteliğini birden çok öznitelik kullanımına izin verecek şekilde değiştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="09323-109">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a><span data-ttu-id="09323-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09323-110">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="09323-111">Özel Öznitelikler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="09323-111">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="09323-112">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="09323-112">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
