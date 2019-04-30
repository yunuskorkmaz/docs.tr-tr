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
# <a name="backreference-constructs-in-regular-expressions"></a>Normal İfadelerdeki Yeniden Başvuru Yapıları

Yeniden başvurular yinelenen karakter veya dize içinde alt dizeyi tanımlamak için kullanışlı bir yol sağlar. Örneğin, giriş dizesini birden çok defa geçmelerine rastgele bir alt dizenin içeriyorsa, ilk geçtiği bir yakalama grubuyla eşleşen ve ardından alt dizeyi sonraki tekrarı ile eşleştir için bir yeniden başvuru kullanın.

> [!NOTE]
> Ayrı bir söz dizimi, adlandırılmış veya numaralandırılmış yakalama grupları değiştirme Dizelerdeki başvurmak için kullanılır. Daha fazla bilgi için bkz. [Değişimler](substitutions-in-regular-expressions.md).

.NET için numaralandırılmış ve adlandırılmış yakalama grupları başvurmak için ayrı dil öğelerini tanımlar. Yakalama grupları hakkında daha fazla bilgi için bkz. [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

## <a name="numbered-backreferences"></a>Numaralandırılmış yeniden başvurular

Numaralandırılmış bir yeniden başvuru aşağıdaki sözdizimini kullanır:

`\` *Sayı*

Burada *numarası* normal ifadedeki yakalama grubunun sıralı konumu. Örneğin, `\4` dördüncü yakalama grubunun içeriğiyle eşleşir. Varsa *numarası* normal ifade deseninde tanımlı değil, bir ayrıştırma hatasını ortaya çıkar ve normal ifade motoru oluşturur bir <xref:System.ArgumentException>. Örneğin, normal ifade `\b(\w+)\s\1` geçerlidir, çünkü `(\w+)` ilk ve tek Grup ifadesinde yakalıyor. Öte yandan, `\b(\w+)\s\2` numaralandırılmış yakalama grubu yok olduğundan bir bağımsız değişken özel durum oluşturur ve geçersiz `\2`. Ayrıca, varsa *numarası* sıralı belirli bir konumda bir yakalama grubunu tanımlar, yakalama grubu sayısal verildiğine göre ancak sıra konumuna farklı bir ad, normal ifade ayrıştırıcısı bir deoluşturur<xref:System.ArgumentException>.

Sekizli çıkış kodlarını arasında belirsizlik unutmayın (gibi `\16`) ve `\` *numarası* aynı gösterimi kullanan yeniden başvurular. Bu belirsizlik işlemler sırasında aşağıdaki gibi çözümlenir:

- İfadeleri `\1` aracılığıyla `\9` her zaman yeniden başvurular ve sekizlik kodları değil olarak yorumlanır.

- İlk basamak multidigit ifadesinin 8 veya 9 olup olmadığını (gibi `\80` veya `\91`), ifade bir sabit değer yorumlanır.

- Gelen ifadeleri `\10` ve daha fazla bigli varsa o sayı; Aksi takdirde karşılık gelen bir yeniden başvuru kabul, bunlar sekizlik kodları yorumlanır.

- Normal bir ifade tanımsız grup numarası bir yeniden başvuru içeriyorsa, bir ayrıştırma hatası oluşur ve normal ifade motoru oluşturur bir <xref:System.ArgumentException>.

Belirsizliği bir sorun olması durumunda, kullanabileceğiniz `\k<` *adı* `>` anlaşılır ve sekizli karakter kodlarıyla kafanız olamaz, gösterimi. Benzer şekilde, onaltılı gibi kodları `\xdd` anlaşılır ve geribaşvurular ile karıştırılır olamaz.

Aşağıdaki örnek bir dizedeki yinelenen sözcük karakterlerini bulur. Bir normal ifade tanımlar `(\w)\1`, aşağıdaki öğelerden oluşur.

|Öğe|Açıklama|
|-------------|-----------------|
|`(\w)`|Bir sözcük karakteri Eşleştir ve ilk yakalama gruba atayın.|
|`\1`|İlk yakalama grubunun değeri ile aynıdır sonraki karakterle eşleş.|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a>Adlandırılmış yeniden başvurular

Adlandırılmış bir yeniden başvuru, aşağıdaki söz dizimini kullanarak tanımlanır:

`\k<` *Adı* `>`

veya:

`\k'` *Adı* `'`

Burada *adı* normal ifade deseninde tanımlanan bir yakalama grubunun adıdır. Varsa *adı* normal ifade deseninde tanımlı değil, bir ayrıştırma hatasını ortaya çıkar ve normal ifade motoru oluşturur bir <xref:System.ArgumentException>.

Aşağıdaki örnek bir dizedeki yinelenen sözcük karakterlerini bulur. Bir normal ifade tanımlar `(?<char>\w)\k<char>`, aşağıdaki öğelerden oluşur.

|Öğe|Açıklama|
|-------------|-----------------|
|`(?<char>\w)`|Bir sözcük karakteri Eşleştir ve adlandırılmış bir tutma grubu atamak `char`.|
|`\k<char>`|Değerini aynıdır sonraki karakteri eşleştirmek `char` yakalama grubu.|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a>Adlandırılmış sayısal yeniden başvurular

Adlandırılmış bir yeniden başvuru ile içinde `\k`, *adı* bir sayının dize gösterimini de olabilir. Örneğin, aşağıdaki örnekte normal ifadeyi kullanan `(?<2>\w)\k<2>` yinelenen sözcük karakterlerini bir dizeyi bulmak için. Bu durumda, örnek açıkça "2" adında bir yakalama grubunu tanımlar ve geribaşvuru gelenlere "2" olarak adlandırılır.

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

Varsa *adı* bir sayının dize gösterimini olduğundan ve hiçbir yakalama grubu bu ada sahip `\k<` *adı* `>` geribaşvuru aynı `\`  *sayı*burada *numarası* yakalama sıralı konumudur. Aşağıdaki örnekte adlı tek bir yakalama grubu yoktur `char`. Yeniden başvuru yapısı olarak başvurur `\k<1>`. Örnekte gösterildiği çağrısı çıktısı olarak <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> çünkü başarılı `char` ilk yakalama grubudur.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

Ancak, varsa *adı* bir sayının dize gösterimini olduğunu ve konumu sayısal bir ada, normal ifade ayrıştırıcısı açıkça atandığını yakalama grubundaki sıralı konumuna göre yakalama grubu tanımlanamıyor . Bunun yerine, oluşturur bir <xref:System.ArgumentException>. Aşağıdaki örnekte yalnızca yakalama grubu "2" olarak adlandırılır. Çünkü `\k` yapısı "1" adlı bir yeniden başvuru tanımlamak için kullanıldığında, normal ifade ayrıştırıcısı ilk yakalama grubuyla belirleyemiyor ve bir özel durum oluşturur.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a>Hangi Geribaşvurular eşleştir

Bir yeniden başvuru en son (en hemen eşleştirirken sola, tanım soldan sağa) bir grup tanımını gösterir. Birden çok yakalayan bir grup yapar, bir yeniden başvuru için en son yakalama ifade eder.

Aşağıdaki örnek, bir normal ifade deseni içerir `(?<1>a)(?<1>\1b)*`, adlandırılmış Grup \1 yeniden tanımlar. Aşağıdaki tabloda her normal ifade deseninde açıklanmaktadır.

|Desen|Açıklama|
|-------------|-----------------|
|`(?<1>a)`|Bir karakterle Eşleştir "a" ve yakalama grubu sonucu adlı Ata `1`.|
|`(?<1>\1b)*`|Adlı grubu sıfır veya daha çok tekrarı ile eşleştir `1` yanı sıra bir "b" ve ata adlı yakalama grubudur sonucu `1`.|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

Normal ifade giriş dizesini ("aababb") ile karşılaştırmak, normal ifade altyapısı aşağıdaki işlemleri gerçekleştirir:

1. Dize başlangıcında başlar ve başarıyla eşleşen with ifadesi "a" `(?<1>a)`. Değerini `1` grubudur artık "a".

2. İkinci karakter ilerler ve başarıyla dize "ab" ifadesi ile eşleşen `\1b`, veya "ab". Ardından, "ab" için sonuç atar `\1`.

3. Bu dördüncü karaktere ilerletir. İfade `(?<1>\1b)*` olarak eşleşen sıfır veya birden fazla kez şekilde başarıyla eşleşecek bir dize ifadesiyle, "abb" `\1b`. Sonuç, "abb" geri atar `\1`.

Bu örnekte, `*` döngü bir miktar belirleyiciyi--olan normal ifade motoru tanımlar deseni eşleşemez kadar sürekli olarak değerlendirilir. Döngü miktar belirleyiciler grup tanımlarını işaretini kaldırmayın.

Bir grubu herhangi bir alt dize yakalanan değil, bu gruba bir yeniden başvuru tanımlı değildir ve ile eşleşir. Bu normal ifade deseni tarafından gösterilen `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, hangi şu şekilde tanımlanır:

|Desen|Açıklama|
|-------------|-----------------|
|`\b`|Bir sözcük sınırında eşleşmeye başla.|
|`(\p{Lu}{2})`|İki büyük harfler eşleştirin. Bu ilk yakalama grubudur.|
|`(\d{2})?`|İki ondalık basamak sıfır veya bir oluşumunu eşleştirin. Bu ikinci yakalama grubudur.|
|`(\p{Lu}{2})`|İki büyük harfler eşleştirin. Bu, üçüncü yakalama grubudur.|
|`\b`|Eşleşme bir sözcük sınırında sonlandır.|

İkinci yakalama grubu tarafından tanımlanan iki ondalık basamak mevcut olmasa bile bir Giriş dizesinin bu normal ifade eşleşebilir. Aşağıdaki örnek, eşleşmenin başarılı olsa bile başarılı iki yakalama grupları arasında boş bir yakalama grubu bulunamazsa olduğunu gösterir.

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
