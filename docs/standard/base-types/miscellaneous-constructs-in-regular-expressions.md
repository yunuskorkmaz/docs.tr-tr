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
ms.openlocfilehash: a43ce44e11a9231dee2961ee02bac745d9ca71cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141607"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Normal İfadelerdeki Çeşitli Yapılar
.NET'teki normal ifadeler üç çeşitli dil yapısı içerir. Bir normal ifade deseni ortasında belirli eşleştirme seçenekleri etkinleştirmek veya devre dışı etmenizi sağlar. Geri kalan iki normal bir ifade yorum eklemenize izin verin.  
  
## <a name="inline-options"></a>Satır Satır Seçenekleri  
 Sözdizimini kullanarak normal bir ifadenin bir bölümü için belirli desen eşleştirme seçeneklerini ayarlayabilir veya devre dışı bırakabilirsiniz  
  
`(?imnsx-imnsx)`  
  
 Soru işaretinden sonra etkinleştirmek istediğiniz seçenekleri ve eksi işaretinden sonra devre dışı kılmasını istediğiniz seçenekleri listelersiniz. Aşağıdaki tabloda her bir seçenek açıklanmaktadır. Her seçenek hakkında daha fazla bilgi için [Düzenli İfade Seçenekleri'ne](../../../docs/standard/base-types/regular-expression-options.md)bakın.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`i`|Büyük/küçük harf duyarsız eşleştirme.|  
|`m`|Çoklu çizgi modu.|  
|`n`|Yalnızca açık yakalar. (Parantezler yakalama grubu olarak hareket etmez.)|  
|`s`|Tek satırlı mod.|  
|`x`|Kaçan beyaz alanı yoksay ve x-modu açıklamalarına izin verin.|  
  
 `(?imnsx-imnsx)` Yapı tarafından tanımlanan normal ifade seçeneklerindeki herhangi bir değişiklik, çevreleyen grubun sonuna kadar geçerli kalır.  
  
> [!NOTE]
> `(?imnsx-imnsx:` *Alt ifade* `)` gruplandırma yapısı, bir alt ifade için aynı işlevselliği sağlar. Daha fazla bilgi için [yapıyı gruplandırma](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)ya da gruplandırma'ya bakın.  
  
 Aşağıdaki örnek, `i`büyük/küçük `x` harf duyarsızlığını ve açık yakalamaları etkinleştirmek ve normal ifadenin ortasındaki normal ifade desenindeki beyaz alanı yok saymak için , ve `n`seçenekleri kullanır.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 Örnek, iki normal ifade tanımlar. İlk, `\b(D\w+)\s(d\w+)\b`bir büyük harf "D" ve küçük bir "d" ile başlayan iki ardışık kelime eşleşir. İkinci normal ifade, `\b(D\w+)(?ixn) \s (d\w+) \b`aşağıdaki tabloda açıklandığı gibi, bu deseni değiştirmek için satır satır seçeneklerini kullanır. Sonuçların karşılaştırılması `(?ixn)` yapının etkisini doğrular.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(D\w+)`|Bir veya daha fazla sözcük karakteri nin ardından büyük "D" harflerini eşleştirin. Bu ilk yakalama grubu.|  
|`(?ixn)`|Bu noktadan itibaren, karşılaştırmalar büyük/küçük harf duyarsız yapmak, yalnızca açık yakalar yapmak ve normal ifade desen beyaz boşluk yoksay.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(d\w+)`|Bir büyük veya küçük "d" harfve ardından bir veya daha fazla sözcük karakteri eşleştirin. `n` (Açık yakalama) seçeneği etkin olduğu için bu grup ele geçirilmez...|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
## <a name="inline-comment"></a>Satır Satırda Yorum  
 `(?#` *comment* Açıklama`)` yapısı, normal bir ifadeye satır içinde bir açıklama eklemenizi sağlar. Normal ifade altyapısı, <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> açıklama yöntemtarafından döndürülen dizeye dahil olmasına rağmen, desen eşleştirmesinde yorumun herhangi bir bölümünü kullanmaz. Açıklama ilk kapanış parantezinde sona erer.  
  
 Aşağıdaki örnek, önceki bölümdeki örnekteki ilk normal ifade deseni yineler. Karşılaştırmanın büyük/küçük harf duyarlı olup olmadığını belirtmek için normal ifadeye iki satır içi yorum ekler. Normal ifade deseni aşağıdaki `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b`gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?# case-sensitive comparison)`|Bir yorum. Desen eşleştirme davranışını etkilemez.|  
|`(D\w+)`|Bir veya daha fazla sözcük karakteri nin ardından büyük "D" harflerini eşleştirin. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(?ixn)`|Bu noktadan itibaren, karşılaştırmalar büyük/küçük harf duyarsız yapmak, yalnızca açık yakalar yapmak ve normal ifade desen beyaz boşluk yoksay.|  
|`(?#case-insensitive comparison)`|Bir yorum. Desen eşleştirme davranışını etkilemez.|  
|`(d\w+)`|Bir büyük veya küçük "d" harfve ardından bir veya daha fazla sözcük karakteri eşleştirin. Bu ikinci yakalama grubu.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Satır Sonu Yorumu  
 Bir sayı`#`işareti ( )normal ifade deseninin sonundaki unescape # karakterinden başlayan ve satırın sonuna kadar devam eden bir x-mode yorumunu işaretler. Bu yapıyı kullanmak için, `x` nesneyi <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> anında kullanırken `option` <xref:System.Text.RegularExpressions.Regex> veya statik <xref:System.Text.RegularExpressions.Regex> bir yöntem ararken seçeneği (satır satır seçenekleri aracılığıyla) etkinleştirmeniz veya değeri parametreye sağlamanız gerekir.  
  
 Aşağıdaki örnek, satır sonu yorum yapısını göstermektedir. Bir dize en az bir biçim öğesi içeren bir bileşik biçim dize olup olmadığını belirler. Aşağıdaki tabloda normal ifade desenindeki yapılar açıklanmaktadır:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\{`|Açılış ayracıyla eşleştirin.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`(,-*\d+)*`|Sıfır veya virgül oluşumunu eşleştirin, ardından isteğe bağlı eksi işareti ve ardından bir veya daha fazla ondalık basamak.|  
|`(\:\w{1,4}?)*`|Bir üst noktanın sıfır veya bir oluşumunu, ardından bir-dört ile, ancak mümkün olduğunca az beyaz boşluk karakterleri eşleştirin.|  
|`\}`|Kapanış ayraçlarını eşleştirin.|  
|`(?x)`|Satır sonu yorumunun tanınması için desen beyaz boşluk seçeneğini etkinleştirin.|  
|`# Looks for a composite format item.`|Satır sonu yorumu.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Yapıyı `(?x)` normal ifadede sağlamak yerine, açıklamanın <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi arayarak ve numaralandırma değerini geçirerek <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> de tanımış olabileceğini unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
