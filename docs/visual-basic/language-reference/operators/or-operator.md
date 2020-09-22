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
ms.openlocfilehash: f6cfd1073ada42aa2db8be9b14c81319bc0db294
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874764"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="a273d-102">Or İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a273d-102">Or Operator (Visual Basic)</span></span>

<span data-ttu-id="a273d-103">İki ifadeye mantıksal bir ayırıcı `Boolean` ya da iki sayısal ifadeye bit düzeyinde ayırıcı uygular.</span><span class="sxs-lookup"><span data-stu-id="a273d-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a273d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a273d-104">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="a273d-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a273d-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="a273d-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a273d-106">Required.</span></span> <span data-ttu-id="a273d-107">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="a273d-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="a273d-108">`Boolean`Karşılaştırma için `result` iki değerden oluşan kapsamlı mantıksal ayırıcı olur `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="a273d-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="a273d-109">Bit düzeyinde işlemler için `result` iki sayısal bit deseninin kapsamlı bit düzeyinde debirleşimin temsil eden sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="a273d-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="a273d-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a273d-110">Required.</span></span> <span data-ttu-id="a273d-111">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="a273d-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a273d-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a273d-112">Required.</span></span> <span data-ttu-id="a273d-113">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="a273d-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a273d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a273d-114">Remarks</span></span>  

 <span data-ttu-id="a273d-115">`Boolean`Karşılaştırma için `result` `False` ve yalnızca her ikisi de `expression1` `expression2` olarak değerlendirilir `False` .</span><span class="sxs-lookup"><span data-stu-id="a273d-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="a273d-116">Aşağıdaki tabloda nasıl belirlendiği gösterilmektedir `result` .</span><span class="sxs-lookup"><span data-stu-id="a273d-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="a273d-117">İse `expression1`</span><span class="sxs-lookup"><span data-stu-id="a273d-117">If `expression1` is</span></span>|<span data-ttu-id="a273d-118">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="a273d-118">And `expression2` is</span></span>|<span data-ttu-id="a273d-119">`result`Öğesinin değeri</span><span class="sxs-lookup"><span data-stu-id="a273d-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="a273d-120">Bir `Boolean` karşılaştırmada, `Or` işleç her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a273d-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="a273d-121">[OrElse işleci](orelse-operator.md) *kısa*devre uygular, yani `expression1` ise, `True` `expression2` hesaplanmaz.</span><span class="sxs-lookup"><span data-stu-id="a273d-121">The [OrElse Operator](orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="a273d-122">Bit düzeyinde işlemler için, `Or` işleç iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve karşılık gelen biti `result` aşağıdaki tabloya göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a273d-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="a273d-123">Eğer bit `expression1` ise</span><span class="sxs-lookup"><span data-stu-id="a273d-123">If bit in `expression1` is</span></span>|<span data-ttu-id="a273d-124">Ve bit `expression2` ,</span><span class="sxs-lookup"><span data-stu-id="a273d-124">And bit in `expression2` is</span></span>|<span data-ttu-id="a273d-125">`result`İçindeki bit</span><span class="sxs-lookup"><span data-stu-id="a273d-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="a273d-126">1</span><span class="sxs-lookup"><span data-stu-id="a273d-126">1</span></span>|<span data-ttu-id="a273d-127">1</span><span class="sxs-lookup"><span data-stu-id="a273d-127">1</span></span>|<span data-ttu-id="a273d-128">1</span><span class="sxs-lookup"><span data-stu-id="a273d-128">1</span></span>|  
|<span data-ttu-id="a273d-129">1</span><span class="sxs-lookup"><span data-stu-id="a273d-129">1</span></span>|<span data-ttu-id="a273d-130">0</span><span class="sxs-lookup"><span data-stu-id="a273d-130">0</span></span>|<span data-ttu-id="a273d-131">1</span><span class="sxs-lookup"><span data-stu-id="a273d-131">1</span></span>|  
|<span data-ttu-id="a273d-132">0</span><span class="sxs-lookup"><span data-stu-id="a273d-132">0</span></span>|<span data-ttu-id="a273d-133">1</span><span class="sxs-lookup"><span data-stu-id="a273d-133">1</span></span>|<span data-ttu-id="a273d-134">1</span><span class="sxs-lookup"><span data-stu-id="a273d-134">1</span></span>|  
|<span data-ttu-id="a273d-135">0</span><span class="sxs-lookup"><span data-stu-id="a273d-135">0</span></span>|<span data-ttu-id="a273d-136">0</span><span class="sxs-lookup"><span data-stu-id="a273d-136">0</span></span>|<span data-ttu-id="a273d-137">0</span><span class="sxs-lookup"><span data-stu-id="a273d-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a273d-138">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a273d-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="a273d-139">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="a273d-139">Data Types</span></span>  

 <span data-ttu-id="a273d-140">İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadeyi sayısal bir değere dönüştürür (– 1 `True` ve için 0 `False` ) ve bit düzeyinde bir işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a273d-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="a273d-141">Bir `Boolean` karşılaştırma için sonucun veri türü olur `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="a273d-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="a273d-142">Bit düzeyinde karşılaştırma için, sonuç veri türü ve veri türleri için uygun sayısal bir türdür `expression1` `expression2` .</span><span class="sxs-lookup"><span data-stu-id="a273d-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="a273d-143">[Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="a273d-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a273d-144">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="a273d-144">Overloading</span></span>  

 <span data-ttu-id="a273d-145">`Or`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a273d-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a273d-146">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a273d-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a273d-147">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a273d-147">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a273d-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="a273d-148">Example</span></span>  

 <span data-ttu-id="a273d-149">Aşağıdaki örnek, `Or` iki ifadeye kapsamlı bir mantıksal ayırıcı gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a273d-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="a273d-150">Sonuç, `Boolean` iki deyimden birinin olup olmadığını temsil eden bir değerdir `True` .</span><span class="sxs-lookup"><span data-stu-id="a273d-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="a273d-151">Yukarıdaki örnek `True` sırasıyla,, ve sonuçlarını üretir `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="a273d-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a273d-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="a273d-152">Example</span></span>  

 <span data-ttu-id="a273d-153">Aşağıdaki örnek, `Or` iki sayısal ifadenin ayrı bitleri üzerinde kapsamlı mantıksal ayırıcı gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a273d-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="a273d-154">Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin biri 1 olarak ayarlandıysa ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a273d-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="a273d-155">Yukarıdaki örnek sırasıyla 10, 14 ve 14 sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="a273d-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a273d-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a273d-156">See also</span></span>

- [<span data-ttu-id="a273d-157">Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a273d-157">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="a273d-158">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="a273d-158">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="a273d-159">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="a273d-159">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="a273d-160">OrElse İşleci</span><span class="sxs-lookup"><span data-stu-id="a273d-160">OrElse Operator</span></span>](orelse-operator.md)
- [<span data-ttu-id="a273d-161">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="a273d-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
