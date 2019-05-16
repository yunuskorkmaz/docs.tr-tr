---
title: "'<procedurename>' işlevinin dönüş türü CLS uyumlu değil"
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 881726ea2cfb23493d85097635adb15608ed741d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642251"
---
# <a name="return-type-of-function-procedurename-is-not-cls-compliant"></a><span data-ttu-id="aa27a-102">İşlevinin dönüş türü '\<procedurename >' CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="aa27a-102">Return type of function '\<procedurename>' is not CLS-compliant</span></span>
<span data-ttu-id="aa27a-103">A `Function` yordam olarak işaretlenmiş `<CLSCompliant(True)>` ancak olarak işaretlenmiş bir tür döndüren `<CLSCompliant(False)>`işaret konulmadıysa veya uyumlu olmayan bir tür olduğu için uygun değil.</span><span class="sxs-lookup"><span data-stu-id="aa27a-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="aa27a-104">İle uyumlu olması için bir yordam için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), yalnızca CLS uyumlu türler kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa27a-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="aa27a-105">Bu parametre türleri, dönüş türü ve tüm yerel değişkenlerin türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aa27a-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="aa27a-106">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="aa27a-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="aa27a-107">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="aa27a-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="aa27a-108">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="aa27a-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="aa27a-109">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="aa27a-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="aa27a-110">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="aa27a-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="aa27a-111">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesine özniteliğin ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="aa27a-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="aa27a-112">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa27a-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="aa27a-113">Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aa27a-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="aa27a-114">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="aa27a-114">By default, this message is a warning.</span></span> <span data-ttu-id="aa27a-115">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="aa27a-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="aa27a-116">**Hata Kimliği:** BC40027</span><span class="sxs-lookup"><span data-stu-id="aa27a-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aa27a-117">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="aa27a-117">To correct this error</span></span>  
  
- <span data-ttu-id="aa27a-118">Varsa `Function` yordamı bu türdeki döndürür, Kaldır <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="aa27a-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="aa27a-119">Yordamı, CLS uyumlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="aa27a-119">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="aa27a-120">Varsa `Function` yordamı CLS uyumlu olmalıdır, dönüş türünü değiştirmek için en yakın CLS uyumlu türü.</span><span class="sxs-lookup"><span data-stu-id="aa27a-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="aa27a-121">Örneğin, içinde yerine, `UInteger` kullanmanız mümkün olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="aa27a-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="aa27a-122">Genişletilmiş aralık gerekiyorsa, değiştirebileceğiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="aa27a-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="aa27a-123">Otomasyon ve COM nesneleri ile arabirim, .NET Framework'teki bazı türleri değerinden farklı veri genişliği olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="aa27a-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="aa27a-124">Örneğin, `int` 16 bit diğer ortamlarda genellikle olur.</span><span class="sxs-lookup"><span data-stu-id="aa27a-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="aa27a-125">Böyle bir bileşene bir 16 bitlik tamsayı döndüren, olarak bildirin `Short` yerine `Integer` Yönetilen Visual Basic kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="aa27a-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
