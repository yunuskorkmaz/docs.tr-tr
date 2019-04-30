---
title: .NET normal ifadelerde yeniden başvuru yapıları
description: Normal bir ifade içinde yeniden başvuru yapıları kullanarak yinelenen metin öğeleri tanımlamak öğrenin.
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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: d478ae9e1db86718236da73917d772820707ea03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698869"
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="ac10e-103">Normal İfadelerdeki Yeniden Başvuru Yapıları</span><span class="sxs-lookup"><span data-stu-id="ac10e-103">Backreference Constructs in Regular Expressions</span></span>

<span data-ttu-id="ac10e-104">Yeniden başvurular yinelenen karakter veya dize içinde alt dizeyi tanımlamak için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac10e-104">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="ac10e-105">Örneğin, giriş dizesini birden çok defa geçmelerine rastgele bir alt dizenin içeriyorsa, ilk geçtiği bir yakalama grubuyla eşleşen ve ardından alt dizeyi sonraki tekrarı ile eşleştir için bir yeniden başvuru kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac10e-105">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>

> [!NOTE]
> <span data-ttu-id="ac10e-106">Ayrı bir söz dizimi, adlandırılmış veya numaralandırılmış yakalama grupları değiştirme Dizelerdeki başvurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-106">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="ac10e-107">Daha fazla bilgi için bkz. [Değişimler](substitutions-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ac10e-107">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>

<span data-ttu-id="ac10e-108">.NET için numaralandırılmış ve adlandırılmış yakalama grupları başvurmak için ayrı dil öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac10e-108">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="ac10e-109">Yakalama grupları hakkında daha fazla bilgi için bkz. [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ac10e-109">For more information about capturing groups, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>

## <a name="numbered-backreferences"></a><span data-ttu-id="ac10e-110">Numaralandırılmış yeniden başvurular</span><span class="sxs-lookup"><span data-stu-id="ac10e-110">Numbered Backreferences</span></span>

<span data-ttu-id="ac10e-111">Numaralandırılmış bir yeniden başvuru aşağıdaki sözdizimini kullanır:</span><span class="sxs-lookup"><span data-stu-id="ac10e-111">A numbered backreference uses the following syntax:</span></span>

