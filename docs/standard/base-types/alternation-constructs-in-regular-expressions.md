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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 560597770d667cf8c7668bf2338ac4bac3eb192f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968567"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="c304c-103">Normal İfadelerdeki Değişim Yapıları</span><span class="sxs-lookup"><span data-stu-id="c304c-103">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a><span data-ttu-id="c304c-104">Değişim yapıları,/veya veya koşullu eşleştirmeyi etkinleştirmek için bir normal ifadeyi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c304c-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="c304c-105">.NET üç değişim yapılarını destekler:</span><span class="sxs-lookup"><span data-stu-id="c304c-105">.NET supports three alternation constructs:</span></span>  
  
- [<span data-ttu-id="c304c-106">İle eşleşen desenler&#124;</span><span class="sxs-lookup"><span data-stu-id="c304c-106">Pattern matching with &#124;</span></span>](#Either_Or)  
  
- [<span data-ttu-id="c304c-107">(? () İle koşullu eşleme ifade) Evet&#124;Hayır)</span><span class="sxs-lookup"><span data-stu-id="c304c-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
- [<span data-ttu-id="c304c-108">Geçerli bir yakalanan gruba göre koşullu eşleme</span><span class="sxs-lookup"><span data-stu-id="c304c-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="c304c-109">İle eşleşen desenler&#124;</span><span class="sxs-lookup"><span data-stu-id="c304c-109">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="c304c-110">Dikey çubuk (`|`) karakterini, bir dizi desenden eşleştirmek için kullanabilirsiniz, `|` burada karakter her bir deseni ayırır.</span><span class="sxs-lookup"><span data-stu-id="c304c-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="c304c-111">Pozitif karakter sınıfı gibi, `|` karakter, bir dizi tek karakterden biriyle eşleştirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c304c-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="c304c-112">Aşağıdaki örnek, bir dizede "gri" veya "gri" kelimelerin tekrarlamalarını bulmak `|` için hem pozitif bir karakter sınıfını hem de karakteri ile eşleşen stili kullanır.</span><span class="sxs-lookup"><span data-stu-id="c304c-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="c304c-113">Bu durumda, `|` karakter daha ayrıntılı olan bir normal ifade üretir.</span><span class="sxs-lookup"><span data-stu-id="c304c-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="c304c-114">`|` Bu`\bgr(a|e)y\b`karakteri kullanan normal ifade, aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="c304c-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="c304c-115">Desen</span><span class="sxs-lookup"><span data-stu-id="c304c-115">Pattern</span></span>|<span data-ttu-id="c304c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c304c-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c304c-117">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="c304c-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="c304c-118">"Gr" karakterlerini eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="c304c-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="c304c-119">Bir "a" veya "e" ile eşleş.</span><span class="sxs-lookup"><span data-stu-id="c304c-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="c304c-120">Bir sözcük sınırında "y" ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="c304c-120">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="c304c-121">Karakter `|` , ya da karakter değişmez değerleri ve normal ifade dili öğelerinin herhangi bir birleşimini içerebilen birden çok karakterle veya alt ifadeyle eşleşme gerçekleştirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c304c-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="c304c-122">(Karakter sınıfı bu işlevselliği sağlamaz.) Aşağıdaki örnek, bir ABD `|` 'yi ayıklamak için karakteri kullanır Bir 9 basamaklı bir sayı olan sosyal güvenlik numarası (SSN), *ddd*-*gg*-*gggg*veya ABD 7 basamaklı bir sayı-olan işveren kimlik numarası (EIN).</span><span class="sxs-lookup"><span data-stu-id="c304c-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="c304c-123">Normal ifade `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="c304c-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="c304c-124">Desen</span><span class="sxs-lookup"><span data-stu-id="c304c-124">Pattern</span></span>|<span data-ttu-id="c304c-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c304c-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c304c-126">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="c304c-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="c304c-127">Aşağıdakilerden birini eşleştirin: iki ondalık basamak ve sonra da yedi ondalık basamak gelen tire. ya da üç ondalık basamak, kısa çizgi, iki ondalık basamak, başka bir tire ve dört ondalık basamak.</span><span class="sxs-lookup"><span data-stu-id="c304c-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="c304c-128">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="c304c-128">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="c304c-129">Başa dön</span><span class="sxs-lookup"><span data-stu-id="c304c-129">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="c304c-130">İfade Kullanarak Koşullu Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="c304c-130">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="c304c-131">Bu dil öğesi, bir başlangıç deseniyle eşleşmediğine bağlı olarak iki desenden birini eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="c304c-131">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="c304c-132">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="c304c-132">Its syntax is:</span></span>  
  
 <span data-ttu-id="c304c-133">`(?(`*ifade* *Evet* Hayır `)` `|``)`</span><span class="sxs-lookup"><span data-stu-id="c304c-133">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="c304c-134">Burada *ifadesi* eşleşmek üzere başlangıç düzensiyse, *Evet* *ifadesi* eşleşiyorsa eşleşen bir modeldir ve *hiçbir* değer *ifade* eşleşmezse eşleşen isteğe bağlı bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="c304c-134">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="c304c-135">Normal ifade altyapısı, *ifadeyi* sıfır genişlikli bir onaylama olarak değerlendirir; diğer bir deyişle, normal ifade altyapısı, *ifade*değerlendirdikten sonra giriş akışında ilerlemez.</span><span class="sxs-lookup"><span data-stu-id="c304c-135">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="c304c-136">Bu nedenle, bu yapı aşağıdaki ile eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="c304c-136">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="c304c-137">`(?(?=`*ifade* *Evet* Hayır `)` `|``)`</span><span class="sxs-lookup"><span data-stu-id="c304c-137">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="c304c-138">Burada `(?=` ifadesi`)` sıfır genişlikli bir onaylama yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="c304c-138">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="c304c-139">(Daha fazla bilgi için bkz. [yapıları gruplandırma](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Normal ifade altyapısı *ifadeyi* bir tutturucu (sıfır genişlikli bir onaylama) olarak yorumladığı için, *ifadenin* sıfır genişlikli bir onaylama (daha fazla bilgi Için, bkz. [Tutturucular](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) veya içinde de bulunan bir alt ifade olması gerekir. *Evet*.</span><span class="sxs-lookup"><span data-stu-id="c304c-139">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="c304c-140">Aksi halde, *Evet* deseninin eşleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="c304c-140">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c304c-141">*İfade*adlandırılmış veya numaralandırılmış yakalama grubsiyse, değişim yapısı yakalama testi olarak yorumlanır; daha fazla bilgi için, [geçerli bir yakalama grubuna göre koşullu eşleme](#Conditional_Group)başlıklı sonraki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="c304c-141">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="c304c-142">Diğer bir deyişle, normal ifade altyapısı yakalanan alt dizeyle eşleştirmeye çalışmaz, bunun yerine grubun varlığını veya yokluğunu sınar.</span><span class="sxs-lookup"><span data-stu-id="c304c-142">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="c304c-143">Aşağıdaki örnek, [ile &#124; eşleşen bir/veya desenli](#Either_Or) bir örnek çeşitlemesi olan bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="c304c-143">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="c304c-144">Bir sözcük sınırından sonraki ilk üç karakterin, kısa çizgi ve sonrasında iki basamak olup olmadığını anlamak için koşullu eşleştirmeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c304c-144">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="c304c-145">Varsa, bir ABD ile eşleştirmeye çalışır İşveren Kimlik numarası (EIN).</span><span class="sxs-lookup"><span data-stu-id="c304c-145">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="c304c-146">Aksi takdirde, bir ABD ile eşleştirmeye çalışır Sosyal güvenlik numarası (SSK).</span><span class="sxs-lookup"><span data-stu-id="c304c-146">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="c304c-147">Normal ifade deseninin `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="c304c-147">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="c304c-148">Desen</span><span class="sxs-lookup"><span data-stu-id="c304c-148">Pattern</span></span>|<span data-ttu-id="c304c-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c304c-149">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c304c-150">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="c304c-150">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="c304c-151">Sonraki üç karakterin iki basamakla ve sonra bir tire ile olup olmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="c304c-151">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="c304c-152">Önceki kalıp eşleşiyorsa, iki basamakla ve sonra da yedi basamakla eşleşen bir tire ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="c304c-152">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="c304c-153">Önceki model eşleşmiyorsa üç ondalık basamağı, kısa çizgi, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="c304c-153">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="c304c-154">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="c304c-154">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="c304c-155">Başa dön</span><span class="sxs-lookup"><span data-stu-id="c304c-155">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="c304c-156">Yakalanan Geçerli Bir Gruba Göre Koşullu Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="c304c-156">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="c304c-157">Bu dil öğesi, belirtilen bir yakalama grubuyla eşleşip eşleşmediğine bağlı olarak iki desenden birini eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="c304c-157">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="c304c-158">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="c304c-158">Its syntax is:</span></span>  
  
 <span data-ttu-id="c304c-159">`(?(`*ad* *Evet* Hayır `)` `|``)`</span><span class="sxs-lookup"><span data-stu-id="c304c-159">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="c304c-160">veya</span><span class="sxs-lookup"><span data-stu-id="c304c-160">or</span></span>  
  
 <span data-ttu-id="c304c-161">`(?(`*sayı* *Evet* Hayır `)` `|``)`</span><span class="sxs-lookup"><span data-stu-id="c304c-161">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="c304c-162">Burada *ad* , ad ve *sayı* bir yakalama grubu numarasıdır, *Evet* , *ad* veya *sayı* bir eşleşme içeriyorsa ve *Hayır* ise eşleşmesi gereken isteğe bağlı ifadedir.</span><span class="sxs-lookup"><span data-stu-id="c304c-162">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="c304c-163">*Ad* , normal ifade modelinde kullanılan bir yakalama grubunun adına karşılık gelmiyorsa, değişim yapısı, önceki bölümde açıklandığı gibi bir ifade testi olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="c304c-163">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="c304c-164">Genellikle, bu *ifade* olarak `false`değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c304c-164">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="c304c-165">*Sayı* , normal ifade deseninin kullandığı numaralandırılmış bir yakalama grubuna karşılık gelmiyorsa, normal ifade altyapısı bir <xref:System.ArgumentException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c304c-165">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="c304c-166">Aşağıdaki örnek, [ile &#124; eşleşen bir/veya desenli](#Either_Or) bir örnek çeşitlemesi olan bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="c304c-166">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="c304c-167">İki basamaktan oluşan adlı `n2` bir yakalama grubu kullanır ve kısa çizgi gelir.</span><span class="sxs-lookup"><span data-stu-id="c304c-167">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="c304c-168">Değişim yapısı, bu yakalama grubunun giriş dizesinde eşleştirilip eşleştirilmediğini test eder.</span><span class="sxs-lookup"><span data-stu-id="c304c-168">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="c304c-169">Varsa, değişim yapısı dokuz basamaklı ABD 'nin son yedi basamağıyla eşleştirmeye çalışır İşveren Kimlik numarası (EIN).</span><span class="sxs-lookup"><span data-stu-id="c304c-169">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="c304c-170">Bu yoksa dokuz basamaklı bir ABD ile eşleştirmeye çalışır Sosyal güvenlik numarası (SSK).</span><span class="sxs-lookup"><span data-stu-id="c304c-170">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="c304c-171">Normal ifade deseninin `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="c304c-171">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="c304c-172">Desen</span><span class="sxs-lookup"><span data-stu-id="c304c-172">Pattern</span></span>|<span data-ttu-id="c304c-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c304c-173">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c304c-174">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="c304c-174">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="c304c-175">Sıfır veya iki basamaklı bir oluşumu izleyen kısa çizgi ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="c304c-175">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="c304c-176">Bu yakalama grubunu `n2`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c304c-176">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="c304c-177">Giriş dizesinde `n2` eşleştirilip eşleştirilmediğini test edin.</span><span class="sxs-lookup"><span data-stu-id="c304c-177">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="c304c-178">Eşleştiriliyorsa `n2` yedi ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="c304c-178">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="c304c-179">`n2` Eşleştirilmedi, üç ondalık basamağı, kısa çizgi, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="c304c-179">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="c304c-180">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="c304c-180">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="c304c-181">Bu örneğin, adlandırılmış bir grup yerine numaralandırılmış bir grup kullanan bir çeşitlemesi aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c304c-181">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="c304c-182">Normal ifade deseninin `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="c304c-182">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="c304c-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c304c-183">See also</span></span>

- [<span data-ttu-id="c304c-184">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="c304c-184">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
