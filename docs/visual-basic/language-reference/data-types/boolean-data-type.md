---
title: Boole Veri Türü (Visual Basic)
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
ms.openlocfilehash: bbd914d8b4239bbae1de7031e68b2900cf5ad6a3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862389"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="fed43-102">Boole Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fed43-102">Boolean Data Type (Visual Basic)</span></span>
<span data-ttu-id="fed43-103">Yalnızca ayrı tutma değerleri `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="fed43-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="fed43-104">Anahtar sözcükler `True` ve `False` iki durum için karşılık gelen `Boolean` değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="fed43-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fed43-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fed43-105">Remarks</span></span>  
 <span data-ttu-id="fed43-106">Kullanım [Boole veri türü (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) Evet/Hayır veya açık/kapalı true/false gibi iki durumlu değerler içerecek şekilde.</span><span class="sxs-lookup"><span data-stu-id="fed43-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="fed43-107">Varsayılan değer olan `Boolean` olduğu `False`.</span><span class="sxs-lookup"><span data-stu-id="fed43-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="fed43-108">`Boolean` Değer sayı olarak depolanmaz ve depolanan değerler sayıya eşdeğer olması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="fed43-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="fed43-109">Hiçbir zaman eşdeğer sayısal değerler için dayanan kod yazmanız gerekir `True` ve `False`.</span><span class="sxs-lookup"><span data-stu-id="fed43-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="fed43-110">Mümkün olduğunda, kullanımını sınırlamanız gerekir `Boolean` kendisi için tasarlanan mantıksal değerleri değişkenlere.</span><span class="sxs-lookup"><span data-stu-id="fed43-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="fed43-111">Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="fed43-111">Type Conversions</span></span>  
 <span data-ttu-id="fed43-112">Visual Basic sayısal veri türü değerleri için ne zaman dönüştürür `Boolean`, 0 olur `False` ve diğer tüm değerler `True`.</span><span class="sxs-lookup"><span data-stu-id="fed43-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="fed43-113">Visual Basic zaman dönüştürür `Boolean` değerleri sayısal türlere `False` 0 olur ve `True` -1 olur.</span><span class="sxs-lookup"><span data-stu-id="fed43-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="fed43-114">Arasında dönüştürürken `Boolean` değerlerini ve sayısal veri türlerini tutmak .NET Framework dönüştürme yöntemleri Visual Basic dönüştürme anahtar sözcükleri'dekiyle aynı sonucu her zaman oluşturmamasını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fed43-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="fed43-115">Visual Basic dönüştürme davranışını önceki sürümleriyle uyumlu korur olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="fed43-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="fed43-116">Daha fazla bilgi için "Boole türü mu değil dönüştürmek için sayısal türü doğru" bölümüne bakın [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="fed43-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="fed43-117">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="fed43-117">Programming Tips</span></span>  
  
-   <span data-ttu-id="fed43-118">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="fed43-118">**Negative Numbers.**</span></span> <span data-ttu-id="fed43-119">`Boolean` bir sayısal tür değil ve negatif bir değeri temsil edemeyen.</span><span class="sxs-lookup"><span data-stu-id="fed43-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="fed43-120">Her iki durumda da kullanmamalısınız `Boolean` sayısal değerleri tutmak için.</span><span class="sxs-lookup"><span data-stu-id="fed43-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="fed43-121">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="fed43-121">**Type Characters.**</span></span> <span data-ttu-id="fed43-122">`Boolean` değişmez değer türü karakteri ya da tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="fed43-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="fed43-123">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="fed43-123">**Framework Type.**</span></span> <span data-ttu-id="fed43-124">.NET Framework içinde karşılık gelen türü <xref:System.Boolean?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="fed43-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fed43-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="fed43-125">Example</span></span>  
 <span data-ttu-id="fed43-126">Aşağıdaki örnekte, `runningVB` olduğu bir `Boolean` Evet/Hayır basit depolayan değişken.</span><span class="sxs-lookup"><span data-stu-id="fed43-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="fed43-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fed43-127">See Also</span></span>  
 <xref:System.Boolean?displayProperty=nameWithType>  
 [<span data-ttu-id="fed43-128">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="fed43-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="fed43-129">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fed43-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="fed43-130">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="fed43-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="fed43-131">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="fed43-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="fed43-132">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="fed43-132">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="fed43-133">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="fed43-133">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
