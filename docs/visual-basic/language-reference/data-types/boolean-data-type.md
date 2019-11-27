---
title: Boole Veri Türü
ms.date: 07/20/2015
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
ms.openlocfilehash: 5d05514207c5d07e81aab897f40f728570f6bd87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347843"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="09128-102">Boole Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09128-102">Boolean Data Type (Visual Basic)</span></span>

<span data-ttu-id="09128-103">Yalnızca `True` veya `False`olabilecek değerleri tutar.</span><span class="sxs-lookup"><span data-stu-id="09128-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="09128-104">`True` ve `False` anahtar sözcükleri `Boolean` değişkenlerinin iki durumuna karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="09128-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09128-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09128-105">Remarks</span></span>  

 <span data-ttu-id="09128-106">True/false, Yes/No veya on/off gibi iki durumlu değerler içeren [Boolean veri türü (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="09128-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="09128-107">`Boolean` varsayılan değeri `False`.</span><span class="sxs-lookup"><span data-stu-id="09128-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="09128-108">`Boolean` değerler sayı olarak depolanmaz ve depolanan değerlerin sayılara eşit olması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="09128-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="09128-109">`True` ve `False`için eşdeğer sayısal değerleri temel alan hiçbir kodu asla yazmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="09128-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="09128-110">Mümkün olduğunda, `Boolean` değişkenlerinin kullanımını, tasarlandıkları mantıksal değerlerle kısıtlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="09128-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="09128-111">Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="09128-111">Type Conversions</span></span>  

 <span data-ttu-id="09128-112">Visual Basic sayısal veri türü değerlerini `Boolean`dönüştürdüğünde 0 `False` ve diğer tüm değerler `True`olur.</span><span class="sxs-lookup"><span data-stu-id="09128-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="09128-113">Visual Basic `Boolean` değerlerini sayısal türlere dönüştürdüğünde, `False` 0 olur ve `True` 1 olur.</span><span class="sxs-lookup"><span data-stu-id="09128-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="09128-114">`Boolean` değerleri ve sayısal veri türleri arasında dönüştürme yaptığınızda, .NET Framework dönüştürme yöntemlerinin Visual Basic dönüştürme anahtar sözcükleriyle her zaman aynı sonuçları üretmeyeceğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="09128-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="09128-115">Bunun nedeni Visual Basic dönüştürmenin önceki sürümlerle uyumlu davranışları korumasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="09128-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="09128-116">Daha fazla bilgi için bkz. [sorun giderme veri türlerinde](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)"Boole türü doğru şekilde sayısal türe dönüştürülmüyor".</span><span class="sxs-lookup"><span data-stu-id="09128-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="09128-117">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="09128-117">Programming Tips</span></span>  
  
- <span data-ttu-id="09128-118">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="09128-118">**Negative Numbers.**</span></span> <span data-ttu-id="09128-119">`Boolean` sayısal bir tür değil ve negatif bir değeri temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="09128-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="09128-120">Herhangi bir durumda, sayısal değerleri tutmak için `Boolean` kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="09128-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="09128-121">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="09128-121">**Type Characters.**</span></span> <span data-ttu-id="09128-122">`Boolean` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="09128-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="09128-123">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="09128-123">**Framework Type.**</span></span> <span data-ttu-id="09128-124">.NET Framework karşılık gelen tür <xref:System.Boolean?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="09128-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09128-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="09128-125">Example</span></span>  

 <span data-ttu-id="09128-126">Aşağıdaki örnekte `runningVB`, basit bir Evet/Hayır ayarı depolayan bir `Boolean` değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="09128-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="09128-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09128-127">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="09128-128">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="09128-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="09128-129">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="09128-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="09128-130">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="09128-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="09128-131">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="09128-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="09128-132">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="09128-132">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="09128-133">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="09128-133">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
