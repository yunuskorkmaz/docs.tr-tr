---
description: 'Daha fazla bilgi için Visual Basic: mantıksal ve bit düzeyinde Işleçler'
title: Mantıksal ve Bit Düzeyinde İşleçler
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: 55d9567813a9114573e1e3f70fe181cb8621b350
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472728"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a><span data-ttu-id="b0598-103">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="b0598-103">Logical and Bitwise Operators in Visual Basic</span></span>

<span data-ttu-id="b0598-104">Mantıksal işleçler `Boolean` ifadeleri karşılaştırır ve bir `Boolean` sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="b0598-104">Logical operators compare `Boolean` expressions and return a `Boolean` result.</span></span> <span data-ttu-id="b0598-105">`And`,, `Or` , `AndAlso` `OrElse` Ve `Xor` işleçleri iki işlenen kullandığından,  `Not` tek bir işlenen aldığı için işleç *tekil* olduğu için ikili bir dosyaysa.</span><span class="sxs-lookup"><span data-stu-id="b0598-105">The `And`, `Or`, `AndAlso`, `OrElse`, and `Xor` operators are *binary* because they take two operands, while the `Not` operator is *unary* because it takes a single operand.</span></span> <span data-ttu-id="b0598-106">Bu işleçlerden bazıları, tam sayı değerlerinde bit düzeyinde mantıksal işlemler de gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="b0598-106">Some of these operators can also perform bitwise logical operations on integral values.</span></span>  
  
