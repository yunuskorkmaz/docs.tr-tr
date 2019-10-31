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
ms.openlocfilehash: f2704e3fb5ceb68609a475d52e11030177ad760b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138729"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma
Aşağıdaki örnek bir URL 'den protokol ve bağlantı noktası numarası ayıklar.  
  
## <a name="example"></a>Örnek  
 Örnek, ardından bağlantı noktası numarasını izleyen bir iki nokta üst üste gelen kuralı döndürmek için <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemini kullanır.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` normal ifade deseninin aşağıdaki tabloda gösterildiği gibi yorumlanması gösterilebilir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Dizenin başlangıcında eşleşmeyi başlatın.|  
|`(?<proto>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu grubun `proto`adlandırın.|  
|`://`|İki nokta üst üste ve ardından iki eğik çizgi ile eşleştirin.|  
|`[^/]+?`|Eğik çizgi işareti dışında herhangi bir karakterin bir veya daha fazla tekrarı (mümkün olan en az sayıda) eşleştirin.|  
|`(?<port>:\d+)?`|İki nokta üst üste ve ardından bir veya daha fazla rakam karakteri ile eşleşen sıfır veya bir oluşumu eşleştirin. Bu grubun `port`adlandırın.|  
|`/`|Eğik çizgi işaretiyle eşleştirin.|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi, normal ifade modelinde yakalanan iki adlandırılmış grubun değerini birleştiren `${proto}${port}` değiştirme sırasını genişletir. <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği tarafından döndürülen koleksiyon nesnesinden alınan dizeleri açıkça birleştirerek kullanışlı bir alternatiftir.  
  
 Örnek, <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemini, `${proto}` ve `${port}`olmak üzere iki değişim ile kullanır. Bu, yakalanan grupları çıkış dizesine dahil eder. Aşağıdaki kodun gösterdiği gibi, eşleşme <xref:System.Text.RegularExpressions.GroupCollection> nesnesinden yakalanan grupları alabilirsiniz.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal Ifadeleri](../../../docs/standard/base-types/regular-expressions.md)
