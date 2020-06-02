---
title: .NET normal Ifadelerinde geri başvuru yapıları
description: Normal bir ifadede yeniden başvuru yapılarını kullanarak yinelenen metin öğelerini nasıl tanımlayacağınızı öğrenin.
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
ms.openlocfilehash: 87c3dbde2eb2b5a19b91f34bb2b088af5c0d1827
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290610"
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="a3441-103">Normal İfadelerdeki Yeniden Başvuru Yapıları</span><span class="sxs-lookup"><span data-stu-id="a3441-103">Backreference Constructs in Regular Expressions</span></span>

<span data-ttu-id="a3441-104">Geri başvurular, bir dize içinde yinelenen bir karakter veya alt dizenin tanımlanması için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3441-104">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="a3441-105">Örneğin, giriş dizesi rastgele bir alt dizenin birden çok oluşumunu içeriyorsa, ilk oluşumu bir yakalama grubuyla eşleştirebilir ve sonra alt dizenin sonraki tekrarlamalarını eşleştirmek için bir geri başvuru kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3441-105">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>

> [!NOTE]
> <span data-ttu-id="a3441-106">Değiştirme dizelerindeki adlandırılmış ve Numaralandırılmış yakalama gruplarına başvurmak için ayrı bir sözdizimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a3441-106">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="a3441-107">Daha fazla bilgi için bkz. [alternatifler](substitutions-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a3441-107">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>

<span data-ttu-id="a3441-108">.NET, numaralandırılmış ve adlandırılmış yakalama gruplarına başvuracak ayrı dil öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a3441-108">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="a3441-109">Grupları yakalama hakkında daha fazla bilgi için bkz. [gruplandırma yapıları](grouping-constructs-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a3441-109">For more information about capturing groups, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).</span></span>

## <a name="numbered-backreferences"></a><span data-ttu-id="a3441-110">Numaralandırılmış geri başvurular</span><span class="sxs-lookup"><span data-stu-id="a3441-110">Numbered Backreferences</span></span>

<span data-ttu-id="a3441-111">Numaralandırılmış geri başvuru, aşağıdaki sözdizimini kullanır:</span><span class="sxs-lookup"><span data-stu-id="a3441-111">A numbered backreference uses the following syntax:</span></span>

