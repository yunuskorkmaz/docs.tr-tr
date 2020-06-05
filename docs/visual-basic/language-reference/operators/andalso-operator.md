---
title: AndAlso İşleci
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
ms.openlocfilehash: 8b67897956a21d06d465cf206856354d2e3f9d68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371940"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="7ad1f-102">AndAlso İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ad1f-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="7ad1f-103">İki ifadeye kısa devre mantıksal birlikte uygular.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ad1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ad1f-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="7ad1f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7ad1f-105">Parts</span></span>  
  
|<span data-ttu-id="7ad1f-106">Terim</span><span class="sxs-lookup"><span data-stu-id="7ad1f-106">Term</span></span>|<span data-ttu-id="7ad1f-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="7ad1f-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="7ad1f-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-108">Required.</span></span> <span data-ttu-id="7ad1f-109">Herhangi bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-109">Any `Boolean` expression.</span></span> <span data-ttu-id="7ad1f-110">Sonuç, `Boolean` iki ifadenin karşılaştırmasının sonucudur.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="7ad1f-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-111">Required.</span></span> <span data-ttu-id="7ad1f-112">Herhangi bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="7ad1f-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-113">Required.</span></span> <span data-ttu-id="7ad1f-114">Herhangi bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ad1f-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ad1f-115">Remarks</span></span>  
 <span data-ttu-id="7ad1f-116">Derlenmiş kod, başka bir ifadenin sonucuna bağlı olarak bir ifadenin değerlendirmesini atlayabiliyorsa, mantıksal bir işlemin *kısa devre dışı* olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="7ad1f-117">Değerlendirilen ilk ifadenin sonucu işlemin nihai sonucunu belirlerse, nihai sonucu değiştiremediğinden ikinci ifadeyi değerlendirmeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="7ad1f-118">Atlanan ifade karmaşık olduğunda veya yordam çağrıları içeriyorsa, kısa devre dışı hale getirebilirsiniz performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="7ad1f-119">Her iki ifade ise olarak `True` değerlendirilir `result` `True` .</span><span class="sxs-lookup"><span data-stu-id="7ad1f-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="7ad1f-120">Aşağıdaki tabloda nasıl belirlendiği gösterilmektedir `result` .</span><span class="sxs-lookup"><span data-stu-id="7ad1f-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="7ad1f-121">İse `expression1`</span><span class="sxs-lookup"><span data-stu-id="7ad1f-121">If `expression1` is</span></span>|<span data-ttu-id="7ad1f-122">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="7ad1f-122">And `expression2` is</span></span>|<span data-ttu-id="7ad1f-123">`result`Öğesinin değeri</span><span class="sxs-lookup"><span data-stu-id="7ad1f-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="7ad1f-124">(değerlendirilmedi)</span><span class="sxs-lookup"><span data-stu-id="7ad1f-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="7ad1f-125">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="7ad1f-125">Data Types</span></span>  
 <span data-ttu-id="7ad1f-126">`AndAlso`İşleci yalnızca [Boole veri türü](../data-types/boolean-data-type.md)için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="7ad1f-127">Visual Basic `Boolean` , ifadeyi değerlendirmeden önce her işleneni gerektiği şekilde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="7ad1f-128">Sonucu sayısal bir türe atarsanız, Visual Basic, ve haline gelen bu türe dönüştürür `Boolean` `False` `0` `True` `-1` .</span><span class="sxs-lookup"><span data-stu-id="7ad1f-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="7ad1f-129">Daha fazla bilgi için bkz. [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="7ad1f-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="7ad1f-130">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="7ad1f-130">Overloading</span></span>  
 <span data-ttu-id="7ad1f-131">[And işleci](and-operator.md) ve [IsFalse işleci](isfalse-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-131">The [And Operator](and-operator.md) and the [IsFalse Operator](isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7ad1f-132">`And`Ve işleçlerini aşırı yüklemek `IsFalse` işlecin davranışını etkiler `AndAlso` .</span><span class="sxs-lookup"><span data-stu-id="7ad1f-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="7ad1f-133">Kodunuz `AndAlso` , ve ' yi aşırı yükleyen bir sınıf veya yapı üzerinde kullanıyorsa `And` `IsFalse` , yeniden tanımlanmış davranışlarını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="7ad1f-134">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7ad1f-134">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ad1f-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ad1f-135">Example</span></span>  
 <span data-ttu-id="7ad1f-136">Aşağıdaki örnek, `AndAlso` iki ifadeye mantıksal bir birlikte gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="7ad1f-137">Sonuç, `Boolean` Tüm konkatılmış ifadenin doğru olup olmadığını temsil eden bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="7ad1f-138">İlk ifade ise, `False` ikincisi değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="7ad1f-139">Yukarıdaki örnek `True` sırasıyla,, ve sonuçlarını üretir `False` `False` .</span><span class="sxs-lookup"><span data-stu-id="7ad1f-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="7ad1f-140">Hesaplamasında `secondCheck` ikinci ifade değerlendirilmez çünkü ilki zaten var `False` .</span><span class="sxs-lookup"><span data-stu-id="7ad1f-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="7ad1f-141">Ancak, ikinci ifade hesaplamasında değerlendirilir `thirdCheck` .</span><span class="sxs-lookup"><span data-stu-id="7ad1f-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ad1f-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ad1f-142">Example</span></span>  
 <span data-ttu-id="7ad1f-143">Aşağıdaki örnek, bir `Function` dizinin öğeleri arasında belirli bir değeri arayan bir yordamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="7ad1f-144">Dizi boşsa veya dizi uzunluğu aşılmışsa, `While` ifade dizi öğesini arama değerine karşı test etmez.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="7ad1f-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ad1f-145">See also</span></span>

- [<span data-ttu-id="7ad1f-146">Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ad1f-146">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="7ad1f-147">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="7ad1f-147">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="7ad1f-148">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="7ad1f-148">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="7ad1f-149">And İşleci</span><span class="sxs-lookup"><span data-stu-id="7ad1f-149">And Operator</span></span>](and-operator.md)
- [<span data-ttu-id="7ad1f-150">IsFalse İşleci</span><span class="sxs-lookup"><span data-stu-id="7ad1f-150">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="7ad1f-151">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="7ad1f-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
