---
title: Or İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 9e02f619a81ee3c15321dfd44963c1a7d29843ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604776"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="742ee-102">Or İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="742ee-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="742ee-103">Mantıksal ayrım iki gerçekleştirir `Boolean` ifadeler veya iki sayısal ifadeye bit tabanlı bir ayrım.</span><span class="sxs-lookup"><span data-stu-id="742ee-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="742ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="742ee-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="742ee-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="742ee-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="742ee-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="742ee-106">Required.</span></span> <span data-ttu-id="742ee-107">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="742ee-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="742ee-108">İçin `Boolean` karşılaştırma, `result` iki dahil mantıksal ayrım olduğu `Boolean` değerleri.</span><span class="sxs-lookup"><span data-stu-id="742ee-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="742ee-109">Bit düzeyinde işlemler için `result` iki sayısal bit desenleri dahil Bitsel ayrım temsil eden bir sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="742ee-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="742ee-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="742ee-110">Required.</span></span> <span data-ttu-id="742ee-111">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="742ee-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="742ee-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="742ee-112">Required.</span></span> <span data-ttu-id="742ee-113">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="742ee-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="742ee-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="742ee-114">Remarks</span></span>  
 <span data-ttu-id="742ee-115">İçin `Boolean` karşılaştırma, `result` olan `False` varsa ve yalnızca her iki `expression1` ve `expression2` için değerlendirin `False`.</span><span class="sxs-lookup"><span data-stu-id="742ee-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="742ee-116">Aşağıdaki tabloda gösterilmektedir nasıl `result` belirlenir.</span><span class="sxs-lookup"><span data-stu-id="742ee-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="742ee-117">Varsa `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="742ee-117">If `expression1` is</span></span>|<span data-ttu-id="742ee-118">Ve `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="742ee-118">And `expression2` is</span></span>|<span data-ttu-id="742ee-119">Değeri `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="742ee-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="742ee-120">İçinde bir `Boolean` karşılaştırma, `Or` işleci her zaman yordam çağrıları yapma dahil olabilir hem ifadeleri değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="742ee-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="742ee-121">[OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md) gerçekleştirir *kısa devre*, başka bir deyişle, olması durumunda `expression1` olan `True`, ardından `expression2` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="742ee-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="742ee-122">Bit düzeyinde işlemler için `Or` işleci içinde iki sayısal ifadeye bit tabanlı karşılaştırma aynı konumlandırılmış bit gerçekleştirir ve buna karşılık gelen içinde bit ayarlar `result` aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="742ee-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="742ee-123">Varsa, bit `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="742ee-123">If bit in `expression1` is</span></span>|<span data-ttu-id="742ee-124">Ve içinde bit `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="742ee-124">And bit in `expression2` is</span></span>|<span data-ttu-id="742ee-125">Bit `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="742ee-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="742ee-126">1.</span><span class="sxs-lookup"><span data-stu-id="742ee-126">1</span></span>|<span data-ttu-id="742ee-127">1.</span><span class="sxs-lookup"><span data-stu-id="742ee-127">1</span></span>|<span data-ttu-id="742ee-128">1.</span><span class="sxs-lookup"><span data-stu-id="742ee-128">1</span></span>|  
|<span data-ttu-id="742ee-129">1.</span><span class="sxs-lookup"><span data-stu-id="742ee-129">1</span></span>|<span data-ttu-id="742ee-130">0</span><span class="sxs-lookup"><span data-stu-id="742ee-130">0</span></span>|<span data-ttu-id="742ee-131">1.</span><span class="sxs-lookup"><span data-stu-id="742ee-131">1</span></span>|  
|<span data-ttu-id="742ee-132">0</span><span class="sxs-lookup"><span data-stu-id="742ee-132">0</span></span>|<span data-ttu-id="742ee-133">1.</span><span class="sxs-lookup"><span data-stu-id="742ee-133">1</span></span>|<span data-ttu-id="742ee-134">1.</span><span class="sxs-lookup"><span data-stu-id="742ee-134">1</span></span>|  
|<span data-ttu-id="742ee-135">0</span><span class="sxs-lookup"><span data-stu-id="742ee-135">0</span></span>|<span data-ttu-id="742ee-136">0</span><span class="sxs-lookup"><span data-stu-id="742ee-136">0</span></span>|<span data-ttu-id="742ee-137">0</span><span class="sxs-lookup"><span data-stu-id="742ee-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="742ee-138">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçleri düşük önceliğe sahip olduğundan, tüm bit düzeyinde işlemler doğru yürütme emin olmak için parantez içine alınmış.</span><span class="sxs-lookup"><span data-stu-id="742ee-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="742ee-139">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="742ee-139">Data Types</span></span>  
 <span data-ttu-id="742ee-140">İşlenen birini oluşması durumunda `Boolean` ifadesi ve tek bir sayısal ifade, Visual Basic dönüştürür `Boolean` ifade sayısal bir değere (– 1 için `True` ve 0 `False`) ve bit tabanlı işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="742ee-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="742ee-141">İçin bir `Boolean` karşılaştırma, sonuç veri türünde `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="742ee-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="742ee-142">Bit tabanlı karşılaştırma için sonuç veri türü veri türleri için uygun sayısal bir tür değil. `expression1` ve `expression2`.</span><span class="sxs-lookup"><span data-stu-id="742ee-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="742ee-143">"İlişkisel ve Bitsel karşılaştırmaları" tablosunda görmek [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="742ee-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="742ee-144">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="742ee-144">Overloading</span></span>  
 <span data-ttu-id="742ee-145">`Or` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="742ee-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="742ee-146">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="742ee-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="742ee-147">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="742ee-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="742ee-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="742ee-148">Example</span></span>  
 <span data-ttu-id="742ee-149">Aşağıdaki örnek kullanır `Or` iki ifadeleri (bunlar dahil) bir mantıksal ayrım gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="742ee-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="742ee-150">Sonuç bir `Boolean` gösteren bir değer ya da iki ifadeye olup olmadığını `True`.</span><span class="sxs-lookup"><span data-stu-id="742ee-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]  
  
 <span data-ttu-id="742ee-151">Önceki örnekte sonuçlarını üreten `True`, `True`, ve `False`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="742ee-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="742ee-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="742ee-152">Example</span></span>  
 <span data-ttu-id="742ee-153">Aşağıdaki örnek kullanır `Or` iki sayısal ifadeye tek tek bitleri dahil mantıksal ayrım gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="742ee-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="742ee-154">İşlenen karşılık gelen bitleri ya da ayarlanmış 1 sonuç düzeninde bit ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="742ee-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]  
  
 <span data-ttu-id="742ee-155">Önceki örnekte, 10, 14 ve 14, sonuçları sırasıyla üretir.</span><span class="sxs-lookup"><span data-stu-id="742ee-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="742ee-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="742ee-156">See Also</span></span>  
 [<span data-ttu-id="742ee-157">Mantıksal ve bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="742ee-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="742ee-158">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="742ee-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="742ee-159">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="742ee-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="742ee-160">OrElse İşleci</span><span class="sxs-lookup"><span data-stu-id="742ee-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)  
 [<span data-ttu-id="742ee-161">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="742ee-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
