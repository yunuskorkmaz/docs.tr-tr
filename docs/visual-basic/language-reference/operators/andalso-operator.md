---
title: AndAlso Işleci (Visual Basic)
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
ms.openlocfilehash: a52f598c8a7c7a79b0f2436f1add7b3eb5d5261b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835222"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="0895a-102">AndAlso Işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0895a-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="0895a-103">İki ifadeye kısa devre mantıksal birlikte uygular.</span><span class="sxs-lookup"><span data-stu-id="0895a-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0895a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0895a-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="0895a-105">Parçaya</span><span class="sxs-lookup"><span data-stu-id="0895a-105">Parts</span></span>  
  
|<span data-ttu-id="0895a-106">Sözleşme Dönemi</span><span class="sxs-lookup"><span data-stu-id="0895a-106">Term</span></span>|<span data-ttu-id="0895a-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="0895a-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="0895a-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0895a-108">Required.</span></span> <span data-ttu-id="0895a-109">Herhangi bir `Boolean` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="0895a-109">Any `Boolean` expression.</span></span> <span data-ttu-id="0895a-110">Sonuç, iki ifadenin karşılaştırmasının `Boolean` sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="0895a-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="0895a-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0895a-111">Required.</span></span> <span data-ttu-id="0895a-112">Herhangi bir `Boolean` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="0895a-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="0895a-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0895a-113">Required.</span></span> <span data-ttu-id="0895a-114">Herhangi bir `Boolean` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="0895a-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0895a-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0895a-115">Remarks</span></span>  
 <span data-ttu-id="0895a-116">Derlenmiş kod, başka bir ifadenin sonucuna bağlı olarak bir ifadenin değerlendirmesini atlayabiliyorsa, mantıksal bir işlemin *kısa devre dışı* olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="0895a-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="0895a-117">Değerlendirilen ilk ifadenin sonucu işlemin nihai sonucunu belirlerse, nihai sonucu değiştiremediğinden ikinci ifadeyi değerlendirmeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="0895a-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="0895a-118">Atlanan ifade karmaşık olduğunda veya yordam çağrıları içeriyorsa, kısa devre dışı hale getirebilirsiniz performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="0895a-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="0895a-119">Her iki ifade `True` ' ı değerlendirirken, `result` `True` ' dir.</span><span class="sxs-lookup"><span data-stu-id="0895a-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="0895a-120">Aşağıdaki tabloda `result` ' ın nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0895a-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="0895a-121">@No__t-0 ise</span><span class="sxs-lookup"><span data-stu-id="0895a-121">If `expression1` is</span></span>|<span data-ttu-id="0895a-122">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="0895a-122">And `expression2` is</span></span>|<span data-ttu-id="0895a-123">@No__t-0 değeri</span><span class="sxs-lookup"><span data-stu-id="0895a-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="0895a-124">(değerlendirilmedi)</span><span class="sxs-lookup"><span data-stu-id="0895a-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="0895a-125">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="0895a-125">Data Types</span></span>  
 <span data-ttu-id="0895a-126">@No__t-0 işleci yalnızca [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0895a-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="0895a-127">Visual Basic, ifadeyi değerlendirmeden önce her işleneni gerektiği gibi `Boolean` ' a dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0895a-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="0895a-128">Sonucu sayısal bir türe atarsanız, Visual Basic `Boolean` ' dan bu türe dönüştürür `False` `0` olur ve `True` `-1` olur.</span><span class="sxs-lookup"><span data-stu-id="0895a-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="0895a-129">Daha fazla bilgi için bkz. [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="0895a-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="0895a-130">Aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="0895a-130">Overloading</span></span>  
 <span data-ttu-id="0895a-131">[And işleci](../../../visual-basic/language-reference/operators/and-operator.md) ve [IsFalse işleci](../../../visual-basic/language-reference/operators/isfalse-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0895a-131">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0895a-132">@No__t aşırı yükleme-0 ve `IsFalse` işleçleri `AndAlso` işlecinin davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="0895a-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="0895a-133">Kodunuz, `And` ve `IsFalse` ' yi aşırı yükleyen bir sınıf veya yapı üzerinde `AndAlso` kullanıyorsa, yeniden tanımlanmış davranışlarını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0895a-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="0895a-134">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0895a-134">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0895a-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="0895a-135">Example</span></span>  
 <span data-ttu-id="0895a-136">Aşağıdaki örnek, iki ifadeye mantıksal bir birlikte gerçekleştirmek için `AndAlso` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0895a-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="0895a-137">Sonuç, tüm konkatılmış ifadenin doğru olup olmadığını temsil eden bir `Boolean` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0895a-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="0895a-138">İlk ifade `False` ise, ikincisi değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="0895a-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="0895a-139">Yukarıdaki örnek sırasıyla `True`, `False` ve `False` sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="0895a-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="0895a-140">@No__t-0 hesaplamasında ikinci ifade değerlendirilmez çünkü ilki zaten `False` ' dir.</span><span class="sxs-lookup"><span data-stu-id="0895a-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="0895a-141">Ancak, ikinci ifade `thirdCheck` hesaplamasında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0895a-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0895a-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="0895a-142">Example</span></span>  
 <span data-ttu-id="0895a-143">Aşağıdaki örnek, bir dizinin öğeleri arasında belirli bir değeri arayan `Function` yordamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0895a-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="0895a-144">Dizi boşsa veya dizi uzunluğu aşılmışsa, `While` açıklaması dizi öğesini arama değerine karşı test etmez.</span><span class="sxs-lookup"><span data-stu-id="0895a-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="0895a-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0895a-145">See also</span></span>

- [<span data-ttu-id="0895a-146">Mantıksal/bit düzeyinde Işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0895a-146">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="0895a-147">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="0895a-147">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0895a-148">IŞLEVLERE göre listelenen işleçler</span><span class="sxs-lookup"><span data-stu-id="0895a-148">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0895a-149">And Işleci</span><span class="sxs-lookup"><span data-stu-id="0895a-149">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)
- [<span data-ttu-id="0895a-150">IsFalse Işleci</span><span class="sxs-lookup"><span data-stu-id="0895a-150">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="0895a-151">Visual Basic mantıksal ve bit düzeyinde Işleçler</span><span class="sxs-lookup"><span data-stu-id="0895a-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
