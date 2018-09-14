---
title: "Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma"
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
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a08e97b02e2f60422132e97e2f3f7d4d2d5b8ec4
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45507920"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma
Aşağıdaki örnek, bir URL'den protokol ve bağlantı noktası numarası ayıklar.  
  
## <a name="example"></a>Örnek  
 Örnekte <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> bağlantı noktası numarası ile üste arkasından Protokolü döndürmek için yöntemi.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Normal ifade deseni `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` aşağıdaki tabloda gösterildiği gibi yorumlanabilir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Dizesinin başında eşleşmeye başla.|  
|`(?<proto>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu gruba adını `proto`.|  
|`://`|Üste iki eğik çizgi işaretleriyle eşleş.|  
|`[^/]+?`|Bir veya daha çok tekrarı (ama olabildiğince az sayıda) eğik çizgi işareti dışındaki herhangi bir karakterle eşleş.|  
|`(?<port>:\d+)?`|Bir veya daha fazla basamak karakterleri üste sıfır veya bir oluşumunu eşleştirin. Bu gruba adını `port`.|  
|`/`|Bir eğik çizgi işareti eşleştirin.|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Yöntemi genişletir `${proto}${port}` değeri normal ifade deseninde yakalanan iki adlandırılmış gruplar, sıralar değiştirme dizisi. Açıkça tarafından döndürülen koleksiyon nesnesinden alınan dizeleri birleştirirken için kullanışlı bir alternatiftir <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği.  
  
 Örnekte <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> iki değişimler yöntemiyle `${proto}` ve `${port}`, çıktı dizesinde yakalanan gruplar eklemek için. Eşleşmeden 's yakalanan gruplar alabilirsiniz <xref:System.Text.RegularExpressions.GroupCollection> bunun yerine, aşağıdaki kodun gösterdiği nesne.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