<span data-ttu-id="a3441-112">`\`*sayı*</span><span class="sxs-lookup"><span data-stu-id="a3441-112">`\` *number*</span></span>

<span data-ttu-id="a3441-113">Burada *sayı* , normal ifadede yakalama grubunun sıralı konumudur.</span><span class="sxs-lookup"><span data-stu-id="a3441-113">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="a3441-114">Örneğin, `\4` dördüncü yakalama grubunun içeriğiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="a3441-114">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="a3441-115">*Sayı* normal ifade modelinde tanımlanmamışsa, bir ayrıştırma hatası oluşur ve normal ifade altyapısı bir oluşturur <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="a3441-115">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="a3441-116">Örneğin, `\b(\w+)\s\1` `(\w+)` ifadedeki ilk ve tek yakalama grubu olduğundan, normal ifade geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="a3441-116">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="a3441-117">Öte yandan, `\b(\w+)\s\2` geçersizdir ve numaralandırılmış bir yakalama grubu bulunmadığından bir bağımsız değişken özel durumu oluşturur `\2` .</span><span class="sxs-lookup"><span data-stu-id="a3441-117">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span> <span data-ttu-id="a3441-118">Ayrıca, *sayı* belirli bir sıra konumunda bir yakalama grubu tanımlarsa, ancak bu yakalama grubuna sıra konumundan farklı bir sayısal ad atanmışsa, normal ifade ayrıştırıcısı da bir oluşturur <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="a3441-118">In addition, if *number* identifies a capturing group in a particular ordinal position, but that capturing group has been assigned a numeric name different than its ordinal position, the regular expression parser also throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="a3441-119">Sekizlik kaçış kodları (gibi `\16` ) ve `\` aynı gösterimi kullanan *numara* geri başvuruları arasındaki belirsizlik ' i unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a3441-119">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="a3441-120">Bu belirsizlik aşağıdaki şekilde çözümlenir:</span><span class="sxs-lookup"><span data-stu-id="a3441-120">This ambiguity is resolved as follows:</span></span>

- <span data-ttu-id="a3441-121">`\1`Aracılığıyla yapılan ifadeler `\9` her zaman geri başvuru olarak yorumlanır ve sekizlik kodlar değildir.</span><span class="sxs-lookup"><span data-stu-id="a3441-121">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>

- <span data-ttu-id="a3441-122">Çok basamaklı bir ifadenin ilk rakamı 8 veya 9 ( `\80` veya gibi `\91` ) ise, ifade değişmez değer olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="a3441-122">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>

- <span data-ttu-id="a3441-123">`\10`Ve üzeri ifadeler, bu numaraya karşılık gelen bir geri başvuru varsa, geri başvuru olarak kabul edilir; Aksi takdirde, sekizlik kodlar olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="a3441-123">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>

- <span data-ttu-id="a3441-124">Normal bir ifade tanımsız bir grup numarasına geri başvuru içeriyorsa, bir ayrıştırma hatası oluşur ve normal ifade altyapısı bir oluşturur <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="a3441-124">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="a3441-125">Belirsizlik bir sorun ise, `\k<` *name* `>` belirsiz olan ve sekizli karakter kodlarıyla karıştırılmamalıdır olan ad gösterimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3441-125">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="a3441-126">Benzer şekilde, gibi onaltılık kodlar ise `\xdd` ve geri başvurularıyla karıştırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a3441-126">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>

<span data-ttu-id="a3441-127">Aşağıdaki örnek bir dizedeki iki katına oluşan sözcük karakterlerini bulur.</span><span class="sxs-lookup"><span data-stu-id="a3441-127">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="a3441-128">Aşağıdaki öğelerden oluşan bir normal ifadeyi tanımlar `(\w)\1` .</span><span class="sxs-lookup"><span data-stu-id="a3441-128">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>

|<span data-ttu-id="a3441-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3441-129">Element</span></span>|<span data-ttu-id="a3441-130">Description</span><span class="sxs-lookup"><span data-stu-id="a3441-130">Description</span></span>|
|-------------|-----------------|
|`(\w)`|<span data-ttu-id="a3441-131">Bir sözcük karakterini eşleştirin ve ilk yakalama grubuna atayın.</span><span class="sxs-lookup"><span data-stu-id="a3441-131">Match a word character and assign it to the first capturing group.</span></span>|
|`\1`|<span data-ttu-id="a3441-132">İlk yakalama grubunun değeriyle aynı olan bir sonraki karakterle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="a3441-132">Match the next character that is the same as the value of the first capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a><span data-ttu-id="a3441-133">Adlandırılmış geri başvurular</span><span class="sxs-lookup"><span data-stu-id="a3441-133">Named Backreferences</span></span>

<span data-ttu-id="a3441-134">Adlandırılmış bir geri başvuru, aşağıdaki sözdizimi kullanılarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="a3441-134">A named backreference is defined by using the following syntax:</span></span>

<span data-ttu-id="a3441-135">`\k<`*ad*`>`</span><span class="sxs-lookup"><span data-stu-id="a3441-135">`\k<` *name* `>`</span></span>

<span data-ttu-id="a3441-136">veya:</span><span class="sxs-lookup"><span data-stu-id="a3441-136">or:</span></span>

<span data-ttu-id="a3441-137">`\k'`*ad*`'`</span><span class="sxs-lookup"><span data-stu-id="a3441-137">`\k'` *name* `'`</span></span>

<span data-ttu-id="a3441-138">Burada *ad* , normal ifade düzeninde tanımlanan yakalama grubunun adıdır.</span><span class="sxs-lookup"><span data-stu-id="a3441-138">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="a3441-139">*Ad* normal ifade modelinde tanımlanmamışsa, bir ayrıştırma hatası oluşur ve normal ifade altyapısı bir oluşturur <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="a3441-139">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="a3441-140">Aşağıdaki örnek bir dizedeki iki katına oluşan sözcük karakterlerini bulur.</span><span class="sxs-lookup"><span data-stu-id="a3441-140">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="a3441-141">Aşağıdaki öğelerden oluşan bir normal ifadeyi tanımlar `(?<char>\w)\k<char>` .</span><span class="sxs-lookup"><span data-stu-id="a3441-141">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>

|<span data-ttu-id="a3441-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3441-142">Element</span></span>|<span data-ttu-id="a3441-143">Description</span><span class="sxs-lookup"><span data-stu-id="a3441-143">Description</span></span>|
|-------------|-----------------|
|`(?<char>\w)`|<span data-ttu-id="a3441-144">Bir sözcük karakterini eşleştirin ve adlı bir yakalama grubuna atayın `char` .</span><span class="sxs-lookup"><span data-stu-id="a3441-144">Match a word character and assign it to a capturing group named `char`.</span></span>|
|`\k<char>`|<span data-ttu-id="a3441-145">Yakalama grubu değeriyle aynı olan bir sonraki karakterle eşleştirin `char` .</span><span class="sxs-lookup"><span data-stu-id="a3441-145">Match the next character that is the same as the value of the `char` capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a><span data-ttu-id="a3441-146">Adlandırılmış sayısal geribaşvurular</span><span class="sxs-lookup"><span data-stu-id="a3441-146">Named numeric backreferences</span></span>

<span data-ttu-id="a3441-147">Adlı adlandırılmış bir geri başvuru içinde `\k` , *ad* bir sayının dize temsili de olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3441-147">In a named backreference with `\k`, *name* can also be the string representation of a number.</span></span> <span data-ttu-id="a3441-148">Örneğin, aşağıdaki örnek, `(?<2>\w)\k<2>` bir dizedeki iki katına oluşan sözcük karakterlerini bulmak için normal ifadeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a3441-148">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span> <span data-ttu-id="a3441-149">Bu durumda, örnek "2" olarak adlandırılan bir yakalama grubunu tanımlar ve geri başvuru "2" olarak adlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a3441-149">In this case, the example defines a capturing group that is explicitly named "2", and the backreference is correspondingly named "2".</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

<span data-ttu-id="a3441-150">*Ad* bir sayının dize gösterimiyse ve yakalama grubu bu ada sahip değilse, `\k<` *ad* `>` geri başvuru `\` *numarasıyla*aynıdır, burada *sayı* yakalamanın sıra konumudur.</span><span class="sxs-lookup"><span data-stu-id="a3441-150">If *name* is the string representation of a number, and no capturing group has that name, `\k<`*name*`>` is the same as the backreference `\`*number*, where *number* is the ordinal position of the capture.</span></span> <span data-ttu-id="a3441-151">Aşağıdaki örnekte adlı tek bir yakalama grubu vardır `char` .</span><span class="sxs-lookup"><span data-stu-id="a3441-151">In the following example, there is a single capturing group named `char`.</span></span> <span data-ttu-id="a3441-152">Geribaşvuru yapısı, bu öğeyi olarak ifade eder `\k<1>` .</span><span class="sxs-lookup"><span data-stu-id="a3441-152">The backreference construct refers to it as `\k<1>`.</span></span> <span data-ttu-id="a3441-153">Örneğin çıkışının gösterdiği gibi, <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> ilk yakalama grubu olduğundan, başarılı olma çağrısı `char` .</span><span class="sxs-lookup"><span data-stu-id="a3441-153">As the output from the example shows, the call to the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> succeeds because `char` is the first capturing group.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

<span data-ttu-id="a3441-154">Ancak, *ad* bir sayının dize gösterimiyse ve bu konumdaki yakalama grubuna açıkça sayısal bir ad atanmışsa, normal ifade ayrıştırıcısı yakalama grubunu sıra konumuna göre tanımlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="a3441-154">However, if *name* is the string representation of a number and the capturing group in that position has been explicitly assigned a numeric name, the regular expression parser cannot identify the capturing group by its ordinal position.</span></span> <span data-ttu-id="a3441-155">Bunun yerine, bir oluşturur <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="a3441-155">Instead, it throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="a3441-156">Aşağıdaki örnekteki tek yakalama grubu "2" olarak adlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a3441-156">The only capturing group in the following example is named "2".</span></span> <span data-ttu-id="a3441-157">Yapı, `\k` "1" adlı bir geri başvuru tanımlamak için kullanıldığından, normal ifade ayrıştırıcısı ilk yakalama grubunu tanımlayamıyor ve bir özel durum oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="a3441-157">Because the `\k` construct is used to define a backreference named "1", the regular expression parser is unable to identify the first capturing group and throws an exception.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a><span data-ttu-id="a3441-158">Hangi geribaşvuruların eşleşmesi</span><span class="sxs-lookup"><span data-stu-id="a3441-158">What Backreferences Match</span></span>

<span data-ttu-id="a3441-159">Geri başvuru, bir grubun en son tanımına (soldan sağa eşleştirilirken en yakın bir tanım) başvurur.</span><span class="sxs-lookup"><span data-stu-id="a3441-159">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="a3441-160">Bir grup birden çok yakalama yaptığında, geri başvuru en son yakalamayı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="a3441-160">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>

<span data-ttu-id="a3441-161">Aşağıdaki örnek, `(?<1>a)(?<1>\1b)*` \ 1 adlandırılmış grubunu tekrar tanımlayan bir normal ifade deseninin yer aldığı bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="a3441-161">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="a3441-162">Aşağıdaki tabloda, Normal ifadedeki her bir model açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3441-162">The following table describes each pattern in the regular expression.</span></span>

|<span data-ttu-id="a3441-163">Desen</span><span class="sxs-lookup"><span data-stu-id="a3441-163">Pattern</span></span>|<span data-ttu-id="a3441-164">Description</span><span class="sxs-lookup"><span data-stu-id="a3441-164">Description</span></span>|
|-------------|-----------------|
|`(?<1>a)`|<span data-ttu-id="a3441-165">"A" karakteriyle eşleşir ve sonucu adlı yakalama grubuna atayın `1` .</span><span class="sxs-lookup"><span data-stu-id="a3441-165">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|
|`(?<1>\1b)*`|<span data-ttu-id="a3441-166">"B" ile birlikte adlı grubun sıfır veya daha fazla `1` tekrarlanmasını eşleştirin ve sonucu adlı yakalama grubuna atayın `1` .</span><span class="sxs-lookup"><span data-stu-id="a3441-166">Match zero or more occurrences of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

<span data-ttu-id="a3441-167">Normal ifadeyi giriş dizesiyle ("aababb") karşılaştırırken, normal ifade altyapısı aşağıdaki işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="a3441-167">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>

1. <span data-ttu-id="a3441-168">Bu, dizenin başlangıcında başlar ve ifadesiyle "a" ile başarılı bir şekilde eşleşir `(?<1>a)` .</span><span class="sxs-lookup"><span data-stu-id="a3441-168">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="a3441-169">`1`Grubun değeri artık "a" dır.</span><span class="sxs-lookup"><span data-stu-id="a3441-169">The value of the `1` group is now "a".</span></span>

2. <span data-ttu-id="a3441-170">İkinci karaktere ilerletir ve "AB" dizesiyle `\1b` , veya "AB" ifadesiyle başarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="a3441-170">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="a3441-171">Ardından "AB" sonucunu atar `\1` .</span><span class="sxs-lookup"><span data-stu-id="a3441-171">It then assigns the result, "ab" to `\1`.</span></span>

3. <span data-ttu-id="a3441-172">Dördüncü karaktere ilerletir.</span><span class="sxs-lookup"><span data-stu-id="a3441-172">It advances to the fourth character.</span></span> <span data-ttu-id="a3441-173">İfade `(?<1>\1b)*` sıfır veya daha fazla kez eşleştirilecek, bu nedenle "abb" dizesiyle birlikte ifadesiyle başarıyla eşleşiyor `\1b` .</span><span class="sxs-lookup"><span data-stu-id="a3441-173">The expression `(?<1>\1b)*` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="a3441-174">"Abb" sonucunu, öğesine geri atar `\1` .</span><span class="sxs-lookup"><span data-stu-id="a3441-174">It assigns the result, "abb", back to `\1`.</span></span>

<span data-ttu-id="a3441-175">Bu örnekte, `*` bir döngü nicelik belirteci, normal ifade altyapısı tanımladığı Düzenle eşleşene kadar sürekli değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a3441-175">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="a3441-176">Döngü nicelik belirteçleri grup tanımlarını temizlemez.</span><span class="sxs-lookup"><span data-stu-id="a3441-176">Looping quantifiers do not clear group definitions.</span></span>

<span data-ttu-id="a3441-177">Bir grupta herhangi bir alt dize yakalanmadıysa, bu gruba yönelik bir geri başvuru tanımsızdır ve hiçbir şekilde eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="a3441-177">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="a3441-178">Bu, aşağıdaki gibi tanımlanan normal ifade deseninin gösterilmektedir `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` :</span><span class="sxs-lookup"><span data-stu-id="a3441-178">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>

|<span data-ttu-id="a3441-179">Desen</span><span class="sxs-lookup"><span data-stu-id="a3441-179">Pattern</span></span>|<span data-ttu-id="a3441-180">Description</span><span class="sxs-lookup"><span data-stu-id="a3441-180">Description</span></span>|
|-------------|-----------------|
|`\b`|<span data-ttu-id="a3441-181">Eşleşmeyi bir sözcük sınırında başlatın.</span><span class="sxs-lookup"><span data-stu-id="a3441-181">Begin the match on a word boundary.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="a3441-182">İki büyük harfi eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="a3441-182">Match two uppercase letters.</span></span> <span data-ttu-id="a3441-183">Bu ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="a3441-183">This is the first capturing group.</span></span>|
|`(\d{2})?`|<span data-ttu-id="a3441-184">İki ondalık basamağın sıfır veya bir oluşumunu eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="a3441-184">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="a3441-185">Bu ikinci yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="a3441-185">This is the second capturing group.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="a3441-186">İki büyük harfi eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="a3441-186">Match two uppercase letters.</span></span> <span data-ttu-id="a3441-187">Bu, üçüncü yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="a3441-187">This is the third capturing group.</span></span>|
|`\b`|<span data-ttu-id="a3441-188">Eşleşmeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="a3441-188">End the match on a word boundary.</span></span>|

<span data-ttu-id="a3441-189">İkinci yakalama grubu tarafından tanımlanan iki ondalık basamak mevcut olmasa bile, bir giriş dizesi bu normal ifadeyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="a3441-189">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="a3441-190">Aşağıdaki örnekte, eşleşme başarılı olsa da, iki başarılı yakalama grubu arasında boş bir yakalama grubu bulunur.</span><span class="sxs-lookup"><span data-stu-id="a3441-190">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="a3441-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3441-191">See also</span></span>

- [<span data-ttu-id="a3441-192">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="a3441-192">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
