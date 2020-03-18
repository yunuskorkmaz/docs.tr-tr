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
ms.openlocfilehash: 358e26957747073fec9dfe9eb0d404cb438afaf9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084189"
---
# <a name="regular-expression-example-changing-date-formats"></a>Normal İfade Örneği: Tarih Biçimlerini Değiştirme
Aşağıdaki kod örneği, <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> *dd*-*mm*-yy formuna sahip tarihler ile *mm*/*dd*/*yy* formuna sahip tarihleri değiştirmek için yöntemi kullanır.*yy*  
  
## <a name="example"></a>Örnek  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Aşağıdaki kod, yöntemin `MDYToDMY` bir uygulamada nasıl çağrılabileceğini gösterir.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Yorumlar  
 Normal ifade `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?<month>\d{1,2})`|Bir veya iki ondalık basamak eşleştirin. Bu `month` yakalanan grup.|  
|`/`|Eğik çizgi işaretiyle eşleştirin.|  
|`(?<day>\d{1,2})`|Bir veya iki ondalık basamak eşleştirin. Bu `day` yakalanan grup.|  
|`/`|Eğik çizgi işaretiyle eşleştirin.|  
|`(?<year>\d{2,4})`|İki ila dört ondalık basamak eşleştirin. Bu `year` yakalanan grup.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Desen, `${day}-${month}-${year}` aşağıdaki tabloda gösterildiği gibi değiştirme dizesini tanımlar.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`$(day)`|`day` Yakalama grubu tarafından yakalanan dize ekleyin.|  
|`-`|Tire ekle.|  
|`$(month)`|`month` Yakalama grubu tarafından yakalanan dize ekleyin.|  
|`-`|Tire ekle.|  
|`$(year)`|`year` Yakalama grubu tarafından yakalanan dize ekleyin.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Düzenli İfadeler](../../../docs/standard/base-types/regular-expressions.md)