<span data-ttu-id="ac10e-112">`\` *Sayı*</span><span class="sxs-lookup"><span data-stu-id="ac10e-112">`\` *number*</span></span>

<span data-ttu-id="ac10e-113">Burada *numarası* normal ifadedeki yakalama grubunun sıralı konumu.</span><span class="sxs-lookup"><span data-stu-id="ac10e-113">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="ac10e-114">Örneğin, `\4` dördüncü yakalama grubunun içeriğiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="ac10e-114">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="ac10e-115">Varsa *numarası* normal ifade deseninde tanımlı değil, bir ayrıştırma hatasını ortaya çıkar ve normal ifade motoru oluşturur bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="ac10e-115">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="ac10e-116">Örneğin, normal ifade `\b(\w+)\s\1` geçerlidir, çünkü `(\w+)` ilk ve tek Grup ifadesinde yakalıyor.</span><span class="sxs-lookup"><span data-stu-id="ac10e-116">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="ac10e-117">Öte yandan, `\b(\w+)\s\2` numaralandırılmış yakalama grubu yok olduğundan bir bağımsız değişken özel durum oluşturur ve geçersiz `\2`.</span><span class="sxs-lookup"><span data-stu-id="ac10e-117">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span> <span data-ttu-id="ac10e-118">Ayrıca, varsa *numarası* sıralı belirli bir konumda bir yakalama grubunu tanımlar, yakalama grubu sayısal verildiğine göre ancak sıra konumuna farklı bir ad, normal ifade ayrıştırıcısı bir deoluşturur<xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="ac10e-118">In addition, if *number* identifies a capturing group in a particular ordinal position, but that capturing group has been assigned a numeric name different than its ordinal position, the regular expression parser also throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="ac10e-119">Sekizli çıkış kodlarını arasında belirsizlik unutmayın (gibi `\16`) ve `\` *numarası* aynı gösterimi kullanan yeniden başvurular.</span><span class="sxs-lookup"><span data-stu-id="ac10e-119">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="ac10e-120">Bu belirsizlik işlemler sırasında aşağıdaki gibi çözümlenir:</span><span class="sxs-lookup"><span data-stu-id="ac10e-120">This ambiguity is resolved as follows:</span></span>

- <span data-ttu-id="ac10e-121">İfadeleri `\1` aracılığıyla `\9` her zaman yeniden başvurular ve sekizlik kodları değil olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-121">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>

- <span data-ttu-id="ac10e-122">İlk basamak multidigit ifadesinin 8 veya 9 olup olmadığını (gibi `\80` veya `\91`), ifade bir sabit değer yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-122">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>

- <span data-ttu-id="ac10e-123">Gelen ifadeleri `\10` ve daha fazla bigli varsa o sayı; Aksi takdirde karşılık gelen bir yeniden başvuru kabul, bunlar sekizlik kodları yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-123">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>

- <span data-ttu-id="ac10e-124">Normal bir ifade tanımsız grup numarası bir yeniden başvuru içeriyorsa, bir ayrıştırma hatası oluşur ve normal ifade motoru oluşturur bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="ac10e-124">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="ac10e-125">Belirsizliği bir sorun olması durumunda, kullanabileceğiniz `\k<` *adı* `>` anlaşılır ve sekizli karakter kodlarıyla kafanız olamaz, gösterimi.</span><span class="sxs-lookup"><span data-stu-id="ac10e-125">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="ac10e-126">Benzer şekilde, onaltılı gibi kodları `\xdd` anlaşılır ve geribaşvurular ile karıştırılır olamaz.</span><span class="sxs-lookup"><span data-stu-id="ac10e-126">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>

<span data-ttu-id="ac10e-127">Aşağıdaki örnek bir dizedeki yinelenen sözcük karakterlerini bulur.</span><span class="sxs-lookup"><span data-stu-id="ac10e-127">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="ac10e-128">Bir normal ifade tanımlar `(\w)\1`, aşağıdaki öğelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ac10e-128">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>

|<span data-ttu-id="ac10e-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac10e-129">Element</span></span>|<span data-ttu-id="ac10e-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac10e-130">Description</span></span>|
|-------------|-----------------|
|`(\w)`|<span data-ttu-id="ac10e-131">Bir sözcük karakteri Eşleştir ve ilk yakalama gruba atayın.</span><span class="sxs-lookup"><span data-stu-id="ac10e-131">Match a word character and assign it to the first capturing group.</span></span>|
|`\1`|<span data-ttu-id="ac10e-132">İlk yakalama grubunun değeri ile aynıdır sonraki karakterle eşleş.</span><span class="sxs-lookup"><span data-stu-id="ac10e-132">Match the next character that is the same as the value of the first capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a><span data-ttu-id="ac10e-133">Adlandırılmış yeniden başvurular</span><span class="sxs-lookup"><span data-stu-id="ac10e-133">Named Backreferences</span></span>

<span data-ttu-id="ac10e-134">Adlandırılmış bir yeniden başvuru, aşağıdaki söz dizimini kullanarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="ac10e-134">A named backreference is defined by using the following syntax:</span></span>

<span data-ttu-id="ac10e-135">`\k<` *Adı* `>`</span><span class="sxs-lookup"><span data-stu-id="ac10e-135">`\k<` *name* `>`</span></span>

<span data-ttu-id="ac10e-136">veya:</span><span class="sxs-lookup"><span data-stu-id="ac10e-136">or:</span></span>

<span data-ttu-id="ac10e-137">`\k'` *Adı* `'`</span><span class="sxs-lookup"><span data-stu-id="ac10e-137">`\k'` *name* `'`</span></span>

<span data-ttu-id="ac10e-138">Burada *adı* normal ifade deseninde tanımlanan bir yakalama grubunun adıdır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-138">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="ac10e-139">Varsa *adı* normal ifade deseninde tanımlı değil, bir ayrıştırma hatasını ortaya çıkar ve normal ifade motoru oluşturur bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="ac10e-139">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="ac10e-140">Aşağıdaki örnek bir dizedeki yinelenen sözcük karakterlerini bulur.</span><span class="sxs-lookup"><span data-stu-id="ac10e-140">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="ac10e-141">Bir normal ifade tanımlar `(?<char>\w)\k<char>`, aşağıdaki öğelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ac10e-141">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>

|<span data-ttu-id="ac10e-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac10e-142">Element</span></span>|<span data-ttu-id="ac10e-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac10e-143">Description</span></span>|
|-------------|-----------------|
|`(?<char>\w)`|<span data-ttu-id="ac10e-144">Bir sözcük karakteri Eşleştir ve adlandırılmış bir tutma grubu atamak `char`.</span><span class="sxs-lookup"><span data-stu-id="ac10e-144">Match a word character and assign it to a capturing group named `char`.</span></span>|
|`\k<char>`|<span data-ttu-id="ac10e-145">Değerini aynıdır sonraki karakteri eşleştirmek `char` yakalama grubu.</span><span class="sxs-lookup"><span data-stu-id="ac10e-145">Match the next character that is the same as the value of the `char` capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a><span data-ttu-id="ac10e-146">Adlandırılmış sayısal yeniden başvurular</span><span class="sxs-lookup"><span data-stu-id="ac10e-146">Named numeric backreferences</span></span>

<span data-ttu-id="ac10e-147">Adlandırılmış bir yeniden başvuru ile içinde `\k`, *adı* bir sayının dize gösterimini de olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac10e-147">In a named backreference with `\k`, *name* can also be the string representation of a number.</span></span> <span data-ttu-id="ac10e-148">Örneğin, aşağıdaki örnekte normal ifadeyi kullanan `(?<2>\w)\k<2>` yinelenen sözcük karakterlerini bir dizeyi bulmak için.</span><span class="sxs-lookup"><span data-stu-id="ac10e-148">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span> <span data-ttu-id="ac10e-149">Bu durumda, örnek açıkça "2" adında bir yakalama grubunu tanımlar ve geribaşvuru gelenlere "2" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-149">In this case, the example defines a capturing group that is explicitly named "2", and the backreference is correspondingly named "2".</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

<span data-ttu-id="ac10e-150">Varsa *adı* bir sayının dize gösterimini olduğundan ve hiçbir yakalama grubu bu ada sahip `\k<` *adı* `>` geribaşvuru aynı `\`  *sayı*burada *numarası* yakalama sıralı konumudur.</span><span class="sxs-lookup"><span data-stu-id="ac10e-150">If *name* is the string representation of a number, and no capturing group has that name, `\k<`*name*`>` is the same as the backreference `\`*number*, where *number* is the ordinal position of the capture.</span></span> <span data-ttu-id="ac10e-151">Aşağıdaki örnekte adlı tek bir yakalama grubu yoktur `char`.</span><span class="sxs-lookup"><span data-stu-id="ac10e-151">In the following example, there is a single capturing group named `char`.</span></span> <span data-ttu-id="ac10e-152">Yeniden başvuru yapısı olarak başvurur `\k<1>`.</span><span class="sxs-lookup"><span data-stu-id="ac10e-152">The backreference construct refers to it as `\k<1>`.</span></span> <span data-ttu-id="ac10e-153">Örnekte gösterildiği çağrısı çıktısı olarak <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> çünkü başarılı `char` ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="ac10e-153">As the output from the example shows, the call to the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> succeeds because `char` is the first capturing group.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

<span data-ttu-id="ac10e-154">Ancak, varsa *adı* bir sayının dize gösterimini olduğunu ve konumu sayısal bir ada, normal ifade ayrıştırıcısı açıkça atandığını yakalama grubundaki sıralı konumuna göre yakalama grubu tanımlanamıyor .</span><span class="sxs-lookup"><span data-stu-id="ac10e-154">However, if *name* is the string representation of a number and the capturing group in that position has been explicitly assigned a numeric name, the regular expression parser cannot identify the capturing group by its ordinal position.</span></span> <span data-ttu-id="ac10e-155">Bunun yerine, oluşturur bir <xref:System.ArgumentException>. Aşağıdaki örnekte yalnızca yakalama grubu "2" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-155">Instead, it throws an <xref:System.ArgumentException>.The only capturing group in the following example is named "2".</span></span> <span data-ttu-id="ac10e-156">Çünkü `\k` yapısı "1" adlı bir yeniden başvuru tanımlamak için kullanıldığında, normal ifade ayrıştırıcısı ilk yakalama grubuyla belirleyemiyor ve bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac10e-156">Because the `\k` construct is used to define a backreference named "1", the regular expression parser is unable to identify the first capturing group and throws an exception.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a><span data-ttu-id="ac10e-157">Hangi Geribaşvurular eşleştir</span><span class="sxs-lookup"><span data-stu-id="ac10e-157">What Backreferences Match</span></span>

<span data-ttu-id="ac10e-158">Bir yeniden başvuru en son (en hemen eşleştirirken sola, tanım soldan sağa) bir grup tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac10e-158">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="ac10e-159">Birden çok yakalayan bir grup yapar, bir yeniden başvuru için en son yakalama ifade eder.</span><span class="sxs-lookup"><span data-stu-id="ac10e-159">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>

<span data-ttu-id="ac10e-160">Aşağıdaki örnek, bir normal ifade deseni içerir `(?<1>a)(?<1>\1b)*`, adlandırılmış Grup \1 yeniden tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac10e-160">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="ac10e-161">Aşağıdaki tabloda her normal ifade deseninde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-161">The following table describes each pattern in the regular expression.</span></span>

|<span data-ttu-id="ac10e-162">Desen</span><span class="sxs-lookup"><span data-stu-id="ac10e-162">Pattern</span></span>|<span data-ttu-id="ac10e-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac10e-163">Description</span></span>|
|-------------|-----------------|
|`(?<1>a)`|<span data-ttu-id="ac10e-164">Bir karakterle Eşleştir "a" ve yakalama grubu sonucu adlı Ata `1`.</span><span class="sxs-lookup"><span data-stu-id="ac10e-164">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|
|`(?<1>\1b)*`|<span data-ttu-id="ac10e-165">Adlı grubu sıfır veya daha çok tekrarı ile eşleştir `1` yanı sıra bir "b" ve ata adlı yakalama grubudur sonucu `1`.</span><span class="sxs-lookup"><span data-stu-id="ac10e-165">Match zero or more occurrences of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

<span data-ttu-id="ac10e-166">Normal ifade giriş dizesini ("aababb") ile karşılaştırmak, normal ifade altyapısı aşağıdaki işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="ac10e-166">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>

1. <span data-ttu-id="ac10e-167">Dize başlangıcında başlar ve başarıyla eşleşen with ifadesi "a" `(?<1>a)`.</span><span class="sxs-lookup"><span data-stu-id="ac10e-167">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="ac10e-168">Değerini `1` grubudur artık "a".</span><span class="sxs-lookup"><span data-stu-id="ac10e-168">The value of the `1` group is now "a".</span></span>

2. <span data-ttu-id="ac10e-169">İkinci karakter ilerler ve başarıyla dize "ab" ifadesi ile eşleşen `\1b`, veya "ab".</span><span class="sxs-lookup"><span data-stu-id="ac10e-169">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="ac10e-170">Ardından, "ab" için sonuç atar `\1`.</span><span class="sxs-lookup"><span data-stu-id="ac10e-170">It then assigns the result, "ab" to `\1`.</span></span>

3. <span data-ttu-id="ac10e-171">Bu dördüncü karaktere ilerletir.</span><span class="sxs-lookup"><span data-stu-id="ac10e-171">It advances to the fourth character.</span></span> <span data-ttu-id="ac10e-172">İfade `(?<1>\1b)*` olarak eşleşen sıfır veya birden fazla kez şekilde başarıyla eşleşecek bir dize ifadesiyle, "abb" `\1b`.</span><span class="sxs-lookup"><span data-stu-id="ac10e-172">The expression `(?<1>\1b)*` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="ac10e-173">Sonuç, "abb" geri atar `\1`.</span><span class="sxs-lookup"><span data-stu-id="ac10e-173">It assigns the result, "abb", back to `\1`.</span></span>

<span data-ttu-id="ac10e-174">Bu örnekte, `*` döngü bir miktar belirleyiciyi--olan normal ifade motoru tanımlar deseni eşleşemez kadar sürekli olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ac10e-174">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="ac10e-175">Döngü miktar belirleyiciler grup tanımlarını işaretini kaldırmayın.</span><span class="sxs-lookup"><span data-stu-id="ac10e-175">Looping quantifiers do not clear group definitions.</span></span>

<span data-ttu-id="ac10e-176">Bir grubu herhangi bir alt dize yakalanan değil, bu gruba bir yeniden başvuru tanımlı değildir ve ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="ac10e-176">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="ac10e-177">Bu normal ifade deseni tarafından gösterilen `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, hangi şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="ac10e-177">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>

