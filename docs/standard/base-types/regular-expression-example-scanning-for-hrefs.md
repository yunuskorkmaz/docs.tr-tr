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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6fe667ca908b2a4ba16e34e8e74dd39ca01f153
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203650"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Normal İfade Örneği: HREF Tarama
Aşağıdaki örnek, bir Giriş dizesinin arar ve görüntüler veya href = "..." değerleri ve konumlarına dize.  
  
## <a name="the-regex-object"></a>Regex Nesnesi  
 Çünkü `DumpHRefs` yöntemi çağrıldığında birden çok kez kullanıcı kodundan, kullandığı `static` (`Shared` Visual Basic'te) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> yöntemi. Bu normal ifade altyapısının normal ifade önbellekte sağlar ve yeni bir örnekleme ek yükü ortadan kaldırır <xref:System.Text.RegularExpressions.Regex> nesne her zaman yöntemi çağrılır. A <xref:System.Text.RegularExpressions.Match> nesne ardından dizedeki tüm eşleşmeleri yinelemek için kullanılır.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Aşağıdaki örnekte, ardından bir çağrı gösterilmektedir `DumpHRefs` yöntemi.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Normal ifade deseni `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`href`|"Href =" sabit dizesini eşleştirin. Eşleşme büyük/küçük harf duyarlıdır.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`=`|Eşittir işareti eşleyin.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|<code>(?:\["'\](?<1>\[^"'\]*)["']&#124;(?<1>\S+))</code>|Aşağıdakilerden birini bir yakalanan gruba sonucu atamadan eşleşmesi:<br /> <ul><li><p>Tırnak işareti veya kesme işareti, tırnak işareti veya kesme işareti, tırnak işareti veya kesme işareti tarafından izlenen dışındaki herhangi bir karakter sıfır veya daha çok tekrarı ardından. Adlı grubu `1` Bu düzende dahildir.</p></li><li><p>Bir veya daha fazla boşluk olmayan karakter. Adlı grubu `1` Bu düzende dahildir.</p></li></ul>|  
|`(?<1>[^"']*)`|Adlandırılmış yakalama grubu için tırnak işareti veya kesme işareti dışındaki herhangi bir karakterin sıfır veya daha çok tekrarı atama `1`.|  
|`(?<1>\S+)`|Adlandırılmış yakalama grubu için bir veya daha fazla boşluk olmayan karakterle atama `1`.|  
  
## <a name="match-result-class"></a>Sonuç Sınıfını Eşleştirme  
 Bir aramanın sonuçları depolanan <xref:System.Text.RegularExpressions.Match> aramada ayıklanan tüm alt dizeler erişim sağlayan sınıf. Bunu çağırabilirsiniz, ayrıca Aranan dize ve kullanılan, normal ifade hatırlar <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> başka bir arama sonuncu burada sona erdi başlangıç yapmak için yöntemi.  
  
## <a name="explicitly-named-captures"></a>Açıkça Adlandırılmış Yakalamalar  
 Geleneksel normal ifadelerde yakalama parantez otomatik olarak ardışık olarak numaralandırılır. Bu iki sorunlara yol açar. Normal bir ifade ekleme veya kaldırma parantez kümesi değiştirilirse, ilk olarak, numaralandırılmış yakalama için başvuran tüm kodlar yeni numaralandırmalara yansıtacak şekilde yazılması gerekir. İkinci olarak, genellikle farklı ayarlar parantez iki alternatif ifadeleri kabul edilebilir bir eşleşme sağlamak için kullanıldığından, iki ifadeden aslında bir sonuç döndürdü saptamak zor olabilir.  
  
 Bu sorunları gidermeye yönelik <xref:System.Text.RegularExpressions.Regex> sınıfı sözdizimi destekler `(?<name>…)` bir eşleşmenin belirtilen yuvaya yakalanması için (bir dize veya tamsayı kullanarak yuvaya adlandırılabilir; tamsayılar geri daha hızlı). Bu nedenle, tüm aynı yere yönlendirilebilir aynı dize için alternatif eşleşir. Bir çakışma olması durumunda bir yuvaya bırakılan son eşleşmenin başarılı eşleşmedir. (Ancak, tek bir yuva için birden fazla eşleşme tam listesi kullanılabilir. Bkz: <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> koleksiyon için ayrıntıları.)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
