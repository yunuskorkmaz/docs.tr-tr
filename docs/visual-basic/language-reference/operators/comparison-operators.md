---
title: Karşılaştırma İşleçleri (Visual Basic)
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
- comparison operators [Visual Basic], Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 4e37f55b4c873c3dbea22a8edf0e5e2b58824720
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604932"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="ccde9-102">Karşılaştırma İşleçleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccde9-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="ccde9-103">Visual Basic'te tanımlanan Karşılaştırma işleçleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-103">The following are the comparison operators defined in Visual Basic.</span></span>  
  
 <span data-ttu-id="ccde9-104">`<` işleci</span><span class="sxs-lookup"><span data-stu-id="ccde9-104">`<` operator</span></span>  
  
 <span data-ttu-id="ccde9-105">`<=` işleci</span><span class="sxs-lookup"><span data-stu-id="ccde9-105">`<=` operator</span></span>  
  
 <span data-ttu-id="ccde9-106">`>` işleci</span><span class="sxs-lookup"><span data-stu-id="ccde9-106">`>` operator</span></span>  
  
 <span data-ttu-id="ccde9-107">`>=` işleci</span><span class="sxs-lookup"><span data-stu-id="ccde9-107">`>=` operator</span></span>  
  
 <span data-ttu-id="ccde9-108">`=` işleci</span><span class="sxs-lookup"><span data-stu-id="ccde9-108">`=` operator</span></span>  
  
 <span data-ttu-id="ccde9-109">`<>` işleci</span><span class="sxs-lookup"><span data-stu-id="ccde9-109">`<>` operator</span></span>  
  
 [<span data-ttu-id="ccde9-110">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="ccde9-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [<span data-ttu-id="ccde9-111">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="ccde9-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [<span data-ttu-id="ccde9-112">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="ccde9-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 <span data-ttu-id="ccde9-113">Bu işleçlere eşit değilse, bunların nasıl farklı olup olmadığını belirlemek için iki ifadeye karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="ccde9-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="ccde9-114">`Is`, `IsNot`, ve `Like` ayrı Yardım sayfalarına ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="ccde9-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="ccde9-115">İlişkisel Karşılaştırma işleçleri bu sayfada ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="ccde9-115">The relational comparison operators are discussed in detail on this page.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccde9-116">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccde9-116">Syntax</span></span>  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="ccde9-117">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ccde9-117">Parts</span></span>  
 `result`  
 <span data-ttu-id="ccde9-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ccde9-118">Required.</span></span> <span data-ttu-id="ccde9-119">A `Boolean` karşılaştırma sonucunu temsil eden değer.</span><span class="sxs-lookup"><span data-stu-id="ccde9-119">A `Boolean` value representing the result of the comparison.</span></span>  
  
 `expression`  
 <span data-ttu-id="ccde9-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ccde9-120">Required.</span></span> <span data-ttu-id="ccde9-121">Herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="ccde9-121">Any expression.</span></span>  
  
 `comparisonoperator`  
 <span data-ttu-id="ccde9-122">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ccde9-122">Required.</span></span> <span data-ttu-id="ccde9-123">Herhangi bir ilişkisel karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="ccde9-123">Any relational comparison operator.</span></span>  
  
 <span data-ttu-id="ccde9-124">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="ccde9-124">`object1`, `object2`</span></span>  
 <span data-ttu-id="ccde9-125">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ccde9-125">Required.</span></span> <span data-ttu-id="ccde9-126">Herhangi bir nesne adlarını başvuru.</span><span class="sxs-lookup"><span data-stu-id="ccde9-126">Any reference object names.</span></span>  
  
 `string`  
 <span data-ttu-id="ccde9-127">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ccde9-127">Required.</span></span> <span data-ttu-id="ccde9-128">Tüm `String` ifade.</span><span class="sxs-lookup"><span data-stu-id="ccde9-128">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="ccde9-129">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ccde9-129">Required.</span></span> <span data-ttu-id="ccde9-130">Tüm `String` ifadesi veya karakter aralığı.</span><span class="sxs-lookup"><span data-stu-id="ccde9-130">Any `String` expression or range of characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccde9-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ccde9-131">Remarks</span></span>  
 <span data-ttu-id="ccde9-132">Aşağıdaki tabloda ilişkisel Karşılaştırma işleçleri ve belirleyen koşulları listesini içeren olup olmadığını `result` olan `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="ccde9-132">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>  
  
|<span data-ttu-id="ccde9-133">İşleç</span><span class="sxs-lookup"><span data-stu-id="ccde9-133">Operator</span></span>|<span data-ttu-id="ccde9-134">`True` Eğer</span><span class="sxs-lookup"><span data-stu-id="ccde9-134">`True` if</span></span>|<span data-ttu-id="ccde9-135">`False` Eğer</span><span class="sxs-lookup"><span data-stu-id="ccde9-135">`False` if</span></span>|  
|--------------|---------------|----------------|  
|<span data-ttu-id="ccde9-136">`<` (Küçüktür)</span><span class="sxs-lookup"><span data-stu-id="ccde9-136">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|  
|<span data-ttu-id="ccde9-137">`<=` (Küçük veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="ccde9-137">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|  
|<span data-ttu-id="ccde9-138">`>` (Büyük)</span><span class="sxs-lookup"><span data-stu-id="ccde9-138">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|  
|<span data-ttu-id="ccde9-139">`>=` (Büyük veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="ccde9-139">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|  
|<span data-ttu-id="ccde9-140">`=` (Eşit)</span><span class="sxs-lookup"><span data-stu-id="ccde9-140">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|  
|<span data-ttu-id="ccde9-141">`<>` (Eşit değildir)</span><span class="sxs-lookup"><span data-stu-id="ccde9-141">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  <span data-ttu-id="ccde9-142">[= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md) atama işleci da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ccde9-142">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>  
  
 <span data-ttu-id="ccde9-143">`Is` İşleci, `IsNot` işleci ve `Like` işleci işleçleri önceki tabloda farklı belirli karşılaştırma işlevler sahip.</span><span class="sxs-lookup"><span data-stu-id="ccde9-143">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>  
  
## <a name="comparing-numbers"></a><span data-ttu-id="ccde9-144">Sayı karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="ccde9-144">Comparing Numbers</span></span>  
 <span data-ttu-id="ccde9-145">Türünde bir ifadenin karşılaştırmak zaman `Single` türü birine `Double`, `Single` ifade için dönüştürülür `Double`.</span><span class="sxs-lookup"><span data-stu-id="ccde9-145">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="ccde9-146">Bu Visual Basic 6'bulunan davranışı ters yönde bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="ccde9-146">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>  
  
 <span data-ttu-id="ccde9-147">Benzer şekilde, ne zaman, karşılaştırma türü bir ifadenin `Decimal` türünde bir ifadenin için `Single` veya `Double`, `Decimal` ifade için dönüştürülür `Single` veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="ccde9-147">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="ccde9-148">İçin `Decimal` ifadeleri, herhangi bir kesir değerini 1E-28 kaybolabilir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-148">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="ccde9-149">Böyle bir kesir değerini kaybı olmadıkları zaman eşit karşılaştırmak iki değer neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-149">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="ccde9-150">Bu nedenle, eşitlik kullanırken dikkatli (`=`) iki kayan nokta değişkenleri karşılaştırmak için.</span><span class="sxs-lookup"><span data-stu-id="ccde9-150">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="ccde9-151">İki sayı arasındaki farkı mutlak değerini küçük kabul edilebilir tolerans değerinden olup olmadığını sınamak daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-151">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>  
  
### <a name="floating-point-imprecision"></a><span data-ttu-id="ccde9-152">Kayan nokta Imprecision</span><span class="sxs-lookup"><span data-stu-id="ccde9-152">Floating-point Imprecision</span></span>  
 <span data-ttu-id="ccde9-153">Kayan nokta sayıları ile çalışırken, her zaman kesin gösterimi bellekte olmadığı olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ccde9-153">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="ccde9-154">Değer karşılaştırması gibi bazı işlemleri alanından bu beklenmeyen sonuçlara neden ve [Mod işleci](../../../visual-basic/language-reference/operators/mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ccde9-154">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="ccde9-155">Daha fazla bilgi için bkz: [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="ccde9-155">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="comparing-strings"></a><span data-ttu-id="ccde9-156">Dizeleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="ccde9-156">Comparing Strings</span></span>  
 <span data-ttu-id="ccde9-157">Dizeleri karşılaştırmak, dize ifadeler bağlıdır alfabetik sıralama düzenlerine göre değerlendirilir `Option Compare` ayarı.</span><span class="sxs-lookup"><span data-stu-id="ccde9-157">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>  
  
 <span data-ttu-id="ccde9-158">`Option Compare Binary` tabanları iç ikili gösterimlerini karakterleri türetilmiş bir sıralama düzeni üzerinde karşılaştırmalarına dize.</span><span class="sxs-lookup"><span data-stu-id="ccde9-158">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="ccde9-159">Sıralama düzenini kod sayfası tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-159">The sort order is determined by the code page.</span></span> <span data-ttu-id="ccde9-160">Aşağıdaki örnek, tipik bir ikili sıralama gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-160">The following example shows a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="ccde9-161">`Option Compare Text` tabanları uygulamanızın bölgeye göre belirlenir büyük küçük harf duyarsız, metinsel sıralama düzeni üzerinde karşılaştırmalarına dize.</span><span class="sxs-lookup"><span data-stu-id="ccde9-161">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="ccde9-162">Ayarladığınızda `Option Compare Text` ve önceki örnekte karakterleri sıralamak için aşağıdaki metni sıralama düzeni uygular:</span><span class="sxs-lookup"><span data-stu-id="ccde9-162">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a><span data-ttu-id="ccde9-163">Yerel ayar bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="ccde9-163">Locale Dependence</span></span>  
 <span data-ttu-id="ccde9-164">Ayarladığınızda `Option Compare Text`, dize karşılaştırmasının sonucu uygulamanın çalıştığı yerel ayara bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-164">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="ccde9-165">İki karakter, bir yerel ancak başka eşit olarak karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="ccde9-165">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="ccde9-166">Oturum girişimi kabul edilip edilmeyeceğini gibi önemli kararları yapmak için bir dize karşılaştırma kullanıyorsanız, yerel ayar duyarlılık uyarısını olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccde9-166">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="ccde9-167">Her iki ayar göz önünde bulundurun `Option Compare Binary` veya arama <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, hesaba yerel alır.</span><span class="sxs-lookup"><span data-stu-id="ccde9-167">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="ccde9-168">İlişkisel Karşılaştırma işleçleri ile yazısız programlama</span><span class="sxs-lookup"><span data-stu-id="ccde9-168">Typeless Programming with Relational Comparison Operators</span></span>  
 <span data-ttu-id="ccde9-169">İlişkisel Karşılaştırma işleçleri ile kullanımını `Object` ifadeleri altında izin verilmeyen `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="ccde9-169">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="ccde9-170">Zaman `Option Strict` olan `Off`ve her iki `expression1` veya `expression2` olan bir `Object` ifadesi nasıl karşılaştırılır çalışma zamanı türlerini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="ccde9-170">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="ccde9-171">Aşağıdaki tablo ifadeleri nasıl karşılaştırılır ve işlenen çalışma zamanı türüne bağlı olarak karşılaştırma sonucundan gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-171">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>  
  
|<span data-ttu-id="ccde9-172">İşlenen olursa</span><span class="sxs-lookup"><span data-stu-id="ccde9-172">If operands are</span></span>|<span data-ttu-id="ccde9-173">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="ccde9-173">Comparison is</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="ccde9-174">Her ikisi `String`</span><span class="sxs-lookup"><span data-stu-id="ccde9-174">Both `String`</span></span>|<span data-ttu-id="ccde9-175">Özellikleri sıralama dizesine dayalı karşılaştırma sıralayın.</span><span class="sxs-lookup"><span data-stu-id="ccde9-175">Sort comparison based on string sorting characteristics.</span></span>|  
|<span data-ttu-id="ccde9-176">Her iki sayısal</span><span class="sxs-lookup"><span data-stu-id="ccde9-176">Both numeric</span></span>|<span data-ttu-id="ccde9-177">Nesneleri dönüştürülür `Double`, sayısal karşılaştırma.</span><span class="sxs-lookup"><span data-stu-id="ccde9-177">Objects converted to `Double`, numeric comparison.</span></span>|  
|<span data-ttu-id="ccde9-178">Bir sayısal ve bir `String`</span><span class="sxs-lookup"><span data-stu-id="ccde9-178">One numeric and one `String`</span></span>|<span data-ttu-id="ccde9-179">`String` Dönüştürülür bir `Double` ve sayısal karşılaştırma gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-179">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="ccde9-180">Varsa `String` dönüştürülemiyor `Double`, bir <xref:System.InvalidCastException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ccde9-180">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|  
|<span data-ttu-id="ccde9-181">Ya da her ikisini de dışında başvuru türleri: `String`</span><span class="sxs-lookup"><span data-stu-id="ccde9-181">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="ccde9-182">Bir <xref:System.InvalidCastException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ccde9-182">An <xref:System.InvalidCastException> is thrown.</span></span>|  
  
 <span data-ttu-id="ccde9-183">Sayısal karşılaştırmaları kabul `Nothing` 0 olarak.</span><span class="sxs-lookup"><span data-stu-id="ccde9-183">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="ccde9-184">Dize karşılaştırmaları kabul `Nothing` olarak `""` (boş bir dize).</span><span class="sxs-lookup"><span data-stu-id="ccde9-184">String comparisons treat `Nothing` as `""` (an empty string).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ccde9-185">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="ccde9-185">Overloading</span></span>  
 <span data-ttu-id="ccde9-186">İlişkisel Karşılaştırma işleçleri (`<`.</span><span class="sxs-lookup"><span data-stu-id="ccde9-186">The relational comparison operators (`<`.</span></span> <span data-ttu-id="ccde9-187">`<=``>`, `>=`, `=`, `<>`) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışlarını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-187">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ccde9-188">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleçlere hiçbirini kullanıyorsa, yeniden tanımlanan davranışı anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ccde9-188">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="ccde9-189">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ccde9-189">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
 <span data-ttu-id="ccde9-190">Dikkat [= işleci](../../../visual-basic/language-reference/operators/assignment-operator.md) aşırı yüklenmiş olabilir yalnızca bir ilişkisel karşılaştırma işleci olarak değil olarak atama işleci.</span><span class="sxs-lookup"><span data-stu-id="ccde9-190">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccde9-191">Örnek</span><span class="sxs-lookup"><span data-stu-id="ccde9-191">Example</span></span>  
 <span data-ttu-id="ccde9-192">Aşağıdaki örnek ifadeler karşılaştırmak için kullandığınız ilişkisel Karşılaştırma işleçleri çeşitli kullanımları gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-192">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="ccde9-193">İlişkisel Karşılaştırma işleçleri dönüş bir `Boolean` için belirtilen ifadeyi hesaplar olup olmadığına bakılmaksızın temsil eden sonuç `True`.</span><span class="sxs-lookup"><span data-stu-id="ccde9-193">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="ccde9-194">Uyguladığınızda `>` ve `<` işleçleri dizeleri için Karşılaştırma yapıldığında dizelerin normal alfabetik sıralama düzenini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ccde9-194">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="ccde9-195">Bu sırada, yerel ayara bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ccde9-195">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="ccde9-196">Sıralama büyük küçük harfe duyarlı olup olmamasına bağlıdır [seçeneği karşılaştırmak](../../../visual-basic/language-reference/statements/option-compare-statement.md) ayarı.</span><span class="sxs-lookup"><span data-stu-id="ccde9-196">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 <span data-ttu-id="ccde9-197">Önceki örnekte, ilk karşılaştırma döndürür `False` ve kalan karşılaştırmaları dönmek `True`.</span><span class="sxs-lookup"><span data-stu-id="ccde9-197">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccde9-198">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ccde9-198">See Also</span></span>  
 <xref:System.InvalidCastException>  
 [<span data-ttu-id="ccde9-199">= İşleci</span><span class="sxs-lookup"><span data-stu-id="ccde9-199">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [<span data-ttu-id="ccde9-200">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="ccde9-200">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="ccde9-201">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="ccde9-201">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="ccde9-202">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="ccde9-202">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="ccde9-203">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="ccde9-203">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