|<span data-ttu-id="ac10e-178">Desen</span><span class="sxs-lookup"><span data-stu-id="ac10e-178">Pattern</span></span>|<span data-ttu-id="ac10e-179">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac10e-179">Description</span></span>|
|-------------|-----------------|
|`\b`|<span data-ttu-id="ac10e-180">Bir sözcük sınırında eşleşmeye başla.</span><span class="sxs-lookup"><span data-stu-id="ac10e-180">Begin the match on a word boundary.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="ac10e-181">İki büyük harfler eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="ac10e-181">Match two uppercase letters.</span></span> <span data-ttu-id="ac10e-182">Bu ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="ac10e-182">This is the first capturing group.</span></span>|
|`(\d{2})?`|<span data-ttu-id="ac10e-183">İki ondalık basamak sıfır veya bir oluşumunu eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="ac10e-183">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="ac10e-184">Bu ikinci yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="ac10e-184">This is the second capturing group.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="ac10e-185">İki büyük harfler eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="ac10e-185">Match two uppercase letters.</span></span> <span data-ttu-id="ac10e-186">Bu, üçüncü yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="ac10e-186">This is the third capturing group.</span></span>|
|`\b`|<span data-ttu-id="ac10e-187">Eşleşme bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="ac10e-187">End the match on a word boundary.</span></span>|

<span data-ttu-id="ac10e-188">İkinci yakalama grubu tarafından tanımlanan iki ondalık basamak mevcut olmasa bile bir Giriş dizesinin bu normal ifade eşleşebilir.</span><span class="sxs-lookup"><span data-stu-id="ac10e-188">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="ac10e-189">Aşağıdaki örnek, eşleşmenin başarılı olsa bile başarılı iki yakalama grupları arasında boş bir yakalama grubu bulunamazsa olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac10e-189">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="ac10e-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac10e-190">See also</span></span>

- [<span data-ttu-id="ac10e-191">Normal İfade Dili - Hızlı Başvuru</span><span class="sxs-lookup"><span data-stu-id="ac10e-191">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
