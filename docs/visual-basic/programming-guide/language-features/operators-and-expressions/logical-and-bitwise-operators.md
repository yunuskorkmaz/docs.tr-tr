---
title: "Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba48f722a11e93f82ae99aa407c3096a964e5ddd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a><span data-ttu-id="3a339-102">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="3a339-102">Logical and Bitwise Operators in Visual Basic</span></span>
<span data-ttu-id="3a339-103">Mantıksal işleçler karşılaştırmak `Boolean` ifadeleri ve return bir `Boolean` sonucu.</span><span class="sxs-lookup"><span data-stu-id="3a339-103">Logical operators compare `Boolean` expressions and return a `Boolean` result.</span></span> <span data-ttu-id="3a339-104">`And`, `Or`, `AndAlso`, `OrElse`, Ve `Xor` işleçler *ikili* iki işlenen alır çünkü while `Not` işlecidir *birli* tek bir işlenen aldığından.</span><span class="sxs-lookup"><span data-stu-id="3a339-104">The `And`, `Or`, `AndAlso`, `OrElse`, and `Xor` operators are *binary* because they take two operands, while the `Not` operator is *unary* because it takes a single operand.</span></span> <span data-ttu-id="3a339-105">Bu işleçlere bazıları tam sayı değerleri üzerinde bit tabanlı mantıksal işlemlerini de gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a339-105">Some of these operators can also perform bitwise logical operations on integral values.</span></span>  
  
## <a name="unary-logical-operator"></a><span data-ttu-id="3a339-106">Birli mantıksal işleç</span><span class="sxs-lookup"><span data-stu-id="3a339-106">Unary Logical Operator</span></span>  
 <span data-ttu-id="3a339-107">[Not işleci](../../../../visual-basic/language-reference/operators/not-operator.md) mantıksal gerçekleştirir *değilleme* üzerinde bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="3a339-107">The [Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md) performs logical *negation* on a `Boolean` expression.</span></span> <span data-ttu-id="3a339-108">Kendi işleneni mantıksal karşıtı verir.</span><span class="sxs-lookup"><span data-stu-id="3a339-108">It yields the logical opposite of its operand.</span></span> <span data-ttu-id="3a339-109">İfade değerlendirilirse `True`, ardından `Not` döndürür `False`; ifade değerlendirilirse `False`, ardından `Not` döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="3a339-109">If the expression evaluates to `True`, then `Not` returns `False`; if the expression evaluates to `False`, then `Not` returns `True`.</span></span> <span data-ttu-id="3a339-110">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3a339-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
## <a name="binary-logical-operators"></a><span data-ttu-id="3a339-111">İkili mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="3a339-111">Binary Logical Operators</span></span>  
 <span data-ttu-id="3a339-112">[Ve işleç](../../../../visual-basic/language-reference/operators/and-operator.md) mantıksal gerçekleştirir *birlikte* iki üzerinde `Boolean` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="3a339-112">The [And Operator](../../../../visual-basic/language-reference/operators/and-operator.md) performs logical *conjunction* on two `Boolean` expressions.</span></span> <span data-ttu-id="3a339-113">İçin her iki ifade değerlendirin varsa `True`, ardından `And` döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="3a339-113">If both expressions evaluate to `True`, then `And` returns `True`.</span></span> <span data-ttu-id="3a339-114">En az bir ifadenin değerlendirilirse `False`, ardından `And` döndürür `False`.</span><span class="sxs-lookup"><span data-stu-id="3a339-114">If at least one of the expressions evaluates to `False`, then `And` returns `False`.</span></span>  
  
 <span data-ttu-id="3a339-115">[Veya işleci](../../../../visual-basic/language-reference/operators/or-operator.md) mantıksal gerçekleştirir *ayrım* veya *ekleme* iki üzerinde `Boolean` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="3a339-115">The [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) performs logical *disjunction* or *inclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="3a339-116">Ya da ifade değerlendirilirse `True`, veya her ikisi için değerlendirin `True`, ardından `Or` döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="3a339-116">If either expression evaluates to `True`, or both evaluate to `True`, then `Or` returns `True`.</span></span> <span data-ttu-id="3a339-117">Hiçbiri ifade değerlendirilirse `True`, `Or` döndürür `False`.</span><span class="sxs-lookup"><span data-stu-id="3a339-117">If neither expression evaluates to `True`, `Or` returns `False`.</span></span>  
  
 <span data-ttu-id="3a339-118">[Xor işleci](../../../../visual-basic/language-reference/operators/xor-operator.md) mantıksal gerçekleştirir *dışlama* iki üzerinde `Boolean` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="3a339-118">The [Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md) performs logical *exclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="3a339-119">Tam olarak bir ifade değerlendirilirse `True`, ancak ikisini, `Xor` döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="3a339-119">If exactly one expression evaluates to `True`, but not both, `Xor` returns `True`.</span></span> <span data-ttu-id="3a339-120">İçin her iki ifade değerlendirin varsa `True` veya her ikisi için değerlendirin `False`, `Xor` döndürür `False`.</span><span class="sxs-lookup"><span data-stu-id="3a339-120">If both expressions evaluate to `True` or both evaluate to `False`, `Xor` returns `False`.</span></span>  
  
 <span data-ttu-id="3a339-121">Aşağıdaki örnek gösterilmektedir `And`, `Or`, ve `Xor` işleçler.</span><span class="sxs-lookup"><span data-stu-id="3a339-121">The following example illustrates the `And`, `Or`, and `Xor` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]  
  