## <a name="unary-logical-operator"></a><span data-ttu-id="b0598-107">Birli mantıksal Işleç</span><span class="sxs-lookup"><span data-stu-id="b0598-107">Unary Logical Operator</span></span>  

 <span data-ttu-id="b0598-108">[Not işleci](../../../language-reference/operators/not-operator.md) bir ifadede mantıksal *değilleme* gerçekleştirir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b0598-108">The [Not Operator](../../../language-reference/operators/not-operator.md) performs logical *negation* on a `Boolean` expression.</span></span> <span data-ttu-id="b0598-109">İşleneni, işleneninin mantıksal tersini verir.</span><span class="sxs-lookup"><span data-stu-id="b0598-109">It yields the logical opposite of its operand.</span></span> <span data-ttu-id="b0598-110">İfade olarak değerlendirilirse,, `True` `Not` `False` ifadesi olarak değerlendirilirse, öğesini döndürür `False` `Not` `True` .</span><span class="sxs-lookup"><span data-stu-id="b0598-110">If the expression evaluates to `True`, then `Not` returns `False`; if the expression evaluates to `False`, then `Not` returns `True`.</span></span> <span data-ttu-id="b0598-111">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b0598-111">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a><span data-ttu-id="b0598-112">İkili mantıksal Işleçler</span><span class="sxs-lookup"><span data-stu-id="b0598-112">Binary Logical Operators</span></span>  

 <span data-ttu-id="b0598-113">[And işleci](../../../language-reference/operators/and-operator.md) iki ifade üzerinde mantıksal bir *birlikte* gerçekleştirir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b0598-113">The [And Operator](../../../language-reference/operators/and-operator.md) performs logical *conjunction* on two `Boolean` expressions.</span></span> <span data-ttu-id="b0598-114">Her iki ifade olarak değerlendirilir `True` , öğesini `And` döndürür `True` .</span><span class="sxs-lookup"><span data-stu-id="b0598-114">If both expressions evaluate to `True`, then `And` returns `True`.</span></span> <span data-ttu-id="b0598-115">Deyimlerden en az biri olarak değerlendirilirse, öğesini `False` `And` döndürür `False` .</span><span class="sxs-lookup"><span data-stu-id="b0598-115">If at least one of the expressions evaluates to `False`, then `And` returns `False`.</span></span>  
  
 <span data-ttu-id="b0598-116">[OR işleci](../../../language-reference/operators/or-operator.md) , mantıksal *ayırıcı* veya iki ifadeye *dahil* etme işlemini gerçekleştirir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b0598-116">The [Or Operator](../../../language-reference/operators/or-operator.md) performs logical *disjunction* or *inclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="b0598-117">İki ifade olarak değerlendirilirse `True` veya her ikisi de olarak değerlendirilirse, öğesini `True` `Or` döndürür `True` .</span><span class="sxs-lookup"><span data-stu-id="b0598-117">If either expression evaluates to `True`, or both evaluate to `True`, then `Or` returns `True`.</span></span> <span data-ttu-id="b0598-118">Hiçbir ifadenin olarak değerlendiriliyorsa `True` , `Or` döndürür `False` .</span><span class="sxs-lookup"><span data-stu-id="b0598-118">If neither expression evaluates to `True`, `Or` returns `False`.</span></span>  
  
 <span data-ttu-id="b0598-119">[Xor işleci](../../../language-reference/operators/xor-operator.md) iki ifadeye mantıksal *dışlama* gerçekleştirir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b0598-119">The [Xor Operator](../../../language-reference/operators/xor-operator.md) performs logical *exclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="b0598-120">Tam olarak bir ifade olarak değerlendirilir `True` , ancak her ikisini de değil, `Xor` döndürür `True` .</span><span class="sxs-lookup"><span data-stu-id="b0598-120">If exactly one expression evaluates to `True`, but not both, `Xor` returns `True`.</span></span> <span data-ttu-id="b0598-121">Her iki ifade de olarak değerlendirilir `True` veya her ikisini de olarak değerlendirir `False` , `Xor` döndürür `False` .</span><span class="sxs-lookup"><span data-stu-id="b0598-121">If both expressions evaluate to `True` or both evaluate to `False`, `Xor` returns `False`.</span></span>  
  
 <span data-ttu-id="b0598-122">Aşağıdaki örnekte `And` ,, `Or` ve işleçleri gösterilmektedir `Xor` .</span><span class="sxs-lookup"><span data-stu-id="b0598-122">The following example illustrates the `And`, `Or`, and `Xor` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a><span data-ttu-id="b0598-123">Short-Circuiting mantıksal Işlemler</span><span class="sxs-lookup"><span data-stu-id="b0598-123">Short-Circuiting Logical Operations</span></span>  

 <span data-ttu-id="b0598-124">[AndAlso işleci](../../../language-reference/operators/andalso-operator.md) , `And` işleçle çok benzerdir, bu da iki ifadeye de mantıksal bir işlem yapar `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b0598-124">The [AndAlso Operator](../../../language-reference/operators/andalso-operator.md) is very similar to the `And` operator, in that it also performs logical conjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="b0598-125">İkisi arasındaki temel fark, kısa devre uygulayan `AndAlso` davranışı  gösteriyor.</span><span class="sxs-lookup"><span data-stu-id="b0598-125">The key difference between the two is that `AndAlso` exhibits *short-circuiting* behavior.</span></span> <span data-ttu-id="b0598-126">Bir ifadedeki ilk ifade `AndAlso` olarak değerlendirilirse `False` , ikinci ifade nihai sonucu değiştirmediği ve döndürdüğü için değerlendirilmez `AndAlso` `False` .</span><span class="sxs-lookup"><span data-stu-id="b0598-126">If the first expression in an `AndAlso` expression evaluates to `False`, then the second expression is not evaluated because it cannot alter the final result, and `AndAlso` returns `False`.</span></span>  
  
 <span data-ttu-id="b0598-127">Benzer şekilde, [OrElse işleci](../../../language-reference/operators/orelse-operator.md) iki ifadeye kısa devre uygulayan mantıksal bir birleşim uygular `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b0598-127">Similarly, the [OrElse Operator](../../../language-reference/operators/orelse-operator.md) performs short-circuiting logical disjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="b0598-128">Bir ifadedeki ilk ifade `OrElse` olarak değerlendirilirse `True` , ikinci ifade nihai sonucu değiştirmediği ve döndürdüğü için değerlendirilmez `OrElse` `True` .</span><span class="sxs-lookup"><span data-stu-id="b0598-128">If the first expression in an `OrElse` expression evaluates to `True`, then the second expression is not evaluated because it cannot alter the final result, and `OrElse` returns `True`.</span></span>  
  
