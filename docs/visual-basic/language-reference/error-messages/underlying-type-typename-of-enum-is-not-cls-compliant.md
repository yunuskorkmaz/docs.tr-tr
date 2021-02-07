---
description: 'Hakkında daha fazla bilgi edinin: BC40032: <typename> sabit listesinin temel alınan türü CLS uyumlu değil'
title: Enum tarafından temel olarak kullanılan <typename> türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: aebee5a9e0cd7f2e780d0171ad59dcfd4fd1d940
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674798"
---
# <a name="bc40032-underlying-type-typename-of-enum-is-not-cls-compliant"></a><span data-ttu-id="0ea3d-103">BC40032: sabit listesinin temel alınan türü \<typename> CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="0ea3d-103">BC40032: Underlying type \<typename> of Enum is not CLS-compliant</span></span>

<span data-ttu-id="0ea3d-104">Bu numaralandırma için belirtilen veri türü, [dil bağımsızlık ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) 'nin (CLS) bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-104">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="0ea3d-105">.NET Framework ve Visual Basic bu veri türünü desteklediği için bu, bileşeninizdeki bir hata değildir.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-105">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="0ea3d-106">Ancak, tamamen CLS uyumlu kodda yazılmış başka bir bileşen bu veri türünü desteklemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-106">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="0ea3d-107">Bu tür bir bileşen, bileşeniniz ile başarılı bir şekilde etkileşim kurabilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-107">Such a component might not be able to interact successfully with your component.</span></span>

 <span data-ttu-id="0ea3d-108">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="0ea3d-108">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="0ea3d-109">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0ea3d-109">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="0ea3d-110">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0ea3d-110">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="0ea3d-111">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0ea3d-111">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="0ea3d-112">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0ea3d-112">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="0ea3d-113">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-113">By default, this message is a warning.</span></span> <span data-ttu-id="0ea3d-114">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0ea3d-114">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="0ea3d-115">**Hata kimliği:** BC40032</span><span class="sxs-lookup"><span data-stu-id="0ea3d-115">**Error ID:** BC40032</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0ea3d-116">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0ea3d-116">To correct this error</span></span>

- <span data-ttu-id="0ea3d-117">Bileşeniniz yalnızca diğer .NET Framework bileşenleriyle arabirimlerinizde veya başka herhangi bir bileşenle arabirim içermiyorsa, herhangi bir şeyi değiştirmenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-117">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>

- <span data-ttu-id="0ea3d-118">.NET Framework için yazılmayan bir bileşenle ilgili bir arabiriminiz varsa, bu veri türünü destekleyip desteklemediğine göre, yansıma veya belgelerinden birini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-118">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="0ea3d-119">Varsa, herhangi bir değişiklik yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-119">If it does, you do not need to change anything.</span></span>

- <span data-ttu-id="0ea3d-120">Bu veri türünü desteklemeyen bir bileşenle ilgili arabiriminiz varsa, bunu en yakın CLS uyumlu türle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-120">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="0ea3d-121">Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="0ea3d-122">Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .</span><span class="sxs-lookup"><span data-stu-id="0ea3d-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="0ea3d-123">Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="0ea3d-124">Örneğin, `uint` genellikle diğer ortamlarda 16 bittir.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-124">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="0ea3d-125">Böyle bir bileşene 16 bitlik bir bağımsız değişken geçirirseniz, bunu `UShort` `UInteger` yönetilen Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-125">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ea3d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ea3d-126">See also</span></span>

- [<span data-ttu-id="0ea3d-127">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ea3d-127">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)
- [<span data-ttu-id="0ea3d-128">Yansıma</span><span class="sxs-lookup"><span data-stu-id="0ea3d-128">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
