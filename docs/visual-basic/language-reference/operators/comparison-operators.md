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
ms.openlocfilehash: bf7ff1870a523903babd7140e0d8271f9946064b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628064"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="9d09d-102">Karşılaştırma İşleçleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d09d-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="9d09d-103">Visual Basic içinde tanımlanan Karşılaştırma işleçleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9d09d-103">The following are the comparison operators defined in Visual Basic.</span></span>  
  
 <span data-ttu-id="9d09d-104">`<` İşleci</span><span class="sxs-lookup"><span data-stu-id="9d09d-104">`<` operator</span></span>  
  
 <span data-ttu-id="9d09d-105">`<=` İşleci</span><span class="sxs-lookup"><span data-stu-id="9d09d-105">`<=` operator</span></span>  
  
 <span data-ttu-id="9d09d-106">`>` İşleci</span><span class="sxs-lookup"><span data-stu-id="9d09d-106">`>` operator</span></span>  
  
 <span data-ttu-id="9d09d-107">`>=` İşleci</span><span class="sxs-lookup"><span data-stu-id="9d09d-107">`>=` operator</span></span>  
  
 <span data-ttu-id="9d09d-108">`=` İşleci</span><span class="sxs-lookup"><span data-stu-id="9d09d-108">`=` operator</span></span>  
  
 <span data-ttu-id="9d09d-109">`<>` İşleci</span><span class="sxs-lookup"><span data-stu-id="9d09d-109">`<>` operator</span></span>  
  
 [<span data-ttu-id="9d09d-110">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="9d09d-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [<span data-ttu-id="9d09d-111">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="9d09d-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [<span data-ttu-id="9d09d-112">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="9d09d-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 <span data-ttu-id="9d09d-113">Bu işleçler, eşit oldukları ve aksi durumda, bunlar farklılıklar olup olmadığını belirlemek için iki deyim karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="9d09d-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="9d09d-114">`Is`, `IsNot`, ve `Like` ayrı Yardım sayfalarında ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="9d09d-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="9d09d-115">İlişkisel Karşılaştırma işleçleri, bu sayfada ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="9d09d-115">The relational comparison operators are discussed in detail on this page.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d09d-116">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d09d-116">Syntax</span></span>  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="9d09d-117">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9d09d-117">Parts</span></span>  
 `result`  
 <span data-ttu-id="9d09d-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9d09d-118">Required.</span></span> <span data-ttu-id="9d09d-119">A `Boolean` Karşılaştırmanın sonucu temsil eden değer.</span><span class="sxs-lookup"><span data-stu-id="9d09d-119">A `Boolean` value representing the result of the comparison.</span></span>  
  
 `expression`  
 <span data-ttu-id="9d09d-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9d09d-120">Required.</span></span> <span data-ttu-id="9d09d-121">Herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="9d09d-121">Any expression.</span></span>  
  
 `comparisonoperator`  
 <span data-ttu-id="9d09d-122">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9d09d-122">Required.</span></span> <span data-ttu-id="9d09d-123">Herhangi bir ilişkisel karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="9d09d-123">Any relational comparison operator.</span></span>  
  
 <span data-ttu-id="9d09d-124">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="9d09d-124">`object1`, `object2`</span></span>  
 <span data-ttu-id="9d09d-125">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9d09d-125">Required.</span></span> <span data-ttu-id="9d09d-126">Tüm başvuru nesne adları.</span><span class="sxs-lookup"><span data-stu-id="9d09d-126">Any reference object names.</span></span>  
  
 `string`  
 <span data-ttu-id="9d09d-127">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9d09d-127">Required.</span></span> <span data-ttu-id="9d09d-128">Tüm `String` ifade.</span><span class="sxs-lookup"><span data-stu-id="9d09d-128">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="9d09d-129">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9d09d-129">Required.</span></span> <span data-ttu-id="9d09d-130">Tüm `String` ifadesi veya karakter aralığı.</span><span class="sxs-lookup"><span data-stu-id="9d09d-130">Any `String` expression or range of characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d09d-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d09d-131">Remarks</span></span>  
 <span data-ttu-id="9d09d-132">Aşağıdaki tabloda ilişkisel Karşılaştırma işleçleri ve belirleyen koşulları listesini içeren olmadığını `result` olduğu `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="9d09d-132">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>  
  
|<span data-ttu-id="9d09d-133">İşleç</span><span class="sxs-lookup"><span data-stu-id="9d09d-133">Operator</span></span>|<span data-ttu-id="9d09d-134">`True` Eğer</span><span class="sxs-lookup"><span data-stu-id="9d09d-134">`True` if</span></span>|<span data-ttu-id="9d09d-135">`False` Eğer</span><span class="sxs-lookup"><span data-stu-id="9d09d-135">`False` if</span></span>|  
|--------------|---------------|----------------|  
|<span data-ttu-id="9d09d-136">`<` (Küçüktür)</span><span class="sxs-lookup"><span data-stu-id="9d09d-136">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|  
|<span data-ttu-id="9d09d-137">`<=` (Küçüktür veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="9d09d-137">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|  
|<span data-ttu-id="9d09d-138">`>` (Büyüktür)</span><span class="sxs-lookup"><span data-stu-id="9d09d-138">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|  
|<span data-ttu-id="9d09d-139">`>=` (Büyüktür veya eşittir)</span><span class="sxs-lookup"><span data-stu-id="9d09d-139">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|  
|<span data-ttu-id="9d09d-140">`=` (Eşittir)</span><span class="sxs-lookup"><span data-stu-id="9d09d-140">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|  
|<span data-ttu-id="9d09d-141">`<>` (Eşit değildir)</span><span class="sxs-lookup"><span data-stu-id="9d09d-141">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  <span data-ttu-id="9d09d-142">[= İşleci](../../../visual-basic/language-reference/operators/assignment-operator.md) bir atama işleci da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d09d-142">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>  
  
 <span data-ttu-id="9d09d-143">`Is` İşleci `IsNot` işleci ve `Like` operatörü sahip işleçler yukarıdaki tabloda, farklı belirli karşılaştırma işlevleri.</span><span class="sxs-lookup"><span data-stu-id="9d09d-143">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>  
  
## <a name="comparing-numbers"></a><span data-ttu-id="9d09d-144">Sayı karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="9d09d-144">Comparing Numbers</span></span>  
 <span data-ttu-id="9d09d-145">Türündeki bir ifade karşılaştığınızda `Single` türü birine `Double`, `Single` ifade dönüştürülür `Double`.</span><span class="sxs-lookup"><span data-stu-id="9d09d-145">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="9d09d-146">Bu davranış, Visual Basic 6'da bulunan ters yönde, davranıştır.</span><span class="sxs-lookup"><span data-stu-id="9d09d-146">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>  
  
 <span data-ttu-id="9d09d-147">Benzer şekilde, bir ifade türü karşılaştığınızda `Decimal` türündeki bir ifadeye `Single` veya `Double`, `Decimal` ifade dönüştürülür `Single` veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="9d09d-147">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="9d09d-148">İçin `Decimal` ifadeleri herhangi bir kesirli değer 1E-28 kesilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d09d-148">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="9d09d-149">Böyle bir kesirli değer kaybı olmadıkları zaman eşit karşılaştırmak iki değeri neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d09d-149">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="9d09d-150">Bu nedenle, eşitlik kullanırken dikkatli (`=`) iki kayan nokta değişkeni karşılaştırmak için.</span><span class="sxs-lookup"><span data-stu-id="9d09d-150">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="9d09d-151">İki sayı arasındaki farkı mutlak değerini küçük kabul edilebilir tolerans'dan küçük olup olmadığını test etmek daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="9d09d-151">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>  
  
### <a name="floating-point-imprecision"></a><span data-ttu-id="9d09d-152">Kayan nokta kesinlik eksikliği</span><span class="sxs-lookup"><span data-stu-id="9d09d-152">Floating-point Imprecision</span></span>  
 <span data-ttu-id="9d09d-153">Kayan noktalı sayı ile çalıştığınızda, bunlar her zaman kesin bir gösterimi bellekte olmadığını aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9d09d-153">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="9d09d-154">Değer karşılaştırması gibi bazı işlemleri öğesinden bu beklenmeyen sonuçlara neden olabilir ve [Mod işleci](../../../visual-basic/language-reference/operators/mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="9d09d-154">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="9d09d-155">Daha fazla bilgi için [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="9d09d-155">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="comparing-strings"></a><span data-ttu-id="9d09d-156">Dizeleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="9d09d-156">Comparing Strings</span></span>  
 <span data-ttu-id="9d09d-157">Dizeleri karşılaştırırken dize ifadeleri bağlıdır alfabetik sıralama düzenlerine göre değerlendirilir `Option Compare` ayarı.</span><span class="sxs-lookup"><span data-stu-id="9d09d-157">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>  
  
 <span data-ttu-id="9d09d-158">`Option Compare Binary` tabanları karakterlerin dahili ikili gösterimi türetilmiş bir sıralama düzeni üzerindeki dize.</span><span class="sxs-lookup"><span data-stu-id="9d09d-158">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="9d09d-159">Sıralama düzenini kod sayfası tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9d09d-159">The sort order is determined by the code page.</span></span> <span data-ttu-id="9d09d-160">Aşağıdaki örnek, tipik ikili sıralama düzeninde gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d09d-160">The following example shows a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="9d09d-161">`Option Compare Text` tabanları, uygulamanızın yerel ayarı tarafından belirlenen büyük küçük harf duyarsız, metin sıralama düzeni üzerindeki dize.</span><span class="sxs-lookup"><span data-stu-id="9d09d-161">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="9d09d-162">Ayarladığınızda `Option Compare Text` ve önceki örnekte karakterleri sıralamak için aşağıdaki metin sıralama düzeni uygular:</span><span class="sxs-lookup"><span data-stu-id="9d09d-162">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a><span data-ttu-id="9d09d-163">Yerel ayar bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="9d09d-163">Locale Dependence</span></span>  
 <span data-ttu-id="9d09d-164">Ayarladığınızda `Option Compare Text`, bir dize karşılaştırmasının sonucunu uygulamasının çalıştığı yerel ayarına göre değişebilir.</span><span class="sxs-lookup"><span data-stu-id="9d09d-164">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="9d09d-165">İki karakteri, eşittir, ancak, başka bir yerel ayardaki karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="9d09d-165">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="9d09d-166">Oturum girişimi kabul edilip edilmeyeceğini gibi önemli kararları yapmak için bir dize karşılaştırmasının kullanıyorsanız, yerel ayar duyarlılık uyarı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d09d-166">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="9d09d-167">Her iki ayarlamayı düşünün `Option Compare Binary` veya çağıran <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, hesaba yerel alır.</span><span class="sxs-lookup"><span data-stu-id="9d09d-167">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="9d09d-168">Yazısız programlama ilişkisel Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="9d09d-168">Typeless Programming with Relational Comparison Operators</span></span>  
 <span data-ttu-id="9d09d-169">İlişkisel Karşılaştırma işleçleri ile kullanımını `Object` altında ifadeleri verilmez `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="9d09d-169">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="9d09d-170">Zaman `Option Strict` olduğu `Off`ve her iki `expression1` veya `expression2` olduğu bir `Object` ifade nasıl kıyasla çalışma zamanı türlerini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="9d09d-170">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="9d09d-171">Aşağıdaki tabloda, ifadelerin nasıl karşılaştırılır ve işlenenleri çalışma zamanı türüne bağlı olarak, karşılaştırma sonucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d09d-171">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>  
  
|<span data-ttu-id="9d09d-172">İşlenen</span><span class="sxs-lookup"><span data-stu-id="9d09d-172">If operands are</span></span>|<span data-ttu-id="9d09d-173">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="9d09d-173">Comparison is</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="9d09d-174">Her ikisi de `String`</span><span class="sxs-lookup"><span data-stu-id="9d09d-174">Both `String`</span></span>|<span data-ttu-id="9d09d-175">Karşılaştırma özelliklerini sıralama dizesine dayalı sıralayın.</span><span class="sxs-lookup"><span data-stu-id="9d09d-175">Sort comparison based on string sorting characteristics.</span></span>|  
|<span data-ttu-id="9d09d-176">Her iki sayısal</span><span class="sxs-lookup"><span data-stu-id="9d09d-176">Both numeric</span></span>|<span data-ttu-id="9d09d-177">Nesneleri dönüştürülen `Double`, sayısal karşılaştırma.</span><span class="sxs-lookup"><span data-stu-id="9d09d-177">Objects converted to `Double`, numeric comparison.</span></span>|  
|<span data-ttu-id="9d09d-178">Bir sayısal ve bir `String`</span><span class="sxs-lookup"><span data-stu-id="9d09d-178">One numeric and one `String`</span></span>|<span data-ttu-id="9d09d-179">`String` Dönüştürülür bir `Double` ve sayısal karşılaştırma gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9d09d-179">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="9d09d-180">Varsa `String` dönüştürülemez `Double`e <xref:System.InvalidCastException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9d09d-180">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|  
|<span data-ttu-id="9d09d-181">Veya ikisini birden fazla başvuru türleri olan `String`</span><span class="sxs-lookup"><span data-stu-id="9d09d-181">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="9d09d-182">Bir <xref:System.InvalidCastException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9d09d-182">An <xref:System.InvalidCastException> is thrown.</span></span>|  
  
 <span data-ttu-id="9d09d-183">Sayısal karşılaştırma kabul `Nothing` 0 olarak.</span><span class="sxs-lookup"><span data-stu-id="9d09d-183">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="9d09d-184">Dize karşılaştırmaları kabul `Nothing` olarak `""` (boş bir dize).</span><span class="sxs-lookup"><span data-stu-id="9d09d-184">String comparisons treat `Nothing` as `""` (an empty string).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9d09d-185">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="9d09d-185">Overloading</span></span>  
 <span data-ttu-id="9d09d-186">İlişkisel Karşılaştırma işleçleri (`<`.</span><span class="sxs-lookup"><span data-stu-id="9d09d-186">The relational comparison operators (`<`.</span></span> <span data-ttu-id="9d09d-187">`<=``>`, `>=`, `=`, `<>`) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışlarını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9d09d-187">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9d09d-188">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleçler birini kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9d09d-188">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="9d09d-189">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9d09d-189">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
 <span data-ttu-id="9d09d-190">Dikkat [= işleci](../../../visual-basic/language-reference/operators/assignment-operator.md) aşırı yüklenmiş olabilir yalnızca ilişkisel karşılaştırma işleci olarak, bir atama işleci olarak değil.</span><span class="sxs-lookup"><span data-stu-id="9d09d-190">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d09d-191">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d09d-191">Example</span></span>  
 <span data-ttu-id="9d09d-192">Aşağıdaki örnek, çeşitli kullanımları ifadeleri karşılaştırmak için kullanılan ilişkisel karşılaştırma işleçlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d09d-192">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="9d09d-193">İlişkisel Karşılaştırma işleçleri dönüş bir `Boolean` belirtilen ifadenin değerlendirdiği olup olmadığını gösteren bir sonuç `True`.</span><span class="sxs-lookup"><span data-stu-id="9d09d-193">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="9d09d-194">Uyguladığınızda `>` ve `<` işleçleri için dizeleri Karşılaştırma yapıldığında dizelerin normal alfabetik sıralama düzenini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="9d09d-194">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="9d09d-195">Bu sırada, yerel ayara bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d09d-195">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="9d09d-196">Sıralama büyük küçük harfe duyarlı olup olmamasına bağlıdır [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) ayarı.</span><span class="sxs-lookup"><span data-stu-id="9d09d-196">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 <span data-ttu-id="9d09d-197">Önceki örnekte, ilk karşılaştırma döndürür `False` ve kalan karşılaştırmalar dönüş `True`.</span><span class="sxs-lookup"><span data-stu-id="9d09d-197">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d09d-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d09d-198">See also</span></span>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="9d09d-199">= İşleci</span><span class="sxs-lookup"><span data-stu-id="9d09d-199">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="9d09d-200">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="9d09d-200">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9d09d-201">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="9d09d-201">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9d09d-202">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="9d09d-202">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="9d09d-203">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="9d09d-203">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
