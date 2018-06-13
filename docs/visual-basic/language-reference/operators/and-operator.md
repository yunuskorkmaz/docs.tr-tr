---
title: And İşleci (Visual Basic)
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
ms.openlocfilehash: e14dfd8ba200598084cad04d1faa05f3561f8dab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604652"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="21a4c-102">And İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21a4c-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="21a4c-103">Mantıksal ve işlecini iki gerçekleştirir `Boolean` ifadeler veya iki sayısal ifadeye bit tabanlı birlikte.</span><span class="sxs-lookup"><span data-stu-id="21a4c-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21a4c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21a4c-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="21a4c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="21a4c-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="21a4c-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="21a4c-106">Required.</span></span> <span data-ttu-id="21a4c-107">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="21a4c-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="21a4c-108">Boole karşılaştırma için `result` mantıksal ve işlecini iki olduğu `Boolean` değerleri.</span><span class="sxs-lookup"><span data-stu-id="21a4c-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="21a4c-109">Bit düzeyinde işlemler için `result` iki sayısal bit desenleri Bitsel birlikte temsil eden bir sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="21a4c-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="21a4c-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="21a4c-110">Required.</span></span> <span data-ttu-id="21a4c-111">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="21a4c-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="21a4c-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="21a4c-112">Required.</span></span> <span data-ttu-id="21a4c-113">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="21a4c-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21a4c-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21a4c-114">Remarks</span></span>  
 <span data-ttu-id="21a4c-115">Boole karşılaştırma için `result` olan `True` varsa ve yalnızca her iki `expression1` ve `expression2` için değerlendirin `True`.</span><span class="sxs-lookup"><span data-stu-id="21a4c-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="21a4c-116">Aşağıdaki tabloda gösterilmektedir nasıl `result` belirlenir.</span><span class="sxs-lookup"><span data-stu-id="21a4c-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="21a4c-117">Varsa `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="21a4c-117">If `expression1` is</span></span>|<span data-ttu-id="21a4c-118">Ve `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="21a4c-118">And `expression2` is</span></span>|<span data-ttu-id="21a4c-119">Değeri `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="21a4c-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="21a4c-120">Boole karşılaştırmaya `And` işleci her zaman yordam çağrıları yapma dahil olabilir hem ifadeleri değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="21a4c-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="21a4c-121">[AndAlso işleci](../../../visual-basic/language-reference/operators/andalso-operator.md) gerçekleştirir *kısa devre*, başka bir deyişle, olması durumunda `expression1` olan `False`, ardından `expression2` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="21a4c-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="21a4c-122">Sayısal değerler için uygulandığında `And` işleci içinde iki sayısal ifadeye bit tabanlı karşılaştırma aynı konumlandırılmış bit gerçekleştirir ve buna karşılık gelen içinde bit ayarlar `result` aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="21a4c-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="21a4c-123">Varsa, bit `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="21a4c-123">If bit in `expression1` is</span></span>|<span data-ttu-id="21a4c-124">Ve içinde bit `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="21a4c-124">And bit in `expression2` is</span></span>|<span data-ttu-id="21a4c-125">Bit `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="21a4c-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="21a4c-126">1.</span><span class="sxs-lookup"><span data-stu-id="21a4c-126">1</span></span>|<span data-ttu-id="21a4c-127">1.</span><span class="sxs-lookup"><span data-stu-id="21a4c-127">1</span></span>|<span data-ttu-id="21a4c-128">1.</span><span class="sxs-lookup"><span data-stu-id="21a4c-128">1</span></span>|  
|<span data-ttu-id="21a4c-129">1.</span><span class="sxs-lookup"><span data-stu-id="21a4c-129">1</span></span>|<span data-ttu-id="21a4c-130">0</span><span class="sxs-lookup"><span data-stu-id="21a4c-130">0</span></span>|<span data-ttu-id="21a4c-131">0</span><span class="sxs-lookup"><span data-stu-id="21a4c-131">0</span></span>|  
|<span data-ttu-id="21a4c-132">0</span><span class="sxs-lookup"><span data-stu-id="21a4c-132">0</span></span>|<span data-ttu-id="21a4c-133">1.</span><span class="sxs-lookup"><span data-stu-id="21a4c-133">1</span></span>|<span data-ttu-id="21a4c-134">0</span><span class="sxs-lookup"><span data-stu-id="21a4c-134">0</span></span>|  
|<span data-ttu-id="21a4c-135">0</span><span class="sxs-lookup"><span data-stu-id="21a4c-135">0</span></span>|<span data-ttu-id="21a4c-136">0</span><span class="sxs-lookup"><span data-stu-id="21a4c-136">0</span></span>|<span data-ttu-id="21a4c-137">0</span><span class="sxs-lookup"><span data-stu-id="21a4c-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="21a4c-138">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçleri düşük önceliğe sahip olduğundan, tüm bit düzeyinde işlemler doğru sonuçlar sağlamak için parantez içine alınmış.</span><span class="sxs-lookup"><span data-stu-id="21a4c-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="21a4c-139">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="21a4c-139">Data Types</span></span>  
 <span data-ttu-id="21a4c-140">İşlenen birini oluşması durumunda `Boolean` ifadesi ve tek bir sayısal ifade, Visual Basic dönüştürür `Boolean` ifade sayısal bir değere (– 1 için `True` ve 0 `False`) ve bit tabanlı işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="21a4c-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="21a4c-141">Boolean karşılaştırması için sonuç veri türünde `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="21a4c-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="21a4c-142">Bit tabanlı karşılaştırma için sonuç veri türü veri türleri için uygun sayısal bir tür değil. `expression1` ve `expression2`.</span><span class="sxs-lookup"><span data-stu-id="21a4c-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="21a4c-143">"İlişkisel ve Bitsel karşılaştırmaları" tablosunda görmek [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="21a4c-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21a4c-144">`And` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="21a4c-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="21a4c-145">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="21a4c-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="21a4c-146">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="21a4c-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21a4c-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="21a4c-147">Example</span></span>  
 <span data-ttu-id="21a4c-148">Aşağıdaki örnek kullanır `And` iki ifadeleri mantıksal ve işlecini gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="21a4c-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="21a4c-149">Sonuç bir `Boolean` ifadeleri her ikisi de olup olmadığını gösteren bir değer `True`.</span><span class="sxs-lookup"><span data-stu-id="21a4c-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 <span data-ttu-id="21a4c-150">Önceki örnekte sonuçlarını üreten `True` ve `False`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="21a4c-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21a4c-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="21a4c-151">Example</span></span>  
 <span data-ttu-id="21a4c-152">Aşağıdaki örnek kullanır `And` iki sayısal ifadeye tek tek bitleri mantıksal ve işlecini gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="21a4c-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="21a4c-153">İşlenen karşılık gelen bitleri hem kümesine 1 olduğunda sonuç düzeninde bit ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="21a4c-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 <span data-ttu-id="21a4c-154">Önceki örnekte, 8, 2 ve 0, sonuçları sırasıyla üretir.</span><span class="sxs-lookup"><span data-stu-id="21a4c-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a4c-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21a4c-155">See Also</span></span>  
 [<span data-ttu-id="21a4c-156">Mantıksal ve bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21a4c-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="21a4c-157">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="21a4c-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="21a4c-158">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="21a4c-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="21a4c-159">AndAlso İşleci</span><span class="sxs-lookup"><span data-stu-id="21a4c-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [<span data-ttu-id="21a4c-160">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="21a4c-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
