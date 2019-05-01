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
ms.openlocfilehash: 0277b6f24e62ed5f0cad3dae225c86fffc4c09b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013523"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="902b7-102">Or İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="902b7-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="902b7-103">İkisini de bir mantıksal veya işlecini gerçekleştirir `Boolean` deyimlerde ya da bir iki sayısal ifadeye bit tabanlı veya işlecini.</span><span class="sxs-lookup"><span data-stu-id="902b7-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="902b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="902b7-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="902b7-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="902b7-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="902b7-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="902b7-106">Required.</span></span> <span data-ttu-id="902b7-107">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="902b7-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="902b7-108">İçin `Boolean` karşılaştırması, `result` iki kapsamlı mantıksal veya işlecini olan `Boolean` değerleri.</span><span class="sxs-lookup"><span data-stu-id="902b7-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="902b7-109">Bit düzeyinde işlemler için `result` iki sayısal bit desenlerinin kapsamlı bit tabanlı veya işlecini temsil eden sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="902b7-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="902b7-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="902b7-110">Required.</span></span> <span data-ttu-id="902b7-111">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="902b7-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="902b7-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="902b7-112">Required.</span></span> <span data-ttu-id="902b7-113">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="902b7-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="902b7-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="902b7-114">Remarks</span></span>  
 <span data-ttu-id="902b7-115">İçin `Boolean` karşılaştırması, `result` olduğu `False` varsa ve yalnızca her iki `expression1` ve `expression2` vermesi `False`.</span><span class="sxs-lookup"><span data-stu-id="902b7-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="902b7-116">Aşağıdaki tabloda gösterilmiştir nasıl `result` belirlenir.</span><span class="sxs-lookup"><span data-stu-id="902b7-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="902b7-117">Varsa `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="902b7-117">If `expression1` is</span></span>|<span data-ttu-id="902b7-118">Ve `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="902b7-118">And `expression2` is</span></span>|<span data-ttu-id="902b7-119">Değerini `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="902b7-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="902b7-120">İçinde bir `Boolean` karşılaştırması, `Or` işleci yordam çağrıları yapma içerebilir her iki ifade her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="902b7-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="902b7-121">[OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md) gerçekleştirir *kısa devre*, olması durumunda anlamına gelir `expression1` olduğu `True`, ardından `expression2` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="902b7-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="902b7-122">Bit düzeyinde işlemler için `Or` işleci iki sayısal ifadeye bit düzeyinde bir karşılaştırma aynı şekilde konumlandırılmış bit gerçekleştirir ve karşılık gelen, bit ayarlar `result` aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="902b7-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="902b7-123">Varsa, bit `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="902b7-123">If bit in `expression1` is</span></span>|<span data-ttu-id="902b7-124">Ve içindeki bit `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="902b7-124">And bit in `expression2` is</span></span>|<span data-ttu-id="902b7-125">Bit `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="902b7-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="902b7-126">1.</span><span class="sxs-lookup"><span data-stu-id="902b7-126">1</span></span>|<span data-ttu-id="902b7-127">1.</span><span class="sxs-lookup"><span data-stu-id="902b7-127">1</span></span>|<span data-ttu-id="902b7-128">1.</span><span class="sxs-lookup"><span data-stu-id="902b7-128">1</span></span>|  
|<span data-ttu-id="902b7-129">1</span><span class="sxs-lookup"><span data-stu-id="902b7-129">1</span></span>|<span data-ttu-id="902b7-130">0</span><span class="sxs-lookup"><span data-stu-id="902b7-130">0</span></span>|<span data-ttu-id="902b7-131">1.</span><span class="sxs-lookup"><span data-stu-id="902b7-131">1</span></span>|  
|<span data-ttu-id="902b7-132">0</span><span class="sxs-lookup"><span data-stu-id="902b7-132">0</span></span>|<span data-ttu-id="902b7-133">1.</span><span class="sxs-lookup"><span data-stu-id="902b7-133">1</span></span>|<span data-ttu-id="902b7-134">1</span><span class="sxs-lookup"><span data-stu-id="902b7-134">1</span></span>|  
|<span data-ttu-id="902b7-135">0</span><span class="sxs-lookup"><span data-stu-id="902b7-135">0</span></span>|<span data-ttu-id="902b7-136">0</span><span class="sxs-lookup"><span data-stu-id="902b7-136">0</span></span>|<span data-ttu-id="902b7-137">0</span><span class="sxs-lookup"><span data-stu-id="902b7-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="902b7-138">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçler düşük önceliğe sahip olduğundan, herhangi bir bit düzeyinde işlemler doğru yürütme emin olmak için parantez içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="902b7-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="902b7-139">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="902b7-139">Data Types</span></span>  
 <span data-ttu-id="902b7-140">İşlenenler biri oluşuyorsa `Boolean` ifadesi ve bir sayısal ifade, Visual Basic dönüştürür `Boolean` ifadesi bir sayısal değere (– 1 için `True` ve 0 `False`) ve bir bit düzeyinde işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="902b7-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="902b7-141">İçin bir `Boolean` karşılaştırma, sonuç veri türü olan `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="902b7-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="902b7-142">Bit düzeyinde bir karşılaştırması için sonuç veri türü bir sayısal veri türleri için uygun türüdür `expression1` ve `expression2`.</span><span class="sxs-lookup"><span data-stu-id="902b7-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="902b7-143">"İlişkisel ve bit düzeyinde karşılaştırmaları" tablosuna bakın [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="902b7-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="902b7-144">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="902b7-144">Overloading</span></span>  
 <span data-ttu-id="902b7-145">`Or` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="902b7-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="902b7-146">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="902b7-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="902b7-147">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="902b7-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="902b7-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="902b7-148">Example</span></span>  
 <span data-ttu-id="902b7-149">Aşağıdaki örnekte `Or` kapsamlı mantıksal veya işlecini iki ifadelerini gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="902b7-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="902b7-150">Sonuç bir `Boolean` gösteren bir değer iki ifadeden birini olup olmadığını `True`.</span><span class="sxs-lookup"><span data-stu-id="902b7-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="902b7-151">Yukarıdaki örnekte sonuçlarını üretir `True`, `True`, ve `False`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="902b7-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="902b7-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="902b7-152">Example</span></span>  
 <span data-ttu-id="902b7-153">Aşağıdaki örnekte `Or` kapsamlı mantıksal veya işlecini bireysel iki sayısal ifadeye bit üzerinde gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="902b7-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="902b7-154">Sonuç deseninde bit işlenenler karşılık gelen bitleri ya da ayarlanmış ise 1 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="902b7-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="902b7-155">Yukarıdaki örnekte sırasıyla 10, 14 ve 14, sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="902b7-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902b7-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="902b7-156">See also</span></span>

- [<span data-ttu-id="902b7-157">Mantıksal/bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="902b7-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="902b7-158">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="902b7-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="902b7-159">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="902b7-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="902b7-160">OrElse İşleci</span><span class="sxs-lookup"><span data-stu-id="902b7-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="902b7-161">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="902b7-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
