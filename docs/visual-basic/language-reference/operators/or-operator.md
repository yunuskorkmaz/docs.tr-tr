---
title: Or İşleci
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
ms.openlocfilehash: 8f28026b526c29a6122725b2689e53b7f6ee7327
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348248"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="a94cb-102">Or İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a94cb-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="a94cb-103">İki `Boolean` ifadelerinde mantıksal bir ayırıcı ya da iki sayısal ifadeye bit düzeyinde ayırıcı uygular.</span><span class="sxs-lookup"><span data-stu-id="a94cb-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a94cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a94cb-104">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="a94cb-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a94cb-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="a94cb-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a94cb-106">Required.</span></span> <span data-ttu-id="a94cb-107">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="a94cb-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="a94cb-108">`Boolean` karşılaştırma için, `result` iki `Boolean` değerin kapsamlı mantıksal bir birleşimi olur.</span><span class="sxs-lookup"><span data-stu-id="a94cb-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="a94cb-109">Bit düzeyinde işlemler için `result`, iki sayısal bit desenlerinin kapsamlı bit düzeyinde debirleşimin temsil eden sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="a94cb-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="a94cb-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a94cb-110">Required.</span></span> <span data-ttu-id="a94cb-111">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="a94cb-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a94cb-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a94cb-112">Required.</span></span> <span data-ttu-id="a94cb-113">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="a94cb-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a94cb-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a94cb-114">Remarks</span></span>  
 <span data-ttu-id="a94cb-115">`Boolean` karşılaştırma için `result` `False` ve yalnızca hem `expression1` hem de `expression2` `False`olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a94cb-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="a94cb-116">Aşağıdaki tabloda `result` nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a94cb-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="a94cb-117">`expression1`</span><span class="sxs-lookup"><span data-stu-id="a94cb-117">If `expression1` is</span></span>|<span data-ttu-id="a94cb-118">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="a94cb-118">And `expression2` is</span></span>|<span data-ttu-id="a94cb-119">`result` değeri</span><span class="sxs-lookup"><span data-stu-id="a94cb-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="a94cb-120">`Boolean` bir karşılaştırmayla `Or` işleci her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a94cb-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="a94cb-121">[OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md) *kısa*devre uygular. Bu, `expression1` `True`, `expression2` değerlendirilmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a94cb-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="a94cb-122">Bit düzeyinde işlemler için `Or` işleci, iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve aşağıdaki tabloya göre `result` karşılık gelen biti ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a94cb-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="a94cb-123">`expression1` bit ise</span><span class="sxs-lookup"><span data-stu-id="a94cb-123">If bit in `expression1` is</span></span>|<span data-ttu-id="a94cb-124">Ve `expression2` bit</span><span class="sxs-lookup"><span data-stu-id="a94cb-124">And bit in `expression2` is</span></span>|<span data-ttu-id="a94cb-125">`result` bit</span><span class="sxs-lookup"><span data-stu-id="a94cb-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="a94cb-126">1</span><span class="sxs-lookup"><span data-stu-id="a94cb-126">1</span></span>|<span data-ttu-id="a94cb-127">1</span><span class="sxs-lookup"><span data-stu-id="a94cb-127">1</span></span>|<span data-ttu-id="a94cb-128">1</span><span class="sxs-lookup"><span data-stu-id="a94cb-128">1</span></span>|  
|<span data-ttu-id="a94cb-129">1</span><span class="sxs-lookup"><span data-stu-id="a94cb-129">1</span></span>|<span data-ttu-id="a94cb-130">0</span><span class="sxs-lookup"><span data-stu-id="a94cb-130">0</span></span>|<span data-ttu-id="a94cb-131">1</span><span class="sxs-lookup"><span data-stu-id="a94cb-131">1</span></span>|  
|<span data-ttu-id="a94cb-132">0</span><span class="sxs-lookup"><span data-stu-id="a94cb-132">0</span></span>|<span data-ttu-id="a94cb-133">1</span><span class="sxs-lookup"><span data-stu-id="a94cb-133">1</span></span>|<span data-ttu-id="a94cb-134">1</span><span class="sxs-lookup"><span data-stu-id="a94cb-134">1</span></span>|  
|<span data-ttu-id="a94cb-135">0</span><span class="sxs-lookup"><span data-stu-id="a94cb-135">0</span></span>|<span data-ttu-id="a94cb-136">0</span><span class="sxs-lookup"><span data-stu-id="a94cb-136">0</span></span>|<span data-ttu-id="a94cb-137">0</span><span class="sxs-lookup"><span data-stu-id="a94cb-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a94cb-138">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a94cb-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="a94cb-139">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="a94cb-139">Data Types</span></span>  
 <span data-ttu-id="a94cb-140">İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadesini sayısal bir değere dönüştürür (`True` için – 1 ve `False`için 0) ve bit düzeyinde bir işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a94cb-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="a94cb-141">`Boolean` karşılaştırma için sonucun veri türü `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a94cb-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="a94cb-142">Bit düzeyinde karşılaştırma için, sonuç veri türü `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür.</span><span class="sxs-lookup"><span data-stu-id="a94cb-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="a94cb-143">[Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="a94cb-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a94cb-144">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="a94cb-144">Overloading</span></span>  
 <span data-ttu-id="a94cb-145">`Or` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a94cb-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a94cb-146">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a94cb-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a94cb-147">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a94cb-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a94cb-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="a94cb-148">Example</span></span>  
 <span data-ttu-id="a94cb-149">Aşağıdaki örnek iki ifadeye kapsamlı bir mantıksal ayırıcı gerçekleştirmek için `Or` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a94cb-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="a94cb-150">Sonuç, iki deyimden birinin `True`olup olmadığını temsil eden bir `Boolean` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a94cb-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="a94cb-151">Yukarıdaki örnek, sırasıyla `True`, `True`ve `False`sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="a94cb-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a94cb-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="a94cb-152">Example</span></span>  
 <span data-ttu-id="a94cb-153">Aşağıdaki örnek, iki sayısal ifadenin tek bir bit biti üzerinde kapsamlı mantıksal ayırıcı gerçekleştirmek için `Or` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a94cb-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="a94cb-154">Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin biri 1 olarak ayarlandıysa ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a94cb-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="a94cb-155">Yukarıdaki örnek sırasıyla 10, 14 ve 14 sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="a94cb-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a94cb-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a94cb-156">See also</span></span>

- [<span data-ttu-id="a94cb-157">Mantıksal/bit düzeyinde Işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a94cb-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="a94cb-158">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="a94cb-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="a94cb-159">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="a94cb-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="a94cb-160">OrElse İşleci</span><span class="sxs-lookup"><span data-stu-id="a94cb-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="a94cb-161">Visual Basic mantıksal ve bit düzeyinde Işleçler</span><span class="sxs-lookup"><span data-stu-id="a94cb-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
