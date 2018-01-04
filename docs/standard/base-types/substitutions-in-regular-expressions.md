---
title: "Normal İfadelerdeki Değişimler"
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
- regular expressions, substitutions
- replacement patterns
- metacharacters, substitutions
- .NET Framework regular expressions, substitutions
- constructs, substitutions
- substitutions
ms.assetid: d1f52431-1c7d-4dc6-8792-6b988256892e
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f93584b9dff721c8521d8cb58aaf5eab2c1fc931
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="substitutions-in-regular-expressions"></a>Normal İfadelerdeki Değişimler
<a name="Top"></a>Değişimler yalnızca değiştirme desenleri içinde tanınan dil öğelerdir. Giriş dizesinde eşleşen metnin yerini alacak metnin tümünü veya bir kısmını tanımlamak için normal bir ifade deseni kullanırlar. Değiştirme deseni, değişmez karakterlerin yanı sıra bir veya birden çok değiştirmeden oluşabilir. Değiştirme desenleri aşırı için sağlanan <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> sahip yöntemi bir `replacement` parametre ve <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi. Yöntemleri tarafından tanımlanan düzeni eşleşen düzeni yerine `replacement` parametresi.  
  
 .NET Framework, aşağıdaki tabloda listelenen değişim öğelerini tanımlar.  
  
