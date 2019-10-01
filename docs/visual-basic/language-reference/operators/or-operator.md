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
ms.openlocfilehash: 03decb4ad32e8ff2c03e3b64a272bce779282973
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701234"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="8f959-102">Or İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f959-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="8f959-103">İki `Boolean` ifadelerinde mantıksal bir ayırma veya iki sayısal ifadeye bit tabanlı bir ayırıcı uygular.</span><span class="sxs-lookup"><span data-stu-id="8f959-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f959-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f959-104">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="8f959-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8f959-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="8f959-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8f959-106">Required.</span></span> <span data-ttu-id="8f959-107">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="8f959-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="8f959-108">@No__t-0 karşılaştırması için, `result` iki `Boolean` değerinin kapsamlı mantıksal bir birleşimdir.</span><span class="sxs-lookup"><span data-stu-id="8f959-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="8f959-109">Bit düzeyinde işlemler için `result`, iki sayısal bit desenlerinin kapsamlı bit düzeyinde bir ilişkisini temsil eden sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="8f959-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="8f959-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8f959-110">Required.</span></span> <span data-ttu-id="8f959-111">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="8f959-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="8f959-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8f959-112">Required.</span></span> <span data-ttu-id="8f959-113">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="8f959-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f959-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f959-114">Remarks</span></span>  
 <span data-ttu-id="8f959-115">@No__t 0 karşılaştırması için, `result` `False` ' dir ve yalnızca hem `expression1` hem de `expression2` `False` olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8f959-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="8f959-116">Aşağıdaki tabloda `result` ' ın nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f959-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="8f959-117">@No__t-0 ise</span><span class="sxs-lookup"><span data-stu-id="8f959-117">If `expression1` is</span></span>|<span data-ttu-id="8f959-118">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="8f959-118">And `expression2` is</span></span>|<span data-ttu-id="8f959-119">@No__t-0 değeri</span><span class="sxs-lookup"><span data-stu-id="8f959-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="8f959-120">@No__t-0 karşılaştırmasına `Or` işleci her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8f959-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="8f959-121">[OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md) *kısa*devre uygular, yani `expression1` `True` ise `expression2` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="8f959-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="8f959-122">Bit düzeyinde işlemler için `Or` işleci iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve `result` ' de karşılık gelen biti aşağıdaki tabloya göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f959-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="8f959-123">Bit `expression1` ise</span><span class="sxs-lookup"><span data-stu-id="8f959-123">If bit in `expression1` is</span></span>|<span data-ttu-id="8f959-124">Ve bit `expression2` ' dır</span><span class="sxs-lookup"><span data-stu-id="8f959-124">And bit in `expression2` is</span></span>|<span data-ttu-id="8f959-125">@No__t-0 ' daki bit</span><span class="sxs-lookup"><span data-stu-id="8f959-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="8f959-126">1\.</span><span class="sxs-lookup"><span data-stu-id="8f959-126">1</span></span>|<span data-ttu-id="8f959-127">1\.</span><span class="sxs-lookup"><span data-stu-id="8f959-127">1</span></span>|<span data-ttu-id="8f959-128">1\.</span><span class="sxs-lookup"><span data-stu-id="8f959-128">1</span></span>|  
|<span data-ttu-id="8f959-129">1\.</span><span class="sxs-lookup"><span data-stu-id="8f959-129">1</span></span>|<span data-ttu-id="8f959-130">0</span><span class="sxs-lookup"><span data-stu-id="8f959-130">0</span></span>|<span data-ttu-id="8f959-131">1\.</span><span class="sxs-lookup"><span data-stu-id="8f959-131">1</span></span>|  
|<span data-ttu-id="8f959-132">0</span><span class="sxs-lookup"><span data-stu-id="8f959-132">0</span></span>|<span data-ttu-id="8f959-133">1\.</span><span class="sxs-lookup"><span data-stu-id="8f959-133">1</span></span>|<span data-ttu-id="8f959-134">1\.</span><span class="sxs-lookup"><span data-stu-id="8f959-134">1</span></span>|  
|<span data-ttu-id="8f959-135">0</span><span class="sxs-lookup"><span data-stu-id="8f959-135">0</span></span>|<span data-ttu-id="8f959-136">0</span><span class="sxs-lookup"><span data-stu-id="8f959-136">0</span></span>|<span data-ttu-id="8f959-137">0</span><span class="sxs-lookup"><span data-stu-id="8f959-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="8f959-138">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f959-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="8f959-139">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="8f959-139">Data Types</span></span>  
 <span data-ttu-id="8f959-140">İşlenenler bir `Boolean` ifadesinde ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadesini sayısal bir değere dönüştürür (-1 `True` ve `False` için 0) ve bit düzeyinde bir işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8f959-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="8f959-141">@No__t 0 karşılaştırması için sonucun veri türü `Boolean` ' dir.</span><span class="sxs-lookup"><span data-stu-id="8f959-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="8f959-142">Bit düzeyinde karşılaştırma için sonuç veri türü, `expression1` ve `expression2` veri türleri için uygun sayısal bir türdür.</span><span class="sxs-lookup"><span data-stu-id="8f959-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="8f959-143">[Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="8f959-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8f959-144">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="8f959-144">Overloading</span></span>  
 <span data-ttu-id="8f959-145">@No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8f959-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8f959-146">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8f959-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8f959-147">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8f959-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f959-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f959-148">Example</span></span>  
 <span data-ttu-id="8f959-149">Aşağıdaki örnek, iki ifadeye kapsamlı bir mantıksal ayırıcı gerçekleştirmek için `Or` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f959-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="8f959-150">Sonuç, iki ifadeden birinin `True` olup olmadığını temsil eden bir `Boolean` değeridir.</span><span class="sxs-lookup"><span data-stu-id="8f959-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="8f959-151">Yukarıdaki örnek sırasıyla `True`, `True` ve `False` sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="8f959-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f959-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f959-152">Example</span></span>  
 <span data-ttu-id="8f959-153">Aşağıdaki örnek, iki sayısal ifadenin tek bir bit üzerinde kapsamlı mantıksal ayırıcı gerçekleştirmek için `Or` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f959-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="8f959-154">Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin biri 1 olarak ayarlandıysa ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8f959-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="8f959-155">Yukarıdaki örnek sırasıyla 10, 14 ve 14 sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="8f959-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f959-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f959-156">See also</span></span>

- [<span data-ttu-id="8f959-157">Mantıksal/bit düzeyinde Işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f959-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="8f959-158">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="8f959-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8f959-159">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="8f959-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8f959-160">OrElse İşleci</span><span class="sxs-lookup"><span data-stu-id="8f959-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="8f959-161">Visual Basic mantıksal ve bit düzeyinde Işleçler</span><span class="sxs-lookup"><span data-stu-id="8f959-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
