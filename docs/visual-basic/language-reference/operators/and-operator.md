---
title: And İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: 78a65843a449bd15d5615710e1685f40d94c37f7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350249"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="52c81-102">And İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52c81-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="52c81-103">İki `Boolean` ifadeye veya iki sayısal ifadeye bit düzeyinde bir birlikte mantıksal bir birlikte gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="52c81-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52c81-104">Syntax</span></span>  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="52c81-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="52c81-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="52c81-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="52c81-106">Required.</span></span> <span data-ttu-id="52c81-107">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="52c81-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="52c81-108">Boolean karşılaştırma için, iki `Boolean` değerinin mantıksal bir `result`.</span><span class="sxs-lookup"><span data-stu-id="52c81-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="52c81-109">Bit düzeyinde işlemler için `result`, iki sayısal bit deseninin bit düzeyinde birlikte temsil eden sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="52c81-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="52c81-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="52c81-110">Required.</span></span> <span data-ttu-id="52c81-111">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="52c81-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="52c81-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="52c81-112">Required.</span></span> <span data-ttu-id="52c81-113">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="52c81-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52c81-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52c81-114">Remarks</span></span>  
 <span data-ttu-id="52c81-115">Boolean karşılaştırma için, yalnızca hem `expression1` hem de `expression2` `True`olarak değerlendirip `result` `True`.</span><span class="sxs-lookup"><span data-stu-id="52c81-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="52c81-116">Aşağıdaki tabloda `result` nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="52c81-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="52c81-117">`expression1`</span><span class="sxs-lookup"><span data-stu-id="52c81-117">If `expression1` is</span></span>|<span data-ttu-id="52c81-118">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="52c81-118">And `expression2` is</span></span>|<span data-ttu-id="52c81-119">`result` değeri</span><span class="sxs-lookup"><span data-stu-id="52c81-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="52c81-120">Boole karşılaştırmasına `And` işleci her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="52c81-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="52c81-121">[AndAlso işleci de](../../../visual-basic/language-reference/operators/andalso-operator.md) *kısa*devre uygular, yani `expression1` `False`, `expression2` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="52c81-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="52c81-122">Sayısal değerlere uygulandığında `And` işleci iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve aşağıdaki tabloya göre `result` karşılık gelen biti ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52c81-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="52c81-123">`expression1` bit ise</span><span class="sxs-lookup"><span data-stu-id="52c81-123">If bit in `expression1` is</span></span>|<span data-ttu-id="52c81-124">Ve `expression2` bit</span><span class="sxs-lookup"><span data-stu-id="52c81-124">And bit in `expression2` is</span></span>|<span data-ttu-id="52c81-125">`result` bit</span><span class="sxs-lookup"><span data-stu-id="52c81-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="52c81-126">1</span><span class="sxs-lookup"><span data-stu-id="52c81-126">1</span></span>|<span data-ttu-id="52c81-127">1</span><span class="sxs-lookup"><span data-stu-id="52c81-127">1</span></span>|<span data-ttu-id="52c81-128">1</span><span class="sxs-lookup"><span data-stu-id="52c81-128">1</span></span>|  
|<span data-ttu-id="52c81-129">1</span><span class="sxs-lookup"><span data-stu-id="52c81-129">1</span></span>|<span data-ttu-id="52c81-130">0</span><span class="sxs-lookup"><span data-stu-id="52c81-130">0</span></span>|<span data-ttu-id="52c81-131">0</span><span class="sxs-lookup"><span data-stu-id="52c81-131">0</span></span>|  
|<span data-ttu-id="52c81-132">0</span><span class="sxs-lookup"><span data-stu-id="52c81-132">0</span></span>|<span data-ttu-id="52c81-133">1</span><span class="sxs-lookup"><span data-stu-id="52c81-133">1</span></span>|<span data-ttu-id="52c81-134">0</span><span class="sxs-lookup"><span data-stu-id="52c81-134">0</span></span>|  
|<span data-ttu-id="52c81-135">0</span><span class="sxs-lookup"><span data-stu-id="52c81-135">0</span></span>|<span data-ttu-id="52c81-136">0</span><span class="sxs-lookup"><span data-stu-id="52c81-136">0</span></span>|<span data-ttu-id="52c81-137">0</span><span class="sxs-lookup"><span data-stu-id="52c81-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="52c81-138">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru sonuçları sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="52c81-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="52c81-139">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="52c81-139">Data Types</span></span>  
 <span data-ttu-id="52c81-140">İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadesini sayısal bir değere dönüştürür (`True` için – 1 ve `False`için 0) ve bit düzeyinde bir işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="52c81-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="52c81-141">Boolean karşılaştırma için sonucun veri türü `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="52c81-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="52c81-142">Bit düzeyinde karşılaştırma için, sonuç veri türü `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür.</span><span class="sxs-lookup"><span data-stu-id="52c81-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="52c81-143">[Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="52c81-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52c81-144">`And` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="52c81-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="52c81-145">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="52c81-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="52c81-146">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="52c81-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52c81-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="52c81-147">Example</span></span>  
 <span data-ttu-id="52c81-148">Aşağıdaki örnek, iki ifadeye mantıksal bir birlikte gerçekleştirmek için `And` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="52c81-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="52c81-149">Sonuç, her iki ifadenin `True`olup olmadığını temsil eden bir `Boolean` değeridir.</span><span class="sxs-lookup"><span data-stu-id="52c81-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="52c81-150">Yukarıdaki örnek, sırasıyla `True` ve `False`sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="52c81-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52c81-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="52c81-151">Example</span></span>  
 <span data-ttu-id="52c81-152">Aşağıdaki örnek, iki sayısal ifadenin ayrı bitleri üzerinde mantıksal bir işlem gerçekleştirmek için `And` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="52c81-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="52c81-153">Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin her ikisi de 1 olarak ayarlandıysa ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="52c81-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="52c81-154">Yukarıdaki örnek sırasıyla 8, 2 ve 0 sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="52c81-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c81-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52c81-155">See also</span></span>

- [<span data-ttu-id="52c81-156">Mantıksal/bit düzeyinde Işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52c81-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="52c81-157">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="52c81-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="52c81-158">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="52c81-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="52c81-159">AndAlso İşleci</span><span class="sxs-lookup"><span data-stu-id="52c81-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="52c81-160">Visual Basic mantıksal ve bit düzeyinde Işleçler</span><span class="sxs-lookup"><span data-stu-id="52c81-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
