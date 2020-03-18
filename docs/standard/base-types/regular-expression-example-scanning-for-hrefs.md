---
title: 'Normal İfade Örneği: HREF Tarama'
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
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
ms.openlocfilehash: d8546980dd0cf58ca7c095750f2749d5a6bc7723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084219"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Normal İfade Örneği: HREF Tarama
Aşağıdaki örnekbir giriş dizesini arar ve tüm href="..." değerleri ve konumlarını dize.  
  
## <a name="the-regex-object"></a>Regex Nesnesi  
 Yöntem kullanıcı kodundan birden çok kez çağrılabildiği`Shared` için, <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> `static` (Visual Basic'te) yöntemini kullanır. `DumpHRefs` Bu, normal ifade altyapısının normal ifadeyi önbelleğe almamasını sağlar ve <xref:System.Text.RegularExpressions.Regex> yöntem her çağrıldığında yeni bir nesnenin anlık olarak anlık olarak yapılmasını önler. Bir <xref:System.Text.RegularExpressions.Match> nesne daha sonra dizedeki tüm eşleşmeleri yinelemek için kullanılır.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Aşağıdaki örnekte yönteme `DumpHRefs` bir çağrı gösterilir.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Normal ifade `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`href`|"Href" dizesini eşleştirin. Eşleşme büyük/küçük bir ihtimal duyarsız.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`=`|Eşitler işaretini eşleştirin.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`(?:\["'\](?<1>\[^"'\]*)["']|(?<1>\S+))`|Sonucu yakalanan gruba atamadan aşağıdakilerden birini eşleştirin:<br /> <ul><li><p>Bir tırnak işareti veya apostrophe, ardından bir tırnak işareti veya apostrophe dışında herhangi bir karakterin sıfır veya daha fazla oluşumları, ardından bir tırnak işareti veya apostrophe. Adlandırılmış `1` grup bu desene dahildir.</p></li><li><p>Bir veya daha fazla beyaz boşluk olmayan karakter. Adlandırılmış `1` grup bu desene dahildir.</p></li></ul>|  
|`(?<1>[^"']*)`|Bir tırnak işareti veya apostrophe dışında herhangi bir karakterin sıfır veya daha `1`fazla oluşumlarını yakalama grubuna ata.|  
|`(?<1>\S+)`|Bir veya daha fazla beyaz boşluk olmayan karakteri yakalama `1`grubuna ata.|  
  
## <a name="match-result-class"></a>Sonuç Sınıfını Eşleştirme  
 Bir aramanın sonuçları, arama <xref:System.Text.RegularExpressions.Match> tarafından çıkarılan tüm alt dizeleri erişim sağlayan sınıfta depolanır. Ayrıca aranmakta olan dize yi ve kullanılan normal ifadeyi <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> hatırlar, böylece sonuncusunun bittiği yerden başlayarak başka bir arama gerçekleştirme yöntemini arayabilir.  
  
## <a name="explicitly-named-captures"></a>Açıkça Adlandırılmış Yakalamalar  
 Geleneksel normal ifadelerde, yakalama parantezleri otomatik olarak sırayla numaralandırılır. Bu iki soruna yol açar. İlk olarak, normal bir ifade bir parantez kümesi ekleyerek veya kaldırarak değiştirilirse, numaralanmış yakalamalara başvuran tüm kodlar yeni numaralandırmayı yansıtacak şekilde yeniden yazılmalıdır. İkinci olarak, farklı parantez kümeleri genellikle kabul edilebilir bir eşleşme için iki alternatif ifade sağlamak için kullanıldığından, iki ifadeden hangisinin aslında bir sonucu döndüreceğini belirlemek zor olabilir.  
  
 Bu sorunları gidermek <xref:System.Text.RegularExpressions.Regex> için sınıf, `(?<name>…)` eşleşmeyi belirli bir yuvaya yakalamak için sözdizimini destekler (yuva bir dize veya tamsayı kullanılarak adlandırılabilir; tamsayılar daha hızlı geri çağrılabilir). Böylece, aynı dize için alternatif eşleşmeler tüm aynı yere yönlendirilebilir. Bir çakışma durumunda, son maç bir yuvaya düştü başarılı bir maç. (Ancak, tek bir yuva için birden çok eşleşmenin tam listesi kullanılabilir. Ayrıntılar <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> için koleksiyona bakın.)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Düzenli İfadeler](../../../docs/standard/base-types/regular-expressions.md)
