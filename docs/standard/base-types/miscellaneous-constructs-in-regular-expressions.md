---
description: 'Daha fazla bilgi edinin: normal Ifadelerde çeşitli yapılar'
title: Normal İfadelerdeki Çeşitli Yapılar
ms.date: 03/30/2017
ms.topic: conceptual
dev_langs:
- csharp
- vb
helpviewer_keywords:
- constructs, miscellaneous
- .NET regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
ms.openlocfilehash: 68e17e406ea22a52cd7b121c60595667cf054290
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642765"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a><span data-ttu-id="99bcf-103">Normal İfadelerdeki Çeşitli Yapılar</span><span class="sxs-lookup"><span data-stu-id="99bcf-103">Miscellaneous Constructs in Regular Expressions</span></span>

<span data-ttu-id="99bcf-104">.NET 'teki normal ifadeler üç çeşitli dil yapılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="99bcf-104">Regular expressions in .NET include three miscellaneous language constructs.</span></span> <span data-ttu-id="99bcf-105">Bir normal ifade deseninin ortasında belirli eşleştirme seçeneklerini etkinleştirmenizi veya devre dışı bırakmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="99bcf-105">One lets you enable or disable particular matching options in the middle of a regular expression pattern.</span></span> <span data-ttu-id="99bcf-106">Kalan iki, açıklamaları normal bir ifadeye eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="99bcf-106">The remaining two let you include comments in a regular expression.</span></span>  
  
## <a name="inline-options"></a><span data-ttu-id="99bcf-107">Satır içi seçenekler</span><span class="sxs-lookup"><span data-stu-id="99bcf-107">Inline Options</span></span>  

 <span data-ttu-id="99bcf-108">Sözdizimini kullanarak normal bir ifadenin bir parçası için belirli bir model eşleştirme seçeneklerini ayarlayabilir veya devre dışı bırakabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="99bcf-108">You can set or disable specific pattern matching options for part of a regular expression by using the syntax</span></span>  
  
`(?imnsx-imnsx)`  
  
 <span data-ttu-id="99bcf-109">Soru işaretinden sonra etkinleştirmek istediğiniz seçenekleri ve eksi işaretinden sonra devre dışı bırakmak istediğiniz seçenekleri listeleyin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-109">You list the options you want to enable after the question mark, and the options you want to disable after the minus sign.</span></span> <span data-ttu-id="99bcf-110">Aşağıdaki tabloda her bir seçenek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99bcf-110">The following table describes each option.</span></span> <span data-ttu-id="99bcf-111">Her seçenek hakkında daha fazla bilgi için bkz. [normal Ifade seçenekleri](regular-expression-options.md).</span><span class="sxs-lookup"><span data-stu-id="99bcf-111">For more information about each option, see [Regular Expression Options](regular-expression-options.md).</span></span>  
  
