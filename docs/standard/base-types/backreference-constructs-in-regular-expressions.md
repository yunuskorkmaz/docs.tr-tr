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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2ec92933bdf123412a3d489fc493d76c4a0dc0d0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="backreference-constructs-in-regular-expressions"></a>Normal İfadelerdeki Yeniden Başvuru Yapıları
Yeniden başvurular yinelenen karakter veya bir dize içindeki alt dizenin tanımlamak için kolay bir yol sağlamak. Örneğin, giriş dizesi birden çok tekrarı rastgele bir alt dizeyi içeriyorsa, birinci yakalama grubu ile eşleşen ve ardından sonraki oluşumlarını alt dizeyi eşleştirmek için bir yeniden başvuru kullanın.  
  
> [!NOTE]
>  Ayrı bir söz dizimi, adlandırılmış ve numaralı değiştirme dizelerini gruplarında yakalama başvurmak için kullanılır. Daha fazla bilgi için bkz: [değişimler](substitutions-in-regular-expressions.md).  
  
 .NET numaralı ve adlandırılmış yakalama gruplarına başvurmak için ayrı dil öğeleri tanımlar. Grupları yakalama hakkında daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="numbered-backreferences"></a>Numaralı yeniden başvurular  
 Numaralı yeniden başvuru aşağıdaki söz dizimini kullanır:  
  
 `\`*numarası*  
  
 Burada *numarası* sıralı yakalama grubunu normal ifadede konumudur. Örneğin, `\4` dördüncü yakalama Grup içeriğini eşleştirir. Varsa *numarası* normal ifade deseni içinde tanımlı değil, bir ayrıştırma hatası ortaya çıkar ve normal ifade altyapısı oluşturur bir <xref:System.ArgumentException>. Örneğin, normal ifade `\b(\w+)\s\1` geçerlidir, çünkü `(\w+)` ilk ve yalnızca ifade grubunda yakalıyor. Diğer taraftan, `\b(\w+)\s\2` geçersiz ve numaralı yakalama Grup olduğundan bir bağımsız değişken özel durum oluşturur `\2`.  
  
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
  
 `\k<`*adı*`>`  
  
 veya:  
  
 `\k'`*adı*`'`  
  
 Burada *adı* normal ifade deseni içinde tanımlanan bir yakalama grubunu adıdır. Varsa *adı* normal ifade deseni içinde tanımlı değil, bir ayrıştırma hatası ortaya çıkar ve normal ifade altyapısı oluşturur bir <xref:System.ArgumentException>.  
  
 Aşağıdaki örnek, bir dize iki kat sözcük karakterlerini bulur. Normal bir ifade tanımlar `(?<char>\w)\k<char>`, aşağıdaki öğelerden oluşur.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`(?<char>\w)`|Adlı bir yakalama grubuna atayın ve bir sözcük karakteriyle eşleşiyor `char`.|  
|`\k<char>`|Değeri aynı sonraki karakteri eşleştirmek `char` Grup yakalama.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 Unutmayın *adı* bir sayı dize gösterimini de olabilir. Örneğin, aşağıdaki örnekte normal ifade kullanan `(?<2>\w)\k<2>` dizede iki kat sözcük karakterlerini bulmak için.  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
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
