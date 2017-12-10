---
title: "Temel alınan tür &lt;typename&gt; Enum CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords: BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6a301c06cb86a4681709fbf67d3f731e2e6a9eb
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a><span data-ttu-id="e3bd5-102">Temel alınan tür &lt;typename&gt; Enum CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="e3bd5-102">Underlying type &lt;typename&gt; of Enum is not CLS-compliant</span></span>
<span data-ttu-id="e3bd5-103">Bu numaralandırma değil için belirtilen veri türü parçası [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="e3bd5-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="e3bd5-104">Bu, bileşen içinde bir hata olmadığından [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ve [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bu veri türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] support this data type.</span></span> <span data-ttu-id="e3bd5-105">Ancak, başka bir bileşen kesinlikle CLS uyumlu kod içinde yazılmış bu veri türünü desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="e3bd5-106">Bu tür bir bileşeni başarıyla bileşeni ile etkileşim mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="e3bd5-107">Aşağıdaki [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] veri türleri, CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="e3bd5-107">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="e3bd5-108">SByte veri türü</span><span class="sxs-lookup"><span data-stu-id="e3bd5-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="e3bd5-109">Uınteger veri türü</span><span class="sxs-lookup"><span data-stu-id="e3bd5-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="e3bd5-110">ULong veri türü</span><span class="sxs-lookup"><span data-stu-id="e3bd5-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="e3bd5-111">UShort veri türü</span><span class="sxs-lookup"><span data-stu-id="e3bd5-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="e3bd5-112">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-112">By default, this message is a warning.</span></span> <span data-ttu-id="e3bd5-113">Uyarıları gizleme veya uyarıları hata olarak davranma daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e3bd5-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e3bd5-114">**Hata Kimliği:** BC40032</span><span class="sxs-lookup"><span data-stu-id="e3bd5-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e3bd5-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e3bd5-115">To correct this error</span></span>  
  
-   <span data-ttu-id="e3bd5-116">Bileşeniniz yalnızca diğer arabirimleri varsa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bileşenleri veya yoksa diğer bileşenlerle birlikte arabirim, değişikliği gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="e3bd5-117">İçin yazılmaz bileşeniyle arabirim varsa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], belirlemek, her iki aracılığıyla yansıma kullanabilir veya belgelerinden destekleyip bu veri türü.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="e3bd5-118">Aşması durumunda değişikliği gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="e3bd5-119">Bu veri türü desteklemeyen bir bileşeni arabirim, en yakın CLS uyumlu türü ile değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="e3bd5-120">Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="e3bd5-121">Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="e3bd5-122">Otomasyon veya COM nesnesi ile arabirim, bazı türleri farklı veri genişliği biçimde olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3bd5-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="e3bd5-123">Örneğin, `uint` diğer ortamlarda 16 bit görülür.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="e3bd5-124">Bir 16 bit bağımsız değişkeni tür bileşen geçirilirse, olarak bildirme `UShort` yerine `UInteger` , yönetilen içinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3bd5-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3bd5-125">See Also</span></span>  
 [<span data-ttu-id="e3bd5-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e3bd5-126">Reflection</span></span>](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
 [<span data-ttu-id="e3bd5-127">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e3bd5-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="e3bd5-128">\<PAVE üzerinden > CLS uyumlu kod yazma</span><span class="sxs-lookup"><span data-stu-id="e3bd5-128">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
