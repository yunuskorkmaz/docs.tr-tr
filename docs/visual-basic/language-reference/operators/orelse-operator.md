---
title: OrElse İşleci
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 361de44711c3b41411f2fa1dd81a3dd8db6b01e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348243"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="63b74-102">OrElse İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63b74-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="63b74-103">İki ifadeye kısa devre uygulayan kapsamlı mantıksal ayırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="63b74-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63b74-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63b74-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="63b74-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="63b74-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="63b74-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="63b74-106">Required.</span></span> <span data-ttu-id="63b74-107">Herhangi bir `Boolean` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="63b74-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="63b74-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="63b74-108">Required.</span></span> <span data-ttu-id="63b74-109">Herhangi bir `Boolean` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="63b74-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="63b74-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="63b74-110">Required.</span></span> <span data-ttu-id="63b74-111">Herhangi bir `Boolean` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="63b74-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63b74-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63b74-112">Remarks</span></span>  
 <span data-ttu-id="63b74-113">Derlenmiş kod, başka bir ifadenin sonucuna bağlı olarak bir ifadenin değerlendirmesini atlayabiliyorsa, mantıksal bir işlemin *kısa devre dışı* olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="63b74-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="63b74-114">Değerlendirilen ilk ifadenin sonucu işlemin nihai sonucunu belirlerse, nihai sonucu değiştiremediğinden ikinci ifadeyi değerlendirmeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="63b74-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="63b74-115">Atlanan ifade karmaşık olduğunda veya yordam çağrıları içeriyorsa, kısa devre dışı hale getirebilirsiniz performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="63b74-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="63b74-116">Ya da her iki ifade `True`olarak değerlendirilir `result` `True`.</span><span class="sxs-lookup"><span data-stu-id="63b74-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="63b74-117">Aşağıdaki tabloda `result` nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="63b74-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="63b74-118">`expression1`</span><span class="sxs-lookup"><span data-stu-id="63b74-118">If `expression1` is</span></span>|<span data-ttu-id="63b74-119">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="63b74-119">And `expression2` is</span></span>|<span data-ttu-id="63b74-120">`result` değeri</span><span class="sxs-lookup"><span data-stu-id="63b74-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="63b74-121">(değerlendirilmedi)</span><span class="sxs-lookup"><span data-stu-id="63b74-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="63b74-122">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="63b74-122">Data Types</span></span>  
 <span data-ttu-id="63b74-123">`OrElse` işleci yalnızca [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="63b74-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="63b74-124">Visual Basic, ifadeyi değerlendirmeden önce `Boolean` gereken her işleneni dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="63b74-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="63b74-125">Sonucu sayısal bir türe atarsanız, Visual Basic `Boolean` `False` `0` haline gelir ve `True` `-1`hale gelir.</span><span class="sxs-lookup"><span data-stu-id="63b74-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="63b74-126">Daha fazla bilgi için bkz. [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="63b74-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="63b74-127">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="63b74-127">Overloading</span></span>  
 <span data-ttu-id="63b74-128">[OR işleci](../../../visual-basic/language-reference/operators/or-operator.md) ve [IsTrue işleci](../../../visual-basic/language-reference/operators/istrue-operator.md) *aşırı*yüklenebilir, bu da bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="63b74-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="63b74-129">`Or` aşırı yükleme ve `IsTrue` işleçleri `OrElse` işlecinin davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="63b74-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="63b74-130">Kodunuz, `Or` ve `IsTrue`aşırı yükleyen bir sınıf veya yapı üzerinde `OrElse` kullanıyorsa, yeniden tanımlanmış davranışlarını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="63b74-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="63b74-131">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="63b74-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63b74-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="63b74-132">Example</span></span>  
 <span data-ttu-id="63b74-133">Aşağıdaki örnek, iki ifadeye mantıksal ayırıcı gerçekleştirmek için `OrElse` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="63b74-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="63b74-134">Sonuç, iki ifadeden birinin doğru olup olmadığını temsil eden bir `Boolean` değeridir.</span><span class="sxs-lookup"><span data-stu-id="63b74-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="63b74-135">İlk ifade `True`, ikincisi değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="63b74-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="63b74-136">Yukarıdaki örnek, sırasıyla `True`, `True`ve `False` sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="63b74-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="63b74-137">`firstCheck`hesaplamasında ikinci ifade değerlendirilmez çünkü ilki zaten `True`.</span><span class="sxs-lookup"><span data-stu-id="63b74-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="63b74-138">Ancak, ikinci ifade `secondCheck`hesaplamasında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="63b74-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63b74-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="63b74-139">Example</span></span>  
 <span data-ttu-id="63b74-140">Aşağıdaki örnek, iki yordam çağrısı içeren bir `If`...`Then` ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="63b74-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="63b74-141">İlk çağrı `True`döndürürse ikinci yordam çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="63b74-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="63b74-142">Bu, ikinci yordam kodun bu bölümü çalıştırıldığında her zaman gerçekleştirilmesi gereken önemli görevleri gerçekleştirdiğinde beklenmedik sonuçlar verebilir.</span><span class="sxs-lookup"><span data-stu-id="63b74-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="63b74-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63b74-143">See also</span></span>

- [<span data-ttu-id="63b74-144">Mantıksal/bit düzeyinde Işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63b74-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="63b74-145">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="63b74-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="63b74-146">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="63b74-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="63b74-147">Or İşleci</span><span class="sxs-lookup"><span data-stu-id="63b74-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="63b74-148">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="63b74-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="63b74-149">Visual Basic mantıksal ve bit düzeyinde Işleçler</span><span class="sxs-lookup"><span data-stu-id="63b74-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
