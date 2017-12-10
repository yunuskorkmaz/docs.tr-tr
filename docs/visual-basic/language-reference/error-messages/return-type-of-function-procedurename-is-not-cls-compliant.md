---
title: "Dönüş türü işlevi &#39; &lt;procedurename&gt;&#39; CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords: BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 14adc6f8f2d89713bd681a1d55e4801b930cf642
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a><span data-ttu-id="fae63-102">Dönüş türü işlevi &#39; &lt;procedurename&gt;&#39; CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="fae63-102">Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="fae63-103">A `Function` yordamı olarak işaretli `<CLSCompliant(True)>` ancak olarak işaretlenmiş bir tür döndüren `<CLSCompliant(False)>`işaretlenmemiş veya uyumlu olmayan bir tür olduğundan geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="fae63-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="fae63-104">Uyumlu olması için bir yordam için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), onu yalnızca CLS uyumlu türleri kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fae63-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="fae63-105">Bu parametre türleri, dönüş türü ve tüm yerel değişkenler türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fae63-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="fae63-106">Aşağıdaki [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] veri türleri, CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="fae63-106">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="fae63-107">SByte veri türü</span><span class="sxs-lookup"><span data-stu-id="fae63-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="fae63-108">Uınteger veri türü</span><span class="sxs-lookup"><span data-stu-id="fae63-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="fae63-109">ULong veri türü</span><span class="sxs-lookup"><span data-stu-id="fae63-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="fae63-110">UShort veri türü</span><span class="sxs-lookup"><span data-stu-id="fae63-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="fae63-111">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="fae63-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="fae63-112">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fae63-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="fae63-113">Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fae63-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="fae63-114">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="fae63-114">By default, this message is a warning.</span></span> <span data-ttu-id="fae63-115">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fae63-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="fae63-116">**Hata Kimliği:** BC40027</span><span class="sxs-lookup"><span data-stu-id="fae63-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fae63-117">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fae63-117">To correct this error</span></span>  
  
-   <span data-ttu-id="fae63-118">Varsa `Function` yordamı gerekir, bu türdeki dönüş kaldırmak <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fae63-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="fae63-119">Yordam, CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="fae63-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="fae63-120">Varsa `Function` yordamı CLS ile uyumlu olması, en yakın CLS uyumlu türü dönüş türünü değiştir.</span><span class="sxs-lookup"><span data-stu-id="fae63-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="fae63-121">Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="fae63-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="fae63-122">Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="fae63-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="fae63-123">Otomasyon veya COM nesnesi ile arabirim, bazı türleri farklı veri genişliği biçimde olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fae63-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="fae63-124">Örneğin, `int` diğer ortamlarda 16 bit görülür.</span><span class="sxs-lookup"><span data-stu-id="fae63-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="fae63-125">Bu tür bir bileşenine bir 16 bit tam sayı döndüren, olarak bildirme `Short` yerine `Integer` , yönetilen içinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="fae63-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae63-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fae63-126">See Also</span></span>  
 [<span data-ttu-id="fae63-127">\<PAVE üzerinden > CLS uyumlu kod yazma</span><span class="sxs-lookup"><span data-stu-id="fae63-127">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
