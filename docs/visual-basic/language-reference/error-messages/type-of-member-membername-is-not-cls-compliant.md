---
title: "'<membername>' üyesinin türü CLS uyumlu değil"
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: c8c14a2d6df8804967807af881384bc7d9ccd99f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163486"
---
# <a name="bc40025-type-of-member-membername-is-not-cls-compliant"></a><span data-ttu-id="418c0-102">BC40025: ' ' üyesinin türü \<membername> CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="418c0-102">BC40025: Type of member '\<membername>' is not CLS-compliant</span></span>

<span data-ttu-id="418c0-103">Bu üye için belirtilen veri türü, [dil bağımsızlık ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) 'nin (CLS) bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="418c0-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="418c0-104">.NET Framework ve Visual Basic bu veri türünü desteklediği için bu, bileşeninizdeki bir hata değildir.</span><span class="sxs-lookup"><span data-stu-id="418c0-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="418c0-105">Ancak, tamamen CLS uyumlu kodda yazılmış başka bir bileşen bu veri türünü desteklemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="418c0-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="418c0-106">Bu tür bir bileşen, bileşeniniz ile başarılı bir şekilde etkileşim kurabilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="418c0-106">Such a component might not be able to interact successfully with your component.</span></span>

 <span data-ttu-id="418c0-107">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="418c0-107">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="418c0-108">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="418c0-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="418c0-109">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="418c0-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="418c0-110">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="418c0-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="418c0-111">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="418c0-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="418c0-112">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="418c0-112">By default, this message is a warning.</span></span> <span data-ttu-id="418c0-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="418c0-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="418c0-114">**Hata kimliği:** BC40025</span><span class="sxs-lookup"><span data-stu-id="418c0-114">**Error ID:** BC40025</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="418c0-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="418c0-115">To correct this error</span></span>

- <span data-ttu-id="418c0-116">Bileşeniniz yalnızca diğer .NET Framework bileşenleriyle arabirimlerinizde veya başka herhangi bir bileşenle arabirim içermiyorsa, herhangi bir şeyi değiştirmenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="418c0-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>

- <span data-ttu-id="418c0-117">.NET Framework için yazılmayan bir bileşenle ilgili bir arabiriminiz varsa, bu veri türünü destekleyip desteklemediğine göre, yansıma veya belgelerinden birini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="418c0-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="418c0-118">Varsa, herhangi bir değişiklik yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="418c0-118">If it does, you do not need to change anything.</span></span>

- <span data-ttu-id="418c0-119">Bu veri türünü desteklemeyen bir bileşenle ilgili arabiriminiz varsa, bunu en yakın CLS uyumlu türle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="418c0-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="418c0-120">Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="418c0-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="418c0-121">Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .</span><span class="sxs-lookup"><span data-stu-id="418c0-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="418c0-122">Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="418c0-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="418c0-123">Örneğin, `uint` genellikle diğer ortamlarda 16 bittir.</span><span class="sxs-lookup"><span data-stu-id="418c0-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="418c0-124">Böyle bir bileşene 16 bitlik bir bağımsız değişken geçirirseniz, bunu `UShort` `UInteger` yönetilen Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="418c0-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

## <a name="see-also"></a><span data-ttu-id="418c0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="418c0-125">See also</span></span>

- [<span data-ttu-id="418c0-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="418c0-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
