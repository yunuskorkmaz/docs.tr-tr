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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 11df25617a618cdc835ca6555c671a187ce09f8d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991653"
---
# <a name="backreference-constructs-in-regular-expressions"></a>Normal İfadelerdeki Yeniden Başvuru Yapıları

Geri başvurular, bir dize içinde yinelenen bir karakter veya alt dizenin tanımlanması için kullanışlı bir yol sağlar. Örneğin, giriş dizesi rastgele bir alt dizenin birden çok oluşumunu içeriyorsa, ilk oluşumu bir yakalama grubuyla eşleştirebilir ve sonra alt dizenin sonraki tekrarlamalarını eşleştirmek için bir geri başvuru kullanabilirsiniz.

> [!NOTE]
> Değiştirme dizelerindeki adlandırılmış ve Numaralandırılmış yakalama gruplarına başvurmak için ayrı bir sözdizimi kullanılır. Daha fazla bilgi için bkz. [Değişimler](substitutions-in-regular-expressions.md).

.NET, numaralandırılmış ve adlandırılmış yakalama gruplarına başvuracak ayrı dil öğelerini tanımlar. Grupları yakalama hakkında daha fazla bilgi için bkz. [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

## <a name="numbered-backreferences"></a>Numaralandırılmış geri başvurular

Numaralandırılmış geri başvuru, aşağıdaki sözdizimini kullanır:

`\`*sayı*

Burada *sayı* , normal ifadede yakalama grubunun sıralı konumudur. Örneğin, `\4` dördüncü yakalama grubunun içeriğiyle eşleşir. *Sayı* normal ifade modelinde tanımlanmamışsa, bir ayrıştırma hatası oluşur ve normal ifade altyapısı bir <xref:System.ArgumentException>oluşturur. Örneğin, ifadedeki ilk ve tek `\b(\w+)\s\1` yakalama grubu olduğundan `(\w+)` , normal ifade geçerli olur. Öte yandan, `\b(\w+)\s\2` geçersizdir ve numaralandırılmış `\2`bir yakalama grubu bulunmadığından bir bağımsız değişken özel durumu oluşturur. Ayrıca, varsa *numarası* sıralı belirli bir konumda bir yakalama grubunu tanımlar, yakalama grubu sayısal verildiğine göre ancak sıra konumuna farklı bir ad, normal ifade ayrıştırıcısı bir deoluşturur<xref:System.ArgumentException>.

Sekizlik kaçış kodları ( `\16`gibi) ve aynı gösterimi kullanan *numara* geri başvuruları arasındaki belirsizlik ' i `\`unutmayın. Bu belirsizlik aşağıdaki şekilde çözümlenir:

- `\1` Aracılığıyla`\9` yapılan ifadeler her zaman geri başvuru olarak yorumlanır ve sekizlik kodlar değildir.

- Çok basamaklı bir ifadenin ilk rakamı 8 veya 9 ( `\80` veya `\91`gibi) ise, ifade değişmez değer olarak yorumlanır.

- `\10` Ve üzeri ifadeler, bu numaraya karşılık gelen bir geri başvuru varsa, geri başvuru olarak kabul edilir; Aksi takdirde, sekizlik kodlar olarak yorumlanır.

- Normal bir ifade tanımsız bir grup numarasına geri başvuru içeriyorsa, bir ayrıştırma hatası oluşur ve normal ifade altyapısı bir <xref:System.ArgumentException>oluşturur.

Belirsizlik bir sorun ise, belirsiz olan ve sekizli karakter kodlarıyla `\k<`karıştırılmamalıdır olan *ad* `>` gösterimini kullanabilirsiniz. Benzer şekilde, gibi onaltılık kodlar `\xdd` ise ve geri başvurularıyla karıştırılmamalıdır.

Aşağıdaki örnek bir dizedeki iki katına oluşan sözcük karakterlerini bulur. Aşağıdaki öğelerden oluşan bir normal ifadeyi `(\w)\1`tanımlar.

|Öğe|Açıklama|
|-------------|-----------------|
|`(\w)`|Bir sözcük karakterini eşleştirin ve ilk yakalama grubuna atayın.|
|`\1`|İlk yakalama grubunun değeriyle aynı olan bir sonraki karakterle eşleştirin.|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a>Adlandırılmış geri başvurular

Adlandırılmış bir geri başvuru, aşağıdaki sözdizimi kullanılarak tanımlanır:

`\k<`*ad*`>`

veya:

`\k'`*ad*`'`

Burada *ad* , normal ifade düzeninde tanımlanan yakalama grubunun adıdır. *Ad* normal ifade modelinde tanımlanmamışsa, bir ayrıştırma hatası oluşur ve normal ifade altyapısı bir <xref:System.ArgumentException>oluşturur.

Aşağıdaki örnek bir dizedeki iki katına oluşan sözcük karakterlerini bulur. Aşağıdaki öğelerden oluşan bir normal ifadeyi `(?<char>\w)\k<char>`tanımlar.

|Öğe|Açıklama|
|-------------|-----------------|
|`(?<char>\w)`|Bir sözcük karakterini eşleştirin ve adlı `char`bir yakalama grubuna atayın.|
|`\k<char>`|`char` Yakalama grubu değeriyle aynı olan bir sonraki karakterle eşleştirin.|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a>Adlandırılmış sayısal geribaşvurular

Adlı adlandırılmış bir geri başvuru `\k`içinde, *ad* bir sayının dize temsili de olabilir. Örneğin, aşağıdaki örnek, bir dizedeki iki katına oluşan `(?<2>\w)\k<2>` sözcük karakterlerini bulmak için normal ifadeyi kullanır. Bu durumda, örnek "2" olarak adlandırılan bir yakalama grubunu tanımlar ve geri başvuru "2" olarak adlandırılmıştır.

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

*Ad* bir sayının dize gösterimiyse ve yakalama grubu `\k<`bu ada sahip değilse, *ad* `>` geri başvuru `\`numarasıyla aynıdır; burada *sayı* , lamanız. Aşağıdaki örnekte adlı `char`tek bir yakalama grubu vardır. Geribaşvuru yapısı, bu öğeyi olarak `\k<1>`ifade eder. Örneğin çıkışının gösterdiği gibi, ilk yakalama grubu olduğundan <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> `char` , başarılı olma çağrısı.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

Ancak, *ad* bir sayının dize gösterimiyse ve bu konumdaki yakalama grubuna açıkça sayısal bir ad atanmışsa, normal ifade ayrıştırıcısı yakalama grubunu sıra konumuna göre tanımlayamıyor. Bunun yerine, bir <xref:System.ArgumentException>oluşturur. Aşağıdaki örnekteki tek yakalama grubu "2" olarak adlandırılmıştır. `\k` Yapı, "1" adlı bir geri başvuru tanımlamak için kullanıldığından, normal ifade ayrıştırıcısı ilk yakalama grubunu tanımlayamıyor ve bir özel durum oluşturuyor.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a>Hangi geribaşvuruların eşleşmesi

Geri başvuru, bir grubun en son tanımına (soldan sağa eşleştirilirken en yakın bir tanım) başvurur. Bir grup birden çok yakalama yaptığında, geri başvuru en son yakalamayı ifade eder.

Aşağıdaki örnek, \ 1 adlandırılmış grubunu tekrar tanımlayan `(?<1>a)(?<1>\1b)*`bir normal ifade deseninin yer aldığı bir örnektir. Aşağıdaki tabloda, Normal ifadedeki her bir model açıklanmaktadır.

|Desen|Açıklama|
|-------------|-----------------|
|`(?<1>a)`|"A" karakteriyle eşleşir ve sonucu adlı `1`yakalama grubuna atayın.|
|`(?<1>\1b)*`|"B" ile birlikte adlı `1` grubun sıfır veya daha fazla tekrarlanmasını eşleştirin ve sonucu adlı `1`yakalama grubuna atayın.|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

Normal ifadeyi giriş dizesiyle ("aababb") karşılaştırırken, normal ifade altyapısı aşağıdaki işlemleri gerçekleştirir:

1. Bu, dizenin başlangıcında başlar ve ifadesiyle `(?<1>a)`"a" ile başarılı bir şekilde eşleşir. `1` Grubun değeri artık "a" dır.

2. İkinci karaktere ilerletir ve "AB" dizesiyle, veya "AB" ifadesiyle `\1b`başarıyla eşleşir. Ardından "AB" `\1`sonucunu atar.

3. Dördüncü karaktere ilerletir. İfade `(?<1>\1b)*` sıfır veya daha fazla kez eşleştirilecek, bu nedenle "abb" dizesiyle birlikte ifadesiyle `\1b`başarıyla eşleşiyor. "Abb" sonucunu, öğesine `\1`geri atar.

Bu örnekte, `*` bir döngü nicelik belirteci, normal ifade altyapısı tanımladığı Düzenle eşleşene kadar sürekli değerlendirilir. Döngü nicelik belirteçleri grup tanımlarını temizlemez.

Bir grupta herhangi bir alt dize yakalanmadıysa, bu gruba yönelik bir geri başvuru tanımsızdır ve hiçbir şekilde eşleşmez. Bu, aşağıdaki gibi tanımlanan normal ifade deseninin `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`gösterilmektedir:

|Desen|Açıklama|
|-------------|-----------------|
|`\b`|Eşleşmeyi bir sözcük sınırında başlatın.|
|`(\p{Lu}{2})`|İki büyük harfi eşleştirin. Bu ilk yakalama grubudur.|
|`(\d{2})?`|İki ondalık basamağın sıfır veya bir oluşumunu eşleştirin. Bu ikinci yakalama grubudur.|
|`(\p{Lu}{2})`|İki büyük harfi eşleştirin. Bu, üçüncü yakalama grubudur.|
|`\b`|Eşleşmeyi bir sözcük sınırında sonlandır.|

İkinci yakalama grubu tarafından tanımlanan iki ondalık basamak mevcut olmasa bile, bir giriş dizesi bu normal ifadeyle eşleşir. Aşağıdaki örnekte, eşleşme başarılı olsa da, iki başarılı yakalama grubu arasında boş bir yakalama grubu bulunur.

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