## <a name="short-circuiting-logical-operations"></a><span data-ttu-id="3a339-122">Kısa devre mantıksal işlemleri</span><span class="sxs-lookup"><span data-stu-id="3a339-122">Short-Circuiting Logical Operations</span></span>  
 <span data-ttu-id="3a339-123">[AndAlso işleci](../../../../visual-basic/language-reference/operators/andalso-operator.md) çok benzer `And` işleci, ayrıca mantıksal ve işlecini iki gerçekleştirir, `Boolean` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="3a339-123">The [AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md) is very similar to the `And` operator, in that it also performs logical conjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="3a339-124">İkisi arasındaki temel fark `AndAlso` sergiler *kısa devre* davranışı.</span><span class="sxs-lookup"><span data-stu-id="3a339-124">The key difference between the two is that `AndAlso` exhibits *short-circuiting* behavior.</span></span> <span data-ttu-id="3a339-125">İlk ifadesinde bir `AndAlso` ifadeyi hesaplar için `False`, sonra da nihai sonucu değiştirilemiyor çünkü ikinci ifade değerlendirilmez ve `AndAlso` döndürür `False`.</span><span class="sxs-lookup"><span data-stu-id="3a339-125">If the first expression in an `AndAlso` expression evaluates to `False`, then the second expression is not evaluated because it cannot alter the final result, and `AndAlso` returns `False`.</span></span>  
  
 <span data-ttu-id="3a339-126">Benzer şekilde, [OrElse işleci](../../../../visual-basic/language-reference/operators/orelse-operator.md) kısa devre mantıksal veya işlecini iki gerçekleştirir `Boolean` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="3a339-126">Similarly, the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md) performs short-circuiting logical disjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="3a339-127">İlk ifadesinde bir `OrElse` ifadeyi hesaplar için `True`, sonra da nihai sonucu değiştirilemiyor çünkü ikinci ifade değerlendirilmez ve `OrElse` döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="3a339-127">If the first expression in an `OrElse` expression evaluates to `True`, then the second expression is not evaluated because it cannot alter the final result, and `OrElse` returns `True`.</span></span>  
  