|<span data-ttu-id="99bcf-112">Seçenek</span><span class="sxs-lookup"><span data-stu-id="99bcf-112">Option</span></span>|<span data-ttu-id="99bcf-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99bcf-113">Description</span></span>|  
|------------|-----------------|  
|`i`|<span data-ttu-id="99bcf-114">Büyük/küçük harfe duyarsız eşleşme.</span><span class="sxs-lookup"><span data-stu-id="99bcf-114">Case-insensitive matching.</span></span>|  
|`m`|<span data-ttu-id="99bcf-115">Çok satırlı mod.</span><span class="sxs-lookup"><span data-stu-id="99bcf-115">Multiline mode.</span></span>|  
|`n`|<span data-ttu-id="99bcf-116">Yalnızca açık yakalamaları.</span><span class="sxs-lookup"><span data-stu-id="99bcf-116">Explicit captures only.</span></span> <span data-ttu-id="99bcf-117">(Parantezler, yakalama grupları olarak davranmaz.)</span><span class="sxs-lookup"><span data-stu-id="99bcf-117">(Parentheses do not act as capturing groups.)</span></span>|  
|`s`|<span data-ttu-id="99bcf-118">Tek satırlık mod.</span><span class="sxs-lookup"><span data-stu-id="99bcf-118">Single-line mode.</span></span>|  
|`x`|<span data-ttu-id="99bcf-119">Kaçışsız boşluk işaretini yoksayın ve x-Mode yorumlara izin verin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-119">Ignore unescaped white space, and allow x-mode comments.</span></span>|  
  
 <span data-ttu-id="99bcf-120">Yapı tarafından tanımlanan normal ifade seçeneklerinde yapılan herhangi bir değişiklik, `(?imnsx-imnsx)` kapsayan grubun sonuna kadar yürürlükte kalır.</span><span class="sxs-lookup"><span data-stu-id="99bcf-120">Any change in regular expression options defined by the `(?imnsx-imnsx)` construct remains in effect until the end of the enclosing group.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99bcf-121">Alt `(?imnsx-imnsx:` *ifade* `)` gruplama yapısı, bir alt ifade için özdeş işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="99bcf-121">The `(?imnsx-imnsx:`*subexpression*`)` grouping construct provides identical functionality for a subexpression.</span></span> <span data-ttu-id="99bcf-122">Daha fazla bilgi için bkz. [yapıları gruplandırma](grouping-constructs-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="99bcf-122">For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="99bcf-123">Aşağıdaki örnek, `i` `n` `x` büyük/küçük harf duyarlı ve açık yakalamaları etkinleştirmek ve normal bir ifadenin ortasında yer alan normal ifade deseninin boşluk yoksaymak için, ve seçeneklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="99bcf-123">The following example uses the `i`, `n`, and `x` options to enable case insensitivity and explicit captures, and to ignore white space in the regular expression pattern in the middle of a regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 <span data-ttu-id="99bcf-124">Örnek iki normal ifade tanımlar.</span><span class="sxs-lookup"><span data-stu-id="99bcf-124">The example defines two regular expressions.</span></span> <span data-ttu-id="99bcf-125">Birincisi, `\b(D\w+)\s(d\w+)\b` büyük bir "d" ve küçük harf "d" ile başlayan iki ardışık sözcükten eşleşir.</span><span class="sxs-lookup"><span data-stu-id="99bcf-125">The first, `\b(D\w+)\s(d\w+)\b`, matches two consecutive words that begin with an uppercase "D" and a lowercase "d".</span></span> <span data-ttu-id="99bcf-126">İkinci normal ifade, `\b(D\w+)(?ixn) \s (d\w+) \b` Aşağıdaki tabloda açıklandığı gibi, bu kalıbı değiştirmek için satır içi seçenekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="99bcf-126">The second regular expression, `\b(D\w+)(?ixn) \s (d\w+) \b`, uses inline options to modify this pattern, as described in the following table.</span></span> <span data-ttu-id="99bcf-127">Sonuçların karşılaştırması yapının etkisini onaylar `(?ixn)` .</span><span class="sxs-lookup"><span data-stu-id="99bcf-127">A comparison of the results confirms the effect of the `(?ixn)` construct.</span></span>  
  
|<span data-ttu-id="99bcf-128">Desen</span><span class="sxs-lookup"><span data-stu-id="99bcf-128">Pattern</span></span>|<span data-ttu-id="99bcf-129">Description</span><span class="sxs-lookup"><span data-stu-id="99bcf-129">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="99bcf-130">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="99bcf-130">Start at a word boundary.</span></span>|  
|`(D\w+)`|<span data-ttu-id="99bcf-131">Büyük bir "D" ve ardından bir veya daha fazla sözcük karakteri Eşleştir.</span><span class="sxs-lookup"><span data-stu-id="99bcf-131">Match a capital "D" followed by one or more word characters.</span></span> <span data-ttu-id="99bcf-132">Bu ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="99bcf-132">This is the first capture group.</span></span>|  
|`(?ixn)`|<span data-ttu-id="99bcf-133">Bu noktadan itibaren, karşılaştırmalar büyük/küçük harf duyarsız, yalnızca açık yakalamaları yapın ve normal ifade deseninin boşluk olduğunu yoksayın.</span><span class="sxs-lookup"><span data-stu-id="99bcf-133">From this point on, make comparisons case-insensitive, make only explicit captures, and ignore white space in the regular expression pattern.</span></span>|  
|`\s`|<span data-ttu-id="99bcf-134">Bir boşluk karakteri ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-134">Match a white-space character.</span></span>|  
|`(d\w+)`|<span data-ttu-id="99bcf-135">Büyük veya küçük harf "d" ile sonra bir veya daha fazla sözcük karakteri eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-135">Match an uppercase or lowercase "d" followed by one or more word characters.</span></span> <span data-ttu-id="99bcf-136">`n`(Açık yakalama) seçeneği etkinleştirildiğinden bu grup yakalanmadı..</span><span class="sxs-lookup"><span data-stu-id="99bcf-136">This group is not captured because the `n` (explicit capture) option was enabled..</span></span>|  
|`\b`|<span data-ttu-id="99bcf-137">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="99bcf-137">Match a word boundary.</span></span>|  
  
