---
title: "İsteğe bağlı bir parametre için isteğe bağlı değer türü &lt;parametername&gt; CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords: BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 442ff2e4b582287e03f425dad98128726fe18c43
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a><span data-ttu-id="f5e1a-102">İsteğe bağlı bir parametre için isteğe bağlı değer türü &lt;parametername&gt; CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="f5e1a-102">Type of optional value for optional parameter &lt;parametername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="f5e1a-103">Bir yordam olarak işaretlenmiş `<CLSCompliant(True)>` ancak bildiren bir [isteğe bağlı](../../../visual-basic/language-reference/modifiers/optional.md) parametresi uyumsuz bir türde varsayılan değere sahip.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../../../visual-basic/language-reference/modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="f5e1a-104">Uyumlu olması için bir yordam için [dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/12a7a7h3) (CLS), onu yalnızca CLS uyumlu türleri kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="f5e1a-105">Bu parametre türleri, dönüş türü ve tüm yerel değişkenler türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="f5e1a-106">Ayrıca, isteğe bağlı parametreler varsayılan değerlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="f5e1a-107">Aşağıdaki [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] veri türleri, CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="f5e1a-107">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="f5e1a-108">SByte veri türü</span><span class="sxs-lookup"><span data-stu-id="f5e1a-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="f5e1a-109">Uınteger veri türü</span><span class="sxs-lookup"><span data-stu-id="f5e1a-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="f5e1a-110">ULong veri türü</span><span class="sxs-lookup"><span data-stu-id="f5e1a-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="f5e1a-111">UShort veri türü</span><span class="sxs-lookup"><span data-stu-id="f5e1a-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="f5e1a-112">Uyguladığınızda <xref:System.CLSCompliantAttribute> özniteliği özniteliğin bir programlama öğesi için ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="f5e1a-113">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="f5e1a-114">Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="f5e1a-115">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-115">By default, this message is a warning.</span></span> <span data-ttu-id="f5e1a-116">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f5e1a-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f5e1a-117">**Hata Kimliği:** BC40042</span><span class="sxs-lookup"><span data-stu-id="f5e1a-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5e1a-118">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f5e1a-118">To correct this error</span></span>  
  
-   <span data-ttu-id="f5e1a-119">İsteğe bağlı parametresi bu türdeki bir varsayılan değeri olması gerekiyorsa kaldırma <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="f5e1a-120">Yordam, CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-120">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="f5e1a-121">Yordam CLS ile uyumlu olması gerekiyorsa, bu varsayılan değerin türü en yakın CLS uyumlu türüne değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="f5e1a-122">Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="f5e1a-123">Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="f5e1a-124">Otomasyon veya COM nesnesi ile arabirim, bazı türleri farklı veri genişliği biçimde olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f5e1a-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="f5e1a-125">Örneğin, `int` diğer ortamlarda 16 bit görülür.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="f5e1a-126">Bir 16 bit tamsayı böyle bir bileşenin kabul ettiğiniz, olarak bildirme `Short` yerine `Integer` , yönetilen içinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e1a-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5e1a-127">See Also</span></span>  
 [<span data-ttu-id="f5e1a-128">\<PAVE üzerinden > CLS uyumlu kod yazma</span><span class="sxs-lookup"><span data-stu-id="f5e1a-128">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
