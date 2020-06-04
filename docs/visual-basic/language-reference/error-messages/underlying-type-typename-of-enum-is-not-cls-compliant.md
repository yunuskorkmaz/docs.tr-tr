---
title: Enum tarafından temel olarak kullanılan <typename> türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 79faf0038b2b313bdc21e12c8ae76854bcd6957f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406579"
---
# <a name="underlying-type-typename-of-enum-is-not-cls-compliant"></a><span data-ttu-id="2e2fb-102">Enum tarafından temel olarak kullanılan \<typename> türü CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="2e2fb-102">Underlying type \<typename> of Enum is not CLS-compliant</span></span>
<span data-ttu-id="2e2fb-103">Bu numaralandırma için belirtilen veri türü, [Dil bağımsızlığı ve dilden bağımsız bileşenlerin](../../../standard/language-independence-and-language-independent-components.md) (CLS) bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="2e2fb-104">.NET Framework ve Visual Basic bu veri türünü desteklediği için bu, bileşeninizdeki bir hata değildir.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="2e2fb-105">Ancak, tamamen CLS uyumlu kodda yazılmış başka bir bileşen bu veri türünü desteklemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="2e2fb-106">Bu tür bir bileşen, bileşeniniz ile başarılı bir şekilde etkileşim kurabilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="2e2fb-107">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="2e2fb-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="2e2fb-108">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2e2fb-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="2e2fb-109">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2e2fb-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="2e2fb-110">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2e2fb-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="2e2fb-111">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2e2fb-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="2e2fb-112">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-112">By default, this message is a warning.</span></span> <span data-ttu-id="2e2fb-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2e2fb-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2e2fb-114">**Hata kimliği:** BC40032</span><span class="sxs-lookup"><span data-stu-id="2e2fb-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2e2fb-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2e2fb-115">To correct this error</span></span>  
  
- <span data-ttu-id="2e2fb-116">Bileşeniniz yalnızca diğer .NET Framework bileşenleriyle arabirimlerinizde veya başka herhangi bir bileşenle arabirim içermiyorsa, herhangi bir şeyi değiştirmenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="2e2fb-117">.NET Framework için yazılmayan bir bileşenle ilgili bir arabiriminiz varsa, bu veri türünü destekleyip desteklemediğine göre, yansıma veya belgelerinden birini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="2e2fb-118">Varsa, herhangi bir değişiklik yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-118">If it does, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="2e2fb-119">Bu veri türünü desteklemeyen bir bileşenle ilgili arabiriminiz varsa, bunu en yakın CLS uyumlu türle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="2e2fb-120">Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="2e2fb-121">Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .</span><span class="sxs-lookup"><span data-stu-id="2e2fb-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="2e2fb-122">Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="2e2fb-123">Örneğin, `uint` genellikle diğer ortamlarda 16 bittir.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="2e2fb-124">Böyle bir bileşene 16 bitlik bir bağımsız değişken geçirirseniz, bunu `UShort` `UInteger` yönetilen Visual Basic kodunuzda değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e2fb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e2fb-125">See also</span></span>

- [<span data-ttu-id="2e2fb-126">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e2fb-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)
- [<span data-ttu-id="2e2fb-127">Yansıma</span><span class="sxs-lookup"><span data-stu-id="2e2fb-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
