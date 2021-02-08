---
description: 'Daha fazla bilgi edinin: karşılaştırma Işleçleri (Visual Basic)'
title: Karşılaştırma İşleçleri
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 28eded0cfae54ec83ad9546b801243e4de0e45fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774115"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="284d8-103">Karşılaştırma İşleçleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="284d8-103">Comparison Operators (Visual Basic)</span></span>

<span data-ttu-id="284d8-104">Aşağıda, Visual Basic tanımlanan karşılaştırma işleçleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="284d8-104">The following are the comparison operators defined in Visual Basic.</span></span>

 <span data-ttu-id="284d8-105">`<` işlecinde</span><span class="sxs-lookup"><span data-stu-id="284d8-105">`<` operator</span></span>

 <span data-ttu-id="284d8-106">`<=` işlecinde</span><span class="sxs-lookup"><span data-stu-id="284d8-106">`<=` operator</span></span>

 <span data-ttu-id="284d8-107">`>` işlecinde</span><span class="sxs-lookup"><span data-stu-id="284d8-107">`>` operator</span></span>

 <span data-ttu-id="284d8-108">`>=` işlecinde</span><span class="sxs-lookup"><span data-stu-id="284d8-108">`>=` operator</span></span>

 <span data-ttu-id="284d8-109">`=` işlecinde</span><span class="sxs-lookup"><span data-stu-id="284d8-109">`=` operator</span></span>

 <span data-ttu-id="284d8-110">`<>` işlecinde</span><span class="sxs-lookup"><span data-stu-id="284d8-110">`<>` operator</span></span>

 [<span data-ttu-id="284d8-111">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="284d8-111">Is Operator</span></span>](is-operator.md)

 [<span data-ttu-id="284d8-112">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="284d8-112">IsNot Operator</span></span>](isnot-operator.md)

 [<span data-ttu-id="284d8-113">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="284d8-113">Like Operator</span></span>](like-operator.md)

 <span data-ttu-id="284d8-114">Bu işleçler, eşit olup olmadığını ve değilse ne farklılık olduğunu anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="284d8-114">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="284d8-115">`Is`, `IsNot` ve `Like` ayrı Yardım sayfalarında ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="284d8-115">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="284d8-116">İlişkisel karşılaştırma işleçleri bu sayfada ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="284d8-116">The relational comparison operators are discussed in detail on this page.</span></span>

## <a name="syntax"></a><span data-ttu-id="284d8-117">Syntax</span><span class="sxs-lookup"><span data-stu-id="284d8-117">Syntax</span></span>
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="284d8-118">Bölümler</span><span class="sxs-lookup"><span data-stu-id="284d8-118">Parts</span></span>

 `result`  
 <span data-ttu-id="284d8-119">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="284d8-119">Required.</span></span> <span data-ttu-id="284d8-120">`Boolean`Karşılaştırmanın sonucunu temsil eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="284d8-120">A `Boolean` value representing the result of the comparison.</span></span>

 <span data-ttu-id="284d8-121">`expression1`, `expression2`</span><span class="sxs-lookup"><span data-stu-id="284d8-121">`expression1`, `expression2`</span></span>  
 <span data-ttu-id="284d8-122">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="284d8-122">Required.</span></span> <span data-ttu-id="284d8-123">Herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="284d8-123">Any expression.</span></span>

 `comparisonoperator`  
 <span data-ttu-id="284d8-124">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="284d8-124">Required.</span></span> <span data-ttu-id="284d8-125">Herhangi bir ilişkisel karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="284d8-125">Any relational comparison operator.</span></span>

 <span data-ttu-id="284d8-126">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="284d8-126">`object1`, `object2`</span></span>  
 <span data-ttu-id="284d8-127">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="284d8-127">Required.</span></span> <span data-ttu-id="284d8-128">Herhangi bir başvuru nesnesi adı.</span><span class="sxs-lookup"><span data-stu-id="284d8-128">Any reference object names.</span></span>

 `string`  
 <span data-ttu-id="284d8-129">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="284d8-129">Required.</span></span> <span data-ttu-id="284d8-130">Herhangi bir `String` ifade.</span><span class="sxs-lookup"><span data-stu-id="284d8-130">Any `String` expression.</span></span>

 `pattern`  
 <span data-ttu-id="284d8-131">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="284d8-131">Required.</span></span> <span data-ttu-id="284d8-132">Herhangi bir `String` ifade veya karakter aralığı.</span><span class="sxs-lookup"><span data-stu-id="284d8-132">Any `String` expression or range of characters.</span></span>

