---
title: "Tür &lt;typename&gt; CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords: BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16c12ee6c4f6efa20b9bab5ccf10077496b931ac
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a><span data-ttu-id="95165-102">Tür &lt;typename&gt; CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="95165-102">Type &lt;typename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="95165-103">Değişken, özellik veya işlev dönüş CLS ile uyumlu olmayan bir veri türüyle bildirildi.</span><span class="sxs-lookup"><span data-stu-id="95165-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="95165-104">Bir uygulama ile uyumlu olması için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), onu yalnızca CLS uyumlu türleri kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95165-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="95165-105">Aşağıdaki [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] veri türleri, CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="95165-105">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="95165-106">SByte veri türü</span><span class="sxs-lookup"><span data-stu-id="95165-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="95165-107">Uınteger veri türü</span><span class="sxs-lookup"><span data-stu-id="95165-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="95165-108">ULong veri türü</span><span class="sxs-lookup"><span data-stu-id="95165-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="95165-109">UShort veri türü</span><span class="sxs-lookup"><span data-stu-id="95165-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="95165-110">**Hata Kimliği:** BC40041</span><span class="sxs-lookup"><span data-stu-id="95165-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="95165-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="95165-111">To correct this error</span></span>  
  
-   <span data-ttu-id="95165-112">Uygulamanızı CLS ile uyumlu olması gerekiyorsa, bu öğenin veri türü için en yakın CLS uyumlu türünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="95165-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="95165-113">Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="95165-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="95165-114">Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="95165-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="95165-115">Uygulamanızı CLS ile uyumlu olması gerekmez, değişikliği gerekmez.</span><span class="sxs-lookup"><span data-stu-id="95165-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="95165-116">Ancak kendi uyumsuzluğunu, farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95165-116">You should be aware of its noncompliance, however.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95165-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95165-117">See Also</span></span>  
 [<span data-ttu-id="95165-118">\<PAVE üzerinden > CLS uyumlu kod yazma</span><span class="sxs-lookup"><span data-stu-id="95165-118">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
