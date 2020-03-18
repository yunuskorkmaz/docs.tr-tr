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
ms.openlocfilehash: 3562bd113ae4c9a3f721d8858a5d3625ef548d3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160085"
---
# <a name="substitutions-in-regular-expressions"></a>Normal İfadelerdeki Değişimler
Değiştirmeler, yalnızca değiştirme desenleri içinde tanınan dil öğeleridir. Giriş dizesinde eşleşen metnin yerini alacak metnin tümünü veya bir kısmını tanımlamak için normal bir ifade deseni kullanırlar. Değiştirme deseni, değişmez karakterlerin yanı sıra bir veya birden çok değiştirmeden oluşabilir. Değiştirme desenleri, <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> `replacement` parametresi olan yöntemin aşırı yüklerine ve yönteme <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> sağlanır. Yöntemler, eşleşen deseni `replacement` parametre yle tanımlanan desenle değiştirir.  
  
 .NET Framework, aşağıdaki tabloda listelenen değişim öğelerini tanımlar.  
  
|Değiştirme|Açıklama|  
|------------------|-----------------|  
|$ *Numarası*|Değiştirme dizesinde, *sayının* ondalık değer *number*olduğu sayıyla tanımlanan yakalama grubuyla eşleşen son alt dizeyi içerir. Daha fazla bilgi için [bkz.](#substituting-a-numbered-group)|  
|${ *adı* }|Değiştirilen dizedeki `(?<` *ada* `> )` göre atanan adgrubuyla eşleşen son alt dizeyi içerir. Daha fazla bilgi için [bkz.](#substituting-a-named-group)|  
|$$|Değiştirme dizesinde tek bir "$" değişmez değerini içerir. Daha fazla bilgi için bkz: ["$" Simgesini Değiştirme.](#substituting-a--character)|  
|$&|Değiştirme dizesinde tüm eşleşmenin bir kopyasını içerir. Daha fazla bilgi için tüm [eşleşmeyi değiştirme 'ye](#substituting-the-entire-match)bakın.|  
|$\`|Giriş dizesinin tüm metini, değiştirme dizininde eşleşmenin önüne ekler. Daha fazla bilgi için Bkz. [Eşleşmeden Önce Metni Değiştirme.](#substituting-the-text-before-the-match)|  
|$'|Giriş dizesinin tüm metini, değiştirme dizininde eşleşmenin sonrasına ekler. Daha fazla bilgi için, [Eşleşmeden Sonra Metni Değiştirme'ye](#substituting-the-text-after-the-match)bakın.|  
|$+|Değiştirme dizesinde yakalanan son grubu içerir. Daha fazla bilgi için [bkz.](#substituting-the-last-captured-group)|  
|$\_|Değiştirme dizesinde tüm giriş dizesinin bir kopyasını içerir. Daha fazla bilgi için [bkz.](#substituting-the-entire-input-string)|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Değişim Öğeleri ve Değiştirme Desenleri  
 Değişimler, bir değiştirme deseninde tanınan tek özel yapılarıdır. Karakter kaçışları ve herhangi bir karakterle eşleşen dönem`.`( ) dahil olmak üzere diğer normal ifade dili öğelerinin hiçbiri desteklenmez. Benzer şekilde, değişim dil öğeleri yalnızca değiştirme desenlerinde tanınır ve normal ifade desenlerinde hiçbir zaman geçerli değildirler.  
  
 Her bağlamda farklı bir anlamı olmasına rağmen, normal bir ifade `$` deseni veya değiştirme denizm içinde görünebilen tek karakter karakterdir. Normal bir ifade `$` deseninde, dize sonuna uyan bir çapa dır. Değiştirme deseninde, `$` bir ikame başlangıcını gösterir.  
  
> [!NOTE]
> Bir normal ifade içindeki bir değiştirme desenine benzer işlevsellik için, bir yeniden başvuru kullanın. Geri göndermeler hakkında daha fazla bilgi için [Bkz. Backreference Yapıları.](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md)  

## <a name="substituting-a-numbered-group"></a>Numaralandırılmış Bir Grubu Değiştirme  
 `$` *Sayı* dili öğesi, *sayı* yakalama grubunun dizini olan değiştirme dizesindeki *sayı* yakalama grubuyla eşleşen son alt dizeyi içerir. Örneğin, değiştirme deseni `$1` eşleşen substring ilk yakalanan grup tarafından değiştirilecek olduğunu gösterir. Numaralı yakalama grupları hakkında daha fazla bilgi için [yapıyı gruplandırma'ya](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)bakın.  
  
 İzleyen `$` tüm basamaklar *sayı* grubuna ait olarak yorumlanır. Amacınız bu değilse, onun yerine adlandırılmış bir grup kullanabilirsiniz. Örneğin, değiştirme dizesini `${1}1` "1" sayısıyla birlikte ilk yakalanan grubun değeri olarak tanımlamak `$11` yerine değiştirme dizesini kullanabilirsiniz. Daha fazla bilgi için [bkz.](#substituting-a-named-group)  
  
 `(?<` *name* Ad`>)` sözdizimini kullanarak açıkça atanmamış olan yakalama grupları, bir andan itibaren soldan sağa numaralandırılır. Adlandırılmış gruplar da, son adlandırılmamış grubun dizininin bir büyüğünden başlanarak, soldan sağa doğru numaralandırılır. Örneğin, normal ifadede, `(\w)(?<digit>\d)` `digit` adlandırılmış grubun dizini 2'dir.  
  
 *Sayı* normal ifade deseninde tanımlanan geçerli bir yakalama `$`grubu belirtmezse, *sayı* her eşleşmeyi değiştirmek için kullanılan gerçek bir karakter dizisi olarak yorumlanır.  
  
 Aşağıdaki örnekte, `$`para birimi simgesini ondalık değerden çıkarmak için *sayı* yerine kullanılır. Bir parasal değerin başında ve sonunda bulunan para birimi simgesini kaldırır ve en yaygın iki ondalık ayırıcıyı ("." ve ",") tanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Normal ifade `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\p{Sc}*`|Sıfır veya daha fazla para birimi simgesi karakterini eşleştirin.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`[.,]?`|Sıfır veya bir nokta ya da virgülü eşleştirin.|  
|`\d*`|Sıfır veya daha fazla ondalık basamağı eşleştirin.|  
|`(\s?\d+[.,]?\d*)`|Ardından bir veya birden fazla ondalık basamak, sıfır veya bir nokta veya virgül, sıfır veya daha fazla ondalık basamak gelen bir beyaz alanı eşleştirin. Bu ilk yakalama grubudur. Değiştirme deseni `$1`olduğundan, yönteme <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> çağrı yakalanan grupla eşleşen tüm substring'in yerini alır.|  

## <a name="substituting-a-named-group"></a>Adlandırılmış Bir Grubu Değiştirme  
 `${` *name* Ad`}` dili öğesi, *ad* `(?<` *name* `>)` dil öğesi tarafından tanımlanan bir yakalama grubunun adı olduğu *ad* yakalama grubuyla eşleşen son alt dizenin yerine geçer. Adlandırılmış yakalama grupları hakkında daha fazla bilgi için, [Yapıgruplandırma'ya](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)bakın.  
  
 *Ad,* normal ifade deseninde tanımlanan ancak basamaklardan oluşan geçerli bir `${`adlandırılmış yakalama grubu belirtmezse, *ad* `}` numaralandırılmış bir grup olarak yorumlanır.  
  
 *Ad,* normal ifade deseninde tanımlanan geçerli bir adlandırılmış yakalama grubu veya geçerli `${`bir numaralandırılmış yakalama grubu belirtmezse, *ad* `}` her eşleşmeyi değiştirmek için kullanılan gerçek bir karakter dizisi olarak yorumlanır.  
  
 Aşağıdaki örnekte, `${`para birimi simgesini ondalık değerden çıkarmak için *ad* `}` ikamesi kullanılır. Bir parasal değerin başında ve sonunda bulunan para birimi simgesini kaldırır ve en yaygın iki ondalık ayırıcıyı ("." ve ",") tanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Normal ifade `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\p{Sc}*`|Sıfır veya daha fazla para birimi simgesi karakterini eşleştirin.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`[.,]?`|Sıfır veya bir nokta ya da virgülü eşleştirin.|  
|`\d*`|Sıfır veya daha fazla ondalık basamağı eşleştirin.|  
|`(?<amount>\s?\d[.,]?\d*)`|Ardından bir veya birden fazla ondalık basamak, sıfır veya bir nokta veya virgül, sıfır veya daha fazla ondalık basamak gelen bir beyaz alanı eşleştirin. Bu, ". `amount` Değiştirme deseni `${amount}`olduğundan, yönteme <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> çağrı yakalanan grupla eşleşen tüm substring'in yerini alır.|  

## <a name="substituting-a--character"></a>Bir "$" Karakterini Değiştirme  
 Değiştirme, `$$` değiştirilen dizeye gerçek bir "$" karakteri ekler.  
  
 Aşağıdaki örnek, <xref:System.Globalization.NumberFormatInfo> geçerli kültürün para birimi simgesini ve bir para birimi dizesinde yerleşimini belirlemek için nesneyi kullanır. Ardından, normal bir ifade deseni ve bir değiştirme desenini dinamik olarak oluşturur. Örnek, geçerli kültürü en-ABD olan bir bilgisayarda çalıştırılırsa, normal `\b(\d+)(\.(\d+))?` ifade deseni ve değiştirme deseni `$$ $1$2`oluşturur. Değiştirme deseni, eşleşen metni bir para birimi simgesiyle ve ardından birinci ve ikinci yakalanan grupların geldiği bir boşlukla değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Normal ifade `\b(\d+)(\.(\d+))?` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Eşleştirmeyi bir sözcük sınırının başlangıcında başlatın.|  
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu ilk yakalama grubudur.|  
|`\.`|Bir noktayı eşleştirin (ondalık ayırıcı).|  
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu, üçüncü yakalama grubudur.|  
|`(\.(\d+))?`|Bir noktanın sıfır veya bir örneğini, ardından bir veya birden çok ondalık basamak gelecek şekilde eşleştirin. Bu ikinci yakalama grubudur.|  

## <a name="substituting-the-entire-match"></a>Tüm Eşleştirmeyi Değiştirme  
 Değiştirme, `$&` değiştirme dizesinde tüm eşleşmeyi içerir. Genellikle, eşleştirilen dizenin başlangıcına veya sonuna bir alt dize eklemek için kullanılır. Örneğin, değiştirme `($&)` deseni her eşleşmenin başına ve sonuna parantez ekler. Eşleşme yoksa, ikame `$&` etkisi yoktur.  
  
 Aşağıdaki örnek, `$&` bir dize dizisinde depolanan kitap başlıklarının başında ve sonunda tırnak işaretleri eklemek için ikame kullanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Normal ifade `^(\w+\s?)+$` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşlemeyi giriş dizesinin başından başlatın.|  
|`(\w+\s?)+`|Bir veya birden çok sözcük karakteri desenini, ardından sıfır veya bir beyaz alan karakteri bir veya birden çok kez gelecek şekilde eşleştirin.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 Değiştirme `"$&"` deseni, her eşleşmenin başına ve sonuna gerçek bir tırnak işareti ekler.  

## <a name="substituting-the-text-before-the-match"></a>Eşleştirmeden Önceki Metni Değiştirme  
 Değiştirme, ``$` `` eşleşmeden önce eşleşen dizeyle tüm giriş dizesiyle değiştirilir. Yani, giriş dizesini eşleştirmeye kadar çoğaltırken, eşleştirilen metni kaldırır. Eşleştirilen metni izleyen metin, sonuç dizesinde değiştirilmez. Bir giriş dizesinde birden çok eşleştirme varsa, değiştirme metni, metnin daha önceki eşleştirmelerle değiştirildiği dizeden değil, özgün giriş dizesinden türetilir. \(Örnek bir resim sağlar. \) Eşleşme yoksa, ikame ``$` `` etkisi yoktur.  
  
 Aşağıdaki örnek, giriş dizesinde bir veya daha fazla ondalık basamak tan oluşan bir diziyle eşleştirmek için normal ifade deseni `\d+` kullanır. Değiştirme dizesi, ``$` `` bu basamakları eşleşmeden önce gelen metinle değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 Bu örnekte, giriş `"aa1bb2cc3dd4ee5"` dizesi beş eşleşme içerir. Aşağıdaki tablo, ``$` `` ikame giriş dizesinde her eşleşmeyi değiştirmek için normal ifade altyapısı neden nasıl gösterin. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
|Eşleştirme|Konum|Eşleştirmeden önceki dize|Sonuç Dizesi|  
|-----------|--------------|-------------------------|-------------------|  
|1|2|aa|aa**aa**bb2cc3d4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd ee5**|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|

## <a name="substituting-the-text-after-the-match"></a>Eşleştirmeden Sonraki Metni Değiştirme  
 Değiştirme, `$'` eşleşen dizeyle eşleşmeden sonra tüm giriş dizesiyle değiştirilir. Yani, giriş dizesini eşleştirmeden sonra çoğaltırken, eşleştirilen metni kaldırır. Eşleştirilen metinden önce gelen metin, sonuç dizesinde değiştirilmez. Eşleşme yoksa, ikame `$'` etkisi yoktur.  
  
 Aşağıdaki örnek, giriş dizesinde bir veya daha fazla ondalık basamak tan oluşan bir diziyle eşleştirmek için normal ifade deseni `\d+` kullanır. Değiştirme dizesi, `$'` bu basamakları eşleşmeyi izleyen metinle değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 Bu örnekte, giriş `"aa1bb2cc3dd4ee5"` dizesi beş eşleşme içerir. Aşağıdaki tablo, `$'` ikame giriş dizesinde her eşleşmeyi değiştirmek için normal ifade altyapısı neden nasıl gösterin. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
|Eşleştirme|Konum|Eşleşmeden sonraki dize|Sonuç Dizesi|  
|-----------|--------------|------------------------|-------------------|  
|1|2|bb2cc3dd4ee5|aa**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5 dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  

## <a name="substituting-the-last-captured-group"></a>Yakalanan Son Grubu Değiştirme  
 Değiştirme, `$+` eşleşen dizeilenin yerine yakalanan son grupla birlikte yer alır. Yakalanan grup yoksa veya yakalanan son grubun değeri <xref:System.String.Empty?displayProperty=nameWithType>ise, `$+` ikame etkisi yoktur.  
  
 Aşağıdaki örnek, yinelenen sözcükleri bir `$+` dizede tanımlar ve bunları sözcüğün tek bir oluşumuyla değiştirmek için ikame kullanır. Bu <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçenek, her durumda farklı olan ancak başka bir şekilde aynı olan sözcüklerin yinede yinelenen olarak kabul edilmesini sağlamak için kullanılır.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Normal ifade `\b(\w+)\s\1\b` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`\1`|İlk yakalanan grubu eşleştirin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  

## <a name="substituting-the-entire-input-string"></a>Tüm Giriş Dizesini Değiştirme  
 Değiştirme, `$_` eşleşen dizeilenin yerine tüm giriş dizesi ile birlikte konur. Diğer bir deyişle, eşleştirilen metni kaldırır ve eşleştirilen metni içeren tüm dize ile değiştirir.  
  
 Aşağıdaki örnekte, giriş dizesindeki bir veya daha fazla ondalık basamak eşleştirilmektedir. Tüm giriş `$_` dizesiyle değiştirmek için ikame kullanır.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 Bu örnekte, giriş `"ABC123DEF456"` dizesi iki eşleşme içerir. Aşağıdaki tablo, `$_` ikame giriş dizesinde her eşleşmeyi değiştirmek için normal ifade altyapısı neden nasıl gösterin. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
|Eşleştirme|Konum|Eşleştirme|Sonuç Dizesi|  
|-----------|--------------|-----------|-------------------|  
|1|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
