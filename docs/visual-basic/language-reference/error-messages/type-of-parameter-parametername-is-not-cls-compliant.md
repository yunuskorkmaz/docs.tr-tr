---
title: "'<parametername>' parametresinin türü CLS uyumlu değil"
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: a4617d3550cfb48f32a19a4c70809141173c6147
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875124"
---
# <a name="type-of-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="3826b-102">'\<parametername>' parametresinin türü CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="3826b-102">Type of parameter '\<parametername>' is not CLS-compliant</span></span>

<span data-ttu-id="3826b-103">Bir yordam olarak işaretlenir `<CLSCompliant(True)>` , ancak olarak işaretlenen `<CLSCompliant(False)>` , işaretlenmemiş veya uyumsuz bir tür olduğundan uygun olmayan bir parametre bildirir.</span><span class="sxs-lookup"><span data-stu-id="3826b-103">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="3826b-104">Bir yordamın [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, yalnızca CLS uyumlu türler kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3826b-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="3826b-105">Bu, parametre türleri, dönüş türü ve tüm yerel değişkenlerinin türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3826b-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="3826b-106">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="3826b-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="3826b-107">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="3826b-107">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="3826b-108">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="3826b-108">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="3826b-109">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="3826b-109">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="3826b-110">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="3826b-110">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="3826b-111"><xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3826b-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="3826b-112">Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3826b-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="3826b-113"><xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3826b-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="3826b-114">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="3826b-114">By default, this message is a warning.</span></span> <span data-ttu-id="3826b-115">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3826b-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3826b-116">**Hata kimliği:** BC40028</span><span class="sxs-lookup"><span data-stu-id="3826b-116">**Error ID:** BC40028</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3826b-117">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3826b-117">To correct this error</span></span>  
  
- <span data-ttu-id="3826b-118">Yordam bu belirli türden bir parametre almalıdır, öğesini kaldırın <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3826b-118">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="3826b-119">Yordam CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="3826b-119">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="3826b-120">Yordamın CLS uyumlu olması gerekiyorsa, bu parametrenin türünü, en yakın CLS uyumlu türle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3826b-120">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="3826b-121">Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3826b-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="3826b-122">Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .</span><span class="sxs-lookup"><span data-stu-id="3826b-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="3826b-123">Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="3826b-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="3826b-124">Örneğin, `int` genellikle diğer ortamlarda 16 bittir.</span><span class="sxs-lookup"><span data-stu-id="3826b-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="3826b-125">Böyle bir bileşenden 16 bit tam sayı kabul ediyorsanız, bunu `Short` `Integer` yönetilen Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="3826b-125">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
