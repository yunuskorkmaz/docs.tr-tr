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
# <a name="backreference-constructs-in-regular-expressions"></a>Normal İfadelerdeki Yeniden Başvuru Yapıları

Geri başvurular, bir dize içinde yinelenen bir karakter veya alt dizenin tanımlanması için kullanışlı bir yol sağlar. Örneğin, giriş dizesi rastgele bir alt dizenin birden çok oluşumunu içeriyorsa, ilk oluşumu bir yakalama grubuyla eşleştirebilir ve sonra alt dizenin sonraki tekrarlamalarını eşleştirmek için bir geri başvuru kullanabilirsiniz.

> [!NOTE]
> Değiştirme dizelerindeki adlandırılmış ve Numaralandırılmış yakalama gruplarına başvurmak için ayrı bir sözdizimi kullanılır. Daha fazla bilgi için bkz. [alternatifler](substitutions-in-regular-expressions.md).

.NET, numaralandırılmış ve adlandırılmış yakalama gruplarına başvuracak ayrı dil öğelerini tanımlar. Grupları yakalama hakkında daha fazla bilgi için bkz. [gruplandırma yapıları](grouping-constructs-in-regular-expressions.md).

## <a name="numbered-backreferences"></a>Numaralandırılmış geri başvurular

Numaralandırılmış geri başvuru, aşağıdaki sözdizimini kullanır:

`\`*sayı*

Burada *sayı* , normal ifadede yakalama grubunun sıralı konumudur. Örneğin, `\4` dördüncü yakalama grubunun içeriğiyle eşleşir. *Sayı* normal ifade modelinde tanımlanmamışsa, bir ayrıştırma hatası oluşur ve normal ifade altyapısı bir oluşturur <xref:System.ArgumentException> . Örneğin, `\b(\w+)\s\1` `(\w+)` ifadedeki ilk ve tek yakalama grubu olduğundan, normal ifade geçerli olur. Öte yandan, `\b(\w+)\s\2` geçersizdir ve numaralandırılmış bir yakalama grubu bulunmadığından bir bağımsız değişken özel durumu oluşturur `\2` . Ayrıca, *sayı* belirli bir sıra konumunda bir yakalama grubu tanımlarsa, ancak bu yakalama grubuna sıra konumundan farklı bir sayısal ad atanmışsa, normal ifade ayrıştırıcısı da bir oluşturur <xref:System.ArgumentException> .

Sekizlik kaçış kodları (gibi `\16` ) ve `\` aynı gösterimi kullanan *numara* geri başvuruları arasındaki belirsizlik ' i unutmayın. Bu belirsizlik aşağıdaki şekilde çözümlenir:

- `\1`Aracılığıyla yapılan ifadeler `\9` her zaman geri başvuru olarak yorumlanır ve sekizlik kodlar değildir.

- Çok basamaklı bir ifadenin ilk rakamı 8 veya 9 ( `\80` veya gibi `\91` ) ise, ifade değişmez değer olarak yorumlanır.

- `\10`Ve üzeri ifadeler, bu numaraya karşılık gelen bir geri başvuru varsa, geri başvuru olarak kabul edilir; Aksi takdirde, sekizlik kodlar olarak yorumlanır.

- Normal bir ifade tanımsız bir grup numarasına geri başvuru içeriyorsa, bir ayrıştırma hatası oluşur ve normal ifade altyapısı bir oluşturur <xref:System.ArgumentException> .

Belirsizlik bir sorun ise, `\k<` *name* `>` belirsiz olan ve sekizli karakter kodlarıyla karıştırılmamalıdır olan ad gösterimini kullanabilirsiniz. Benzer şekilde, gibi onaltılık kodlar ise `\xdd` ve geri başvurularıyla karıştırılmamalıdır.

Aşağıdaki örnek bir dizedeki iki katına oluşan sözcük karakterlerini bulur. Aşağıdaki öğelerden oluşan bir normal ifadeyi tanımlar `(\w)\1` .

|Öğe|Description|
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

Burada *ad* , normal ifade düzeninde tanımlanan yakalama grubunun adıdır. *Ad* normal ifade modelinde tanımlanmamışsa, bir ayrıştırma hatası oluşur ve normal ifade altyapısı bir oluşturur <xref:System.ArgumentException> .

Aşağıdaki örnek bir dizedeki iki katına oluşan sözcük karakterlerini bulur. Aşağıdaki öğelerden oluşan bir normal ifadeyi tanımlar `(?<char>\w)\k<char>` .

|Öğe|Description|
|-------------|-----------------|
|`(?<char>\w)`|Bir sözcük karakterini eşleştirin ve adlı bir yakalama grubuna atayın `char` .|
|`\k<char>`|Yakalama grubu değeriyle aynı olan bir sonraki karakterle eşleştirin `char` .|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a>Adlandırılmış sayısal geribaşvurular

Adlı adlandırılmış bir geri başvuru içinde `\k` , *ad* bir sayının dize temsili de olabilir. Örneğin, aşağıdaki örnek, `(?<2>\w)\k<2>` bir dizedeki iki katına oluşan sözcük karakterlerini bulmak için normal ifadeyi kullanır. Bu durumda, örnek "2" olarak adlandırılan bir yakalama grubunu tanımlar ve geri başvuru "2" olarak adlandırılmıştır.

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

*Ad* bir sayının dize gösterimiyse ve yakalama grubu bu ada sahip değilse, `\k<` *ad* `>` geri başvuru `\` *numarasıyla*aynıdır, burada *sayı* yakalamanın sıra konumudur. Aşağıdaki örnekte adlı tek bir yakalama grubu vardır `char` . Geribaşvuru yapısı, bu öğeyi olarak ifade eder `\k<1>` . Örneğin çıkışının gösterdiği gibi, <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> ilk yakalama grubu olduğundan, başarılı olma çağrısı `char` .

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

Ancak, *ad* bir sayının dize gösterimiyse ve bu konumdaki yakalama grubuna açıkça sayısal bir ad atanmışsa, normal ifade ayrıştırıcısı yakalama grubunu sıra konumuna göre tanımlayamıyor. Bunun yerine, bir oluşturur <xref:System.ArgumentException> . Aşağıdaki örnekteki tek yakalama grubu "2" olarak adlandırılmıştır. Yapı, `\k` "1" adlı bir geri başvuru tanımlamak için kullanıldığından, normal ifade ayrıştırıcısı ilk yakalama grubunu tanımlayamıyor ve bir özel durum oluşturuyor.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a>Hangi geribaşvuruların eşleşmesi

Geri başvuru, bir grubun en son tanımına (soldan sağa eşleştirilirken en yakın bir tanım) başvurur. Bir grup birden çok yakalama yaptığında, geri başvuru en son yakalamayı ifade eder.

Aşağıdaki örnek, `(?<1>a)(?<1>\1b)*` \ 1 adlandırılmış grubunu tekrar tanımlayan bir normal ifade deseninin yer aldığı bir örnektir. Aşağıdaki tabloda, Normal ifadedeki her bir model açıklanmaktadır.

|Desen|Description|
|-------------|-----------------|
|`(?<1>a)`|"A" karakteriyle eşleşir ve sonucu adlı yakalama grubuna atayın `1` .|
|`(?<1>\1b)*`|"B" ile birlikte adlı grubun sıfır veya daha fazla `1` tekrarlanmasını eşleştirin ve sonucu adlı yakalama grubuna atayın `1` .|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

Normal ifadeyi giriş dizesiyle ("aababb") karşılaştırırken, normal ifade altyapısı aşağıdaki işlemleri gerçekleştirir:

1. Bu, dizenin başlangıcında başlar ve ifadesiyle "a" ile başarılı bir şekilde eşleşir `(?<1>a)` . `1`Grubun değeri artık "a" dır.

2. İkinci karaktere ilerletir ve "AB" dizesiyle `\1b` , veya "AB" ifadesiyle başarıyla eşleşir. Ardından "AB" sonucunu atar `\1` .

3. Dördüncü karaktere ilerletir. İfade `(?<1>\1b)*` sıfır veya daha fazla kez eşleştirilecek, bu nedenle "abb" dizesiyle birlikte ifadesiyle başarıyla eşleşiyor `\1b` . "Abb" sonucunu, öğesine geri atar `\1` .

Bu örnekte, `*` bir döngü nicelik belirteci, normal ifade altyapısı tanımladığı Düzenle eşleşene kadar sürekli değerlendirilir. Döngü nicelik belirteçleri grup tanımlarını temizlemez.

Bir grupta herhangi bir alt dize yakalanmadıysa, bu gruba yönelik bir geri başvuru tanımsızdır ve hiçbir şekilde eşleşmez. Bu, aşağıdaki gibi tanımlanan normal ifade deseninin gösterilmektedir `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` :

|Desen|Description|
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

- [Normal İfade Dili - Hızlı Başvuru](regular-expression-language-quick-reference.md)