### <a name="short-circuiting-trade-offs"></a><span data-ttu-id="3a339-128">Dengelemeler kısa devre</span><span class="sxs-lookup"><span data-stu-id="3a339-128">Short-Circuiting Trade-Offs</span></span>  
 <span data-ttu-id="3a339-129">Kısa devre mantıksal işleminin sonucu değiştirilemiyor bir ifade değerlendirerek değil performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="3a339-129">Short-circuiting can improve performance by not evaluating an expression that cannot alter the result of the logical operation.</span></span> <span data-ttu-id="3a339-130">Ancak, bu deyim ek eylemler gerçekleştiriyorsa, bu eylemleri bir kısa devre atlar.</span><span class="sxs-lookup"><span data-stu-id="3a339-130">However, if that expression performs additional actions, short-circuiting skips those actions.</span></span> <span data-ttu-id="3a339-131">İfade için bir çağrı içeriyorsa, örneğin, bir `Function` yordamı, yordam ifade kısa devre yapılma ise ve herhangi bir ek kod bulunan çağrılmaz `Function` çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="3a339-131">For example, if the expression includes a call to a `Function` procedure, that procedure is not called if the expression is short-circuited, and any additional code contained in the `Function` does not run.</span></span> <span data-ttu-id="3a339-132">Bu nedenle, işlevi yalnızca bazı durumlarda çalışabilir ve doğru bir şekilde test edilmelidir değil.</span><span class="sxs-lookup"><span data-stu-id="3a339-132">Therefore, the function might run only occasionally, and might not be tested correctly.</span></span> <span data-ttu-id="3a339-133">Veya program mantığı kodda bağlı `Function`.</span><span class="sxs-lookup"><span data-stu-id="3a339-133">Or the program logic might depend on the code in the `Function`.</span></span>  
  
 <span data-ttu-id="3a339-134">Aşağıdaki örnek arasındaki fark gösterilmektedir `And`, `Or`ve short-circuiting'dekiler.</span><span class="sxs-lookup"><span data-stu-id="3a339-134">The following example illustrates the difference between `And`, `Or`, and their short-circuiting counterparts.</span></span>  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]  
  
 <span data-ttu-id="3a339-135">Önceki örnekte unutmayın bazı önemli kod içinde `checkIfValid()` çağrı kısa devre yapılma olduğunda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="3a339-135">In the preceding example, note that some important code inside `checkIfValid()` does not run when the call is short-circuited.</span></span> <span data-ttu-id="3a339-136">İlk `If` deyimi çağrıları `checkIfValid()` olsa bile `12 > 45` döndürür `False`, çünkü `And` değil kısa devre oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3a339-136">The first `If` statement calls `checkIfValid()` even though `12 > 45` returns `False`, because `And` does not short-circuit.</span></span> <span data-ttu-id="3a339-137">İkinci `If` deyimi çağırmaz `checkIfValid()`, çünkü zaman `12 > 45` döndürür `False`, `AndAlso` ikinci ifade short-circuits.</span><span class="sxs-lookup"><span data-stu-id="3a339-137">The second `If` statement does not call `checkIfValid()`, because when `12 > 45` returns `False`, `AndAlso` short-circuits the second expression.</span></span> <span data-ttu-id="3a339-138">Üçüncü `If` deyimi çağrıları `checkIfValid()` olsa bile `12 < 45` döndürür `True`, çünkü `Or` değil kısa devre oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3a339-138">The third `If` statement calls `checkIfValid()` even though `12 < 45` returns `True`, because `Or` does not short-circuit.</span></span> <span data-ttu-id="3a339-139">Dördüncü `If` deyimi çağırmaz `checkIfValid()`, çünkü zaman `12 < 45` döndürür `True`, `OrElse` ikinci ifade short-circuits.</span><span class="sxs-lookup"><span data-stu-id="3a339-139">The fourth `If` statement does not call `checkIfValid()`, because when `12 < 45` returns `True`, `OrElse` short-circuits the second expression.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="3a339-140">Bit düzeyinde işlemler</span><span class="sxs-lookup"><span data-stu-id="3a339-140">Bitwise Operations</span></span>  
 <span data-ttu-id="3a339-141">Bit düzeyinde işlemler ikili (2 tabanı) formunda iki tamsayı değerleri değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="3a339-141">Bitwise operations evaluate two integral values in binary (base 2) form.</span></span> <span data-ttu-id="3a339-142">Bunlar, karşılık gelen konumlarda BITS karşılaştırın ve karşılaştırma üzerine dayalı değerler atayın.</span><span class="sxs-lookup"><span data-stu-id="3a339-142">They compare the bits at corresponding positions and then assign values based on the comparison.</span></span> <span data-ttu-id="3a339-143">Aşağıdaki örnek gösterilmektedir `And` işleci.</span><span class="sxs-lookup"><span data-stu-id="3a339-143">The following example illustrates the `And` operator.</span></span>  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]  
  
 <span data-ttu-id="3a339-144">Önceki örnekte değerini ayarlar `x` 1.</span><span class="sxs-lookup"><span data-stu-id="3a339-144">The preceding example sets the value of `x` to 1.</span></span> <span data-ttu-id="3a339-145">Bu şu nedenlerden dolayı gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="3a339-145">This happens for the following reasons:</span></span>  
  
-   <span data-ttu-id="3a339-146">Değerleri, binary olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="3a339-146">The values are treated as binary:</span></span>  
  
     <span data-ttu-id="3a339-147">ikili biçimde 3 011 =</span><span class="sxs-lookup"><span data-stu-id="3a339-147">3 in binary form = 011</span></span>  
  
     <span data-ttu-id="3a339-148">ikili biçimde 5 101 =</span><span class="sxs-lookup"><span data-stu-id="3a339-148">5 in binary form = 101</span></span>  
  
