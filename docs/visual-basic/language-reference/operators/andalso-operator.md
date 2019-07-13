---
title: AndAlso İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 1cb4d372d3ac228f29c6fa45f124796e5dfb6709
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859894"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="9e626-102">AndAlso İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e626-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="9e626-103">Kısa devre mantıksal ve işlecini iki gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9e626-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e626-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e626-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="9e626-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9e626-105">Parts</span></span>  
  
|<span data-ttu-id="9e626-106">Terim</span><span class="sxs-lookup"><span data-stu-id="9e626-106">Term</span></span>|<span data-ttu-id="9e626-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="9e626-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="9e626-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9e626-108">Required.</span></span> <span data-ttu-id="9e626-109">Tüm `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="9e626-109">Any `Boolean` expression.</span></span> <span data-ttu-id="9e626-110">Sonuç `Boolean` karşılaştırma iki ifadenin sonucu.</span><span class="sxs-lookup"><span data-stu-id="9e626-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="9e626-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9e626-111">Required.</span></span> <span data-ttu-id="9e626-112">Tüm `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="9e626-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="9e626-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9e626-113">Required.</span></span> <span data-ttu-id="9e626-114">Tüm `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="9e626-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e626-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e626-115">Remarks</span></span>  
 <span data-ttu-id="9e626-116">Bir mantıksal işlemi olduğu söylenir *kısa devre* , derlenmiş kod başka bir ifadenin sonucu bağlı olarak tek bir ifade değerlendirmesi devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="9e626-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="9e626-117">Hesaplanan ilk ifadenin sonucu işlem son sonucunu belirlerse, ikinci ifade değerlendirilemiyor gerek yoktur nihai sonucu değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e626-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="9e626-118">Kısa devre Atlanan ifade karmaşıksa veya yordam çağrılarını içeriyorsa performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="9e626-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="9e626-119">Her iki ifade sonucunu verirse `True`, `result` olduğu `True`.</span><span class="sxs-lookup"><span data-stu-id="9e626-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="9e626-120">Aşağıdaki tabloda gösterilmiştir nasıl `result` belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9e626-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="9e626-121">Varsa `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="9e626-121">If `expression1` is</span></span>|<span data-ttu-id="9e626-122">Ve `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="9e626-122">And `expression2` is</span></span>|<span data-ttu-id="9e626-123">Değerini `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="9e626-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="9e626-124">(Değerlendirilmedi)</span><span class="sxs-lookup"><span data-stu-id="9e626-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="9e626-125">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="9e626-125">Data Types</span></span>  
 <span data-ttu-id="9e626-126">`AndAlso` İşleci yalnızca tanımlanmış [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="9e626-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="9e626-127">Visual Basic, her işlenen gerektiği şekilde dönüştürür `Boolean` ifade değerlendirmeden önce.</span><span class="sxs-lookup"><span data-stu-id="9e626-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="9e626-128">Sonucu bir sayısal tür için atarsanız, Visual Basic ondan dönüştürür `Boolean` o türe şekilde `False` olur `0` ve `True` olur `-1`.</span><span class="sxs-lookup"><span data-stu-id="9e626-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="9e626-129">Daha fazla bilgi için [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions)</span><span class="sxs-lookup"><span data-stu-id="9e626-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions)</span></span>
  
## <a name="overloading"></a><span data-ttu-id="9e626-130">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="9e626-130">Overloading</span></span>  
 <span data-ttu-id="9e626-131">[And işlecini](../../../visual-basic/language-reference/operators/and-operator.md) ve [IsFalse işleci](../../../visual-basic/language-reference/operators/isfalse-operator.md) olabilir *aşırı*, yani bir işlenen türü, söz konusu olduğunda bir sınıf veya yapı davranışlarını tanımlayabilirsiniz, sınıf veya yapı.</span><span class="sxs-lookup"><span data-stu-id="9e626-131">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9e626-132">Aşırı yükleme `And` ve `IsFalse` işleçleri davranışını etkileyen `AndAlso` işleci.</span><span class="sxs-lookup"><span data-stu-id="9e626-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="9e626-133">Kodunuzu kullanıyorsa `AndAlso` bir sınıf veya aşırı yapısı `And` ve `IsFalse`, yeniden tanımlanan davranışlarını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9e626-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="9e626-134">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9e626-134">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e626-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e626-135">Example</span></span>  
 <span data-ttu-id="9e626-136">Aşağıdaki örnekte `AndAlso` mantıksal ve işlecini iki ifadelerini gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="9e626-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="9e626-137">Sonuç bir `Boolean` tüm ifade conjoined olup olmadığını gösteren bir değer doğrudur.</span><span class="sxs-lookup"><span data-stu-id="9e626-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="9e626-138">İlk ifade yanlışsa `False`, ikinci değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="9e626-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="9e626-139">Yukarıdaki örnekte sonuçlarını üretir `True`, `False`, ve `False`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="9e626-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="9e626-140">Hesaplamasında `secondCheck`, ilk zaten olduğundan ikinci ifade değerlendirilmez `False`.</span><span class="sxs-lookup"><span data-stu-id="9e626-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="9e626-141">Ancak, ikinci ifade hesaplamasına değerlendirilir `thirdCheck`.</span><span class="sxs-lookup"><span data-stu-id="9e626-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e626-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e626-142">Example</span></span>  
 <span data-ttu-id="9e626-143">Aşağıdaki örnekte gösterildiği bir `Function` bir dizinin öğeleri arasında belirli bir değeri arar yordamı.</span><span class="sxs-lookup"><span data-stu-id="9e626-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="9e626-144">Boş diziyse ya da dizi uzunluğu aşıldı, `While` deyimi, dizi öğesini arama değeri karşı test değil.</span><span class="sxs-lookup"><span data-stu-id="9e626-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="9e626-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e626-145">See also</span></span>

- [<span data-ttu-id="9e626-146">Mantıksal/bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e626-146">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="9e626-147">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="9e626-147">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9e626-148">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="9e626-148">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9e626-149">And İşleci</span><span class="sxs-lookup"><span data-stu-id="9e626-149">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)
- [<span data-ttu-id="9e626-150">IsFalse İşleci</span><span class="sxs-lookup"><span data-stu-id="9e626-150">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="9e626-151">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="9e626-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