|Değiştirme|Açıklama|  
|------------------|-----------------|  
|`$`*numarası*|Tarafından tanımlanan yakalama grubuna göre eşleşen son alt dizeyi içeren *numarası*, burada *numarası* değiştirme dizesi içinde ondalık bir değer. Daha fazla bilgi için bkz: [numaralı grup değiştirerek](#Numbered).|  
|`${`*adı*`}`|Tarafından belirlenen adlı gruba göre eşleşen son alt dizeyi içeren `(?<` *adı* `> )` değiştirme dizesi içinde. Daha fazla bilgi için bkz: [adlandırılmış Grup değiştirerek](#Named).|  
|`$$`|Değiştirme dizesinde tek bir "$" değişmez değerini içerir. Daha fazla bilgi için bkz: ["$" simgesi değiştirerek](#DollarSign).|  
|`$&`|Değiştirme dizesinde tüm eşleşmenin bir kopyasını içerir. Daha fazla bilgi için bkz: [tüm eşleşme değiştirerek](#EntireMatch).|  
|<code>$\`</code>|Giriş dizesinin tüm metini, değiştirme dizininde eşleşmenin önüne ekler. Daha fazla bilgi için bkz: [metinden önce eşleşme değiştirerek](#BeforeMatch).|  
|`$'`|Giriş dizesinin tüm metini, değiştirme dizininde eşleşmenin sonrasına ekler. Daha fazla bilgi için bkz: [eşleşmeden sonra metin değiştirerek](#AfterMatch).|  
|`$+`|Değiştirme dizesinde yakalanan son grubu içerir. Daha fazla bilgi için bkz: [son yakalanan Grup değiştirerek](#LastGroup).|  
|`$_`|Değiştirme dizesinde tüm giriş dizesinin bir kopyasını içerir. Daha fazla bilgi için bkz: [tüm giriş dizesini değiştirerek](#EntireString).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Değişim Öğeleri ve Değiştirme Desenleri  
 Değişimler, bir değiştirme deseninde tanınan tek özel yapılarıdır. Dahil olmak üzere diğer normal ifade dili öğelerinin hiçbiri, karakter çıkışları ve süresi (`.`), hangi herhangi bir karakterle eşleşir desteklenir. Benzer şekilde, değişim dil öğeleri yalnızca değiştirme desenlerinde tanınır ve normal ifade desenlerinde hiçbir zaman geçerli değildirler.  
  
 Normal ifade deseni veya bir değiştirme olduğu görünebilir tek karakter `$` her bağlamında farklı bir anlama sahip olsa da, karakter. Normal ifade deseni içinde `$` dizenin sonunda eşleşen bir bağlantıdır. Değiştirme düzeninde `$` bir değiştirme başlangıcını gösterir.  
  
> [!NOTE]
>  Bir normal ifade içindeki bir değiştirme desenine benzer işlevsellik için, bir yeniden başvuru kullanın. Yeniden başvurular hakkında daha fazla bilgi için bkz: [yeniden başvuru yapıları](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).  
  
<a name="Numbered"></a>   
## <a name="substituting-a-numbered-group"></a>Numaralandırılmış Bir Grubu Değiştirme  
 `$` *Numarası* language öğesi tarafından eşleşen son alt dizeyi içeren *numarası* değiştirme dizesini grubunda yakalama nerede *numarası* olan yakalama grubunu dizini. Örneğin, değiştirme deseni `$1` eşleşen alt dizeyi ilk yakalanan grupla değiştirilmesi olduğunu gösterir. Numaralı yakalama grupları hakkında daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 İzleyen tüm basamak `$` ait olarak yorumlanır *numarası* grubu. Amacınız bu değilse, onun yerine adlandırılmış bir grup kullanabilirsiniz. Örneğin, değiştirme dizesini kullanabilirsiniz `${1}1` yerine `$11` değiştirme dizesini ilk yakalanan grubu ile birlikte "1" değeri olarak tanımlamak için. Daha fazla bilgi için bkz: [adlandırılmış Grup değiştirerek](#Named).  
  
 Açıkça atanmadı grupları yakalama adları kullanarak `(?<` *adı* `>)` söz dizimi numaralı soldan sağ birer başlatmaya. Adlandırılmış gruplar da, son adlandırılmamış grubun dizininin bir büyüğünden başlanarak, soldan sağa doğru numaralandırılır. Örneğin, normal ifadede `(\w)(?<digit>\d)`, dizini `digit` adlandırılmış gruptur 2.  
  
 Varsa *numarası* normal ifade deseni tanımlanan geçerli bir yakalama grubunu belirtmiyor `$` *numarası* her eşleşme değiştirmek için kullanılan bir değişmez değer karakter dizisi yorumlanır.  
  
 Aşağıdaki örnek kullanır `$` *numarası* ondalık bir değeri olan para birimi simgesini Şerit değiştirme. Bir parasal değerin başında ve sonunda bulunan para birimi simgesini kaldırır ve en yaygın iki ondalık ayırıcıyı ("." ve ",") tanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Normal ifade deseni `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\p{Sc}*`|Sıfır veya daha fazla para birimi simgesi karakterini eşleştirin.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`[.,]?`|Sıfır veya bir nokta ya da virgülü eşleştirin.|  
|`\d*`|Sıfır veya daha fazla ondalık basamağı eşleştirin.|  
|`(\s?\d+[.,]?\d*)`|Ardından bir veya birden fazla ondalık basamak, sıfır veya bir nokta veya virgül, sıfır veya daha fazla ondalık basamak gelen bir beyaz alanı eşleştirin. Bu ilk yakalama grubudur. Değiştirme deseni olduğundan `$1`, çağrısı <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemi ile yakalanan bu grubun alt dizenin tamamı eşleşen değiştirir.|  
  
 [Başa dön](#Top)  
  
<a name="Named"></a>   
## <a name="substituting-a-named-group"></a>Adlandırılmış Bir Grubu Değiştirme  
 `${` *Adı* `}` language öğesi tarafından eşleşen son alt dizeyi değiştirir *adı* grup, yakalama nerede *adı* adı bir Grup tarafından tanımlanan yakalama `(?<` *adı* `>)` language öğesi. Adlandırılmış yakalama grupları hakkında daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Varsa *adı* geçerli bir normal ifade deseni tanımlı yakalama grubu adlı belirtmeyen ancak rakamı, oluşur `${` *adı* `}` numaralandırılmış bir grup olarak yorumlanır.  
  
 Varsa *adı* geçerli bir adlandırılmış yakalama grubu ne normal ifade deseni tanımlı bir geçerli numaralı yakalama grubunu belirtir `${` *adı* `}` olarak yorumlanır bir Her eşleşme değiştirmek için kullanılan harf karakter dizisi.  
  
 Aşağıdaki örnek kullanır `${` *adı* `}` ondalık bir değeri olan para birimi simgesini Şerit değiştirme. Bir parasal değerin başında ve sonunda bulunan para birimi simgesini kaldırır ve en yaygın iki ondalık ayırıcıyı ("." ve ",") tanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Normal ifade deseni `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\p{Sc}*`|Sıfır veya daha fazla para birimi simgesi karakterini eşleştirin.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`[.,]?`|Sıfır veya bir nokta ya da virgülü eşleştirin.|  
|`\d*`|Sıfır veya daha fazla ondalık basamağı eşleştirin.|  
|`(?<amount>\s?\d[.,]?\d*)`|Ardından bir veya birden fazla ondalık basamak, sıfır veya bir nokta veya virgül, sıfır veya daha fazla ondalık basamak gelen bir beyaz alanı eşleştirin. Bu adlı yakalama grubudur `amount`. Değiştirme deseni olduğundan `${amount}`, çağrısı <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemi ile yakalanan bu grubun alt dizenin tamamı eşleşen değiştirir.|  
  
 [Başa dön](#Top)  
  
<a name="DollarSign"></a>   
## <a name="substituting-a--character"></a>Bir "$" Karakterini Değiştirme  
 `$$` Değiştirme değiştirilen dize sabit değeri bir "$" karakterini ekler.  
  
 Aşağıdaki örnek kullanır <xref:System.Globalization.NumberFormatInfo> geçerli kültürün para birimi simgesini ve yerleşimi, bir para birimi dizesindeki belirlemek için nesne. Ardından, normal bir ifade deseni ve bir değiştirme desenini dinamik olarak oluşturur. Örnek, geçerli kültürü en-US olan bir bilgisayarda çalışıyorsa, normal ifade deseni oluşturur `\b(\d+)(\.(\d+))?` ve değiştirme düzeni `$$ $1$2`. Değiştirme deseni, eşleşen metni bir para birimi simgesiyle ve ardından birinci ve ikinci yakalanan grupların geldiği bir boşlukla değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Normal ifade deseni `\b(\d+)(\.(\d+))?` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Eşleştirmeyi bir sözcük sınırının başlangıcında başlatın.|  
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu ilk yakalama grubudur.|  
|`\.`|Bir noktayı eşleştirin (ondalık ayırıcı).|  
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu, üçüncü yakalama grubudur.|  
|`(\.(\d+))?`|Bir noktanın sıfır veya bir örneğini, ardından bir veya birden çok ondalık basamak gelecek şekilde eşleştirin. Bu ikinci yakalama grubudur.|  
  
<a name="EntireMatch"></a>   
## <a name="substituting-the-entire-match"></a>Tüm Eşleştirmeyi Değiştirme  
 `$&` Değiştirme tüm eşleşme değiştirme dizesini içerir. Genellikle, eşleştirilen dizenin başlangıcına veya sonuna bir alt dize eklemek için kullanılır. Örneğin, `($&)` değiştirme deseni, başlangıç ve bitiş her eşleşme parantez ekler. Hiçbir eşleşme varsa `$&` değiştirme etkisi yoktur.  
  
 Aşağıdaki örnek kullanır `$&` başında ve dize dizisinde depolanan kitap başlıklarını sonuna tırnak işaretleri eklemek için değiştirme.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Normal ifade deseni `^(\w+\s?)+$` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşlemeyi giriş dizesinin başından başlatın.|  
|`(\w+\s?)+`|Bir veya birden çok sözcük karakteri desenini, ardından sıfır veya bir beyaz alan karakteri bir veya birden çok kez gelecek şekilde eşleştirin.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 `"$&"` Değiştirme düzeni başlangıcını ve bitişini her eşleşme için değişmez değer tırnak işareti ekler.  
  
 [Başa dön](#Top)  
  
<a name="BeforeMatch"></a>   
## <a name="substituting-the-text-before-the-match"></a>Eşleştirmeden Önceki Metni Değiştirme  
 <code>$\`</code> Değiştirme eşleşme önce tüm giriş dizesiyle eşleşen dize değiştirir. Yani, giriş dizesini eşleştirmeye kadar çoğaltırken, eşleştirilen metni kaldırır. Eşleştirilen metni izleyen metin, sonuç dizesinde değiştirilmez. Bir giriş dizesinde birden çok eşleştirme varsa, değiştirme metni, metnin daha önceki eşleştirmelerle değiştirildiği dizeden değil, özgün giriş dizesinden türetilir. \(Örnek bir çizim verilmektedir.\) Hiçbir eşleşme varsa <code>$\`</code> değiştirme etkisi yoktur.  
  
 Aşağıdaki örnek, normal ifade deseni kullanır `\d+` giriş dizesi bir veya daha fazla ondalık basamak dizisi eşleşecek şekilde. Değiştirme dizesini <code>$`</code> bu basamağını eşleşme önündeki metni ile değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 Bu örnekte, giriş dizesi `"aa1bb2cc3dd4ee5"` beş eşleşmeleri içerir. Aşağıdaki tabloda gösterilmektedir nasıl <code>$`</code> değiştirme her eşlemesinde giriş dizesini değiştirmek normal ifade altyapısı neden olur. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
|Eşleştirme|Konum|Eşleştirmeden önceki dize|Sonuç Dizesi|  
|-----------|--------------|-------------------------|-------------------|  
|1.|2|aa|aa**aa**bb2cc3dd4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|  
  
 [Başa dön](#Top)  
  
<a name="AfterMatch"></a>   
## <a name="substituting-the-text-after-the-match"></a>Eşleştirmeden Sonraki Metni Değiştirme  
 `$'` Değiştirme eşleşmeden sonra tüm giriş dizesi ile eşleşen dize değiştirir. Yani, giriş dizesini eşleştirmeden sonra çoğaltırken, eşleştirilen metni kaldırır. Eşleştirilen metinden önce gelen metin, sonuç dizesinde değiştirilmez. Hiçbir eşleşme varsa `$'` değiştirme etkisi yoktur.  
  
 Aşağıdaki örnek, normal ifade deseni kullanır `\d+` giriş dizesi bir veya daha fazla ondalık basamak dizisi eşleşecek şekilde. Değiştirme dizesini `$'` bu basamak eşleşme izleyen metinle değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 Bu örnekte, giriş dizesi `"aa1bb2cc3dd4ee5"` beş eşleşmeleri içerir. Aşağıdaki tabloda gösterilmektedir nasıl `$'` değiştirme her eşlemesinde giriş dizesini değiştirmek normal ifade altyapısı neden olur. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
|Eşleştirme|Konum|Eşleşmeden sonraki dize|Sonuç Dizesi|  
|-----------|--------------|------------------------|-------------------|  
|1.|2|bb2cc3dd4ee5|aa**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  
  
 [Başa dön](#Top)  
  
<a name="LastGroup"></a>   
## <a name="substituting-the-last-captured-group"></a>Yakalanan Son Grubu Değiştirme  
 `$+` Değiştirme son yakalanan grubuyla eşleşen dize yerini alır. Yakalanan bir grup yok varsa ya da son yakalanan grubunun değeri ise <xref:System.String.Empty?displayProperty=nameWithType>, `$+` değiştirme etkisi yoktur.  
  
 Aşağıdaki örnekte bir dizedeki yinelenen sözcükler tanımlar ve kullandığı `$+` bunları tek bir sözcük tekrarlamasını ile değiştirmek için değiştirme. <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> Seçeneği durumda farklılık gösterir ancak, aksi takdirde aynı sözcükler çoğaltmaları dikkate alınmasını sağlamak için kullanılır.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Normal ifade deseni `\b(\w+)\s\1\b` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`\1`|İlk yakalanan grubu eşleştirin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 [Başa dön](#Top)  
  
<a name="EntireString"></a>   
## <a name="substituting-the-entire-input-string"></a>Tüm Giriş Dizesini Değiştirme  
 `$_` Değiştirme tüm giriş dizesiyle eşleşen dize yerini alır. Diğer bir deyişle, eşleştirilen metni kaldırır ve eşleştirilen metni içeren tüm dize ile değiştirir.  
  
 Aşağıdaki örnekte, giriş dizesindeki bir veya daha fazla ondalık basamak eşleştirilmektedir. Kullandığı `$_` değiştirme tüm giriş dizesi ile değiştirin.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 Bu örnekte, giriş dizesi `"ABC123DEF456"` iki eşleşmeleri içerir. Aşağıdaki tabloda gösterilmektedir nasıl `$_` değiştirme her eşlemesinde giriş dizesini değiştirmek normal ifade altyapısı neden olur. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
|Eşleştirme|Konum|Eşleştirme|Sonuç Dizesi|  
|-----------|--------------|-----------|-------------------|  
|1.|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
