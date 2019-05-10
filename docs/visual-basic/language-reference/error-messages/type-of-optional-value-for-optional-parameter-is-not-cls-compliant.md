---
title: <parametername> isteğe bağlı parametresi için isteğe bağlı değerin türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: ee7d208f7a579f81690ffbda265bde29316e4ec3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664296"
---
# <a name="type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="0f3ac-102">İsteğe bağlı parametre için isteğe bağlı değerin türü \<parametername > CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="0f3ac-102">Type of optional value for optional parameter \<parametername> is not CLS-compliant</span></span>
<span data-ttu-id="0f3ac-103">Bir yordam olarak işaretlenmiş `<CLSCompliant(True)>` bildirir, ancak bir [isteğe bağlı](../../../visual-basic/language-reference/modifiers/optional.md) parametresi ile uyumlu olmayan bir türün varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../../../visual-basic/language-reference/modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="0f3ac-104">İle uyumlu olması için bir yordam için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), yalnızca CLS uyumlu türler kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="0f3ac-105">Bu parametre türleri, dönüş türü ve tüm yerel değişkenlerin türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="0f3ac-106">Ayrıca, isteğe bağlı parametrelerinin varsayılan değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="0f3ac-107">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="0f3ac-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="0f3ac-108">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0f3ac-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="0f3ac-109">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0f3ac-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="0f3ac-110">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0f3ac-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="0f3ac-111">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0f3ac-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="0f3ac-112">Uyguladığınızda <xref:System.CLSCompliantAttribute> özniteliği özniteliğin ayarladığınız bir programlama öğesine `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="0f3ac-113">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="0f3ac-114">Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="0f3ac-115">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-115">By default, this message is a warning.</span></span> <span data-ttu-id="0f3ac-116">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0f3ac-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0f3ac-117">**Hata Kimliği:** BC40042</span><span class="sxs-lookup"><span data-stu-id="0f3ac-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f3ac-118">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0f3ac-118">To correct this error</span></span>  
  
- <span data-ttu-id="0f3ac-119">İsteğe bağlı parametre isteyenler bu tür bir varsayılan değerine sahip olmalıdır, kaldırmanız <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="0f3ac-120">Yordamı, CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-120">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="0f3ac-121">Yordamı CLS uyumlu olması gerekiyorsa, bu varsayılan değer türü en yakın CLS uyumlu türüne değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="0f3ac-122">Örneğin, içinde yerine, `UInteger` kullanmanız mümkün olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="0f3ac-123">Genişletilmiş aralık gerekiyorsa, değiştirebileceğiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="0f3ac-124">Otomasyon ve COM nesneleri ile arabirim, bazı türleri farklı veri genişliği kıyasla olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f3ac-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="0f3ac-125">Örneğin, `int` 16 bit diğer ortamlarda genellikle olur.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="0f3ac-126">Böyle bir bileşenin bir 16 bitlik tamsayı kabul ediyorsanız, olarak bildirin `Short` yerine `Integer` Yönetilen Visual Basic kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="0f3ac-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>