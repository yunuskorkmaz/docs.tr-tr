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
ms.openlocfilehash: 090ae67c1e5f04c5d9c4f6aed7f8131d8f830166
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968861"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="80412-102">And İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80412-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="80412-103">İki mantıksal ve işlecini gerçekleştirir `Boolean` deyimlerde ya da iki sayısal ifadeye bit tabanlı ve işlecini bir.</span><span class="sxs-lookup"><span data-stu-id="80412-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80412-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80412-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="80412-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="80412-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="80412-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="80412-106">Required.</span></span> <span data-ttu-id="80412-107">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="80412-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="80412-108">Boole karşılaştırma `result` mantıksal ve işlecini iki olan `Boolean` değerleri.</span><span class="sxs-lookup"><span data-stu-id="80412-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="80412-109">Bit düzeyinde işlemler için `result` bit tabanlı ve işlecini iki sayısal bit desenlerinin temsil eden sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="80412-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="80412-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="80412-110">Required.</span></span> <span data-ttu-id="80412-111">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="80412-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="80412-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="80412-112">Required.</span></span> <span data-ttu-id="80412-113">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="80412-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80412-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80412-114">Remarks</span></span>  
 <span data-ttu-id="80412-115">Boole karşılaştırma `result` olduğu `True` varsa ve yalnızca her iki `expression1` ve `expression2` vermesi `True`.</span><span class="sxs-lookup"><span data-stu-id="80412-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="80412-116">Aşağıdaki tabloda gösterilmiştir nasıl `result` belirlenir.</span><span class="sxs-lookup"><span data-stu-id="80412-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="80412-117">Varsa `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="80412-117">If `expression1` is</span></span>|<span data-ttu-id="80412-118">Ve `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="80412-118">And `expression2` is</span></span>|<span data-ttu-id="80412-119">Değerini `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="80412-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="80412-120">Bir Boolean karşılaştırmaya `And` işleci yordam çağrıları yapma içerebilir her iki ifade her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="80412-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="80412-121">[AndAlso işleci](../../../visual-basic/language-reference/operators/andalso-operator.md) gerçekleştirir *kısa devre*, olması durumunda anlamına gelir `expression1` olduğu `False`, ardından `expression2` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="80412-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="80412-122">Sayısal değerlere uygulandığında `And` işleci iki sayısal ifadeye bit düzeyinde bir karşılaştırma aynı şekilde konumlandırılmış bit gerçekleştirir ve karşılık gelen, bit ayarlar `result` aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="80412-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="80412-123">Varsa, bit `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="80412-123">If bit in `expression1` is</span></span>|<span data-ttu-id="80412-124">Ve içindeki bit `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="80412-124">And bit in `expression2` is</span></span>|<span data-ttu-id="80412-125">Bit `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="80412-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="80412-126">1.</span><span class="sxs-lookup"><span data-stu-id="80412-126">1</span></span>|<span data-ttu-id="80412-127">1.</span><span class="sxs-lookup"><span data-stu-id="80412-127">1</span></span>|<span data-ttu-id="80412-128">1.</span><span class="sxs-lookup"><span data-stu-id="80412-128">1</span></span>|  
|<span data-ttu-id="80412-129">1</span><span class="sxs-lookup"><span data-stu-id="80412-129">1</span></span>|<span data-ttu-id="80412-130">0</span><span class="sxs-lookup"><span data-stu-id="80412-130">0</span></span>|<span data-ttu-id="80412-131">0</span><span class="sxs-lookup"><span data-stu-id="80412-131">0</span></span>|  
|<span data-ttu-id="80412-132">0</span><span class="sxs-lookup"><span data-stu-id="80412-132">0</span></span>|<span data-ttu-id="80412-133">1.</span><span class="sxs-lookup"><span data-stu-id="80412-133">1</span></span>|<span data-ttu-id="80412-134">0</span><span class="sxs-lookup"><span data-stu-id="80412-134">0</span></span>|  
|<span data-ttu-id="80412-135">0</span><span class="sxs-lookup"><span data-stu-id="80412-135">0</span></span>|<span data-ttu-id="80412-136">0</span><span class="sxs-lookup"><span data-stu-id="80412-136">0</span></span>|<span data-ttu-id="80412-137">0</span><span class="sxs-lookup"><span data-stu-id="80412-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="80412-138">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçler düşük önceliğe sahip olduğundan, herhangi bir bit düzeyinde işlemler doğru sonuçlar sağlamak için parantez içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="80412-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="80412-139">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="80412-139">Data Types</span></span>  
 <span data-ttu-id="80412-140">İşlenenler biri oluşuyorsa `Boolean` ifadesi ve bir sayısal ifade, Visual Basic dönüştürür `Boolean` ifadesi bir sayısal değere (– 1 için `True` ve 0 `False`) ve bir bit düzeyinde işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="80412-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="80412-141">Boole bir karşılaştırması için sonuç veri türü olan `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="80412-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="80412-142">Bit düzeyinde bir karşılaştırması için sonuç veri türü bir sayısal veri türleri için uygun türüdür `expression1` ve `expression2`.</span><span class="sxs-lookup"><span data-stu-id="80412-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="80412-143">"İlişkisel ve bit düzeyinde karşılaştırmaları" tablosuna bakın [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="80412-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80412-144">`And` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="80412-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="80412-145">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="80412-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="80412-146">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="80412-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80412-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="80412-147">Example</span></span>  
 <span data-ttu-id="80412-148">Aşağıdaki örnekte `And` mantıksal ve işlecini iki ifadelerini gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="80412-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="80412-149">Sonuç bir `Boolean` hem ifadelerin olup olmadığını gösteren bir değer `True`.</span><span class="sxs-lookup"><span data-stu-id="80412-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="80412-150">Yukarıdaki örnekte sonuçlarını üretir `True` ve `False`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="80412-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80412-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="80412-151">Example</span></span>  
 <span data-ttu-id="80412-152">Aşağıdaki örnekte `And` mantıksal ve işlecini bireysel iki sayısal ifadeye bit üzerinde gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="80412-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="80412-153">İşlenenler karşılık gelen bitler her iki küme 1 olduğunda sonuç deseninde bir bit ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="80412-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="80412-154">Yukarıdaki örnekte sırasıyla 8, 2 ve 0, sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="80412-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80412-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80412-155">See also</span></span>
- [<span data-ttu-id="80412-156">Mantıksal/bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80412-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="80412-157">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="80412-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="80412-158">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="80412-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="80412-159">AndAlso İşleci</span><span class="sxs-lookup"><span data-stu-id="80412-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="80412-160">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="80412-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
