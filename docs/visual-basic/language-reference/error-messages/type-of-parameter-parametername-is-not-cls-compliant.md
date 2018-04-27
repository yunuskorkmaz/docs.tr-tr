---
title: Parametrenin türü &#39; &lt;parametername&gt; &#39; CLS uyumlu değil
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d34de9e5914b02a0e878b87e786b81a5940a6d85
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a><span data-ttu-id="646b3-102">Parametrenin türü &#39; &lt;parametername&gt; &#39; CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="646b3-102">Type of parameter &#39;&lt;parametername&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="646b3-103">Bir yordam olarak işaretlenmiş `<CLSCompliant(True)>` ancak bir parametresi olarak işaretlenmiş bir türüyle bildirir `<CLSCompliant(False)>`işaretlenmemiş veya uyumlu olmayan bir tür olduğundan geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="646b3-103">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="646b3-104">Uyumlu olması için bir yordam için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), onu yalnızca CLS uyumlu türleri kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="646b3-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="646b3-105">Bu parametre türleri, dönüş türü ve tüm yerel değişkenler türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="646b3-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="646b3-106">Aşağıdaki Visual Basic veri türleri CLS uyumlu değil:</span><span class="sxs-lookup"><span data-stu-id="646b3-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="646b3-107">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="646b3-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="646b3-108">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="646b3-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="646b3-109">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="646b3-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="646b3-110">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="646b3-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="646b3-111">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="646b3-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="646b3-112">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="646b3-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="646b3-113">Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="646b3-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="646b3-114">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="646b3-114">By default, this message is a warning.</span></span> <span data-ttu-id="646b3-115">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="646b3-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="646b3-116">**Hata Kimliği:** BC40028</span><span class="sxs-lookup"><span data-stu-id="646b3-116">**Error ID:** BC40028</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="646b3-117">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="646b3-117">To correct this error</span></span>  
  
-   <span data-ttu-id="646b3-118">Yordamın bu belirli türde bir parametre almalıdır, kaldırmanız <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="646b3-118">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="646b3-119">Yordam, CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="646b3-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="646b3-120">Yordam CLS ile uyumlu olması gerekiyorsa, bu parametrenin türü en yakın CLS uyumlu türüne değiştirin.</span><span class="sxs-lookup"><span data-stu-id="646b3-120">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="646b3-121">Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="646b3-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="646b3-122">Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="646b3-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="646b3-123">Otomasyon veya COM nesnesi ile arabirim, bazı türleri farklı veri genişliği biçimde olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="646b3-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="646b3-124">Örneğin, `int` diğer ortamlarda 16 bit görülür.</span><span class="sxs-lookup"><span data-stu-id="646b3-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="646b3-125">Bir 16 bit tamsayı böyle bir bileşenin kabul ettiğiniz, olarak bildirme `Short` yerine `Integer` Yönetilen Visual Basic kod.</span><span class="sxs-lookup"><span data-stu-id="646b3-125">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>