---
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
ms.openlocfilehash: fcbb9052a79fa4b20b5a0f8fdc15de73d55a4281
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873451"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="5866b-102">Karşılaştırma İşleçleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5866b-102">Comparison Operators (Visual Basic)</span></span>

<span data-ttu-id="5866b-103">Aşağıda, Visual Basic tanımlanan karşılaştırma işleçleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5866b-103">The following are the comparison operators defined in Visual Basic.</span></span>

 <span data-ttu-id="5866b-104">`<` işlecinde</span><span class="sxs-lookup"><span data-stu-id="5866b-104">`<` operator</span></span>

 <span data-ttu-id="5866b-105">`<=` işlecinde</span><span class="sxs-lookup"><span data-stu-id="5866b-105">`<=` operator</span></span>

 <span data-ttu-id="5866b-106">`>` işlecinde</span><span class="sxs-lookup"><span data-stu-id="5866b-106">`>` operator</span></span>

 <span data-ttu-id="5866b-107">`>=` işlecinde</span><span class="sxs-lookup"><span data-stu-id="5866b-107">`>=` operator</span></span>

 <span data-ttu-id="5866b-108">`=` işlecinde</span><span class="sxs-lookup"><span data-stu-id="5866b-108">`=` operator</span></span>

 <span data-ttu-id="5866b-109">`<>` işlecinde</span><span class="sxs-lookup"><span data-stu-id="5866b-109">`<>` operator</span></span>

 [<span data-ttu-id="5866b-110">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="5866b-110">Is Operator</span></span>](is-operator.md)

 [<span data-ttu-id="5866b-111">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="5866b-111">IsNot Operator</span></span>](isnot-operator.md)

 [<span data-ttu-id="5866b-112">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="5866b-112">Like Operator</span></span>](like-operator.md)

 <span data-ttu-id="5866b-113">Bu işleçler, eşit olup olmadığını ve değilse ne farklılık olduğunu anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="5866b-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="5866b-114">`Is`, `IsNot` ve `Like` ayrı Yardım sayfalarında ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="5866b-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="5866b-115">İlişkisel karşılaştırma işleçleri bu sayfada ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="5866b-115">The relational comparison operators are discussed in detail on this page.</span></span>

## <a name="syntax"></a><span data-ttu-id="5866b-116">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5866b-116">Syntax</span></span>
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="5866b-117">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5866b-117">Parts</span></span>

 `result`  
 <span data-ttu-id="5866b-118">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5866b-118">Required.</span></span> <span data-ttu-id="5866b-119">`Boolean`Karşılaştırmanın sonucunu temsil eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="5866b-119">A `Boolean` value representing the result of the comparison.</span></span>

 <span data-ttu-id="5866b-120">`expression1`, `expression2`</span><span class="sxs-lookup"><span data-stu-id="5866b-120">`expression1`, `expression2`</span></span>  
 <span data-ttu-id="5866b-121">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5866b-121">Required.</span></span> <span data-ttu-id="5866b-122">Herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="5866b-122">Any expression.</span></span>

 `comparisonoperator`  
 <span data-ttu-id="5866b-123">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5866b-123">Required.</span></span> <span data-ttu-id="5866b-124">Herhangi bir ilişkisel karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="5866b-124">Any relational comparison operator.</span></span>

 <span data-ttu-id="5866b-125">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="5866b-125">`object1`, `object2`</span></span>  
 <span data-ttu-id="5866b-126">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5866b-126">Required.</span></span> <span data-ttu-id="5866b-127">Herhangi bir başvuru nesnesi adı.</span><span class="sxs-lookup"><span data-stu-id="5866b-127">Any reference object names.</span></span>

 `string`  
 <span data-ttu-id="5866b-128">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5866b-128">Required.</span></span> <span data-ttu-id="5866b-129">Herhangi bir `String` ifade.</span><span class="sxs-lookup"><span data-stu-id="5866b-129">Any `String` expression.</span></span>

 `pattern`  
 <span data-ttu-id="5866b-130">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5866b-130">Required.</span></span> <span data-ttu-id="5866b-131">Herhangi bir `String` ifade veya karakter aralığı.</span><span class="sxs-lookup"><span data-stu-id="5866b-131">Any `String` expression or range of characters.</span></span>

