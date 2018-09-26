---
title: 'Normal İfade Örneği: Tarih Biçimlerini Değiştirme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8c26608115a22a5402d671c5f5e51c75442a0a5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108903"
---
# <a name="regular-expression-example-changing-date-formats"></a>Normal İfade Örneği: Tarih Biçimlerini Değiştirme
Aşağıdaki kod örneğinde <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> formu tarihleri yönteminin *mm*/*GG*/*yy* ile tarihleri Formun *GG*-*mm*-*yy*.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Aşağıdaki kodda gösterildiği nasıl `MDYToDMY` yöntemi, uygulamada çağrılabilir.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Açıklamalar  
 Normal ifade deseni `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?<month>\d{1,2})`|Bir veya iki ondalık basamağı eşleştirin. Bu `month` yakalanan grubu.|  
|`/`|Eğik çizgi işareti eşleştirin.|  
|`(?<day>\d{1,2})`|Bir veya iki ondalık basamağı eşleştirin. Bu `day` yakalanan grubu.|  
|`/`|Eğik çizgi işareti eşleştirin.|  
|`(?<year>\d{2,4})`|Dört ondalık basamak için ikisinden eşleştirin. Bu `year` yakalanan grubu.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Desen `${day}-${month}-${year}` değiştirme dizesi aşağıdaki tabloda gösterildiği gibi tanımlar.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`$(day)`|Tarafından yakalanan dizesi eklemek `day` yakalama grubu.|  
|`-`|Bir kısa çizgi ekleyin.|  
|`$(month)`|Tarafından yakalanan dizesi eklemek `month` yakalama grubu.|  
|`-`|Bir kısa çizgi ekleyin.|  
|`$(year)`|Tarafından yakalanan dizesi eklemek `year` yakalama grubu.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
