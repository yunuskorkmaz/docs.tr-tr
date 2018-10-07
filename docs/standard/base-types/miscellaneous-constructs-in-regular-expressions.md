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
ms.openlocfilehash: 8956726915ebe1c0b1c7654e62e2e28620274b4a
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836290"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Normal İfadelerdeki Çeşitli Yapılar
.NET içinde normal ifadeler üç çeşitli dil yapıları içerir. Biri, etkinleştirme veya devre dışı ortasında bir normal ifade deseni eşleştirme belirli seçenekleri sağlar. Kalan iki normal bir ifadede açıklamalar ekleme olanak tanır.  
  
## <a name="inline-options"></a>Satır içi Seçenekler  
 Ayarlayabilir veya belirli desen eşleştirme için normal bir ifade parçası seçeneklerini sözdizimi kullanılarak devre dışı bırak  
  
```  
(?imnsx-imnsx)  
```  
  
 Soru işaretinden sonra etkinleştirmek istediğiniz seçenekleri ve eksi işareti sonra devre dışı bırakmak istediğiniz seçenekleri listeler. Aşağıdaki tabloda her bir seçenek açıklanmaktadır. Her bir seçenek hakkında daha fazla bilgi için bkz. [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`i`|Büyük küçük harf duyarsız eşleştirme.|  
|`m`|Çok satırlı modu.|  
|`n`|Yalnızca açık yakalamalar. (Parantez hareket değil olarak yakalama grupları.)|  
|`s`|Tek satır modu.|  
|`x`|Çıkmamış boşluğu yoksay ve x modu açıklamalara izin verme.|  
  
 Normal ifade seçenekleri tarafından tanımlanan herhangi bir değişiklik `(?imnsx-imnsx)` kalır kapsayan grubun sonuna kadar geçerli oluşturun.  
  
> [!NOTE]
>  `(?imnsx-imnsx:` *Subexpression* `)` gruplama yapısında bir alt ifade için aynı işlevselliği sağlar. Daha fazla bilgi için [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Aşağıdaki örnekte `i`, `n`, ve `x` büyük/küçük harfe ve açık yakalamalar etkinleştirmek ve normal ifade deseninde bir normal ifade ortasında beyaz boşluğu yok saymak için Seçenekler.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 Örneğin, iki normal ifade tanımlar. Birincisi, `\b(D\w+)\s(d\w+)\b`, "D" bir büyük harf ve küçük harf "d" ile başlayan iki ardışık sözcüklerle eşleşir. İkinci normal ifade `\b(D\w+)(?ixn) \s (d\w+) \b`, aşağıdaki tabloda açıklandığı gibi bu düzeni değiştirmek için satıriçi seçeneklerini kullanır. Sonuçları karşılaştırması etkisini onaylar `(?ixn)` oluşturun.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(D\w+)`|Büyük harf "D" bir veya daha fazla sözcük karakteri ve ardından eşleştirin. Bu ilk yakalama grubudur.|  
|`(?ixn)`|Bu noktasında, büyük küçük harf duyarsız karşılaştırmalar yapmak, yalnızca açık olun yakalar ve normal ifade deseninde beyaz boşluğu yok saymak.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(d\w+)`|Bir büyük veya küçük harf "d" bir veya daha fazla sözcük karakteri ve ardından eşleştirin. Bu grup, çünkü yakalanmaz `n` (belirtik yakalama) seçeneği etkinleştirilmiş...|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
## <a name="inline-comment"></a>Satır için açıklama  
 `(?#` *Yorum* `)` yapısı normal bir ifadede bir satır içi açıklama eklemenize olanak tanır. Normal ifade altyapısı tarafından döndürülen dize içinde açıklamayı olsa desen eşleştirme, açıklaması, herhangi bir bölümünü kullanmaz <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> yöntemi. Açıklama ilk kapanış parantezinde sona erer.  
  
 Aşağıdaki örnek, önceki bölümdeki örnekte birinci normal ifade deseni tekrarlar. Karşılaştırma büyük/küçük harfe olup olmadığını belirtmek için normal ifade iki satır içi açıklamalara ekler. Normal ifade deseni `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b`, şu şekilde tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?# case-sensitive comparison)`|Bir yorum. Desen eşleştirme davranışını etkilemez.|  
|`(D\w+)`|Büyük harf "D" bir veya daha fazla sözcük karakteri ve ardından eşleştirin. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(?ixn)`|Bu noktasında, büyük küçük harf duyarsız karşılaştırmalar yapmak, yalnızca açık olun yakalar ve normal ifade deseninde beyaz boşluğu yok saymak.|  
|`(?#case-insensitive comparison)`|Bir yorum. Desen eşleştirme davranışını etkilemez.|  
|`(d\w+)`|Bir büyük veya küçük harf "d" bir veya daha fazla sözcük karakteri ve ardından eşleştirin. Bu ikinci yakalama grubudur.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Satır sonu açıklaması  
 Sayı işareti (`#`) normal ifade deseni sonunda atlanmayan # karakteri başlar ve satırın sonuna kadar devam eder, x-mode yorumu işaretler. Bu yapı kullanmak için Etkinleştir'i gerekir `x` seçeneğini (satır içi seçenekleri) veya tedarik <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> değerini `option` örneği oluşturulurken parametre <xref:System.Text.RegularExpressions.Regex> nesne veya statik bir çağırma <xref:System.Text.RegularExpressions.Regex> yöntemi.  
  
 Aşağıdaki örnekte, satır sonu yorum yapısı gösterilmektedir. Bu, bir dize en az bir biçim öğesi içeren bir bileşik biçimlendirme dizesi olup olmadığını belirler. Aşağıdaki tablo, normal ifade deseninde yapıları açıklar:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\{`|Bir açılış ayracı eşleşmesi.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`(,-*\d+)*`|Bir veya daha fazla ondalık basamak gelen bir isteğe bağlı eksi işareti, ardından virgül, sıfır veya bir oluşumunu eşleştirin.|  
|`(\:\w{1,4}?)*`|Bir ile dört ama olabildiğince az olabildiğince, boşluk karakterlerinin izlediği bir virgül, sıfır veya bir oluşumunu eşleştirin.|  
|`\}`|Bir kapanış ayracı eşleşmesi.|  
|`(?x)`|Satır sonu yorum tanınması yoksay deseni boşluk seçeneğini etkinleştirin.|  
|`# Looks for a composite format item.`|Bir satır sonu açıklama.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Sağlamak yerine Not `(?x)` oluşturmak içindeki bir normal ifade, açıklama da çağırarak kabul edilmemiş <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi ve geçirerek <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> numaralandırma değeri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