## <a name="inline-comment"></a><span data-ttu-id="99bcf-138">Satır içi açıklama</span><span class="sxs-lookup"><span data-stu-id="99bcf-138">Inline Comment</span></span>  

 <span data-ttu-id="99bcf-139">`(?#` *Açıklama* `)` yapısı, bir normal ifadeye satır içi bir yorum eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="99bcf-139">The `(?#` *comment*`)` construct lets you include an inline comment in a regular expression.</span></span> <span data-ttu-id="99bcf-140">Normal ifade altyapısı, açıklama yöntemi tarafından döndürülen dizeye dahil edilse de, bu açıklamanın herhangi bir parçasını model eşleme içinde kullanmaz <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="99bcf-140">The regular expression engine does not use any part of the comment in pattern matching, although the comment is included in the string that is returned by the <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="99bcf-141">Açıklama ilk kapanış parantezinde sona erer.</span><span class="sxs-lookup"><span data-stu-id="99bcf-141">The comment ends at the first closing parenthesis.</span></span>  
  
 <span data-ttu-id="99bcf-142">Aşağıdaki örnek, önceki bölümdeki örnekteki ilk normal ifade deseninin yinelenir.</span><span class="sxs-lookup"><span data-stu-id="99bcf-142">The following example repeats the first regular expression pattern from the example in the previous section.</span></span> <span data-ttu-id="99bcf-143">Karşılaştırmayı, büyük/küçük harfe duyarlı olup olmadığını belirtmek için normal ifadeye iki satır içi açıklama ekler.</span><span class="sxs-lookup"><span data-stu-id="99bcf-143">It adds two inline comments to the regular expression to indicate whether the comparison is case-sensitive.</span></span> <span data-ttu-id="99bcf-144">Normal ifade deseninin `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b` aşağıdaki şekilde tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99bcf-144">The regular expression pattern, `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b`, is defined as follows.</span></span>  
  
|<span data-ttu-id="99bcf-145">Desen</span><span class="sxs-lookup"><span data-stu-id="99bcf-145">Pattern</span></span>|<span data-ttu-id="99bcf-146">Description</span><span class="sxs-lookup"><span data-stu-id="99bcf-146">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="99bcf-147">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="99bcf-147">Start at a word boundary.</span></span>|  
|`(?# case-sensitive comparison)`|<span data-ttu-id="99bcf-148">Bir yorum.</span><span class="sxs-lookup"><span data-stu-id="99bcf-148">A comment.</span></span> <span data-ttu-id="99bcf-149">Desenler ile eşleşen davranışı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="99bcf-149">It does not affect pattern-matching behavior.</span></span>|  
|`(D\w+)`|<span data-ttu-id="99bcf-150">Büyük bir "D" ve ardından bir veya daha fazla sözcük karakteri Eşleştir.</span><span class="sxs-lookup"><span data-stu-id="99bcf-150">Match a capital "D" followed by one or more word characters.</span></span> <span data-ttu-id="99bcf-151">Bu ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="99bcf-151">This is the first capturing group.</span></span>|  
|`\s`|<span data-ttu-id="99bcf-152">Bir boşluk karakteri ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-152">Match a white-space character.</span></span>|  
|`(?ixn)`|<span data-ttu-id="99bcf-153">Bu noktadan itibaren, karşılaştırmalar büyük/küçük harf duyarsız, yalnızca açık yakalamaları yapın ve normal ifade deseninin boşluk olduğunu yoksayın.</span><span class="sxs-lookup"><span data-stu-id="99bcf-153">From this point on, make comparisons case-insensitive, make only explicit captures, and ignore white space in the regular expression pattern.</span></span>|  
|`(?#case-insensitive comparison)`|<span data-ttu-id="99bcf-154">Bir yorum.</span><span class="sxs-lookup"><span data-stu-id="99bcf-154">A comment.</span></span> <span data-ttu-id="99bcf-155">Desenler ile eşleşen davranışı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="99bcf-155">It does not affect pattern-matching behavior.</span></span>|  
|`(d\w+)`|<span data-ttu-id="99bcf-156">Büyük veya küçük harf "d" ile sonra bir veya daha fazla sözcük karakteri eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-156">Match an uppercase or lowercase "d" followed by one or more word characters.</span></span> <span data-ttu-id="99bcf-157">Bu ikinci yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="99bcf-157">This is the second capture group.</span></span>|  
|`\b`|<span data-ttu-id="99bcf-158">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="99bcf-158">Match a word boundary.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a><span data-ttu-id="99bcf-159">Satır sonu açıklaması</span><span class="sxs-lookup"><span data-stu-id="99bcf-159">End-of-Line Comment</span></span>  

 <span data-ttu-id="99bcf-160">Bir sayı işareti ( `#` ), normal ifade deseninin sonunda kaçışsız # karakteriyle başlayan ve satırın sonuna kadar devam eden bir x-Mode yorumunu işaretler.</span><span class="sxs-lookup"><span data-stu-id="99bcf-160">A number sign (`#`)marks an x-mode comment, which starts at the unescaped # character at the end of the regular expression pattern and continues until the end of the line.</span></span> <span data-ttu-id="99bcf-161">Bu yapıyı kullanmak için, `x` seçeneğini etkinleştirmeniz (satır içi seçenekler aracılığıyla) veya <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> `option` nesneyi örnekledikten <xref:System.Text.RegularExpressions.Regex> ya da statik bir yöntemi çağırırken parametreye değeri sağlamanız gerekir <xref:System.Text.RegularExpressions.Regex> .</span><span class="sxs-lookup"><span data-stu-id="99bcf-161">To use this construct, you must either enable the `x` option (through inline options) or supply the <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> value to the `option` parameter when instantiating the <xref:System.Text.RegularExpressions.Regex> object or calling a static <xref:System.Text.RegularExpressions.Regex> method.</span></span>  
  
 <span data-ttu-id="99bcf-162">Aşağıdaki örnek satır sonu açıklama yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="99bcf-162">The following example illustrates the end-of-line comment construct.</span></span> <span data-ttu-id="99bcf-163">Bir dizenin en az bir biçim öğesi içeren bir bileşik biçim dizesi olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="99bcf-163">It determines whether a string is a composite format string that includes at least one format item.</span></span> <span data-ttu-id="99bcf-164">Aşağıdaki tabloda, normal ifade deseninin yapıları açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="99bcf-164">The following table describes the constructs in the regular expression pattern:</span></span>  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|<span data-ttu-id="99bcf-165">Desen</span><span class="sxs-lookup"><span data-stu-id="99bcf-165">Pattern</span></span>|<span data-ttu-id="99bcf-166">Description</span><span class="sxs-lookup"><span data-stu-id="99bcf-166">Description</span></span>|  
