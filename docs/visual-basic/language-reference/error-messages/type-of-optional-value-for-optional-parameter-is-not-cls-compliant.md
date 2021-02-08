---
description: 'Hakkında daha fazla bilgi edinin: BC40042: isteğe bağlı parametre için isteğe bağlı değerin türü <parametername> CLS uyumlu değil'
title: <parametername> isteğe bağlı parametresi için isteğe bağlı değerin türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: 44dee07120ebcd99be69257aef6a334f9067cdb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774869"
---
# <a name="bc40042-type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="c520f-103">BC40042: isteğe bağlı parametre için isteğe bağlı değerin türü \<parametername> CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="c520f-103">BC40042: Type of optional value for optional parameter \<parametername> is not CLS-compliant</span></span>

<span data-ttu-id="c520f-104">Bir yordam olarak işaretlenir, `<CLSCompliant(True)>` ancak uyumlu olmayan bir türün varsayılan değerine sahip [isteğe bağlı](../modifiers/optional.md) bir parametre bildirir.</span><span class="sxs-lookup"><span data-stu-id="c520f-104">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>

 <span data-ttu-id="c520f-105">Bir yordamın [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, yalnızca CLS uyumlu türler kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c520f-105">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="c520f-106">Bu, parametre türleri, dönüş türü ve tüm yerel değişkenlerinin türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c520f-106">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="c520f-107">Ayrıca, isteğe bağlı parametrelerin varsayılan değerleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c520f-107">It also applies to the default values of optional parameters.</span></span>

 <span data-ttu-id="c520f-108">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="c520f-108">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="c520f-109">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c520f-109">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="c520f-110">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c520f-110">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="c520f-111">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c520f-111">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="c520f-112">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c520f-112">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="c520f-113"><xref:System.CLSCompliantAttribute>Özniteliği bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu belirtmek için özniteliğin parametresini veya olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c520f-113">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="c520f-114">Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c520f-114">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="c520f-115"><xref:System.CLSCompliantAttribute>Bir öğesi için uygulamazsanız, uyumsuz olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c520f-115">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="c520f-116">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="c520f-116">By default, this message is a warning.</span></span> <span data-ttu-id="c520f-117">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c520f-117">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="c520f-118">**Hata kimliği:** BC40042</span><span class="sxs-lookup"><span data-stu-id="c520f-118">**Error ID:** BC40042</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c520f-119">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c520f-119">To correct this error</span></span>

- <span data-ttu-id="c520f-120">İsteğe bağlı parametrenin bu belirli türden bir varsayılan değeri olması gerekiyorsa, öğesini kaldırın <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c520f-120">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="c520f-121">Yordam CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="c520f-121">The procedure cannot be CLS-compliant.</span></span>

- <span data-ttu-id="c520f-122">Yordamın CLS uyumlu olması gerekiyorsa, bu varsayılan değerin türünü, en yakın CLS uyumlu türe değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c520f-122">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="c520f-123">Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c520f-123">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="c520f-124">Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .</span><span class="sxs-lookup"><span data-stu-id="c520f-124">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="c520f-125">Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c520f-125">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="c520f-126">Örneğin, `int` genellikle diğer ortamlarda 16 bittir.</span><span class="sxs-lookup"><span data-stu-id="c520f-126">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="c520f-127">Böyle bir bileşenden 16 bit tam sayı kabul ediyorsanız, bunu `Short` `Integer` yönetilen Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="c520f-127">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