## <a name="remarks"></a><span data-ttu-id="5866b-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5866b-132">Remarks</span></span>

 <span data-ttu-id="5866b-133">Aşağıdaki tabloda, ilişkisel karşılaştırma işleçleri ve olup olmadığını belirleme koşulları yer almaktadır `result` `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="5866b-133">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>

|<span data-ttu-id="5866b-134">Operatör</span><span class="sxs-lookup"><span data-stu-id="5866b-134">Operator</span></span>|<span data-ttu-id="5866b-135">`True` kullandıysanız</span><span class="sxs-lookup"><span data-stu-id="5866b-135">`True` if</span></span>|<span data-ttu-id="5866b-136">`False` kullandıysanız</span><span class="sxs-lookup"><span data-stu-id="5866b-136">`False` if</span></span>|
|--------------|---------------|----------------|
|<span data-ttu-id="5866b-137">`<` (Küçüktür)</span><span class="sxs-lookup"><span data-stu-id="5866b-137">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|
|<span data-ttu-id="5866b-138">`<=` (Küçüktür veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="5866b-138">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|
|<span data-ttu-id="5866b-139">`>` (Büyüktür)</span><span class="sxs-lookup"><span data-stu-id="5866b-139">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|
|<span data-ttu-id="5866b-140">`>=` (Büyüktür veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="5866b-140">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|
|<span data-ttu-id="5866b-141">`=` (Eşittir)</span><span class="sxs-lookup"><span data-stu-id="5866b-141">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|
|<span data-ttu-id="5866b-142">`<>` (Eşit değildir)</span><span class="sxs-lookup"><span data-stu-id="5866b-142">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> <span data-ttu-id="5866b-143">[= İşleci](assignment-operator.md) atama işleci olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5866b-143">The [= Operator](assignment-operator.md) is also used as an assignment operator.</span></span>

 <span data-ttu-id="5866b-144">İşleci `Is` , `IsNot` işleci ve `Like` işleci, önceki tablodaki işleçlerden farklı olan özel karşılaştırma işlevlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5866b-144">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>

## <a name="comparing-numbers"></a><span data-ttu-id="5866b-145">Sayıları karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="5866b-145">Comparing Numbers</span></span>

 <span data-ttu-id="5866b-146">Türünde bir ifadeyi türünden birine karşılaştırdığınızda `Single` `Double` , `Single` ifadesi öğesine dönüştürülür `Double` .</span><span class="sxs-lookup"><span data-stu-id="5866b-146">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="5866b-147">Bu davranış, Visual Basic 6 ' da bulunan davranışın tersidir.</span><span class="sxs-lookup"><span data-stu-id="5866b-147">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>

 <span data-ttu-id="5866b-148">Benzer şekilde, türü bir ifadesini `Decimal` veya türünde bir ifadeye karşılaştırdığınızda `Single` `Double` , ifade veya ' a `Decimal` dönüştürülür `Single` `Double` .</span><span class="sxs-lookup"><span data-stu-id="5866b-148">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="5866b-149">`Decimal`İfadeler için, 1E-28 ' den küçük herhangi bir kesirli değer kaybolmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="5866b-149">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="5866b-150">Bu tür kesirli değer kaybı, iki değerin, olmadıkları zaman eşit olarak karşılaştırılmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="5866b-150">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="5866b-151">Bu nedenle, `=` iki kayan nokta değişkenini karşılaştırmak için eşitlik () kullanırken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5866b-151">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="5866b-152">İki sayı arasındaki farkın mutlak değerinin, kabul edilebilir küçük bir toleranstan daha az olup olmadığını test etmek daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="5866b-152">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>

### <a name="floating-point-imprecision"></a><span data-ttu-id="5866b-153">Kayan nokta noktasında kesinlik eksikliği</span><span class="sxs-lookup"><span data-stu-id="5866b-153">Floating-point Imprecision</span></span>

 <span data-ttu-id="5866b-154">Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimine sahip olmadıkları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5866b-154">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="5866b-155">Bu, değer karşılaştırması ve [Mod işleci](mod-operator.md)gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="5866b-155">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](mod-operator.md).</span></span> <span data-ttu-id="5866b-156">Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="5866b-156">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="comparing-strings"></a><span data-ttu-id="5866b-157">Dizeleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="5866b-157">Comparing Strings</span></span>

 <span data-ttu-id="5866b-158">Dizeleri karşılaştırdığınızda, dize ifadeleri alfabetik sıralama sıralamasına göre değerlendirilir ve bu `Option Compare` ayar değişir.</span><span class="sxs-lookup"><span data-stu-id="5866b-158">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>

 <span data-ttu-id="5866b-159">`Option Compare Binary` , karakterlerin iç ikili gösterimlerine göre türetilmiş bir sıralama düzeninde dize karşılaştırmaları dayandırır.</span><span class="sxs-lookup"><span data-stu-id="5866b-159">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="5866b-160">Sıralama düzeni kod sayfası tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5866b-160">The sort order is determined by the code page.</span></span> <span data-ttu-id="5866b-161">Aşağıdaki örnek tipik bir ikili sıralama düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="5866b-161">The following example shows a typical binary sort order.</span></span>

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 <span data-ttu-id="5866b-162">`Option Compare Text` , uygulamanızın yerel ayarı tarafından belirlenen büyük/küçük harf duyarsız, metinsel sıralama düzeninde dize karşılaştırmaları dayandırır.</span><span class="sxs-lookup"><span data-stu-id="5866b-162">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="5866b-163">`Option Compare Text`Önceki örnekteki karakterleri ayarlayıp sıraladığınızda aşağıdaki metin sıralama düzeni geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="5866b-163">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a><span data-ttu-id="5866b-164">Yerel ayar bağımlılığını</span><span class="sxs-lookup"><span data-stu-id="5866b-164">Locale Dependence</span></span>

 <span data-ttu-id="5866b-165">Ayarladığınızda `Option Compare Text` , bir dize karşılaştırmasının sonucu uygulamanın çalıştığı yerel ayara bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5866b-165">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="5866b-166">İki karakter, bir yerel ayarda eşit olarak karşılaştırılabilir ancak başka bir şekilde karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5866b-166">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="5866b-167">Oturum açma denemesinin kabul edilip edilmeyeceğini kabul etmeksizin, önemli kararlar almak için bir dize karşılaştırması kullanıyorsanız, yerel ayar duyarlılığı için uyarı almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5866b-167">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="5866b-168">`Option Compare Binary`Yerel ayarı hesabına alan öğesini ayarlamayı veya çağırmayı düşünün <xref:Microsoft.VisualBasic.Strings.StrComp%2A> .</span><span class="sxs-lookup"><span data-stu-id="5866b-168">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>

## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="5866b-169">Ilişkisel karşılaştırma Işleçleri ile Türsüz programlama</span><span class="sxs-lookup"><span data-stu-id="5866b-169">Typeless Programming with Relational Comparison Operators</span></span>

 <span data-ttu-id="5866b-170">İçinde deyimlerle ilişkisel karşılaştırma işleçleri kullanımına `Object` izin verilmez `Option Strict On` .</span><span class="sxs-lookup"><span data-stu-id="5866b-170">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="5866b-171">Olduğunda `Option Strict` `Off` ve ya da `expression1` `expression2` bir ifade olduğunda `Object` , çalışma zamanı türleri nasıl karşılaştırıldığını tespit edilir.</span><span class="sxs-lookup"><span data-stu-id="5866b-171">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="5866b-172">Aşağıdaki tabloda, işlenenlerinin çalışma zamanı türüne bağlı olarak ifadelerin karşılaştırılacağı ve Karşılaştırmanın sonucu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5866b-172">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>

|<span data-ttu-id="5866b-173">İşlenenler</span><span class="sxs-lookup"><span data-stu-id="5866b-173">If operands are</span></span>|<span data-ttu-id="5866b-174">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="5866b-174">Comparison is</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="5866b-175">İs `String`</span><span class="sxs-lookup"><span data-stu-id="5866b-175">Both `String`</span></span>|<span data-ttu-id="5866b-176">Dize sıralama özelliklerine göre karşılaştırmayı sıralayın.</span><span class="sxs-lookup"><span data-stu-id="5866b-176">Sort comparison based on string sorting characteristics.</span></span>|
|<span data-ttu-id="5866b-177">Her iki sayısal</span><span class="sxs-lookup"><span data-stu-id="5866b-177">Both numeric</span></span>|<span data-ttu-id="5866b-178">' A dönüştürülen nesneler `Double` , sayısal karşılaştırmaya.</span><span class="sxs-lookup"><span data-stu-id="5866b-178">Objects converted to `Double`, numeric comparison.</span></span>|
|<span data-ttu-id="5866b-179">Bir sayısal ve bir `String`</span><span class="sxs-lookup"><span data-stu-id="5866b-179">One numeric and one `String`</span></span>|<span data-ttu-id="5866b-180">, `String` Bir değerine dönüştürülür `Double` ve sayısal bir karşılaştırmaya yapılır.</span><span class="sxs-lookup"><span data-stu-id="5866b-180">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="5866b-181">`String`Öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> atılır.</span><span class="sxs-lookup"><span data-stu-id="5866b-181">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|
|<span data-ttu-id="5866b-182">Ya da her ikisi birden dışında başvuru türleridir `String`</span><span class="sxs-lookup"><span data-stu-id="5866b-182">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="5866b-183">Bir oluşturulur <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="5866b-183">An <xref:System.InvalidCastException> is thrown.</span></span>|

 <span data-ttu-id="5866b-184">Sayısal karşılaştırmalar `Nothing` 0 olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5866b-184">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="5866b-185">Dize karşılaştırmaları `Nothing` `""` (boş bir dize) olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5866b-185">String comparisons treat `Nothing` as `""` (an empty string).</span></span>

## <a name="overloading"></a><span data-ttu-id="5866b-186">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="5866b-186">Overloading</span></span>

 <span data-ttu-id="5866b-187">İlişkisel karşılaştırma işleçleri ( `<` .</span><span class="sxs-lookup"><span data-stu-id="5866b-187">The relational comparison operators (`<`.</span></span> <span data-ttu-id="5866b-188">`<=`,,, `>` `>=` `=` , `<>` ) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5866b-188">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5866b-189">Kodunuz böyle bir sınıf veya yapıda bu işleçlerden herhangi birini kullanıyorsa, yeniden tanımlanan davranışı anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5866b-189">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="5866b-190">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5866b-190">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

 <span data-ttu-id="5866b-191">[= İşlecinin](assignment-operator.md) , atama işleci olarak değil, yalnızca ilişkisel karşılaştırma operatörü olarak aşırı yüklenebilir olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5866b-191">Notice that the [= Operator](assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>

## <a name="example"></a><span data-ttu-id="5866b-192">Örnek</span><span class="sxs-lookup"><span data-stu-id="5866b-192">Example</span></span>

 <span data-ttu-id="5866b-193">Aşağıdaki örnek, ifadeleri karşılaştırmak için kullandığınız, ilişkisel karşılaştırma işleçlerinin çeşitli kullanımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5866b-193">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="5866b-194">İlişkisel karşılaştırma işleçleri `Boolean` , belirtilen ifadenin olarak değerlendirilip değerlendirilmediğini temsil eden bir sonuç döndürür `True` .</span><span class="sxs-lookup"><span data-stu-id="5866b-194">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="5866b-195">`>`Ve `<` işleçlerini dizelere uyguladığınızda, karşılaştırma, dizelerin normal alfabetik sıralama düzeni kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="5866b-195">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="5866b-196">Bu sipariş, yerel ayara bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5866b-196">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="5866b-197">Sıralamanın büyük/küçük harfe duyarlı olup olmadığı veya [Seçenek karşılaştırma](../statements/option-compare-statement.md) ayarına bağlı olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="5866b-197">Whether the sort is case-sensitive or not depends on the [Option Compare](../statements/option-compare-statement.md) setting.</span></span>

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 <span data-ttu-id="5866b-198">Önceki örnekte, ilk karşılaştırma döndürülür `False` ve kalan karşılaştırmalar döndürülür `True` .</span><span class="sxs-lookup"><span data-stu-id="5866b-198">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5866b-199">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5866b-199">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="5866b-200">= İşleci</span><span class="sxs-lookup"><span data-stu-id="5866b-200">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="5866b-201">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="5866b-201">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="5866b-202">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="5866b-202">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="5866b-203">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="5866b-203">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="5866b-204">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="5866b-204">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
