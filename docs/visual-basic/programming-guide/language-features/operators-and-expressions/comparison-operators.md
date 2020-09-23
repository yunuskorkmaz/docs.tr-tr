---
title: Karşılaştırma İşleçleri
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: fbe81532bb435e54e694f9b5fe9dd497392f31e1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071774"
---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="43918-102">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="43918-102">Comparison Operators in Visual Basic</span></span>

<span data-ttu-id="43918-103">Karşılaştırma işleçleri iki ifadeyi karşılaştırır ve `Boolean` değerlerinin ilişkisini temsil eden bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="43918-103">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="43918-104">Sayısal değerleri karşılaştırma işleçleri, dizeleri karşılaştırmak için İşleçleri ve nesneleri karşılaştırmak için işleçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="43918-104">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="43918-105">Üç tür işlecin hepsi burada açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="43918-105">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="43918-106">Sayısal değerleri karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="43918-106">Comparing Numeric Values</span></span>  

 <span data-ttu-id="43918-107">Visual Basic altı sayısal karşılaştırma işlecini kullanarak sayısal değerleri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="43918-107">Visual Basic compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="43918-108">Her operatör, işlenen iki ifade olarak sayısal değerler değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="43918-108">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="43918-109">Aşağıdaki tablo işleçleri listeler ve bunların örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="43918-109">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="43918-110">Operatör</span><span class="sxs-lookup"><span data-stu-id="43918-110">Operator</span></span>|<span data-ttu-id="43918-111">Durum test edildi</span><span class="sxs-lookup"><span data-stu-id="43918-111">Condition tested</span></span>|<span data-ttu-id="43918-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="43918-112">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="43918-113">`=` Eþit</span><span class="sxs-lookup"><span data-stu-id="43918-113">`=` (Equality)</span></span>|<span data-ttu-id="43918-114">İkincinin değerine eşit olan ilk ifadenin değeri mi?</span><span class="sxs-lookup"><span data-stu-id="43918-114">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="43918-115">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="43918-115">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="43918-116">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="43918-116">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="43918-117">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="43918-117">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="43918-118">`<>` Olmama</span><span class="sxs-lookup"><span data-stu-id="43918-118">`<>` (Inequality)</span></span>|<span data-ttu-id="43918-119">İlk ifadenin değeri ikincinin değerine eşit değil mi?</span><span class="sxs-lookup"><span data-stu-id="43918-119">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="43918-120">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="43918-120">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="43918-121">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="43918-121">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="43918-122">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="43918-122">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="43918-123">`<` (Küçüktür)</span><span class="sxs-lookup"><span data-stu-id="43918-123">`<` (Less than)</span></span>|<span data-ttu-id="43918-124">İlk ifadenin değeri ikinciden küçük mi?</span><span class="sxs-lookup"><span data-stu-id="43918-124">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="43918-125">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="43918-125">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="43918-126">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="43918-126">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="43918-127">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="43918-127">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="43918-128">`>` (Büyüktür)</span><span class="sxs-lookup"><span data-stu-id="43918-128">`>` (Greater than)</span></span>|<span data-ttu-id="43918-129">İkincisinin değerinden büyük olan ilk ifadenin değeri mi?</span><span class="sxs-lookup"><span data-stu-id="43918-129">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="43918-130">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="43918-130">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="43918-131">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="43918-131">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="43918-132">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="43918-132">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="43918-133">`<=` (Küçüktür veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="43918-133">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="43918-134">İlk ifadenin değeri ikinciden küçük veya ona eşit mi?</span><span class="sxs-lookup"><span data-stu-id="43918-134">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="43918-135">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="43918-135">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="43918-136">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="43918-136">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="43918-137">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="43918-137">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="43918-138">`>=` (Büyüktür veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="43918-138">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="43918-139">İlk ifadenin değeri ikinciden büyük veya ona eşit mi?</span><span class="sxs-lookup"><span data-stu-id="43918-139">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="43918-140">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="43918-140">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="43918-141">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="43918-141">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="43918-142">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="43918-142">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="43918-143">Dizeleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="43918-143">Comparing Strings</span></span>  

 <span data-ttu-id="43918-144">Visual Basic, dizeleri [benzer işleci](../../../language-reference/operators/like-operator.md) ve sayısal karşılaştırma işleçleri ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="43918-144">Visual Basic compares strings using the [Like Operator](../../../language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="43918-145">`Like`İşleci, bir model belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="43918-145">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="43918-146">Daha sonra dize, bu düzene göre karşılaştırılır ve eşleşiyorsa sonuç olur `True` .</span><span class="sxs-lookup"><span data-stu-id="43918-146">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="43918-147">Aksi takdirde, sonuç olur `False` .</span><span class="sxs-lookup"><span data-stu-id="43918-147">Otherwise, the result is `False`.</span></span> <span data-ttu-id="43918-148">Sayısal işleçler, `String` Aşağıdaki örnekte gösterildiği gibi, değerlerini sıralama sıralarına göre karşılaştırmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="43918-148">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="43918-149">Önceki örnekteki sonuç, `True` ilk dizedeki ilk karakter ikinci dizedeki ilk karakterden önce sıralandığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="43918-149">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="43918-150">İlk karakter eşitse, karşılaştırma her iki dizelerde de bir sonraki karaktere devam eder ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="43918-150">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="43918-151">Ayrıca, aşağıdaki örnekte gösterildiği gibi, eşitlik işlecini kullanarak dizelerin eşitliğini test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43918-151">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="43918-152">Bir dize diğerinin ön eki ise (örneğin, "AA" ve "aaa"), daha uzun dize, daha kısa dizeden daha büyük olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="43918-152">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="43918-153">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="43918-153">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="43918-154">Sıralama düzeni, ayarına bağlı olarak bir ikili karşılaştırmaya veya metinsel karşılaştırmaya göre belirlenir `Option Compare` .</span><span class="sxs-lookup"><span data-stu-id="43918-154">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="43918-155">Daha fazla bilgi için bkz. [Option Compare deyimleri](../../../language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="43918-155">For more information see [Option Compare Statement](../../../language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="43918-156">Nesneleri karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="43918-156">Comparing Objects</span></span>  

 <span data-ttu-id="43918-157">Visual Basic, iki nesne başvuru değişkenini [,, işleç](../../../language-reference/operators/is-operator.md) ve [IsNot işleci](../../../language-reference/operators/isnot-operator.md)ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="43918-157">Visual Basic compares two object reference variables with the [Is Operator](../../../language-reference/operators/is-operator.md) and the [IsNot Operator](../../../language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="43918-158">İki başvuru değişkeninin aynı nesne örneğine başvuruda bulunduğunu anlamak için bu işleçlerden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43918-158">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="43918-159">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="43918-159">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 <span data-ttu-id="43918-160">Yukarıdaki örnekte,, `x Is y` `True` her iki değişken de aynı örneğe başvurduğundan olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="43918-160">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="43918-161">Bu sonucu aşağıdaki örnekle karşıtın.</span><span class="sxs-lookup"><span data-stu-id="43918-161">Contrast this result with the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 <span data-ttu-id="43918-162">Önceki örnekte, `x Is y` olarak değerlendirilir `False` , çünkü değişkenler aynı türdeki nesnelere başvurmakla birlikte, bu tür farklı örneklere başvururlar.</span><span class="sxs-lookup"><span data-stu-id="43918-162">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="43918-163">Aynı örneğe işaret eden iki nesne için test etmek istediğinizde, `IsNot` işleç, ve ' nin dilbilgisi ve birleşimini önlemenize olanak sağlar `Not` `Is` .</span><span class="sxs-lookup"><span data-stu-id="43918-163">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="43918-164">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="43918-164">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 <span data-ttu-id="43918-165">Yukarıdaki örnekte, `If a IsNot b` öğesine eşdeğerdir `If Not a Is b` .</span><span class="sxs-lookup"><span data-stu-id="43918-165">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="43918-166">Nesne türünü karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="43918-166">Comparing Object Type</span></span>  

 <span data-ttu-id="43918-167">Bir nesnenin `TypeOf` ... ifadesiyle belirli bir türde olup olmadığını test edebilirsiniz `Is` .</span><span class="sxs-lookup"><span data-stu-id="43918-167">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="43918-168">Söz dizimi şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="43918-168">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="43918-169">`typename`Bir arabirim türü belirttiğinde, `TypeOf` `Is` `True` nesne arabirim türünü uygularsa... ifadesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="43918-169">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="43918-170">`typename`, Bir sınıf türü olduğunda, `True` nesne belirtilen sınıfın bir örneği veya belirtilen sınıftan türetilen bir sınıf ise, ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="43918-170">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="43918-171">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="43918-171">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 <span data-ttu-id="43918-172">Önceki örnekte, `TypeOf x Is Control` ifadesi, `True` `x` `Button` ' den devralan, türü olduğu için olarak değerlendirilir `Control` .</span><span class="sxs-lookup"><span data-stu-id="43918-172">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="43918-173">Daha fazla bilgi için bkz. [typeof işleci](../../../language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="43918-173">For more information, see [TypeOf Operator](../../../language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43918-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43918-174">See also</span></span>

- [<span data-ttu-id="43918-175">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="43918-175">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="43918-176">Karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="43918-176">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="43918-177">İşleçler</span><span class="sxs-lookup"><span data-stu-id="43918-177">Operators</span></span>](../../../language-reference/operators/index.md)
- [<span data-ttu-id="43918-178">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="43918-178">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="43918-179">Visual Basic'de Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="43918-179">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="43918-180">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="43918-180">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
