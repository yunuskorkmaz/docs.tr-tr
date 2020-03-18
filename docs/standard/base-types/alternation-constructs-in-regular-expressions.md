---
title: .NET Düzenli İfadelerde Alternation Yapılar
description: Düzenli ifadelerde koşullu eşleştirme için alternasyon yapılarını nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
ms.openlocfilehash: 02664bd2812f89649ec933483161263bae530a75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159695"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="78df7-103">Normal İfadelerdeki Değişim Yapıları</span><span class="sxs-lookup"><span data-stu-id="78df7-103">Alternation Constructs in Regular Expressions</span></span>

<span data-ttu-id="78df7-104">Alternation yapıları ya / veya koşullu eşleştirme etkinleştirmek için normal bir ifade değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="78df7-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="78df7-105">.NET üç değişim yapısını destekler:</span><span class="sxs-lookup"><span data-stu-id="78df7-105">.NET supports three alternation constructs:</span></span>

- [<span data-ttu-id="78df7-106">&#124;ile eşleşen desen</span><span class="sxs-lookup"><span data-stu-id="78df7-106">Pattern matching with &#124;</span></span>](#Either_Or)
- [<span data-ttu-id="78df7-107">Koşullu eşleştirme ile (?( ifade)evet&#124;hayır)</span><span class="sxs-lookup"><span data-stu-id="78df7-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)
- [<span data-ttu-id="78df7-108">Yakalanan geçerli bir gruba göre koşullu eşleştirme</span><span class="sxs-lookup"><span data-stu-id="78df7-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a><span data-ttu-id="78df7-109">&#124; ile Örüntü Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="78df7-109">Pattern Matching with &#124;</span></span>

<span data-ttu-id="78df7-110">Dikey çubuk (`|`) karakterini, `|` karakterin her deseni ayırdığı bir dizi desenle eşleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78df7-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>

<span data-ttu-id="78df7-111">Pozitif karakter sınıfı gibi, `|` karakter de tek karakterden herhangi biriyle eşleşmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78df7-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="78df7-112">Aşağıdaki örnekte, bir dizedeki "gri" veya `|` "gri" sözcüklerinin oluşumlarını bulmak için hem pozitif karakter sınıfı hem de karakterle eşleşen bir deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="78df7-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="78df7-113">Bu durumda, `|` karakter daha ayrıntılı düzenli bir ifade üretir.</span><span class="sxs-lookup"><span data-stu-id="78df7-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

<span data-ttu-id="78df7-114">`|` Karakteri kullanan normal ifade, `\bgr(a|e)y\b`aşağıdaki tabloda gösterildiği gibi yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="78df7-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="78df7-115">Desen</span><span class="sxs-lookup"><span data-stu-id="78df7-115">Pattern</span></span>|<span data-ttu-id="78df7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78df7-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="78df7-117">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="78df7-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="78df7-118">"gr" karakterlerini eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="78df7-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="78df7-119">Bir "a" veya "e" ile eşleş.</span><span class="sxs-lookup"><span data-stu-id="78df7-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="78df7-120">Sözcük sınırında bir "y" ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="78df7-120">Match a "y" on a word boundary.</span></span>|  

<span data-ttu-id="78df7-121">`|` Karakter, karakter gerçek ve normal ifade dili öğelerinin herhangi bir birleşimini içerebilen birden çok karakter veya alt ifadeyle eşleştirme yapmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78df7-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="78df7-122">(Karakter sınıfı bu işlevselliği sağlamaz.) Aşağıdaki örnek, `|` *ddd*-*ddddd\*\*dd*-biçimine sahip 9 basamaklı bir sayı olan ABD Sosyal Güvenlik Numarası (SSN) veya-*dddddd*biçimine sahip 9 basamaklı bir sayı *dd*olan ABD İşveren Kimlik Numarası (EIN) özelliğini ayıklamak için karakteri kullanır.</span><span class="sxs-lookup"><span data-stu-id="78df7-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

<span data-ttu-id="78df7-123">Normal ifade `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="78df7-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>
  
|<span data-ttu-id="78df7-124">Desen</span><span class="sxs-lookup"><span data-stu-id="78df7-124">Pattern</span></span>|<span data-ttu-id="78df7-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78df7-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="78df7-126">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="78df7-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="78df7-127">Aşağıdakilerden birini eşleştirin: iki ondalık basamak ve ardından bir tire ve ardından yedi ondalık basamak; veya üç ondalık basamak, bir tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak.</span><span class="sxs-lookup"><span data-stu-id="78df7-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="78df7-128">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="78df7-128">End the match at a word boundary.</span></span>|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="78df7-129">Bir ifadeyle koşullu eşleştirme</span><span class="sxs-lookup"><span data-stu-id="78df7-129">Conditional matching with an expression</span></span>

<span data-ttu-id="78df7-130">Bu dil öğesi, ilk desenle eşleşip eşleşmediğine bağlı olarak iki desenden birini eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="78df7-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="78df7-131">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="78df7-131">Its syntax is:</span></span>  

<span data-ttu-id="78df7-132">`(?(`*ifade* `)` *evet* `|` *hayır*`)`</span><span class="sxs-lookup"><span data-stu-id="78df7-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="78df7-133">*ifadenin* eşleşecek ilk desen olduğu yerde, *evet* *ifade* eşleşip eşleşmediği desendir ve *ifade* eşleşmiyorsa eşleşen isteğe bağlı desen *hayırdır.*</span><span class="sxs-lookup"><span data-stu-id="78df7-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="78df7-134">Normal ifade altyapısı *ifadeyi* sıfır genişlikli bir tasnı olarak ele alar; diğer bir deyişle, normal ifade altyapısı *ifadeyi*değerlendirdikten sonra giriş akışında ilerlemez.</span><span class="sxs-lookup"><span data-stu-id="78df7-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="78df7-135">Bu nedenle, bu yapı aşağıdakilere eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="78df7-135">Therefore, this construct is equivalent to the following:</span></span>

<span data-ttu-id="78df7-136">`(?(?=`*ifade* `)` *evet* `|` *hayır*`)`</span><span class="sxs-lookup"><span data-stu-id="78df7-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="78df7-137">`(?=` *ifadenin* `)` sıfır genişlikte bir tasnİf yapısı olduğu yerde.</span><span class="sxs-lookup"><span data-stu-id="78df7-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="78df7-138">(Daha fazla bilgi için yapı [yı gruplandırma](grouping-constructs-in-regular-expressions.md)ya da gruplandırma 'ya bakın.) Normal ifade altyapısı *ifadeyi* bir bağlantı noktası (sıfır genişlikte bir iddia) olarak yorumladığı için, *ifade* nin sıfır genişlikte bir tasnİf (daha fazla bilgi için, [Bkz. Çapalar)](anchors-in-regular-expressions.md)veya *evet'te*de bulunan bir alt ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="78df7-138">(For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="78df7-139">Aksi takdirde, *evet* deseni eşleşemez.</span><span class="sxs-lookup"><span data-stu-id="78df7-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78df7-140">*İfade* adlandırılmış veya numaralandırılmış bir yakalama grubuysa, değiştirme yapısı bir yakalama testi olarak yorumlanır; daha fazla bilgi için, [geçerli bir yakalama grubuna dayalı koşullu eşleştirme](#Conditional_Group)sonraki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="78df7-140">If *expression* is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="78df7-141">Başka bir deyişle, normal ifade altyapısı yakalanan alt dizeyle eşleşmeye çalışmaz, bunun yerine grubun varlığı veya yokluğu için test eder.</span><span class="sxs-lookup"><span data-stu-id="78df7-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
<span data-ttu-id="78df7-142">Aşağıdaki örnek, [ya/veya desen eşleştirmesinde &#124;bölümüyle](#Either_Or) görünen örneğin bir varyasyonudur.</span><span class="sxs-lookup"><span data-stu-id="78df7-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="78df7-143">Bir sözcük sınırından sonraki ilk üç karakterin iki basamaklı olup olmadığını belirlemek için koşullu eşleştirmeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="78df7-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="78df7-144">Varsa, bir ABD İşveren Kimlik Numarası (EIN) eşleşmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="78df7-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="78df7-145">Değilse, bir ABD Sosyal Güvenlik Numarası (SSN) eşleşmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="78df7-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

<span data-ttu-id="78df7-146">Normal ifade `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="78df7-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="78df7-147">Desen</span><span class="sxs-lookup"><span data-stu-id="78df7-147">Pattern</span></span>|<span data-ttu-id="78df7-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78df7-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="78df7-149">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="78df7-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="78df7-150">Sonraki üç karakterin iki basamaktan oluşup oluşmadığını ve ardından tireyi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="78df7-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="78df7-151">Önceki desen eşleşirse, iki basamak ve ardından bir tire ve ardından yedi basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="78df7-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="78df7-152">Önceki desen eşleşmiyorsa, üç ondalık basamak, bir tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="78df7-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="78df7-153">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="78df7-153">Match a word boundary.</span></span>|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="78df7-154">Yakalanan geçerli bir gruba göre koşullu eşleştirme</span><span class="sxs-lookup"><span data-stu-id="78df7-154">Conditional matching based on a valid captured group</span></span>

<span data-ttu-id="78df7-155">Bu dil öğesi, belirli bir yakalama grubuyla eşleşip eşleşmediğine bağlı olarak iki desenden birini eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="78df7-155">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="78df7-156">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="78df7-156">Its syntax is:</span></span>

<span data-ttu-id="78df7-157">`(?(`*isim* `)` *evet* `|` *hayır*`)`</span><span class="sxs-lookup"><span data-stu-id="78df7-157">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="78df7-158">or</span><span class="sxs-lookup"><span data-stu-id="78df7-158">or</span></span>

<span data-ttu-id="78df7-159">`(?(`*numara* `)` *evet* `|` *hayır*`)`</span><span class="sxs-lookup"><span data-stu-id="78df7-159">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="78df7-160">*adı* nisisim ve *sayı* bir yakalama grubunun numarasıdır, *evet* *ad* veya *sayı* eşleşip eşleşmediği ifadedir ve *hayır,* yoksa eşleşecek isteğe bağlı ifadedir.</span><span class="sxs-lookup"><span data-stu-id="78df7-160">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>

<span data-ttu-id="78df7-161">*Ad,* normal ifade deseninde kullanılan bir yakalama grubunun adıile uyuşmuyorsa, değiştirme yapısı önceki bölümde açıklandığı gibi bir ifade testi olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="78df7-161">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="78df7-162">Genellikle, bu *ifadenin* `false`.</span><span class="sxs-lookup"><span data-stu-id="78df7-162">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="78df7-163">*Sayı,* normal ifade deseninde kullanılan numaralanmış bir yakalama grubuna karşılık gelmiyorsa, normal ifade motoru . <xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="78df7-163">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="78df7-164">Aşağıdaki örnek, [ya/veya desen eşleştirmesinde &#124;bölümüyle](#Either_Or) görünen örneğin bir varyasyonudur.</span><span class="sxs-lookup"><span data-stu-id="78df7-164">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="78df7-165">İki basamaktan oluşan `n2` ve ardından tire yi izleyen bir yakalama grubu kullanır.</span><span class="sxs-lookup"><span data-stu-id="78df7-165">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="78df7-166">Alternation yapı, bu yakalama grubunun giriş dizesinde eşleşip eşleşmediğini sınar.</span><span class="sxs-lookup"><span data-stu-id="78df7-166">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="78df7-167">Varsa, alternation yapı dokuz basamaklı BIR ABD İşveren Kimlik Numarası (EIN) son yedi basamak eşleşmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="78df7-167">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="78df7-168">Değilse, dokuz basamaklı bir ABD Sosyal Güvenlik Numarası (SSN) eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="78df7-168">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

<span data-ttu-id="78df7-169">Normal ifade `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="78df7-169">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="78df7-170">Desen</span><span class="sxs-lookup"><span data-stu-id="78df7-170">Pattern</span></span>|<span data-ttu-id="78df7-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78df7-171">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="78df7-172">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="78df7-172">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="78df7-173">Eşleştirme sıfır veya iki basamaklı bir olay ardından bir tire.</span><span class="sxs-lookup"><span data-stu-id="78df7-173">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="78df7-174">Bu yakalama grubunu `n2`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="78df7-174">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="78df7-175">Giriş `n2` dizesinde eşleşip eşleşmediğini test edin.</span><span class="sxs-lookup"><span data-stu-id="78df7-175">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="78df7-176">Eşleştirildiyse, `n2` yedi ondalık basamakeşleştirin.</span><span class="sxs-lookup"><span data-stu-id="78df7-176">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="78df7-177">Eşleşmediyse, `n2` üç ondalık basamak, bir tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="78df7-177">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="78df7-178">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="78df7-178">Match a word boundary.</span></span>|  

<span data-ttu-id="78df7-179">Bu örneğin, adlandırılmış bir grup yerine numaralandırılmış bir grup kullanan bir varyasyonu aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="78df7-179">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="78df7-180">Onun düzenli ifade `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`deseni .</span><span class="sxs-lookup"><span data-stu-id="78df7-180">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="78df7-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78df7-181">See also</span></span>

- [<span data-ttu-id="78df7-182">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="78df7-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
