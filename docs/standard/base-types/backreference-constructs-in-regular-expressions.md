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
# <a name="backreference-constructs-in-regular-expressions"></a>Normal İfadelerdeki Yeniden Başvuru Yapıları

Geri göndermeler, yinelenen bir karakteri veya bir dize içindeki alt dizeyi tanımlamak için kullanışlı bir yol sağlar. Örneğin, giriş dizesi rasgele bir alt dize birden çok olay içeriyorsa, bir yakalama grubu ile ilk oluşumu eşleşebilir ve sonra substring sonraki oluşumları eşleştirmek için bir backreference kullanabilirsiniz.

> [!NOTE]
> Değiştirme dizelerinde adlandırılmış ve numaralandırılmış yakalama gruplarını ifade etmek için ayrı bir sözdizimi kullanılır. Daha fazla bilgi için [Bkz.](substitutions-in-regular-expressions.md)

.NET, numaralandırılmış ve adlandırılmış yakalama gruplarına başvurmak için ayrı dil öğeleri tanımlar. Grupları yakalama hakkında daha fazla bilgi için [yapıyı gruplandırma'ya](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)bakın.

## <a name="numbered-backreferences"></a>Numaralı Referanslar

Numaralı bir geri başvuru aşağıdaki sözdizimini kullanır:

`\` *number*

*numaranın* normal ifadedeki yakalama grubunun ordinal konumu olduğu yer. Örneğin, `\4` dördüncü yakalama grubunun içeriğiyle eşleşir. Normal ifade deseninde *sayı* tanımlanmamışsa, ayrıştırma hatası oluşur ve <xref:System.ArgumentException>normal ifade altyapısı . Örneğin, ifadedeki `\b(\w+)\s\1` ilk ve `(\w+)` tek yakalama grubu olduğundan, normal ifade geçerlidir. Diğer taraftan, `\b(\w+)\s\2` geçersizdir ve numaralandırılmış `\2`yakalama grubu olmadığından bağımsız değişken özel durumu atar. Buna ek olarak, *sayı* belirli bir ordinal konumda bir yakalama grubu tanımlar, ancak bu yakalama grubu kendi ordinal konumu farklı sayısal <xref:System.ArgumentException>bir ad atanmış sayılsa, normal ifade parer de bir .

Sekizli kaçış kodları (örneğin) `\16`ve `\`aynı gösterimi kullanan *sayı* geri başvuruları arasındaki belirsizliğe dikkat edin. Bu belirsizlik aşağıdaki gibi çözülür:

- Üzerinden ifadeler `\1` `\9` her zaman backreferences olarak yorumlanır, değil, sekizkodlar olarak.

- Çok basamaklı bir ifadenin ilk basamağı 8 `\80` `\91`veya 9 ise (gibi), ifade tam olarak yorumlanır.

- Bu sayıya karşılık gelen bir geri başvuru varsa, gelen `\10` ve daha büyük ifadeler geri başvuru olarak kabul edilir; aksi takdirde, sekizkodlu olarak yorumlanır.

- Normal bir ifade tanımlanmamış bir grup numarasına geri gönderme içeriyorsa, ayrıştırma hatası <xref:System.ArgumentException>oluşur ve normal ifade altyapısı .

Belirsizlik bir sorunsa, açık olan `\k<`ve sekizli karakter kodlarıyla karıştırılamayan *ad* `>` gösterimini kullanabilirsiniz. Benzer şekilde, hexadecimal `\xdd` kodlar gibi kesin ve backreferences ile karıştırılmamalıdır.

Aşağıdaki örnekte, bir dizedeki iki katına çıkan sözcük karakterleri bulur. Aşağıdaki öğelerden oluşan `(\w)\1`düzenli bir ifade tanımlar.

|Öğe|Açıklama|
|-------------|-----------------|
|`(\w)`|Bir sözcük karakterini eşleştirin ve ilk yakalama grubuna atayın.|
|`\1`|İlk yakalama grubunun değeriyle aynı olan bir sonraki karakteri eşleştirin.|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a>İsimli Backreferences

Adlandırılmış bir geri başvuru aşağıdaki sözdizimi kullanılarak tanımlanır:

`\k<`*isim*`>`

veya:

`\k'`*isim*`'`

*adı* normal ifade deseni tanımlanan bir yakalama grubunun adıdır. *Ad* normal ifade deseninde tanımlanmamışsa, ayrıştırma hatası oluşur ve <xref:System.ArgumentException>normal ifade altyapısı bir .

Aşağıdaki örnekte, bir dizedeki iki katına çıkan sözcük karakterleri bulur. Aşağıdaki öğelerden oluşan `(?<char>\w)\k<char>`düzenli bir ifade tanımlar.

|Öğe|Açıklama|
|-------------|-----------------|
|`(?<char>\w)`|Bir sözcük karakterini eşleştirin ve onu `char`bir yakalama grubuna atayın.|
|`\k<char>`|`char` Yakalama grubunun değeriyle aynı olan bir sonraki karakteri eşleştirin.|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a>Sayısal geri referanslar adlı

Adlandırılmış bir geri `\k`başvuruda , *adı* da bir sayının dize gösterimi olabilir. Örneğin, aşağıdaki örnek, bir `(?<2>\w)\k<2>` dizede iki katına çıkan sözcük karakterlerini bulmak için normal ifadeyi kullanır. Bu durumda, örnek açıkça "2" adlı bir yakalama grubu tanımlar ve geri başvuru buna karşılık "2" olarak adlandırılır.

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

*Ad* bir sayının dize gösterimiyse ve hiçbir yakalama `\k<`grubu bu ada `\`sahipdeğilse, *ad,* `>` *numaranın* yakalamanın ordinal konumu olduğu backreference *numarasıyla*aynıdır. Aşağıdaki örnekte, adlı `char`tek bir yakalama grubu vardır. Geri başvuru yapısı ona `\k<1>`. Örnekteki çıktının gösterdiği gibi, ilk <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yakalama `char` grubu olduğu için başarılı olan çağrı.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

Ancak, *ad* bir sayının dize gösterimi yse ve bu konumdaki yakalama grubuna açıkça sayısal bir ad atanmışsa, normal ifade parlayıcısı yakalama grubunu kendi ordinal konumuna göre tanımlayamaz. Bunun yerine, bir <xref:System.ArgumentException>atar . Aşağıdaki örnekteki tek yakalama grubu "2" olarak adlandırılır. `\k` Yapı "1" adlı bir geri başvuru tanımlamak için kullanıldığından, normal ifade parer ilk yakalama grubunu tanımlayamaz ve bir özel durum atar.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a>Backreferences Match Ne

Bir geri başvuru, bir grubun en son tanımına (soldan sağa eşleşirken en çok sola doğru tanım) başvurur. Bir grup birden çok yakalama yaptığında, bir geri başvuru en son yakalama anlamına gelir.

Aşağıdaki örnek, `(?<1>a)(?<1>\1b)*`\1 adlı grubu yeniden tanımlayan normal bir ifade deseni içerir. Aşağıdaki tabloda normal ifadedeki her desen açıklanmaktadır.

|Desen|Açıklama|
|-------------|-----------------|
|`(?<1>a)`|"a" karakterini eşleştirin ve sonucu ' yu `1`adlandırılmış yakalama grubuna atayın.|
|`(?<1>\1b)*`|"b" ile birlikte adlandırılan `1` grubun sıfır veya daha fazla oluşumlarını eşleştirin ve `1`sonucu ' yu ' adlı yakalama grubuna atayın.|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

Normal ifadeyi giriş dizesi ("aababb") ile karşılaştırırken, normal ifade altyapısı aşağıdaki işlemleri gerçekleştirir:

1. Bu dize başında başlar ve başarıyla ifade `(?<1>a)`ile "a" eşleşir. `1` Grubun değeri artık "a"dır.

2. İkinci karaktere ilerler ve "ab" dizesini `\1b`"ab" ifadesi veya "ab" ile başarıyla eşler. Daha sonra sonucu atar, "ab" için `\1`.

3. Dördüncü karaktere doğru ilerler. İfade `(?<1>\1b)*` sıfır veya daha fazla kez eşleşecek, bu nedenle başarıyla "abb" `\1b`ifadesi ile dize eşleşir. Bu sonuç atar, "abb", `\1`geri .

Bu örnekte, `*` bir döngü niceleyicisidir -- normal ifade altyapısı tanımladığı desenle eşleştirene kadar tekrar tekrar değerlendirilir. Döngü niceleyicileri grup tanımlarını temizlemez.

Bir grup herhangi bir alt dize yakalamadıysa, bu gruba bir geri gönderme tanımsızdır ve hiçbir zaman eşleşmez. Bu aşağıdaki gibi tanımlanan `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`normal ifade deseni ile gösterilmiştir:

|Desen|Açıklama|
|-------------|-----------------|
|`\b`|Eşleşmeyi sözcük sınırında başlatın.|
|`(\p{Lu}{2})`|İki büyük harfle eşleştirin. Bu ilk yakalama grubudur.|
|`(\d{2})?`|İki ondalık basamaktan sıfır veya bir oluşum eşleştirin. Bu ikinci yakalama grubudur.|
|`(\p{Lu}{2})`|İki büyük harfle eşleştirin. Bu, üçüncü yakalama grubudur.|
|`\b`|Eşleşmeyi sözcük sınırında sonla.|

İkinci yakalama grubu tarafından tanımlanan iki ondalık basamak mevcut olmasa bile, bir giriş dizesi bu normal ifadeyle eşleşebilir. Aşağıdaki örnek, eşleşme başarılı olsa bile, iki başarılı yakalama grubu arasında boş bir yakalama grubu bulunduğunu gösterir.

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
