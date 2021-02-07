---
description: "Hakkında daha fazla bilgi edinin: BC40028: ' ' parametresinin türü <parametername> CLS uyumlu değil"
title: "'<parametername>' parametresinin türü CLS uyumlu değil"
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: 5e430e55e24001d779243645cf4b409d1801d6f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731163"
---
# <a name="bc40028-type-of-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="1ebf7-103">BC40028: ' ' parametresinin türü \<parametername> CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="1ebf7-103">BC40028: Type of parameter '\<parametername>' is not CLS-compliant</span></span>

<span data-ttu-id="1ebf7-104">Bir yordam olarak işaretlenir `<CLSCompliant(True)>` , ancak olarak işaretlenen `<CLSCompliant(False)>` , işaretlenmemiş veya uyumsuz bir tür olduğundan uygun olmayan bir parametre bildirir.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-104">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>

 <span data-ttu-id="1ebf7-105">Bir yordamın [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, yalnızca CLS uyumlu türler kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-105">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="1ebf7-106">Bu, parametre türleri, dönüş türü ve tüm yerel değişkenlerinin türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-106">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>

 <span data-ttu-id="1ebf7-107">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="1ebf7-107">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="1ebf7-108">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="1ebf7-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="1ebf7-109">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="1ebf7-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="1ebf7-110">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="1ebf7-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="1ebf7-111">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="1ebf7-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="1ebf7-112"><xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-112">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="1ebf7-113">Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-113">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="1ebf7-114"><xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-114">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="1ebf7-115">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-115">By default, this message is a warning.</span></span> <span data-ttu-id="1ebf7-116">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1ebf7-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="1ebf7-117">**Hata kimliği:** BC40028</span><span class="sxs-lookup"><span data-stu-id="1ebf7-117">**Error ID:** BC40028</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1ebf7-118">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1ebf7-118">To correct this error</span></span>

- <span data-ttu-id="1ebf7-119">Yordam bu belirli türden bir parametre almalıdır, öğesini kaldırın <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="1ebf7-119">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="1ebf7-120">Yordam CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-120">The procedure cannot be CLS-compliant.</span></span>

- <span data-ttu-id="1ebf7-121">Yordamın CLS uyumlu olması gerekiyorsa, bu parametrenin türünü, en yakın CLS uyumlu türle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-121">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="1ebf7-122">Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="1ebf7-123">Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .</span><span class="sxs-lookup"><span data-stu-id="1ebf7-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="1ebf7-124">Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="1ebf7-125">Örneğin, `int` genellikle diğer ortamlarda 16 bittir.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="1ebf7-126">Böyle bir bileşenden 16 bit tam sayı kabul ediyorsanız, bunu `Short` `Integer` yönetilen Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="1ebf7-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
