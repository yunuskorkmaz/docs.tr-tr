---
title: Normal İfadelerdeki Değişim Yapıları
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b653972fad71ce3a89c35598513b94f71fb4bf0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44063582"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="97b99-102">Normal İfadelerdeki Değişim Yapıları</span><span class="sxs-lookup"><span data-stu-id="97b99-102">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a> <span data-ttu-id="97b99-103">Değişim yapıları etkinleştirmek üzere bir normal ifade değiştirmek / veya veya koşullu eşleştirme.</span><span class="sxs-lookup"><span data-stu-id="97b99-103">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="97b99-104">.NET üç değişim yapıları destekler:</span><span class="sxs-lookup"><span data-stu-id="97b99-104">.NET supports three alternation constructs:</span></span>  
  
-   [<span data-ttu-id="97b99-105">İle desen eşleştirme&#124;</span><span class="sxs-lookup"><span data-stu-id="97b99-105">Pattern matching with &#124;</span></span>](#Either_Or)  
  
-   [<span data-ttu-id="97b99-106">Koşullu eşleşen (? () ifade) Evet&#124;yok)</span><span class="sxs-lookup"><span data-stu-id="97b99-106">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
-   [<span data-ttu-id="97b99-107">Yakalanan geçerli bir gruba bağlı koşullu eşleştirme</span><span class="sxs-lookup"><span data-stu-id="97b99-107">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="97b99-108">İle desen eşleştirme&#124;</span><span class="sxs-lookup"><span data-stu-id="97b99-108">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="97b99-109">Dikey çubuk kullanabilirsiniz (`|`) herhangi bir desen, bir dizi karakter burada `|` karakter her desen ayırır.</span><span class="sxs-lookup"><span data-stu-id="97b99-109">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="97b99-110">Pozitif karakter sınıfı gibi `|` karakteri, herhangi bir tek karakteri eşleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97b99-110">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="97b99-111">Aşağıdaki örnek, bir pozitif karakter sınıfını hem ya da kullanır. / veya deseni ile eşleşen `|` bir dizede sözcükler "gri" veya "gri" oluşumlarını bulmak için kullanılan karakter.</span><span class="sxs-lookup"><span data-stu-id="97b99-111">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="97b99-112">Bu durumda, `|` karakter daha ayrıntılıdır normal bir ifade oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97b99-112">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="97b99-113">Kullanan normal ifade `|` karakter `\bgr(a|e)y\b`, aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="97b99-113">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="97b99-114">Desen</span><span class="sxs-lookup"><span data-stu-id="97b99-114">Pattern</span></span>|<span data-ttu-id="97b99-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97b99-115">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97b99-116">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="97b99-116">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="97b99-117">"Gr" karakteriyle eşleş.</span><span class="sxs-lookup"><span data-stu-id="97b99-117">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="97b99-118">Bir "a" veya "e" ile eşleş.</span><span class="sxs-lookup"><span data-stu-id="97b99-118">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="97b99-119">Bir sözcük sınırında bir "y" eşleşir.</span><span class="sxs-lookup"><span data-stu-id="97b99-119">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="97b99-120">`|` Karakter de kullanılabilir ya da gerçekleştirmek için / veya birden çok karakter veya alt ifadeler karakter değişmez değerleri ve normal ifade dil öğesi herhangi bir birleşimini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="97b99-120">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="97b99-121">(Karakter sınıfı, bu işlevsellik sağlamaz.) Aşağıdaki örnekte `|` ya da bir ABD ayıklanacak karakter Sosyal Güvenlik numarası (9 basamaklı bir sayı biçiminde olan SSN), *ddd*-*GG*-*dddd*, veya bir ABD 9 basamaklı sayı biçimiyle İşveren Kimlik Numaranız'ne (EIN) *GG*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="97b99-121">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="97b99-122">Normal ifade `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="97b99-122">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="97b99-123">Desen</span><span class="sxs-lookup"><span data-stu-id="97b99-123">Pattern</span></span>|<span data-ttu-id="97b99-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97b99-124">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97b99-125">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="97b99-125">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="97b99-126">Aşağıdakilerden birini eşleşen: yedi ondalık basamak; ardından gelen bir tirenin ardından iki ondalık basamak veya üç ondalık basamak, tire, iki ondalık basamak, başka bir kısa çizgi ve dört ondalık basamak.</span><span class="sxs-lookup"><span data-stu-id="97b99-126">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="97b99-127">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="97b99-127">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="97b99-128">Başa dön</span><span class="sxs-lookup"><span data-stu-id="97b99-128">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="97b99-129">İfade Kullanarak Koşullu Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="97b99-129">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="97b99-130">Bu dil öğesi, bir ilk desen olup eşleşebilir bağlı olarak iki desenlerden birini eşleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="97b99-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="97b99-131">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="97b99-131">Its syntax is:</span></span>  
  
 <span data-ttu-id="97b99-132">`(?(` *ifade* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="97b99-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="97b99-133">Burada *ifade* eşleştirmek için ilk desen *Evet* deseni eşleşiyorsa *ifade* eşleştirilir, ve *hiçbir* isteğe bağlıdır deseni eşleşiyorsa *ifade* eşlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="97b99-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="97b99-134">Normal ifade altyapısı işler *ifade* değerlendirir, sonra sıfır genişlikli onaylama olarak; diğer bir deyişle, normal ifade motoru giriş akışında ilerleyin değil *ifade*.</span><span class="sxs-lookup"><span data-stu-id="97b99-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="97b99-135">Bu nedenle, bu yapı aşağıdakine eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="97b99-135">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="97b99-136">`(?(?=` *ifade* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="97b99-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="97b99-137">Burada `(?=` *ifade* `)` Sıfır genişlikli onaylama yapıdır.</span><span class="sxs-lookup"><span data-stu-id="97b99-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="97b99-138">(Daha fazla bilgi için [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Normal ifade altyapısı yorumladığından *ifade* bir bağlantı (bir sıfır genişlikli onaylama) olarak *ifade* ya da Sıfır genişlikli onaylama olmalıdır (daha fazla bilgi için [ Yer işaretleri](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) ya da bulunan bir alt ifade *Evet*.</span><span class="sxs-lookup"><span data-stu-id="97b99-138">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="97b99-139">Aksi takdirde, *Evet* deseni olamaz eşleşti.</span><span class="sxs-lookup"><span data-stu-id="97b99-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97b99-140">Varsa *ifade*bir adlandırışmış veya numaralandırılmış yakalama grubu, değişim yapısı yorumlanır yakalama test olarak; daha fazla bilgi için sonraki bölüme bakın [koşullu eşleştirme dayalı olarak bir geçerli bir yakalama grubundaki](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="97b99-140">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="97b99-141">Diğer bir deyişle, normal ifade altyapısı yakalanan alt dizeyi eşleştirmek çalışmaz ancak bunun yerine, varlığı veya yokluğu grubunun için test eder.</span><span class="sxs-lookup"><span data-stu-id="97b99-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="97b99-142">Aşağıdaki örnekte gösterildiği örnek bir çeşididir [ya da / veya desen eşleştirme ile &#124; ](#Either_Or) bölümü.</span><span class="sxs-lookup"><span data-stu-id="97b99-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="97b99-143">Bir sözcük sınırı sonra ilk üç karakter, kısa çizgi ve ardından iki basamak olup olmadığını belirlemek için koşullu eşleştirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="97b99-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="97b99-144">Böyle bir durumda, bir ABD eşleştirmeye çalışır İşveren Kimlik numarası (EIN).</span><span class="sxs-lookup"><span data-stu-id="97b99-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="97b99-145">Aksi halde, bir ABD eşleştirmeyi dener Sosyal Güvenlik numarası (SSN).</span><span class="sxs-lookup"><span data-stu-id="97b99-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="97b99-146">Normal ifade deseni `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="97b99-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="97b99-147">Desen</span><span class="sxs-lookup"><span data-stu-id="97b99-147">Pattern</span></span>|<span data-ttu-id="97b99-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97b99-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97b99-149">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="97b99-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="97b99-150">Sonraki üç karakter tireyle izleyen iki basamak oluşur olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="97b99-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="97b99-151">Önceki desenle eşleşiyorsa bir tire yedi haneli ve ardından iki basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="97b99-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="97b99-152">Önceki desenle eşleşmez, üç ondalık basamak, tire, iki ondalık basamak, başka bir tire ve dört ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="97b99-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="97b99-153">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="97b99-153">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="97b99-154">Başa dön</span><span class="sxs-lookup"><span data-stu-id="97b99-154">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="97b99-155">Yakalanan Geçerli Bir Gruba Göre Koşullu Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="97b99-155">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="97b99-156">Bu dil öğesi, belirtilen bir yakalama grubu olup olmadığını eşleşti bağlı olarak iki desenlerden birini eşleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="97b99-156">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="97b99-157">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="97b99-157">Its syntax is:</span></span>  
  
 <span data-ttu-id="97b99-158">`(?(` *adı* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="97b99-158">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="97b99-159">veya</span><span class="sxs-lookup"><span data-stu-id="97b99-159">or</span></span>  
  
 <span data-ttu-id="97b99-160">`(?(` *sayı* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="97b99-160">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="97b99-161">Burada *adı* adıdır ve *numarası* bir yakalama grubu sayısı *Evet* eşleşiyorsa ifadesidir *adı* veya *numarası* bir eşleşmeye sahip ve *hiçbir* kullanmıyorsa eşleştirmek için isteğe bağlı ifade.</span><span class="sxs-lookup"><span data-stu-id="97b99-161">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="97b99-162">Varsa *adı* gelmediğinden normal ifade deseninde kullanılan bir yakalama grubunun adına, değişim yapısı bir ifade testi olarak önceki bölümde açıklandığı gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="97b99-162">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="97b99-163">Genellikle, yani *ifade* değerlendiren `false`.</span><span class="sxs-lookup"><span data-stu-id="97b99-163">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="97b99-164">Varsa *numarası* normal ifade deseni, normal ifade motoru oluşturur kullanılan numaralandırılmış bir tutma grubu gelmiyor bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="97b99-164">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="97b99-165">Aşağıdaki örnekte gösterildiği örnek bir çeşididir [ya da / veya desen eşleştirme ile &#124; ](#Either_Or) bölümü.</span><span class="sxs-lookup"><span data-stu-id="97b99-165">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="97b99-166">Adlı bir yakalama grubunu kullanan `n2` tireyle izleyen iki basamak içerir.</span><span class="sxs-lookup"><span data-stu-id="97b99-166">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="97b99-167">Değişim, giriş dizesinde Bu yakalama grubuyla eşleşen olup olmadığını testler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97b99-167">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="97b99-168">Varsa, değişim oluşturmak dokuz basamak ABD son yedi rakamı eşleşmeyi dener İşveren Kimlik numarası (EIN).</span><span class="sxs-lookup"><span data-stu-id="97b99-168">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="97b99-169">Sahip değil, dokuz basamak ABD eşleştirmeye çalışır Sosyal Güvenlik numarası (SSN).</span><span class="sxs-lookup"><span data-stu-id="97b99-169">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="97b99-170">Normal ifade deseni `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="97b99-170">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="97b99-171">Desen</span><span class="sxs-lookup"><span data-stu-id="97b99-171">Pattern</span></span>|<span data-ttu-id="97b99-172">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97b99-172">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97b99-173">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="97b99-173">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="97b99-174">İki basamaklı bir tire işaretiyle ardından sıfır veya bir oluşumunu eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="97b99-174">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="97b99-175">Bu yakalama grubu adı `n2`.</span><span class="sxs-lookup"><span data-stu-id="97b99-175">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="97b99-176">Test olmadığını `n2` giriş dizesinde eşleştirildi.</span><span class="sxs-lookup"><span data-stu-id="97b99-176">Test whether `n2` was matched in the input string.</span></span>|  
|`)\d{7}`|<span data-ttu-id="97b99-177">Varsa `n2` olan yedi ondalık basamak eşleşen, eşleşen.</span><span class="sxs-lookup"><span data-stu-id="97b99-177">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="97b99-178">Varsa `n2` eşleşmeyen, eşleşen üç ondalık basamak, tire, iki ondalık basamak, başka bir kısa çizgi ve dört ondalık basamak.</span><span class="sxs-lookup"><span data-stu-id="97b99-178">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="97b99-179">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="97b99-179">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="97b99-180">Bu örnek yerine adlandırılmış bir grubu numaralandırılmış bir grubu kullanan bir çeşitlemesi, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="97b99-180">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="97b99-181">Normal ifade desenine olan `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="97b99-181">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="97b99-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97b99-182">See also</span></span>

- [<span data-ttu-id="97b99-183">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="97b99-183">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
