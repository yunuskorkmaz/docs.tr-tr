---
title: Normal İfadelerdeki Değişimler
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20050bee696f9d47324f1b095b0b3c1120f78255
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508861"
---
# <a name="substitutions-in-regular-expressions"></a>Normal İfadelerdeki Değişimler
<a name="Top"></a> Değişimler, yalnızca değişiklik desenleri içinde tanınan dil öğeleridir. Giriş dizesinde eşleşen metnin yerini alacak metnin tümünü veya bir kısmını tanımlamak için normal bir ifade deseni kullanırlar. Değiştirme deseni, değişmez karakterlerin yanı sıra bir veya birden çok değiştirmeden oluşabilir. Değiştirme desenleri aşırı yüklemeleri için sağlanan <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yönteminin bir `replacement` parametresi ve <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi. Yöntemleri tarafından tanımlanan deseni ile eşleşen desen değiştirin `replacement` parametresi.  
  
 .NET Framework, aşağıdaki tabloda listelenen değişim öğelerini tanımlar.  
  
|Değiştirme|Açıklama|  
|------------------|-----------------|  
|`$` *Sayı*|İle tanımlanan yakalama grubuyla eşleşen son alt dizeyi içerir *numarası*burada *numarası* değiştirme dizesindeki ondalık bir değer. Daha fazla bilgi için [numaralandırılmış bir grubu değiştirme](#Numbered).|  
|`${` *Adı* `}`|Tarafından belirtilen adlandırılmış grubuyla eşleştirilen son alt dizeyi içerir `(?<` *adı* `> )` değiştirme dizesinde. Daha fazla bilgi için [adlandırılmış bir grubu değiştirme](#Named).|  
|`$$`|Değiştirme dizesinde tek bir "$" değişmez değerini içerir. Daha fazla bilgi için [bir "$" simgesini değiştirme](#DollarSign).|  
|`$&`|Değiştirme dizesinde tüm eşleşmenin bir kopyasını içerir. Daha fazla bilgi için [tüm eşleşmeyi değiştirme](#EntireMatch).|  
|<code>$\`</code>|Giriş dizesinin tüm metini, değiştirme dizininde eşleşmenin önüne ekler. Daha fazla bilgi için [metni değiştirme](#BeforeMatch).|  
|`$'`|Giriş dizesinin tüm metini, değiştirme dizininde eşleşmenin sonrasına ekler. Daha fazla bilgi için [eşleştirmeden sonraki metni](#AfterMatch).|  
|`$+`|Değiştirme dizesinde yakalanan son grubu içerir. Daha fazla bilgi için [son yakalanan grubu değiştirme](#LastGroup).|  
|`$_`|Değiştirme dizesinde tüm giriş dizesinin bir kopyasını içerir. Daha fazla bilgi için [tüm giriş dizesini değiştirme](#EntireString).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Değişim Öğeleri ve Değiştirme Desenleri  
 Değişimler, bir değiştirme deseninde tanınan tek özel yapılarıdır. Dahil olmak üzere diğer normal ifade dil öğeleri hiçbiri karakter kaçışları ve nokta (`.`), desteklenen hangi herhangi bir karakterle eşleşir. Benzer şekilde, değişim dil öğeleri yalnızca değiştirme desenlerinde tanınır ve normal ifade desenlerinde hiçbir zaman geçerli değildirler.  
  
 Herhangi bir normal ifade deseninde ve bir değiştirmede görünebilecek tek karakter `$` her bağlamda farklı bir anlama sahip olsa da, karakter. Bir normal ifade deseninde `$` dizenin sonuyla eşleşen bir tutturucudur. Bir değiştirme deseninde `$` bir değişimin başlangıcını gösterir.  
  
> [!NOTE]
>  Bir normal ifade içindeki bir değiştirme desenine benzer işlevsellik için, bir yeniden başvuru kullanın. Yeniden başvurular hakkında daha fazla bilgi için bkz. [yeniden başvuru yapıları](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).  
  
<a name="Numbered"></a>   
## <a name="substituting-a-numbered-group"></a>Numaralandırılmış Bir Grubu Değiştirme  
 `$` *Numarası* dil öğesi tarafından eşleştirilen son alt dizeyi içerir *numarası* yakalama grubu değiştirme dizesinde burada *numarası* olduğu Yakalama grubu dizini. Örneğin, değiştirme deseni `$1` eşleşen alt dizenin yakalanan ilk grupla değiştirileceğini gösterir. Numaralandırılmış yakalama grupları hakkında daha fazla bilgi için bkz. [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 İzleyen tüm basamakları `$` ait olarak yorumlanır *numarası* grubu. Amacınız bu değilse, onun yerine adlandırılmış bir grup kullanabilirsiniz. Örneğin, değiştirme dizesini kullanabilirsiniz `${1}1` yerine `$11` değiştirme dizesini "1" sayısının yanı sıra yakalanan ilk grubun değeri olarak tanımlamak için. Daha fazla bilgi için [adlandırılmış bir grubu değiştirme](#Named).  
  
 Yakalama olmayan açıkça atanan grupları adları kullanarak `(?<` *adı* `>)` söz dizimi olarak doğru başlanarak soldan numaralandırılır. Adlandırılmış gruplar da, son adlandırılmamış grubun dizininin bir büyüğünden başlanarak, soldan sağa doğru numaralandırılır. Örneğin, normal ifadede `(\w)(?<digit>\d)`, dizini `digit` adlandırılmış gruptur 2.  
  
 Varsa *numarası* normal ifade deseninde tanımlanan geçerli bir yakalama grubu belirtmiyor `$` *numarası* her bir eşleştirmeyi değiştirmek için kullanılan değişmez bir karakter dizilimi yorumlanır.  
  
 Aşağıdaki örnekte `$` *numarası* para birimi simgesini bir ondalık değerden Kendiyle değiştirme. Bir parasal değerin başında ve sonunda bulunan para birimi simgesini kaldırır ve en yaygın iki ondalık ayırıcıyı ("." ve ",") tanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Normal ifade deseni `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\p{Sc}*`|Sıfır veya daha fazla para birimi simgesi karakterini eşleştirin.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`[.,]?`|Sıfır veya bir nokta ya da virgülü eşleştirin.|  
|`\d*`|Sıfır veya daha fazla ondalık basamağı eşleştirin.|  
|`(\s?\d+[.,]?\d*)`|Ardından bir veya birden fazla ondalık basamak, sıfır veya bir nokta veya virgül, sıfır veya daha fazla ondalık basamak gelen bir beyaz alanı eşleştirin. Bu ilk yakalama grubudur. Değiştirme deseni olduğundan `$1`, çağrı <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemi, eşleştirilen tüm alt dizeyi bu yakalanan grupla değiştirir.|  
  
 [Başa dön](#Top)  
  
<a name="Named"></a>   
## <a name="substituting-a-named-group"></a>Adlandırılmış Bir Grubu Değiştirme  
 `${` *Adı* `}` dil öğesi tarafından eşleştirilen son alt dizeyi değiştirir *adı* yakalama grubu burada *adı* adı bir Yakalama grubu tarafından tanımlanan `(?<` *adı* `>)` dil öğesi. Adlandırılmış yakalama grupları hakkında daha fazla bilgi için bkz. [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Varsa *adı* geçerli bir adlandırılmış normal ifade deseninde tanımlanan yakalama grubu belirtmiyorsa, fakat basamaklardan oluşuyorsa, `${` *adı* `}` numaralandırılmış bir grup olarak yorumlanır.  
  
 Varsa *adı* geçerli bir adlandırılmış yakalama grubu ya da normal ifade deseninde tanımlanan geçerli bir numaralandırılmış yakalama grubu belirtir `${` *adı* `}` yorumlanan bir Her bir eşleştirmeyi değiştirmek için kullanılan değişmez bir karakter dizisi.  
  
 Aşağıdaki örnekte `${` *adı* `}` para birimi simgesini bir ondalık değerden Kendiyle değiştirme. Bir parasal değerin başında ve sonunda bulunan para birimi simgesini kaldırır ve en yaygın iki ondalık ayırıcıyı ("." ve ",") tanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Normal ifade deseni `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\p{Sc}*`|Sıfır veya daha fazla para birimi simgesi karakterini eşleştirin.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`[.,]?`|Sıfır veya bir nokta ya da virgülü eşleştirin.|  
|`\d*`|Sıfır veya daha fazla ondalık basamağı eşleştirin.|  
|`(?<amount>\s?\d[.,]?\d*)`|Ardından bir veya birden fazla ondalık basamak, sıfır veya bir nokta veya virgül, sıfır veya daha fazla ondalık basamak gelen bir beyaz alanı eşleştirin. Bu adlı yakalama grubudur `amount`. Değiştirme deseni olduğundan `${amount}`, çağrı <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemi, eşleştirilen tüm alt dizeyi bu yakalanan grupla değiştirir.|  
  
 [Başa dön](#Top)  
  
<a name="DollarSign"></a>   
## <a name="substituting-a--character"></a>Bir "$" Karakterini Değiştirme  
 `$$` Değişimi değiştirilen dizeye değişmez bir "$" karakteri ekler.  
  
 Aşağıdaki örnekte <xref:System.Globalization.NumberFormatInfo> geçerli kültürün para birimi simgesini ve bir para birimi dizesindeki belirlemek için nesne. Ardından, normal bir ifade deseni ve bir değiştirme desenini dinamik olarak oluşturur. Örnek, geçerli kültürü en-US olan bir bilgisayarda çalıştırılırsa, normal ifade deseni ürettiği `\b(\d+)(\.(\d+))?` ve değiştirme deseni `$$ $1$2`. Değiştirme deseni, eşleşen metni bir para birimi simgesiyle ve ardından birinci ve ikinci yakalanan grupların geldiği bir boşlukla değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Normal ifade deseni `\b(\d+)(\.(\d+))?` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Eşleştirmeyi bir sözcük sınırının başlangıcında başlatın.|  
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu ilk yakalama grubudur.|  
|`\.`|Bir noktayı eşleştirin (ondalık ayırıcı).|  
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu, üçüncü yakalama grubudur.|  
|`(\.(\d+))?`|Bir noktanın sıfır veya bir örneğini, ardından bir veya birden çok ondalık basamak gelecek şekilde eşleştirin. Bu ikinci yakalama grubudur.|  
  
<a name="EntireMatch"></a>   
## <a name="substituting-the-entire-match"></a>Tüm Eşleştirmeyi Değiştirme  
 `$&` Değiştirme, değiştirme dizesinde tüm eşleşmenin içerir. Genellikle, eşleştirilen dizenin başlangıcına veya sonuna bir alt dize eklemek için kullanılır. Örneğin, `($&)` değiştirme deseni, başlangıcını ve bitişini her bir eşleşme için parantez ekliyor. Hiçbir eşleşme varsa `$&` değişiminin etkisi olmaz.  
  
 Aşağıdaki örnekte `$&` başlangıcına ve sonuna bir dize dizisinde depolanan kitap başlıklarının tırnak işaretleri eklemek için değiştirme.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Normal ifade deseni `^(\w+\s?)+$` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşlemeyi giriş dizesinin başından başlatın.|  
|`(\w+\s?)+`|Bir veya birden çok sözcük karakteri desenini, ardından sıfır veya bir beyaz alan karakteri bir veya birden çok kez gelecek şekilde eşleştirin.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 `"$&"` Değiştirme deseni, başlangıç ve bitiş, her bir değişmez değer tırnak işareti ekler.  
  
 [Başa dön](#Top)  
  
<a name="BeforeMatch"></a>   
## <a name="substituting-the-text-before-the-match"></a>Eşleştirmeden Önceki Metni Değiştirme  
 <code>$\`</code> Değişimi eşleştirilen dizeyi eşleştir önce tüm giriş dizesiyle değiştirir. Yani, giriş dizesini eşleştirmeye kadar çoğaltırken, eşleştirilen metni kaldırır. Eşleştirilen metni izleyen metin, sonuç dizesinde değiştirilmez. Bir giriş dizesinde birden çok eşleştirme varsa, değiştirme metni, metnin daha önceki eşleştirmelerle değiştirildiği dizeden değil, özgün giriş dizesinden türetilir. \(Örneğin, bir gösterim sağlar.\) Hiçbir eşleşme varsa <code>$\`</code> değişiminin etkisi olmaz.  
  
 Aşağıdaki örnek, normal ifade deseni kullanır. `\d+` giriş dizesindeki bir veya daha fazla ondalık basamak dizisi eşleştirilecek. Değiştirme dizesi <code>$`</code> bu basamakları eşleştirmeden metinle değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 Bu örnekte, Giriş dizesinin `"aa1bb2cc3dd4ee5"` beş eşleştirme içermektedir. Aşağıdaki tabloda gösterilmiştir nasıl <code>$`</code> değiştirme için normal ifade altyapısının giriş dizesindeki her bir eşleştirmeyi değiştirmek neden olur. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
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
 `$'` Değiştirme tüm giriş dizesiyle eşleştirilen dizeyi eşleştirmeden sonraki değiştirir. Yani, giriş dizesini eşleştirmeden sonra çoğaltırken, eşleştirilen metni kaldırır. Eşleştirilen metinden önce gelen metin, sonuç dizesinde değiştirilmez. Hiçbir eşleşme varsa `$'` değişiminin etkisi olmaz.  
  
 Aşağıdaki örnek, normal ifade deseni kullanır. `\d+` giriş dizesindeki bir veya daha fazla ondalık basamak dizisi eşleştirilecek. Değiştirme dizesi `$'` bu basamakları eşleştirmeden metinle değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 Bu örnekte, Giriş dizesinin `"aa1bb2cc3dd4ee5"` beş eşleştirme içermektedir. Aşağıdaki tabloda gösterilmiştir nasıl `$'` değiştirme için normal ifade altyapısının giriş dizesindeki her bir eşleştirmeyi değiştirmek neden olur. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
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
 `$+` Değişimi, eşleştirilen dizeyi son yakalanan grupla değiştirir. Yakalanan grup yoksa veya son yakalanan grubun değeri ise <xref:System.String.Empty?displayProperty=nameWithType>, `$+` değişiminin etkisi olmaz.  
  
 Aşağıdaki örnek bir dizedeki yinelenen sözcükler tanımlar ve kullandığı `$+` Word'ün tek bir oluşumunu değiştirmeye değiştirme. <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> Seçeneği durumda farklılık gösterir ancak olan aynı sözcükler çoğaltmaları dikkate alınmasını sağlamak için kullanılır.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Normal ifade deseni `\b(\w+)\s\1\b` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
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
 `$_` Değişimi, eşleştirilen dizeyi tüm giriş dizesiyle değiştirir. Diğer bir deyişle, eşleştirilen metni kaldırır ve eşleştirilen metni içeren tüm dize ile değiştirir.  
  
 Aşağıdaki örnekte, giriş dizesindeki bir veya daha fazla ondalık basamak eşleştirilmektedir. Kullandığı `$_` değişimini onları tüm giriş dizesiyle değiştirin.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 Bu örnekte, Giriş dizesinin `"ABC123DEF456"` iki eşleştirme içermektedir. Aşağıdaki tabloda gösterilmiştir nasıl `$_` değiştirme için normal ifade altyapısının giriş dizesindeki her bir eşleştirmeyi değiştirmek neden olur. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
|Eşleştirme|Konum|Eşleştirme|Sonuç Dizesi|  
|-----------|--------------|-----------|-------------------|  
|1.|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
