---
title: "Boole Veri Türü (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdc106f1ec874c1a2165df069d5f3485fe5b2e43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="13fec-102">Boole Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13fec-102">Boolean Data Type (Visual Basic)</span></span>
<span data-ttu-id="13fec-103">Yalnızca ayrı tutma değerleri `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="13fec-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="13fec-104">Anahtar sözcükler `True` ve `False` için iki durumlarını karşılık `Boolean` değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="13fec-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13fec-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13fec-105">Remarks</span></span>  
 <span data-ttu-id="13fec-106">Kullanım [Boole veri türü (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) true/false gibi iki durumlu değerler içermesini Evet/Hayır, veya açık/kapalı.</span><span class="sxs-lookup"><span data-stu-id="13fec-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="13fec-107">Varsayılan değer olan `Boolean` olan `False`.</span><span class="sxs-lookup"><span data-stu-id="13fec-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="13fec-108">`Boolean`değerleri sayı olarak depolanmaz ve depolanan değerlerin sayıya eşit olması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="13fec-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="13fec-109">Hiçbir zaman eşdeğer sayısal değerler için güvenen kod yazmanız gerekir `True` ve `False`.</span><span class="sxs-lookup"><span data-stu-id="13fec-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="13fec-110">Mümkün olduğunda, kullanımını kısıtlamalısınız `Boolean` , bunlar tasarlanan mantıksal değerleri değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="13fec-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="13fec-111">Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="13fec-111">Type Conversions</span></span>  
 <span data-ttu-id="13fec-112">Visual Basic sayısal veri türü değerleri için ne zaman dönüştürür `Boolean`, 0 olur `False` ve diğer tüm değerler duruma `True`.</span><span class="sxs-lookup"><span data-stu-id="13fec-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="13fec-113">Visual Basic zaman dönüştürür `Boolean` sayısal türler değerlere `False` 0 olur ve `True` -1 olur.</span><span class="sxs-lookup"><span data-stu-id="13fec-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="13fec-114">Arasında dönüştürürken `Boolean` değerleri ve sayısal veri türleri tutmak .NET Framework dönüştürme yöntemleri her zaman aynı sonucu olarak Visual Basic dönüşüm anahtar sözcükleri vermez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="13fec-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="13fec-115">Visual Basic dönüştürme davranış önceki sürümleriyle uyumlu koruyacağından budur.</span><span class="sxs-lookup"><span data-stu-id="13fec-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="13fec-116">Daha fazla bilgi için "Boole türü mu değil dönüştürmek için sayısal türü doğru şekilde" bölümüne bakın [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="13fec-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="13fec-117">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="13fec-117">Programming Tips</span></span>  
  
-   <span data-ttu-id="13fec-118">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="13fec-118">**Negative Numbers.**</span></span> <span data-ttu-id="13fec-119">`Boolean`sayısal bir tür değil ve negatif bir değeri temsil edilemez.</span><span class="sxs-lookup"><span data-stu-id="13fec-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="13fec-120">Her iki durumda da kullanılamaz `Boolean` sayısal değerleri tutmak için.</span><span class="sxs-lookup"><span data-stu-id="13fec-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="13fec-121">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="13fec-121">**Type Characters.**</span></span> <span data-ttu-id="13fec-122">`Boolean`değişmez değer türü karakteri ya da tanımlayıcı türü karakteri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="13fec-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="13fec-123">**Framework türü.**</span><span class="sxs-lookup"><span data-stu-id="13fec-123">**Framework Type.**</span></span> <span data-ttu-id="13fec-124">.NET Framework'teki karşılık gelen tür <xref:System.Boolean?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="13fec-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13fec-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="13fec-125">Example</span></span>  
 <span data-ttu-id="13fec-126">Aşağıdaki örnekte, `runningVB` olan bir `Boolean` Evet/Hayır ayarı basit depolar değişkeni.</span><span class="sxs-lookup"><span data-stu-id="13fec-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="13fec-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13fec-127">See Also</span></span>  
 <xref:System.Boolean?displayProperty=nameWithType>  
 [<span data-ttu-id="13fec-128">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="13fec-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="13fec-129">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="13fec-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="13fec-130">Dönüştürme özeti</span><span class="sxs-lookup"><span data-stu-id="13fec-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="13fec-131">Veri türlerinin etkili kullanımı</span><span class="sxs-lookup"><span data-stu-id="13fec-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="13fec-132">Veri türleri sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="13fec-132">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="13fec-133">CType işlevi</span><span class="sxs-lookup"><span data-stu-id="13fec-133">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
