---
title: Normal İfadelerdeki Gruplandırma Yapıları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lookbehinds
- regular expressions, grouping constructs
- lookaheads
- .NET Framework regular expressions, grouping constructs
- constructs, grouping
- grouping constructs
ms.assetid: 0fc18634-f590-4062-8d5c-f0b71abe405b
ms.openlocfilehash: 5b2ea110837d9d5b905f97ab706af52a594f1c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159227"
---
# <a name="grouping-constructs-in-regular-expressions"></a>Normal İfadelerdeki Gruplandırma Yapıları
Gruplandırma yapıları, normal bir ifadenin alt ifadelerini demi ve giriş dizesinin alt dizeleri yakalar. Gruplandırma yapılarını aşağıdakileri yapmak için kullanabilirsiniz:  
  
- Giriş dizesinde yinelenen bir alt ifadeeşleştirin.  
  
- Birden çok normal ifade dili öğesi olan bir alt ifadeye niceleyici uygulayın. Niceleyiciler hakkında daha fazla bilgi için, [bkz.](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)  
  
- Dize <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemlerle döndürülen bir alt ifade ekleyin.  
  
- <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Özellikten tek tek alt ifadeleri alın ve bunları eşleşen metinden ayrı ayrı bir bütün olarak işleyin.  
  
 Aşağıdaki tabloda .NET normal ifade altyapısı tarafından desteklenen gruplandırma yapıları listelenir ve yakalama olup olmadığını gösterir.  
  
