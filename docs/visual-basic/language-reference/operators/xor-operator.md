---
title: Xor İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: 0cba3a995fb1ab774c8a5308e58f0b6905fc23f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827074"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="68845-102">Xor İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68845-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="68845-103">İki mantıksal dışlama gerçekleştirir `Boolean` deyimlerde ya da iki sayısal ifadeye bit tabanlı dışlama.</span><span class="sxs-lookup"><span data-stu-id="68845-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68845-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68845-104">Syntax</span></span>  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="68845-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="68845-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="68845-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="68845-106">Required.</span></span> <span data-ttu-id="68845-107">Tüm `Boolean` veya sayısal bir değişken.</span><span class="sxs-lookup"><span data-stu-id="68845-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="68845-108">Boole karşılaştırma `result` (özel mantıksal veya işlecini) iki mantıksal dışlama `Boolean` değerleri.</span><span class="sxs-lookup"><span data-stu-id="68845-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="68845-109">Bit düzeyinde işlemler için `result` iki sayısal bit desenlerinin (özel bit tabanlı veya işlecini) bit tabanlı dışlama temsil eden sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="68845-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="68845-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="68845-110">Required.</span></span> <span data-ttu-id="68845-111">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="68845-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="68845-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="68845-112">Required.</span></span> <span data-ttu-id="68845-113">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="68845-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68845-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68845-114">Remarks</span></span>  
 <span data-ttu-id="68845-115">Boole karşılaştırma `result` olduğu `True` ve yalnızca, tam olarak birine `expression1` ve `expression2` değerlendiren `True`.</span><span class="sxs-lookup"><span data-stu-id="68845-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="68845-116">Diğer bir deyişle, ve yalnızca, `expression1` ve `expression2` değerlendirmek için ters `Boolean` değerleri.</span><span class="sxs-lookup"><span data-stu-id="68845-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="68845-117">Aşağıdaki tabloda gösterilmiştir nasıl `result` belirlenir.</span><span class="sxs-lookup"><span data-stu-id="68845-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="68845-118">Varsa `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="68845-118">If `expression1` is</span></span>|<span data-ttu-id="68845-119">Ve `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="68845-119">And `expression2` is</span></span>|<span data-ttu-id="68845-120">Değerini `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="68845-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="68845-121">Bir Boolean karşılaştırmaya `Xor` işleci yordam çağrıları yapma içerebilir her iki ifade her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="68845-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="68845-122">İçin hiçbir short-circuiting karşılığı yoktur `Xor`, sonucu her zaman her iki işlenen üzerinde de bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="68845-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="68845-123">İçin *kısa devre* mantıksal işleçler bkz [AndAlso işleci](../../../visual-basic/language-reference/operators/andalso-operator.md) ve [OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="68845-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="68845-124">Bit düzeyinde işlemler için `Xor` işleci iki sayısal ifadeye bit düzeyinde bir karşılaştırma aynı şekilde konumlandırılmış bit gerçekleştirir ve karşılık gelen, bit ayarlar `result` aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="68845-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="68845-125">Varsa, bit `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="68845-125">If bit in `expression1` is</span></span>|<span data-ttu-id="68845-126">Ve içindeki bit `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="68845-126">And bit in `expression2` is</span></span>|<span data-ttu-id="68845-127">Bit `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="68845-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="68845-128">1.</span><span class="sxs-lookup"><span data-stu-id="68845-128">1</span></span>|<span data-ttu-id="68845-129">1</span><span class="sxs-lookup"><span data-stu-id="68845-129">1</span></span>|<span data-ttu-id="68845-130">0</span><span class="sxs-lookup"><span data-stu-id="68845-130">0</span></span>|  
|<span data-ttu-id="68845-131">1.</span><span class="sxs-lookup"><span data-stu-id="68845-131">1</span></span>|<span data-ttu-id="68845-132">0</span><span class="sxs-lookup"><span data-stu-id="68845-132">0</span></span>|<span data-ttu-id="68845-133">1.</span><span class="sxs-lookup"><span data-stu-id="68845-133">1</span></span>|  
|<span data-ttu-id="68845-134">0</span><span class="sxs-lookup"><span data-stu-id="68845-134">0</span></span>|<span data-ttu-id="68845-135">1.</span><span class="sxs-lookup"><span data-stu-id="68845-135">1</span></span>|<span data-ttu-id="68845-136">1</span><span class="sxs-lookup"><span data-stu-id="68845-136">1</span></span>|  
|<span data-ttu-id="68845-137">0</span><span class="sxs-lookup"><span data-stu-id="68845-137">0</span></span>|<span data-ttu-id="68845-138">0</span><span class="sxs-lookup"><span data-stu-id="68845-138">0</span></span>|<span data-ttu-id="68845-139">0</span><span class="sxs-lookup"><span data-stu-id="68845-139">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="68845-140">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçler düşük önceliğe sahip olduğundan, herhangi bir bit düzeyinde işlemler doğru yürütme emin olmak için parantez içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68845-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="68845-141">Örneğin, 5 `Xor` 3, 6.</span><span class="sxs-lookup"><span data-stu-id="68845-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="68845-142">Bu neden olduğunu görmek için bu nedenle, 5. ve 3, ikili gösterimler için 101 ve 011 Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="68845-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="68845-143">Ardından, ondalık sayı 6 ikili gösterimini olduğu 101 Xor 011 110, olduğunu belirlemek için önceki tabloyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="68845-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="68845-144">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="68845-144">Data Types</span></span>  
 <span data-ttu-id="68845-145">İşlenenler biri oluşuyorsa `Boolean` ifadesi ve bir sayısal ifade, Visual Basic dönüştürür `Boolean` ifadesi bir sayısal değere (– 1 için `True` ve 0 `False`) ve bir bit düzeyinde işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="68845-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="68845-146">İçin bir `Boolean` karşılaştırma, sonuç veri türü olan `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="68845-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="68845-147">Bit düzeyinde bir karşılaştırması için sonuç veri türü bir sayısal veri türleri için uygun türüdür `expression1` ve `expression2`.</span><span class="sxs-lookup"><span data-stu-id="68845-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="68845-148">"İlişkisel ve bit düzeyinde karşılaştırmaları" tablosuna bakın [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="68845-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="68845-149">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="68845-149">Overloading</span></span>  
 <span data-ttu-id="68845-150">`Xor` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="68845-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="68845-151">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="68845-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="68845-152">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="68845-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68845-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="68845-153">Example</span></span>  
 <span data-ttu-id="68845-154">Aşağıdaki örnekte `Xor` iki ifadelerini temel (özel mantıksal veya işlecini) mantıksal dışlama gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="68845-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="68845-155">Sonuç bir `Boolean` tam olarak bir ifade olup olmadığını gösteren bir değer `True`.</span><span class="sxs-lookup"><span data-stu-id="68845-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="68845-156">Önceki örnekte sonuçlarını üretir `False`, `True`, ve `False`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="68845-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68845-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="68845-157">Example</span></span>  
 <span data-ttu-id="68845-158">Aşağıdaki örnekte `Xor` mantıksal dışlama (özel mantıksal veya işlecini) bireysel iki sayısal ifadeye bit üzerinde gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="68845-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="68845-159">Tek bir işlenen karşılık gelen bitleri 1 olarak ayarlarsanız sonucu deseninde bir bit ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="68845-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="68845-160">Önceki örnekte sırasıyla 2, 12 ve 14, sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="68845-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68845-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68845-161">See also</span></span>

- [<span data-ttu-id="68845-162">Mantıksal/bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68845-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="68845-163">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="68845-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="68845-164">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="68845-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="68845-165">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="68845-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
