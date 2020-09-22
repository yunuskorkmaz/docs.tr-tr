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
ms.openlocfilehash: b4d6d08cca2907befeab2e31c6804b69849c9e38
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874866"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="1ef0b-102">And İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ef0b-102">And Operator (Visual Basic)</span></span>

<span data-ttu-id="1ef0b-103">İki ifadeye bir mantıksal birlikte `Boolean` veya iki sayısal ifadeye bit tabanlı bir birlikte uygular.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ef0b-104">Syntax</span></span>  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="1ef0b-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="1ef0b-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="1ef0b-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-106">Required.</span></span> <span data-ttu-id="1ef0b-107">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="1ef0b-108">Boolean karşılaştırma için `result` iki değerden oluşan mantıksal bir değer `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="1ef0b-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="1ef0b-109">Bit düzeyinde işlemler için, `result` iki sayısal bit deseninin bit düzeyinde birlikte temsil eden sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="1ef0b-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-110">Required.</span></span> <span data-ttu-id="1ef0b-111">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="1ef0b-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-112">Required.</span></span> <span data-ttu-id="1ef0b-113">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ef0b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ef0b-114">Remarks</span></span>  

 <span data-ttu-id="1ef0b-115">Boolean karşılaştırma için `result` `True` ve yalnızca her ikisi de `expression1` `expression2` olarak değerlendirilir `True` .</span><span class="sxs-lookup"><span data-stu-id="1ef0b-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="1ef0b-116">Aşağıdaki tabloda nasıl belirlendiği gösterilmektedir `result` .</span><span class="sxs-lookup"><span data-stu-id="1ef0b-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="1ef0b-117">İse `expression1`</span><span class="sxs-lookup"><span data-stu-id="1ef0b-117">If `expression1` is</span></span>|<span data-ttu-id="1ef0b-118">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="1ef0b-118">And `expression2` is</span></span>|<span data-ttu-id="1ef0b-119">`result`Öğesinin değeri</span><span class="sxs-lookup"><span data-stu-id="1ef0b-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="1ef0b-120">Boole karşılaştırmasına, `And` işleç her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="1ef0b-121">[AndAlso işleci de](andalso-operator.md) *kısa*devre uygular, yani varsa `expression1` `False` , `expression2` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-121">The [AndAlso Operator](andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="1ef0b-122">Sayısal değerlere uygulandığında `And` operatör iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve karşılık gelen biti `result` aşağıdaki tabloya göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="1ef0b-123">Eğer bit `expression1` ise</span><span class="sxs-lookup"><span data-stu-id="1ef0b-123">If bit in `expression1` is</span></span>|<span data-ttu-id="1ef0b-124">Ve bit `expression2` ,</span><span class="sxs-lookup"><span data-stu-id="1ef0b-124">And bit in `expression2` is</span></span>|<span data-ttu-id="1ef0b-125">`result`İçindeki bit</span><span class="sxs-lookup"><span data-stu-id="1ef0b-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="1ef0b-126">1</span><span class="sxs-lookup"><span data-stu-id="1ef0b-126">1</span></span>|<span data-ttu-id="1ef0b-127">1</span><span class="sxs-lookup"><span data-stu-id="1ef0b-127">1</span></span>|<span data-ttu-id="1ef0b-128">1</span><span class="sxs-lookup"><span data-stu-id="1ef0b-128">1</span></span>|  
|<span data-ttu-id="1ef0b-129">1</span><span class="sxs-lookup"><span data-stu-id="1ef0b-129">1</span></span>|<span data-ttu-id="1ef0b-130">0</span><span class="sxs-lookup"><span data-stu-id="1ef0b-130">0</span></span>|<span data-ttu-id="1ef0b-131">0</span><span class="sxs-lookup"><span data-stu-id="1ef0b-131">0</span></span>|  
|<span data-ttu-id="1ef0b-132">0</span><span class="sxs-lookup"><span data-stu-id="1ef0b-132">0</span></span>|<span data-ttu-id="1ef0b-133">1</span><span class="sxs-lookup"><span data-stu-id="1ef0b-133">1</span></span>|<span data-ttu-id="1ef0b-134">0</span><span class="sxs-lookup"><span data-stu-id="1ef0b-134">0</span></span>|  
|<span data-ttu-id="1ef0b-135">0</span><span class="sxs-lookup"><span data-stu-id="1ef0b-135">0</span></span>|<span data-ttu-id="1ef0b-136">0</span><span class="sxs-lookup"><span data-stu-id="1ef0b-136">0</span></span>|<span data-ttu-id="1ef0b-137">0</span><span class="sxs-lookup"><span data-stu-id="1ef0b-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="1ef0b-138">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru sonuçları sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="1ef0b-139">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="1ef0b-139">Data Types</span></span>  

 <span data-ttu-id="1ef0b-140">İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadeyi sayısal bir değere dönüştürür (– 1 `True` ve için 0 `False` ) ve bit düzeyinde bir işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="1ef0b-141">Boolean karşılaştırma için sonucun veri türü olur `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="1ef0b-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="1ef0b-142">Bit düzeyinde karşılaştırma için, sonuç veri türü ve veri türleri için uygun sayısal bir türdür `expression1` `expression2` .</span><span class="sxs-lookup"><span data-stu-id="1ef0b-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="1ef0b-143">[Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ef0b-144">`And`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1ef0b-145">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1ef0b-146">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1ef0b-146">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ef0b-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ef0b-147">Example</span></span>  

 <span data-ttu-id="1ef0b-148">Aşağıdaki örnek, `And` iki ifadeye mantıksal bir birlikte gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="1ef0b-149">Sonuç, `Boolean` ifadelerin her ikisinin de olup olmadığını temsil eden bir değerdir `True` .</span><span class="sxs-lookup"><span data-stu-id="1ef0b-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="1ef0b-150">Yukarıdaki örnek `True` sırasıyla ve, sonuçları üretir `False` .</span><span class="sxs-lookup"><span data-stu-id="1ef0b-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ef0b-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ef0b-151">Example</span></span>  

 <span data-ttu-id="1ef0b-152">Aşağıdaki örnek, `And` iki sayısal ifadenin ayrı bitleri üzerinde mantıksal bir işlem gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="1ef0b-153">Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin her ikisi de 1 olarak ayarlandıysa ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="1ef0b-154">Yukarıdaki örnek sırasıyla 8, 2 ve 0 sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef0b-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ef0b-155">See also</span></span>

- [<span data-ttu-id="1ef0b-156">Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ef0b-156">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="1ef0b-157">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="1ef0b-157">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="1ef0b-158">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="1ef0b-158">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="1ef0b-159">AndAlso İşleci</span><span class="sxs-lookup"><span data-stu-id="1ef0b-159">AndAlso Operator</span></span>](andalso-operator.md)
- [<span data-ttu-id="1ef0b-160">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="1ef0b-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
