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
ms.openlocfilehash: 4290bf0d6ee9deec8129c5f4f6092eedb08345f0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276185"
---
# <a name="regular-expression-example-changing-date-formats"></a>Normal İfade Örneği: Tarih Biçimlerini Değiştirme
Aşağıdaki kod örneği, <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> *AA* / *gg* / *yy* biçimindeki tarihleri *gg* - *AA* - *yy*olan tarihlerle değiştirmek için yöntemini kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Aşağıdaki kod, `MDYToDMY` yönteminin bir uygulamada nasıl çağrılabilecek olduğunu gösterir.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Yorumlar  
 Normal ifade deseninin `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?<month>\d{1,2})`|Bir veya iki ondalık basamağı eşleştirin. Bu, `month` yakalanan gruptur.|  
|`/`|Eğik çizgi işaretiyle eşleştirin.|  
|`(?<day>\d{1,2})`|Bir veya iki ondalık basamağı eşleştirin. Bu, `day` yakalanan gruptur.|  
|`/`|Eğik çizgi işaretiyle eşleştirin.|  
|`(?<year>\d{2,4})`|İki ile dört ondalık basamağa eşleştirin. Bu, `year` yakalanan gruptur.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Bu model, `${day}-${month}-${year}` Aşağıdaki tabloda gösterildiği gibi değiştirme dizesini tanımlar.  
  
|Desen|Description|  
|-------------|-----------------|  
|`$(day)`|Yakalama grubu tarafından yakalanan dizeyi ekleyin `day` .|  
|`-`|Kısa çizgi ekleyin.|  
|`$(month)`|Yakalama grubu tarafından yakalanan dizeyi ekleyin `month` .|  
|`-`|Kısa çizgi ekleyin.|  
|`$(year)`|Yakalama grubu tarafından yakalanan dizeyi ekleyin `year` .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal Ifadeleri](regular-expressions.md)
