---
title: Normal İfadelerdeki Yeniden Başvuru Yapıları
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
ms.openlocfilehash: 5b16cfeda88b8e700c4d473962155a8510ce7df2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="backreference-constructs-in-regular-expressions"></a>Normal İfadelerdeki Yeniden Başvuru Yapıları
Yeniden başvurular yinelenen karakter veya bir dize içindeki alt dizenin tanımlamak için kolay bir yol sağlamak. Örneğin, giriş dizesi birden çok tekrarı rastgele bir alt dizeyi içeriyorsa, birinci yakalama grubu ile eşleşen ve ardından sonraki oluşumlarını alt dizeyi eşleştirmek için bir yeniden başvuru kullanın.  
  
> [!NOTE]
>  Ayrı bir söz dizimi, adlandırılmış ve numaralı değiştirme dizelerini gruplarında yakalama başvurmak için kullanılır. Daha fazla bilgi için bkz: [değişimler](substitutions-in-regular-expressions.md).  
  
 .NET numaralı ve adlandırılmış yakalama gruplarına başvurmak için ayrı dil öğeleri tanımlar. Grupları yakalama hakkında daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="numbered-backreferences"></a>Numaralı yeniden başvurular  
 Numaralı yeniden başvuru aşağıdaki söz dizimini kullanır:  
  
 `\` *Sayı*  
  
 Burada *numarası* sıralı yakalama grubunu normal ifadede konumudur. Örneğin, `\4` dördüncü yakalama Grup içeriğini eşleştirir. Varsa *numarası* normal ifade deseni içinde tanımlı değil, bir ayrıştırma hatası ortaya çıkar ve normal ifade altyapısı oluşturur bir <xref:System.ArgumentException>. Örneğin, normal ifade `\b(\w+)\s\1` geçerlidir, çünkü `(\w+)` ilk ve yalnızca ifade grubunda yakalıyor. Diğer taraftan, `\b(\w+)\s\2` geçersiz ve numaralı yakalama Grup olduğundan bir bağımsız değişken özel durum oluşturur `\2`. Ayrıca, varsa *numarası* belirli bir sıra konuma yakalama grubunda tanımlar, Grup yakalama sayısal atandı, ancak sıra konumunu farklı adı, normal ifade ayrıştırıcısının ayrıca bir oluşturur<xref:System.ArgumentException>. 
  
 Sekizli çıkış kodları arasında bir belirsizliğe unutmayın (gibi `\16`) ve `\` *numarası* aynı gösterimini kullanın yeniden başvurular. Bu belirsizlik gibi çözümlendi:  
  
-   İfadeleri `\1` aracılığıyla `\9` her zaman sekizli kodları olarak değil de, yeniden başvurular olarak yorumlanır.  
  
-   Multidigit ifadesinin ilk rakam 8 veya 9 olup olmadığını (gibi `\80` veya `\91`), bir hazır değer yorumlanan olarak ifade.  
  
-   Gelen ifadeleri `\10` ve büyük bu numara; Aksi takdirde karşılık gelen bir yeniden başvuru ise yeniden başvurular kabul, bunlar sekizli kodlar olarak yorumlanır.  
  
-   Normal bir ifade tanımsız grup numarası yeniden başvuru içeriyorsa, bir ayrıştırma hatası ortaya çıkar ve normal ifade altyapısı oluşturur bir <xref:System.ArgumentException>.  
  
 Belirsizliği bir sorunsa, kullanabileceğiniz `\k<` *adı* `>` anlaşılır ve sekizli karakter kodlarıyla kafası olamaz gösterimi. Benzer şekilde, onaltılık gibi kodları `\xdd` anlaşılır ve yeniden başvurular ile kafası olamaz.  
  
 Aşağıdaki örnek, bir dize iki kat sözcük karakterlerini bulur. Normal bir ifade tanımlar `(\w)\1`, aşağıdaki öğelerden oluşur.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`(\w)`|İlk yakalama grubuna atayın ve bir sözcük karakteriyle eşleşmiyor.|  
|`\1`|İlk yakalama grubunun değeri aynı sonraki karakteri eşleştirmek.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a>Adlandırılmış yeniden başvurular  
 Adlandırılmış yeniden başvuru, aşağıdaki sözdizimi kullanılarak tanımlanır:  
  
 `\k<` *Adı* `>`  
  
 veya:  
  
 `\k'` *Adı* `'`  
  
 Burada *adı* normal ifade deseni içinde tanımlanan bir yakalama grubunu adıdır. Varsa *adı* normal ifade deseni içinde tanımlı değil, bir ayrıştırma hatası ortaya çıkar ve normal ifade altyapısı oluşturur bir <xref:System.ArgumentException>.  
  
 Aşağıdaki örnek, bir dize iki kat sözcük karakterlerini bulur. Normal bir ifade tanımlar `(?<char>\w)\k<char>`, aşağıdaki öğelerden oluşur.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`(?<char>\w)`|Adlı bir yakalama grubuna atayın ve bir sözcük karakteriyle eşleşiyor `char`.|  
|`\k<char>`|Değeri aynı sonraki karakteri eşleştirmek `char` Grup yakalama.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  

## <a name="named-numeric-backreferences"></a>Adlandırılmış sayısal yeniden başvurular

Adlandırılmış bir yeniden başvuru ile içinde `\k`, *adı* bir sayı dize gösterimini de olabilir. Örneğin, aşağıdaki örnekte normal ifade kullanan `(?<2>\w)\k<2>` dizede iki kat sözcük karakterlerini bulmak için. Bu durumda, örnek açıkça "2" adında bir yakalama grubunu tanımlar ve yeniden başvuru gelenlere "2" adında. 
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  

Varsa *adı* bir sayı dize gösterimini olduğundan ve hiçbir yakalama grubu bu ada sahip `\k<` *adı* `>` yeniden başvuru aynı `\`  *sayı*, burada *numarası* yakalama sıralı konumudur. Aşağıdaki örnekte, yok adlı tek bir yakalama grubunu `char`. Yeniden başvuru yapı olarak başvuruyor `\k<1>`. Örnek gösterir, çağrısı çıktısı olarak <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> çünkü başarılı `char` ilk yakalama grubudur.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]  

Ancak, varsa *adı* bir sayı dize gösterimi ise ve konumu sayısal bir ad, normal ifade ayrıştırıcısının açıkça atandı yakalama grubunda sıralı konumuna göre yakalama grubunu tanımlanamıyor . Bunun yerine, oluşturur bir <xref:System.ArgumentException>. Aşağıdaki örnekte yalnızca yakalama grubunu, "2" olarak adlandırılır. Çünkü `\k` yapı "1" adlı bir yeniden başvuru tanımlamak için kullanılır, normal ifade ayrıştırıcısının ilk yakalama grubunu belirleyemiyor ve bir özel durum oluşturur.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]  

## <a name="what-backreferences-match"></a>Hangi yeniden başvurular eşleşmiyor  
 Bir yeniden başvuru (eşleştirirken hemen en soldaki, tanımına soldan sağa) bir grubun en son tanım ifade eder. Birden çok yakalayan bir grup yapar, bir yeniden başvuru en son yakalama başvuruyor.  
  
 Aşağıdaki örnek, bir normal ifade deseni içerir `(?<1>a)(?<1>\1b)*`, Grup adlı \1 yeniden tanımlamaktadır. Aşağıdaki tabloda her düzeni normal ifadede açıklanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(?<1>a)`|Karakter eşleşmesi "a" ve yakalama grubunu sonucu adlı Ata `1`.|  
