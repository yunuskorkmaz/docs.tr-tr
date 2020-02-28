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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159227"
---
# <a name="grouping-constructs-in-regular-expressions"></a>Normal İfadelerdeki Gruplandırma Yapıları
Yapıları gruplandırma, normal bir ifadenin alt ifadelerini ayırıcıları ve bir giriş dizesinin alt dizelerini yakalar. Aşağıdakileri yapmak için gruplandırma yapılarını kullanabilirsiniz:  
  
- Giriş dizesinde yinelenen bir alt ifadeyi eşleştirin.  
  
- Birden çok normal ifade dili öğesine sahip olan bir alt ifade için nicelik belirteci uygulayın. Nicelik belirteçleri hakkında daha fazla bilgi için bkz. [nicelik belirteçleri](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
- <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemleri tarafından döndürülen dizeye bir alt ifade ekleyin.  
  
- <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliğinden tek bir alt ifade alın ve bunları bir bütün olarak eşleşen metinden ayrı olarak işleyin.  
  
 Aşağıdaki tabloda, .NET normal ifade altyapısı tarafından desteklenen gruplandırma yapıları listelenmekte ve yakalanıp yakalanmayacağını veya yakalanmadığını belirtir.  
  
|Yapıyı gruplandırma|Yakalama veya Yakalama yapmayan|  
|------------------------|-------------------------------|  
|[Eşleşen alt ifadeler](#matched_subexpression)|Yakalayan|  
|[Adlandırılmış eşleşen alt ifadeler](#named_matched_subexpression)|Yakalayan|  
|[Grup tanımlarını Dengeleme](#balancing_group_definition)|Yakalayan|  
|[Yakalama olmayan gruplar](#noncapturing_group)|Yakalama yapmayan|  
|[Grup seçenekleri](#group_options)|Yakalama yapmayan|  
|[Sıfır genişlikli pozitif ileri yönlü onaylar](#zerowidth_positive_lookahead_assertion)|Yakalama yapmayan|  
|[Sıfır Genişlik negatif ileri düzey onaylama](#zerowidth_negative_lookahead_assertion)|Yakalama yapmayan|  
|[Sıfır Genişlik pozitif geriye yönelik onaylar](#zerowidth_positive_lookbehind_assertion)|Yakalama yapmayan|  
|[Sıfır Genişlik negatif geriye yönelik onaylar](#zerowidth_negative_lookbehind_assertion)|Yakalama yapmayan|  
|[Atomik gruplar](#atomic_groups)|Yakalama yapmayan|  
  
 Gruplar ve normal ifade nesne modeli hakkında bilgi için bkz. [gruplandırma yapıları ve normal ifade nesneleri](#Objects).  
  
<a name="matched_subexpression"></a>
## <a name="matched-subexpressions"></a>Eşleşen Alt İfadeler  
 Aşağıdaki gruplandırma yapısı eşleşen bir alt ifadeyi yakalar:  
  
 `(` alt *ifade* `)`  
  
 Burada alt *ifade* geçerli bir normal ifade deseninin olduğu yerdir. Parantez kullanan yakalamalar, normal ifadede yer alan açılış parantezleri sırasına göre otomatik olarak soldan sağa numaralandırılır. Sıfır Numaralandırılmış yakalama, tüm normal ifade deseninin eşleştirildiği metindir.  
  
> [!NOTE]
> Varsayılan olarak `(`alt *ifade*`)` Language öğesi eşleşen alt ifadeyi yakalar. Ancak, bir normal ifade deseninin eşleştirme yönteminin <xref:System.Text.RegularExpressions.RegexOptions> parametresi <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> bayrağını içeriyorsa veya bu alt ifadeye `n` seçeneği uygulanmışsa (Bu konunun ilerleyen kısımlarında bulunan [Grup seçeneklerine](#group_options) bakın), eşleşen alt ifade yakalanmaz.  
  
 Yakalanan gruplara dört şekilde erişebilirsiniz:  
  
- Normal ifade içinde geri başvuru yapısını kullanarak. Eşleşen alt ifadeye, `\`*Number*sözdizimi kullanılarak aynı normal ifadede başvurulur, burada *sayı* yakalanan alt ifadenin sıra numarasıdır.  
  
- Normal ifade içinde adlandırılmış yeniden başvuru yapısını kullanarak. Eşleşen alt ifadeye aynı normal ifadede `\k<`*ad*`>`sözdizimi kullanılarak başvurulur, burada *ad* bir yakalama grubunun adıdır veya `\k<`*sayı*`>`, burada *sayı* bir yakalama grubunun sıra numarasıdır. Yakalama grubu, sıra numarasıyla aynı olan varsayılan bir ada sahiptir. Daha fazla bilgi için bu konunun ilerleyen kısımlarında bulunan [eşleşen alt ifadeler](#named_matched_subexpression) bölümüne bakın.  
  
- Bir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Yöntem çağrısında `$`*numarası* değiştirme sırasını kullanarak, burada *sayı* yakalanan alt ifadenin sıra numarasıdır.  
  
- Program aracılığıyla, <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Text.RegularExpressions.GroupCollection> nesnesini kullanarak. Koleksiyonda sıfır konumundaki üye, tüm normal ifade eşleşmesini temsil eder. Sonraki her üye, eşleşen bir alt ifadeyi temsil eder. Daha fazla bilgi için bkz. [Grup yapıları ve normal Ifade nesneleri](#Objects) bölümü.  
  
 Aşağıdaki örnek, metinde yinelenen sözcükleri tanımlayan bir normal ifadeyi gösterir. Normal ifade deseninin iki yakalama grubu, yinelenen sözcüğün iki örneğini temsil eder. İkinci örnek, giriş dizesindeki başlangıç konumunu raporlamak için yakalanır.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Normal ifade deseninin nedeni şunlardır:  
  
`(\w+)\s(\1)\W`  
  
 Aşağıdaki tabloda, normal ifade deseninin nasıl yorumlanacağı gösterilmektedir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\1)`|Yakalanan ilk gruptaki dizeyle eşleştirin. Bu ikinci yakalama grubudur. Örnek, yinelenen sözcüğün başlangıç konumunun `Match.Index` özelliğinden alınabilmesi için onu yakalanan bir gruba atar.|  
|`\W`|Boşluk ve noktalama işaretleri de dahil olmak üzere sözcüksiz bir karakterle eşleştirin. Bu, normal ifade deseninin, ilk yakalanan gruptan kelimeyle başlayan bir sözcükle eşleşmesini önler.|  
  
<a name="named_matched_subexpression"></a>
## <a name="named-matched-subexpressions"></a>Adlandırılmış Eşleşen Alt İfadeler  
 Aşağıdaki gruplandırma yapısı eşleşen bir alt ifadeyi yakalar ve ada veya numaraya göre erişmenizi sağlar:  
  
`(?<name>subexpression)`  
  
 veya:  
  
`(?'name'subexpression)`  
  
 Burada *Name* geçerli bir grup adıdır ve alt *ifade* geçerli bir normal ifade örüntü. *ad* , herhangi bir noktalama karakteri içermemelidir ve bir sayıyla başlayamaz.  
  
> [!NOTE]
> Bir normal ifade deseninin eşleşen yönteminin <xref:System.Text.RegularExpressions.RegexOptions> parametresi <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> bayrağını içeriyorsa veya bu alt ifadeye `n` seçeneği uygulanmışsa (Bu konunun ilerleyen kısımlarında bulunan [Grup seçeneklerine](#group_options) bakın), bir alt ifadeyi yakalamaya yönelik tek yol, yakalama gruplarının açıkça adı olarak adlandırılmalıdır.  
  
 Adlandırılmış yakalanan gruplara aşağıdaki yollarla erişebilirsiniz:  
  
- Normal ifade içinde adlandırılmış yeniden başvuru yapısını kullanarak. Eşleşen alt ifadeye aynı normal ifadede `\k<`*ad*`>`sözdizimi kullanılarak başvurulur, burada *ad* yakalanan alt ifadenin adıdır.  
  
- Normal ifade içinde geri başvuru yapısını kullanarak. Eşleşen alt ifadeye, `\`*Number*sözdizimi kullanılarak aynı normal ifadede başvurulur, burada *sayı* yakalanan alt ifadenin sıra numarasıdır. Adlandırılmış eşleşen alt ifadeler, eşleşen alt ifadelerden sonra soldan sağa doğru numaralandırılır.  
  
- `${`*adı*`}` bir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Yöntem çağrısında değiştirme sırası kullanarak, *ad* yakalanan alt ifadenin adıdır.  
  
- Bir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Yöntem çağrısında `$`*numarası* değiştirme sırasını kullanarak, burada *sayı* yakalanan alt ifadenin sıra numarasıdır.  
  
- Program aracılığıyla, <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Text.RegularExpressions.GroupCollection> nesnesini kullanarak. Koleksiyonda sıfır konumundaki üye, tüm normal ifade eşleşmesini temsil eder. Sonraki her üye, eşleşen bir alt ifadeyi temsil eder. Adlandırılmış yakalanan gruplar, yakalanan grupların numaralandırıldıktan sonra koleksiyonda depolanır.  
  
- Programlı olarak, <xref:System.Text.RegularExpressions.GroupCollection> nesnenin dizin oluşturucusuna (içinde C#) veya <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> özelliğine (Visual Basic) alt ifade adı sağlayarak.  
  
 Basit bir normal ifade modelinde, numaralandırılmış (adlandırılmamış) ve adlandırılmış grupların programlı olarak veya normal ifade dili sözdizimi kullanılarak nasıl başvurulabileceği gösterilmektedir. Normal ifade `((?<One>abc)\d+)?(?<Two>xyz)(.*)`, aşağıdaki yakalama gruplarını sayıyla ve ada göre üretir. İlk yakalama grubu (sayı 0) her zaman tüm modele başvurur.  
  
|Sayı|Adı|Desen|  
|------------|----------|-------------|  
|0|0 (varsayılan ad)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1|1 (varsayılan ad)|`((?<One>abc)\d+)`|  
|2|2 (varsayılan ad)|`(.*)`|  
|3|Bir|`(?<One>abc)`|  
|4|İki|`(?<Two>xyz)`|  
  
 Aşağıdaki örnek, yinelenen kelimeleri ve her bir yinelenen sözcüğü hemen izleyen kelimeyi tanımlayan bir normal ifade gösterir. Normal ifade deseninin iki adlandırılmış alt ifadesi tanımlar: yinelenen kelimeyi temsil eden `duplicateWord`; ve yinelenen kelimeyi izleyen kelimeyi temsil eden `nextWord`.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Normal ifade deseninin aşağıdaki gibidir:  
  
`(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)`  
  
 Aşağıdaki tabloda, normal ifadenin nasıl yorumlanacağı gösterilmektedir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunu adlandırın `duplicateWord`.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`\k<duplicateWord>`|`duplicateWord`adlı yakalanan gruptaki dizeyle eşleştirin.|  
|`\W`|Boşluk ve noktalama işaretleri de dahil olmak üzere sözcüksiz bir karakterle eşleştirin. Bu, normal ifade deseninin, ilk yakalanan gruptan kelimeyle başlayan bir sözcükle eşleşmesini önler.|  
|`(?<nextWord>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunu adlandırın `nextWord`.|  
  
 Bir grup adının normal bir ifadede tekrarlanabilir olduğunu unutmayın. Örneğin, aşağıdaki örnekte gösterildiği gibi, birden fazla grubun `digit`adlandırılmış olması mümkündür. Yinelenen adlar söz konusu olduğunda, <xref:System.Text.RegularExpressions.Group> nesnesinin değeri giriş dizesindeki son başarılı yakalama tarafından belirlenir. Ayrıca, <xref:System.Text.RegularExpressions.CaptureCollection> her yakalama hakkında, Grup adı yinelenmediğinden olduğu gibi bilgilerle doldurulur.  
  
 Aşağıdaki örnekte, `\D+(?<digit>\d+)\D+(?<digit>\d+)?` normal ifade, `digit`adlı bir grubun iki yinelemesini içerir. Adlandırılmış ilk `digit` grubu bir veya daha fazla rakam karakteri yakalar. İkinci `digit` adlı grup, bir veya daha fazla rakam karakteri veya bir veya daha fazla karakter örneğini yakalar. Örneğin çıkışının gösterdiği gibi, ikinci yakalama grubu metinle başarıyla eşleşiyorsa, bu metnin değeri <xref:System.Text.RegularExpressions.Group> nesnesinin değerini tanımlar. İkinci yakalama grubu giriş dizesiyle eşleşmezse, son başarılı eşleşmenin değeri <xref:System.Text.RegularExpressions.Group> nesnesinin değerini tanımlar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 Aşağıdaki tabloda, normal ifadenin nasıl yorumlanacağı gösterilmektedir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\D+`|Ondalık olmayan bir veya daha fazla karakter eşleştirin.|  
|`(?<digit>\d+)`|Bir veya daha fazla ondalık basamak karakteri eşleştirin. Eşleşmeyi `digit` adlı gruba atayın.|  
|`\D+`|Ondalık olmayan bir veya daha fazla karakter eşleştirin.|  
|`(?<digit>\d+)?`|Bir veya daha fazla ondalık basamak karakterinin sıfır veya bir oluşumunu eşleştirin. Eşleşmeyi `digit` adlı gruba atayın.|  
  
<a name="balancing_group_definition"></a>
## <a name="balancing-group-definitions"></a>Grup Tanımlarını Dengeleme  
 Bir Dengeleme grubu tanımı, daha önce tanımlanmış bir grubun tanımını ve geçerli grupta, daha önce tanımlanan grup ve geçerli grup arasındaki aralığı siler. Bu gruplandırma yapısı aşağıdaki biçimdedir:  
  
`(?<name1-name2>subexpression)`  
  
 veya:  
  
`(?'name1-name2' subexpression)`
  
 Burada *name1* geçerli grup (isteğe bağlı) ise, *AD2* daha önce tanımlanmış bir gruptur ve alt *ifade* geçerli bir normal ifade örünyordu. Dengeleme grubu tanımı, *AD2* tanımını siler ve *name1*içinde *AD2* ve *name1* arasındaki aralığı depolar. Hiçbir *AD2* grubu tanımlanmamışsa, eşleşme geri izler. N} öğesinin son tanımını silmek, *AD2* *'ın önceki tanımını ortaya* çıkardığı için, bu yapı, boşluk olarak grup *AD2* için yakalama yığınını, parantez gibi iç içe yapıları izlemek için bir sayaç olarak kullanmanıza olanak sağlar.  
  
 Dengeleme grubu tanımı bir yığın olarak *AD2* kullanır. İç içe yerleştirilmiş her yapının başlangıç karakteri gruba ve <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> koleksiyonuna yerleştirilir. Kapanış karakteri eşleştiğinde, karşılık gelen açma karakteri gruptan kaldırılır ve <xref:System.Text.RegularExpressions.Group.Captures%2A> koleksiyonu bir tane azaltılır. Tüm iç içe yapıların açılış ve kapanış karakterleri eşleştirdikten sonra, *AD2* boş olur.  
  
> [!NOTE]
> Aşağıdaki örnekte, iç içe yerleştirilmiş bir yapının uygun açılış ve kapanış karakterini kullanmak için normal ifadeyi değiştirdikten sonra, matematiksel ifadeler veya dahil edilen program kodu satırları gibi iç içe geçmiş yapıları işlemek için kullanabilirsiniz. birden çok iç içe geçmiş yöntem çağrısı.  
  
 Aşağıdaki örnek, bir giriş dizesinde Left ve Right açılı ayraçları (< >) ile eşleştirmek için bir Dengeleme grubu tanımı kullanır. Örnek, eşleşen açılı ayraç çiftlerini izlemek için bir yığın gibi kullanılan `Open` ve `Close`iki adlandırılmış grubu tanımlar. Her yakalanan sol açılı ayraç, `Open` grubunun yakalama koleksiyonuna gönderilir ve her yakalanan sağ açılı ayraç, `Close` grubunun yakalama koleksiyonuna gönderilir. Dengeleme grubu tanımı, her bir sol açılı ayraç için eşleşen bir sağ açılı ayraç olmasını sağlar. Aksi takdirde, `(?(Open)(?!))`son alt model yalnızca `Open` grubu boş olmadığında değerlendirilir (ve bu nedenle, iç içe yerleştirilmiş yapılar kapatıldıysa). Son alt model değerlendiriliyorsa, eşleşme başarısız olur, çünkü `(?!)` alt model her zaman başarısız olan sıfır Genişlik negatif ileriye yönelik bir onaylama yöntemidir.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Normal ifade deseninin:  
  
`^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$`  
  
 Normal ifade aşağıdaki gibi yorumlanır:  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Dizenin başlangıcında başlayın.|  
|`[^<>]*`|Sol veya sağ açılı parantez olmayan sıfır veya daha fazla karakterle eşleştirin.|  
|`(?'Open'<)`|Sol açılı köşeli ayracı eşleştirin ve `Open`adlı bir gruba atayın.|  
|`[^<>]*`|Sol veya sağ açılı parantez olmayan sıfır veya daha fazla karakterle eşleştirin.|  
|`((?'Open'<)[^<>]*)+`|Sol açılı köşeli ayracın bir veya daha fazla tekrarından sonra sıfır veya sol açılı köşeli ayraç olmayan bir veya daha fazla karakterle eşleştirin. Bu ikinci yakalama grubudur.|  
|`(?'Close-Open'>)`|Dik açılı köşeli ayracı eşleştirin, `Open` grubu ile geçerli grup arasındaki alt dizeyi `Close` grubuna atayın ve `Open` grubunun tanımını silin.|  
|`[^<>]*`|Sol veya sağ açılı parantez olmayan herhangi bir karakterin sıfır veya daha fazla tekrarını eşleştirin.|  
|`((?'Close-Open'>)[^<>]*)+`|Sağ açılı köşeli ayracın bir veya daha fazla tekrarını, ardından sıfır veya sağ açılı parantez olmayan herhangi bir karakterin sıfır veya daha fazla tekrarını eşleştirin. Sağ açılı köşeli ayracı eşleştirirken, `Open` grubu ile geçerli grup arasındaki alt dizeyi `Close` grubuna atayın ve `Open` grubunun tanımını silin. Bu, üçüncü yakalama grubudur.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Aşağıdaki düzenin sıfır veya daha fazla tekrarını eşleştir: sol açılı köşeli ayracın bir veya daha fazla tekrarı, ardından sıfır veya daha fazla açılı ayraç karakteri ve ardından sıfır veya daha fazla tekrardan oluşan bir veya daha fazla oluşum açılı olmayan köşeli ayraç. Sağ açılı ayraç eşleştirirken `Open` grubunun tanımını silin ve `Open` grubu ile geçerli grup arasındaki alt dizeyi `Close` grubuna atayın. Bu ilk yakalama grubudur.|  
|`(?(Open)(?!))`|`Open` grubu varsa, boş bir dize eşleştirilemezse eşleşmeyi iptal edin, ancak dizedeki normal ifade altyapısının konumunu ilerletin. Bu sıfır Genişlik negatif ileriye yönelik bir onaylama işlemi. Bir giriş dizesinde boş bir dize her zaman örtük olarak bulunduğundan, bu eşleşme her zaman başarısız olur. Bu eşleşmesinin başarısız olması, Açılı ayraçların dengelenmediğini belirtir.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 `(?(Open)(?!))`son alt ifadesi, giriş dizesindeki iç içe geçme yapılarının doğru şekilde dengelenip dengelenmediğini belirtir (örneğin, her bir sol açılı ayracın dik açılı ayraç ile eşleştiğini). Geçerli bir yakalanan gruba göre koşullu eşleme kullanır; daha fazla bilgi için bkz. [değişim yapıları](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md). `Open` grubu tanımlanmışsa, normal ifade altyapısı giriş dizesindeki `(?!)` alt ifade ile eşleştirmeye çalışır. `Open` grubu yalnızca iç içe yapılar dengesiz ise tanımlanmalıdır. Bu nedenle, giriş dizesinde eşleştirilecek model her zaman eşleşenlerin başarısız olmasına neden olan bir olmalıdır. Bu durumda, `(?!)` her zaman başarısız olan sıfır genişlikli negatif ileri düzey onaylama işlemi, giriş dizesindeki bir sonraki konumda boş bir dize her zaman örtük olarak açık bir şekilde vardır.  
  
 Örnekte, normal ifade altyapısı, aşağıdaki tabloda gösterildiği gibi "\<ABC > < MNO\<xyz > >" giriş dizesini değerlendirir.  
  
|Adım|Desen|Sonuç|  
|----------|-------------|------------|  
|1|`^`|Giriş dizesinin başlangıcında eşleşmeyi başlatır|  
|2|`[^<>]*`|Sol açılı ayraçtan önce açılı olmayan köşeli ayraç karakterleri arar; eşleşme bulmazsa.|  
|3|`(((?'Open'<)`|"\<ABC >" içindeki sol açılı parantezle eşleşir ve onu `Open` grubuna atar.|  
|4|`[^<>]*`|"Abc" ile eşleşir.|  
|5|`)+`|"< ABC" değeri, yakalanan ikinci grubun değeridir.<br /><br /> Giriş dizesindeki sonraki karakter sol açılı ayraç değildir, bu nedenle normal ifade altyapısı `(?'Open'<)[^<>]*)` alt düzenine geri döngülemez.|  
|6|`((?'Close-Open'>)`|"\<ABC >" içindeki sağ açılı parantezle eşleşir, `Open` grubu ile sağ açılı ayraç ile `Close` grubuna alt dize olan "abc" atar ve < grubunun geçerli değerini ("`Open`") siler ve boş bırakır.|  
|7|`[^<>]*`|Sağ açılı parantezden sonra açılı olmayan köşeli ayraç karakterleri arar; eşleşme buluyor.|  
|8|`)+`|Yakalanan üçüncü grubun değeri ">".<br /><br /> Giriş dizesindeki sonraki karakter sağ açılı ayraç değildir, bu nedenle normal ifade altyapısı `((?'Close-Open'>)[^<>]*)` alt düzenine geri döngülemez.|  
|9|`)*`|Yakalanan ilk grubun değeri "\<ABC >".<br /><br /> Giriş dizesindeki sonraki karakter sol açılı köşeli ayraç olduğundan, normal ifade altyapısı `(((?'Open'<)` alt düzenine geri döngü sağlar.|  
|10|`(((?'Open'<)`|"\<MNO" içindeki sol açılı parantezle eşleşir ve `Open` grubuna atar. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> koleksiyonu artık tek bir değer olan "<".|  
|11|`[^<>]*`|"MNO" ile eşleşir.|  
|12|`)+`|"< MNO" değeri, yakalanan ikinci grubun değeridir.<br /><br /> Giriş dizesindeki sonraki karakter bir sol açılı köşeli ayraç olduğundan, normal ifade altyapısı `(?'Open'<)[^<>]*)` alt düzenine geri döngü sağlar.|  
|13|`(((?'Open'<)`|"\<xyz >" içindeki sol açılı parantezle eşleşir ve onu `Open` grubuna atar. `Open` grubunun <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> koleksiyonu şu anda iki yakalama içerir: sol açılı ayraç "\<MNO" ve sol açılı ayraç "\<xyz >".|  
|14|`[^<>]*`|"XYZ" ile eşleşir.|  
|15|`)+`|"< XYZ", ikinci yakalanan grubun değeridir.<br /><br /> Giriş dizesindeki sonraki karakter sol açılı ayraç değildir, bu nedenle normal ifade altyapısı `(?'Open'<)[^<>]*)` alt düzenine geri döngülemez.|  
|16|`((?'Close-Open'>)`|"\<xyz >" içindeki sağ açılı parantezle eşleşir. "XYZ", `Open` grubu ile sağ açılı ayraç arasındaki alt dizeyi `Close` grubuna atar ve `Open` grubunun geçerli değerini siler. Önceki yakalamanın değeri ("\<MNO" içindeki sol açılı ayraç) `Open` grubunun geçerli değeri haline gelir. `Open` grubunun <xref:System.Text.RegularExpressions.Group.Captures%2A> koleksiyonu, "\<xyz >" olan sol açılı köşeli ayracını artık tek bir yakalama içerir.|  
|17|`[^<>]*`|Açı olmayan köşeli ayraç karakterleri arar; eşleşme buluyor.|  
|18|`)+`|Yakalanan üçüncü grubun değeri ">".<br /><br /> Giriş dizesindeki sonraki karakter sağ açılı bir köşeli ayraç olduğundan, normal ifade altyapısı `((?'Close-Open'>)[^<>]*)` alt düzenine geri döngü sağlar.|  
|19|`((?'Close-Open'>)`|"Xyz > >" içindeki son sağ açılı parantezle eşleşir, "MNO\<xyz >" (`Open` grubu ile sağ açılı ayraç arasındaki alt dize) `Close` grubuna atar ve `Open` grubunun geçerli değerini siler. `Open` grubu artık boş.|  
|20|`[^<>]*`|Açı olmayan köşeli ayraç karakterleri arar; eşleşme buluyor.|  
|21|`)+`|Yakalanan üçüncü grubun değeri ">".<br /><br /> Giriş dizesindeki sonraki karakter sağ açılı ayraç değildir, bu nedenle normal ifade altyapısı `((?'Close-Open'>)[^<>]*)` alt düzenine geri döngülemez.|  
|22|`)*`|Yakalanan ilk grubun değeri "< MNO\<xyz > >" değeridir.<br /><br /> Giriş dizesindeki sonraki karakter sol açılı ayraç değildir, bu nedenle normal ifade altyapısı `(((?'Open'<)` alt düzenine geri döngülemez.|  
|23|`(?(Open)(?!))`|`Open` grubu tanımlı değil, bu nedenle hiçbir eşleşme denenmedi.|  
|24|`$`|Giriş dizesinin sonuyla eşleşir.|  
  
<a name="noncapturing_group"></a>
## <a name="noncapturing-groups"></a>Yakalama Yapmayan Gruplar  
 Aşağıdaki gruplandırma yapısı bir alt ifade ile eşleşen alt dizeyi yakalamaz:  
  
`(?:subexpression)`
  
 Burada alt *ifade* geçerli bir normal ifade deseninin olduğu yerdir. Yakalama olmayan Grup yapısı genellikle bir gruba bir nicelik belirteci uygulandığında kullanılır, ancak grup tarafından yakalanan alt dizeler hiçbir ilgi değildir.  
  
> [!NOTE]
> Normal bir ifade iç içe gruplandırma yapıları içeriyorsa, iç içe geçmiş grup yapılarına bir dış yakalama olmayan Grup yapısı uygulanmaz.  
  
 Aşağıdaki örnek, yakalama olmayan gruplar içeren bir normal ifadeyi gösterir. Çıktının yakalanan grupları içermediğinden emin olmanız gerektiğini unutmayın.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Normal ifade `(?:\b(?:\w+)\W*)+\.` bir noktayla sonlandırılan bir cümle ile eşleşir. Normal ifade tek sözcüklerde değil, cümlelere odaklandığı ve gruplandırma yapıları özel olarak nicelik belirteçleri olarak kullanılır. Normal ifade deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?:\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Eşleşen metni yakalanan bir gruba atamayın.|  
|`\W*`|Sıfır veya daha fazla sözcük olmayan karakter eşleştirin.|  
|`(?:\b(?:\w+)\W*)+`|Bir sözcük sınırında başlayan bir veya daha fazla sözcük karakterinin örüntüsünün ardından sıfır veya daha fazla sözcük olmayan karakter, bir veya daha fazla kez olacak şekilde eşleştirin. Eşleşen metni yakalanan bir gruba atamayın.|  
|`\.`|Bir noktayla eşleştirin.|  
  
<a name="group_options"></a>
## <a name="group-options"></a>Grup Seçenekleri  
 Aşağıdaki gruplandırma yapısı, bir alt ifade içinde belirtilen seçenekleri uygular veya devre dışı bırakır:  
  
 `(?imnsx-imnsx:` alt *ifade* `)`  
  
 Burada alt *ifade* geçerli bir normal ifade deseninin olduğu yerdir. Örneğin `(?i-s:)`, büyük/küçük harf duyarlı modunu etkinleştirir ve tek satırlık modu devre dışı bırakır. Belirtebileceğiniz satır içi seçenekler hakkında daha fazla bilgi için bkz. [normal Ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
> Bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıf oluşturucusu veya statik bir yöntem kullanarak, bir alt ifade yerine tüm normal ifadeye uygulanan seçenekleri belirtebilirsiniz. Ayrıca, `(?imnsx-imnsx)` dil yapısını kullanarak, normal bir ifadede belirli bir noktadan sonra uygulanacak olan satır içi seçenekleri de belirtebilirsiniz.  
  
 Grup seçenekleri yapısı bir yakalama grubu değil. Diğer bir deyişle, alt *ifade* tarafından yakalanan bir dizenin herhangi bir bölümü eşleştirmeye dahil edilse de, yakalanan bir gruba dahil edilmez veya <xref:System.Text.RegularExpressions.GroupCollection> nesnesini doldurmak için kullanılır.  
  
 Örneğin, aşağıdaki örnekteki `\b(?ix: d \w+)\s` normal ifade, büyük/küçük harfe duyarsız eşleştirmeyi etkinleştirmek ve "d" harfiyle başlayan tüm sözcükleri tanımlamak için bir gruplandırma yapısında satır içi seçenekleri kullanır. Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?ix: d \w+)`|Büyük/küçük harf duyarsız eşleştirme ve bu düzende boşluk yok sayılıyor, "d" ile ve bir veya daha fazla sözcük karakteri ile eşleşir.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>
## <a name="zero-width-positive-lookahead-assertions"></a>Sıfır Genişlik Pozitif İleriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır genişlikli pozitif ileri yönlü bir onaylama işlemi tanımlar:  
  
 `(?=` alt *ifade* `)`  
  
 Burada alt *ifade* herhangi bir normal ifade deseninin olduğu yerdir. Bir eşleşmenin başarılı olması için, eşleşen alt dizenin eşleşme sonucuna dahil edilmemesine rağmen giriş dizesinin alt *ifade*içindeki normal ifade düzeniyle eşleşmesi gerekir. Sıfır genişlikli pozitif ileri yönlü onaylama işlemi geri izlememez.  
  
 Genellikle, normal ifade deseninin sonunda sıfır genişlikli pozitif ileri yönlü onaylama işlemi bulunur. Bir eşleşmenin gerçekleşmesi için bir dizenin sonunda bulunması gereken ancak eşleştirmeye dahil olmaması gereken bir alt dize tanımlar. Aşırı geri izlemeyi önlemek için de kullanışlıdır. Belirli bir yakalanan grubun, yakalanan grup için tanımlanan bir düzenin alt kümesiyle eşleşen metinle başladığından emin olmak için sıfır genişlikli pozitif ileriye yönelik bir onaylama işlemi kullanabilirsiniz. Örneğin, bir yakalama grubu ardışık sözcük karakterleriyle eşleşiyorsa, ilk karakterin alfabetik bir büyük harf karakter olmasını gerektirmek için sıfır genişlikli pozitif ileri yönlü bir onaylama işlemi kullanabilirsiniz.  
  
 Aşağıdaki örnek, giriş dizesinde "," fiilinin önündeki kelimeyi eşleştirmek için sıfır genişlikli pozitif ileriye yönelik bir onaylama işlemi kullanır.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 `\b\w+(?=\sis\b)` normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`(?=\sis\b)`|Sözcük karakterlerinin ardından bir boşluk karakteri ve "olup olmadığını" dizesinin bir sözcük sınırı üzerinde bittiğini belirleme. Öyleyse, eşleşme başarılı olur.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>
## <a name="zero-width-negative-lookahead-assertions"></a>Sıfır Genişlik Negatif İleriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır Genişlik negatif ileriye yönelik bir onaylama tanımlar:  
  
 `(?!` alt *ifade* `)`  
  
 Burada alt *ifade* herhangi bir normal ifade deseninin olduğu yerdir. Eşleşmenin başarılı olması için, eşleşen dize eşleşme sonucuna dahil olmasa da giriş dizesinin alt *ifade*içindeki normal ifade düzeniyle eşleşmesi gerekir.  
  
 Sıfır genişlikli negatif ileri yönlü onaylama genellikle normal bir ifadenin başında veya sonunda kullanılır. Normal bir ifadenin başlangıcında, normal ifadenin başlangıcı eşleşmesi gereken benzer ancak daha fazla genel bir model tanımladığı zaman eşleştirileceği belirli bir model tanımlayabilir. Bu durumda, genellikle geri izlemeyi sınırlandırmak için kullanılır. Normal bir ifadenin sonunda, bir eşleşmenin sonunda gerçekleşmeyecek bir alt ifade tanımlayabilir.  
  
 Aşağıdaki örnek, "un" ile başlamayan kelimeleri eşleştirmek için normal ifadenin başlangıcında sıfır genişlikli ileri yönlü bir onaylama işlemi kullanan bir normal ifade tanımlar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 `\b(?!un)\w+\b` normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?!un)`|Sonraki iki karakterin "un" olup olmadığını belirleme. Aksi takdirde eşleşme mümkündür.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Aşağıdaki örnek, bir noktalama karakteriyle bitolmayan kelimeleri eşleştirmek için normal ifadenin sonunda sıfır genişlikli ileri bir onaylama işlemi kullanan bir normal ifade tanımlar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 `\b\w+\b(?!\p{P})` normal ifade aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
|`\p{P})`|Sonraki karakter bir noktalama simgesi (nokta veya virgül gibi) değilse, eşleşme başarılı olur.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>
## <a name="zero-width-positive-lookbehind-assertions"></a>Sıfır Genişlik Pozitif Geriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır genişlikli pozitif geriye yönelik bir onaylama işlemi tanımlar:  
  
 `(?<=` alt *ifade* `)`  
  
 Burada alt *ifade* herhangi bir normal ifade deseninin olduğu yerdir. Bir eşleşmenin başarılı olması için, alt *ifade* geçerli konumun solundaki giriş dizesinde gerçekleşmelidir, ancak `subexpression` eşleşme sonucuna dahil edilmez. Sıfır genişlikli pozitif geriye yönelik onaylama işlemi geri izlememez.  
  
 Sıfır genişlikli pozitif geriye yönelik Onaylamalar genellikle normal ifadelerin başlangıcında kullanılır. Tanımladıkları model, eşleşme sonucunun bir parçası olmasa da bir eşleşmenin ön koşuludur.  
  
 Örneğin, aşağıdaki örnek, yirmi ilk yüzyıl için yılın son iki basamağıyla eşleşir (yani, "20" basamağının eşleşen dizeden önce gelmesini gerektirir).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Normal ifade deseninin `(?<=\b20)\d{2}\b`, aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`(?<=\b20)`|İki ondalık basamak bundan önce bir sözcük sınırında "20" ondalık haneleri içeriyorsa eşleştirmeye devam edin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Sıfır genişlikli pozitif geriye yönelik onaylar Ayrıca, yakalanan bir gruptaki son karakter veya karakterlerin, bu grubun normal ifade düzeniyle eşleşen karakterlerin bir alt kümesi olması gerektiğinde geri izlemeyi sınırlandırmak için de kullanılır. Örneğin, bir grup tüm ardışık kelime karakterlerini yakaladığında, son karakterin alfabetik olmasını gerektirmek için sıfır genişlikli pozitif geriye yönelik bir onaylama işlemi kullanabilirsiniz.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>
## <a name="zero-width-negative-lookbehind-assertions"></a>Sıfır Genişlik Negatif Geriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır Genişlik negatif geriye yönelik bir onaylama işlemi tanımlar:  
  
 `(?<!` alt *ifade* `)`  
  
 Burada alt *ifade* herhangi bir normal ifade deseninin olduğu yerdir. Bir eşleşmenin başarılı olması için alt *ifade* , geçerli konumun solundaki giriş dizesinde gerçekleşmemelidir. Ancak, `subexpression` eşleşmeyen herhangi bir alt dize, eşleşme sonucuna dahil edilmez.  
  
 Sıfır Genişlik negatif geriye yönelik onaylar genellikle normal ifadelerin başlangıcında kullanılır. Tanımladıkları model, izleyen dizedeki bir eşleşmeyi daha fazla haline aşıyor. Ayrıca, yakalanan bir gruptaki son karakter veya karakterlerin, bu grubun normal ifade düzeniyle eşleşen bir veya daha fazla karakter olmaması gerektiğinde geri izlemeyi sınırlandırmak için de kullanılır. Örneğin, bir grup tüm birbirini izleyen kelime karakterlerini yakaladığında, son karakterin alt çizgi (\_) olmasını gerektirmek için sıfır genişlikli pozitif geriye yönelik bir onaylama işlemi kullanabilirsiniz.  
  
 Aşağıdaki örnek, hafta sonu olmayan (yani, Cumartesi veya Pazar olmayan) haftanın herhangi bir gününe ait tarihle eşleşir.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Normal ifade deseninin `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b`, aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri ve ardından bir boşluk karakteri eşleştirin.|  
|`\d{1,2},`|Bir veya iki ondalık basamakla, sonra da boşluk karakteri ve virgül ile eşleştirin.|  
|`\d{4}\b`|Dört ondalık basamağı eşleştirin ve eşleşmeyi bir sözcük sınırında sonlandırın.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Eşleşmeden önce "Cumartesi" veya "Pazar" dizelerinden sonra bir boşluk gelmesi durumunda eşleşme başarılı olur.|  
  
<a name="atomic_groups"></a>
## <a name="atomic-groups"></a>Atomik gruplar  
 Aşağıdaki gruplandırma yapısı bir atomik grubu temsil eder (diğer bazı normal ifade altyapılarında geri alma olmayan alt ifade, atomik alt ifade veya yalnızca bir kez alt ifade olarak bilinir):
  
 `(?>` alt *ifade* `)`  
  
 Burada alt *ifade* herhangi bir normal ifade deseninin olduğu yerdir.  
  
 Genellikle, normal bir ifade isteğe bağlı veya alternatif eşleşen bir model içeriyorsa ve bir eşleşme başarılı olmazsa, normal ifade altyapısı, bir giriş dizesiyle bir Düzenle eşleştirmek için birden çok yönde Dalla çalışabilir. İlk dalı aldığında bir eşleşme bulunamazsa, normal ifade altyapısı ilk eşleşmeyi geçen noktaya yedekleyebilir veya geri izleyebilir ve ikinci dalı kullanarak eşleşmeyi dener. Bu işlem, tüm dallar denenene kadar devam edebilir.  
  
 `(?>`alt *ifade*`)` dil yapısı geri izlemeyi devre dışı bırakır. Normal ifade altyapısı, giriş dizesindeki gibi çok sayıda karakterle eşleştirecektir. Başka bir eşleşme mümkün olmadığında, alternatif kalıp eşleşmelerini denemek için geri izlemecektir. (Yani, alt ifade yalnızca alt ifade tarafından eşleştirilecek dizeleriyle eşleşir; alt ifadeyi ve bunu izleyen tüm alt ifadeleri temel alan bir dizeyle eşleştirmeye çalışmaz.)  
  
 Geri izlemenin başarısız olacağını biliyorsanız bu seçenek önerilir. Normal ifade altyapısının gereksiz arama gerçekleştirmesini önlemek performansı geliştirir.  
  
 Aşağıdaki örnek, bir atomik grubun bir model eşleşme sonuçlarını nasıl değiştirdiği gösterilmektedir. Geri izleme normal ifadesi, bir dizi yinelenen karakterle başarıyla eşleşir, ancak bir sözcük sınırında aynı karakterin daha fazla tekrarı gelir, ancak geri dönüş olmayan normal ifade değildir.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Geri dönüş olmayan normal ifade `(?>(\w)\1+).\b`, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(\w)`|Tek bir sözcük karakteriyle eşleştirin ve ilk yakalama grubuna atayın.|  
|`\1+`|İlk yakalanan alt dizenin değerini bir veya daha fazla kez eşleştirin.|  
|`.`|Herhangi bir karakterle eşleştirin.|  
|`\b`|Eşleşmeyi bir sözcük sınırında sonlandır.|  
|`(?>(\w)\1+)`|Yinelenen bir sözcük karakterinin bir veya daha fazla tekrarı ile eşleşir, ancak bir sözcük sınırının son karakteriyle eşleşecek şekilde geri izlememeyin.|  
  
<a name="Objects"></a>
## <a name="grouping-constructs-and-regular-expression-objects"></a>Yapıları ve Normal İfade Nesnelerini Gruplandırma  
 Normal bir ifade yakalama grubuyla eşleşen alt dizeler, <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> nesnesinden alınabilecek <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> nesneleri tarafından temsil edilir. <xref:System.Text.RegularExpressions.GroupCollection> nesnesi aşağıdaki gibi doldurulur:  
  
- Koleksiyondaki ilk <xref:System.Text.RegularExpressions.Group> nesnesi (sıfır dizinindeki nesne) tüm eşleşmeyi temsil eder.  
  
- Sonraki <xref:System.Text.RegularExpressions.Group> nesneleri kümesi adlandırılmamış (numaralandırılmış) yakalama gruplarını temsil eder. Bunlar, soldan sağa doğru normal ifadede tanımlandıkları sırada görünürler. Bu grupların Dizin değerleri 1 ' den koleksiyondaki adlandırılmamış yakalama grupları sayısına göre değişir. (Belirli bir grubun dizini numaralandırılmış geribaşvuruya eşdeğerdir. Geri başvurular hakkında daha fazla bilgi için bkz. [Backreference yapıları](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)  
  
- <xref:System.Text.RegularExpressions.Group> nesnelerinin son kümesi, adlandırılmış yakalama gruplarını temsil eder. Bunlar, soldan sağa doğru normal ifadede tanımlandıkları sırada görünürler. İlk adlandırılmış yakalama grubunun dizin değeri, son adlandırılmamış yakalama grubunun dizininden bir daha büyük. Normal ifadede adlandırılmamış bir yakalama grubu yoksa, ilk adlandırılmış yakalama grubunun dizin değeri bir olur.  
  
 Bir yakalama grubuna nicelik belirteci uygularsanız, karşılık gelen <xref:System.Text.RegularExpressions.Group> nesnenin <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>, <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType>ve <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> özellikleri bir yakalama grubu tarafından yakalanan son alt dizeyi yansıtır. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Text.RegularExpressions.CaptureCollection> nesnesinden nicelik belirteçleri olan gruplar tarafından yakalanan tüm alt dizeler kümesini alabilirsiniz.  
  
 Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Group> ve <xref:System.Text.RegularExpressions.Capture> nesneleri arasındaki ilişkiyi açıklar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Normal ifade deseninin `(\b(\w+)\W+)+` bir dizeden bağımsız sözcükleri ayıklar. Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Birlikte, bu karakterler bir kelime oluşturur. Bu ikinci yakalama grubudur.|  
|`\W+`|Bir veya daha fazla sözcük olmayan karakteri eşleştirin.|  
|`(\b(\w+)\W+)`|Bir veya daha fazla sözcük karakteri ve ardından bir veya daha fazla sözcük olmayan karakter örüntüsünün bir veya daha fazla kez eşleşmesini eşleştirin. Bu ilk yakalama grubudur.|  
  
 İkinci yakalama grubu, cümlenin her sözcüğüyle eşleşir. İlk yakalama grubu, sözcüğü izleyen noktalama ve boşluk ile birlikte her sözcükle eşleşir. Dizini 2 olan <xref:System.Text.RegularExpressions.Group> nesnesi ikinci yakalama grubuyla eşleşen metin hakkında bilgi sağlar. Yakalama grubu tarafından yakalanan tüm sözcüklerin kümesi, <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Text.RegularExpressions.CaptureCollection> nesnesinden bulunabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