## <a name="remarks"></a><span data-ttu-id="284d8-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="284d8-133">Remarks</span></span>

 <span data-ttu-id="284d8-134">Aşağıdaki tabloda, ilişkisel karşılaştırma işleçleri ve olup olmadığını belirleme koşulları yer almaktadır `result` `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="284d8-134">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>

|<span data-ttu-id="284d8-135">Operatör</span><span class="sxs-lookup"><span data-stu-id="284d8-135">Operator</span></span>|<span data-ttu-id="284d8-136">`True` kullandıysanız</span><span class="sxs-lookup"><span data-stu-id="284d8-136">`True` if</span></span>|<span data-ttu-id="284d8-137">`False` kullandıysanız</span><span class="sxs-lookup"><span data-stu-id="284d8-137">`False` if</span></span>|
|--------------|---------------|----------------|
|<span data-ttu-id="284d8-138">`<` (Küçüktür)</span><span class="sxs-lookup"><span data-stu-id="284d8-138">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|
|<span data-ttu-id="284d8-139">`<=` (Küçüktür veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="284d8-139">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|
|<span data-ttu-id="284d8-140">`>` (Büyüktür)</span><span class="sxs-lookup"><span data-stu-id="284d8-140">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|
|<span data-ttu-id="284d8-141">`>=` (Büyüktür veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="284d8-141">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|
|<span data-ttu-id="284d8-142">`=` (Eşittir)</span><span class="sxs-lookup"><span data-stu-id="284d8-142">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|
|<span data-ttu-id="284d8-143">`<>` (Eşit değildir)</span><span class="sxs-lookup"><span data-stu-id="284d8-143">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> <span data-ttu-id="284d8-144">[= İşleci](assignment-operator.md) atama işleci olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="284d8-144">The [= Operator](assignment-operator.md) is also used as an assignment operator.</span></span>

 <span data-ttu-id="284d8-145">İşleci `Is` , `IsNot` işleci ve `Like` işleci, önceki tablodaki işleçlerden farklı olan özel karşılaştırma işlevlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="284d8-145">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>

## <a name="comparing-numbers"></a><span data-ttu-id="284d8-146">Sayıları karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="284d8-146">Comparing Numbers</span></span>

 <span data-ttu-id="284d8-147">Türünde bir ifadeyi türünden birine karşılaştırdığınızda `Single` `Double` , `Single` ifadesi öğesine dönüştürülür `Double` .</span><span class="sxs-lookup"><span data-stu-id="284d8-147">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="284d8-148">Bu davranış, Visual Basic 6 ' da bulunan davranışın tersidir.</span><span class="sxs-lookup"><span data-stu-id="284d8-148">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>

 <span data-ttu-id="284d8-149">Benzer şekilde, türü bir ifadesini `Decimal` veya türünde bir ifadeye karşılaştırdığınızda `Single` `Double` , ifade veya ' a `Decimal` dönüştürülür `Single` `Double` .</span><span class="sxs-lookup"><span data-stu-id="284d8-149">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="284d8-150">`Decimal`İfadeler için, 1E-28 ' den küçük herhangi bir kesirli değer kaybolmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="284d8-150">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="284d8-151">Bu tür kesirli değer kaybı, iki değerin, olmadıkları zaman eşit olarak karşılaştırılmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="284d8-151">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="284d8-152">Bu nedenle, `=` iki kayan nokta değişkenini karşılaştırmak için eşitlik () kullanırken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="284d8-152">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="284d8-153">İki sayı arasındaki farkın mutlak değerinin, kabul edilebilir küçük bir toleranstan daha az olup olmadığını test etmek daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="284d8-153">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>

### <a name="floating-point-imprecision"></a><span data-ttu-id="284d8-154">Kayan nokta noktasında kesinlik eksikliği</span><span class="sxs-lookup"><span data-stu-id="284d8-154">Floating-point Imprecision</span></span>

 <span data-ttu-id="284d8-155">Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimine sahip olmadıkları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="284d8-155">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="284d8-156">Bu, değer karşılaştırması ve [Mod işleci](mod-operator.md)gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="284d8-156">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](mod-operator.md).</span></span> <span data-ttu-id="284d8-157">Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="284d8-157">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="comparing-strings"></a><span data-ttu-id="284d8-158">Dizeleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="284d8-158">Comparing Strings</span></span>

 <span data-ttu-id="284d8-159">Dizeleri karşılaştırdığınızda, dize ifadeleri alfabetik sıralama sıralamasına göre değerlendirilir ve bu `Option Compare` ayar değişir.</span><span class="sxs-lookup"><span data-stu-id="284d8-159">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>

 <span data-ttu-id="284d8-160">`Option Compare Binary` , karakterlerin iç ikili gösterimlerine göre türetilmiş bir sıralama düzeninde dize karşılaştırmaları dayandırır.</span><span class="sxs-lookup"><span data-stu-id="284d8-160">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="284d8-161">Sıralama düzeni kod sayfası tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="284d8-161">The sort order is determined by the code page.</span></span> <span data-ttu-id="284d8-162">Aşağıdaki örnek tipik bir ikili sıralama düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="284d8-162">The following example shows a typical binary sort order.</span></span>

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 <span data-ttu-id="284d8-163">`Option Compare Text` , uygulamanızın yerel ayarı tarafından belirlenen büyük/küçük harf duyarsız, metinsel sıralama düzeninde dize karşılaştırmaları dayandırır.</span><span class="sxs-lookup"><span data-stu-id="284d8-163">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="284d8-164">`Option Compare Text`Önceki örnekteki karakterleri ayarlayıp sıraladığınızda aşağıdaki metin sıralama düzeni geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="284d8-164">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a><span data-ttu-id="284d8-165">Yerel ayar bağımlılığını</span><span class="sxs-lookup"><span data-stu-id="284d8-165">Locale Dependence</span></span>

 <span data-ttu-id="284d8-166">Ayarladığınızda `Option Compare Text` , bir dize karşılaştırmasının sonucu uygulamanın çalıştığı yerel ayara bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="284d8-166">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="284d8-167">İki karakter, bir yerel ayarda eşit olarak karşılaştırılabilir ancak başka bir şekilde karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="284d8-167">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="284d8-168">Oturum açma denemesinin kabul edilip edilmeyeceğini kabul etmeksizin, önemli kararlar almak için bir dize karşılaştırması kullanıyorsanız, yerel ayar duyarlılığı için uyarı almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="284d8-168">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="284d8-169">`Option Compare Binary`Yerel ayarı hesabına alan öğesini ayarlamayı veya çağırmayı düşünün <xref:Microsoft.VisualBasic.Strings.StrComp%2A> .</span><span class="sxs-lookup"><span data-stu-id="284d8-169">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>

## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="284d8-170">Ilişkisel karşılaştırma Işleçleri ile Türsüz programlama</span><span class="sxs-lookup"><span data-stu-id="284d8-170">Typeless Programming with Relational Comparison Operators</span></span>

 <span data-ttu-id="284d8-171">İçinde deyimlerle ilişkisel karşılaştırma işleçleri kullanımına `Object` izin verilmez `Option Strict On` .</span><span class="sxs-lookup"><span data-stu-id="284d8-171">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="284d8-172">Olduğunda `Option Strict` `Off` ve ya da `expression1` `expression2` bir ifade olduğunda `Object` , çalışma zamanı türleri nasıl karşılaştırıldığını tespit edilir.</span><span class="sxs-lookup"><span data-stu-id="284d8-172">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="284d8-173">Aşağıdaki tabloda, işlenenlerinin çalışma zamanı türüne bağlı olarak ifadelerin karşılaştırılacağı ve Karşılaştırmanın sonucu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="284d8-173">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>

|<span data-ttu-id="284d8-174">İşlenenler</span><span class="sxs-lookup"><span data-stu-id="284d8-174">If operands are</span></span>|<span data-ttu-id="284d8-175">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="284d8-175">Comparison is</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="284d8-176">İs `String`</span><span class="sxs-lookup"><span data-stu-id="284d8-176">Both `String`</span></span>|<span data-ttu-id="284d8-177">Dize sıralama özelliklerine göre karşılaştırmayı sıralayın.</span><span class="sxs-lookup"><span data-stu-id="284d8-177">Sort comparison based on string sorting characteristics.</span></span>|
|<span data-ttu-id="284d8-178">Her iki sayısal</span><span class="sxs-lookup"><span data-stu-id="284d8-178">Both numeric</span></span>|<span data-ttu-id="284d8-179">' A dönüştürülen nesneler `Double` , sayısal karşılaştırmaya.</span><span class="sxs-lookup"><span data-stu-id="284d8-179">Objects converted to `Double`, numeric comparison.</span></span>|
|<span data-ttu-id="284d8-180">Bir sayısal ve bir `String`</span><span class="sxs-lookup"><span data-stu-id="284d8-180">One numeric and one `String`</span></span>|<span data-ttu-id="284d8-181">, `String` Bir değerine dönüştürülür `Double` ve sayısal bir karşılaştırmaya yapılır.</span><span class="sxs-lookup"><span data-stu-id="284d8-181">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="284d8-182">`String`Öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> atılır.</span><span class="sxs-lookup"><span data-stu-id="284d8-182">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|
|<span data-ttu-id="284d8-183">Ya da her ikisi birden dışında başvuru türleridir `String`</span><span class="sxs-lookup"><span data-stu-id="284d8-183">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="284d8-184">Bir oluşturulur <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="284d8-184">An <xref:System.InvalidCastException> is thrown.</span></span>|

 <span data-ttu-id="284d8-185">Sayısal karşılaştırmalar `Nothing` 0 olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="284d8-185">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="284d8-186">Dize karşılaştırmaları `Nothing` `""` (boş bir dize) olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="284d8-186">String comparisons treat `Nothing` as `""` (an empty string).</span></span>

## <a name="overloading"></a><span data-ttu-id="284d8-187">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="284d8-187">Overloading</span></span>

 <span data-ttu-id="284d8-188">İlişkisel karşılaştırma işleçleri ( `<` .</span><span class="sxs-lookup"><span data-stu-id="284d8-188">The relational comparison operators (`<`.</span></span> <span data-ttu-id="284d8-189">`<=`,,, `>` `>=` `=` , `<>` ) *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="284d8-189">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="284d8-190">Kodunuz böyle bir sınıf veya yapıda bu işleçlerden herhangi birini kullanıyorsa, yeniden tanımlanan davranışı anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="284d8-190">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="284d8-191">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="284d8-191">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

 <span data-ttu-id="284d8-192">[= İşlecinin](assignment-operator.md) , atama işleci olarak değil, yalnızca ilişkisel karşılaştırma operatörü olarak aşırı yüklenebilir olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="284d8-192">Notice that the [= Operator](assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>

## <a name="example"></a><span data-ttu-id="284d8-193">Örnek</span><span class="sxs-lookup"><span data-stu-id="284d8-193">Example</span></span>

 <span data-ttu-id="284d8-194">Aşağıdaki örnek, ifadeleri karşılaştırmak için kullandığınız, ilişkisel karşılaştırma işleçlerinin çeşitli kullanımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="284d8-194">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="284d8-195">İlişkisel karşılaştırma işleçleri `Boolean` , belirtilen ifadenin olarak değerlendirilip değerlendirilmediğini temsil eden bir sonuç döndürür `True` .</span><span class="sxs-lookup"><span data-stu-id="284d8-195">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="284d8-196">`>`Ve `<` işleçlerini dizelere uyguladığınızda, karşılaştırma, dizelerin normal alfabetik sıralama düzeni kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="284d8-196">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="284d8-197">Bu sipariş, yerel ayara bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="284d8-197">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="284d8-198">Sıralamanın büyük/küçük harfe duyarlı olup olmadığı veya [Seçenek karşılaştırma](../statements/option-compare-statement.md) ayarına bağlı olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="284d8-198">Whether the sort is case-sensitive or not depends on the [Option Compare](../statements/option-compare-statement.md) setting.</span></span>

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 <span data-ttu-id="284d8-199">Önceki örnekte, ilk karşılaştırma döndürülür `False` ve kalan karşılaştırmalar döndürülür `True` .</span><span class="sxs-lookup"><span data-stu-id="284d8-199">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>

## <a name="see-also"></a><span data-ttu-id="284d8-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="284d8-200">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="284d8-201">= İşleci</span><span class="sxs-lookup"><span data-stu-id="284d8-201">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="284d8-202">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="284d8-202">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="284d8-203">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="284d8-203">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="284d8-204">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="284d8-204">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="284d8-205">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="284d8-205">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
