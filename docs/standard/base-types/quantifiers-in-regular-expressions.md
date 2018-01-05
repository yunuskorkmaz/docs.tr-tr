---
title: "Normal İfadelerdeki Miktar Belirleyiciler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET Framework regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db1c3af1bb3ad207278eed64a8fb2ef8ed6dc465
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="quantifiers-in-regular-expressions"></a><span data-ttu-id="24cb7-102">Normal İfadelerdeki Miktar Belirleyiciler</span><span class="sxs-lookup"><span data-stu-id="24cb7-102">Quantifiers in Regular Expressions</span></span>
<span data-ttu-id="24cb7-103">Miktar belirleyiciler kaç tane karakter, Grup veya karakter sınıfı örneğinin bulunması bir eşleşme için giriş bulunmalıdır belirtin.</span><span class="sxs-lookup"><span data-stu-id="24cb7-103">Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.</span></span>  <span data-ttu-id="24cb7-104">Aşağıdaki tabloda .NET tarafından desteklenen nicelik listeler.</span><span class="sxs-lookup"><span data-stu-id="24cb7-104">The following table lists the quantifiers supported by .NET.</span></span>  
  
|<span data-ttu-id="24cb7-105">Doyumsuz niceleyici</span><span class="sxs-lookup"><span data-stu-id="24cb7-105">Greedy quantifier</span></span>|<span data-ttu-id="24cb7-106">Yavaş niceleyici</span><span class="sxs-lookup"><span data-stu-id="24cb7-106">Lazy quantifier</span></span>|<span data-ttu-id="24cb7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cb7-107">Description</span></span>|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|<span data-ttu-id="24cb7-108">Sıfır veya daha fazla kez eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-108">Match zero or more times.</span></span>|  
|`+`|`+?`|<span data-ttu-id="24cb7-109">Bir veya birden çok kez eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-109">Match one or more times.</span></span>|  
|`?`|`??`|<span data-ttu-id="24cb7-110">Sıfır veya bir kez eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-110">Match zero or one time.</span></span>|  
|<span data-ttu-id="24cb7-111">`{` *n* `}`</span><span class="sxs-lookup"><span data-stu-id="24cb7-111">`{` *n* `}`</span></span>|<span data-ttu-id="24cb7-112">`{` *n* `}?`</span><span class="sxs-lookup"><span data-stu-id="24cb7-112">`{` *n* `}?`</span></span>|<span data-ttu-id="24cb7-113">Tam olarak eşleştiğinden  *n*  kez.</span><span class="sxs-lookup"><span data-stu-id="24cb7-113">Match exactly *n* times.</span></span>|  
|<span data-ttu-id="24cb7-114">`{` *n* `,}`</span><span class="sxs-lookup"><span data-stu-id="24cb7-114">`{` *n* `,}`</span></span>|<span data-ttu-id="24cb7-115">`{` *n* `,}?`</span><span class="sxs-lookup"><span data-stu-id="24cb7-115">`{` *n* `,}?`</span></span>|<span data-ttu-id="24cb7-116">En az eşleşen  *n*  kez.</span><span class="sxs-lookup"><span data-stu-id="24cb7-116">Match at least *n* times.</span></span>|  
|<span data-ttu-id="24cb7-117">`{` *n*  `,` *m*`}`</span><span class="sxs-lookup"><span data-stu-id="24cb7-117">`{` *n* `,` *m* `}`</span></span>|<span data-ttu-id="24cb7-118">`{` *n*  `,` *m*`}?`</span><span class="sxs-lookup"><span data-stu-id="24cb7-118">`{` *n* `,` *m* `}?`</span></span>|<span data-ttu-id="24cb7-119">Gelen eşleşen  *n*  için *m* kez.</span><span class="sxs-lookup"><span data-stu-id="24cb7-119">Match from *n* to *m* times.</span></span>|  
  
 <span data-ttu-id="24cb7-120">Miktarları `n` ve `m` tamsayı sabittir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-120">The quantities `n` and `m` are integer constants.</span></span> <span data-ttu-id="24cb7-121">Normalde, nicelik doyumsuz; Bunlar, mümkün olduğunca belirli modelleri sayıda oluşumları eşleştirilecek normal ifade altyapısı neden.</span><span class="sxs-lookup"><span data-stu-id="24cb7-121">Ordinarily, quantifiers are greedy; they cause the regular expression engine to match as many occurrences of particular patterns as possible.</span></span> <span data-ttu-id="24cb7-122">Sonuna ekleme `?` bir niceleyici karakter kılar yavaş; mümkün olduğunca en az yinelenme eşleştirilecek normal ifade alt neden olur.</span><span class="sxs-lookup"><span data-stu-id="24cb7-122">Appending the `?` character to a quantifier makes it lazy; it causes the regular expression engine to match as few occurrences as possible.</span></span> <span data-ttu-id="24cb7-123">Doyumsuz ve yavaş miktar belirleyiciler arasındaki farkı tam bir açıklaması için bkz [Greedy ve yavaş miktar belirleyiciler](#Greedy) bu konuda daha sonra.</span><span class="sxs-lookup"><span data-stu-id="24cb7-123">For a complete description of the difference between greedy and lazy quantifiers, see the section [Greedy and Lazy Quantifiers](#Greedy) later in this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="24cb7-124">İç içe geçme nicelik (örneğin, normal ifade deseni olarak `(a*)*` yapar) normal ifade altyapısı giriş dizedeki karakter sayısını üstel bir işlevi olarak gerçekleştirmelisiniz karşılaştırmaları sayısını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24cb7-124">Nesting quantifiers (for example, as the regular expression pattern `(a*)*` does) can increase the number of comparisons that the regular expression engine must perform, as an exponential function of the number of characters in the input string.</span></span> <span data-ttu-id="24cb7-125">Bu davranış ve kendi geçici çözümler hakkında daha fazla bilgi için bkz: [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="24cb7-125">For more information about this behavior and its workarounds, see [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).</span></span>  
  
## <a name="regular-expression-quantifiers"></a><span data-ttu-id="24cb7-126">Normal ifade miktar belirleyiciler</span><span class="sxs-lookup"><span data-stu-id="24cb7-126">Regular Expression Quantifiers</span></span>  
 <span data-ttu-id="24cb7-127">Aşağıdaki bölümlerde .NET normal ifadeleri tarafından desteklenen nicelik listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-127">The following sections list the quantifiers supported by .NET regular expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24cb7-128">*, +,?, {, Ve} bir normal ifade deseni karakteri ile karşılaşıldı, yer alan sürece normal ifade altyapısı bunları nicelik veya niceleyici yapıları bir parçası olarak yorumlar bir [karakter sınıfı](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="24cb7-128">If the *, +, ?, {, and } characters are encountered in a regular expression pattern, the regular expression engine interprets them as quantifiers or part of quantifier constructs unless they are included in a [character class](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).</span></span> <span data-ttu-id="24cb7-129">Bu karakter sınıf dışındaki değişmez karakter olarak yorumlamak için ters bölü işareti koyarak çıkış gerekir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-129">To interpret these as literal characters outside a character class, you must escape them by preceding them with a backslash.</span></span> <span data-ttu-id="24cb7-130">Örneğin, dize `\*` bir normal ifade deseni değişmez değer bir yıldız işareti olarak yorumlanır ("\*") karakter.</span><span class="sxs-lookup"><span data-stu-id="24cb7-130">For example, the string `\*` in a regular expression pattern is interpreted as a literal asterisk ("\*") character.</span></span>  
  
### <a name="match-zero-or-more-times-"></a><span data-ttu-id="24cb7-131">Eşleşen sıfır veya daha fazla kez: *</span><span class="sxs-lookup"><span data-stu-id="24cb7-131">Match Zero or More Times: *</span></span>  
 <span data-ttu-id="24cb7-132">`*` Niceleyici önceki öğesi sıfır veya daha fazla kez eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-132">The `*` quantifier matches the preceding element zero or more times.</span></span> <span data-ttu-id="24cb7-133">Eşdeğer olan `{0,}` niceleyici.</span><span class="sxs-lookup"><span data-stu-id="24cb7-133">It is equivalent to the `{0,}` quantifier.</span></span> <span data-ttu-id="24cb7-134">`*`yavaş olan eşdeğerdir doyumsuz niceleyici olan `*?`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-134">`*` is a greedy quantifier whose lazy equivalent is `*?`.</span></span>  
  
 <span data-ttu-id="24cb7-135">Aşağıdaki örnek, bu normal ifade gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-135">The following example illustrates this regular expression.</span></span> <span data-ttu-id="24cb7-136">Modeli ve dört giriş dizisinde dokuz basamak beş eşleşen (`95`, `929`, `9129`, ve `9919`) desteklemez.</span><span class="sxs-lookup"><span data-stu-id="24cb7-136">Of the nine digits in the input string, five match the pattern and four (`95`, `929`, `9129`, and `9919`) do not.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 <span data-ttu-id="24cb7-137">Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-137">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="24cb7-138">Desen</span><span class="sxs-lookup"><span data-stu-id="24cb7-138">Pattern</span></span>|<span data-ttu-id="24cb7-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cb7-139">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="24cb7-140">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="24cb7-140">Start at a word boundary.</span></span>|  
|`91*`|<span data-ttu-id="24cb7-141">"Sıfır veya daha fazla"1"karakterle devam etmelidir 9" eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-141">Match a "9" followed by zero or more "1" characters.</span></span>|  
|`9*`|<span data-ttu-id="24cb7-142">Sıfır veya daha fazla "9" karakter eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="24cb7-142">Match zero or more "9" characters.</span></span>|  
|`\b`|<span data-ttu-id="24cb7-143">Bir sözcük sınırında bit.</span><span class="sxs-lookup"><span data-stu-id="24cb7-143">End at a word boundary.</span></span>|  
  
### <a name="match-one-or-more-times-"></a><span data-ttu-id="24cb7-144">Bir veya birden çok kez eşleşen: +</span><span class="sxs-lookup"><span data-stu-id="24cb7-144">Match One or More Times: +</span></span>  
 <span data-ttu-id="24cb7-145">`+` Niceleyici önceki öğesi bir veya birden çok kez eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-145">The `+` quantifier matches the preceding element one or more times.</span></span> <span data-ttu-id="24cb7-146">Eşdeğer olan `{1,}`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-146">It is equivalent to `{1,}`.</span></span> <span data-ttu-id="24cb7-147">`+`yavaş olan eşdeğerdir doyumsuz niceleyici olan `+?`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-147">`+` is a greedy quantifier whose lazy equivalent is `+?`.</span></span>  
  
 <span data-ttu-id="24cb7-148">Örneğin, normal ifade `\ban+\w*?\b` harfiyle başlayan tüm sözcükleri eşleştirmeyi dener `a` harf bir veya daha fazla örnekleri tarafından izlenen `n`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-148">For example, the regular expression `\ban+\w*?\b` tries to match entire words that begin with the letter `a` followed by one or more instances of the letter `n`.</span></span> <span data-ttu-id="24cb7-149">Aşağıdaki örnek, bu normal ifade gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-149">The following example illustrates this regular expression.</span></span> <span data-ttu-id="24cb7-150">Sözcükleri normal ifadeyle eşleşen `an`, `annual`, `announcement`, ve `antique`ve eşleşecek şekilde doğru başarısız `autumn` ve `all`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-150">The regular expression matches the words `an`, `annual`, `announcement`, and `antique`, and correctly fails to match `autumn` and `all`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 <span data-ttu-id="24cb7-151">Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-151">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="24cb7-152">Desen</span><span class="sxs-lookup"><span data-stu-id="24cb7-152">Pattern</span></span>|<span data-ttu-id="24cb7-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cb7-153">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="24cb7-154">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="24cb7-154">Start at a word boundary.</span></span>|  
|`an+`|<span data-ttu-id="24cb7-155">Eşleşen bir "a" bir veya daha fazla "n" karakterle devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-155">Match an "a" followed by one or more "n" characters.</span></span>|  
|`\w*?`|<span data-ttu-id="24cb7-156">Bir sözcük karakteriyle sıfır veya daha fazla kez, ancak gibi birkaç kez mümkün olduğunca aynı.</span><span class="sxs-lookup"><span data-stu-id="24cb7-156">Match a word character zero or more times, but as few times as possible.</span></span>|  
|`\b`|<span data-ttu-id="24cb7-157">Bir sözcük sınırında bit.</span><span class="sxs-lookup"><span data-stu-id="24cb7-157">End at a word boundary.</span></span>|  
  
### <a name="match-zero-or-one-time-"></a><span data-ttu-id="24cb7-158">Eşleşen sıfır veya bir kez:?</span><span class="sxs-lookup"><span data-stu-id="24cb7-158">Match Zero or One Time: ?</span></span>  
 <span data-ttu-id="24cb7-159">`?` Niceleyici önceki öğesi sıfır veya bir zaman eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-159">The `?` quantifier matches the preceding element zero or one time.</span></span> <span data-ttu-id="24cb7-160">Eşdeğer olan `{0,1}`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-160">It is equivalent to `{0,1}`.</span></span> <span data-ttu-id="24cb7-161">`?`yavaş olan eşdeğerdir doyumsuz niceleyici olan `??`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-161">`?` is a greedy quantifier whose lazy equivalent is `??`.</span></span>  
  
 <span data-ttu-id="24cb7-162">Örneğin, normal ifade `\ban?\b` harfiyle başlayan tüm sözcükleri eşleştirmeyi dener `a` harf sıfır veya bir örnekleri tarafından izlenen `n`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-162">For example, the regular expression `\ban?\b` tries to match entire words that begin with the letter `a` followed by zero or one instances of the letter `n`.</span></span> <span data-ttu-id="24cb7-163">Diğer bir deyişle, sözcükleri eşleştirmeye çalışır `a` ve `an`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-163">In other words, it tries to match the words `a` and `an`.</span></span> <span data-ttu-id="24cb7-164">Aşağıdaki örnek, bu normal ifade gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-164">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 <span data-ttu-id="24cb7-165">Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-165">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="24cb7-166">Desen</span><span class="sxs-lookup"><span data-stu-id="24cb7-166">Pattern</span></span>|<span data-ttu-id="24cb7-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cb7-167">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="24cb7-168">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="24cb7-168">Start at a word boundary.</span></span>|  
|`an?`|<span data-ttu-id="24cb7-169">Eşleşen bir "a" sıfır veya bir "n" karakter.</span><span class="sxs-lookup"><span data-stu-id="24cb7-169">Match an "a" followed by zero or one "n" character.</span></span>|  
|`\b`|<span data-ttu-id="24cb7-170">Bir sözcük sınırında bit.</span><span class="sxs-lookup"><span data-stu-id="24cb7-170">End at a word boundary.</span></span>|  
  
### <a name="match-exactly-n-times-n"></a><span data-ttu-id="24cb7-171">Tam olarak n kez eşleşen: {n}</span><span class="sxs-lookup"><span data-stu-id="24cb7-171">Match Exactly n Times: {n}</span></span>  
 <span data-ttu-id="24cb7-172">`{`  *n*  `}` Niceleyici önceki öğesi tam olarak eşleşen  *n*  zaman, nerede  *n* herhangi bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-172">The `{`*n*`}` quantifier matches the preceding element exactly *n* times, where *n* is any integer.</span></span> <span data-ttu-id="24cb7-173">`{`*n*`}`yavaş olan eşdeğerdir doyumsuz niceleyici olan `{`  *n*  `}?`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-173">`{`*n*`}` is a greedy quantifier whose lazy equivalent is `{`*n*`}?`.</span></span>  
  
 <span data-ttu-id="24cb7-174">Örneğin, normal ifade `\b\d+\,\d{3}\b` word sınır tarafından izlenen üç ondalık basamak ve ardından bir veya daha fazla ondalık basamak arkasından bir word sınır eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-174">For example, the regular expression `\b\d+\,\d{3}\b` tries to match a word boundary followed by one or more decimal digits followed by three decimal digits followed by a word boundary.</span></span> <span data-ttu-id="24cb7-175">Aşağıdaki örnek, bu normal ifade gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-175">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 <span data-ttu-id="24cb7-176">Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-176">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="24cb7-177">Desen</span><span class="sxs-lookup"><span data-stu-id="24cb7-177">Pattern</span></span>|<span data-ttu-id="24cb7-178">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cb7-178">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="24cb7-179">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="24cb7-179">Start at a word boundary.</span></span>|  
|`\d+`|<span data-ttu-id="24cb7-180">Bir veya daha fazla ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="24cb7-180">Match one or more decimal digits.</span></span>|  
|`\,`|<span data-ttu-id="24cb7-181">Virgül karakteriyle eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="24cb7-181">Match a comma character.</span></span>|  
|`\d{3}`|<span data-ttu-id="24cb7-182">Üç ondalık basamakla eşleş.</span><span class="sxs-lookup"><span data-stu-id="24cb7-182">Match three decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="24cb7-183">Bir sözcük sınırında bit.</span><span class="sxs-lookup"><span data-stu-id="24cb7-183">End at a word boundary.</span></span>|  
  
### <a name="match-at-least-n-times-n"></a><span data-ttu-id="24cb7-184">En az n kez eşleşen: {n}</span><span class="sxs-lookup"><span data-stu-id="24cb7-184">Match at Least n Times: {n,}</span></span>  
 <span data-ttu-id="24cb7-185">`{`  *n*  `,}` Niceleyici eşleşen önceki öğesi en az  *n*  zaman, nerede  *n* herhangi bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-185">The `{`*n*`,}` quantifier matches the preceding element at least *n* times, where *n* is any integer.</span></span> <span data-ttu-id="24cb7-186">`{`*n*`,}`yavaş olan eşdeğerdir doyumsuz niceleyici olan `{`  *n*  `}?`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-186">`{`*n*`,}` is a greedy quantifier whose lazy equivalent is `{`*n*`}?`.</span></span>  
  
 <span data-ttu-id="24cb7-187">Örneğin, normal ifade `\b\d{2,}\b\D+` en az iki basamak ardından word sınır ve sayı olmayan karakter ve ardından word sınır eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-187">For example, the regular expression `\b\d{2,}\b\D+` tries to match a word boundary followed by at least two digits followed by a word boundary and a non-digit character.</span></span> <span data-ttu-id="24cb7-188">Aşağıdaki örnek, bu normal ifade gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-188">The following example illustrates this regular expression.</span></span> <span data-ttu-id="24cb7-189">Tümcecik eşleştirilecek normal ifade başarısız `"7 days"` tek bir ondalık basamak içeriyor, ancak başarılı bir şekilde tümcecikleri eşleşen çünkü `"10 weeks and 300 years"`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-189">The regular expression fails to match the phrase `"7 days"` because it contains just one decimal digit, but it successfully matches the phrases `"10 weeks and 300 years"`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 <span data-ttu-id="24cb7-190">Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-190">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="24cb7-191">Desen</span><span class="sxs-lookup"><span data-stu-id="24cb7-191">Pattern</span></span>|<span data-ttu-id="24cb7-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cb7-192">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="24cb7-193">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="24cb7-193">Start at a word boundary.</span></span>|  
|`\d{2,}`|<span data-ttu-id="24cb7-194">En az iki ondalık basamak eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-194">Match at least two decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="24cb7-195">Bir sözcük sınırıyla eşleş.</span><span class="sxs-lookup"><span data-stu-id="24cb7-195">Match a word boundary.</span></span>|  
|`\D+`|<span data-ttu-id="24cb7-196">En az bir olmayan ondalık basamak eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-196">Match at least one non-decimal digit.</span></span>|  
  
### <a name="match-between-n-and-m-times-nm"></a><span data-ttu-id="24cb7-197">N ve m zamanları arasında eşleştirme: {n, m}</span><span class="sxs-lookup"><span data-stu-id="24cb7-197">Match Between n and m Times: {n,m}</span></span>  
 <span data-ttu-id="24cb7-198">`{`  *n*  `,` *m* `}` niceleyici eşleşen önceki öğesi en az  *n*  kez en çok *m* zaman, nerede  *n*  ve *m* tamsayı olduğunu.</span><span class="sxs-lookup"><span data-stu-id="24cb7-198">The `{`*n*`,`*m*`}` quantifier matches the preceding element at least *n* times, but no more than *m* times, where *n* and *m* are integers.</span></span> <span data-ttu-id="24cb7-199">`{`*n*`,`*m* `}` yavaş olan eşdeğerdir doyumsuz niceleyici olan `{`  *n*  `,` *m*`}?`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-199">`{`*n*`,`*m*`}` is a greedy quantifier whose lazy equivalent is `{`*n*`,`*m*`}?`.</span></span>  
  
 <span data-ttu-id="24cb7-200">Aşağıdaki örnekte, normal ifade `(00\s){2,4}` iki ve dört oluşumları iki arasında bir boşluk bırakarak sıfır basamak eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-200">In the following example, the regular expression `(00\s){2,4}` tries to match between two and four occurrences of two zero digits followed by a space.</span></span> <span data-ttu-id="24cb7-201">Giriş dizesi'nın son kısmı bu deseni beş kez içerdiğini unutmayın yerine en fazla dört.</span><span class="sxs-lookup"><span data-stu-id="24cb7-201">Note that the final portion of the input string includes this pattern five times rather than the maximum of four.</span></span> <span data-ttu-id="24cb7-202">Ancak, bu alt dizeyi (kadar boşluk ve sıfır beşinci çiftinin) yalnızca ilk bölümü normal ifade deseni eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-202">However, only the initial portion of this substring (up to the space and the fifth pair of zeros) matches the regular expression pattern.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a><span data-ttu-id="24cb7-203">Eşleşen sıfır veya daha fazla kez (yavaş eşleşme): *?</span><span class="sxs-lookup"><span data-stu-id="24cb7-203">Match Zero or More Times (Lazy Match): *?</span></span>  
 <span data-ttu-id="24cb7-204">`*?` Niceleyici önceki öğesi sıfır veya daha fazla kez, mümkün olduğunca ancak gibi birkaç kez eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-204">The `*?` quantifier matches the preceding element zero or more times, but as few times as possible.</span></span> <span data-ttu-id="24cb7-205">Doyumsuz nicelik, yavaş karşılık gelen olan `*`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-205">It is the lazy counterpart of the greedy quantifier `*`.</span></span>  
  
 <span data-ttu-id="24cb7-206">Aşağıdaki örnekte, normal ifade `\b\w*?oo\w*?\b` dizesini içeren tüm sözcükleri eşleşen `oo`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-206">In the following example, the regular expression `\b\w*?oo\w*?\b` matches all words that contain the string `oo`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 <span data-ttu-id="24cb7-207">Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-207">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="24cb7-208">Desen</span><span class="sxs-lookup"><span data-stu-id="24cb7-208">Pattern</span></span>|<span data-ttu-id="24cb7-209">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cb7-209">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="24cb7-210">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="24cb7-210">Start at a word boundary.</span></span>|  
|`\w*?`|<span data-ttu-id="24cb7-211">Sıfır veya daha fazla sözcük karakterleri, mümkün olduğunca az karakter ancak aynı.</span><span class="sxs-lookup"><span data-stu-id="24cb7-211">Match zero or more word characters, but as few characters as possible.</span></span>|  
|`oo`|<span data-ttu-id="24cb7-212">"Oo" dize eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="24cb7-212">Match the string "oo".</span></span>|  
|`\w*?`|<span data-ttu-id="24cb7-213">Sıfır veya daha fazla sözcük karakterleri, mümkün olduğunca az karakter ancak aynı.</span><span class="sxs-lookup"><span data-stu-id="24cb7-213">Match zero or more word characters, but as few characters as possible.</span></span>|  
|`\b`|<span data-ttu-id="24cb7-214">Word sınırında sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="24cb7-214">End on a word boundary.</span></span>|  
  
### <a name="match-one-or-more-times-lazy-match-"></a><span data-ttu-id="24cb7-215">Bir veya daha fazla kez (yavaş eşleşme) eşleşmesi: +?</span><span class="sxs-lookup"><span data-stu-id="24cb7-215">Match One or More Times (Lazy Match): +?</span></span>  
 <span data-ttu-id="24cb7-216">`+?` Niceleyici önceki öğesi bir veya birden çok kez, mümkün olduğunca ancak gibi birkaç kez eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-216">The `+?` quantifier matches the preceding element one or more times, but as few times as possible.</span></span> <span data-ttu-id="24cb7-217">Doyumsuz nicelik, yavaş karşılık gelen olan `+`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-217">It is the lazy counterpart of the greedy quantifier `+`.</span></span>  
  
 <span data-ttu-id="24cb7-218">Örneğin, normal ifade `\b\w+?\b` word sınırları tarafından ayrılmış bir veya daha fazla karakter ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-218">For example, the regular expression `\b\w+?\b` matches one or more characters separated by word boundaries.</span></span> <span data-ttu-id="24cb7-219">Aşağıdaki örnek, bu normal ifade gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-219">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a><span data-ttu-id="24cb7-220">Eşleşen sıfır veya bir kez (yavaş eşleşme):??</span><span class="sxs-lookup"><span data-stu-id="24cb7-220">Match Zero or One Time (Lazy Match): ??</span></span>  
 <span data-ttu-id="24cb7-221">`??` Niceleyici önceki öğesi sıfır veya bir zaman mümkün olduğunca ancak gibi birkaç kez eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-221">The `??` quantifier matches the preceding element zero or one time, but as few times as possible.</span></span> <span data-ttu-id="24cb7-222">Doyumsuz nicelik, yavaş karşılık gelen olan `?`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-222">It is the lazy counterpart of the greedy quantifier `?`.</span></span>  
  
 <span data-ttu-id="24cb7-223">Örneğin, normal ifade `^\s*(System.)??Console.Write(Line)??\(??` "Console.Write" veya "Console.WriteLine" dizeleri eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-223">For example, the regular expression `^\s*(System.)??Console.Write(Line)??\(??` attempts to match the strings "Console.Write" or "Console.WriteLine".</span></span> <span data-ttu-id="24cb7-224">"Sistem" dizesini de içerir</span><span class="sxs-lookup"><span data-stu-id="24cb7-224">The string can also include "System."</span></span> <span data-ttu-id="24cb7-225">"Konsol" ve onu bir açma parantezi izlenebilir önce.</span><span class="sxs-lookup"><span data-stu-id="24cb7-225">before "Console", and it can be followed by an opening parenthesis.</span></span> <span data-ttu-id="24cb7-226">Dize, boşluk tarafından öncesinde rağmen bir satır başında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-226">The string must be at the beginning of a line, although it can be preceded by white space.</span></span> <span data-ttu-id="24cb7-227">Aşağıdaki örnek, bu normal ifade gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-227">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 <span data-ttu-id="24cb7-228">Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-228">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="24cb7-229">Desen</span><span class="sxs-lookup"><span data-stu-id="24cb7-229">Pattern</span></span>|<span data-ttu-id="24cb7-230">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cb7-230">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="24cb7-231">Giriş akışı başlangıcı eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-231">Match the start of the input stream.</span></span>|  
|`\s*`|<span data-ttu-id="24cb7-232">Sıfır veya daha fazla boşluk karakteriyle eşleş.</span><span class="sxs-lookup"><span data-stu-id="24cb7-232">Match zero or more white-space characters.</span></span>|  
|`(System.)??`|<span data-ttu-id="24cb7-233">"Sistem" dizenin sıfır veya bir örneğinin aynı.</span><span class="sxs-lookup"><span data-stu-id="24cb7-233">Match zero or one occurrence of the string "System.".</span></span>|  
|`Console.Write`|<span data-ttu-id="24cb7-234">"Console.Write" dize eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="24cb7-234">Match the string "Console.Write".</span></span>|  
|`(Line)??`|<span data-ttu-id="24cb7-235">"Satır" dizenin sıfır veya bir örneğinin aynı.</span><span class="sxs-lookup"><span data-stu-id="24cb7-235">Match zero or one occurrence of the string "Line".</span></span>|  
|`\(??`|<span data-ttu-id="24cb7-236">Sıfır veya bir geçişi parantez ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-236">Match zero or one occurrence of the opening parenthesis.</span></span>|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a><span data-ttu-id="24cb7-237">N kez (yavaş eşleşme) tam olarak eşleşen: {n}?</span><span class="sxs-lookup"><span data-stu-id="24cb7-237">Match Exactly n Times (Lazy Match): {n}?</span></span>  
 <span data-ttu-id="24cb7-238">`{`  *n*  `}?` Niceleyici önceki öğesi tam olarak eşleşen `n` zaman, nerede  *n*  herhangi bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-238">The `{`*n*`}?` quantifier matches the preceding element exactly `n` times, where *n* is any integer.</span></span> <span data-ttu-id="24cb7-239">Doyumsuz nicelik, yavaş karşılık gelen olan `{`  *n*  `}+`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-239">It is the lazy counterpart of the greedy quantifier `{`*n*`}+`.</span></span>  
  
 <span data-ttu-id="24cb7-240">Aşağıdaki örnekte, normal ifade `\b(\w{3,}?\.){2}?\w{3,}?\b` bir Web sitesi adresi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-240">In the following example, the regular expression `\b(\w{3,}?\.){2}?\w{3,}?\b` is used to identify a Web site address.</span></span> <span data-ttu-id="24cb7-241">Bu "www.microsoft.com" ve "msdn.microsoft.com" eşleştirir ancak "numaralı" veya "mycompany.com" eşleşmiyor unutmayın.</span><span class="sxs-lookup"><span data-stu-id="24cb7-241">Note that it matches "www.microsoft.com" and "msdn.microsoft.com", but does not match "mywebsite" or "mycompany.com".</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 <span data-ttu-id="24cb7-242">Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-242">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="24cb7-243">Desen</span><span class="sxs-lookup"><span data-stu-id="24cb7-243">Pattern</span></span>|<span data-ttu-id="24cb7-244">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cb7-244">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="24cb7-245">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="24cb7-245">Start at a word boundary.</span></span>|  
|`(\w{3,}?\.)`|<span data-ttu-id="24cb7-246">En az 3 word karakterlerle eşleşen ancak mümkün olduğunca az karakter, nokta veya nokta karakteri tarafından izlenen.</span><span class="sxs-lookup"><span data-stu-id="24cb7-246">Match at least 3 word characters, but as few characters as possible, followed by a dot or period character.</span></span> <span data-ttu-id="24cb7-247">Bu ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="24cb7-247">This is the first capturing group.</span></span>|  
|`(\w{3,}?\.){2}?`|<span data-ttu-id="24cb7-248">İki kez ilk grubundaki ancak mümkün olduğunca birkaç kez desenle eşleşen.</span><span class="sxs-lookup"><span data-stu-id="24cb7-248">Match the pattern in the first group two times, but as few times as possible.</span></span>|  
|`\b`|<span data-ttu-id="24cb7-249">Son bir word sınırında eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="24cb7-249">End the match on a word boundary.</span></span>|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a><span data-ttu-id="24cb7-250">En az n kez eşleşen (yavaş eşleşme): {n}?</span><span class="sxs-lookup"><span data-stu-id="24cb7-250">Match at Least n Times (Lazy Match): {n,}?</span></span>  
 <span data-ttu-id="24cb7-251">`{`  *n*  `,}?` Niceleyici eşleşen önceki öğesi en az `n` zaman, nerede  *n*  olarak ancak gibi birkaç kez herhangi bir tamsayı değil olası.</span><span class="sxs-lookup"><span data-stu-id="24cb7-251">The `{`*n*`,}?` quantifier matches the preceding element at least `n` times, where *n* is any integer, but as few times as possible.</span></span> <span data-ttu-id="24cb7-252">Doyumsuz nicelik, yavaş karşılık gelen olan `{`  *n*  `,}`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-252">It is the lazy counterpart of the greedy quantifier `{`*n*`,}`.</span></span>  
  
 <span data-ttu-id="24cb7-253">Örneğin bkz `{`  *n*  `}?` niceleyici bir çizim için önceki bölümdeki.</span><span class="sxs-lookup"><span data-stu-id="24cb7-253">See the example for the `{`*n*`}?` quantifier in the previous section for an illustration.</span></span> <span data-ttu-id="24cb7-254">Bu örnekte normal ifade kullanan `{`  *n*  `,}` ardından bir noktayla en az üç karakterden uzun bir dize eşleşmesi için niceleyici.</span><span class="sxs-lookup"><span data-stu-id="24cb7-254">The regular expression in that example uses the `{`*n*`,}` quantifier to match a string that has at least three characters followed by a period.</span></span>  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a><span data-ttu-id="24cb7-255">N ve m (yavaş eşleşme) saatleri arasında eşleşme: {n, m}?</span><span class="sxs-lookup"><span data-stu-id="24cb7-255">Match Between n and m Times (Lazy Match): {n,m}?</span></span>  
 <span data-ttu-id="24cb7-256">`{`  *n*  `,` *m* `}?` niceleyici eşleşir önceki arasında `n` ve `m` zaman, nerede  *n*  ve *m* tamsayılar, mümkün olduğunca ancak gibi birkaç kez olur.</span><span class="sxs-lookup"><span data-stu-id="24cb7-256">The `{`*n*`,`*m*`}?` quantifier matches the preceding element between `n` and `m` times, where *n* and *m* are integers, but as few times as possible.</span></span> <span data-ttu-id="24cb7-257">Doyumsuz nicelik, yavaş karşılık gelen olan `{`  *n*  `,` *m*`}`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-257">It is the lazy counterpart of the greedy quantifier `{`*n*`,`*m*`}`.</span></span>  
  
 <span data-ttu-id="24cb7-258">Aşağıdaki örnekte, normal ifade `\b[A-Z](\w*\s+){1,10}?[.!?]` arasında bir ve on sözcükler içeren tümceler eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-258">In the following example, the regular expression `\b[A-Z](\w*\s+){1,10}?[.!?]` matches sentences that contain between one and ten words.</span></span> <span data-ttu-id="24cb7-259">Giriş dizesi 18 sözcükler içeren bir cümle hariç tüm cümlelerde eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-259">It matches all the sentences in the input string except for one sentence that contains 18 words.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 <span data-ttu-id="24cb7-260">Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24cb7-260">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="24cb7-261">Desen</span><span class="sxs-lookup"><span data-stu-id="24cb7-261">Pattern</span></span>|<span data-ttu-id="24cb7-262">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cb7-262">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="24cb7-263">Bir sözcük sınırında başla.</span><span class="sxs-lookup"><span data-stu-id="24cb7-263">Start at a word boundary.</span></span>|  
|`[A-Z]`|<span data-ttu-id="24cb7-264">Bir büyük harf karakter A'dan Z'ye eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="24cb7-264">Match an uppercase character from A to Z.</span></span>|  
|`(\w*\s+)`|<span data-ttu-id="24cb7-265">Bir veya daha fazla boşluk karakterlerinin ardından sıfır veya daha fazla word karakterlerle eşleşen.</span><span class="sxs-lookup"><span data-stu-id="24cb7-265">Match zero or more word characters, followed by one or more white-space characters.</span></span> <span data-ttu-id="24cb7-266">Bu ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="24cb7-266">This is the first capture group.</span></span>|  
|`{1,10}?`|<span data-ttu-id="24cb7-267">1 ile 10 zamanları arasında ancak mümkün olduğunca birkaç kez olarak önceki desenle eşleşen.</span><span class="sxs-lookup"><span data-stu-id="24cb7-267">Match the previous pattern between 1 and 10 times, but as few times as possible.</span></span>|  
|`[.!?]`|<span data-ttu-id="24cb7-268">Herhangi bir noktalama karakter eşleşmesi ".","!", veya "?".</span><span class="sxs-lookup"><span data-stu-id="24cb7-268">Match any one of the punctuation characters ".", "!", or "?".</span></span>|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a><span data-ttu-id="24cb7-269">Doyumsuz ve yavaş miktar belirleyiciler</span><span class="sxs-lookup"><span data-stu-id="24cb7-269">Greedy and Lazy Quantifiers</span></span>  
 <span data-ttu-id="24cb7-270">Miktar belirleyiciler iki sürümü vardır:</span><span class="sxs-lookup"><span data-stu-id="24cb7-270">A number of the quantifiers have two versions:</span></span>  
  
-   <span data-ttu-id="24cb7-271">Doyumsuz bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="24cb7-271">A greedy version.</span></span>  
  
     <span data-ttu-id="24cb7-272">Doyumsuz niceleyici öğenin olası sayıda eşleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="24cb7-272">A greedy quantifier tries to match an element as many times as possible.</span></span>  
  
-   <span data-ttu-id="24cb7-273">Doyumsuz olmayan (veya yavaş) sürümü.</span><span class="sxs-lookup"><span data-stu-id="24cb7-273">A non-greedy (or lazy) version.</span></span>  
  
     <span data-ttu-id="24cb7-274">Doyumsuz olmayan niceleyici öğenin mümkün olduğunca birkaç kez eşleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="24cb7-274">A non-greedy quantifier tries to match an element as few times as possible.</span></span> <span data-ttu-id="24cb7-275">Basitçe ekleyerek yavaş niceleyici doyumsuz niceleyici kapatabilirsiniz bir `?`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-275">You can turn a greedy quantifier into a lazy quantifier by simply adding a `?`.</span></span>  
  
 <span data-ttu-id="24cb7-276">Kredi kartı numarası gibi sayıların bir dizeden son dört rakamı ayıklamak için tasarlanmıştır basit bir normal ifade göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="24cb7-276">Consider a simple regular expression that is intended to extract the last four digits from a string of numbers such as a credit card number.</span></span> <span data-ttu-id="24cb7-277">Kullanan normal ifade sürümü `*` doyumsuz niceleyici olan `\b.*([0-9]{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-277">The version of the regular expression that uses the `*` greedy quantifier is `\b.*([0-9]{4})\b`.</span></span> <span data-ttu-id="24cb7-278">Ancak, bir dize iki sayı içeriyorsa, bu normal ifade aşağıdaki örnekte gösterildiği gibi ikinci sayı yalnızca, son dört rakamı eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-278">However, if a string contains two numbers, this regular expression matches the last four digits of the second number only, as the following example shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 <span data-ttu-id="24cb7-279">İlk sayı çünkü eşleştirmek normal ifade başarısız `*` niceleyici çalışırsa önceki öğesi tüm dizeyi mümkün olduğunca çok kez olarak eşleşecek şekilde ve eşini dizesi sonunda bulduğu şekilde.</span><span class="sxs-lookup"><span data-stu-id="24cb7-279">The regular expression fails to match the first number because the `*` quantifier tries to match the previous element as many times as possible in the entire string, and so it finds its match at the end of the string.</span></span>  
  
 <span data-ttu-id="24cb7-280">Bu istediğiniz davranış değildir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-280">This is not the desired behavior.</span></span> <span data-ttu-id="24cb7-281">Bunun yerine, kullanabileceğiniz `*?`basamak aşağıdaki örnekte gösterildiği gibi her iki numarayı ayıklamak için yavaş niceleyici.</span><span class="sxs-lookup"><span data-stu-id="24cb7-281">Instead, you can use the `*?`lazy quantifier to extract digits from both numbers, as the following example shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 <span data-ttu-id="24cb7-282">Çoğu durumda, aynı eşleşmeleri doyumsuz ve yavaş miktar belirleyiciler Normal ifadelerle döndür.</span><span class="sxs-lookup"><span data-stu-id="24cb7-282">In most cases, regular expressions with greedy and lazy quantifiers return the same matches.</span></span> <span data-ttu-id="24cb7-283">Joker karakterle kullanıldığında bunlar en yaygın olarak farklı sonuçlar döndürür (`.`) meta karakteri, herhangi bir karakter ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-283">They most commonly return different results when they are used with the wildcard (`.`) metacharacter, which matches any character.</span></span>  
  
## <a name="quantifiers-and-empty-matches"></a><span data-ttu-id="24cb7-284">Miktar belirleyiciler ve boş eşleşiyor</span><span class="sxs-lookup"><span data-stu-id="24cb7-284">Quantifiers and Empty Matches</span></span>  
 <span data-ttu-id="24cb7-285">Miktar belirleyiciler `*`, `+`, ve `{`  *n*  `,` *m* `}` ve yavaş dekiler sonra boş bir hiçbir zaman tekrarlayın. en az sayıda yakalamaları bulduğunuz sırada eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="24cb7-285">The quantifiers `*`, `+`, and `{`*n*`,`*m*`}` and their lazy counterparts never repeat after an empty match when the minimum number of captures has been found.</span></span> <span data-ttu-id="24cb7-286">Bu kural, olası grup yakalamaları maksimum sayısı sonsuz olduğunda boş alt eşleşmeleri ya da sonsuz yanına sonsuz döngüler girişini nicelik engeller.</span><span class="sxs-lookup"><span data-stu-id="24cb7-286">This rule prevents quantifiers from entering infinite loops on empty subexpression matches when the maximum number of possible group captures is infinite or near infinite.</span></span>  
  
 <span data-ttu-id="24cb7-287">Örneğin, aşağıdaki kod bir çağrı sonucunu gösterir <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> normal ifade deseni yöntemiyle `(a?)*`, sıfır veya daha fazla kez sıfır veya bir "a" karakter eşleşir.</span><span class="sxs-lookup"><span data-stu-id="24cb7-287">For example, the following code shows the result of a call to the <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> method with the regular expression pattern `(a?)*`, which matches zero or one "a" character zero or more times.</span></span> <span data-ttu-id="24cb7-288">Tek bir yakalama Grup her "a" olarak yakalamalarına Not hem de <xref:System.String.Empty?displayProperty=nameWithType>, ancak bu ilk boş eşleşme yinelenen durdurmak niceleyici neden olduğundan ikinci boş eşleşme olduğunu.</span><span class="sxs-lookup"><span data-stu-id="24cb7-288">Note that the single capturing group captures each "a" as well as <xref:System.String.Empty?displayProperty=nameWithType>, but that there is no second empty match, because the first empty match causes the quantifier to stop repeating.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 <span data-ttu-id="24cb7-289">En az tanımlayan bir yakalama grubunu ve maksimum sayısını yakalar ve yakalamaları sabit sayıda tanımlayan bir pratik birbirinden görmek için normal ifade desenleri göz önünde bulundurun. `(a\1|(?(1)\1)){0,2}` ve `(a\1|(?(1)\1)){2}`.</span><span class="sxs-lookup"><span data-stu-id="24cb7-289">To see the practical difference between a capturing group that defines a minimum and a maximum number of captures and one that defines a fixed number of captures, consider the regular expression patterns `(a\1|(?(1)\1)){0,2}` and `(a\1|(?(1)\1)){2}`.</span></span> <span data-ttu-id="24cb7-290">Her iki normal ifadeler aşağıdaki tabloda gösterildiği gibi tanımlanan tek bir yakalama grubunu oluşur.</span><span class="sxs-lookup"><span data-stu-id="24cb7-290">Both regular expressions consist of a single capturing group, which is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="24cb7-291">Desen</span><span class="sxs-lookup"><span data-stu-id="24cb7-291">Pattern</span></span>|<span data-ttu-id="24cb7-292">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cb7-292">Description</span></span>|  
|-------------|-----------------|  
|`(a\1`|<span data-ttu-id="24cb7-293">Ya da eşleşme ilk yakalanan grubunun değeri birlikte "a"...</span><span class="sxs-lookup"><span data-stu-id="24cb7-293">Either match "a" along with the value of the first captured group …</span></span>|  
|`&#124;(?(1)`|<span data-ttu-id="24cb7-294">…</span><span class="sxs-lookup"><span data-stu-id="24cb7-294">…</span></span> <span data-ttu-id="24cb7-295">veya ilk yakalanan Grup tanımlı olup olmadığını test etme.</span><span class="sxs-lookup"><span data-stu-id="24cb7-295">or test whether the first captured group has been defined.</span></span> <span data-ttu-id="24cb7-296">(Unutmayın `(?(1)` yapı bir yakalama grubunu tanımlamak değil.)</span><span class="sxs-lookup"><span data-stu-id="24cb7-296">(Note that the `(?(1)` construct does not define a capturing group.)</span></span>|  
|`\1))`|<span data-ttu-id="24cb7-297">İlk yakalanan grup varsa değerini eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="24cb7-297">If the first captured group exists, match its value.</span></span> <span data-ttu-id="24cb7-298">Grup mevcut değilse Grup eşleşir <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="24cb7-298">If the group does not exist, the group will match <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|  
  
 <span data-ttu-id="24cb7-299">İlk normal ifade bu deseni ve iki kez arasındaki eşleştirmeyi dener; İkincisi, tam olarak iki kez.</span><span class="sxs-lookup"><span data-stu-id="24cb7-299">The first regular expression tries to match this pattern between zero and two times; the second, exactly two times.</span></span> <span data-ttu-id="24cb7-300">İlk desen yakalamaları ilk yakalanmasını ile en az sayıda ulaştığında çünkü <xref:System.String.Empty?displayProperty=nameWithType>, hiçbir zaman eşleşecek şekilde denemek için yinelenen `a\1`; `{0,2}` niceleyici son yinelemede yalnızca boş eşleşmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="24cb7-300">Because the first pattern reaches its minimum number of captures with its first capture of <xref:System.String.Empty?displayProperty=nameWithType>, it never repeats to try to match `a\1`; the `{0,2}` quantifier allows only empty matches in the last iteration.</span></span> <span data-ttu-id="24cb7-301">Buna karşılık, ikinci normal ifadeyle eşleşir "a", değerlendirildiği `a\1` ikinci kez; yineleme, 2, en az sayıda sonra boş bir eşleşme yinelenecek altyapısı zorlar.</span><span class="sxs-lookup"><span data-stu-id="24cb7-301">In contrast, the second regular expression does match "a" because it evaluates `a\1` a second time; the minimum number of iterations, 2, forces the engine to repeat after an empty match.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="24cb7-302">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24cb7-302">See Also</span></span>  
 [<span data-ttu-id="24cb7-303">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="24cb7-303">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [<span data-ttu-id="24cb7-304">Geri Dönüş</span><span class="sxs-lookup"><span data-stu-id="24cb7-304">Backtracking</span></span>](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
