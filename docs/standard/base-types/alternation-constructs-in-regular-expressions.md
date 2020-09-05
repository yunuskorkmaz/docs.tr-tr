---
title: .NET normal Ifadelerinde değişim yapıları
description: Normal ifadelerde koşullu eşleme için değişim yapılarını nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 506c1cdeb577452628d67ab00df20dd30881f406
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495440"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="eb57f-103">Normal İfadelerdeki Değişim Yapıları</span><span class="sxs-lookup"><span data-stu-id="eb57f-103">Alternation Constructs in Regular Expressions</span></span>

<span data-ttu-id="eb57f-104">Değişim yapıları,/veya veya koşullu eşleştirmeyi etkinleştirmek için bir normal ifadeyi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="eb57f-105">.NET üç değişim yapılarını destekler:</span><span class="sxs-lookup"><span data-stu-id="eb57f-105">.NET supports three alternation constructs:</span></span>

- [<span data-ttu-id="eb57f-106">&#124;ile eşleşen desenler </span><span class="sxs-lookup"><span data-stu-id="eb57f-106">Pattern matching with &#124;</span></span>](#Either_Or)
- [<span data-ttu-id="eb57f-107">(? () İle koşullu eşleme ifade) Evet&#124;Hayır)</span><span class="sxs-lookup"><span data-stu-id="eb57f-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)
- [<span data-ttu-id="eb57f-108">Geçerli bir yakalanan gruba göre koşullu eşleme</span><span class="sxs-lookup"><span data-stu-id="eb57f-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a><span data-ttu-id="eb57f-109">&#124; ile eşleşen desenler</span><span class="sxs-lookup"><span data-stu-id="eb57f-109">Pattern Matching with &#124;</span></span>

<span data-ttu-id="eb57f-110">Dikey çubuk ( `|` ) karakterini, bir dizi desenden eşleştirmek için kullanabilirsiniz, burada `|` karakter her bir deseni ayırır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>

<span data-ttu-id="eb57f-111">Pozitif karakter sınıfı gibi, karakter, `|` bir dizi tek karakterden biriyle eşleştirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="eb57f-112">Aşağıdaki örnek, `|` bir dizede "gri" veya "gri" kelimelerin tekrarlamalarını bulmak için hem pozitif bir karakter sınıfını hem de karakteri ile eşleşen stili kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="eb57f-113">Bu durumda, `|` karakter daha ayrıntılı olan bir normal ifade üretir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

<span data-ttu-id="eb57f-114">Bu karakteri kullanan normal ifade, `|` `\bgr(a|e)y\b` Aşağıdaki tabloda gösterildiği gibi yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="eb57f-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="eb57f-115">Desen</span><span class="sxs-lookup"><span data-stu-id="eb57f-115">Pattern</span></span>|<span data-ttu-id="eb57f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb57f-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eb57f-117">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="eb57f-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="eb57f-118">"Gr" karakterlerini eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="eb57f-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="eb57f-119">Bir "a" veya "e" ile eşleş.</span><span class="sxs-lookup"><span data-stu-id="eb57f-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="eb57f-120">Bir sözcük sınırında "y" ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-120">Match a "y" on a word boundary.</span></span>|  

<span data-ttu-id="eb57f-121">`|`Karakter, ya da karakter değişmez değerleri ve normal ifade dili öğelerinin herhangi bir birleşimini içerebilen birden çok karakterle veya alt ifadeyle eşleşme gerçekleştirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="eb57f-122">(Karakter sınıfı bu işlevselliği sağlamaz.) Aşağıdaki örnek, bir `|` ABD sosyal güvenlik numarası (SSK), örneğin *ddd*gg dddd olan 9 basamaklı bir sayı - *dd* - *dddd*veya bir ABD işveren kimlik numarası (EIN) *dd*ayıklamak için kullanır - *ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="eb57f-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

<span data-ttu-id="eb57f-123">Normal ifade `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` Aşağıdaki tabloda gösterildiği gibi yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="eb57f-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>
  
|<span data-ttu-id="eb57f-124">Desen</span><span class="sxs-lookup"><span data-stu-id="eb57f-124">Pattern</span></span>|<span data-ttu-id="eb57f-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb57f-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eb57f-126">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="eb57f-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="eb57f-127">Aşağıdakilerden birini eşleştirin: iki ondalık basamak ve sonra da yedi ondalık basamak gelen tire. ya da üç ondalık basamak, kısa çizgi, iki ondalık basamak, başka bir tire ve dört ondalık basamak.</span><span class="sxs-lookup"><span data-stu-id="eb57f-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="eb57f-128">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-128">End the match at a word boundary.</span></span>|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="eb57f-129">Bir ifadeyle koşullu eşleme</span><span class="sxs-lookup"><span data-stu-id="eb57f-129">Conditional matching with an expression</span></span>

<span data-ttu-id="eb57f-130">Bu dil öğesi, bir başlangıç deseniyle eşleşmediğine bağlı olarak iki desenden birini eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="eb57f-131">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="eb57f-131">Its syntax is:</span></span>  

<span data-ttu-id="eb57f-132">`(?(`*ifade* `)` *Evet* `|` *Hayır*`)`</span><span class="sxs-lookup"><span data-stu-id="eb57f-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="eb57f-133">Burada ifadesi eşleşmek üzere Başlangıç *düzensiyse* , *Evet* *ifadesi* eşleşiyorsa eşleşen bir modeldir ve *hiçbir* değer *ifade* eşleşmezse eşleşen isteğe bağlı bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="eb57f-134">Normal ifade altyapısı, *ifadeyi* sıfır genişlikli bir onaylama olarak değerlendirir; diğer bir deyişle, normal ifade altyapısı, *ifade*değerlendirdikten sonra giriş akışında ilerlemez.</span><span class="sxs-lookup"><span data-stu-id="eb57f-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="eb57f-135">Bu nedenle, bu yapı aşağıdaki ile eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="eb57f-135">Therefore, this construct is equivalent to the following:</span></span>

<span data-ttu-id="eb57f-136">`(?(?=`*ifade* `)` *Evet* `|` *Hayır*`)`</span><span class="sxs-lookup"><span data-stu-id="eb57f-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="eb57f-137">Burada `(?=` *ifadesi* `)` sıfır genişlikli bir onaylama yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="eb57f-138">(Daha fazla bilgi için bkz. [yapıları gruplandırma](grouping-constructs-in-regular-expressions.md).) Normal ifade altyapısı *ifadeyi* bir tutturucu (sıfır genişlikli bir onaylama) olarak yorumladığı için, *ifadenin* sıfır genişlikli bir onaylama (daha fazla bilgi Için, bkz. [Tutturucular](anchors-in-regular-expressions.md)) veya *Evet*' de bulunan bir alt ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-138">(For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="eb57f-139">Aksi halde, *Evet* deseninin eşleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="eb57f-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb57f-140">İfade adlandırılmış veya numaralandırılmış yakalama *grubsiyse* , değişim yapısı yakalama testi olarak yorumlanır; daha fazla bilgi için, [geçerli bir yakalama grubuna göre koşullu eşleme](#Conditional_Group)başlıklı sonraki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="eb57f-140">If *expression* is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="eb57f-141">Diğer bir deyişle, normal ifade altyapısı yakalanan alt dizeyle eşleştirmeye çalışmaz, bunun yerine grubun varlığını veya yokluğunu sınar.</span><span class="sxs-lookup"><span data-stu-id="eb57f-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
<span data-ttu-id="eb57f-142">Aşağıdaki örnek, &#124;bölümünde bulunan [/veya düzeniyle eşleşen ](#Either_Or) bir örnek çeşitlemesi örneğidir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="eb57f-143">Bir sözcük sınırından sonraki ilk üç karakterin, kısa çizgi ve sonrasında iki basamak olup olmadığını anlamak için koşullu eşleştirmeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="eb57f-144">Bunlar ise, bir ABD Işveren kimlik numarası (EIN) ile eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="eb57f-145">Aksi takdirde, bir ABD sosyal güvenlik numarası (SSN) ile eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

<span data-ttu-id="eb57f-146">Normal ifade deseninin `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` Aşağıdaki tabloda gösterildiği gibi yorumlanması sağlanır:</span><span class="sxs-lookup"><span data-stu-id="eb57f-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="eb57f-147">Desen</span><span class="sxs-lookup"><span data-stu-id="eb57f-147">Pattern</span></span>|<span data-ttu-id="eb57f-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb57f-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eb57f-149">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="eb57f-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="eb57f-150">Sonraki üç karakterin iki basamakla ve sonra bir tire ile olup olmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="eb57f-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="eb57f-151">Önceki kalıp eşleşiyorsa, iki basamakla ve sonra da yedi basamakla eşleşen bir tire ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="eb57f-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="eb57f-152">Önceki model eşleşmiyorsa üç ondalık basamağı, kısa çizgi, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="eb57f-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="eb57f-153">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="eb57f-153">Match a word boundary.</span></span>|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="eb57f-154">Geçerli bir yakalanan gruba göre koşullu eşleme</span><span class="sxs-lookup"><span data-stu-id="eb57f-154">Conditional matching based on a valid captured group</span></span>

<span data-ttu-id="eb57f-155">Bu dil öğesi, belirtilen bir yakalama grubuyla eşleşip eşleşmediğine bağlı olarak iki desenden birini eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-155">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="eb57f-156">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="eb57f-156">Its syntax is:</span></span>

<span data-ttu-id="eb57f-157">`(?(`*ad* `)` *Evet* `|` *Hayır*`)`</span><span class="sxs-lookup"><span data-stu-id="eb57f-157">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="eb57f-158">veya</span><span class="sxs-lookup"><span data-stu-id="eb57f-158">or</span></span>

<span data-ttu-id="eb57f-159">`(?(`*sayı* `)` *Evet* `|` *Hayır*`)`</span><span class="sxs-lookup"><span data-stu-id="eb57f-159">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="eb57f-160">Burada *ad* , ad ve *sayı* bir yakalama grubu numarasıdır, *Evet* , *ad* veya *sayı* bir eşleşme içeriyorsa ve *Hayır* ise eşleşmesi gereken isteğe bağlı ifadedir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-160">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>

<span data-ttu-id="eb57f-161">*Ad* , normal ifade modelinde kullanılan bir yakalama grubunun adına karşılık gelmiyorsa, değişim yapısı, önceki bölümde açıklandığı gibi bir ifade testi olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-161">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="eb57f-162">Genellikle, bu *ifade* olarak değerlendirilir `false` .</span><span class="sxs-lookup"><span data-stu-id="eb57f-162">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="eb57f-163">*Sayı* , normal ifade deseninin kullandığı numaralandırılmış bir yakalama grubuna karşılık gelmiyorsa, normal ifade altyapısı bir oluşturur <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="eb57f-163">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="eb57f-164">Aşağıdaki örnek, &#124;bölümünde bulunan [/veya düzeniyle eşleşen ](#Either_Or) bir örnek çeşitlemesi örneğidir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-164">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="eb57f-165">İki basamaktan oluşan adlı bir yakalama grubu kullanır `n2` ve kısa çizgi gelir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-165">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="eb57f-166">Değişim yapısı, bu yakalama grubunun giriş dizesinde eşleştirilip eşleştirilmediğini test eder.</span><span class="sxs-lookup"><span data-stu-id="eb57f-166">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="eb57f-167">Varsa, değişim yapısı dokuz basamaklı bir ABD Işveren kimlik numarasının (EIN) son yedi basamağıyla eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-167">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="eb57f-168">Bu yoksa dokuz basamaklı bir ABD sosyal güvenlik numarası (SSK) ile eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="eb57f-168">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

<span data-ttu-id="eb57f-169">Normal ifade deseninin `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` Aşağıdaki tabloda gösterildiği gibi yorumlanması sağlanır:</span><span class="sxs-lookup"><span data-stu-id="eb57f-169">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="eb57f-170">Desen</span><span class="sxs-lookup"><span data-stu-id="eb57f-170">Pattern</span></span>|<span data-ttu-id="eb57f-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb57f-171">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="eb57f-172">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="eb57f-172">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="eb57f-173">Sıfır veya iki basamaklı bir oluşumu izleyen kısa çizgi ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="eb57f-173">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="eb57f-174">Bu yakalama grubunu adlandırın `n2` .</span><span class="sxs-lookup"><span data-stu-id="eb57f-174">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="eb57f-175">`n2`Giriş dizesinde eşleştirilip eşleştirilmediğini test edin.</span><span class="sxs-lookup"><span data-stu-id="eb57f-175">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="eb57f-176">`n2`Eşleştiriliyorsa yedi ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="eb57f-176">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="eb57f-177">`n2`Eşleştirilmedi, üç ondalık basamağı, kısa çizgi, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="eb57f-177">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="eb57f-178">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="eb57f-178">Match a word boundary.</span></span>|  

<span data-ttu-id="eb57f-179">Bu örneğin, adlandırılmış bir grup yerine numaralandırılmış bir grup kullanan bir çeşitlemesi aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb57f-179">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="eb57f-180">Normal ifade deseninin `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b` .</span><span class="sxs-lookup"><span data-stu-id="eb57f-180">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="eb57f-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb57f-181">See also</span></span>

- [<span data-ttu-id="eb57f-182">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="eb57f-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
