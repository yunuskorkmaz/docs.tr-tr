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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138729"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma
Aşağıdaki örnek, bir URL'den bir protokol ve bağlantı noktası numarası ayıklar.  
  
## <a name="example"></a>Örnek  
 Örnek, bağlantı <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> noktası numarası nın ardından bir nokta üst üste gelen protokolü döndürmek için yöntemi kullanır.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Normal ifade `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` deseni aşağıdaki tabloda gösterildiği gibi yorumlanabilir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Dize başında maç başlayın.|  
|`(?<proto>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu gruba `proto`isim verem.|  
|`://`|Bir iki nokta üst üste iki eğik çizgi işaretiyle eşleştirin.|  
|`[^/]+?`|Eğik çizgi işareti dışında herhangi bir karakterin bir veya daha fazla oluşumunu (ancak mümkün olduğunca az) eşleştirin.|  
|`(?<port>:\d+)?`|Bir veya daha fazla basamak lı karakter tarafından izlenen bir iki nokta üst üste sıfır veya bir oluşum eşleştirin. Bu gruba `port`isim verem.|  
|`/`|Eğik çizgi işaretini eşleştirin.|  
  
 Yöntem, <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> normal `${proto}${port}` ifade deseninde yakalanan iki adlandırılmış grubun değerini biraraya getiren değiştirme sırasını genişletir. Özellik tarafından döndürülen koleksiyon nesnesinden alınan dizeleri açıkça bağlamak <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> için kullanışlı bir alternatiftir.  
  
 Örnek, `${proto}` yakalanan grupları çıktı dizesine `${port}`dahil etmek için iki değişiklik le <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi kullanır. Yakalanan grupları aşağıdaki kodun gösterdiği <xref:System.Text.RegularExpressions.GroupCollection> gibi, bunun yerine eşleşmenin nesnesinden alabilirsiniz.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Düzenli İfadeler](../../../docs/standard/base-types/regular-expressions.md)
