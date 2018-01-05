---
title: "Normal İfadelerdeki Çeşitli Yapılar"
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
- constructs, miscellaneous
- .NET Framework regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7a7c577c617ca8f40d64548f9f0f2d103c5887e1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Normal İfadelerdeki Çeşitli Yapılar
.NET normal ifadelerde üç çeşitli dil yapıları içerir. Bir etkinleştirmek veya normal ifade deseni ortasında belirli eşleştirme seçenekleri devre dışı bırakmanızı sağlar. İki kalan normal ifadede açıklamalar dahil olanak tanır.  
  
## <a name="inline-options"></a>Satır içi seçenekleri  
 Ayarlayın veya belirli bir desene sözdizimini kullanarak eşleştirme için normal bir ifade parçası seçeneklerini devre dışı bırakma  
  
```  
(?imnsx-imnsx)  
```  
  
 Soru işareti sonra etkinleştirmek istediğiniz seçenekleri ve eksi sonra devre dışı bırakmak istediğiniz seçenekleri listeleyin. Aşağıdaki tabloda her bir seçenek açıklanmaktadır. Her bir seçenek hakkında daha fazla bilgi için bkz: [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`i`|Büyük küçük harf duyarsız eşleşen.|  
|`m`|Çok satırlı modu.|  
|`n`|Yalnızca açık yakalar. (Parantez yok davranan grupları yakalama olarak.)|  
|`s`|Tek satırlı modu.|  
|`x`|Atlanmayan boşluk yoksay ve x modu açıklamalara izin verme.|  
  
 Normal ifade seçenekleri tarafından tanımlanan herhangi bir değişikliği `(?imnsx-imnsx)` kapsayan grubun sonuna kadar etkin kalır oluşturun.  
  
> [!NOTE]
>  `(?imnsx-imnsx:` *Alt* `)` gruplama yapısı için bir alt aynı işlevselliği sağlar. Daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Aşağıdaki örnek kullanır `i`, `n`, ve `x` seçenekleri büyük/küçük harfe ve açık yakalamaları etkinleştirin ve normal bir ifade ortasında normal ifade deseni boşluk yoksay.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 Örneğin, iki normal ifadeler tanımlar. İlk `\b(D\w+)\s(d\w+)\b`, "D" bir büyük harf ve küçük harf "d" ile başlayan iki ardışık sözcük eşleşir. İkinci normal ifade `\b(D\w+)(?ixn) \s (d\w+) \b`, aşağıdaki tabloda açıklandığı gibi bu deseni değiştirmek için satır içi seçeneklerini kullanır. Sonuçları karşılaştırması etkisini onaylar `(?ixn)` oluşturun.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(D\w+)`|Büyük harf "bir veya daha fazla word karakterle devam etmelidir D" eşleşir. Bu ilk yakalama grubudur.|  
|`(?ixn)`|Bu noktasında, büyük küçük harf duyarsız yapma karşılaştırmaları, yalnızca açık olun yakalar ve normal ifade deseni boşluk yoksay.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(d\w+)`|Eşleşen bir büyük veya küçük harf "d" bir veya daha fazla word karakterle devam etmelidir. Bu grup, çünkü sayılmaz `n` (açık yakalama) seçeneği etkinleştirilmiş...|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
## <a name="inline-comment"></a>Satır içi açıklama  
 `(?#` *Açıklama* `)` yapı normal ifadede bir satır içi açıklama eklemek olanak sağlar. Normal ifade altyapısı tarafından döndürülen dize açıklama bulunmaktadır ancak desen eşleştirme, açıklaması, herhangi bir bölümünü kullanmaz <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> yöntemi. Açıklama ilk kapanış parantezinde sona erer.  
  
 Aşağıdaki örnek, önceki bölümde örneğindeki ilk normal ifade deseni tekrarlar. İki satır içi açıklamalar karşılaştırma büyük küçük harfe duyarlı olup olmadığını belirtmek için normal ifade ekler. Normal ifade deseni `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b`, aşağıdaki gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?# case-sensitive comparison)`|Bir yorum. Desen eşleştirme davranışını etkilemez.|  
|`(D\w+)`|Büyük harf "bir veya daha fazla word karakterle devam etmelidir D" eşleşir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(?ixn)`|Bu noktasında, büyük küçük harf duyarsız yapma karşılaştırmaları, yalnızca açık olun yakalar ve normal ifade deseni boşluk yoksay.|  
|`(?#case-insensitive comparison)`|Bir yorum. Desen eşleştirme davranışını etkilemez.|  
|`(d\w+)`|Eşleşen bir büyük veya küçük harf "d" bir veya daha fazla word karakterle devam etmelidir. Bu ikinci bir yakalama grubudur.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Satır sonu açıklama  
 Sayı işareti (`#`) normal ifade deseni sonunda atlanmayan # karakteri başlar ve satırın sonuna kadar devam x modu yorum işaretler. Bu yapıyı kullanmak için Etkinleştir'i gerekir `x` seçeneği (satır içi seçenekleri) veya kaynağı <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> değeri `option` başlatılırken parametresi <xref:System.Text.RegularExpressions.Regex> nesnesi veya bir statik çağırma <xref:System.Text.RegularExpressions.Regex> yöntemi.  
  
 Aşağıdaki örnek, satır sonu açıklama yapı gösterilmektedir. Bu bir dize en az bir biçim öğesi içeren bileşik biçim dizesi olup olmadığını belirler. Aşağıdaki tabloda, normal ifade deseni yapılardan açıklanmaktadır:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\{`|Açılan parantez eşleşir.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`(,-*\d+)*`|Bir veya daha fazla ondalık basamak ile izlenen isteğe bağlı bir eksi işareti, arkasından virgül, sıfır veya bir örneğini Bul.|  
|`(\:\w{1,4}?)*`|Sıfır veya bir geçişi dörde ancak olabildiğince az olabildiğince, boşluk karakterleri tarafından üste ile eşleşir.|  
|`(?#case insensitive comparison)`|Satır içi bir yorum. Desen eşleştirme davranışı üzerinde bir etkisi yoktur.|  
|`\}`|Kapatılan parantez eşleşir.|  
|`(?x)`|Böylece satır sonu açıklama tanınan yoksay düzeni boşluk seçeneğini etkinleştirin.|  
|`# Looks for a composite format item.`|Bir satır sonu açıklaması.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Sağlama yerine Not `(?x)` oluşturmak normal ifadede açıklama da çağırarak kabul edilmemiş <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi ve onu <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> numaralandırma değeri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
