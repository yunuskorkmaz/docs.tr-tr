---
title: Üye türü &#39; &lt;membername&gt; &#39; CLS uyumlu değil
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 123d19bc3b159578edc7fdfe2a36bc8c79e962ef
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="type-of-member-39ltmembernamegt39-is-not-cls-compliant"></a><span data-ttu-id="efab5-102">Üye türü &#39; &lt;membername&gt; &#39; CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="efab5-102">Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="efab5-103">Bu üye olmadığı için belirtilen veri türü parçası [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="efab5-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="efab5-104">Bu, bileşen içinde bir hata olmadığından [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ve Visual Basic desteği bu veri türü.</span><span class="sxs-lookup"><span data-stu-id="efab5-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and Visual Basic support this data type.</span></span> <span data-ttu-id="efab5-105">Ancak, başka bir bileşen kesinlikle CLS uyumlu kod içinde yazılmış bu veri türünü desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="efab5-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="efab5-106">Bu tür bir bileşeni başarıyla bileşeni ile etkileşim mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="efab5-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="efab5-107">Aşağıdaki Visual Basic veri türleri CLS uyumlu değil:</span><span class="sxs-lookup"><span data-stu-id="efab5-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="efab5-108">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="efab5-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="efab5-109">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="efab5-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="efab5-110">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="efab5-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="efab5-111">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="efab5-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="efab5-112">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="efab5-112">By default, this message is a warning.</span></span> <span data-ttu-id="efab5-113">Uyarıları gizleme veya uyarıları hata olarak davranma daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="efab5-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="efab5-114">**Hata Kimliği:** BC40025</span><span class="sxs-lookup"><span data-stu-id="efab5-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="efab5-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="efab5-115">To correct this error</span></span>  
  
-   <span data-ttu-id="efab5-116">Bileşeniniz yalnızca diğer arabirimleri varsa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bileşenleri veya yoksa diğer bileşenlerle birlikte arabirim, değişikliği gerekmez.</span><span class="sxs-lookup"><span data-stu-id="efab5-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="efab5-117">İçin yazılmaz bileşeniyle arabirim varsa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], belirlemek, her iki aracılığıyla yansıma kullanabilir veya belgelerinden destekleyip bu veri türü.</span><span class="sxs-lookup"><span data-stu-id="efab5-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="efab5-118">Aşması durumunda değişikliği gerekmez.</span><span class="sxs-lookup"><span data-stu-id="efab5-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="efab5-119">Bu veri türü desteklemeyen bir bileşeni arabirim, en yakın CLS uyumlu türü ile değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="efab5-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="efab5-120">Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="efab5-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="efab5-121">Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="efab5-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="efab5-122">Otomasyon veya COM nesnesi ile arabirim, bazı türleri farklı veri genişliği biçimde olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efab5-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="efab5-123">Örneğin, `uint` diğer ortamlarda 16 bit görülür.</span><span class="sxs-lookup"><span data-stu-id="efab5-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="efab5-124">Bir 16 bit bağımsız değişkeni tür bileşen geçirilirse, olarak bildirme `UShort` yerine `UInteger` Yönetilen Visual Basic kod.</span><span class="sxs-lookup"><span data-stu-id="efab5-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efab5-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="efab5-125">See Also</span></span>  
 [<span data-ttu-id="efab5-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="efab5-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
 
