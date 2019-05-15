---
title: <parametername> isteğe bağlı parametresi için isteğe bağlı değerin türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: 35ddf1d42efae20be477c20b89775de64ceee176
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589843"
---
# <a name="type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="29ea6-102">İsteğe bağlı parametre için isteğe bağlı değerin türü \<parametername > CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="29ea6-102">Type of optional value for optional parameter \<parametername> is not CLS-compliant</span></span>
<span data-ttu-id="29ea6-103">Bir yordam olarak işaretlenmiş `<CLSCompliant(True)>` bildirir, ancak bir [isteğe bağlı](../../../visual-basic/language-reference/modifiers/optional.md) parametresi ile uyumlu olmayan bir türün varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="29ea6-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../../../visual-basic/language-reference/modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="29ea6-104">İle uyumlu olması için bir yordam için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), yalnızca CLS uyumlu türler kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="29ea6-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="29ea6-105">Bu parametre türleri, dönüş türü ve tüm yerel değişkenlerin türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29ea6-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="29ea6-106">Ayrıca, isteğe bağlı parametrelerinin varsayılan değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29ea6-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="29ea6-107">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="29ea6-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="29ea6-108">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="29ea6-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="29ea6-109">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="29ea6-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="29ea6-110">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="29ea6-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="29ea6-111">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="29ea6-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="29ea6-112">Uyguladığınızda <xref:System.CLSCompliantAttribute> özniteliği özniteliğin ayarladığınız bir programlama öğesine `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="29ea6-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="29ea6-113">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="29ea6-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="29ea6-114">Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="29ea6-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="29ea6-115">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="29ea6-115">By default, this message is a warning.</span></span> <span data-ttu-id="29ea6-116">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="29ea6-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="29ea6-117">**Hata Kimliği:** BC40042</span><span class="sxs-lookup"><span data-stu-id="29ea6-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="29ea6-118">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="29ea6-118">To correct this error</span></span>  
  
- <span data-ttu-id="29ea6-119">İsteğe bağlı parametre isteyenler bu tür bir varsayılan değerine sahip olmalıdır, kaldırmanız <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="29ea6-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="29ea6-120">Yordamı, CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="29ea6-120">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="29ea6-121">Yordamı CLS uyumlu olması gerekiyorsa, bu varsayılan değer türü en yakın CLS uyumlu türüne değiştirin.</span><span class="sxs-lookup"><span data-stu-id="29ea6-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="29ea6-122">Örneğin, içinde yerine, `UInteger` kullanmanız mümkün olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="29ea6-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="29ea6-123">Genişletilmiş aralık gerekiyorsa, değiştirebileceğiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="29ea6-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="29ea6-124">Otomasyon ve COM nesneleri ile arabirim, .NET Framework'teki bazı türleri değerinden farklı veri genişliği olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="29ea6-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="29ea6-125">Örneğin, `int` 16 bit diğer ortamlarda genellikle olur.</span><span class="sxs-lookup"><span data-stu-id="29ea6-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="29ea6-126">Böyle bir bileşenin bir 16 bitlik tamsayı kabul ediyorsanız, olarak bildirin `Short` yerine `Integer` Yönetilen Visual Basic kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="29ea6-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
