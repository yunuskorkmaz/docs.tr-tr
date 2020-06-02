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
ms.openlocfilehash: 48f2bf5c0d9af0a3fc286561ba978f86d1f11ac8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290493"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Nasıl yapılır: Bir URL'den Protokol ve Bağlantı Noktası Numarası Çıkarma
Aşağıdaki örnek bir URL 'den protokol ve bağlantı noktası numarası ayıklar.  
  
## <a name="example"></a>Örnek  
 Örnek, <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> iletişim kuralını ve ardından bağlantı noktası numarasını döndürmek için yöntemini kullanır.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Normal ifade deseninin `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` Aşağıdaki tabloda gösterildiği gibi yorumlanması gösterilebilir.  
  
|Desen|Description|  
|-------------|-----------------|  
|`^`|Dizenin başlangıcında eşleşmeyi başlatın.|  
|`(?<proto>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu grubu adlandırın `proto` .|  
|`://`|İki nokta üst üste ve ardından iki eğik çizgi ile eşleştirin.|  
|`[^/]+?`|Eğik çizgi işareti dışında herhangi bir karakterin bir veya daha fazla tekrarı (mümkün olan en az sayıda) eşleştirin.|  
|`(?<port>:\d+)?`|İki nokta üst üste ve ardından bir veya daha fazla rakam karakteri ile eşleşen sıfır veya bir oluşumu eşleştirin. Bu grubu adlandırın `port` .|  
|`/`|Eğik çizgi işaretiyle eşleştirin.|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>Yöntemi, `${proto}${port}` normal ifade modelinde yakalanan iki adlandırılmış grubun değerini birleştiren değiştirme sırasını genişletir. Özelliği tarafından döndürülen koleksiyon nesnesinden alınan dizeleri açıkça birleştirerek kullanışlı bir alternatiftir <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> .  
  
 Örnek, <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi iki değiştirme ile birlikte kullanır `${proto}` ve `${port}` yakalanan grupları çıkış dizesine dahil eder. <xref:System.Text.RegularExpressions.GroupCollection>Aşağıdaki kodun gösterdiği gibi, eşleşme nesnesinden yakalanan grupları elde edebilirsiniz.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal Ifadeleri](regular-expressions.md)
