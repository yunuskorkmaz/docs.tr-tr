---
title: "Normal İfade Örneği: Tarih Biçimlerini Değiştirme"
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
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 93c526e87f7aba650cce397962c7262b6fd2f085
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="regular-expression-example-changing-date-formats"></a>Normal İfade Örneği: Tarih Biçimlerini Değiştirme
Aşağıdaki kod örneğinde <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> formu tarihleri değiştirmek için yöntemi *mm*/*GG*/*yy* ile tarihleri Formun *GG*-*mm*-*yy*.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Aşağıdaki kodda gösterildiği nasıl `MDYToDMY` bir uygulamada yöntemi çağrılabilir.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Açıklamalar  
 Normal ifade deseni `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?<month>\d{1,2})`|Bir veya iki ondalık basamak eşleşir. Bu `month` yakalanan grubu.|  
|`/`|Eğik çizgi işareti eşleşir.|  
|`(?<day>\d{1,2})`|Bir veya iki ondalık basamak eşleşir. Bu `day` yakalanan grubu.|  
|`/`|Eğik çizgi işareti eşleşir.|  
|`(?<year>\d{2,4})`|İki dört ondalık basamak eşleşir. Bu `year` yakalanan grubu.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Desen `${day}-${month}-${year}` aşağıdaki tabloda gösterildiği gibi değiştirme dizesini tanımlar.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`$(day)`|Tarafından yakalanan dizesi eklemek `day` Grup yakalama.|  
|`-`|Bir tire ekleyin.|  
|`$(month)`|Tarafından yakalanan dizesi eklemek `month` Grup yakalama.|  
|`-`|Bir tire ekleyin.|  
|`$(year)`|Tarafından yakalanan dizesi eklemek `year` Grup yakalama.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
