---
title: Dönüş türü işlevinin &#39; &lt;procedurename&gt; &#39; CLS uyumlu değil
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b3aa178ec3a33d7edb64190d7c83d3b51483feb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a><span data-ttu-id="e08dd-102">Dönüş türü işlevinin &#39; &lt;procedurename&gt; &#39; CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="e08dd-102">Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="e08dd-103">A `Function` yordamı olarak işaretli `<CLSCompliant(True)>` ancak olarak işaretlenmiş bir tür döndüren `<CLSCompliant(False)>`işaretlenmemiş veya uyumlu olmayan bir tür olduğundan geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="e08dd-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="e08dd-104">Uyumlu olması için bir yordam için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), onu yalnızca CLS uyumlu türleri kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e08dd-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="e08dd-105">Bu parametre türleri, dönüş türü ve tüm yerel değişkenler türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e08dd-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="e08dd-106">Aşağıdaki Visual Basic veri türleri CLS uyumlu değil:</span><span class="sxs-lookup"><span data-stu-id="e08dd-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="e08dd-107">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e08dd-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="e08dd-108">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e08dd-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="e08dd-109">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e08dd-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="e08dd-110">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e08dd-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="e08dd-111">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="e08dd-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="e08dd-112">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e08dd-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="e08dd-113">Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e08dd-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="e08dd-114">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="e08dd-114">By default, this message is a warning.</span></span> <span data-ttu-id="e08dd-115">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e08dd-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e08dd-116">**Hata Kimliği:** BC40027</span><span class="sxs-lookup"><span data-stu-id="e08dd-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e08dd-117">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e08dd-117">To correct this error</span></span>  
  
-   <span data-ttu-id="e08dd-118">Varsa `Function` yordamı gerekir, bu türdeki dönüş kaldırmak <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e08dd-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="e08dd-119">Yordam, CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="e08dd-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="e08dd-120">Varsa `Function` yordamı CLS ile uyumlu olması, en yakın CLS uyumlu türü dönüş türünü değiştir.</span><span class="sxs-lookup"><span data-stu-id="e08dd-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="e08dd-121">Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="e08dd-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="e08dd-122">Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="e08dd-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="e08dd-123">Otomasyon veya COM nesnesi ile arabirim, bazı türleri farklı veri genişliği biçimde olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e08dd-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="e08dd-124">Örneğin, `int` diğer ortamlarda 16 bit görülür.</span><span class="sxs-lookup"><span data-stu-id="e08dd-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="e08dd-125">Bu tür bir bileşenine bir 16 bit tam sayı döndüren, olarak bildirme `Short` yerine `Integer` Yönetilen Visual Basic kod.</span><span class="sxs-lookup"><span data-stu-id="e08dd-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>