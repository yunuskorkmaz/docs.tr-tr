---
description: 'Daha fazla bilgi edinin: Boolean veri türü (Visual Basic)'
title: Boolean Veri Türü
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
ms.openlocfilehash: cdda6bc0571eb0a2a9ee6a079ffd276bfc89a9b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731415"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="d6678-103">Boole Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6678-103">Boolean Data Type (Visual Basic)</span></span>

<span data-ttu-id="d6678-104">Yalnızca veya olabilecek değerleri barındırır `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="d6678-104">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="d6678-105">Anahtar sözcükler `True` ve `False` iki değişken için karşılık gelir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="d6678-105">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6678-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6678-106">Remarks</span></span>  

 <span data-ttu-id="d6678-107">True/false, Yes/No veya on/off gibi iki durumlu değerler içeren [Boolean veri türü (Visual Basic)](boolean-data-type.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d6678-107">Use the [Boolean Data Type (Visual Basic)](boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="d6678-108">Varsayılan değeri `Boolean` `False` .</span><span class="sxs-lookup"><span data-stu-id="d6678-108">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="d6678-109">`Boolean` değerler sayı olarak depolanmaz ve depolanan değerlerin sayılara eşit olması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="d6678-109">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="d6678-110">Ve için eşdeğer sayısal değerleri temel alan hiçbir kodu asla yazmamanız `True` gerekir `False` .</span><span class="sxs-lookup"><span data-stu-id="d6678-110">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="d6678-111">Mümkün olduğunda, `Boolean` değişkenlerin kullanımını tasarlandıkları mantıksal değerlerle kısıtlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="d6678-111">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="d6678-112">Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="d6678-112">Type Conversions</span></span>  

 <span data-ttu-id="d6678-113">Visual Basic sayısal veri türü değerlerini öğesine dönüştürdüğünde `Boolean` 0 olur `False` ve diğer tüm değerler olur `True` .</span><span class="sxs-lookup"><span data-stu-id="d6678-113">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="d6678-114">Visual Basic `Boolean` değerleri sayısal türlere dönüştürdüğünde `False` 0 olur ve `True` -1 olur.</span><span class="sxs-lookup"><span data-stu-id="d6678-114">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="d6678-115">`Boolean`Değerler ve sayısal veri türleri arasında dönüştürme yaptığınızda, .NET Framework dönüştürme yöntemlerinin Visual Basic dönüştürme anahtar sözcükleriyle her zaman aynı sonuçları üretmeyeceğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d6678-115">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="d6678-116">Bunun nedeni Visual Basic dönüştürmenin önceki sürümlerle uyumlu davranışları korumasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="d6678-116">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="d6678-117">Daha fazla bilgi için bkz. [sorun giderme veri türlerinde](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)"Boole türü doğru şekilde sayısal türe dönüştürülmüyor".</span><span class="sxs-lookup"><span data-stu-id="d6678-117">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="d6678-118">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="d6678-118">Programming Tips</span></span>  
  
- <span data-ttu-id="d6678-119">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="d6678-119">**Negative Numbers.**</span></span> <span data-ttu-id="d6678-120">`Boolean` sayısal bir tür değil ve negatif bir değeri temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="d6678-120">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="d6678-121">Herhangi bir durumda, `Boolean` sayısal değerleri tutmak için kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="d6678-121">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="d6678-122">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="d6678-122">**Type Characters.**</span></span> <span data-ttu-id="d6678-123">`Boolean` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="d6678-123">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="d6678-124">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="d6678-124">**Framework Type.**</span></span> <span data-ttu-id="d6678-125">.NET Framework karşılık gelen tür <xref:System.Boolean?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="d6678-125">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6678-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6678-126">Example</span></span>  

 <span data-ttu-id="d6678-127">Aşağıdaki örnekte, basit bir `runningVB` `Boolean` Evet/Hayır ayarı depolayan bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="d6678-127">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6678-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6678-128">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="d6678-129">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="d6678-129">Data Types</span></span>](index.md)
- [<span data-ttu-id="d6678-130">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d6678-130">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="d6678-131">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="d6678-131">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="d6678-132">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="d6678-132">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="d6678-133">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="d6678-133">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="d6678-134">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6678-134">CType Function</span></span>](../functions/ctype-function.md)
