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
ms.openlocfilehash: 1d11a6d009f6ecfea9fb1a86b00c67b87d5555dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955835"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="9cd95-102">Or İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cd95-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="9cd95-103">İki `Boolean` ifadeye mantıksal bir ayırıcı ya da iki sayısal ifadeye bit düzeyinde ayırıcı uygular.</span><span class="sxs-lookup"><span data-stu-id="9cd95-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cd95-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9cd95-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="9cd95-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9cd95-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="9cd95-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9cd95-106">Required.</span></span> <span data-ttu-id="9cd95-107">Herhangi `Boolean` bir veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9cd95-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="9cd95-108">Karşılaştırma için `Boolean` iki değerden`Boolean` oluşan kapsamlı mantıksal ayırıcı olur. `result`</span><span class="sxs-lookup"><span data-stu-id="9cd95-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="9cd95-109">Bit düzeyinde işlemler `result` için iki sayısal bit deseninin kapsamlı bit düzeyinde debirleşimin temsil eden sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="9cd95-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="9cd95-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9cd95-110">Required.</span></span> <span data-ttu-id="9cd95-111">Herhangi `Boolean` bir veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9cd95-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="9cd95-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9cd95-112">Required.</span></span> <span data-ttu-id="9cd95-113">Herhangi `Boolean` bir veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9cd95-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cd95-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9cd95-114">Remarks</span></span>  
 <span data-ttu-id="9cd95-115">`Boolean` `expression1` Karşılaştırma için`False`ve yalnızca her ikisi de olarak`False`değerlendirilir `expression2`. `result`</span><span class="sxs-lookup"><span data-stu-id="9cd95-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="9cd95-116">Aşağıdaki tabloda nasıl `result` belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9cd95-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="9cd95-117">`expression1` İse</span><span class="sxs-lookup"><span data-stu-id="9cd95-117">If `expression1` is</span></span>|<span data-ttu-id="9cd95-118">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="9cd95-118">And `expression2` is</span></span>|<span data-ttu-id="9cd95-119">Öğesinin `result` değeri</span><span class="sxs-lookup"><span data-stu-id="9cd95-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="9cd95-120">Bir `Boolean` karşılaştırmada`Or` , işleç her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9cd95-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="9cd95-121">[OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md) *kısa* `expression1` devre uygular, yani ise `True` `expression2` , hesaplanmaz.</span><span class="sxs-lookup"><span data-stu-id="9cd95-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="9cd95-122">Bit düzeyinde işlemler için, `Or` işleç iki sayısal ifadede aynı şekilde `result` konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve karşılık gelen biti aşağıdaki tabloya göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9cd95-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="9cd95-123">Eğer bit `expression1` ise</span><span class="sxs-lookup"><span data-stu-id="9cd95-123">If bit in `expression1` is</span></span>|<span data-ttu-id="9cd95-124">Ve bit `expression2` ,</span><span class="sxs-lookup"><span data-stu-id="9cd95-124">And bit in `expression2` is</span></span>|<span data-ttu-id="9cd95-125">İçindeki `result` bit</span><span class="sxs-lookup"><span data-stu-id="9cd95-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="9cd95-126">1\.</span><span class="sxs-lookup"><span data-stu-id="9cd95-126">1</span></span>|<span data-ttu-id="9cd95-127">1\.</span><span class="sxs-lookup"><span data-stu-id="9cd95-127">1</span></span>|<span data-ttu-id="9cd95-128">1\.</span><span class="sxs-lookup"><span data-stu-id="9cd95-128">1</span></span>|  
|<span data-ttu-id="9cd95-129">1</span><span class="sxs-lookup"><span data-stu-id="9cd95-129">1</span></span>|<span data-ttu-id="9cd95-130">0</span><span class="sxs-lookup"><span data-stu-id="9cd95-130">0</span></span>|<span data-ttu-id="9cd95-131">1\.</span><span class="sxs-lookup"><span data-stu-id="9cd95-131">1</span></span>|  
|<span data-ttu-id="9cd95-132">0</span><span class="sxs-lookup"><span data-stu-id="9cd95-132">0</span></span>|<span data-ttu-id="9cd95-133">1\.</span><span class="sxs-lookup"><span data-stu-id="9cd95-133">1</span></span>|<span data-ttu-id="9cd95-134">1</span><span class="sxs-lookup"><span data-stu-id="9cd95-134">1</span></span>|  
|<span data-ttu-id="9cd95-135">0</span><span class="sxs-lookup"><span data-stu-id="9cd95-135">0</span></span>|<span data-ttu-id="9cd95-136">0</span><span class="sxs-lookup"><span data-stu-id="9cd95-136">0</span></span>|<span data-ttu-id="9cd95-137">0</span><span class="sxs-lookup"><span data-stu-id="9cd95-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="9cd95-138">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9cd95-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="9cd95-139">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="9cd95-139">Data Types</span></span>  
 <span data-ttu-id="9cd95-140">İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadeyi sayısal bir `True` değere dönüştürür (– `False`1 ve için 0) ve bit düzeyinde bir işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9cd95-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="9cd95-141">Bir `Boolean` karşılaştırma için sonucun veri türü olur `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="9cd95-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="9cd95-142">Bit düzeyinde karşılaştırma için, sonuç veri türü `expression1` ve `expression2`veri türleri için uygun sayısal bir türdür.</span><span class="sxs-lookup"><span data-stu-id="9cd95-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="9cd95-143">[Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="9cd95-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9cd95-144">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="9cd95-144">Overloading</span></span>  
 <span data-ttu-id="9cd95-145">İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `Or`</span><span class="sxs-lookup"><span data-stu-id="9cd95-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9cd95-146">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9cd95-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9cd95-147">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9cd95-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cd95-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="9cd95-148">Example</span></span>  
 <span data-ttu-id="9cd95-149">Aşağıdaki örnek, iki ifadeye `Or` kapsamlı bir mantıksal ayırıcı gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9cd95-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="9cd95-150">Sonuç, iki `Boolean` `True`deyimden birinin olup olmadığını temsil eden bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="9cd95-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="9cd95-151">Yukarıdaki örnek sırasıyla `True`, `True`, ve `False`sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="9cd95-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cd95-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="9cd95-152">Example</span></span>  
 <span data-ttu-id="9cd95-153">Aşağıdaki örnek, iki sayısal `Or` ifadenin ayrı bitleri üzerinde kapsamlı mantıksal ayırıcı gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9cd95-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="9cd95-154">Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin biri 1 olarak ayarlandıysa ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9cd95-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="9cd95-155">Yukarıdaki örnek sırasıyla 10, 14 ve 14 sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="9cd95-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cd95-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cd95-156">See also</span></span>

- [<span data-ttu-id="9cd95-157">Mantıksal/bit düzeyinde Işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cd95-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="9cd95-158">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="9cd95-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9cd95-159">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="9cd95-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9cd95-160">OrElse İşleci</span><span class="sxs-lookup"><span data-stu-id="9cd95-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="9cd95-161">Visual Basic mantıksal ve bit düzeyinde Işleçler</span><span class="sxs-lookup"><span data-stu-id="9cd95-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