-   <span data-ttu-id="3a339-149">`And` İşleci ikili temsili bir ikili konum (bit) aynı anda karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="3a339-149">The `And` operator compares the binary representations, one binary position (bit) at a time.</span></span> <span data-ttu-id="3a339-150">Verilen konumda bitlerin her ikisi de 1 ise, 1, bu konumda sonucu yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3a339-150">If both bits at a given position are 1, then a 1 is placed in that position in the result.</span></span> <span data-ttu-id="3a339-151">Her iki bit 0 ise, 0, bu konumda sonucu yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3a339-151">If either bit is 0, then a 0 is placed in that position in the result.</span></span> <span data-ttu-id="3a339-152">Önceki örnekte bu gibi üretir:</span><span class="sxs-lookup"><span data-stu-id="3a339-152">In the preceding example this works out as follows:</span></span>  
  
     <span data-ttu-id="3a339-153">011 (3 ikili biçimde)</span><span class="sxs-lookup"><span data-stu-id="3a339-153">011 (3 in binary form)</span></span>  
  
     <span data-ttu-id="3a339-154">101 (5 ikili biçimde)</span><span class="sxs-lookup"><span data-stu-id="3a339-154">101 (5 in binary form)</span></span>  
  
     <span data-ttu-id="3a339-155">001 (ikili formunda, sonuç)</span><span class="sxs-lookup"><span data-stu-id="3a339-155">001 (The result, in binary form)</span></span>  
  
-   <span data-ttu-id="3a339-156">Sonuç ondalık olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3a339-156">The result is treated as decimal.</span></span> <span data-ttu-id="3a339-157">Değerin 001 ikili 1, bu nedenle gösterimidir `x` = 1.</span><span class="sxs-lookup"><span data-stu-id="3a339-157">The value 001 is the binary representation of 1, so `x` = 1.</span></span>  
  
 <span data-ttu-id="3a339-158">Bit düzeyinde `Or` işlem olduğunu benzer, birini veya ikisini karşılaştırılan BITS 1 ise 1 sonuç bit atanan dışında.</span><span class="sxs-lookup"><span data-stu-id="3a339-158">The bitwise `Or` operation is similar, except that a 1 is assigned to the result bit if either or both of the compared bits is 1.</span></span> <span data-ttu-id="3a339-159">`Xor`Karşılaştırılan BITS (ikisini) tam olarak birine 1 ise 1 sonuç bit atar.</span><span class="sxs-lookup"><span data-stu-id="3a339-159">`Xor` assigns a 1 to the result bit if exactly one of the compared bits (not both) is 1.</span></span> <span data-ttu-id="3a339-160">`Not`tek bir işlenen alır ve oturum bit dahil olmak üzere tüm BITS tersine çevirir ve bu değeri sonuca atar.</span><span class="sxs-lookup"><span data-stu-id="3a339-160">`Not` takes a single operand and inverts all the bits, including the sign bit, and assigns that value to the result.</span></span> <span data-ttu-id="3a339-161">Bu için pozitif sayılar imzalı anlamına gelir `Not` her zaman negatif bir değer döndürür ve negatif sayıları için `Not` her zaman bir pozitif veya sıfır değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a339-161">This means that for signed positive numbers, `Not` always returns a negative value, and for negative numbers, `Not` always returns a positive or zero value.</span></span>  
  
 <span data-ttu-id="3a339-162">`AndAlso` Ve `OrElse` işleçler bit düzeyinde işlemler desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3a339-162">The `AndAlso` and `OrElse` operators do not support bitwise operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a339-163">Bit düzeyinde işlemler yalnızca tam sayı türleri üzerinde gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3a339-163">Bitwise operations can be performed on integral types only.</span></span> <span data-ttu-id="3a339-164">Bit düzeyinde işlemi devam etmeden önce kayan nokta değerlerine tam sayı türleri dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a339-164">Floating-point values must be converted to integral types before bitwise operation can proceed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a339-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a339-165">See Also</span></span>  
 [<span data-ttu-id="3a339-166">Mantıksal ve bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a339-166">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="3a339-167">Boole ifadeleri</span><span class="sxs-lookup"><span data-stu-id="3a339-167">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="3a339-168">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="3a339-168">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="3a339-169">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="3a339-169">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="3a339-170">Visual Basic'de birleştirme işleçleri</span><span class="sxs-lookup"><span data-stu-id="3a339-170">Concatenation Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [<span data-ttu-id="3a339-171">İşleçlerin etkili bileşimi</span><span class="sxs-lookup"><span data-stu-id="3a339-171">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
