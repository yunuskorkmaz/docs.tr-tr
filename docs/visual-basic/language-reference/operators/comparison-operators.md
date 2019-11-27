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
ms.openlocfilehash: ea7604626ede66da818e4bc22fe4922bc752dc2c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336080"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="fa23d-102">Karşılaştırma İşleçleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa23d-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="fa23d-103">Aşağıda, Visual Basic tanımlanan karşılaştırma işleçleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-103">The following are the comparison operators defined in Visual Basic.</span></span>

 <span data-ttu-id="fa23d-104">`<` işleci</span><span class="sxs-lookup"><span data-stu-id="fa23d-104">`<` operator</span></span>

 <span data-ttu-id="fa23d-105">`<=` işleci</span><span class="sxs-lookup"><span data-stu-id="fa23d-105">`<=` operator</span></span>

 <span data-ttu-id="fa23d-106">`>` işleci</span><span class="sxs-lookup"><span data-stu-id="fa23d-106">`>` operator</span></span>

 <span data-ttu-id="fa23d-107">`>=` işleci</span><span class="sxs-lookup"><span data-stu-id="fa23d-107">`>=` operator</span></span>

 <span data-ttu-id="fa23d-108">`=` işleci</span><span class="sxs-lookup"><span data-stu-id="fa23d-108">`=` operator</span></span>

 <span data-ttu-id="fa23d-109">`<>` işleci</span><span class="sxs-lookup"><span data-stu-id="fa23d-109">`<>` operator</span></span>

 [<span data-ttu-id="fa23d-110">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="fa23d-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)

 [<span data-ttu-id="fa23d-111">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="fa23d-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)

 [<span data-ttu-id="fa23d-112">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="fa23d-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)

 <span data-ttu-id="fa23d-113">Bu işleçler, eşit olup olmadığını ve değilse ne farklılık olduğunu anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="fa23d-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="fa23d-114">`Is`, `IsNot`ve `Like` ayrı Yardım sayfalarında ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="fa23d-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="fa23d-115">İlişkisel karşılaştırma işleçleri bu sayfada ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="fa23d-115">The relational comparison operators are discussed in detail on this page.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa23d-116">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa23d-116">Syntax</span></span>
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="fa23d-117">Bölümler</span><span class="sxs-lookup"><span data-stu-id="fa23d-117">Parts</span></span>
 `result`  
 <span data-ttu-id="fa23d-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fa23d-118">Required.</span></span> <span data-ttu-id="fa23d-119">Karşılaştırmanın sonucunu temsil eden bir `Boolean` değeri.</span><span class="sxs-lookup"><span data-stu-id="fa23d-119">A `Boolean` value representing the result of the comparison.</span></span>

 <span data-ttu-id="fa23d-120">`expression1`, `expression2`</span><span class="sxs-lookup"><span data-stu-id="fa23d-120">`expression1`, `expression2`</span></span>  
 <span data-ttu-id="fa23d-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fa23d-121">Required.</span></span> <span data-ttu-id="fa23d-122">Herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="fa23d-122">Any expression.</span></span>

 `comparisonoperator`  
 <span data-ttu-id="fa23d-123">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fa23d-123">Required.</span></span> <span data-ttu-id="fa23d-124">Herhangi bir ilişkisel karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="fa23d-124">Any relational comparison operator.</span></span>

 <span data-ttu-id="fa23d-125">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="fa23d-125">`object1`, `object2`</span></span>  
 <span data-ttu-id="fa23d-126">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fa23d-126">Required.</span></span> <span data-ttu-id="fa23d-127">Herhangi bir başvuru nesnesi adı.</span><span class="sxs-lookup"><span data-stu-id="fa23d-127">Any reference object names.</span></span>

 `string`  
 <span data-ttu-id="fa23d-128">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fa23d-128">Required.</span></span> <span data-ttu-id="fa23d-129">Herhangi bir `String` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="fa23d-129">Any `String` expression.</span></span>

 `pattern`  
 <span data-ttu-id="fa23d-130">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fa23d-130">Required.</span></span> <span data-ttu-id="fa23d-131">Herhangi bir `String` ifadesi veya karakter aralığı.</span><span class="sxs-lookup"><span data-stu-id="fa23d-131">Any `String` expression or range of characters.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa23d-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa23d-132">Remarks</span></span>
 <span data-ttu-id="fa23d-133">Aşağıdaki tabloda, ilişkisel karşılaştırma işleçleri listesi ve `result` `True` veya `False`olup olmadığını belirleme koşulları yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa23d-133">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>

|<span data-ttu-id="fa23d-134">İşleç</span><span class="sxs-lookup"><span data-stu-id="fa23d-134">Operator</span></span>|<span data-ttu-id="fa23d-135">`True`</span><span class="sxs-lookup"><span data-stu-id="fa23d-135">`True` if</span></span>|<span data-ttu-id="fa23d-136">`False`</span><span class="sxs-lookup"><span data-stu-id="fa23d-136">`False` if</span></span>|
|--------------|---------------|----------------|
|<span data-ttu-id="fa23d-137">`<` (küçüktür)</span><span class="sxs-lookup"><span data-stu-id="fa23d-137">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|
|<span data-ttu-id="fa23d-138">`<=` (küçüktür veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="fa23d-138">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|
|<span data-ttu-id="fa23d-139">`>` (büyüktür)</span><span class="sxs-lookup"><span data-stu-id="fa23d-139">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|
|<span data-ttu-id="fa23d-140">`>=` (büyüktür veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="fa23d-140">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|
|<span data-ttu-id="fa23d-141">`=` (eşittir)</span><span class="sxs-lookup"><span data-stu-id="fa23d-141">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|
|<span data-ttu-id="fa23d-142">`<>` (eşit değildir)</span><span class="sxs-lookup"><span data-stu-id="fa23d-142">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> <span data-ttu-id="fa23d-143">[= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md) atama işleci olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa23d-143">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>

 <span data-ttu-id="fa23d-144">`Is` işleci, `IsNot` işleci ve `Like` işleci, önceki tablodaki işleçlerden farklı olan özel karşılaştırma işlevlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-144">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>

## <a name="comparing-numbers"></a><span data-ttu-id="fa23d-145">Sayıları karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="fa23d-145">Comparing Numbers</span></span>
 <span data-ttu-id="fa23d-146">`Single` türündeki bir ifadeyi `Double`türünden birine karşılaştırdığınızda, `Single` ifadesi `Double`'ye dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="fa23d-146">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="fa23d-147">Bu davranış, Visual Basic 6 ' da bulunan davranışın tersidir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-147">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>

 <span data-ttu-id="fa23d-148">Benzer şekilde, `Decimal` bir ifadesini `Single` veya `Double`türünde bir ifadeyle karşılaştırdığınızda `Decimal` ifadesi `Single` veya `Double`olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="fa23d-148">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="fa23d-149">`Decimal` ifadelerde, 1E-28 ' den küçük olan herhangi bir kesirli değer kaybolmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-149">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="fa23d-150">Bu tür kesirli değer kaybı, iki değerin, olmadıkları zaman eşit olarak karşılaştırılmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-150">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="fa23d-151">Bu nedenle, iki kayan nokta değişkenini karşılaştırmak için eşitlik (`=`) kullanırken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-151">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="fa23d-152">İki sayı arasındaki farkın mutlak değerinin, kabul edilebilir küçük bir toleranstan daha az olup olmadığını test etmek daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-152">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>

### <a name="floating-point-imprecision"></a><span data-ttu-id="fa23d-153">Kayan nokta noktasında kesinlik eksikliği</span><span class="sxs-lookup"><span data-stu-id="fa23d-153">Floating-point Imprecision</span></span>
 <span data-ttu-id="fa23d-154">Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimine sahip olmadıkları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="fa23d-154">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="fa23d-155">Bu, değer karşılaştırması ve [Mod işleci](../../../visual-basic/language-reference/operators/mod-operator.md)gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-155">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="fa23d-156">Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="fa23d-156">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="comparing-strings"></a><span data-ttu-id="fa23d-157">Dizeleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="fa23d-157">Comparing Strings</span></span>
 <span data-ttu-id="fa23d-158">Dizeleri karşılaştırdığınızda, dize ifadeleri alfabetik sıralama sıralamasına göre değerlendirilir ve bu, `Option Compare` ayarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fa23d-158">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>

 <span data-ttu-id="fa23d-159">`Option Compare Binary`, karakterlerin iç ikili gösterimlerine göre türetilmiş bir sıralama düzeninde dize karşılaştırmaları dayandırır.</span><span class="sxs-lookup"><span data-stu-id="fa23d-159">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="fa23d-160">Sıralama düzeni kod sayfası tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-160">The sort order is determined by the code page.</span></span> <span data-ttu-id="fa23d-161">Aşağıdaki örnek tipik bir ikili sıralama düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-161">The following example shows a typical binary sort order.</span></span>

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 <span data-ttu-id="fa23d-162">`Option Compare Text`, uygulamanızın yerel ayarı tarafından belirlenen büyük/küçük harf duyarsız, metinsel sıralama düzeninde dize karşılaştırmaları dayandırır.</span><span class="sxs-lookup"><span data-stu-id="fa23d-162">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="fa23d-163">`Option Compare Text` ayarlayıp önceki örnekteki karakterleri sıraladığınızda aşağıdaki metin sıralama düzeni geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="fa23d-163">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a><span data-ttu-id="fa23d-164">Yerel ayar bağımlılığını</span><span class="sxs-lookup"><span data-stu-id="fa23d-164">Locale Dependence</span></span>
 <span data-ttu-id="fa23d-165">`Option Compare Text`ayarladığınızda, bir dize karşılaştırmasının sonucu uygulamanın çalıştığı yerel ayara bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-165">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="fa23d-166">İki karakter, bir yerel ayarda eşit olarak karşılaştırılabilir ancak başka bir şekilde karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-166">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="fa23d-167">Oturum açma denemesinin kabul edilip edilmeyeceğini kabul etmeksizin, önemli kararlar almak için bir dize karşılaştırması kullanıyorsanız, yerel ayar duyarlılığı için uyarı almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-167">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="fa23d-168">Yerel ayarı hesaba alan `Option Compare Binary` veya <xref:Microsoft.VisualBasic.Strings.StrComp%2A>çağırmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="fa23d-168">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>

## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="fa23d-169">Ilişkisel karşılaştırma Işleçleri ile Türsüz programlama</span><span class="sxs-lookup"><span data-stu-id="fa23d-169">Typeless Programming with Relational Comparison Operators</span></span>
 <span data-ttu-id="fa23d-170">`Option Strict On`altında `Object` ifadelerle ilişkisel karşılaştırma işleçleri kullanımına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="fa23d-170">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="fa23d-171">`Option Strict` `Off`ve `expression1` ya da `expression2` bir `Object` ifadesi olduğunda, çalışma zamanı türleri nasıl karşılaştırılacağını belirlenir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-171">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="fa23d-172">Aşağıdaki tabloda, işlenenlerinin çalışma zamanı türüne bağlı olarak ifadelerin karşılaştırılacağı ve Karşılaştırmanın sonucu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-172">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>

|<span data-ttu-id="fa23d-173">İşlenenler</span><span class="sxs-lookup"><span data-stu-id="fa23d-173">If operands are</span></span>|<span data-ttu-id="fa23d-174">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="fa23d-174">Comparison is</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="fa23d-175">Her iki `String`</span><span class="sxs-lookup"><span data-stu-id="fa23d-175">Both `String`</span></span>|<span data-ttu-id="fa23d-176">Dize sıralama özelliklerine göre karşılaştırmayı sıralayın.</span><span class="sxs-lookup"><span data-stu-id="fa23d-176">Sort comparison based on string sorting characteristics.</span></span>|
|<span data-ttu-id="fa23d-177">Her iki sayısal</span><span class="sxs-lookup"><span data-stu-id="fa23d-177">Both numeric</span></span>|<span data-ttu-id="fa23d-178">`Double`, sayısal karşılaştırmaya dönüştürülen nesneler.</span><span class="sxs-lookup"><span data-stu-id="fa23d-178">Objects converted to `Double`, numeric comparison.</span></span>|
|<span data-ttu-id="fa23d-179">Bir sayısal ve bir `String`</span><span class="sxs-lookup"><span data-stu-id="fa23d-179">One numeric and one `String`</span></span>|<span data-ttu-id="fa23d-180">`String` bir `Double` dönüştürülür ve sayısal karşılaştırma gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-180">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="fa23d-181">`String` `Double`olarak dönüştürülemiyorsa bir <xref:System.InvalidCastException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fa23d-181">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|
|<span data-ttu-id="fa23d-182">Ya da her ikisi de `String` dışındaki başvuru türleridir</span><span class="sxs-lookup"><span data-stu-id="fa23d-182">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="fa23d-183">Bir <xref:System.InvalidCastException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fa23d-183">An <xref:System.InvalidCastException> is thrown.</span></span>|

 <span data-ttu-id="fa23d-184">Sayısal karşılaştırmalar `Nothing` 0 olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-184">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="fa23d-185">Dize karşılaştırmaları `Nothing` `""` (boş bir dize) olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-185">String comparisons treat `Nothing` as `""` (an empty string).</span></span>

## <a name="overloading"></a><span data-ttu-id="fa23d-186">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="fa23d-186">Overloading</span></span>
 <span data-ttu-id="fa23d-187">İlişkisel karşılaştırma işleçleri (`<`.</span><span class="sxs-lookup"><span data-stu-id="fa23d-187">The relational comparison operators (`<`.</span></span> <span data-ttu-id="fa23d-188">`<=`, `>`, `>=`, `=`, `<>`) *aşırı yüklenmiş*olabilir, bu da bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-188">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="fa23d-189">Kodunuz böyle bir sınıf veya yapıda bu işleçlerden herhangi birini kullanıyorsa, yeniden tanımlanan davranışı anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fa23d-189">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="fa23d-190">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fa23d-190">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

 <span data-ttu-id="fa23d-191">[= İşlecinin](../../../visual-basic/language-reference/operators/assignment-operator.md) , atama işleci olarak değil, yalnızca ilişkisel karşılaştırma operatörü olarak aşırı yüklenebilir olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="fa23d-191">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>

## <a name="example"></a><span data-ttu-id="fa23d-192">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa23d-192">Example</span></span>
 <span data-ttu-id="fa23d-193">Aşağıdaki örnek, ifadeleri karşılaştırmak için kullandığınız, ilişkisel karşılaştırma işleçlerinin çeşitli kullanımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-193">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="fa23d-194">İlişkisel karşılaştırma işleçleri, belirtilen ifadenin `True`olarak değerlendirilip değerlendirilmediğini temsil eden `Boolean` bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa23d-194">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="fa23d-195">Dizelere `>` ve `<` işleçlerini uyguladığınızda, karşılaştırma, dizelerin normal alfabetik sıralama düzeni kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="fa23d-195">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="fa23d-196">Bu sipariş, yerel ayara bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa23d-196">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="fa23d-197">Sıralamanın büyük/küçük harfe duyarlı olup olmadığı veya [Seçenek karşılaştırma](../../../visual-basic/language-reference/statements/option-compare-statement.md) ayarına bağlı olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="fa23d-197">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 <span data-ttu-id="fa23d-198">Yukarıdaki örnekte, ilk karşılaştırma `False` döndürür ve kalan karşılaştırmalar `True`döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa23d-198">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa23d-199">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa23d-199">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="fa23d-200">= İşleci</span><span class="sxs-lookup"><span data-stu-id="fa23d-200">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="fa23d-201">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="fa23d-201">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="fa23d-202">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="fa23d-202">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="fa23d-203">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="fa23d-203">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="fa23d-204">Visual Basic karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="fa23d-204">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
