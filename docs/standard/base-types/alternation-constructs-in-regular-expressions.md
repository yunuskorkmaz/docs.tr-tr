---
title: .NET normal ifadelerindeki değişim yapıları
description: Değişim yapıları normal ifadeler koşullu eşleştirme için kullanmayı öğrenin.
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
ms.custom: seodec18
ms.openlocfilehash: 6d9761d2e9904e865e7f6a17526327e1b04a1597
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698882"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="101e8-103">Normal İfadelerdeki Değişim Yapıları</span><span class="sxs-lookup"><span data-stu-id="101e8-103">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a> <span data-ttu-id="101e8-104">Değişim yapıları etkinleştirmek üzere bir normal ifade değiştirmek / veya veya koşullu eşleştirme.</span><span class="sxs-lookup"><span data-stu-id="101e8-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="101e8-105">.NET üç değişim yapıları destekler:</span><span class="sxs-lookup"><span data-stu-id="101e8-105">.NET supports three alternation constructs:</span></span>  
  
- [<span data-ttu-id="101e8-106">İle desen eşleştirme&#124;</span><span class="sxs-lookup"><span data-stu-id="101e8-106">Pattern matching with &#124;</span></span>](#Either_Or)  
  
- [<span data-ttu-id="101e8-107">Koşullu eşleşen (? () ifade) Evet&#124;yok)</span><span class="sxs-lookup"><span data-stu-id="101e8-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
- [<span data-ttu-id="101e8-108">Yakalanan geçerli bir gruba bağlı koşullu eşleştirme</span><span class="sxs-lookup"><span data-stu-id="101e8-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="101e8-109">İle desen eşleştirme&#124;</span><span class="sxs-lookup"><span data-stu-id="101e8-109">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="101e8-110">Dikey çubuk kullanabilirsiniz (`|`) herhangi bir desen, bir dizi karakter burada `|` karakter her desen ayırır.</span><span class="sxs-lookup"><span data-stu-id="101e8-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="101e8-111">Pozitif karakter sınıfı gibi `|` karakteri, herhangi bir tek karakteri eşleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="101e8-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="101e8-112">Aşağıdaki örnek, bir pozitif karakter sınıfını hem ya da kullanır. / veya deseni ile eşleşen `|` bir dizede sözcükler "gri" veya "gri" oluşumlarını bulmak için kullanılan karakter.</span><span class="sxs-lookup"><span data-stu-id="101e8-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="101e8-113">Bu durumda, `|` karakter daha ayrıntılıdır normal bir ifade oluşturur.</span><span class="sxs-lookup"><span data-stu-id="101e8-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="101e8-114">Kullanan normal ifade `|` karakter `\bgr(a|e)y\b`, aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="101e8-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="101e8-115">Desen</span><span class="sxs-lookup"><span data-stu-id="101e8-115">Pattern</span></span>|<span data-ttu-id="101e8-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="101e8-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="101e8-117">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="101e8-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="101e8-118">"Gr" karakteriyle eşleş.</span><span class="sxs-lookup"><span data-stu-id="101e8-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="101e8-119">Bir "a" veya "e" ile eşleş.</span><span class="sxs-lookup"><span data-stu-id="101e8-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="101e8-120">Bir sözcük sınırında bir "y" eşleşir.</span><span class="sxs-lookup"><span data-stu-id="101e8-120">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="101e8-121">`|` Karakter de kullanılabilir ya da gerçekleştirmek için / veya birden çok karakter veya alt ifadeler karakter değişmez değerleri ve normal ifade dil öğesi herhangi bir birleşimini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="101e8-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="101e8-122">(Karakter sınıfı, bu işlevsellik sağlamaz.) Aşağıdaki örnekte `|` ya da bir ABD ayıklanacak karakter Sosyal Güvenlik numarası (9 basamaklı bir sayı biçiminde olan SSN), *ddd*-*GG*-*dddd*, veya bir ABD 9 basamaklı sayı biçimiyle İşveren Kimlik Numaranız'ne (EIN) *GG*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="101e8-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="101e8-123">Normal ifade `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="101e8-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="101e8-124">Desen</span><span class="sxs-lookup"><span data-stu-id="101e8-124">Pattern</span></span>|<span data-ttu-id="101e8-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="101e8-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="101e8-126">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="101e8-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="101e8-127">Aşağıdakilerden birini eşleşen: yedi ondalık basamak; ardından gelen bir tirenin ardından iki ondalık basamak veya üç ondalık basamak, tire, iki ondalık basamak, başka bir kısa çizgi ve dört ondalık basamak.</span><span class="sxs-lookup"><span data-stu-id="101e8-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="101e8-128">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="101e8-128">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="101e8-129">Başa dön</span><span class="sxs-lookup"><span data-stu-id="101e8-129">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="101e8-130">İfade Kullanarak Koşullu Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="101e8-130">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="101e8-131">Bu dil öğesi, bir ilk desen olup eşleşebilir bağlı olarak iki desenlerden birini eşleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="101e8-131">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="101e8-132">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="101e8-132">Its syntax is:</span></span>  
  
 <span data-ttu-id="101e8-133">`(?(` *ifade* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="101e8-133">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="101e8-134">Burada *ifade* eşleştirmek için ilk desen *Evet* deseni eşleşiyorsa *ifade* eşleştirilir, ve *hiçbir* isteğe bağlıdır deseni eşleşiyorsa *ifade* eşlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="101e8-134">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="101e8-135">Normal ifade altyapısı işler *ifade* değerlendirir, sonra sıfır genişlikli onaylama olarak; diğer bir deyişle, normal ifade motoru giriş akışında ilerleyin değil *ifade*.</span><span class="sxs-lookup"><span data-stu-id="101e8-135">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="101e8-136">Bu nedenle, bu yapı aşağıdakine eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="101e8-136">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="101e8-137">`(?(?=` *ifade* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="101e8-137">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="101e8-138">Burada `(?=` *ifade* `)` Sıfır genişlikli onaylama yapıdır.</span><span class="sxs-lookup"><span data-stu-id="101e8-138">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="101e8-139">(Daha fazla bilgi için [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Normal ifade altyapısı yorumladığından *ifade* bir bağlantı (bir sıfır genişlikli onaylama) olarak *ifade* ya da Sıfır genişlikli onaylama olmalıdır (daha fazla bilgi için [ Yer işaretleri](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) ya da bulunan bir alt ifade *Evet*.</span><span class="sxs-lookup"><span data-stu-id="101e8-139">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="101e8-140">Aksi takdirde, *Evet* deseni olamaz eşleşti.</span><span class="sxs-lookup"><span data-stu-id="101e8-140">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="101e8-141">Varsa *ifade*bir adlandırışmış veya numaralandırılmış yakalama grubu, değişim yapısı yorumlanır yakalama test olarak; daha fazla bilgi için sonraki bölüme bakın [koşullu eşleştirme dayalı olarak bir geçerli bir yakalama grubundaki](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="101e8-141">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="101e8-142">Diğer bir deyişle, normal ifade altyapısı yakalanan alt dizeyi eşleştirmek çalışmaz ancak bunun yerine, varlığı veya yokluğu grubunun için test eder.</span><span class="sxs-lookup"><span data-stu-id="101e8-142">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="101e8-143">Aşağıdaki örnekte gösterildiği örnek bir çeşididir [ya da / veya desen eşleştirme ile &#124; ](#Either_Or) bölümü.</span><span class="sxs-lookup"><span data-stu-id="101e8-143">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="101e8-144">Bir sözcük sınırı sonra ilk üç karakter, kısa çizgi ve ardından iki basamak olup olmadığını belirlemek için koşullu eşleştirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="101e8-144">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="101e8-145">Böyle bir durumda, bir ABD eşleştirmeye çalışır İşveren Kimlik numarası (EIN).</span><span class="sxs-lookup"><span data-stu-id="101e8-145">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="101e8-146">Aksi halde, bir ABD eşleştirmeyi dener Sosyal Güvenlik numarası (SSN).</span><span class="sxs-lookup"><span data-stu-id="101e8-146">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="101e8-147">Normal ifade deseni `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="101e8-147">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="101e8-148">Desen</span><span class="sxs-lookup"><span data-stu-id="101e8-148">Pattern</span></span>|<span data-ttu-id="101e8-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="101e8-149">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="101e8-150">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="101e8-150">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="101e8-151">Sonraki üç karakter tireyle izleyen iki basamak oluşur olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="101e8-151">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="101e8-152">Önceki desenle eşleşiyorsa bir tire yedi haneli ve ardından iki basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="101e8-152">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="101e8-153">Önceki desenle eşleşmez, üç ondalık basamak, tire, iki ondalık basamak, başka bir tire ve dört ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="101e8-153">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="101e8-154">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="101e8-154">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="101e8-155">Başa dön</span><span class="sxs-lookup"><span data-stu-id="101e8-155">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="101e8-156">Yakalanan Geçerli Bir Gruba Göre Koşullu Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="101e8-156">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="101e8-157">Bu dil öğesi, belirtilen bir yakalama grubu olup olmadığını eşleşti bağlı olarak iki desenlerden birini eşleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="101e8-157">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="101e8-158">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="101e8-158">Its syntax is:</span></span>  
  
 <span data-ttu-id="101e8-159">`(?(` *adı* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="101e8-159">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="101e8-160">veya</span><span class="sxs-lookup"><span data-stu-id="101e8-160">or</span></span>  
  
 <span data-ttu-id="101e8-161">`(?(` *sayı* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="101e8-161">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="101e8-162">Burada *adı* adıdır ve *numarası* bir yakalama grubu sayısı *Evet* eşleşiyorsa ifadesidir *adı* veya *numarası* bir eşleşmeye sahip ve *hiçbir* kullanmıyorsa eşleştirmek için isteğe bağlı ifade.</span><span class="sxs-lookup"><span data-stu-id="101e8-162">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="101e8-163">Varsa *adı* gelmediğinden normal ifade deseninde kullanılan bir yakalama grubunun adına, değişim yapısı bir ifade testi olarak önceki bölümde açıklandığı gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="101e8-163">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="101e8-164">Genellikle, yani *ifade* değerlendiren `false`.</span><span class="sxs-lookup"><span data-stu-id="101e8-164">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="101e8-165">Varsa *numarası* normal ifade deseni, normal ifade motoru oluşturur kullanılan numaralandırılmış bir tutma grubu gelmiyor bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="101e8-165">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="101e8-166">Aşağıdaki örnekte gösterildiği örnek bir çeşididir [ya da / veya desen eşleştirme ile &#124; ](#Either_Or) bölümü.</span><span class="sxs-lookup"><span data-stu-id="101e8-166">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="101e8-167">Adlı bir yakalama grubunu kullanan `n2` tireyle izleyen iki basamak içerir.</span><span class="sxs-lookup"><span data-stu-id="101e8-167">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="101e8-168">Değişim, giriş dizesinde Bu yakalama grubuyla eşleşen olup olmadığını testler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="101e8-168">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="101e8-169">Varsa, değişim oluşturmak dokuz basamak ABD son yedi rakamı eşleşmeyi dener İşveren Kimlik numarası (EIN).</span><span class="sxs-lookup"><span data-stu-id="101e8-169">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="101e8-170">Sahip değil, dokuz basamak ABD eşleştirmeye çalışır Sosyal Güvenlik numarası (SSN).</span><span class="sxs-lookup"><span data-stu-id="101e8-170">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="101e8-171">Normal ifade deseni `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="101e8-171">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="101e8-172">Desen</span><span class="sxs-lookup"><span data-stu-id="101e8-172">Pattern</span></span>|<span data-ttu-id="101e8-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="101e8-173">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="101e8-174">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="101e8-174">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="101e8-175">İki basamaklı bir tire işaretiyle ardından sıfır veya bir oluşumunu eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="101e8-175">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="101e8-176">Bu yakalama grubu adı `n2`.</span><span class="sxs-lookup"><span data-stu-id="101e8-176">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="101e8-177">Test olmadığını `n2` giriş dizesinde eşleştirildi.</span><span class="sxs-lookup"><span data-stu-id="101e8-177">Test whether `n2` was matched in the input string.</span></span>|  
|`)\d{7}`|<span data-ttu-id="101e8-178">Varsa `n2` olan yedi ondalık basamak eşleşen, eşleşen.</span><span class="sxs-lookup"><span data-stu-id="101e8-178">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="101e8-179">Varsa `n2` eşleşmeyen, eşleşen üç ondalık basamak, tire, iki ondalık basamak, başka bir kısa çizgi ve dört ondalık basamak.</span><span class="sxs-lookup"><span data-stu-id="101e8-179">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="101e8-180">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="101e8-180">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="101e8-181">Bu örnek yerine adlandırılmış bir grubu numaralandırılmış bir grubu kullanan bir çeşitlemesi, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="101e8-181">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="101e8-182">Normal ifade desenine olan `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="101e8-182">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="101e8-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="101e8-183">See also</span></span>

- [<span data-ttu-id="101e8-184">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="101e8-184">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
