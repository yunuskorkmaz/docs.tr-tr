---
title: Normal İfadelerdeki Çeşitli Yapılar
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- constructs, miscellaneous
- .NET Framework regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b4e9072100a25c297dbf3bfb70a928e16b06da4
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956883"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Normal İfadelerdeki Çeşitli Yapılar
.NET 'teki normal ifadeler üç çeşitli dil yapılarını içerir. Bir normal ifade deseninin ortasında belirli eşleştirme seçeneklerini etkinleştirmenizi veya devre dışı bırakmanızı sağlar. Kalan iki, açıklamaları normal bir ifadeye eklemenizi sağlar.  
  
## <a name="inline-options"></a>Satır içi seçenekler  
 Sözdizimini kullanarak normal bir ifadenin bir parçası için belirli bir model eşleştirme seçeneklerini ayarlayabilir veya devre dışı bırakabilirsiniz  
  
`(?imnsx-imnsx)`  
  
 Soru işaretinden sonra etkinleştirmek istediğiniz seçenekleri ve eksi işaretinden sonra devre dışı bırakmak istediğiniz seçenekleri listeleyin. Aşağıdaki tabloda her bir seçenek açıklanmaktadır. Her seçenek hakkında daha fazla bilgi için bkz. [normal Ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`i`|Büyük/küçük harfe duyarsız eşleşme.|  
|`m`|Çok satırlı mod.|  
|`n`|Yalnızca açık yakalamaları. (Parantezler, yakalama grupları olarak davranmaz.)|  
|`s`|Tek satırlık mod.|  
|`x`|Kaçışsız boşluk işaretini yoksayın ve x-Mode yorumlara izin verin.|  
  
 @No__t-0 yapısı tarafından tanımlanan normal ifade seçeneklerinde yapılan herhangi bir değişiklik, kapsayan grubun sonuna kadar yürürlükte kalır.  
  
> [!NOTE]
> @No__t-0 alt*ifadesi*`)` gruplama yapısı, bir alt ifade için aynı işlevselliği sağlar. Daha fazla bilgi için bkz. [yapıları gruplandırma](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Aşağıdaki örnek, büyük/küçük harf duyarlı ve açık yakalamaları etkinleştirmek ve normal bir ifadenin ortasında yer alan normal ifade deseninin boşluk yoksaymak için `i`, `n` ve `x` seçeneklerini kullanır.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 Örnek iki normal ifade tanımlar. Birincisi, `\b(D\w+)\s(d\w+)\b`, büyük bir "D" ve küçük harfli "d" ile başlayan iki ardışık sözcükten eşleşir. İkinci normal ifade `\b(D\w+)(?ixn) \s (d\w+) \b`, aşağıdaki tabloda açıklandığı gibi bu kalıbı değiştirmek için satır içi seçenekleri kullanır. Sonuçların karşılaştırması `(?ixn)` yapısının etkisini onaylar.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(D\w+)`|Büyük bir "D" ve ardından bir veya daha fazla sözcük karakteri Eşleştir. Bu ilk yakalama grubudur.|  
|`(?ixn)`|Bu noktadan itibaren, karşılaştırmalar büyük/küçük harf duyarsız, yalnızca açık yakalamaları yapın ve normal ifade deseninin boşluk olduğunu yoksayın.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(d\w+)`|Büyük veya küçük harf "d" ile sonra bir veya daha fazla sözcük karakteri eşleştirin. @No__t-0 (açık yakalama) seçeneği etkinleştirildiğinden bu grup yakalanmaz.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
## <a name="inline-comment"></a>Satır içi açıklama  
 @No__t-0 *açıklaması*`)` yapısı, bir normal ifadeye satır içi bir açıklama eklemenizi sağlar. Normal ifade altyapısı, açıklama <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> yöntemi tarafından döndürülen dizeye dahil edilse de, bu açıklamanın herhangi bir parçasını model eşleme içinde kullanmaz. Açıklama ilk kapanış parantezinde sona erer.  
  
 Aşağıdaki örnek, önceki bölümdeki örnekteki ilk normal ifade deseninin yinelenir. Karşılaştırmayı, büyük/küçük harfe duyarlı olup olmadığını belirtmek için normal ifadeye iki satır içi açıklama ekler. @No__t-0 normal ifade deseninin aşağıdaki şekilde tanımlanması gerekir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?# case-sensitive comparison)`|Bir yorum. Desenler ile eşleşen davranışı etkilemez.|  
|`(D\w+)`|Büyük bir "D" ve ardından bir veya daha fazla sözcük karakteri Eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(?ixn)`|Bu noktadan itibaren, karşılaştırmalar büyük/küçük harf duyarsız, yalnızca açık yakalamaları yapın ve normal ifade deseninin boşluk olduğunu yoksayın.|  
|`(?#case-insensitive comparison)`|Bir yorum. Desenler ile eşleşen davranışı etkilemez.|  
|`(d\w+)`|Büyük veya küçük harf "d" ile sonra bir veya daha fazla sözcük karakteri eşleştirin. Bu ikinci yakalama grubudur.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Satır sonu açıklaması  
 Numara işareti (`#`), normal ifade deseninin sonunda kaçışsız # karakteriyle başlayan ve satırın sonuna kadar devam eden bir x-Mode açıklamasını işaretler. Bu yapıyı kullanmak için `x` seçeneğini etkinleştirmeniz (satır içi seçenekler aracılığıyla) veya <xref:System.Text.RegularExpressions.Regex> nesnesini örnekledikten veya statik bir <xref:System.Text.RegularExpressions.Regex> yöntemi çağırırken `option` parametresine <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> değeri sağlamanız gerekir.  
  
 Aşağıdaki örnek satır sonu açıklama yapısını gösterir. Bir dizenin en az bir biçim öğesi içeren bir bileşik biçim dizesi olup olmadığını belirler. Aşağıdaki tabloda, normal ifade deseninin yapıları açıklanmaktadır:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\{`|Bir açma ayracı eşleştirin.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`(,-*\d+)*`|Sıfırdan sonra bir veya daha fazla ondalık basamak ile, bir virgülden sonra sıfır veya bir oluşumu ve ardından isteğe bağlı bir eksi işareti ile eşleştirin.|  
|`(\:\w{1,4}?)*`|İki nokta üst üste, ardından bir ile dört arasında, ancak mümkün olan, boşluk karakterlerinden az olan sıfır veya bir oluşumu eşleştirin.|  
|`\}`|Bir kapanış ayracı eşleştirin.|  
|`(?x)`|Satır sonu açıklamasının tanınması için, stili yoksay beyaz alanı seçeneğini etkinleştirin.|  
|`# Looks for a composite format item.`|Satır sonu açıklaması.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Normal ifadede `(?x)` yapısını sağlamak yerine, açıklamanın <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi çağırarak ve <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> sabit listesi değeri geçirerek tanındığını unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
