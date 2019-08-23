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
ms.openlocfilehash: 4b079809fa76097cd575d96c70d17d1c6c85e3a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968535"
---
# <a name="substitutions-in-regular-expressions"></a>Normal İfadelerdeki Değişimler
<a name="Top"></a>Değiştirmeler yalnızca değiştirme desenlerinde tanınan dil öğeleridir. Giriş dizesinde eşleşen metnin yerini alacak metnin tümünü veya bir kısmını tanımlamak için normal bir ifade deseni kullanırlar. Değiştirme deseni, değişmez karakterlerin yanı sıra bir veya birden çok değiştirmeden oluşabilir. Değiştirme desenleri, bir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> `replacement` parametresi ve <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemine sahip olan metodun aşırı yüklemeleri için sağlanır. Yöntemler, eşleşen deseninin `replacement` parametresi tarafından tanımlanan desenli yerini alır.  
  
 .NET Framework, aşağıdaki tabloda listelenen değişim öğelerini tanımlar.  
  
|Değiştirme|Açıklama|  
|------------------|-----------------|  
|$ *sayısından*|*Sayı*ile tanımlanan yakalama grubuyla eşleşen son alt dizeyi içerir; burada *sayı* , değiştirme dizesinde bir ondalık değerdir. Daha fazla bilgi için bkz. [numaralandırılmış bir grubu değiştirme](#Numbered).|  
|$ { *Name* }|Değiştirme dizesinde `(?<` ada`> )` göre belirlenen adlandırılmış grupla eşleşen son alt dizeyi içerir. Daha fazla bilgi için bkz. [adlandırılmış bir grubu değiştirme](#Named).|  
|$$|Değiştirme dizesinde tek bir "$" değişmez değerini içerir. Daha fazla bilgi için, bkz. ["$" sembolünü değiştirme](#DollarSign).|  
|$&|Değiştirme dizesinde tüm eşleşmenin bir kopyasını içerir. Daha fazla bilgi için bkz. [tüm eşleşmeyi değiştirme](#EntireMatch).|  
|$\`|Giriş dizesinin tüm metini, değiştirme dizininde eşleşmenin önüne ekler. Daha fazla bilgi için, bkz. [metni eşleştirmeden önce değiştirme](#BeforeMatch).|  
|$'|Giriş dizesinin tüm metini, değiştirme dizininde eşleşmenin sonrasına ekler. Daha fazla bilgi için bkz. [eşleştirmeden sonra metni değiştirme](#AfterMatch).|  
|$+|Değiştirme dizesinde yakalanan son grubu içerir. Daha fazla bilgi için bkz. [son yakalanan grubu değiştirme](#LastGroup).|  
|$_|Değiştirme dizesinde tüm giriş dizesinin bir kopyasını içerir. Daha fazla bilgi için, bkz. [tüm giriş dizesini değiştirme](#EntireString).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Değişim Öğeleri ve Değiştirme Desenleri  
 Değişimler, bir değiştirme deseninde tanınan tek özel yapılarıdır. Karakter kaçışları dahil diğer normal ifade dili öğelerinden hiçbiri ve herhangi bir karakterle eşleşen nokta`.`() desteklenmez. Benzer şekilde, değişim dil öğeleri yalnızca değiştirme desenlerinde tanınır ve normal ifade desenlerinde hiçbir zaman geçerli değildirler.  
  
 Bir normal ifade deseninde ya da bir değiştirme `$` içinde görünebilen tek karakter, her bağlamda farklı anlamlara sahip olsa da karakterdir. Normal ifade düzeninde, `$` dizenin sonuyla eşleşen bir bağlantıdır. Değiştirme desenindeki `$` bir değiştirme başlangıcını gösterir.  
  
> [!NOTE]
> Bir normal ifade içindeki bir değiştirme desenine benzer işlevsellik için, bir yeniden başvuru kullanın. Geri başvurular hakkında daha fazla bilgi için bkz. [Backreference yapıları](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).  
  
<a name="Numbered"></a>   
## <a name="substituting-a-numbered-group"></a>Numaralandırılmış Bir Grubu Değiştirme  
 Sayı dili öğesi, değiştirme dizesindeki yakalama grubuyla eşleşen son alt dizeyi içerir; burada *sayı* yakalama grubunun dizinidir. `$` Örneğin, değiştirme deseninin `$1` eşleşen alt dizenin ilk yakalanan grupla değiştirileceğini gösterir. Numaralandırılmış yakalama grupları hakkında daha fazla bilgi için bkz. [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 İzleyen `$` tüm basamaklar, *sayı* grubuna ait olarak yorumlanır. Amacınız bu değilse, onun yerine adlandırılmış bir grup kullanabilirsiniz. Örneğin, `${1}1` `$11` yerine konacak dizeyi, ilk yakalanan grubun değeri olarak "1" numarasıyla birlikte tanımlamak için kullanın. Daha fazla bilgi için bkz. [adlandırılmış bir grubu değiştirme](#Named).  
  
 *Ad* `(?<`sözdiziminikullanarakaçıkçaatananadlarasahipolanyakalamagrupları,soldansağadoğrubirşekildenumaralandırılır.`>)` Adlandırılmış gruplar da, son adlandırılmamış grubun dizininin bir büyüğünden başlanarak, soldan sağa doğru numaralandırılır. Örneğin, normal ifadede `(\w)(?<digit>\d)`, `digit` adlandırılmış grubun dizini 2 ' dir.  
  
 *Sayı* , normal ifade düzeninde tanımlı geçerli bir yakalama grubu belirtmezse, `$` *sayı* her eşleşmeyi değiştirmek için kullanılan bir sabit karakter dizisi olarak yorumlanır.  
  
 Aşağıdaki örnek, bir ondalık `$`değerden para birimi sembolünü atamak için *sayı* değişimini kullanır. Bir parasal değerin başında ve sonunda bulunan para birimi simgesini kaldırır ve en yaygın iki ondalık ayırıcıyı ("." ve ",") tanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Normal ifade deseninin `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` , aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\p{Sc}*`|Sıfır veya daha fazla para birimi simgesi karakterini eşleştirin.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`[.,]?`|Sıfır veya bir nokta ya da virgülü eşleştirin.|  
|`\d*`|Sıfır veya daha fazla ondalık basamağı eşleştirin.|  
|`(\s?\d+[.,]?\d*)`|Ardından bir veya birden fazla ondalık basamak, sıfır veya bir nokta veya virgül, sıfır veya daha fazla ondalık basamak gelen bir beyaz alanı eşleştirin. Bu ilk yakalama grubudur. Değiştirme deseninin olduğu `$1` <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> için, yöntemine yapılan çağrı eşleşen alt dizenin tamamını bu yakalanan grupla değiştirir.|  
  
 [Başa dön](#Top)  
  
<a name="Named"></a>   
## <a name="substituting-a-named-group"></a>Adlandırılmış Bir Grubu Değiştirme  
 `(?<` Ad Language öğesi, ad yakalama grubuyla eşleşen son alt dizenin yerini alır; burada ad, ad tarafından tanımlanan yakalama grubunun adıdır`}` `${``>)`Language öğesi. Adlandırılmış yakalama grupları hakkında daha fazla bilgi için bkz. [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 *Ad* , normal ifade modelinde tanımlanmış, ancak rakamlardan oluşan bir adlandırılmış yakalama grubu belirtmezse, `${` *ad* `}` numaralandırılmış bir grup olarak yorumlanır.  
  
 *Ad* , geçerli bir adlandırılmış yakalama grubu veya normal ifade düzeninde tanımlı geçerli bir Numaralandırılmış yakalama grubu belirtiyorsa `${` *ad* `}` , değiştirmek için kullanılan bir sabit değer karakter dizisi olarak yorumlanır her eşleşme.  
  
 Aşağıdaki örnek, bir ondalık `${`değerden para birimi sembolünü atamak için *ad* `}` değiştirme 'yi kullanır. Bir parasal değerin başında ve sonunda bulunan para birimi simgesini kaldırır ve en yaygın iki ondalık ayırıcıyı ("." ve ",") tanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Normal ifade deseninin `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` , aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\p{Sc}*`|Sıfır veya daha fazla para birimi simgesi karakterini eşleştirin.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`[.,]?`|Sıfır veya bir nokta ya da virgülü eşleştirin.|  
|`\d*`|Sıfır veya daha fazla ondalık basamağı eşleştirin.|  
|`(?<amount>\s?\d[.,]?\d*)`|Ardından bir veya birden fazla ondalık basamak, sıfır veya bir nokta veya virgül, sıfır veya daha fazla ondalık basamak gelen bir beyaz alanı eşleştirin. Bu, adlı `amount`yakalama grubudur. Değiştirme deseninin olduğu `${amount}` <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> için, yöntemine yapılan çağrı eşleşen alt dizenin tamamını bu yakalanan grupla değiştirir.|  
  
 [Başa dön](#Top)  
  
<a name="DollarSign"></a>   
## <a name="substituting-a--character"></a>Bir "$" Karakterini Değiştirme  
 Değiştirme `$$` , değiştirilmiş dizeye bir sabit değer "$" karakteri ekler.  
  
 Aşağıdaki örnek, geçerli kültürün para birimi simgesini ve onun yerleşimini bir para birimi dizesinde belirleme <xref:System.Globalization.NumberFormatInfo> nesnesini kullanır. Ardından, normal bir ifade deseni ve bir değiştirme desenini dinamik olarak oluşturur. Örnek, geçerli kültürü en-US olan bir bilgisayarda çalışıyorsa, normal ifade deseninin `\b(\d+)(\.(\d+))?` ve değiştirme düzeninin `$$ $1$2`oluşturulur. Değiştirme deseni, eşleşen metni bir para birimi simgesiyle ve ardından birinci ve ikinci yakalanan grupların geldiği bir boşlukla değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Normal ifade deseninin `\b(\d+)(\.(\d+))?` , aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Eşleştirmeyi bir sözcük sınırının başlangıcında başlatın.|  
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu ilk yakalama grubudur.|  
|`\.`|Bir noktayı eşleştirin (ondalık ayırıcı).|  
|`(\d+)`|Bir veya daha fazla ondalık basamağı eşleştirin. Bu, üçüncü yakalama grubudur.|  
|`(\.(\d+))?`|Bir noktanın sıfır veya bir örneğini, ardından bir veya birden çok ondalık basamak gelecek şekilde eşleştirin. Bu ikinci yakalama grubudur.|  
  
<a name="EntireMatch"></a>   
## <a name="substituting-the-entire-match"></a>Tüm Eşleştirmeyi Değiştirme  
 Değiştirme `$&` , değiştirme dizesinde tüm eşleşmeyi içerir. Genellikle, eşleştirilen dizenin başlangıcına veya sonuna bir alt dize eklemek için kullanılır. Örneğin, `($&)` değiştirme kalıbı her eşleşmenin başına ve sonuna parantez ekler. Eşleşme `$&` yoksa değiştirme hiçbir etkiye sahip değildir.  
  
 Aşağıdaki örnek, bir dize `$&` dizisinde depolanan kitap başlıklarının başlangıcına ve sonuna tırnak işaretleri eklemek için değiştirme 'yi kullanır.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Normal ifade deseninin `^(\w+\s?)+$` , aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşlemeyi giriş dizesinin başından başlatın.|  
|`(\w+\s?)+`|Bir veya birden çok sözcük karakteri desenini, ardından sıfır veya bir beyaz alan karakteri bir veya birden çok kez gelecek şekilde eşleştirin.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 `"$&"` Değiştirme düzeniyle her eşleşmenin başına ve sonuna bir sabit değer tırnak işareti eklenir.  
  
 [Başa dön](#Top)  
  
<a name="BeforeMatch"></a>   
## <a name="substituting-the-text-before-the-match"></a>Eşleştirmeden Önceki Metni Değiştirme  
 ``$` `` Değiştirme, eşleşen dizeyi eşleştirmede tüm giriş dizesiyle değiştirir. Yani, giriş dizesini eşleştirmeye kadar çoğaltırken, eşleştirilen metni kaldırır. Eşleştirilen metni izleyen metin, sonuç dizesinde değiştirilmez. Bir giriş dizesinde birden çok eşleştirme varsa, değiştirme metni, metnin daha önceki eşleştirmelerle değiştirildiği dizeden değil, özgün giriş dizesinden türetilir. \(Örnek, bir çizim sağlar.\) Eşleşme ``$` `` yoksa değiştirme hiçbir etkiye sahip değildir.  
  
 Aşağıdaki örnek, giriş dizesindeki bir veya daha `\d+` fazla ondalık basamak dizisiyle eşleştirmek için normal ifade deseninin kullanımını kullanır. Değiştirme dizesi ``$` `` , bu basamakları eşleşmesinden önce gelen metinle değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 Bu örnekte, giriş dizesinde `"aa1bb2cc3dd4ee5"` beş eşleşme bulunur. Aşağıdaki tabloda, ``$` `` değiştirmenin normal ifade altyapısının giriş dizesindeki her eşleşmeyi nasıl değiştirmesine neden olduğu gösterilmektedir. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
|Eşleştirme|Konum|Eşleştirmeden önceki dize|Sonuç Dizesi|  
|-----------|--------------|-------------------------|-------------------|  
|1\.|2|aa|aa**AA**bb2cc3dd4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**EE5|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|  
  
 [Başa dön](#Top)  
  
<a name="AfterMatch"></a>   
## <a name="substituting-the-text-after-the-match"></a>Eşleştirmeden Sonraki Metni Değiştirme  
 `$'` Değiştirme, eşleşen dizeyi eşleştirdikten sonra tüm giriş dizesiyle değiştirir. Yani, giriş dizesini eşleştirmeden sonra çoğaltırken, eşleştirilen metni kaldırır. Eşleştirilen metinden önce gelen metin, sonuç dizesinde değiştirilmez. Eşleşme `$'` yoksa değiştirme hiçbir etkiye sahip değildir.  
  
 Aşağıdaki örnek, giriş dizesindeki bir veya daha `\d+` fazla ondalık basamak dizisiyle eşleştirmek için normal ifade deseninin kullanımını kullanır. Değiştirme dizesi `$'` , bu basamakları eşleşmeyi izleyen metinle değiştirir.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 Bu örnekte, giriş dizesinde `"aa1bb2cc3dd4ee5"` beş eşleşme bulunur. Aşağıdaki tabloda, `$'` değiştirmenin normal ifade altyapısının giriş dizesindeki her eşleşmeyi nasıl değiştirmesine neden olduğu gösterilmektedir. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
|Eşleştirme|Konum|Eşleşmeden sonraki dize|Sonuç Dizesi|  
|-----------|--------------|------------------------|-------------------|  
|1\.|2|bb2cc3dd4ee5|aa**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**EE5**EE5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  
  
 [Başa dön](#Top)  
  
<a name="LastGroup"></a>   
## <a name="substituting-the-last-captured-group"></a>Yakalanan Son Grubu Değiştirme  
 Değiştirme `$+` , eşleşen dizeyi en son yakalanan grupla değiştirir. Yakalanan grup yoksa veya en son yakalanan grubun <xref:System.String.Empty?displayProperty=nameWithType> `$+` değeri ise değiştirme etkisizdir.  
  
 Aşağıdaki örnek, bir dizedeki yinelenen sözcükleri tanımlar ve bir sözcüğün tek `$+` bir tekrarı ile değiştirmek için değiştirme 'yi kullanır. <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> Seçeneği, büyük/küçük harf bakımından farklı olan sözcüklerin yinelenen olarak değerlendirildiğinden emin olmak için kullanılır.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Normal ifade deseninin `\b(\w+)\s\1\b` , aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
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
 Değiştirme `$_` , eşleşen dizeyi tüm giriş dizesiyle değiştirir. Diğer bir deyişle, eşleştirilen metni kaldırır ve eşleştirilen metni içeren tüm dize ile değiştirir.  
  
 Aşağıdaki örnekte, giriş dizesindeki bir veya daha fazla ondalık basamak eşleştirilmektedir. Bu, `$_` tüm giriş dizesinin yerini alacak şekilde değiştirme kullanır.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 Bu örnekte, giriş dizesi `"ABC123DEF456"` iki eşleşme içerir. Aşağıdaki tabloda, `$_` değiştirmenin normal ifade altyapısının giriş dizesindeki her eşleşmeyi nasıl değiştirmesine neden olduğu gösterilmektedir. Eklenen metin, sonuçlar sütununda kalın olarak gösterilir.  
  
|Eşleştirme|Konum|Eşleştirme|Sonuç Dizesi|  
|-----------|--------------|-----------|-------------------|  
|1\.|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
