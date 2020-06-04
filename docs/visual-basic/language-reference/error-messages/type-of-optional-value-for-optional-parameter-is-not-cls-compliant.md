---
title: <parametername> isteğe bağlı parametresi için isteğe bağlı değerin türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: 8e53d036ead114d828d9035cef76cee72bf6b1db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400298"
---
# <a name="type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="82aa8-102">\<parametername> isteğe bağlı parametresi için isteğe bağlı değerin türü CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="82aa8-102">Type of optional value for optional parameter \<parametername> is not CLS-compliant</span></span>
<span data-ttu-id="82aa8-103">Bir yordam olarak işaretlenir, `<CLSCompliant(True)>` ancak uyumlu olmayan bir türün varsayılan değerine sahip [isteğe bağlı](../modifiers/optional.md) bir parametre bildirir.</span><span class="sxs-lookup"><span data-stu-id="82aa8-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="82aa8-104">Bir yordamın [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, yalnızca CLS uyumlu türler kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82aa8-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="82aa8-105">Bu, parametre türleri, dönüş türü ve tüm yerel değişkenlerinin türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="82aa8-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="82aa8-106">Ayrıca, isteğe bağlı parametrelerin varsayılan değerleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="82aa8-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="82aa8-107">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="82aa8-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="82aa8-108">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="82aa8-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="82aa8-109">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="82aa8-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="82aa8-110">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="82aa8-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="82aa8-111">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="82aa8-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="82aa8-112"><xref:System.CLSCompliantAttribute>Özniteliği bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu belirtmek için özniteliğin parametresini veya olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="82aa8-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="82aa8-113">Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="82aa8-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="82aa8-114"><xref:System.CLSCompliantAttribute>Bir öğesi için uygulamazsanız, uyumsuz olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="82aa8-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="82aa8-115">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="82aa8-115">By default, this message is a warning.</span></span> <span data-ttu-id="82aa8-116">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="82aa8-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="82aa8-117">**Hata kimliği:** BC40042</span><span class="sxs-lookup"><span data-stu-id="82aa8-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="82aa8-118">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="82aa8-118">To correct this error</span></span>  
  
- <span data-ttu-id="82aa8-119">İsteğe bağlı parametrenin bu belirli türden bir varsayılan değeri olması gerekiyorsa, öğesini kaldırın <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="82aa8-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="82aa8-120">Yordam CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="82aa8-120">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="82aa8-121">Yordamın CLS uyumlu olması gerekiyorsa, bu varsayılan değerin türünü, en yakın CLS uyumlu türe değiştirin.</span><span class="sxs-lookup"><span data-stu-id="82aa8-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="82aa8-122">Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82aa8-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="82aa8-123">Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .</span><span class="sxs-lookup"><span data-stu-id="82aa8-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="82aa8-124">Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="82aa8-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="82aa8-125">Örneğin, `int` genellikle diğer ortamlarda 16 bittir.</span><span class="sxs-lookup"><span data-stu-id="82aa8-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="82aa8-126">Böyle bir bileşenden 16 bit tam sayı kabul ediyorsanız, bunu `Short` `Integer` yönetilen Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="82aa8-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