|`(?<1>\1b)*`|Adlı Grup eşleşme 0 veya 1 oluşumunu `1` "b" ve ata adlı yakalama grubunu sonucu birlikte `1`.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 Normal ifade giriş dizesi ("aababb") ile karşılaştırarak normal ifade altyapısı aşağıdaki işlemleri gerçekleştirir:  
  
1.  Dizenin başında başlar ve başarıyla eşleşen with ifadesi "a" `(?<1>a)`. Değeri `1` grubudur şimdi "a".  
  
2.  İkinci karaktere ilerletir ve başarıyla with ifadesi "ab" dizesini eşleştirir `\1b`, veya "ab". Ardından sonucu, "ab" için atar `\1`.  
  
3.  Dördüncü karaktere ilerletir. İfade `(?<1>\1b)` olmasını eşleşen sıfır veya birden fazla kez böylece başarıyla eşleşecek dizesi "abb" ifadesi ile `\1b`. Sonuç, "abb" başa atar `\1`.  
  
 Bu örnekte, `*` döngü niceleyici--olan normal ifade altyapısı tanımladığı düzeni eşleşemez kadar sürekli olarak değerlendirilir. Döngü nicelik grup tanımlarını işaretini kaldırmayın.  
  
 Bir grup herhangi bir alt dize yakalandı değil, bu gruba yeniden başvuru tanımlı değil ve hiçbir zaman eşleştirir. Bu normal ifade deseni tarafından gösterilmiştir `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, hangi aşağıdaki gibi tanımlanır:  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Word sınır eşleşmeye başlayın.|  
|`(\p{Lu}{2})`|İki büyük harf eşleşir. Bu ilk yakalama grubudur.|  
|`(\d{2})?`|İki ondalık basamak sıfır veya bir örneğini Bul. Bu ikinci yakalama grubudur.|  
|`(\p{Lu}{2})`|İki büyük harf eşleşir. Bu, üçüncü yakalama grubudur.|  
|`\b`|Son bir word sınırında eşleşmiyor.|  
  
 İkinci yakalama grubu tarafından tanımlanan iki ondalık basamak mevcut değilse bile giriş dizesi bu normal ifadeyi eşleştirir. Aşağıdaki örnek, eşleştirmenin başarılı olsa bile, boş bir yakalama grubu iki başarılı yakalama grupları arasında bulunan gösterir.  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
