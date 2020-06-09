---
title: 'Normal İfade Örneği: HREF Tarama'
description: .NET 'teki normal ifadeler örneğine bakın. Örnek, bir giriş dizesini arar ve tüm href öznitelik değerlerini ve konumlarını görüntüler.
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
ms.openlocfilehash: 36273901ac9afb762ac70ee5d6dcd80ff0ede11d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583498"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Normal İfade Örneği: HREF Tarama
Aşağıdaki örnek bir giriş dizesini arar ve tüm href = "..." değerler ve dizedeki konumları.  
  
## <a name="the-regex-object"></a>Regex Nesnesi  
 `DumpHRefs`Yöntemi kullanıcı kodundan birden çok kez çağrabileceğinden, `static` ( `Shared` Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemini kullanır. Bu, normal ifade altyapısının normal ifadeyi önbelleğe almasını sağlar ve <xref:System.Text.RegularExpressions.Regex> yöntemin her çağrılışında yeni bir nesne örneği oluşturma yükünü önler. Bir <xref:System.Text.RegularExpressions.Match> nesne daha sonra dizedeki tüm eşleşmeler arasında yineleme yapmak için kullanılır.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Aşağıdaki örnek daha sonra yöntemine bir çağrı gösterir `DumpHRefs` .  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Normal ifade deseninin `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`href`|"Href" değişmez dizesini eşleştirin. Eşleşme büyük/küçük harfe duyarsızdır.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`=`|Eşittir işaretine eşleştirin.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`(?:\["'\](?<1>\[^"'\]*)["']|(?<1>\S+))`|Sonucu yakalanan bir gruba atamadan aşağıdakilerden birini eşleştirin:<br /> <ul><li><p>Tırnak işareti veya kesme işareti, ardından tırnak işareti veya kesme işareti dışında herhangi bir karakterin ardından sıfır veya daha fazla tekrardan oluşan tırnak işareti veya kesme işareti. Adlı grup `1` Bu modele dahildir.</p></li><li><p>Bir veya daha fazla boşluk olmayan karakter. Adlı grup `1` Bu modele dahildir.</p></li></ul>|  
|`(?<1>[^"']*)`|Adlı yakalama grubuna tırnak işareti veya kesme işareti dışında herhangi bir karakterin sıfır veya daha fazla örneğini atayın `1` .|  
|`(?<1>\S+)`|Adlı yakalama grubuna bir veya daha fazla boşluk olmayan karakter atayın `1` .|  
  
## <a name="match-result-class"></a>Sonuç Sınıfını Eşleştirme  
 Bir aramanın sonuçları <xref:System.Text.RegularExpressions.Match> sınıfında depolanır ve bu, arama tarafından ayıklanan tüm alt dizelere erişim sağlar. Ayrıca, aranan dizeyi ve kullanılan normal ifadeyi anımsar ve bu sayede, <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> son birinin sona erdiği yerde başka bir arama gerçekleştirmek için yöntemini çağırabilir.  
  
## <a name="explicitly-named-captures"></a>Açıkça Adlandırılmış Yakalamalar  
 Geleneksel normal ifadelerde yakalama parantezleri otomatik olarak sıralı olarak numaralandırılır. Bu iki soruna yol açar. İlk olarak, bir normal ifade bir parantez kümesi eklenerek veya kaldırılarak değiştirilirse, numaralandırılmış yakalamalara başvuran tüm kodların yeni numaralandırmayı yansıtacak şekilde yeniden yazılması gerekir. İkincisi, kabul edilebilir bir eşleşme için iki alternatif ifade sağlamak üzere genellikle farklı parantezler kümesi kullanıldığından, bu iki ifadenin hangisinin gerçekten sonuç döndürdüğünden belirlenmesi zor olabilir.  
  
 Bu sorunları gidermek için, <xref:System.Text.RegularExpressions.Regex> sınıfı `(?<name>…)` belirtilen bir yuvaya eşleşme yakalama sözdizimini destekler (yuva bir dize veya tamsayı kullanılarak adlandırılabilir; tamsayılar daha hızlı bir şekilde eklenebilir). Bu nedenle, hepsi aynı dize için alternatif eşleşmeler aynı yere yönlendirilebilir. Bir çakışma olması durumunda, bir yuvaya bırakılan son eşleşme, başarılı eşleşmedir. (Ancak, tek bir yuva için birden fazla eşleşme listesinin tamamı kullanılabilir. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>Ayrıntılar için koleksiyona bakın.)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal Ifadeleri](regular-expressions.md)
