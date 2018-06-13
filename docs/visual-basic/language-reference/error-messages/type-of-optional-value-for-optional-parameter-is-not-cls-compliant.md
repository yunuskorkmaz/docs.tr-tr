---
title: İsteğe bağlı bir parametre için isteğe bağlı değer türü &lt;parametername&gt; CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: dd77cd8cbd36f7681e2597d908dd8e55bf249392
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594357"
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a><span data-ttu-id="115c9-102">İsteğe bağlı bir parametre için isteğe bağlı değer türü &lt;parametername&gt; CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="115c9-102">Type of optional value for optional parameter &lt;parametername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="115c9-103">Bir yordam olarak işaretlenmiş `<CLSCompliant(True)>` ancak bildiren bir [isteğe bağlı](../../../visual-basic/language-reference/modifiers/optional.md) parametresi uyumsuz bir türde varsayılan değere sahip.</span><span class="sxs-lookup"><span data-stu-id="115c9-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../../../visual-basic/language-reference/modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="115c9-104">Uyumlu olması için bir yordam için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), onu yalnızca CLS uyumlu türleri kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="115c9-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="115c9-105">Bu parametre türleri, dönüş türü ve tüm yerel değişkenler türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="115c9-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="115c9-106">Ayrıca, isteğe bağlı parametreler varsayılan değerlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="115c9-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="115c9-107">Aşağıdaki Visual Basic veri türleri CLS uyumlu değil:</span><span class="sxs-lookup"><span data-stu-id="115c9-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="115c9-108">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="115c9-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="115c9-109">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="115c9-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="115c9-110">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="115c9-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="115c9-111">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="115c9-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="115c9-112">Uyguladığınızda <xref:System.CLSCompliantAttribute> özniteliği özniteliğin bir programlama öğesi için ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="115c9-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="115c9-113">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="115c9-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="115c9-114">Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="115c9-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="115c9-115">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="115c9-115">By default, this message is a warning.</span></span> <span data-ttu-id="115c9-116">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="115c9-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="115c9-117">**Hata Kimliği:** BC40042</span><span class="sxs-lookup"><span data-stu-id="115c9-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="115c9-118">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="115c9-118">To correct this error</span></span>  
  
-   <span data-ttu-id="115c9-119">İsteğe bağlı parametresi bu türdeki bir varsayılan değeri olması gerekiyorsa kaldırma <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="115c9-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="115c9-120">Yordam, CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="115c9-120">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="115c9-121">Yordam CLS ile uyumlu olması gerekiyorsa, bu varsayılan değerin türü en yakın CLS uyumlu türüne değiştirin.</span><span class="sxs-lookup"><span data-stu-id="115c9-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="115c9-122">Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="115c9-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="115c9-123">Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="115c9-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="115c9-124">Otomasyon veya COM nesnesi ile arabirim, bazı türleri farklı veri genişliği biçimde olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="115c9-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="115c9-125">Örneğin, `int` diğer ortamlarda 16 bit görülür.</span><span class="sxs-lookup"><span data-stu-id="115c9-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="115c9-126">Bir 16 bit tamsayı böyle bir bileşenin kabul ettiğiniz, olarak bildirme `Short` yerine `Integer` Yönetilen Visual Basic kod.</span><span class="sxs-lookup"><span data-stu-id="115c9-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>