### <a name="short-circuiting-trade-offs"></a><span data-ttu-id="b0598-129">Short-Circuiting Trade-Offs</span><span class="sxs-lookup"><span data-stu-id="b0598-129">Short-Circuiting Trade-Offs</span></span>  

 <span data-ttu-id="b0598-130">Kısa devre uygulayan, mantıksal işlemin sonucunu değiştirebilecek bir ifadeyi değerlendirmeden performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="b0598-130">Short-circuiting can improve performance by not evaluating an expression that cannot alter the result of the logical operation.</span></span> <span data-ttu-id="b0598-131">Ancak, bu ifade ek eylemler gerçekleştirdiğinde, kısa devre uygulayan bu eylemleri atlar.</span><span class="sxs-lookup"><span data-stu-id="b0598-131">However, if that expression performs additional actions, short-circuiting skips those actions.</span></span> <span data-ttu-id="b0598-132">Örneğin, ifade bir yordama çağrı içeriyorsa `Function` , ifade kısa devre dışı ise ve içinde yer alan ek kodlar çalıştırılsa, bu yordam çağrılmaz `Function` .</span><span class="sxs-lookup"><span data-stu-id="b0598-132">For example, if the expression includes a call to a `Function` procedure, that procedure is not called if the expression is short-circuited, and any additional code contained in the `Function` does not run.</span></span> <span data-ttu-id="b0598-133">Bu nedenle, işlev yalnızca belirli bir zaman çalışabilir ve doğru şekilde sınanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b0598-133">Therefore, the function might run only occasionally, and might not be tested correctly.</span></span> <span data-ttu-id="b0598-134">Ya da program mantığı içindeki koda bağlı olabilirler `Function` .</span><span class="sxs-lookup"><span data-stu-id="b0598-134">Or the program logic might depend on the code in the `Function`.</span></span>  
  
 <span data-ttu-id="b0598-135">Aşağıdaki örnek `And` ,, `Or` ve bunların kısa devre dışı karşılıkları arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0598-135">The following example illustrates the difference between `And`, `Or`, and their short-circuiting counterparts.</span></span>  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 <span data-ttu-id="b0598-136">Yukarıdaki örnekte, `checkIfValid()` çağrı kısa devre dışı olduğunda, içindeki bazı önemli kodların çalıştırılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b0598-136">In the preceding example, note that some important code inside `checkIfValid()` does not run when the call is short-circuited.</span></span> <span data-ttu-id="b0598-137">İlk `If` ifade çağrı yapmaz `checkIfValid()` , ancak `12 > 45` `False` `And` kısa devre dışı değildir.</span><span class="sxs-lookup"><span data-stu-id="b0598-137">The first `If` statement calls `checkIfValid()` even though `12 > 45` returns `False`, because `And` does not short-circuit.</span></span> <span data-ttu-id="b0598-138">İkinci `If` deyim çağırmaz `checkIfValid()` , çünkü `12 > 45` döndürür, `False` `AndAlso` kısa devreler ikinci ifadedir.</span><span class="sxs-lookup"><span data-stu-id="b0598-138">The second `If` statement does not call `checkIfValid()`, because when `12 > 45` returns `False`, `AndAlso` short-circuits the second expression.</span></span> <span data-ttu-id="b0598-139">`If`Kısa devre olmadığından, üçüncü ifade çağrıları `checkIfValid()` `12 < 45` döndürür `True` `Or` .</span><span class="sxs-lookup"><span data-stu-id="b0598-139">The third `If` statement calls `checkIfValid()` even though `12 < 45` returns `True`, because `Or` does not short-circuit.</span></span> <span data-ttu-id="b0598-140">Dördüncü `If` deyim çağrı yapmaz `checkIfValid()` , çünkü `12 < 45` döndürür, `True` `OrElse` kısa devreler ikinci ifadedir.</span><span class="sxs-lookup"><span data-stu-id="b0598-140">The fourth `If` statement does not call `checkIfValid()`, because when `12 < 45` returns `True`, `OrElse` short-circuits the second expression.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="b0598-141">Bit düzeyinde Işlemler</span><span class="sxs-lookup"><span data-stu-id="b0598-141">Bitwise Operations</span></span>  

 <span data-ttu-id="b0598-142">Bit düzeyinde işlemler ikili (taban 2) formda iki integral değeri değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b0598-142">Bitwise operations evaluate two integral values in binary (base 2) form.</span></span> <span data-ttu-id="b0598-143">Bunlara karşılık gelen konumlarda bitleri karşılaştırırlar ve sonra karşılaştırmaya göre değerler atar.</span><span class="sxs-lookup"><span data-stu-id="b0598-143">They compare the bits at corresponding positions and then assign values based on the comparison.</span></span> <span data-ttu-id="b0598-144">Aşağıdaki örnekte `And` işleç gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b0598-144">The following example illustrates the `And` operator.</span></span>  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 <span data-ttu-id="b0598-145">Önceki örnek değerini `x` 1 olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b0598-145">The preceding example sets the value of `x` to 1.</span></span> <span data-ttu-id="b0598-146">Bu durum aşağıdaki nedenlerden dolayı gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="b0598-146">This happens for the following reasons:</span></span>  
  
- <span data-ttu-id="b0598-147">Değerler ikili olarak değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="b0598-147">The values are treated as binary:</span></span>  
  
     <span data-ttu-id="b0598-148">3 ikili biçiminde 3 = 011</span><span class="sxs-lookup"><span data-stu-id="b0598-148">3 in binary form = 011</span></span>  
  
     <span data-ttu-id="b0598-149">5 ikili biçimi = 101</span><span class="sxs-lookup"><span data-stu-id="b0598-149">5 in binary form = 101</span></span>  
  
