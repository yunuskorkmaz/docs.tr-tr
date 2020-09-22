---
title: Xor İşleci
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
ms.openlocfilehash: ce7592c73f387d6ddbfd328abce8555cb7dcd303
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875296"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="a948c-102">Xor İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a948c-102">Xor Operator (Visual Basic)</span></span>

<span data-ttu-id="a948c-103">İki ifadede bir mantıksal dışlama `Boolean` veya iki sayısal ifadede bit tabanlı dışlama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a948c-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a948c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a948c-104">Syntax</span></span>  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="a948c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a948c-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="a948c-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a948c-106">Required.</span></span> <span data-ttu-id="a948c-107">Herhangi bir `Boolean` veya sayısal değişken.</span><span class="sxs-lookup"><span data-stu-id="a948c-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="a948c-108">Boolean karşılaştırma için `result` iki değerin mantıksal dışlamasıdır (dışlamalı mantıksal ayırıcı) `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="a948c-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="a948c-109">Bit düzeyinde işlemler için `result` iki sayısal bit deseninin bit düzeyinde dışlamasını (dışlayıcı bit düzeyinde ayırıcı) temsil eden sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="a948c-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="a948c-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a948c-110">Required.</span></span> <span data-ttu-id="a948c-111">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="a948c-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a948c-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a948c-112">Required.</span></span> <span data-ttu-id="a948c-113">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="a948c-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a948c-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a948c-114">Remarks</span></span>  

 <span data-ttu-id="a948c-115">Boolean karşılaştırma için, `result` `True` ve yalnızca tam olarak bir tane olarak `expression1` `expression2` değerlendirilir `True` .</span><span class="sxs-lookup"><span data-stu-id="a948c-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="a948c-116">Diğer bir deyişle, ve yalnızca Eğer `expression1` ve `expression2` ters değerler olarak değerlendirilir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="a948c-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="a948c-117">Aşağıdaki tabloda nasıl belirlendiği gösterilmektedir `result` .</span><span class="sxs-lookup"><span data-stu-id="a948c-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="a948c-118">İse `expression1`</span><span class="sxs-lookup"><span data-stu-id="a948c-118">If `expression1` is</span></span>|<span data-ttu-id="a948c-119">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="a948c-119">And `expression2` is</span></span>|<span data-ttu-id="a948c-120">`result`Öğesinin değeri</span><span class="sxs-lookup"><span data-stu-id="a948c-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="a948c-121">Boole karşılaştırmasına, `Xor` işleç her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a948c-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="a948c-122">Her `Xor` iki işlenenden de her zaman bağlı olduğundan, için bir kısa devre temelli karşılık yoktur.</span><span class="sxs-lookup"><span data-stu-id="a948c-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="a948c-123">*Kısa* devre mantıksal işleçler için bkz. [AndAlso Işleci](andalso-operator.md) ve [orelsa işleci](orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="a948c-123">For *short-circuiting* logical operators, see [AndAlso Operator](andalso-operator.md) and [OrElse Operator](orelse-operator.md).</span></span>  
  
 <span data-ttu-id="a948c-124">Bit düzeyinde işlemler için, `Xor` işleç iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve karşılık gelen biti `result` aşağıdaki tabloya göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a948c-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="a948c-125">Eğer bit `expression1` ise</span><span class="sxs-lookup"><span data-stu-id="a948c-125">If bit in `expression1` is</span></span>|<span data-ttu-id="a948c-126">Ve bit `expression2` ,</span><span class="sxs-lookup"><span data-stu-id="a948c-126">And bit in `expression2` is</span></span>|<span data-ttu-id="a948c-127">`result`İçindeki bit</span><span class="sxs-lookup"><span data-stu-id="a948c-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="a948c-128">1</span><span class="sxs-lookup"><span data-stu-id="a948c-128">1</span></span>|<span data-ttu-id="a948c-129">1</span><span class="sxs-lookup"><span data-stu-id="a948c-129">1</span></span>|<span data-ttu-id="a948c-130">0</span><span class="sxs-lookup"><span data-stu-id="a948c-130">0</span></span>|  
