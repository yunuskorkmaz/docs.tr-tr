---
title: Temel alınan türü &lt;typename&gt; Enum CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: ceda7e6ed6fc1744de14afcb0245ebabbd7fa733
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674800"
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a><span data-ttu-id="1be10-102">Temel alınan türü &lt;typename&gt; Enum CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="1be10-102">Underlying type &lt;typename&gt; of Enum is not CLS-compliant</span></span>
<span data-ttu-id="1be10-103">Bu sabit listesi değil için belirtilen veri türü parçası [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="1be10-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="1be10-104">Bu, bileşen içinde bir hata olmadığından [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ve Visual Basic desteği bu veri türü.</span><span class="sxs-lookup"><span data-stu-id="1be10-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and Visual Basic support this data type.</span></span> <span data-ttu-id="1be10-105">Ancak, başka bir bileşen kesinlikle CLS uyumlu bir kod halinde yazılmış bu veri türünü desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1be10-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="1be10-106">Böyle bir bileşene başarıyla bileşeniniz ile etkileşim kurmak mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1be10-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="1be10-107">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="1be10-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="1be10-108">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="1be10-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="1be10-109">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="1be10-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="1be10-110">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="1be10-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="1be10-111">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="1be10-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="1be10-112">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="1be10-112">By default, this message is a warning.</span></span> <span data-ttu-id="1be10-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1be10-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1be10-114">**Hata Kimliği:** BC40032</span><span class="sxs-lookup"><span data-stu-id="1be10-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1be10-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1be10-115">To correct this error</span></span>  
  
-   <span data-ttu-id="1be10-116">Bileşeniniz yalnızca diğer arabirimleri varsa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bileşenler veya yoksa diğer bileşenlerle arabirimi değil, herhangi bir ayarı değiştirmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1be10-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="1be10-117">Bir bileşen için yazılmış değil ile arabirim, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]belgelerinden destekleyip bu veri türü veya belirlemek her iki ile yansıma mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="1be10-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="1be10-118">Aşması durumunda, değişikliği gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1be10-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="1be10-119">Bu veri türü desteklemeyen bir bileşen ile arabirim, en yakın CLS uyumlu türü ile değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1be10-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="1be10-120">Örneğin, içinde yerine, `UInteger` kullanmanız mümkün olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="1be10-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="1be10-121">Genişletilmiş aralık gerekiyorsa, değiştirebileceğiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="1be10-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="1be10-122">Otomasyon ve COM nesneleri ile arabirim, bazı türleri farklı veri genişliği kıyasla olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1be10-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="1be10-123">Örneğin, `uint` 16 bit diğer ortamlarda genellikle olur.</span><span class="sxs-lookup"><span data-stu-id="1be10-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="1be10-124">Bir 16 bit bağımsız değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `UShort` yerine `UInteger` Yönetilen Visual Basic kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="1be10-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be10-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1be10-125">See also</span></span>
- [<span data-ttu-id="1be10-126">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1be10-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)
- [<span data-ttu-id="1be10-127">Yansıma</span><span class="sxs-lookup"><span data-stu-id="1be10-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)

