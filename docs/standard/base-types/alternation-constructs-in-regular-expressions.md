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
ms.openlocfilehash: 956d16b47fb31549de8f25c513d73c43ab41c267
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574741"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="59c97-102">Normal İfadelerdeki Değişim Yapıları</span><span class="sxs-lookup"><span data-stu-id="59c97-102">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a> <span data-ttu-id="59c97-103">Değişim yapıları değiştirin ya da etkinleştirmek için normal bir ifade / veya veya koşullu eşleştirme.</span><span class="sxs-lookup"><span data-stu-id="59c97-103">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="59c97-104">.NET üç değişim yapıları destekler:</span><span class="sxs-lookup"><span data-stu-id="59c97-104">.NET supports three alternation constructs:</span></span>  
  
-   [<span data-ttu-id="59c97-105">Desen ile eşleştirme&#124;</span><span class="sxs-lookup"><span data-stu-id="59c97-105">Pattern matching with &#124;</span></span>](#Either_Or)  
  
-   [<span data-ttu-id="59c97-106">Koşullu ile eşleşen (? () ifade) Evet&#124;yok)</span><span class="sxs-lookup"><span data-stu-id="59c97-106">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
-   [<span data-ttu-id="59c97-107">Koşullu eşleşen bir geçerli yakalanan grubuna bağlı</span><span class="sxs-lookup"><span data-stu-id="59c97-107">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="59c97-108">Desen ile eşleştirme&#124;</span><span class="sxs-lookup"><span data-stu-id="59c97-108">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="59c97-109">Dikey çubuğu'nu kullanabilirsiniz (`|`) karakter düzenleri, bir dizi herhangi biri eşleştirmek için burada `|` karakter her düzeni ayırır.</span><span class="sxs-lookup"><span data-stu-id="59c97-109">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="59c97-110">Pozitif karakter sınıfı gibi `|` karakteri, herhangi bir tek karakteri eşleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="59c97-110">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="59c97-111">Aşağıdaki örnek, bir pozitif karakter sınıfını hem ya da kullanır / veya desen ile eşleşen `|` karakter dizesi içinde sözcükleri "gri" veya "gri" oluşumları bulun.</span><span class="sxs-lookup"><span data-stu-id="59c97-111">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="59c97-112">Bu durumda, `|` karakter daha ayrıntılı bir normal ifade üretir.</span><span class="sxs-lookup"><span data-stu-id="59c97-112">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="59c97-113">Kullanan normal ifade `|` karakter `\bgr(a|e)y\b`, aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="59c97-113">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="59c97-114">Desen</span><span class="sxs-lookup"><span data-stu-id="59c97-114">Pattern</span></span>|<span data-ttu-id="59c97-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59c97-115">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="59c97-116">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="59c97-116">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="59c97-117">"Gr" karakteri eşleştirmek.</span><span class="sxs-lookup"><span data-stu-id="59c97-117">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="59c97-118">Bir "a" veya "e" ile eşleş.</span><span class="sxs-lookup"><span data-stu-id="59c97-118">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="59c97-119">Word sınırında "y" eşleşir.</span><span class="sxs-lookup"><span data-stu-id="59c97-119">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="59c97-120">`|` Karakter de kullanılabilir ya da gerçekleştirmek için / veya birden çok karakter veya karakter değişmez değerleri ve normal ifade dil öğeleri herhangi bir birleşimini içerebilir alt ifadelerin ile eşleşiyor.</span><span class="sxs-lookup"><span data-stu-id="59c97-120">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="59c97-121">(Karakter sınıfı bu işlevselliği sağlamaz.) Aşağıdaki örnek kullanır `|` karakter ya da bir ABD ayıklamak için Sosyal Güvenlik numarası (9 basamaklı bir sayı biçiminde olan SSN), *ddd*-*GG*-*dddd*, veya bir ABD 9 basamaklı sayı biçiminde İşveren Kimlik Numaranız'ne (EIN) *GG*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="59c97-121">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="59c97-122">Normal ifade `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="59c97-122">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="59c97-123">Desen</span><span class="sxs-lookup"><span data-stu-id="59c97-123">Pattern</span></span>|<span data-ttu-id="59c97-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59c97-124">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="59c97-125">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="59c97-125">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="59c97-126">Aşağıdakilerden birini eşleşen: tarafından yedi ondalık basamak; tire arkasından iki ondalık basamak veya üç ondalık basamak, tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak.</span><span class="sxs-lookup"><span data-stu-id="59c97-126">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="59c97-127">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="59c97-127">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="59c97-128">Başa dön</span><span class="sxs-lookup"><span data-stu-id="59c97-128">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="59c97-129">İfade Kullanarak Koşullu Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="59c97-129">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="59c97-130">Bu dil öğe olup bir ilk desen eşleştirebilirsiniz bağlı olarak iki desenleri birini eşleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="59c97-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="59c97-131">Sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="59c97-131">Its syntax is:</span></span>  
  
 <span data-ttu-id="59c97-132">`(?(` *ifade* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="59c97-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="59c97-133">Burada *ifade* eşleştirmek için ilk deseni *Evet* eşleşiyorsa deseni *ifade* eşleştirildiği, ve *hiçbir* isteğe bağlıdır eşleşiyorsa için desen *ifade* eşlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="59c97-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="59c97-134">Normal ifade altyapısı değerlendirir *ifade* bu hesaplar sonra sıfır genişlik onaylama; diğer bir deyişle, normal ifade altyapısı Giriş akışı ilerletmesi değil *ifade*.</span><span class="sxs-lookup"><span data-stu-id="59c97-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="59c97-135">Bu nedenle, bu yapıyı şuna eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="59c97-135">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="59c97-136">`(?(?=` *ifade* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="59c97-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="59c97-137">Burada `(?=` *ifade* `)` Sıfır Genişlik onaylama yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="59c97-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="59c97-138">(Daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Normal ifade altyapısı yorumlaması nedeniyle *ifade* bir bağlantı (bir sıfır genişlik onaylama) olarak *ifade* ya da Sıfır Genişlik onaylama olmalıdır (daha fazla bilgi için bkz: [ Tutturur](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) ya da bulunan bir alt *Evet*.</span><span class="sxs-lookup"><span data-stu-id="59c97-138">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="59c97-139">Aksi takdirde, *Evet* deseni olamaz eşleştirilemedi.</span><span class="sxs-lookup"><span data-stu-id="59c97-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59c97-140">Varsa *ifade*bir adlandırılmış ya da numaralı yakalama grup, değişim yapı yorumlanır yakalama test olarak; daha fazla bilgi için sonraki bölüme bakın [koşullu eşleşen bir geçerli yakalama grubu temelinde](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="59c97-140">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="59c97-141">Diğer bir deyişle, normal ifade altyapısı yakalanan alt dizeyi eşleştirmek çalışmaz, ancak bunun yerine varlığının veya yokluğunun grubunun için sınar.</span><span class="sxs-lookup"><span data-stu-id="59c97-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="59c97-142">Aşağıdaki örnekte gösterildiği örnek bir çeşididir [ya da / veya desen eşleştirme ile &#124; ](#Either_Or) bölümü.</span><span class="sxs-lookup"><span data-stu-id="59c97-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="59c97-143">Bu koşullu eşleşen word sınır sonra ilk üç karakter kısa çizgi ve ardından iki basamak olup olmadığını belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="59c97-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="59c97-144">Böyle bir durumda, bir ABD eşleştirmeye çalışır İşveren Kimlik numarası (EIN).</span><span class="sxs-lookup"><span data-stu-id="59c97-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="59c97-145">Aksi durumda, bir ABD eşleştirmeye çalışır Sosyal Güvenlik numarası (SSN).</span><span class="sxs-lookup"><span data-stu-id="59c97-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="59c97-146">Normal ifade deseni `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="59c97-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="59c97-147">Desen</span><span class="sxs-lookup"><span data-stu-id="59c97-147">Pattern</span></span>|<span data-ttu-id="59c97-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59c97-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="59c97-149">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="59c97-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="59c97-150">Sonraki üç karakter kısa çizgi ve ardından iki basamak oluşur olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="59c97-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="59c97-151">Önceki desen eşleşirse, bir tire yedi rakam ve ardından iki basamak eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="59c97-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="59c97-152">Önceki düzeni eşleşmiyorsa, üç ondalık basamak, tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleşir.</span><span class="sxs-lookup"><span data-stu-id="59c97-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="59c97-153">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="59c97-153">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="59c97-154">Başa dön</span><span class="sxs-lookup"><span data-stu-id="59c97-154">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="59c97-155">Yakalanan Geçerli Bir Gruba Göre Koşullu Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="59c97-155">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="59c97-156">Bu dil öğe olup belirtilen bir yakalama grubunu eşleşti bağlı olarak iki desenleri birini eşleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="59c97-156">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="59c97-157">Sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="59c97-157">Its syntax is:</span></span>  
  
 <span data-ttu-id="59c97-158">`(?(` *ad* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="59c97-158">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="59c97-159">veya</span><span class="sxs-lookup"><span data-stu-id="59c97-159">or</span></span>  
  
 <span data-ttu-id="59c97-160">`(?(` *sayı* `)` *Evet* `|` *yok* `)`</span><span class="sxs-lookup"><span data-stu-id="59c97-160">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="59c97-161">Burada *adı* adıdır ve *numarası* bir yakalama grubunu sayısı *Evet* eşleşiyorsa ifadesidir *adı* veya *numarası* bir eşleşmeye sahip ve *hiçbir* mevcut değilse eşleştirilecek isteğe bağlı ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="59c97-161">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="59c97-162">Varsa *adı* karşılık gelmediğinden normal ifade deseni kullanılan yakalama bir grup adına değişim yapı ifade sınama olarak, önceki bölümde açıklandığı gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="59c97-162">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="59c97-163">Genellikle, bunun anlamı *ifade* değerlendiren `false`.</span><span class="sxs-lookup"><span data-stu-id="59c97-163">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="59c97-164">Varsa *numarası* normal ifade deseni, normal ifade altyapısı atar kullanılan numaralandırılmış bir yakalama grubuna karşılık gelmiyor bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="59c97-164">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="59c97-165">Aşağıdaki örnekte gösterildiği örnek bir çeşididir [ya da / veya desen eşleştirme ile &#124; ](#Either_Or) bölümü.</span><span class="sxs-lookup"><span data-stu-id="59c97-165">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="59c97-166">Adlı bir yakalama grubunu kullanan `n2` tireyle ve ardından iki basamak oluşur.</span><span class="sxs-lookup"><span data-stu-id="59c97-166">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="59c97-167">Değişim Bu yakalama grubunu giriş dizesini eşleşen olup olmadığını testleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="59c97-167">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="59c97-168">Varsa, değişim oluşturmak dokuz basamaklı ABD son yedi rakamı eşleştirmeyi dener İşveren Kimlik numarası (EIN).</span><span class="sxs-lookup"><span data-stu-id="59c97-168">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="59c97-169">Henüz gelmemiş dokuz basamaklı ABD eşleştirmeye çalışır Sosyal Güvenlik numarası (SSN).</span><span class="sxs-lookup"><span data-stu-id="59c97-169">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="59c97-170">Normal ifade deseni `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="59c97-170">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="59c97-171">Desen</span><span class="sxs-lookup"><span data-stu-id="59c97-171">Pattern</span></span>|<span data-ttu-id="59c97-172">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59c97-172">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="59c97-173">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="59c97-173">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="59c97-174">İki basamaklı çizgi ile ardından sıfır veya bir örneğini Bul.</span><span class="sxs-lookup"><span data-stu-id="59c97-174">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="59c97-175">Bu yakalama grubunu adlandırın `n2`.</span><span class="sxs-lookup"><span data-stu-id="59c97-175">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="59c97-176">Test olup olmadığını `n2` giriş dizesini eşleşti.</span><span class="sxs-lookup"><span data-stu-id="59c97-176">Test whether `n2` was matched in the input string.</span></span>|  
|`)\d{7}`|<span data-ttu-id="59c97-177">Varsa `n2` olan yedi ondalık basamak eşleşen eşleşiyor.</span><span class="sxs-lookup"><span data-stu-id="59c97-177">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="59c97-178">Varsa `n2` eşleşmeyen, eşleşen üç ondalık basamak, tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak.</span><span class="sxs-lookup"><span data-stu-id="59c97-178">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="59c97-179">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="59c97-179">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="59c97-180">Değişim numaralandırılmış bir Grup yerine adlandırılmış bir grup kullanan bu örnekte, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="59c97-180">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="59c97-181">Normal ifade deseni `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="59c97-181">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="59c97-182">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59c97-182">See Also</span></span>  
 [<span data-ttu-id="59c97-183">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="59c97-183">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
