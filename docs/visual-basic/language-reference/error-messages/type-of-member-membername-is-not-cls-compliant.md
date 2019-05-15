---
title: "'<membername>' üyesinin türü CLS uyumlu değil"
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: f6f66617774dccff4450cce42904126acf5c3769
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590677"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a><span data-ttu-id="c74e7-102">Üye türü '\<membername >' CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="c74e7-102">Type of member '\<membername>' is not CLS-compliant</span></span>
<span data-ttu-id="c74e7-103">Bu üye olmadığı için belirtilen veri türü parçası [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="c74e7-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="c74e7-104">Bu veri türü .NET Framework ve Visual Basic desteklediğinden, bir hata, bileşen içinde değil.</span><span class="sxs-lookup"><span data-stu-id="c74e7-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="c74e7-105">Ancak, başka bir bileşen kesinlikle CLS uyumlu bir kod halinde yazılmış bu veri türünü desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="c74e7-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="c74e7-106">Böyle bir bileşene başarıyla bileşeniniz ile etkileşim kurmak mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c74e7-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="c74e7-107">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="c74e7-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="c74e7-108">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c74e7-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="c74e7-109">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c74e7-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="c74e7-110">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c74e7-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="c74e7-111">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c74e7-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="c74e7-112">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="c74e7-112">By default, this message is a warning.</span></span> <span data-ttu-id="c74e7-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c74e7-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c74e7-114">**Hata Kimliği:** BC40025</span><span class="sxs-lookup"><span data-stu-id="c74e7-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c74e7-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c74e7-115">To correct this error</span></span>  
  
- <span data-ttu-id="c74e7-116">Bileşeniniz yalnızca diğer .NET Framework bileşenlerini arabirimleri ya da diğer bileşenlerle arabirimi değil, herhangi bir ayarı değiştirmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c74e7-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="c74e7-117">.NET Framework için yazılmaz bir bileşeni ile arabirim, bu veri türünü destekleyip desteklemediğini, yansıma aracılığıyla ya da belge, belirlemek mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="c74e7-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="c74e7-118">Aşması durumunda, değişikliği gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c74e7-118">If it does, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="c74e7-119">Bu veri türü desteklemeyen bir bileşen ile arabirim, en yakın CLS uyumlu türü ile değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c74e7-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="c74e7-120">Örneğin, içinde yerine, `UInteger` kullanmanız mümkün olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="c74e7-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="c74e7-121">Genişletilmiş aralık gerekiyorsa, değiştirebileceğiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="c74e7-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="c74e7-122">Otomasyon ve COM nesneleri ile arabirim, .NET Framework'teki bazı türleri değerinden farklı veri genişliği olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c74e7-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="c74e7-123">Örneğin, `uint` 16 bit diğer ortamlarda genellikle olur.</span><span class="sxs-lookup"><span data-stu-id="c74e7-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="c74e7-124">Bir 16 bit bağımsız değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `UShort` yerine `UInteger` Yönetilen Visual Basic kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="c74e7-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74e7-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c74e7-125">See also</span></span>

- [<span data-ttu-id="c74e7-126">Yansıma</span><span class="sxs-lookup"><span data-stu-id="c74e7-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
