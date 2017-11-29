---
title: "Normal İfadelerdeki Yeniden Başvuru Yapıları"
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
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a884e70f542c2ed7ff63e39cb7eadedf0ef7b4d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="e8a5f-102">Normal İfadelerdeki Yeniden Başvuru Yapıları</span><span class="sxs-lookup"><span data-stu-id="e8a5f-102">Backreference Constructs in Regular Expressions</span></span>
<span data-ttu-id="e8a5f-103">Yeniden başvurular yinelenen karakter veya bir dize içindeki alt dizenin tanımlamak için kolay bir yol sağlamak.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-103">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="e8a5f-104">Örneğin, giriş dizesi birden çok tekrarı rastgele bir alt dizeyi içeriyorsa, birinci yakalama grubu ile eşleşen ve ardından sonraki oluşumlarını alt dizeyi eşleştirmek için bir yeniden başvuru kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-104">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8a5f-105">Ayrı bir söz dizimi, adlandırılmış ve numaralı değiştirme dizelerini gruplarında yakalama başvurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-105">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="e8a5f-106">Daha fazla bilgi için bkz: [değişimler](substitutions-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e8a5f-106">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="e8a5f-107">.NET numaralı ve adlandırılmış yakalama gruplarına başvurmak için ayrı dil öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-107">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="e8a5f-108">Grupları yakalama hakkında daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e8a5f-108">For more information about capturing groups, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>  
  
## <a name="numbered-backreferences"></a><span data-ttu-id="e8a5f-109">Numaralı yeniden başvurular</span><span class="sxs-lookup"><span data-stu-id="e8a5f-109">Numbered Backreferences</span></span>  
 <span data-ttu-id="e8a5f-110">Numaralı yeniden başvuru aşağıdaki söz dizimini kullanır:</span><span class="sxs-lookup"><span data-stu-id="e8a5f-110">A numbered backreference uses the following syntax:</span></span>  
  
 <span data-ttu-id="e8a5f-111">`\`*numarası*</span><span class="sxs-lookup"><span data-stu-id="e8a5f-111">`\` *number*</span></span>  
  
 <span data-ttu-id="e8a5f-112">Burada *numarası* sıralı yakalama grubunu normal ifadede konumudur.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-112">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="e8a5f-113">Örneğin, `\4` dördüncü yakalama Grup içeriğini eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-113">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="e8a5f-114">Varsa *numarası* normal ifade deseni içinde tanımlı değil, bir ayrıştırma hatası ortaya çıkar ve normal ifade altyapısı oluşturur bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-114">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="e8a5f-115">Örneğin, normal ifade `\b(\w+)\s\1` geçerlidir, çünkü `(\w+)` ilk ve yalnızca ifade grubunda yakalıyor.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-115">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="e8a5f-116">Diğer taraftan, `\b(\w+)\s\2` geçersiz ve numaralı yakalama Grup olduğundan bir bağımsız değişken özel durum oluşturur `\2`.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-116">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span>  
  
 <span data-ttu-id="e8a5f-117">Sekizli çıkış kodları arasında bir belirsizliğe unutmayın (gibi `\16`) ve `\` *numarası* aynı gösterimini kullanın yeniden başvurular.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-117">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="e8a5f-118">Bu belirsizlik gibi çözümlendi:</span><span class="sxs-lookup"><span data-stu-id="e8a5f-118">This ambiguity is resolved as follows:</span></span>  
  
-   <span data-ttu-id="e8a5f-119">İfadeleri `\1` aracılığıyla `\9` her zaman sekizli kodları olarak değil de, yeniden başvurular olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-119">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>  
  
-   <span data-ttu-id="e8a5f-120">Multidigit ifadesinin ilk rakam 8 veya 9 olup olmadığını (gibi `\80` veya `\91`), bir hazır değer yorumlanan olarak ifade.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-120">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>  
  
-   <span data-ttu-id="e8a5f-121">Gelen ifadeleri `\10` ve büyük bu numara; Aksi takdirde karşılık gelen bir yeniden başvuru ise yeniden başvurular kabul, bunlar sekizli kodlar olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-121">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>  
  
-   <span data-ttu-id="e8a5f-122">Normal bir ifade tanımsız grup numarası yeniden başvuru içeriyorsa, bir ayrıştırma hatası ortaya çıkar ve normal ifade altyapısı oluşturur bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-122">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="e8a5f-123">Belirsizliği bir sorunsa, kullanabileceğiniz `\k<` *adı* `>` anlaşılır ve sekizli karakter kodlarıyla kafası olamaz gösterimi.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-123">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="e8a5f-124">Benzer şekilde, onaltılık gibi kodları `\xdd` anlaşılır ve yeniden başvurular ile kafası olamaz.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-124">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>  
  
 <span data-ttu-id="e8a5f-125">Aşağıdaki örnek, bir dize iki kat sözcük karakterlerini bulur.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-125">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="e8a5f-126">Normal bir ifade tanımlar `(\w)\1`, aşağıdaki öğelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-126">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="e8a5f-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="e8a5f-127">Element</span></span>|<span data-ttu-id="e8a5f-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8a5f-128">Description</span></span>|  
|-------------|-----------------|  
|`(\w)`|<span data-ttu-id="e8a5f-129">İlk yakalama grubuna atayın ve bir sözcük karakteriyle eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-129">Match a word character and assign it to the first capturing group.</span></span>|  
|`\1`|<span data-ttu-id="e8a5f-130">İlk yakalama grubunun değeri aynı sonraki karakteri eşleştirmek.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-130">Match the next character that is the same as the value of the first capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a><span data-ttu-id="e8a5f-131">Adlandırılmış yeniden başvurular</span><span class="sxs-lookup"><span data-stu-id="e8a5f-131">Named Backreferences</span></span>  
 <span data-ttu-id="e8a5f-132">Adlandırılmış yeniden başvuru, aşağıdaki sözdizimi kullanılarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="e8a5f-132">A named backreference is defined by using the following syntax:</span></span>  
  
 <span data-ttu-id="e8a5f-133">`\k<`*adı*`>`</span><span class="sxs-lookup"><span data-stu-id="e8a5f-133">`\k<` *name* `>`</span></span>  
  
 <span data-ttu-id="e8a5f-134">veya:</span><span class="sxs-lookup"><span data-stu-id="e8a5f-134">or:</span></span>  
  
 <span data-ttu-id="e8a5f-135">`\k'`*adı*`'`</span><span class="sxs-lookup"><span data-stu-id="e8a5f-135">`\k'` *name* `'`</span></span>  
  
 <span data-ttu-id="e8a5f-136">Burada *adı* normal ifade deseni içinde tanımlanan bir yakalama grubunu adıdır.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-136">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="e8a5f-137">Varsa *adı* normal ifade deseni içinde tanımlı değil, bir ayrıştırma hatası ortaya çıkar ve normal ifade altyapısı oluşturur bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-137">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="e8a5f-138">Aşağıdaki örnek, bir dize iki kat sözcük karakterlerini bulur.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-138">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="e8a5f-139">Normal bir ifade tanımlar `(?<char>\w)\k<char>`, aşağıdaki öğelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-139">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="e8a5f-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="e8a5f-140">Element</span></span>|<span data-ttu-id="e8a5f-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8a5f-141">Description</span></span>|  
|-------------|-----------------|  
|`(?<char>\w)`|<span data-ttu-id="e8a5f-142">Adlı bir yakalama grubuna atayın ve bir sözcük karakteriyle eşleşiyor `char`.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-142">Match a word character and assign it to a capturing group named `char`.</span></span>|  
|`\k<char>`|<span data-ttu-id="e8a5f-143">Değeri aynı sonraki karakteri eşleştirmek `char` Grup yakalama.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-143">Match the next character that is the same as the value of the `char` capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 <span data-ttu-id="e8a5f-144">Unutmayın *adı* bir sayı dize gösterimini de olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-144">Note that *name* can also be the string representation of a number.</span></span> <span data-ttu-id="e8a5f-145">Örneğin, aşağıdaki örnekte normal ifade kullanan `(?<2>\w)\k<2>` dizede iki kat sözcük karakterlerini bulmak için.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-145">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## <a name="what-backreferences-match"></a><span data-ttu-id="e8a5f-146">Hangi yeniden başvurular eşleşmiyor</span><span class="sxs-lookup"><span data-stu-id="e8a5f-146">What Backreferences Match</span></span>  
 <span data-ttu-id="e8a5f-147">Bir yeniden başvuru (eşleştirirken hemen en soldaki, tanımına soldan sağa) bir grubun en son tanım ifade eder.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-147">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="e8a5f-148">Birden çok yakalayan bir grup yapar, bir yeniden başvuru en son yakalama başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-148">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>  
  
 <span data-ttu-id="e8a5f-149">Aşağıdaki örnek, bir normal ifade deseni içerir `(?<1>a)(?<1>\1b)*`, Grup adlı \1 yeniden tanımlamaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-149">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="e8a5f-150">Aşağıdaki tabloda her düzeni normal ifadede açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-150">The following table describes each pattern in the regular expression.</span></span>  
  
|<span data-ttu-id="e8a5f-151">Desen</span><span class="sxs-lookup"><span data-stu-id="e8a5f-151">Pattern</span></span>|<span data-ttu-id="e8a5f-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8a5f-152">Description</span></span>|  
|-------------|-----------------|  
|`(?<1>a)`|<span data-ttu-id="e8a5f-153">Karakter eşleşmesi "a" ve yakalama grubunu sonucu adlı Ata `1`.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-153">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|  
|`(?<1>\1b)*`|<span data-ttu-id="e8a5f-154">Adlı Grup eşleşme 0 veya 1 oluşumunu `1` "b" ve ata adlı yakalama grubunu sonucu birlikte `1`.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-154">Match 0 or 1 occurrence of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 <span data-ttu-id="e8a5f-155">Normal ifade giriş dizesi ("aababb") ile karşılaştırarak normal ifade altyapısı aşağıdaki işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="e8a5f-155">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>  
  
1.  <span data-ttu-id="e8a5f-156">Dizenin başında başlar ve başarıyla eşleşen with ifadesi "a" `(?<1>a)`.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-156">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="e8a5f-157">Değeri `1` grubudur şimdi "a".</span><span class="sxs-lookup"><span data-stu-id="e8a5f-157">The value of the `1` group is now "a".</span></span>  
  
2.  <span data-ttu-id="e8a5f-158">İkinci karaktere ilerletir ve başarıyla with ifadesi "ab" dizesini eşleştirir `\1b`, veya "ab".</span><span class="sxs-lookup"><span data-stu-id="e8a5f-158">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="e8a5f-159">Ardından sonucu, "ab" için atar `\1`.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-159">It then assigns the result, "ab" to `\1`.</span></span>  
  
3.  <span data-ttu-id="e8a5f-160">Dördüncü karaktere ilerletir.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-160">It advances to the fourth character.</span></span> <span data-ttu-id="e8a5f-161">İfade `(?<1>\1b)` olmasını eşleşen sıfır veya birden fazla kez böylece başarıyla eşleşecek dizesi "abb" ifadesi ile `\1b`.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-161">The expression `(?<1>\1b)` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="e8a5f-162">Sonuç, "abb" başa atar `\1`.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-162">It assigns the result, "abb", back to `\1`.</span></span>  
  
 <span data-ttu-id="e8a5f-163">Bu örnekte, `*` döngü niceleyici--olan normal ifade altyapısı tanımladığı düzeni eşleşemez kadar sürekli olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-163">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="e8a5f-164">Döngü nicelik grup tanımlarını işaretini kaldırmayın.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-164">Looping quantifiers do not clear group definitions.</span></span>  
  
 <span data-ttu-id="e8a5f-165">Bir grup herhangi bir alt dize yakalandı değil, bu gruba yeniden başvuru tanımlı değil ve hiçbir zaman eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-165">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="e8a5f-166">Bu normal ifade deseni tarafından gösterilmiştir `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, hangi aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="e8a5f-166">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>  
  
|<span data-ttu-id="e8a5f-167">Desen</span><span class="sxs-lookup"><span data-stu-id="e8a5f-167">Pattern</span></span>|<span data-ttu-id="e8a5f-168">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8a5f-168">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="e8a5f-169">Word sınır eşleşmeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-169">Begin the match on a word boundary.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="e8a5f-170">İki büyük harf eşleşir.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-170">Match two uppercase letters.</span></span> <span data-ttu-id="e8a5f-171">Bu ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-171">This is the first capturing group.</span></span>|  
|`(\d{2})?`|<span data-ttu-id="e8a5f-172">İki ondalık basamak sıfır veya bir örneğini Bul.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-172">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="e8a5f-173">Bu ikinci yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-173">This is the second capturing group.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="e8a5f-174">İki büyük harf eşleşir.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-174">Match two uppercase letters.</span></span> <span data-ttu-id="e8a5f-175">Bu, üçüncü yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-175">This is the third capturing group.</span></span>|  
|`\b`|<span data-ttu-id="e8a5f-176">Son bir word sınırında eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-176">End the match on a word boundary.</span></span>|  
  
 <span data-ttu-id="e8a5f-177">İkinci yakalama grubu tarafından tanımlanan iki ondalık basamak mevcut değilse bile giriş dizesi bu normal ifadeyi eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-177">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="e8a5f-178">Aşağıdaki örnek, eşleştirmenin başarılı olsa bile, boş bir yakalama grubu iki başarılı yakalama grupları arasında bulunan gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-178">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e8a5f-179">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8a5f-179">See Also</span></span>  
 [<span data-ttu-id="e8a5f-180">Normal ifade dili - hızlı başvuru</span><span class="sxs-lookup"><span data-stu-id="e8a5f-180">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