- <span data-ttu-id="b0598-150">İşleci, tek seferde bir `And` ikili konum (bit) ikili gösterimlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="b0598-150">The `And` operator compares the binary representations, one binary position (bit) at a time.</span></span> <span data-ttu-id="b0598-151">Belirli bir konumdaki bitlerin her ikisi de 1 ise, sonuçta bu konuma bir 1 konur.</span><span class="sxs-lookup"><span data-stu-id="b0598-151">If both bits at a given position are 1, then a 1 is placed in that position in the result.</span></span> <span data-ttu-id="b0598-152">Her iki bit de 0 ise, sonuçta bu konuma 0 yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b0598-152">If either bit is 0, then a 0 is placed in that position in the result.</span></span> <span data-ttu-id="b0598-153">Yukarıdaki örnekte bu, aşağıdaki gibi çalışmaktadır:</span><span class="sxs-lookup"><span data-stu-id="b0598-153">In the preceding example this works out as follows:</span></span>  
  
     <span data-ttu-id="b0598-154">011 (ikili biçimde 3)</span><span class="sxs-lookup"><span data-stu-id="b0598-154">011 (3 in binary form)</span></span>  
  
     <span data-ttu-id="b0598-155">101 (ikili biçimde 5)</span><span class="sxs-lookup"><span data-stu-id="b0598-155">101 (5 in binary form)</span></span>  
  
     <span data-ttu-id="b0598-156">001 (sonuç, ikili biçimde)</span><span class="sxs-lookup"><span data-stu-id="b0598-156">001 (The result, in binary form)</span></span>  
  
- <span data-ttu-id="b0598-157">Sonuç ondalık olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b0598-157">The result is treated as decimal.</span></span> <span data-ttu-id="b0598-158">001 değeri 1, bu nedenle = 1 ' in ikili gösterimidir `x` .</span><span class="sxs-lookup"><span data-stu-id="b0598-158">The value 001 is the binary representation of 1, so `x` = 1.</span></span>  
  
 <span data-ttu-id="b0598-159">Bit düzeyinde `Or` işlem benzerdir, ancak karşılaştırılan bitlerin biri veya her ikisi 1 ise sonuç bitine 1 atanır.</span><span class="sxs-lookup"><span data-stu-id="b0598-159">The bitwise `Or` operation is similar, except that a 1 is assigned to the result bit if either or both of the compared bits is 1.</span></span> <span data-ttu-id="b0598-160">`Xor` karşılaştırılan bitlerin (her ikisi de değil) tam olarak biri 1 ise, sonuç bitini 1 atar.</span><span class="sxs-lookup"><span data-stu-id="b0598-160">`Xor` assigns a 1 to the result bit if exactly one of the compared bits (not both) is 1.</span></span> <span data-ttu-id="b0598-161">`Not` tek bir işlenen alır ve işaret biti dahil olmak üzere tüm bitleri ters çevirir ve bu değeri sonuca atar.</span><span class="sxs-lookup"><span data-stu-id="b0598-161">`Not` takes a single operand and inverts all the bits, including the sign bit, and assigns that value to the result.</span></span> <span data-ttu-id="b0598-162">Bu, işaretli pozitif sayıların `Not` her zaman negatif bir değer döndüğü ve negatif sayıların `Not` her zaman pozitif veya sıfır değer döndürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b0598-162">This means that for signed positive numbers, `Not` always returns a negative value, and for negative numbers, `Not` always returns a positive or zero value.</span></span>  
  
 <span data-ttu-id="b0598-163">`AndAlso`Ve `OrElse` işleçleri bit düzeyinde işlemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b0598-163">The `AndAlso` and `OrElse` operators do not support bitwise operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0598-164">Bit düzeyinde işlemler yalnızca integral türlerinde gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b0598-164">Bitwise operations can be performed on integral types only.</span></span> <span data-ttu-id="b0598-165">Bit düzeyinde işlemin devam edebilmesi için kayan nokta değerlerinin tamsayı türlerine dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0598-165">Floating-point values must be converted to integral types before bitwise operation can proceed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0598-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0598-166">See also</span></span>

- [<span data-ttu-id="b0598-167">Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0598-167">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="b0598-168">Boole Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="b0598-168">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="b0598-169">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="b0598-169">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="b0598-170">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="b0598-170">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="b0598-171">Visual Basic'de Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="b0598-171">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="b0598-172">İşleçlerin Etkili Bileşimi</span><span class="sxs-lookup"><span data-stu-id="b0598-172">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
