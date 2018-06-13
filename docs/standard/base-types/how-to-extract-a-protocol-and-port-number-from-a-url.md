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
ms.openlocfilehash: ffb31030a2e29458165ae6615a51685ed163fbac
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32768482"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma
Aşağıdaki örnek, bir URL'den protokol ve bağlantı noktası numarası ayıklar.  
  
## <a name="example"></a>Örnek  
 Örnek kullanır <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Protokolü döndürülecek yöntemi tarafından bağlantı noktası numarası üste ve ardından.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Normal ifade deseni `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` aşağıdaki tabloda gösterildiği gibi yorumlanabilir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşleşme dizenin başında başlar.|  
|`(?<proto>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu grubun adı `proto`.|  
|`://`|İki eğik çizgi işareti tarafından üste eşleşir.|  
|`[^/]+?`|(Ancak mümkün olduğunca sayıda) bir veya daha fazla oluşumu bir eğik çizgi işareti dışında herhangi bir karakter ile aynı.|  
|`(?<port>:\d+)?`|Bir veya daha fazla rakamlı karakterleriyle üste sıfır veya bir örneğini Bul. Bu grubun adı `port`.|  
|`/`|Eğik çizgi işareti eşleşir.|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Yöntemi genişletir `${proto}${port}` değeri normal ifade deseni yakalanan iki adlandırılmış gruplar, sıralar değiştirme dizisi. Açıkça tarafından döndürülen koleksiyon nesnesi alınır dizeleri birleştirme için kullanışlı bir alternatiftir <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği.  
  
 Örnek kullanır <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> iki değişimler yöntemiyle `${proto}` ve `${port}`çıktı dizesine yakalanan gruplar eklemek için. Yakalanan gruplar eşleştirmeden 's alabilir <xref:System.Text.RegularExpressions.GroupCollection> nesne bunun yerine, aşağıdaki kodu gösterir.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
