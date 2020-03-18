---
title: .NET Düzenli İfadelerde Backreference Yapıları
description: Normal bir ifadede geri başvuru yapılarını kullanarak yinelenen metin öğelerini nasıl tanımlayarak tanımlayın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
ms.openlocfilehash: 905578d763ebe5d5b8eb96a9056fbe11fbfab137
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711538"
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="907a2-103">Normal İfadelerdeki Yeniden Başvuru Yapıları</span><span class="sxs-lookup"><span data-stu-id="907a2-103">Backreference Constructs in Regular Expressions</span></span>

<span data-ttu-id="907a2-104">Geri göndermeler, yinelenen bir karakteri veya bir dize içindeki alt dizeyi tanımlamak için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="907a2-104">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="907a2-105">Örneğin, giriş dizesi rasgele bir alt dize birden çok olay içeriyorsa, bir yakalama grubu ile ilk oluşumu eşleşebilir ve sonra substring sonraki oluşumları eşleştirmek için bir backreference kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="907a2-105">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>

> [!NOTE]
> <span data-ttu-id="907a2-106">Değiştirme dizelerinde adlandırılmış ve numaralandırılmış yakalama gruplarını ifade etmek için ayrı bir sözdizimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="907a2-106">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="907a2-107">Daha fazla bilgi için [Bkz.](substitutions-in-regular-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="907a2-107">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>

<span data-ttu-id="907a2-108">.NET, numaralandırılmış ve adlandırılmış yakalama gruplarına başvurmak için ayrı dil öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="907a2-108">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="907a2-109">Grupları yakalama hakkında daha fazla bilgi için [yapıyı gruplandırma'ya](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="907a2-109">For more information about capturing groups, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>

## <a name="numbered-backreferences"></a><span data-ttu-id="907a2-110">Numaralı Referanslar</span><span class="sxs-lookup"><span data-stu-id="907a2-110">Numbered Backreferences</span></span>

<span data-ttu-id="907a2-111">Numaralı bir geri başvuru aşağıdaki sözdizimini kullanır:</span><span class="sxs-lookup"><span data-stu-id="907a2-111">A numbered backreference uses the following syntax:</span></span>

<span data-ttu-id="907a2-112">`\` *number*</span><span class="sxs-lookup"><span data-stu-id="907a2-112">`\` *number*</span></span>

<span data-ttu-id="907a2-113">*numaranın* normal ifadedeki yakalama grubunun ordinal konumu olduğu yer.</span><span class="sxs-lookup"><span data-stu-id="907a2-113">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="907a2-114">Örneğin, `\4` dördüncü yakalama grubunun içeriğiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="907a2-114">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="907a2-115">Normal ifade deseninde *sayı* tanımlanmamışsa, ayrıştırma hatası oluşur ve <xref:System.ArgumentException>normal ifade altyapısı .</span><span class="sxs-lookup"><span data-stu-id="907a2-115">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="907a2-116">Örneğin, ifadedeki `\b(\w+)\s\1` ilk ve `(\w+)` tek yakalama grubu olduğundan, normal ifade geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="907a2-116">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="907a2-117">Diğer taraftan, `\b(\w+)\s\2` geçersizdir ve numaralandırılmış `\2`yakalama grubu olmadığından bağımsız değişken özel durumu atar.</span><span class="sxs-lookup"><span data-stu-id="907a2-117">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span> <span data-ttu-id="907a2-118">Buna ek olarak, *sayı* belirli bir ordinal konumda bir yakalama grubu tanımlar, ancak bu yakalama grubu kendi ordinal konumu farklı sayısal <xref:System.ArgumentException>bir ad atanmış sayılsa, normal ifade parer de bir .</span><span class="sxs-lookup"><span data-stu-id="907a2-118">In addition, if *number* identifies a capturing group in a particular ordinal position, but that capturing group has been assigned a numeric name different than its ordinal position, the regular expression parser also throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="907a2-119">Sekizli kaçış kodları (örneğin) `\16`ve `\`aynı gösterimi kullanan *sayı* geri başvuruları arasındaki belirsizliğe dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="907a2-119">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="907a2-120">Bu belirsizlik aşağıdaki gibi çözülür:</span><span class="sxs-lookup"><span data-stu-id="907a2-120">This ambiguity is resolved as follows:</span></span>

- <span data-ttu-id="907a2-121">Üzerinden ifadeler `\1` `\9` her zaman backreferences olarak yorumlanır, değil, sekizkodlar olarak.</span><span class="sxs-lookup"><span data-stu-id="907a2-121">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>

- <span data-ttu-id="907a2-122">Çok basamaklı bir ifadenin ilk basamağı 8 `\80` `\91`veya 9 ise (gibi), ifade tam olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="907a2-122">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>

- <span data-ttu-id="907a2-123">Bu sayıya karşılık gelen bir geri başvuru varsa, gelen `\10` ve daha büyük ifadeler geri başvuru olarak kabul edilir; aksi takdirde, sekizkodlu olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="907a2-123">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>

- <span data-ttu-id="907a2-124">Normal bir ifade tanımlanmamış bir grup numarasına geri gönderme içeriyorsa, ayrıştırma hatası <xref:System.ArgumentException>oluşur ve normal ifade altyapısı .</span><span class="sxs-lookup"><span data-stu-id="907a2-124">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="907a2-125">Belirsizlik bir sorunsa, açık olan `\k<`ve sekizli karakter kodlarıyla karıştırılamayan *ad* `>` gösterimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="907a2-125">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="907a2-126">Benzer şekilde, hexadecimal `\xdd` kodlar gibi kesin ve backreferences ile karıştırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="907a2-126">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>

<span data-ttu-id="907a2-127">Aşağıdaki örnekte, bir dizedeki iki katına çıkan sözcük karakterleri bulur.</span><span class="sxs-lookup"><span data-stu-id="907a2-127">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="907a2-128">Aşağıdaki öğelerden oluşan `(\w)\1`düzenli bir ifade tanımlar.</span><span class="sxs-lookup"><span data-stu-id="907a2-128">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>

|<span data-ttu-id="907a2-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="907a2-129">Element</span></span>|<span data-ttu-id="907a2-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="907a2-130">Description</span></span>|
|-------------|-----------------|
|`(\w)`|<span data-ttu-id="907a2-131">Bir sözcük karakterini eşleştirin ve ilk yakalama grubuna atayın.</span><span class="sxs-lookup"><span data-stu-id="907a2-131">Match a word character and assign it to the first capturing group.</span></span>|
|`\1`|<span data-ttu-id="907a2-132">İlk yakalama grubunun değeriyle aynı olan bir sonraki karakteri eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="907a2-132">Match the next character that is the same as the value of the first capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a><span data-ttu-id="907a2-133">İsimli Backreferences</span><span class="sxs-lookup"><span data-stu-id="907a2-133">Named Backreferences</span></span>

<span data-ttu-id="907a2-134">Adlandırılmış bir geri başvuru aşağıdaki sözdizimi kullanılarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="907a2-134">A named backreference is defined by using the following syntax:</span></span>

<span data-ttu-id="907a2-135">`\k<`*isim*`>`</span><span class="sxs-lookup"><span data-stu-id="907a2-135">`\k<` *name* `>`</span></span>

<span data-ttu-id="907a2-136">veya:</span><span class="sxs-lookup"><span data-stu-id="907a2-136">or:</span></span>

<span data-ttu-id="907a2-137">`\k'`*isim*`'`</span><span class="sxs-lookup"><span data-stu-id="907a2-137">`\k'` *name* `'`</span></span>

<span data-ttu-id="907a2-138">*adı* normal ifade deseni tanımlanan bir yakalama grubunun adıdır.</span><span class="sxs-lookup"><span data-stu-id="907a2-138">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="907a2-139">*Ad* normal ifade deseninde tanımlanmamışsa, ayrıştırma hatası oluşur ve <xref:System.ArgumentException>normal ifade altyapısı bir .</span><span class="sxs-lookup"><span data-stu-id="907a2-139">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="907a2-140">Aşağıdaki örnekte, bir dizedeki iki katına çıkan sözcük karakterleri bulur.</span><span class="sxs-lookup"><span data-stu-id="907a2-140">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="907a2-141">Aşağıdaki öğelerden oluşan `(?<char>\w)\k<char>`düzenli bir ifade tanımlar.</span><span class="sxs-lookup"><span data-stu-id="907a2-141">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>

|<span data-ttu-id="907a2-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="907a2-142">Element</span></span>|<span data-ttu-id="907a2-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="907a2-143">Description</span></span>|
|-------------|-----------------|
|`(?<char>\w)`|<span data-ttu-id="907a2-144">Bir sözcük karakterini eşleştirin ve onu `char`bir yakalama grubuna atayın.</span><span class="sxs-lookup"><span data-stu-id="907a2-144">Match a word character and assign it to a capturing group named `char`.</span></span>|
|`\k<char>`|<span data-ttu-id="907a2-145">`char` Yakalama grubunun değeriyle aynı olan bir sonraki karakteri eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="907a2-145">Match the next character that is the same as the value of the `char` capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a><span data-ttu-id="907a2-146">Sayısal geri referanslar adlı</span><span class="sxs-lookup"><span data-stu-id="907a2-146">Named numeric backreferences</span></span>

<span data-ttu-id="907a2-147">Adlandırılmış bir geri `\k`başvuruda , *adı* da bir sayının dize gösterimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="907a2-147">In a named backreference with `\k`, *name* can also be the string representation of a number.</span></span> <span data-ttu-id="907a2-148">Örneğin, aşağıdaki örnek, bir `(?<2>\w)\k<2>` dizede iki katına çıkan sözcük karakterlerini bulmak için normal ifadeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="907a2-148">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span> <span data-ttu-id="907a2-149">Bu durumda, örnek açıkça "2" adlı bir yakalama grubu tanımlar ve geri başvuru buna karşılık "2" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="907a2-149">In this case, the example defines a capturing group that is explicitly named "2", and the backreference is correspondingly named "2".</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

<span data-ttu-id="907a2-150">*Ad* bir sayının dize gösterimiyse ve hiçbir yakalama `\k<`grubu bu ada `\`sahipdeğilse, *ad,* `>` *numaranın* yakalamanın ordinal konumu olduğu backreference *numarasıyla*aynıdır.</span><span class="sxs-lookup"><span data-stu-id="907a2-150">If *name* is the string representation of a number, and no capturing group has that name, `\k<`*name*`>` is the same as the backreference `\`*number*, where *number* is the ordinal position of the capture.</span></span> <span data-ttu-id="907a2-151">Aşağıdaki örnekte, adlı `char`tek bir yakalama grubu vardır.</span><span class="sxs-lookup"><span data-stu-id="907a2-151">In the following example, there is a single capturing group named `char`.</span></span> <span data-ttu-id="907a2-152">Geri başvuru yapısı ona `\k<1>`.</span><span class="sxs-lookup"><span data-stu-id="907a2-152">The backreference construct refers to it as `\k<1>`.</span></span> <span data-ttu-id="907a2-153">Örnekteki çıktının gösterdiği gibi, ilk <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yakalama `char` grubu olduğu için başarılı olan çağrı.</span><span class="sxs-lookup"><span data-stu-id="907a2-153">As the output from the example shows, the call to the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> succeeds because `char` is the first capturing group.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

<span data-ttu-id="907a2-154">Ancak, *ad* bir sayının dize gösterimi yse ve bu konumdaki yakalama grubuna açıkça sayısal bir ad atanmışsa, normal ifade parlayıcısı yakalama grubunu kendi ordinal konumuna göre tanımlayamaz.</span><span class="sxs-lookup"><span data-stu-id="907a2-154">However, if *name* is the string representation of a number and the capturing group in that position has been explicitly assigned a numeric name, the regular expression parser cannot identify the capturing group by its ordinal position.</span></span> <span data-ttu-id="907a2-155">Bunun yerine, bir <xref:System.ArgumentException>atar .</span><span class="sxs-lookup"><span data-stu-id="907a2-155">Instead, it throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="907a2-156">Aşağıdaki örnekteki tek yakalama grubu "2" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="907a2-156">The only capturing group in the following example is named "2".</span></span> <span data-ttu-id="907a2-157">`\k` Yapı "1" adlı bir geri başvuru tanımlamak için kullanıldığından, normal ifade parer ilk yakalama grubunu tanımlayamaz ve bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="907a2-157">Because the `\k` construct is used to define a backreference named "1", the regular expression parser is unable to identify the first capturing group and throws an exception.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a><span data-ttu-id="907a2-158">Backreferences Match Ne</span><span class="sxs-lookup"><span data-stu-id="907a2-158">What Backreferences Match</span></span>

<span data-ttu-id="907a2-159">Bir geri başvuru, bir grubun en son tanımına (soldan sağa eşleşirken en çok sola doğru tanım) başvurur.</span><span class="sxs-lookup"><span data-stu-id="907a2-159">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="907a2-160">Bir grup birden çok yakalama yaptığında, bir geri başvuru en son yakalama anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="907a2-160">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>

<span data-ttu-id="907a2-161">Aşağıdaki örnek, `(?<1>a)(?<1>\1b)*`\1 adlı grubu yeniden tanımlayan normal bir ifade deseni içerir.</span><span class="sxs-lookup"><span data-stu-id="907a2-161">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="907a2-162">Aşağıdaki tabloda normal ifadedeki her desen açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="907a2-162">The following table describes each pattern in the regular expression.</span></span>

|<span data-ttu-id="907a2-163">Desen</span><span class="sxs-lookup"><span data-stu-id="907a2-163">Pattern</span></span>|<span data-ttu-id="907a2-164">Açıklama</span><span class="sxs-lookup"><span data-stu-id="907a2-164">Description</span></span>|
|-------------|-----------------|
|`(?<1>a)`|<span data-ttu-id="907a2-165">"a" karakterini eşleştirin ve sonucu ' yu `1`adlandırılmış yakalama grubuna atayın.</span><span class="sxs-lookup"><span data-stu-id="907a2-165">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|
|`(?<1>\1b)*`|<span data-ttu-id="907a2-166">"b" ile birlikte adlandırılan `1` grubun sıfır veya daha fazla oluşumlarını eşleştirin ve `1`sonucu ' yu ' adlı yakalama grubuna atayın.</span><span class="sxs-lookup"><span data-stu-id="907a2-166">Match zero or more occurrences of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

<span data-ttu-id="907a2-167">Normal ifadeyi giriş dizesi ("aababb") ile karşılaştırırken, normal ifade altyapısı aşağıdaki işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="907a2-167">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>

1. <span data-ttu-id="907a2-168">Bu dize başında başlar ve başarıyla ifade `(?<1>a)`ile "a" eşleşir.</span><span class="sxs-lookup"><span data-stu-id="907a2-168">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="907a2-169">`1` Grubun değeri artık "a"dır.</span><span class="sxs-lookup"><span data-stu-id="907a2-169">The value of the `1` group is now "a".</span></span>

2. <span data-ttu-id="907a2-170">İkinci karaktere ilerler ve "ab" dizesini `\1b`"ab" ifadesi veya "ab" ile başarıyla eşler.</span><span class="sxs-lookup"><span data-stu-id="907a2-170">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="907a2-171">Daha sonra sonucu atar, "ab" için `\1`.</span><span class="sxs-lookup"><span data-stu-id="907a2-171">It then assigns the result, "ab" to `\1`.</span></span>

3. <span data-ttu-id="907a2-172">Dördüncü karaktere doğru ilerler.</span><span class="sxs-lookup"><span data-stu-id="907a2-172">It advances to the fourth character.</span></span> <span data-ttu-id="907a2-173">İfade `(?<1>\1b)*` sıfır veya daha fazla kez eşleşecek, bu nedenle başarıyla "abb" `\1b`ifadesi ile dize eşleşir.</span><span class="sxs-lookup"><span data-stu-id="907a2-173">The expression `(?<1>\1b)*` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="907a2-174">Bu sonuç atar, "abb", `\1`geri .</span><span class="sxs-lookup"><span data-stu-id="907a2-174">It assigns the result, "abb", back to `\1`.</span></span>

<span data-ttu-id="907a2-175">Bu örnekte, `*` bir döngü niceleyicisidir -- normal ifade altyapısı tanımladığı desenle eşleştirene kadar tekrar tekrar değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="907a2-175">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="907a2-176">Döngü niceleyicileri grup tanımlarını temizlemez.</span><span class="sxs-lookup"><span data-stu-id="907a2-176">Looping quantifiers do not clear group definitions.</span></span>

<span data-ttu-id="907a2-177">Bir grup herhangi bir alt dize yakalamadıysa, bu gruba bir geri gönderme tanımsızdır ve hiçbir zaman eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="907a2-177">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="907a2-178">Bu aşağıdaki gibi tanımlanan `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`normal ifade deseni ile gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="907a2-178">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>

|<span data-ttu-id="907a2-179">Desen</span><span class="sxs-lookup"><span data-stu-id="907a2-179">Pattern</span></span>|<span data-ttu-id="907a2-180">Açıklama</span><span class="sxs-lookup"><span data-stu-id="907a2-180">Description</span></span>|
|-------------|-----------------|
|`\b`|<span data-ttu-id="907a2-181">Eşleşmeyi sözcük sınırında başlatın.</span><span class="sxs-lookup"><span data-stu-id="907a2-181">Begin the match on a word boundary.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="907a2-182">İki büyük harfle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="907a2-182">Match two uppercase letters.</span></span> <span data-ttu-id="907a2-183">Bu ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="907a2-183">This is the first capturing group.</span></span>|
|`(\d{2})?`|<span data-ttu-id="907a2-184">İki ondalık basamaktan sıfır veya bir oluşum eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="907a2-184">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="907a2-185">Bu ikinci yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="907a2-185">This is the second capturing group.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="907a2-186">İki büyük harfle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="907a2-186">Match two uppercase letters.</span></span> <span data-ttu-id="907a2-187">Bu, üçüncü yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="907a2-187">This is the third capturing group.</span></span>|
|`\b`|<span data-ttu-id="907a2-188">Eşleşmeyi sözcük sınırında sonla.</span><span class="sxs-lookup"><span data-stu-id="907a2-188">End the match on a word boundary.</span></span>|

<span data-ttu-id="907a2-189">İkinci yakalama grubu tarafından tanımlanan iki ondalık basamak mevcut olmasa bile, bir giriş dizesi bu normal ifadeyle eşleşebilir.</span><span class="sxs-lookup"><span data-stu-id="907a2-189">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="907a2-190">Aşağıdaki örnek, eşleşme başarılı olsa bile, iki başarılı yakalama grubu arasında boş bir yakalama grubu bulunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="907a2-190">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="907a2-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="907a2-191">See also</span></span>

- [<span data-ttu-id="907a2-192">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="907a2-192">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