|Yapıyı gruplandırma|Yakalama veya yakalamama|  
|------------------------|-------------------------------|  
|[Eşleşen alt ifadeler](#matched_subexpression)|Yakalama|  
|[Adlandırılmış eşleşen alt ifadeler](#named_matched_subexpression)|Yakalama|  
|[Grup tanımlarını dengeleme](#balancing_group_definition)|Yakalama|  
|[Yakalamayan gruplar](#noncapturing_group)|Yakalamama|  
|[Grup seçenekleri](#group_options)|Yakalamama|  
|[Sıfır genişlikpozitif ileriye dönük iddialar](#zerowidth_positive_lookahead_assertion)|Yakalamama|  
|[Sıfır genişliknegatif ileriye dönük iddialar](#zerowidth_negative_lookahead_assertion)|Yakalamama|  
|[İddiaların arkasında sıfır genişlik pozitif bakış](#zerowidth_positive_lookbehind_assertion)|Yakalamama|  
|[İddiaların arkasında sıfır genişliknegatif bakış](#zerowidth_negative_lookbehind_assertion)|Yakalamama|  
|[Atomik gruplar](#atomic_groups)|Yakalamama|  
  
 Gruplar ve normal ifade nesnesi modeli hakkında bilgi için yapı ve [normal ifade nesnelerini gruplandırma](#Objects)konusuna bakın.  
  
<a name="matched_subexpression"></a>
## <a name="matched-subexpressions"></a>Eşleşen Alt İfadeler  
 Aşağıdaki gruplandırma yapısı eşleşen bir alt ifadeyi yakalar:  
  
 `(`*alt ifade*`)`  
  
 *alt ifadenin* geçerli bir normal ifade deseni olduğu yerde. Parantez kullanan yakalar, normal ifadedeki açılış parantezlerinin sırasına göre soldan sağa otomatik olarak numaralandırılır. Sıfır numaralı yakalama, tüm normal ifade deseniyle eşleşen metindir.  
  
> [!NOTE]
> Varsayılan olarak, `(` *alt ifade* `)` dili öğesi eşleşen alt ifadeyi yakalar. Ancak normal <xref:System.Text.RegularExpressions.RegexOptions> bir ifade deseni eşleştirme yönteminin parametresi bayrağı içeriyorsa <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> veya `n` seçenek bu alt ifadeye uygulanıyorsa (bu konunun ilerleyen saatlerinde Grup [seçeneklerine](#group_options) bakın), eşleşen alt ifade yakalanmaz.  
  
 Yakalanan gruplara dört şekilde erişebilirsiniz:  
  
- Normal ifade içinde backreference yapı kullanarak. Eşleşen alt ifade, yakalanan alt ifadenin ordinal `\`numarası *olan* sözdizimi *numarası*kullanılarak aynı normal ifadede başvurulur.  
  
- Normal ifade içinde adlandırılmış backreference yapı kullanarak. Eşleşen alt `\k<`ifade, sözdizimi *adı*`>`kullanılarak aynı normal ifadede başvurulur, burada *ad* bir `\k<`yakalama grubunun adı veya *numarası*`>`, *numara* nın bir yakalama grubunun ordinal numarası olduğu yerdir. Yakalama grubunun varsayılan adı, kendi ordinal numarasıyla aynıdır. Daha fazla bilgi için, bu konunun ilerleyen saatlerinde [Adlandırılmış eşleşen alt ifadelere](#named_matched_subexpression) bakın.  
  
- `$` *Numara* değiştirme sırasını kullanarak <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> bir veya yöntem çağrısında, *yakalanan* alt ifadenin sıra numarası dır.  
  
- Programlı olarak, özellik <xref:System.Text.RegularExpressions.GroupCollection> tarafından döndürülen nesneyi <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> kullanarak. Koleksiyondaki sıfır konumundaki üye, tüm normal ifade eşleşmesini temsil eder. Sonraki her üye eşleşen bir alt ifadeyi temsil eder. Daha fazla bilgi için [Yapı ve Düzenli İfade Nesneleri Gruplandırma](#Objects) bölümüne bakın.  
  
 Aşağıdaki örnekte, metindeki yinelenen sözcükleri tanımlayan normal bir ifade gösteredilmektedir. Normal ifade deseninin iki yakalama grubu, yinelenen sözcüğün iki örneğini temsil eder. İkinci örnek, giriş dizesinde başlangıç konumunu bildirmek için yakalanır.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Normal ifade deseni aşağıdaki gibidir:  
  
`(\w+)\s(\1)\W`  
  
 Aşağıdaki tablo, normal ifade deseninin nasıl yorumlandığını gösterir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\1)`|Yakalanan ilk gruptaki dizeyle eşleştirin. Bu ikinci yakalama grubudur. Örnek, yinelenen sözcüğün başlangıç `Match.Index` konumunun özellikten alınabilmesi için onu yakalanan bir gruba atar.|  
|`\W`|Beyaz boşluk ve noktalama işaretleri de dahil olmak üzere sözcük olmayan bir karakteri eşleştirin. Bu, normal ifade deseni ilk yakalanan gruptan kelime ile başlayan bir sözcük eşleştirmesini engeller.|  
  
<a name="named_matched_subexpression"></a>
## <a name="named-matched-subexpressions"></a>Adlandırılmış Eşleşen Alt İfadeler  
 Aşağıdaki gruplandırma yapısı eşleşen bir alt ifadeyi yakalar ve ada veya numaraya göre erişmenizi sağlar:  
  
`(?<name>subexpression)`  
  
 veya:  
  
`(?'name'subexpression)`  
  
 *adın* geçerli bir grup adı olduğu ve *alt ifadenin* geçerli bir normal ifade deseni olduğu. *ad* herhangi bir noktalama karakteri içermemelidir ve bir sayı ile başlayamaz.  
  
> [!NOTE]
> Normal <xref:System.Text.RegularExpressions.RegexOptions> ifade deseni eşleştirme yönteminin parametresi bayrağı <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> `n` içeriyorsa veya seçenek bu alt ifadeye uygulanıyorsa (bu konunun ilerleyen saatlerinde [Grup seçeneklerine](#group_options) bakın), bir alt ifadeyi yakalamanın tek yolu yakalama gruplarını açıkça adlandırmaktır.  
  
 Adlandırılmış yakalanan gruplara aşağıdaki yollarla erişebilirsiniz:  
  
- Normal ifade içinde adlandırılmış backreference yapı kullanarak. Eşleşen alt ifade, yakalanan alt ifadenin `\k<`adının *sözdizimi* *adı*`>`kullanılarak aynı normal ifadede başvurulur.  
  
- Normal ifade içinde backreference yapı kullanarak. Eşleşen alt ifade, yakalanan alt ifadenin ordinal `\`numarası *olan* sözdizimi *numarası*kullanılarak aynı normal ifadede başvurulur. Eşleşen alt ifadeler eşleştikten sonra soldan sağa doğru ardışık olarak numaralandırılır.  
  
- `${` *name* Ad`}` değiştirme sırasını bir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> veya yöntem çağrısında kullanarak, *yakalanan* alt ifadenin adı dır.  
  
- `$` *Numara* değiştirme sırasını kullanarak <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> bir veya yöntem çağrısında, *yakalanan* alt ifadenin sıra numarası dır.  
  
- Programlı olarak, özellik <xref:System.Text.RegularExpressions.GroupCollection> tarafından döndürülen nesneyi <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> kullanarak. Koleksiyondaki sıfır konumundaki üye, tüm normal ifade eşleşmesini temsil eder. Sonraki her üye eşleşen bir alt ifadeyi temsil eder. Adlandırılmış yakalanan gruplar, numaralandırılmış yakalanan gruplardan sonra koleksiyonda depolanır.  
  
- Programlı olarak, alt ifade adını nesnenin <xref:System.Text.RegularExpressions.GroupCollection> dizinleyicisine (C#' da) veya <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> özelliğine (Visual Basic'te) sağlayarak.  
  
 Basit bir normal ifade deseni, numaralandırılmış (adsız) ve adlandırılmış grupların programlı olarak veya normal ifade dili sözdizimi kullanılarak nasıl başvurulabileceğini gösterir. Normal ifade, `((?<One>abc)\d+)?(?<Two>xyz)(.*)` aşağıdaki yakalama gruplarını sayıya ve ada göre üretir. İlk yakalama grubu (sayı 0) her zaman tüm deseni ifade eder.  
  
|Sayı|Adı|Desen|  
|------------|----------|-------------|  
|0|0 (varsayılan ad)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1|1 (varsayılan ad)|`((?<One>abc)\d+)`|  
|2|2 (varsayılan ad)|`(.*)`|  
|3|Bir|`(?<One>abc)`|  
|4|İki|`(?<Two>xyz)`|  
  
 Aşağıdaki örnekte, yinelenen sözcükleri ve yinelenen her sözcüğü hemen izleyen sözcüğü tanımlayan normal bir ifade gösterilmiştir. Normal ifade deseni iki adlandırılmış `duplicateWord`alt ifadetanımlar: , yinelenen sözcüğü temsil eder; ve `nextWord`, yinelenen sözcüğü izleyen sözcüğü temsil eder.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Normal ifade deseni aşağıdaki gibidir:  
  
`(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)`  
  
 Aşağıdaki tablo, normal ifadenin nasıl yorumlandığını gösterir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunu `duplicateWord`adlandırın.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`\k<duplicateWord>`|Yakalanan gruptan gelen dizeyle `duplicateWord`eşleştirin.|  
|`\W`|Beyaz boşluk ve noktalama işaretleri de dahil olmak üzere sözcük olmayan bir karakteri eşleştirin. Bu, normal ifade deseni ilk yakalanan gruptan kelime ile başlayan bir sözcük eşleştirmesini engeller.|  
|`(?<nextWord>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunu `nextWord`adlandırın.|  
  
 Bir grup adının normal bir ifadede yinelenebileni unutmayın. Örneğin, aşağıdaki örnekte gösterildiği gibi, birden `digit`fazla grubun adlandırılması mümkündür. Yinelenen adlar söz konusu olduğunda, <xref:System.Text.RegularExpressions.Group> nesnenin değeri giriş dizesinde son başarılı yakalama tarafından belirlenir. Buna ek <xref:System.Text.RegularExpressions.CaptureCollection> olarak, grup adı çoğaltılmış değilse olduğu gibi her yakalama hakkında bilgi ile doldurulur.  
  
 Aşağıdaki örnekte, normal `\D+(?<digit>\d+)\D+(?<digit>\d+)?` ifade adlı bir grubun `digit`iki oluşumunu içerir. İlk `digit` adlandırılmış grup bir veya daha fazla basamak lı karakteri yakalar. İkinci `digit` adlandırılmış grup, bir veya daha fazla basamaklı karakterin sıfır veya bir oluşumunu yakalar. Örnekteki çıktının gösterdiği gibi, ikinci yakalama grubu metne başarıyla eşleşirse, bu <xref:System.Text.RegularExpressions.Group> metnin değeri nesnenin değerini tanımlar. İkinci yakalama grubu giriş dizesini eşleştiremezse, son başarılı eşleşmenin değeri <xref:System.Text.RegularExpressions.Group> nesnenin değerini tanımlar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 Aşağıdaki tablo, normal ifadenin nasıl yorumlandığını gösterir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\D+`|Bir veya daha fazla ondalık basamak olmayan karakterleri eşleştirin.|  
|`(?<digit>\d+)`|Bir veya daha fazla ondalık basamak karakterini eşleştirin. Eşleşmeyi `digit` adlandırılmış gruba atayın.|  
|`\D+`|Bir veya daha fazla ondalık basamak olmayan karakterleri eşleştirin.|  
|`(?<digit>\d+)?`|Bir veya daha fazla ondalık basamak karakterinin sıfır veya bir oluşumunu eşleştirin. Eşleşmeyi `digit` adlandırılmış gruba atayın.|  
  
<a name="balancing_group_definition"></a>
## <a name="balancing-group-definitions"></a>Grup Tanımlarını Dengeleme  
 Dengeleme grubu tanımı, daha önce tanımlanmış bir grubun tanımını siler ve geçerli gruptaki depolar, önceden tanımlanmış grup ile geçerli grup arasındaki aralığı siler. Bu gruplandırma yapısı aşağıdaki biçime sahiptir:  
  
`(?<name1-name2>subexpression)`  
  
 veya:  
  
`(?'name1-name2' subexpression)`
  
 *name1* geçerli grup (isteğe bağlı), *name2* önceden tanımlanmış bir grup ve *alt ifade* herhangi bir geçerli düzenli ifade desenidir. Dengeleme grubu tanımı *name2* tanımını siler ve *name2* ve *name1* arasındaki aralığı *depolar1.* *Ad2* grubu tanımlanmamışsa, eşleşme geri teyidi. *Name2'nin* son tanımını sildikçe *ad2'nin*önceki tanımı ortaya çıksA, bu yapı, parantez açma veya açma ve kapatma gibi iç içe yapıları izlemek için grup *adı2* için yakalama yığınını sayaç olarak kullanmanıza olanak tanır.  
  
 Dengeleme grubu *tanımı, ad2'yi* yığın olarak kullanır. İç içe geçen her yapının başlangıç karakteri gruba <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> ve koleksiyonuna yerleştirilir. Kapanış karakteri eşleştirildiğinde, karşılık gelen açılış karakteri gruptan çıkarılır <xref:System.Text.RegularExpressions.Group.Captures%2A> ve koleksiyon bir oranında azalır. İç içe bütün yapıların açılış ve kapanış karakterleri eşleştikten *sonra, name2* boştur.  
  
> [!NOTE]
> İç içe bir yapının uygun açılış ve kapanış karakterini kullanmak için aşağıdaki örnekteki normal ifadeyi değiştirdikten sonra, matematiksel ifadeler veya program kodu satırları gibi iç içe olan yapıları işlemek için kullanabilirsiniz birden çok iç içe geçme yöntemi çağırır.  
  
 Aşağıdaki örnekte, giriş dizesinde sol ve sağ açı ayraçlarını (<>) eşleştirmek için dengeleme grubu tanımı kullanır. Örnek, `Open` iki adlandırılmış grup `Close`tanımlar ve , açı braketleri eşleşen çiftleri izlemek için bir yığın gibi kullanılır. Yakalanan her sol açı braketi `Open` grubun yakalama koleksiyonuna itilir ve yakalanan her bir `Close` dik açı braketi grubun yakalama koleksiyonuna itilir. Dengeleme grubu tanımı, her sol açı ayraç için eşleşen bir dik açı ayraç olmasını sağlar. Yoksa, son alt desen, `(?(Open)(?!))`yalnızca `Open` grup boş değilse (ve bu nedenle iç içe olan tüm yapılar kapatılmadıysa) değerlendirilir. Son alt desen değerlendirilirse, alt desen `(?!)` her zaman başarısız olan sıfır genişliknegatif ileriye dönük bir görünüm olduğundan, eşleşme başarısız olur.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Normal ifade deseni:  
  
`^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$`  
  
 Normal ifade aşağıdaki gibi yorumlanır:  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Dize başında başlayın.|  
|`[^<>]*`|Sol veya sağ açı ayraçları olmayan sıfır veya daha fazla karakteri eşleştirin.|  
|`(?'Open'<)`|Sol açı ayracı eşleştirin ve `Open`adı geçen bir gruba atayın.|  
|`[^<>]*`|Sol veya sağ açı ayraçları olmayan sıfır veya daha fazla karakteri eşleştirin.|  
|`((?'Open'<)[^<>]*)+`|Sol açılı braketin bir veya daha fazla oluşumlarını ve ardından sol veya sağ açı braketleri olmayan sıfır veya daha fazla karakterle eşleştirin. Bu ikinci yakalama grubudur.|  
|`(?'Close-Open'>)`|Dik açılı bir ayraç eşleştirin, `Open` grup la geçerli `Close` grup arasındaki alt dizeyi gruba atayın ve grubun tanımını `Open` silin.|  
|`[^<>]*`|Ne sol ne de doğru açı ayraç olan herhangi bir karakterin sıfır veya daha fazla oluşumlarını eşleştirin.|  
|`((?'Close-Open'>)[^<>]*)+`|Bir veya daha fazla olay, bir sol ne de bir sağ açı braketi olan herhangi bir karakterin sıfır veya daha fazla oluşumları takip maç. Doğru açı braketi eşleştirirken, `Open` grup ve geçerli grup arasındaki `Close` alt dizeyi gruba `Open` atayın ve grubun tanımını silin. Bu, üçüncü yakalama grubudur.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Aşağıdaki desenin sıfır veya daha fazla oluşumlarını eşleştirin: bir veya daha fazla sol açı braketinin, ardından sıfır veya daha fazla açı olmayan köşeli ayraç karakterlerinin, ardından bir veya daha fazla dik açı ayraç oluşumunun, ardından sıfır veya daha fazla oluşum açı olmayan braketler. Doğru açı ayraçeş, `Open` grubun tanımını silmek ve `Open` grup ve geçerli grup arasındaki `Close` alt dizeyi gruba atayın. Bu ilk yakalama grubudur.|  
|`(?(Open)(?!))`|`Open` Grup varsa, boş bir dize eşleşebiliyorsa, ancak dizedeki normal ifade altyapısının konumunu ilerletmeyin. Bu sıfır genişliknegatif ileriye dönük bir iddiadır. Boş bir dize her zaman dolaylı olarak bir giriş dizesinde olduğundan, bu eşleşme her zaman başarısız olur. Bu eşleşmenin başarısızlığı, açı braketlerinin dengeli olmadığını gösterir.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 Son alt ifade, `(?(Open)(?!))`giriş dizesinde iç içe geçme yapılarının düzgün dengelenip dengelenmediğini (örneğin, her sol açı ayracının bir dik açı ayracıyla eşleşip eşleşmediğini) gösterir. Yakalanan geçerli bir gruba göre koşullu eşleştirme kullanır; daha fazla bilgi için [alternation Constructs](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)'a bakın. `Open` Grup tanımlanırsa, normal ifade altyapısı giriş dizesinde alt ifade `(?!)` eşleşmeye çalışır. Grup `Open` yalnızca iç içe geçme yapıları dengesizse tanımlanmalıdır. Bu nedenle, giriş dizesinde eşleşecek desen her zaman eşleşmenin başarısız olması için neden olan bir desen olmalıdır. Bu durumda, `(?!)` boş bir dize her zaman giriş dizesinde bir sonraki konumda her zaman örtülü olarak mevcut olduğundan, her zaman başarısız sıfır genişliknegatif ileriye dönük bir iddiadır.  
  
 Örnekte, normal ifade altyapısı aşağıdaki tabloda\<gösterildiği gibi\<" abc><mno xyz>>" giriş dizesini değerlendirir.  
  
|Adım|Desen|Sonuç|  
|----------|-------------|------------|  
|1|`^`|Eşleşmeyi giriş dizesinin başında başlatır|  
|2|`[^<>]*`|Sol açı ayraç önce non-angle braket karakterleri arar;eşleşme bulur.|  
|3|`(((?'Open'<)`|" abc>"ndeki\<sol açı ayracıyla `Open` eşleşir ve gruba atar.|  
|4|`[^<>]*`|"Abc" ile eşleşiyor.|  
|5|`)+`|"<abc" yakalanan ikinci grubun değeridir.<br /><br /> Giriş dizesinde bir sonraki karakter sol açı ayraç değildir, bu nedenle `(?'Open'<)[^<>]*)` normal ifade altyapısı alt desengeri döngü değildir.|  
|6|`((?'Close-Open'>)`|"abc\<>"deki dik açı ayracıyla eşleşir, `Open` grup ile doğru açı ayracı arasındaki alt `Close` dize olan "abc"yi gruba atar `Open` ve grubun geçerli değerini ("<") siler ve boş bırakır.|  
|7|`[^<>]*`|Doğru açı braketi sonra non-angle braket karakterleri arar; eşleşme bulur.|  
|8|`)+`|Yakalanan üçüncü grubun değeri ">"dir.<br /><br /> Giriş dizesinde bir sonraki karakter dik açı ayraç değildir, bu nedenle `((?'Close-Open'>)[^<>]*)` normal ifade altyapısı alt desengeri döngü değildir.|  
|9|`)*`|Yakalanan ilk grubun değeri "abc\<>"dir.<br /><br /> Giriş dizesinde bir sonraki karakter sol açı ayraç, böylece normal `(((?'Open'<)` ifade motoru alt desen geri döngüler.|  
|10|`(((?'Open'<)`|"mno"daki\<sol açı braketini eşler ve `Open` gruba atar. Koleksiyonu <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> artık tek bir değere sahiptir, "<".|  
|11|`[^<>]*`|"Mno" ile eşleşiyor.|  
|12|`)+`|"<mno" yakalanan ikinci grubun değeridir.<br /><br /> Giriş dizesinde bir sonraki karakter sol açı ayraç, böylece normal `(?'Open'<)[^<>]*)` ifade motoru alt desen geri döngüler.|  
|13|`(((?'Open'<)`|"\<xyz>" sol açı ayraç eşleşir `Open` ve gruba atar. `Open` Grubun <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> koleksiyonu nda artık iki yakalama vardır: "mno"dan\<sol açı braketi\<ve " xyz>"den sol açı braketi.|  
|14|`[^<>]*`|"xyz" ile eşleşiyor.|  
|15|`)+`|"<xyz" yakalanan ikinci grubun değeridir.<br /><br /> Giriş dizesinde bir sonraki karakter sol açı ayraç değildir, bu nedenle `(?'Open'<)[^<>]*)` normal ifade altyapısı alt desengeri döngü değildir.|  
|16|`((?'Close-Open'>)`|" xyz>"\<deki dik açı direğinde eşleşir. "xyz", `Open` grup ve doğru açı ayraç arasındaki alt `Close` dizeyi gruba atar ve `Open` grubun geçerli değerini siler. Önceki yakalamanın değeri ("\<mno"daki sol açı braketi) `Open` grubun geçerli değeri olur. Grubun koleksiyonu artık tek bir yakalama, "\<xyz>" sol açı braketi içerir. <xref:System.Text.RegularExpressions.Group.Captures%2A> `Open`|  
|17|`[^<>]*`|Açı olmayan köşeli ayraç karakterlerini arar; eşleşme bulur.|  
|18|`)+`|Yakalanan üçüncü grubun değeri ">"dir.<br /><br /> Giriş dizesinde bir sonraki karakter dik açılı bir köşeli ayraçtır, bu nedenle normal ifade altyapısı `((?'Close-Open'>)[^<>]*)` alt desene geri döner.|  
|19|`((?'Close-Open'>)`|"xyz>>"deki son dik açı ayracıyla\<eşleşir, "mno xyz `Open`>" (grup ve `Close` doğru açı ayracı arasındaki alt `Open` dize) gruba atar ve grubun geçerli değerini siler. Grup `Open` artık boş.|  
|20|`[^<>]*`|Açı olmayan köşeli ayraç karakterlerini arar; eşleşme bulur.|  
|21|`)+`|Yakalanan üçüncü grubun değeri ">"dir.<br /><br /> Giriş dizesinde bir sonraki karakter dik açı ayraç değildir, bu nedenle `((?'Close-Open'>)[^<>]*)` normal ifade altyapısı alt desengeri döngü değildir.|  
|22|`)*`|Yakalanan ilk grubun değeri "<mno\<xyz>>"dır.<br /><br /> Giriş dizesinde bir sonraki karakter sol açı ayraç değildir, bu nedenle `(((?'Open'<)` normal ifade altyapısı alt desengeri döngü değildir.|  
|23|`(?(Open)(?!))`|Grup `Open` tanımlı olmadığından eşleşme denmez.|  
|24|`$`|Giriş dizesinin sonuyla eşleşir.|  
  
<a name="noncapturing_group"></a>
## <a name="noncapturing-groups"></a>Yakalama Yapmayan Gruplar  
 Aşağıdaki gruplandırma yapısı, bir alt ifadeyle eşleşen alt dizeyi yakalamaz:  
  
`(?:subexpression)`
  
 *alt ifadenin* geçerli bir normal ifade deseni olduğu yerde. Yakalamayan grup yapısı genellikle bir niceleyici bir gruba uygulandığında kullanılır, ancak grup tarafından yakalanan alt dizeleri ilgi alanı değildir.  
  
> [!NOTE]
> Normal bir ifade iç içe gruplama yapıları içeriyorsa, dış yakalama grubu yapısı iç iç içe grup yapıları için geçerli değildir.  
  
 Aşağıdaki örnekte, yakalamama grupları içeren normal bir ifade gösterin. Çıktının yakalanan grupları içermediğini unutmayın.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Normal ifade, `(?:\b(?:\w+)\W*)+\.` bir dönem tarafından sonlandırılan bir cümleyle eşleşir. Normal ifade tek tek sözcüklere değil, cümlelere odaklandığından, gruplandırma yapıları yalnızca ölçüleyici olarak kullanılır. Normal ifade deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?:\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Eşleşen metni yakalanan gruba atamayın.|  
|`\W*`|Sıfır veya daha fazla sözcük olmayan karakterleri eşleştirin.|  
|`(?:\b(?:\w+)\W*)+`|Bir sözcük sınırından başlayarak bir veya daha fazla sözcük karakterinin deseniyle eşleşin ve ardından bir veya daha fazla sözcük olmayan karakter, bir veya daha fazla kez. Eşleşen metni yakalanan gruba atamayın.|  
|`\.`|Bir periyodu eşleştirin.|  
  
<a name="group_options"></a>
## <a name="group-options"></a>Grup Seçenekleri  
 Aşağıdaki gruplandırma yapısı, bir alt ifade içinde belirtilen seçenekleri uygular veya devre dışı eder:  
  
 `(?imnsx-imnsx:`*alt ifade*`)`  
  
 *alt ifadenin* geçerli bir normal ifade deseni olduğu yerde. Örneğin, `(?i-s:)` büyük/küçük harf duyarsızlığını açar ve tek satırlı modu devre dışı kılabilir. Belirtebileceğiniz satır altı seçenekleri hakkında daha fazla bilgi için [Düzenli İfade Seçenekleri'ne](../../../docs/standard/base-types/regular-expression-options.md)bakın.  
  
> [!NOTE]
> Bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıf oluşturucu susini veya statik bir yöntem kullanarak bir alt ifade yerine tüm normal ifadeiçin geçerli olan seçenekleri belirtebilirsiniz. Dil yapısını kullanarak `(?imnsx-imnsx)` normal bir ifadede belirli bir noktadan sonra geçerli olan satır satır seçeneklerini de belirtebilirsiniz.  
  
 Grup seçenekleri yapısı bir yakalama grubu değildir. Diğer bir deyişle, *alt ifade* tarafından yakalanan bir dize herhangi bir bölümü eşleme dahil olmasına rağmen, yakalanan <xref:System.Text.RegularExpressions.GroupCollection> bir gruba dahil edilmez ne de nesne doldurmak için kullanılır.  
  
 Örneğin, aşağıdaki örnekteki normal ifade, `\b(?ix: d \w+)\s` büyük/küçük harf duyarsız eşleştirmeyi etkinleştirmek ve "d" harfiyle başlayan tüm sözcükleri tanımlarken desen beyaz alanı yok saymak için gruplandırma yapısında satır içi seçenekleri kullanır. Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?ix: d \w+)`|Bu desendeki büyük/küçük harf duyarsız eşleştirme ve beyaz alanı yok sayma kullanarak, bir veya daha fazla sözcük karakteri nin ardından bir "d" ile eşleştirin.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>
## <a name="zero-width-positive-lookahead-assertions"></a>Sıfır Genişlik Pozitif İleriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır genişlikpozitif ileriye doğru bir iddia tanımlar:  
  
 `(?=`*alt ifade*`)`  
  
 *alt ifadenin* herhangi bir normal ifade deseni olduğu yerde. Bir eşleşmenin başarılı olabilmesi için, eşleşen substring eşleşme sonucuna dahil edilmese de, giriş dizesi *alt ifadedeki*normal ifade deseniyle eşleşmelidir. Sıfır genişlikte pozitif ileriye dönük iddia geri adım atmaz.  
  
 Genellikle, normal bir ifade deseninin sonunda sıfır genişlikpozitif ileriye dönük bir görünüm bulunur. Bir eşleşmenin oluşması için dize sonunda bulunması gereken ancak eşleşmeye dahil edilmemesi gereken bir alt dize tanımlar. Aşırı geri izlemeyi önlemek için de yararlıdır. Yakalanan belirli bir grubun yakalanan grup için tanımlanan desenin bir alt kümesiyle eşleşen metinle başladığından emin olmak için sıfır genişlikpozitif görünüm iddiası kullanabilirsiniz. Örneğin, bir yakalama grubu ardışık sözcük karakterleriyle eşleşirse, ilk karakterin alfabetik bir büyük harf karakter olmasını gerektirecek sıfır genişlikpozitif görünüm iddiası kullanabilirsiniz.  
  
 Aşağıdaki örnek, giriş dizesinde "is" fiilinden önce gelen sözcüğü eşleştirmek için sıfır genişlikpozitif görünüm iddiası kullanır.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Normal ifade `\b\w+(?=\sis\b)` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`(?=\sis\b)`|Karakter sözcüğünün bir beyaz boşluk karakteri ve sözcük sınırında biten "is" dizesi tarafından izlenip izlenmediğini belirleyin. Eğer öyleyse, maç başarılı olur.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>
## <a name="zero-width-negative-lookahead-assertions"></a>Sıfır Genişlik Negatif İleriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır genişliknegatif ileriye doğru bir iddia tanımlar:  
  
 `(?!`*alt ifade*`)`  
  
 *alt ifadenin* herhangi bir normal ifade deseni olduğu yerde. Eşleşmenin başarılı olabilmesi için, eşleşen dize eşleşme sonucuna dahil edilmese de giriş dizesi *alt ifadedeki*normal ifade deseniyle eşleşmemelidir.  
  
 Sıfır genişliknegatif ileriye dönük görünüm genellikle normal bir ifadenin başında veya sonunda kullanılır. Normal bir ifadenin başında, normal ifadenin başlangıcı eşlenecek benzer ancak daha genel bir deseni tanımladığında eşleşmemesi gereken belirli bir desen tanımlayabilir. Bu durumda, genellikle geri izleme sınırlamak için kullanılır. Normal bir ifadenin sonunda, eşleşmenin sonunda oluşamayan bir alt ifade tanımlayabilirsiniz.  
  
 Aşağıdaki örnekte, "un" ile başlamayan sözcükleri eşleştirmek için normal ifadenin başında sıfır genişlikte bir ileriye dönük görünüm kullanan normal bir ifade tanımlanır.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Normal ifade `\b(?!un)\w+\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?!un)`|Sonraki iki karakterin "un" olup olmadığını belirleyin. Eğer değilse, bir eşleşme mümkündür.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Aşağıdaki örnek, noktalama işareti karakteriyle bitmeyen sözcükleri eşleştirmek için normal ifadenin sonunda sıfır genişlikte bir görünüm ifadesi kullanan normal bir ifade tanımlar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Normal ifade `\b\w+\b(?!\p{P})` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
|`\p{P})`|Bir sonraki karakter noktalama işareti simgesi değilse (dönem veya virgül gibi), eşleşme başarılı olur.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>
## <a name="zero-width-positive-lookbehind-assertions"></a>Sıfır Genişlik Pozitif Geriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır genişlikpozitif görünüm iddiasını tanımlar:  
  
 `(?<=`*alt ifade*`)`  
  
 *alt ifadenin* herhangi bir normal ifade deseni olduğu yerde. Bir eşleşmenin başarılı olabilmesi için, eşleşme sonucuna dahil edilmese de, `subexpression` geçerli konumun solundaki giriş dizesinde alt *ifadenin* oluşması gerekir. Sıfır genişlikte pozitif bir bakış iddiası geri adım atmaz.  
  
 Sıfır genişlik pozitif görünümler genellikle normal ifadelerin başında kullanılır. Tanımladıkları desen, eşleşme sonucunun bir parçası olmasa da, eşleşme için bir ön koşuldur.  
  
 Örneğin, aşağıdaki örnek yirmi birinci yüzyıl için yılın son iki basamağı yla eşleşir (diğer bir süre, "20" rakamlarının eşleşen dizeden önce olmasını gerektirir).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Normal ifade `(?<=\b20)\d{2}\b` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\d{2}`|İki ondalık basamak eşleştirin.|  
|`(?<=\b20)`|İki ondalık basamak, sözcük sınırında "20" ondalık basamaklardan önce yse, eşlebe devam edin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Yakalanan bir gruptaki son karakter veya karakterler, grubun normal ifade deseniyle eşleşen karakterlerin bir alt kümesi olması gerektiğinde, geri izlemeyi sınırlamak için de sıfır genişlikpozitif görünümler kullanılır. Örneğin, bir grup birbirini izleyen tüm sözcük karakterlerini yakalarsa, son karakterin alfabetik olmasını gerektirecek sıfır genişlikpozitif görünüm iddiası kullanabilirsiniz.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>
## <a name="zero-width-negative-lookbehind-assertions"></a>Sıfır Genişlik Negatif Geriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır genişliknegatif görünüm iddiasını tanımlar:  
  
 `(?<!`*alt ifade*`)`  
  
 *alt ifadenin* herhangi bir normal ifade deseni olduğu yerde. Bir eşleşmenin başarılı olabilmesi için, alt *ifadenin* geçerli konumun solundaki giriş dizesinde oluşmaması gerekir. Ancak, eşleşmeyen `subexpression` herhangi bir alt dize maç sonucuna dahil edilmez.  
  
 Sıfır genişliknegatif görünümleri genellikle normal ifadelerin başında kullanılır. Tanımladıkları desen, izleyen dizedeki bir eşleşmeyi engeller. Yakalanan bir gruptaki son karakter veya karakter, o grubun normal ifade deseniyle eşleşen karakterlerden biri veya daha fazlası olmadığında geri izlemeyi sınırlamak için de kullanılır. Örneğin, bir grup tüm ardışık sözcük karakterlerini yakalarsa, son karakterin alt düzeye uygun olmamasını\_gerektirecek sıfır genişlikpozitif görünüm iddiası kullanabilirsiniz.  
  
 Aşağıdaki örnek, hafta sonu olmayan haftanın herhangi bir gününün tarihiyle eşleşir (diğer bir gün, ne Cumartesi ne de Pazar).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Normal ifade `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakterini ve ardından bir beyaz boşluk karakterini eşleştirin.|  
|`\d{1,2},`|Bir veya iki ondalık basamakla, ardından bir beyaz boşluk karakteri ve virgül eşleştirin.|  
|`\d{4}\b`|Dört ondalık basamak eşleştirin ve eşleşmeyi sözcük sınırında sonla.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Eşleşmeden önce "Cumartesi" veya "Pazar" dizeleri ve ardından bir boşluk dışında bir şey varsa, maç başarılı olur.|  
  
<a name="atomic_groups"></a>
## <a name="atomic-groups"></a>Atomik gruplar  
 Aşağıdaki gruplandırma yapısı bir atomik grubu temsil eder (diğer bazı normal ifade motorlarında geri dönüşsüz alt ifade, atomik alt ifade veya yalnızca bir kez kullanılan alt ifade olarak bilinir):
  
 `(?>`*alt ifade*`)`  
  
 *alt ifadenin* herhangi bir normal ifade deseni olduğu yerde.  
  
 Normalde, normal bir ifade isteğe bağlı veya alternatif eşleştirme deseni içeriyorsa ve eşleşme başarılı değilse, normal ifade altyapısı bir giriş dizesini desenle eşleştirmek için birden çok yönde dallanabilir. Bir eşleşme ilk dalı aldığında bulunamazsa, normal ifade altyapısı ilk eşleşmeyi aldığı noktaya yedekleme yapabilir veya geri dönebilir ve ikinci dalı kullanarak eşleşmeyi deneyebilir. Bu işlem, tüm dallar denenene kadar devam edebilir.  
  
 `(?>` *Alt ifade* `)` dili yapısı geri izlemeyi devre dışı kılabilir. Normal ifade altyapısı, giriş dizesinde olabildiğince çok karakterle eşleşir. Başka eşleşme mümkün olmadığında, alternatif desen eşleşmeleri denemek için geri izleme olmaz. (Diğer bir şekilde, alt ifade yalnızca alt ifadeyle eşleşecek dizelerle eşleşir; alt tümmeye ve izleyen alt ifadelere dayalı bir dizeyle eşleşmeye çalışmaz.)  
  
 Geri izlemenin başarılı olmayacağını biliyorsanız bu seçenek önerilir. Normal ifade altyapısının gereksiz arama gerçekleştirmesini engellemek performansı artırır.  
  
 Aşağıdaki örnek, bir atom grubunun bir desen eşleşmesinin sonuçlarını nasıl modifelemelerini göstermektedir. Geri izleme normal ifade başarıyla yinelenen karakterler bir dizi eşleşen bir sözcük sınırında aynı karakterin bir daha oluşumu, ancak geri izleme normal ifade yok.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Geri dönüşümsüz normal `(?>(\w)\1+).\b` ifade aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(\w)`|Tek bir sözcük karakterini eşleştirin ve ilk yakalama grubuna atayın.|  
|`\1+`|Yakalanan ilk alt dizenin değerini bir veya daha fazla kez eşleştirin.|  
|`.`|Herhangi bir karakteri eşleştirin.|  
|`\b`|Eşleşmeyi sözcük sınırında sonla.|  
|`(?>(\w)\1+)`|Yinelenen sözcük karakterinin bir veya daha fazla olayını eşleştirin, ancak sözcük sınırında son karakteri eşleştirmek için geri izleme yapmayın.|  
  
<a name="Objects"></a>
## <a name="grouping-constructs-and-regular-expression-objects"></a>Yapıları ve Normal İfade Nesnelerini Gruplandırma  
 Normal bir ifade yakalama grubuyla eşleşen alt dizeleri, <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özellik tarafından döndürülen nesneden alınabilen nesnelerle temsil edilir. Nesne <xref:System.Text.RegularExpressions.GroupCollection> aşağıdaki gibi doldurulur:  
  
- Koleksiyondaki <xref:System.Text.RegularExpressions.Group> ilk nesne (dizin sıfırdaki nesne) tüm eşleşmeyi temsil eder.  
  
- Sonraki <xref:System.Text.RegularExpressions.Group> nesne kümesi, adsız (numaralanmış) yakalama gruplarını temsil eder. Bunlar, normal ifadede soldan sağa tanımlandıkları sırada görünürler. Bu grupların dizin değerleri 1 ile koleksiyondaki adsız yakalama gruplarının sayısı arasında değişir. (Belirli bir grubun dizin, numaralanmış geri referansına eşdeğerdir. Geri göndermeler hakkında daha fazla bilgi için Bkz. [Backreference Yapıları](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)  
  
- Son <xref:System.Text.RegularExpressions.Group> nesne kümesi adlandırılmış yakalama gruplarını temsil eder. Bunlar, normal ifadede soldan sağa tanımlandıkları sırada görünürler. İlk adlandırılmış yakalama grubunun dizin değeri, son adlandırılmış yakalama grubunun dizininden bir büyüktür. Normal ifadede adsız yakalama grupları yoksa, ilk adlı yakalama grubunun dizin değeri birdir.  
  
 Bir yakalama grubuna niceleyici uygularsanız, karşılık <xref:System.Text.RegularExpressions.Group> gelen <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>nesnenin <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType>, <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> ve özellikleri bir yakalama grubu tarafından yakalanan son alt dizeyi yansıtır. Özellik tarafından döndürülen <xref:System.Text.RegularExpressions.CaptureCollection> nesneden niceleyicileri olan gruplar tarafından yakalanan tam bir alt dizeleri kümesini alabilirsiniz. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>  
  
 Aşağıdaki örnek, nesneler <xref:System.Text.RegularExpressions.Group> ve <xref:System.Text.RegularExpressions.Capture> nesneler arasındaki ilişkiyi açıklar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Normal ifade `(\b(\w+)\W+)+` deseni, bir dizeden tek tek sözcükleri ayıklar. Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Birlikte, bu karakterler bir kelime oluştururlar. Bu ikinci yakalama grubudur.|  
|`\W+`|Bir veya daha fazla sözcük olmayan karakteri eşleştirin.|  
|`(\b(\w+)\W+)`|Bir veya daha fazla sözcük karakterinin deseni yle eşleşin ve ardından bir veya daha fazla sözcük olmayan karakter bir veya daha fazla kez eşleştirin. Bu ilk yakalama grubudur.|  
  
 İkinci yakalama grubu tümcenin her sözcüğüyle eşleşir. İlk yakalama grubu, kelimeyi izleyen noktalama işaretleri ve beyaz boşlukla birlikte her sözcüğü eşler. Dizini 2 olan <xref:System.Text.RegularExpressions.Group> nesne, ikinci yakalama grubuyla eşleşen metin hakkında bilgi sağlar. Yakalama grubu tarafından yakalanan sözcüklerin tam <xref:System.Text.RegularExpressions.CaptureCollection> <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kümesi, özellik tarafından döndürülen nesneden kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
