---
title: "Visual Basic'de Karşılaştırma İşleçleri"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d8bf37ad30f410251f18aea6747734fc24d42cd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="59278-102">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="59278-102">Comparison Operators in Visual Basic</span></span>
<span data-ttu-id="59278-103">Karşılaştırma işleçleri iki ifadeye karşılaştırır ve dönüş bir `Boolean` değerlerine ilişkiyi gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="59278-103">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="59278-104">Sayısal değerler, dizeleri Karşılaştırma işleçleri ve nesneleri Karşılaştırma işleçleri Karşılaştırma işleçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="59278-104">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="59278-105">Üç tür işleçleri burada açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="59278-105">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="59278-106">Sayısal değerleri karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="59278-106">Comparing Numeric Values</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="59278-107">altı sayısal Karşılaştırma işleçleri kullanarak sayısal değerleri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="59278-107"> compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="59278-108">Her işleç sayısal değerlere değerlendirmek iki ifadeye işlenen alır.</span><span class="sxs-lookup"><span data-stu-id="59278-108">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="59278-109">Aşağıdaki tabloda işleçleri listeler ve her örnekler gösterir.</span><span class="sxs-lookup"><span data-stu-id="59278-109">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="59278-110">İşleç</span><span class="sxs-lookup"><span data-stu-id="59278-110">Operator</span></span>|<span data-ttu-id="59278-111">Test durumu</span><span class="sxs-lookup"><span data-stu-id="59278-111">Condition tested</span></span>|<span data-ttu-id="59278-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="59278-112">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="59278-113">`=`(Eşitlik)</span><span class="sxs-lookup"><span data-stu-id="59278-113">`=` (Equality)</span></span>|<span data-ttu-id="59278-114">İlk ifade değerini ikinci değerine mi?</span><span class="sxs-lookup"><span data-stu-id="59278-114">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="59278-115">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="59278-115">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="59278-116">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="59278-116">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="59278-117">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="59278-117">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="59278-118">`<>`(Eşitsizlik)</span><span class="sxs-lookup"><span data-stu-id="59278-118">`<>` (Inequality)</span></span>|<span data-ttu-id="59278-119">İlk ifade değeri ikinci değerine eşit mi?</span><span class="sxs-lookup"><span data-stu-id="59278-119">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="59278-120">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="59278-120">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="59278-121">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="59278-121">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="59278-122">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="59278-122">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="59278-123">`<`(Küçüktür)</span><span class="sxs-lookup"><span data-stu-id="59278-123">`<` (Less than)</span></span>|<span data-ttu-id="59278-124">İlk ifade değerden daha az saniye değerini mi?</span><span class="sxs-lookup"><span data-stu-id="59278-124">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="59278-125">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="59278-125">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="59278-126">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="59278-126">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="59278-127">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="59278-127">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="59278-128">`>`(Büyük)</span><span class="sxs-lookup"><span data-stu-id="59278-128">`>` (Greater than)</span></span>|<span data-ttu-id="59278-129">İlk ifade değeri ikinci değerinden büyük mü?</span><span class="sxs-lookup"><span data-stu-id="59278-129">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="59278-130">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="59278-130">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="59278-131">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="59278-131">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="59278-132">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="59278-132">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="59278-133">`<=`(Küçük veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="59278-133">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="59278-134">İlk ifade değeri ikinci değerine eşit veya daha az mi?</span><span class="sxs-lookup"><span data-stu-id="59278-134">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="59278-135">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="59278-135">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="59278-136">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="59278-136">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="59278-137">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="59278-137">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="59278-138">`>=`(Büyük veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="59278-138">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="59278-139">İlk ifade değeri ikinci değerine eşit veya daha büyük mi?</span><span class="sxs-lookup"><span data-stu-id="59278-139">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="59278-140">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="59278-140">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="59278-141">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="59278-141">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="59278-142">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="59278-142">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="59278-143">Dizeleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="59278-143">Comparing Strings</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="59278-144">kullanarak dizeleri karşılaştırır [gibi işleci](../../../../visual-basic/language-reference/operators/like-operator.md) sayısal Karşılaştırma işleçleri yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="59278-144"> compares strings using the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="59278-145">`Like` İşleci bir desen belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="59278-145">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="59278-146">Dize desenini karşı karşılaştırılır ve eşleşirse sonucudur `True`.</span><span class="sxs-lookup"><span data-stu-id="59278-146">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="59278-147">Aksi takdirde, sonuç değer `False`.</span><span class="sxs-lookup"><span data-stu-id="59278-147">Otherwise, the result is `False`.</span></span> <span data-ttu-id="59278-148">Sayısal işleçleri, karşılaştırmanızı sağlar `String` değerler aşağıdaki örnekte gösterildiği gibi sıralama düzeni üzerinde temel.</span><span class="sxs-lookup"><span data-stu-id="59278-148">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="59278-149">Önceki örnekte sonuç `True` ikinci dizedeki ilk karakter önce ilk dizedeki ilk karakter sıralar olduğundan.</span><span class="sxs-lookup"><span data-stu-id="59278-149">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="59278-150">İlk karakteri eşit olsaydı, karşılaştırma iki dize sonraki karakteri devam ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="59278-150">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="59278-151">Ayrıca aşağıdaki örnekte gösterildiği gibi eşitlik işleci kullanarak dizeleri eşitlik test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59278-151">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="59278-152">Başka bir önek "aa" ve "aaa" gibi bir dize ise, uzun dizeyi kısa dize büyük olması kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="59278-152">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="59278-153">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="59278-153">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="59278-154">İkili karşılaştırma ya da bir metinsel karşılaştırma ayarını bağlı olarak sıralama düzenini temel `Option Compare`.</span><span class="sxs-lookup"><span data-stu-id="59278-154">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="59278-155">Daha fazla bilgi için bkz: [Option Compare deyimi](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="59278-155">For more information see [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="59278-156">Nesneleri karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="59278-156">Comparing Objects</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="59278-157">karşılaştırır iki nesne başvuru değişkenlerle [Is işlecini](../../../../visual-basic/language-reference/operators/is-operator.md) ve [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span><span class="sxs-lookup"><span data-stu-id="59278-157"> compares two object reference variables with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="59278-158">Aynı nesne örneğini iki başvuru değişkenleri başvurduğundan belirlemek için bu işleçlere birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59278-158">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="59278-159">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="59278-159">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 <span data-ttu-id="59278-160">Önceki örnekte `x Is y` değerlendiren `True`, her iki değişken aynı örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="59278-160">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="59278-161">Aşağıdaki örnekte bu sonuçla karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="59278-161">Contrast this result with the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 <span data-ttu-id="59278-162">Önceki örnekte `x Is y` değerlendiren `False`, değişkenleri aynı türde nesnelere atıfta karşın, bu tür farklı örneklerine başvurduğundan.</span><span class="sxs-lookup"><span data-stu-id="59278-162">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="59278-163">İki nesnenin aynı örneğine işaret değil için test etmek istediğiniz zaman `IsNot` işleci dilbilgisi açısından biçimsiz bileşimini kaçının olanak tanır `Not` ve `Is`.</span><span class="sxs-lookup"><span data-stu-id="59278-163">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="59278-164">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="59278-164">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 <span data-ttu-id="59278-165">Önceki örnekte `If a IsNot b` eşdeğerdir `If Not a Is b`.</span><span class="sxs-lookup"><span data-stu-id="59278-165">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="59278-166">Nesne türü karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="59278-166">Comparing Object Type</span></span>  
 <span data-ttu-id="59278-167">İle belirli bir türdeki bir nesne olup olmadığını sınayabilirsiniz `TypeOf`... `Is` ifade.</span><span class="sxs-lookup"><span data-stu-id="59278-167">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="59278-168">Söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="59278-168">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="59278-169">Zaman `typename` bir arabirim türü belirtir sonra `TypeOf`... `Is` ifadesi döndürür `True` nesne arabirim türü uyguluyorsa.</span><span class="sxs-lookup"><span data-stu-id="59278-169">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="59278-170">Zaman `typename` ifade döndürür sonra bir sınıf türü olan `True` nesne örneğini belirtilen sınıf veya belirtilen sınıfından türeyen bir sınıf ise.</span><span class="sxs-lookup"><span data-stu-id="59278-170">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="59278-171">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="59278-171">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 <span data-ttu-id="59278-172">Önceki örnekte `TypeOf x Is Control` ifadeyi hesaplar için `True` çünkü türünü `x` olan `Button`, devralan `Control`.</span><span class="sxs-lookup"><span data-stu-id="59278-172">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="59278-173">Daha fazla bilgi için bkz: [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="59278-173">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59278-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59278-174">See Also</span></span>  
 [<span data-ttu-id="59278-175">Değer karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="59278-175">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="59278-176">Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="59278-176">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="59278-177">İşleçler</span><span class="sxs-lookup"><span data-stu-id="59278-177">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)  
 [<span data-ttu-id="59278-178">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="59278-178">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="59278-179">Visual Basic'de birleştirme işleçleri</span><span class="sxs-lookup"><span data-stu-id="59278-179">Concatenation Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [<span data-ttu-id="59278-180">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="59278-180">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