|-------------|-----------------|  
|`\{`|<span data-ttu-id="99bcf-167">Bir açma ayracı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-167">Match an opening brace.</span></span>|  
|`\d+`|<span data-ttu-id="99bcf-168">Bir veya daha fazla ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-168">Match one or more decimal digits.</span></span>|  
|`(,-*\d+)*`|<span data-ttu-id="99bcf-169">Sıfırdan sonra bir veya daha fazla ondalık basamak ile, bir virgülden sonra sıfır veya bir oluşumu ve ardından isteğe bağlı bir eksi işareti ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-169">Match zero or one occurrence of a comma, followed by an optional minus sign, followed by one or more decimal digits.</span></span>|  
|`(\:\w{1,4}?)*`|<span data-ttu-id="99bcf-170">İki nokta üst üste, ardından bir ile dört arasında, ancak mümkün olan, boşluk karakterlerinden az olan sıfır veya bir oluşumu eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-170">Match zero or one occurrence of a colon, followed by one to four, but as few as possible, white-space characters.</span></span>|  
|`\}`|<span data-ttu-id="99bcf-171">Bir kapanış ayracı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-171">Match a closing brace.</span></span>|  
|`(?x)`|<span data-ttu-id="99bcf-172">Satır sonu açıklamasının tanınması için, stili yoksay beyaz alanı seçeneğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="99bcf-172">Enable the ignore pattern white-space option so that the end-of-line comment will be recognized.</span></span>|  
|`# Looks for a composite format item.`|<span data-ttu-id="99bcf-173">Satır sonu açıklaması.</span><span class="sxs-lookup"><span data-stu-id="99bcf-173">An end-of-line comment.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 <span data-ttu-id="99bcf-174">`(?x)`Normal ifadede yapıyı sağlamak yerine, açıklama <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi çağırarak ve numaralandırma değeri geçirerek de tanınabilmesi gerektiğini unutmayın <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="99bcf-174">Note that, instead of providing the `(?x)` construct in the regular expression, the comment could also have been recognized by calling the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method and passing it the <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> enumeration value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99bcf-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99bcf-175">See also</span></span>

- [<span data-ttu-id="99bcf-176">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="99bcf-176">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