|<span data-ttu-id="a948c-131">1</span><span class="sxs-lookup"><span data-stu-id="a948c-131">1</span></span>|<span data-ttu-id="a948c-132">0</span><span class="sxs-lookup"><span data-stu-id="a948c-132">0</span></span>|<span data-ttu-id="a948c-133">1</span><span class="sxs-lookup"><span data-stu-id="a948c-133">1</span></span>|  
|<span data-ttu-id="a948c-134">0</span><span class="sxs-lookup"><span data-stu-id="a948c-134">0</span></span>|<span data-ttu-id="a948c-135">1</span><span class="sxs-lookup"><span data-stu-id="a948c-135">1</span></span>|<span data-ttu-id="a948c-136">1</span><span class="sxs-lookup"><span data-stu-id="a948c-136">1</span></span>|  
|<span data-ttu-id="a948c-137">0</span><span class="sxs-lookup"><span data-stu-id="a948c-137">0</span></span>|<span data-ttu-id="a948c-138">0</span><span class="sxs-lookup"><span data-stu-id="a948c-138">0</span></span>|<span data-ttu-id="a948c-139">0</span><span class="sxs-lookup"><span data-stu-id="a948c-139">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a948c-140">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a948c-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="a948c-141">Örneğin, 5 `Xor` 3, 6 ' dır.</span><span class="sxs-lookup"><span data-stu-id="a948c-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="a948c-142">Bunun neden olduğunu görmek için, 5 ve 3 ' ü ikili gösterimlerine, 101 ve 011 dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="a948c-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="a948c-143">Ardından önceki tabloyu kullanarak 101 XOR 011 'in 6 ondalık sayının ikili temsili olan 110 olduğunu öğrenin.</span><span class="sxs-lookup"><span data-stu-id="a948c-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="a948c-144">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="a948c-144">Data Types</span></span>  

 <span data-ttu-id="a948c-145">İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadeyi sayısal bir değere dönüştürür (– 1 `True` ve için 0 `False` ) ve bit düzeyinde bir işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a948c-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="a948c-146">Bir `Boolean` karşılaştırma için sonucun veri türü olur `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="a948c-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="a948c-147">Bit düzeyinde karşılaştırma için, sonuç veri türü ve veri türleri için uygun sayısal bir türdür `expression1` `expression2` .</span><span class="sxs-lookup"><span data-stu-id="a948c-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="a948c-148">[Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="a948c-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a948c-149">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="a948c-149">Overloading</span></span>  

 <span data-ttu-id="a948c-150">`Xor`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a948c-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a948c-151">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a948c-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="a948c-152">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a948c-152">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a948c-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="a948c-153">Example</span></span>  

 <span data-ttu-id="a948c-154">Aşağıdaki örnek, `Xor` iki ifadeye mantıksal dışlama (dışlamalı mantıksal ayırıcı) gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a948c-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="a948c-155">Sonuç, `Boolean` ifadelerden tam olarak bir tane olup olmadığını temsil eden bir değerdir `True` .</span><span class="sxs-lookup"><span data-stu-id="a948c-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="a948c-156">Önceki örnek `False` sırasıyla,, ve sonuçlarını üretir `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="a948c-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a948c-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="a948c-157">Example</span></span>  

 <span data-ttu-id="a948c-158">Aşağıdaki örnek, `Xor` iki sayısal ifadenin ayrı bitleri üzerinde mantıksal dışlama (dışlamalı mantıksal ayırıcı) gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a948c-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="a948c-159">Sonuç düzenindeki bit, işlenenlerde karşılık gelen bir bitlerin tam olarak 1 olarak ayarlanması halinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a948c-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="a948c-160">Önceki örnek sırasıyla 2, 12 ve 14 sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="a948c-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a948c-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a948c-161">See also</span></span>

- [<span data-ttu-id="a948c-162">Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a948c-162">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="a948c-163">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="a948c-163">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="a948c-164">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="a948c-164">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="a948c-165">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="a948c-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
