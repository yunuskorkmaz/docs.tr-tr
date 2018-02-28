---
title: "Normal İfade Örneği: HREF Tarama"
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
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6592647ab3ff133bceb05b9ee84ce794e41aaf13
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2018
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Normal İfade Örneği: HREF Tarama
Aşağıdaki örnek giriş dizesi arar ve görüntüler tüm href = "..." değerlerini ve konumlarına dize.  
  
## <a name="the-regex-object"></a>Regex Nesnesi  
 Çünkü `DumpHRefs` yöntemi çağrılabilir birden çok kez kullanıcı kodundan, kullandığı `static` (`Shared` Visual Basic'te) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi. Bu normal ifade önbelleğe almak normal ifade altyapısı sağlar ve yeni bir örneği, yüke engel <xref:System.Text.RegularExpressions.Regex> nesne her zaman yöntemi çağrılır. A <xref:System.Text.RegularExpressions.Match> nesnesi dizesindeki tüm eşleşmeleri yinelemek için sonra kullanılır.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Aşağıdaki örnekte, ardından bir çağrı gösterilmektedir `DumpHRefs` yöntemi.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Normal ifade deseni `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`href`|"Href" değişmez değer dize eşleşmesi. Eşleşme büyük/küçük harf duyarlıdır.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`=`|Eşittir işareti ile aynı.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|<code>(?:\["'\](?<1>\[^"'\]*)"&#124;(?<1>\S+))</code>|Aşağıdakilerden birini yakalanan bir gruba sonucu atamadan eşleştir:<br /> <ul><li><p>Tırnak işareti veya tırnak işareti veya kesme işareti, bir tırnak işareti veya kesme işareti gelmelidir dışındaki herhangi bir karakter, sıfır veya daha fazla tekrarı ve ardından kesme işareti. Adlı grup `1` bu modelinde eklenmiştir.</p></li><li><p>Bir veya daha fazla boşluk olmayan karakter. Adlı grup `1` bu modelinde eklenmiştir.</p></li></ul>|  
|`(?<1>[^"']*)`|Tırnak işareti veya kesme işareti dışındaki herhangi bir karakter, sıfır veya daha fazla tekrarı adlı yakalama grubuna atayın `1`.|  
|`"(?<1>\S+)`|Bir veya daha fazla boşluk olmayan karakter adlı yakalama grubuna atayın `1`.|  
  
## <a name="match-result-class"></a>Sonuç Sınıfını Eşleştirme  
 Arama sonuçlarını depolanmış <xref:System.Text.RegularExpressions.Match> aramada ayıklanan tüm alt dizeler erişim sağlayan sınıf. Bunu çağırması, ayrıca Aranmakta dize ve kullanılan, normal ifade hatırlıyor <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> başka bir arama burada sonuncu sona erdi başlangıç yapmak için yöntemi.  
  
## <a name="explicitly-named-captures"></a>Açıkça Adlandırılmış Yakalamalar  
 Geleneksel normal ifadelerde yakalama parantez otomatik olarak ardışık olarak numaralandırılır. Bu iki sorunlara yol açar. Normal bir ifade ekleme veya bir dizi parantez kaldırarak değiştirilirse, ilk olarak, numaralandırılmış yakalamaları başvuran tüm kod yeni numaralandırma yansıtacak şekilde yazılması gerekir. İkinci olarak, genellikle farklı ayarlar parantez kabul edilebilir bir eşleşme için iki alternatif ifadeler sağlamak için kullanıldığından, iki ifadeye hangisinin gerçekte bir sonuç döndürdü belirlemek zor olabilir.  
  
 Bu sorunları gidermek için <xref:System.Text.RegularExpressions.Regex> sınıfı destekler söz dizimi `(?<name>…)` bir eşleşme belirtilen yuvaya yakalamak için (bir string veya tamsayı kullanarak yuvaya adlandırılabilir; tamsayılar geri daha hızlı). Bu nedenle, tüm aynı yerde yönlendirilebilir aynı dize için alternatif eşleşir. Bir çakışma durumunda bir yuvaya bırakılan son başarılı eşleşme eşleşmedir. (Ancak, tek bir yuva için birden çok eşleşen tam bir listesi kullanılabilir. Bkz: <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> ayrıntıları toplamalarında.)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
