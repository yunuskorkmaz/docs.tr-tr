---
description: "Hakkında daha fazla bilgi edinin: BC40025: ' ' üyesinin türü <membername> CLS uyumlu değil"
title: "'<membername>' üyesinin türü CLS uyumlu değil"
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: 4fe83999a0cb2d678ccc0119509a368160dfc3ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774882"
---
# <a name="bc40025-type-of-member-membername-is-not-cls-compliant"></a><span data-ttu-id="a0e49-103">BC40025: ' ' üyesinin türü \<membername> CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="a0e49-103">BC40025: Type of member '\<membername>' is not CLS-compliant</span></span>

<span data-ttu-id="a0e49-104">Bu üye için belirtilen veri türü, [dil bağımsızlık ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) 'nin (CLS) bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="a0e49-104">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="a0e49-105">.NET Framework ve Visual Basic bu veri türünü desteklediği için bu, bileşeninizdeki bir hata değildir.</span><span class="sxs-lookup"><span data-stu-id="a0e49-105">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="a0e49-106">Ancak, tamamen CLS uyumlu kodda yazılmış başka bir bileşen bu veri türünü desteklemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="a0e49-106">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="a0e49-107">Bu tür bir bileşen, bileşeniniz ile başarılı bir şekilde etkileşim kurabilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="a0e49-107">Such a component might not be able to interact successfully with your component.</span></span>

 <span data-ttu-id="a0e49-108">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="a0e49-108">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="a0e49-109">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a0e49-109">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="a0e49-110">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a0e49-110">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="a0e49-111">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a0e49-111">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="a0e49-112">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a0e49-112">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="a0e49-113">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="a0e49-113">By default, this message is a warning.</span></span> <span data-ttu-id="a0e49-114">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a0e49-114">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="a0e49-115">**Hata kimliği:** BC40025</span><span class="sxs-lookup"><span data-stu-id="a0e49-115">**Error ID:** BC40025</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a0e49-116">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a0e49-116">To correct this error</span></span>

- <span data-ttu-id="a0e49-117">Bileşeniniz yalnızca diğer .NET Framework bileşenleriyle arabirimlerinizde veya başka herhangi bir bileşenle arabirim içermiyorsa, herhangi bir şeyi değiştirmenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="a0e49-117">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>

- <span data-ttu-id="a0e49-118">.NET Framework için yazılmayan bir bileşenle ilgili bir arabiriminiz varsa, bu veri türünü destekleyip desteklemediğine göre, yansıma veya belgelerinden birini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0e49-118">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="a0e49-119">Varsa, herhangi bir değişiklik yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a0e49-119">If it does, you do not need to change anything.</span></span>

- <span data-ttu-id="a0e49-120">Bu veri türünü desteklemeyen bir bileşenle ilgili arabiriminiz varsa, bunu en yakın CLS uyumlu türle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a0e49-120">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="a0e49-121">Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0e49-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="a0e49-122">Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .</span><span class="sxs-lookup"><span data-stu-id="a0e49-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="a0e49-123">Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a0e49-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="a0e49-124">Örneğin, `uint` genellikle diğer ortamlarda 16 bittir.</span><span class="sxs-lookup"><span data-stu-id="a0e49-124">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="a0e49-125">Böyle bir bileşene 16 bitlik bir bağımsız değişken geçirirseniz, bunu `UShort` `UInteger` yönetilen Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="a0e49-125">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0e49-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0e49-126">See also</span></span>

- [<span data-ttu-id="a0e49-127">Yansıma</span><span class="sxs-lookup"><span data-stu-id="a0e49-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
