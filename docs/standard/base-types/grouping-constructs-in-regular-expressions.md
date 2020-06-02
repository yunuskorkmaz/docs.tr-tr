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
ms.openlocfilehash: 5be98a5a213592b169bee430d84c4fc3a1d5fcef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290532"
---
# <a name="grouping-constructs-in-regular-expressions"></a>Normal İfadelerdeki Gruplandırma Yapıları
Yapıları gruplandırma, normal bir ifadenin alt ifadelerini ayırıcıları ve bir giriş dizesinin alt dizelerini yakalar. Aşağıdakileri yapmak için gruplandırma yapılarını kullanabilirsiniz:  
  
- Giriş dizesinde yinelenen bir alt ifadeyi eşleştirin.  
  
- Birden çok normal ifade dili öğesine sahip olan bir alt ifade için nicelik belirteci uygulayın. Nicelik belirteçleri hakkında daha fazla bilgi için bkz. [nicelik belirteçleri](quantifiers-in-regular-expressions.md).  
  
- Ve yöntemleri tarafından döndürülen dizeye bir alt ifade ekleyin <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> .  
  
- Özellikten tek tek alt ifadeleri alın <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> ve eşleşen metinden bir bütün olarak onları ayrı olarak işleyin.  
  
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
  
 `(`alt *ifade*`)`  
  
 Burada alt *ifade* geçerli bir normal ifade deseninin olduğu yerdir. Parantez kullanan yakalamalar, normal ifadede yer alan açılış parantezleri sırasına göre otomatik olarak soldan sağa numaralandırılır. Sıfır Numaralandırılmış yakalama, tüm normal ifade deseninin eşleştirildiği metindir.  
  
> [!NOTE]
> Varsayılan olarak, alt `(` *ifade* `)` Language öğesi eşleşen alt ifadeyi yakalar. Ancak <xref:System.Text.RegularExpressions.RegexOptions> , bir normal ifade deseninin eşleştirme yönteminin parametresi <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> bayrağını içeriyorsa veya `n` seçenek bu alt ifadeye uygulanmışsa (Bu konunun ilerleyen kısımlarında [Grup seçeneklerine](#group_options) bakın), eşleşen alt ifade yakalanmaz.  
  
 Yakalanan gruplara dört şekilde erişebilirsiniz:  
  
- Normal ifade içinde geri başvuru yapısını kullanarak. Eşleşen alt ifadeye, söz dizimi numarası kullanılarak aynı normal ifadede başvurulur `\` *number*, burada *sayı* yakalanan alt ifadenin sıra numarasıdır.  
  
- Normal ifade içinde adlandırılmış yeniden başvuru yapısını kullanarak. Eşleşen alt ifadeye, sözdizimi adı kullanılarak aynı normal ifadede başvurulur `\k<` *name* `>` ; burada *ad* bir yakalama grubunun adı veya `\k<` *sayı* `>` , burada *sayı* bir yakalama grubunun sıra numarasıdır. Yakalama grubu, sıra numarasıyla aynı olan varsayılan bir ada sahiptir. Daha fazla bilgi için bu konunun ilerleyen kısımlarında bulunan [eşleşen alt ifadeler](#named_matched_subexpression) bölümüne bakın.  
  
- `$`Bir veya yöntem çağrısında *sayı* değiştirme sırasını kullanarak <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> , *sayı* yakalanan alt ifadenin sıra numarasıdır.  
  
- Program aracılığıyla, <xref:System.Text.RegularExpressions.GroupCollection> özelliği tarafından döndürülen nesnesini kullanarak <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> . Koleksiyonda sıfır konumundaki üye, tüm normal ifade eşleşmesini temsil eder. Sonraki her üye, eşleşen bir alt ifadeyi temsil eder. Daha fazla bilgi için bkz. [Grup yapıları ve normal Ifade nesneleri](#Objects) bölümü.  
  
 Aşağıdaki örnek, metinde yinelenen sözcükleri tanımlayan bir normal ifadeyi gösterir. Normal ifade deseninin iki yakalama grubu, yinelenen sözcüğün iki örneğini temsil eder. İkinci örnek, giriş dizesindeki başlangıç konumunu raporlamak için yakalanır.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Normal ifade deseninin nedeni şunlardır:  
  
`(\w+)\s(\1)\W`  
  
 Aşağıdaki tabloda, normal ifade deseninin nasıl yorumlanacağı gösterilmektedir.  
  
|Desen|Description|  
|-------------|-----------------|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\1)`|Yakalanan ilk gruptaki dizeyle eşleştirin. Bu ikinci yakalama grubudur. Örnek, yinelenen sözcüğün başlangıç konumunun özelliğinden alınabilmesi için onu yakalanan bir gruba atar `Match.Index` .|  
|`\W`|Boşluk ve noktalama işaretleri de dahil olmak üzere sözcüksiz bir karakterle eşleştirin. Bu, normal ifade deseninin, ilk yakalanan gruptan kelimeyle başlayan bir sözcükle eşleşmesini önler.|  
  
<a name="named_matched_subexpression"></a>
## <a name="named-matched-subexpressions"></a>Adlandırılmış Eşleşen Alt İfadeler  
 Aşağıdaki gruplandırma yapısı eşleşen bir alt ifadeyi yakalar ve ada veya numaraya göre erişmenizi sağlar:  
  
`(?<name>subexpression)`  
  
 veya:  
  
`(?'name'subexpression)`  
  
 Burada *Name* geçerli bir grup adıdır ve alt *ifade* geçerli bir normal ifade örüntü. *ad* , herhangi bir noktalama karakteri içermemelidir ve bir sayıyla başlayamaz.  
  
> [!NOTE]
> <xref:System.Text.RegularExpressions.RegexOptions>Bir normal ifade deseninin eşleştirme yönteminin parametresi <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> bayrağını içeriyorsa veya `n` seçenek bu alt ifadeye uygulanmışsa (Bu konunun Ilerleyen kısımlarında bulunan [Grup seçeneklerine](#group_options) bakın), bir alt ifadeyi yakalamaya yönelik tek yol, yakalama gruplarının açıkça adı olarak adlandırılmalıdır.  
  
 Adlandırılmış yakalanan gruplara aşağıdaki yollarla erişebilirsiniz:  
  
- Normal ifade içinde adlandırılmış yeniden başvuru yapısını kullanarak. Eşleşen alt ifadeye, sözdizimi adı kullanılarak aynı normal ifadede başvurulur `\k<` *name* `>` ; burada *ad* , yakalanan alt ifadenin adıdır.  
  
- Normal ifade içinde geri başvuru yapısını kullanarak. Eşleşen alt ifadeye, söz dizimi numarası kullanılarak aynı normal ifadede başvurulur `\` *number*, burada *sayı* yakalanan alt ifadenin sıra numarasıdır. Adlandırılmış eşleşen alt ifadeler, eşleşen alt ifadelerden sonra soldan sağa doğru numaralandırılır.  
  
- `${` *name* `}` Bir veya yöntem çağrısında ad değiştirme sırasını kullanarak <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> , *adı* yakalanan alt ifadenin adıdır.  
  
- `$`Bir veya yöntem çağrısında *sayı* değiştirme sırasını kullanarak <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> , *sayı* yakalanan alt ifadenin sıra numarasıdır.  
  
- Program aracılığıyla, <xref:System.Text.RegularExpressions.GroupCollection> özelliği tarafından döndürülen nesnesini kullanarak <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> . Koleksiyonda sıfır konumundaki üye, tüm normal ifade eşleşmesini temsil eder. Sonraki her üye, eşleşen bir alt ifadeyi temsil eder. Adlandırılmış yakalanan gruplar, yakalanan grupların numaralandırıldıktan sonra koleksiyonda depolanır.  
  
- Programlama yoluyla, <xref:System.Text.RegularExpressions.GroupCollection> nesnenin dizin oluşturucusuna (C# ' de) veya <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> özelliğine (Visual Basic) alt ifade adı sağlayarak.  
  
 Basit bir normal ifade modelinde, numaralandırılmış (adlandırılmamış) ve adlandırılmış grupların programlı olarak veya normal ifade dili sözdizimi kullanılarak nasıl başvurulabileceği gösterilmektedir. Normal ifade, `((?<One>abc)\d+)?(?<Two>xyz)(.*)` aşağıdaki yakalama gruplarını numaraya göre ve adına göre oluşturur. İlk yakalama grubu (sayı 0) her zaman tüm modele başvurur.  
  
|Sayı|Name|Desen|  
|------------|----------|-------------|  
|0|0 (varsayılan ad)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1|1 (varsayılan ad)|`((?<One>abc)\d+)`|  
|2|2 (varsayılan ad)|`(.*)`|  
|3|Bir|`(?<One>abc)`|  
|4|İki|`(?<Two>xyz)`|  
  
 Aşağıdaki örnek, yinelenen kelimeleri ve her bir yinelenen sözcüğü hemen izleyen kelimeyi tanımlayan bir normal ifade gösterir. Normal ifade deseninin iki adlandırılmış alt ifadesi tanımlar: `duplicateWord` , çoğaltılan kelimeyi temsil `nextWord` eden ve yinelenen kelimeyi izleyen kelimeyi temsil eden.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Normal ifade deseninin aşağıdaki gibidir:  
  
`(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)`  
  
 Aşağıdaki tabloda, normal ifadenin nasıl yorumlanacağı gösterilmektedir.  
  
|Desen|Description|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunu adlandırın `duplicateWord` .|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`\k<duplicateWord>`|Adlı yakalanan gruptaki dizeyle eşleştirin `duplicateWord` .|  
|`\W`|Boşluk ve noktalama işaretleri de dahil olmak üzere sözcüksiz bir karakterle eşleştirin. Bu, normal ifade deseninin, ilk yakalanan gruptan kelimeyle başlayan bir sözcükle eşleşmesini önler.|  
|`(?<nextWord>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunu adlandırın `nextWord` .|  
  
 Bir grup adının normal bir ifadede tekrarlanabilir olduğunu unutmayın. Örneğin, aşağıdaki örnekte gösterildiği gibi, birden fazla grubun adlandırılması mümkündür `digit` . Yinelenen adlar söz konusu olduğunda, <xref:System.Text.RegularExpressions.Group> nesne değeri giriş dizesindeki son başarılı yakalama tarafından belirlenir. Bunlara ek olarak, <xref:System.Text.RegularExpressions.CaptureCollection> Grup adı yinelenmediğinden olduğu gibi her yakalama hakkındaki bilgilerle doldurulur.  
  
 Aşağıdaki örnekte, normal ifade `\D+(?<digit>\d+)\D+(?<digit>\d+)?` adlı bir grubun iki örneğini içerir `digit` . İlk `digit` adlandırılmış grup bir veya daha fazla rakam karakteri yakalar. İkinci `digit` adlandırılmış Grup, bir veya daha fazla basamak karakterinin sıfır veya bir oluşumunu yakalar. Örneğin çıkışının gösterdiği gibi, ikinci yakalama grubu metinle başarıyla eşleşiyorsa, metnin değeri nesnenin değerini tanımlar <xref:System.Text.RegularExpressions.Group> . İkinci yakalama grubu giriş dizesiyle eşleşmezse, son başarılı eşleşmenin değeri nesnenin değerini tanımlar <xref:System.Text.RegularExpressions.Group> .  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 Aşağıdaki tabloda, normal ifadenin nasıl yorumlanacağı gösterilmektedir.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\D+`|Ondalık olmayan bir veya daha fazla karakter eşleştirin.|  
|`(?<digit>\d+)`|Bir veya daha fazla ondalık basamak karakteri eşleştirin. Eşleşmeyi `digit` adlandırılmış gruba atayın.|  
|`\D+`|Ondalık olmayan bir veya daha fazla karakter eşleştirin.|  
|`(?<digit>\d+)?`|Bir veya daha fazla ondalık basamak karakterinin sıfır veya bir oluşumunu eşleştirin. Eşleşmeyi `digit` adlandırılmış gruba atayın.|  
  
<a name="balancing_group_definition"></a>
## <a name="balancing-group-definitions"></a>Grup Tanımlarını Dengeleme  
 Bir Dengeleme grubu tanımı, daha önce tanımlanmış bir grubun tanımını ve geçerli grupta, daha önce tanımlanan grup ve geçerli grup arasındaki aralığı siler. Bu gruplandırma yapısı aşağıdaki biçimdedir:  
  
`(?<name1-name2>subexpression)`  
  
 veya:  
  
`(?'name1-name2' subexpression)`
  
 Burada *name1* geçerli grup (isteğe bağlı) ise, *AD2* daha önce tanımlanmış bir gruptur ve alt *ifade* geçerli bir normal ifade örünyordu. Dengeleme grubu tanımı, *AD2* tanımını siler ve *name1*içinde *AD2* ve *name1* arasındaki aralığı depolar. Hiçbir *AD2* grubu tanımlanmamışsa, eşleşme geri izler. N} öğesinin son tanımını silmek, *AD2* *'ın önceki tanımını ortaya* çıkardığı için, bu yapı, boşluk olarak grup *AD2* için yakalama yığınını, parantez gibi iç içe yapıları izlemek için bir sayaç olarak kullanmanıza olanak sağlar.  
  
 Dengeleme grubu tanımı bir yığın olarak *AD2* kullanır. İç içe yerleştirilmiş her yapının başlangıç karakteri gruba ve <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> koleksiyonuna yerleştirilir. Kapanış karakteri eşleştiğinde, karşılık gelen açma karakteri gruptan kaldırılır ve <xref:System.Text.RegularExpressions.Group.Captures%2A> koleksiyon bir ile azaltılır. Tüm iç içe yapıların açılış ve kapanış karakterleri eşleştirdikten sonra, *AD2* boş olur.  
  
> [!NOTE]
> Aşağıdaki örnekte yer alan, iç içe bir yapının uygun açılış ve kapanış karakterini kullanmak için normal ifadeyi değiştirdikten sonra, matematiksel ifadeler veya birden çok iç içe geçmiş yöntem çağrısı içeren program kodu satırları gibi iç içe geçmiş yapıları işlemek için kullanabilirsiniz.  
  
 Aşağıdaki örnek, bir giriş dizesinde Left ve Right açılı ayraçları (<>) ile eşleştirmek için bir Dengeleme grubu tanımı kullanır. Örnek, `Open` `Close` eşleşen açılı ayraç çiftlerini izlemek için bir yığın gibi kullanılan iki adlandırılmış grubu tanımlar. Her yakalanan sol açılı ayraç grubun yakalama koleksiyonuna gönderilir `Open` ve her yakalanan sağ açılı ayraç grubun yakalama koleksiyonuna gönderilir `Close` . Dengeleme grubu tanımı, her bir sol açılı ayraç için eşleşen bir sağ açılı ayraç olmasını sağlar. Aksi takdirde, son alt model `(?(Open)(?!))` yalnızca `Open` Grup boş değilse değerlendirilir (ve bu nedenle, iç içe yerleştirilmiş tüm yapılar kapatılmamıştır). Son alt model değerlendiriliyorsa, eşleştirme başarısız olur, çünkü `(?!)` alt model her zaman başarısız olan sıfır Genişlik negatif ileriye yönelik bir onaylama yöntemidir.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Normal ifade deseninin:  
  
`^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$`  
  
 Normal ifade aşağıdaki gibi yorumlanır:  
  
|Desen|Description|  
|-------------|-----------------|  
|`^`|Dizenin başlangıcında başlayın.|  
|`[^<>]*`|Sol veya sağ açılı parantez olmayan sıfır veya daha fazla karakterle eşleştirin.|  
|`(?'Open'<)`|Sol açılı köşeli ayracı eşleştirin ve adlı bir gruba atayın `Open` .|  
|`[^<>]*`|Sol veya sağ açılı parantez olmayan sıfır veya daha fazla karakterle eşleştirin.|  
|`((?'Open'<)[^<>]*)+`|Sol açılı köşeli ayracın bir veya daha fazla tekrarından sonra sıfır veya sol açılı köşeli ayraç olmayan bir veya daha fazla karakterle eşleştirin. Bu ikinci yakalama grubudur.|  
|`(?'Close-Open'>)`|Sağ açılı köşeli ayracı eşleştirin, `Open` Grup ve geçerli grup arasındaki alt dizeyi `Close` gruba atayın ve grubun tanımını silin `Open` .|  
|`[^<>]*`|Sol veya sağ açılı parantez olmayan herhangi bir karakterin sıfır veya daha fazla tekrarını eşleştirin.|  
|`((?'Close-Open'>)[^<>]*)+`|Sağ açılı köşeli ayracın bir veya daha fazla tekrarını, ardından sıfır veya sağ açılı parantez olmayan herhangi bir karakterin sıfır veya daha fazla tekrarını eşleştirin. Sağ açılı köşeli ayracı eşleştirirken grup `Open` ve geçerli grup arasındaki alt dizeyi `Close` gruba atayın ve grubun tanımını silin `Open` . Bu, üçüncü yakalama grubudur.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Aşağıdaki düzenin sıfır veya daha fazla tekrarını eşleştirin: sol açılı köşeli ayracın bir veya daha fazla tekrarı, ardından sıfır veya daha fazla açılı ayraç karakteri ve ardından sıfır veya daha fazla açılı ayracın bir veya daha fazla tekrarı tarafından izlenen bir ya da daha fazla açı köşeli ayraçın bir veya daha fazla tekrarı. Sağ açılı ayraç eşleştirirken, grubun tanımını silin `Open` ve grup `Open` ile geçerli grup arasındaki alt dizeyi gruba atayın `Close` . Bu ilk yakalama grubudur.|  
|`(?(Open)(?!))`|`Open`Grup varsa, boş bir dize eşleştirilemezse eşleşmeyi iptal edin, ancak dizedeki normal ifade altyapısının konumunu ilerletin. Bu sıfır Genişlik negatif ileriye yönelik bir onaylama işlemi. Bir giriş dizesinde boş bir dize her zaman örtük olarak bulunduğundan, bu eşleşme her zaman başarısız olur. Bu eşleşmesinin başarısız olması, Açılı ayraçların dengelenmediğini belirtir.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 Son alt ifade, `(?(Open)(?!))` Giriş dizesindeki iç içe geçme yapılarının düzgün şekilde dengelenip dengelenmediğini belirtir (örneğin, her bir sol açılı ayracın dik açılı ayraç ile eşleştiğini belirtir). Geçerli bir yakalanan gruba göre koşullu eşleme kullanır; daha fazla bilgi için bkz. [değişim yapıları](alternation-constructs-in-regular-expressions.md). `Open`Grup tanımlanmışsa, normal ifade altyapısı giriş dizesindeki alt ifadeyi eşleştirmeye çalışır `(?!)` . `Open`Grup yalnızca iç içe yapılar dengesiz ise tanımlanmalıdır. Bu nedenle, giriş dizesinde eşleştirilecek model her zaman eşleşenlerin başarısız olmasına neden olan bir olmalıdır. Bu durumda, `(?!)` her zaman başarısız olan sıfır Genişlik negatif ileriye yönelik bir onaylama işlemi, giriş dizesindeki bir sonraki konumda boş bir dize her zaman örtük olarak yer almıyor.  
  
 Örnekte, normal ifade altyapısı, \<abc> Aşağıdaki tabloda gösterildiği gibi "<MNO>" giriş dizesini değerlendirir \<xyz> .  
  
|Adım|Desen|Sonuç|  
|----------|-------------|------------|  
|1|`^`|Giriş dizesinin başlangıcında eşleşmeyi başlatır|  
|2|`[^<>]*`|Sol açılı ayraçtan önce açılı olmayan köşeli ayraç karakterleri arar; eşleşme bulmazsa.|  
|3|`(((?'Open'<)`|"" İçindeki sol açılı parantezle eşleşir \<abc> ve `Open` gruba atar.|  
|4|`[^<>]*`|"Abc" ile eşleşir.|  
|5|`)+`|"<ABC" değeri, yakalanan ikinci grubun değeridir.<br /><br /> Giriş dizesindeki sonraki karakter sol açılı ayraç değildir, bu nedenle normal ifade altyapısı alt modele geri döngülemez `(?'Open'<)[^<>]*)` .|  
|6|`((?'Close-Open'>)`|"" İçindeki sağ açılı parantezle eşleşir, Grup \<abc> ile sağ açılı ayraç arasında alt dize olan "abc" atar `Open` `Close` ve grubun geçerli değerini ("<") siler ve `Open` boş bırakır.|  
|7|`[^<>]*`|Sağ açılı parantezden sonra açılı olmayan köşeli ayraç karakterleri arar; eşleşme buluyor.|  
|8|`)+`|Yakalanan üçüncü grubun değeri ">".<br /><br /> Giriş dizesindeki sonraki karakter sağ açılı ayraç değildir, bu nedenle normal ifade altyapısı alt modele geri döngülemez `((?'Close-Open'>)[^<>]*)` .|  
|9|`)*`|Yakalanan ilk grubun değeri " \<abc> ".<br /><br /> Giriş dizesindeki sonraki karakter sol açılı köşeli ayraçdır, bu nedenle normal ifade altyapısı alt modele geri döngü sağlar `(((?'Open'<)` .|  
|10|`(((?'Open'<)`|" \<mno" and assigns it to the `Open` group. Its <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Koleksiyonda artık tek bir değer," < "olan sol açılı parantezle eşleşir.|  
|11|`[^<>]*`|"MNO" ile eşleşir.|  
|12|`)+`|"<MNO" değeri, yakalanan ikinci grubun değeridir.<br /><br /> Giriş dizesindeki sonraki karakter bir sol açılı köşeli ayraç, bu nedenle normal ifade altyapısı alt modele geri döngü sağlar `(?'Open'<)[^<>]*)` .|  
|13|`(((?'Open'<)`|"" İçindeki sol açılı parantezle eşleşir \<xyz> ve `Open` gruba atar. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> `Open` Grubun koleksiyonu şu anda iki yakalama içerir: sol açılı köşeli ayraç " \<mno", and the left angle bracket from "\<xyz> ".|  
|14|`[^<>]*`|"XYZ" ile eşleşir.|  
|15|`)+`|"<XYZ", ikinci yakalanan grubun değeridir.<br /><br /> Giriş dizesindeki sonraki karakter sol açılı ayraç değildir, bu nedenle normal ifade altyapısı alt modele geri döngülemez `(?'Open'<)[^<>]*)` .|  
|16|`((?'Close-Open'>)`|"" İçindeki sağ açılı parantezle eşleşir \<xyz> . "XYZ", Grup `Open` ile sağ açılı ayraç arasına alt dizeyi atar `Close` ve grubun geçerli değerini siler `Open` . Önceki yakalamanın değeri (grubun sol açılı ayraç \<mno") becomes the current value of the `Open` group. The <xref:System.Text.RegularExpressions.Group.Captures%2A> `Open` , "", sol açılı ayraç olan tek bir yakalama içerir \<xyz> .|  
|17|`[^<>]*`|Açı olmayan köşeli ayraç karakterleri arar; eşleşme buluyor.|  
|18|`)+`|Yakalanan üçüncü grubun değeri ">".<br /><br /> Giriş dizesindeki sonraki karakter sağ açılı bir köşeli ayraçdır, bu nedenle normal ifade altyapısı alt modele geri döngü sağlar `((?'Close-Open'>)[^<>]*)` .|  
|19|`((?'Close-Open'>)`|"Xyz>>" içindeki son sağ açılı parantezle eşleşir, "MNO \<xyz> " ( `Open` Grup ve sağ açılı ayraç arasındaki alt dize) `Close` gruba atar ve grubun geçerli değerini siler `Open` . `Open`Grup artık boş.|  
|20|`[^<>]*`|Açı olmayan köşeli ayraç karakterleri arar; eşleşme buluyor.|  
|21|`)+`|Yakalanan üçüncü grubun değeri ">".<br /><br /> Giriş dizesindeki sonraki karakter sağ açılı ayraç değildir, bu nedenle normal ifade altyapısı alt modele geri döngülemez `((?'Close-Open'>)[^<>]*)` .|  
|22|`)*`|Yakalanan ilk grubun değeri "<MNO \<xyz>>".<br /><br /> Giriş dizesindeki sonraki karakter sol açılı ayraç değildir, bu nedenle normal ifade altyapısı alt modele geri döngülemez `(((?'Open'<)` .|  
|23|`(?(Open)(?!))`|`Open`Grup tanımlı değil, bu nedenle hiçbir eşleşme denenmedi.|  
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
  
 Normal ifade, `(?:\b(?:\w+)\W*)+\.` bir noktayla sonlandırılan bir cümle ile eşleşir. Normal ifade tek sözcüklerde değil, cümlelere odaklandığı ve gruplandırma yapıları özel olarak nicelik belirteçleri olarak kullanılır. Normal ifade deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?:\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Eşleşen metni yakalanan bir gruba atamayın.|  
|`\W*`|Sıfır veya daha fazla sözcük olmayan karakter eşleştirin.|  
|`(?:\b(?:\w+)\W*)+`|Bir sözcük sınırında başlayan bir veya daha fazla sözcük karakterinin örüntüsünün ardından sıfır veya daha fazla sözcük olmayan karakter, bir veya daha fazla kez olacak şekilde eşleştirin. Eşleşen metni yakalanan bir gruba atamayın.|  
|`\.`|Bir noktayla eşleştirin.|  
  
<a name="group_options"></a>
## <a name="group-options"></a>Grup Seçenekleri  
 Aşağıdaki gruplandırma yapısı, bir alt ifade içinde belirtilen seçenekleri uygular veya devre dışı bırakır:  
  
 `(?imnsx-imnsx:`alt *ifade*`)`  
  
 Burada alt *ifade* geçerli bir normal ifade deseninin olduğu yerdir. Örneğin, `(?i-s:)` büyük/küçük harf duyarlı modunu etkinleştirir ve tek satırlık modu devre dışı bırakır. Belirtebileceğiniz satır içi seçenekler hakkında daha fazla bilgi için bkz. [normal Ifade seçenekleri](regular-expression-options.md).  
  
> [!NOTE]
> Bir sınıf oluşturucusu veya statik bir yöntem kullanarak, bir alt ifade yerine tüm normal ifadeye uygulanan seçenekleri belirtebilirsiniz <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> . Ayrıca, bir normal ifadede belirli bir noktadan sonra, dil yapısını kullanarak uygulanan satır içi seçenekleri de belirtebilirsiniz `(?imnsx-imnsx)` .  
  
 Grup seçenekleri yapısı bir yakalama grubu değil. Diğer bir deyişle, alt *ifade* tarafından yakalanan bir dizenin herhangi bir kısmı eşleştirmeye dahil edilse de, yakalanan bir grupta yer almaz ve nesneyi doldurmak için kullanılır <xref:System.Text.RegularExpressions.GroupCollection> .  
  
 Örneğin, aşağıdaki örnekteki normal ifade, `\b(?ix: d \w+)\s` büyük/küçük harfe duyarsız eşleştirmeyi etkinleştirmek ve "d" harfiyle başlayan tüm sözcükleri tanımlamak için bir gruplandırma yapısında satır içi seçenekler kullanır. Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?ix: d \w+)`|Büyük/küçük harf duyarsız eşleştirme ve bu düzende boşluk yok sayılıyor, "d" ile ve bir veya daha fazla sözcük karakteri ile eşleşir.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>
## <a name="zero-width-positive-lookahead-assertions"></a>Sıfır Genişlik Pozitif İleriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır genişlikli pozitif ileri yönlü bir onaylama işlemi tanımlar:  
  
 `(?=`alt *ifade*`)`  
  
 Burada alt *ifade* herhangi bir normal ifade deseninin olduğu yerdir. Bir eşleşmenin başarılı olması için, eşleşen alt dizenin eşleşme sonucuna dahil edilmemesine rağmen giriş dizesinin alt *ifade*içindeki normal ifade düzeniyle eşleşmesi gerekir. Sıfır genişlikli pozitif ileri yönlü onaylama işlemi geri izlememez.  
  
 Genellikle, normal ifade deseninin sonunda sıfır genişlikli pozitif ileri yönlü onaylama işlemi bulunur. Bir eşleşmenin gerçekleşmesi için bir dizenin sonunda bulunması gereken ancak eşleştirmeye dahil olmaması gereken bir alt dize tanımlar. Aşırı geri izlemeyi önlemek için de kullanışlıdır. Belirli bir yakalanan grubun, yakalanan grup için tanımlanan bir düzenin alt kümesiyle eşleşen metinle başladığından emin olmak için sıfır genişlikli pozitif ileriye yönelik bir onaylama işlemi kullanabilirsiniz. Örneğin, bir yakalama grubu ardışık sözcük karakterleriyle eşleşiyorsa, ilk karakterin alfabetik bir büyük harf karakter olmasını gerektirmek için sıfır genişlikli pozitif ileri yönlü bir onaylama işlemi kullanabilirsiniz.  
  
 Aşağıdaki örnek, giriş dizesinde "," fiilinin önündeki kelimeyi eşleştirmek için sıfır genişlikli pozitif ileriye yönelik bir onaylama işlemi kullanır.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Normal ifade `\b\w+(?=\sis\b)` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`(?=\sis\b)`|Sözcük karakterlerinin ardından bir boşluk karakteri ve "olup olmadığını" dizesinin bir sözcük sınırı üzerinde bittiğini belirleme. Öyleyse, eşleşme başarılı olur.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>
## <a name="zero-width-negative-lookahead-assertions"></a>Sıfır Genişlik Negatif İleriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır Genişlik negatif ileriye yönelik bir onaylama tanımlar:  
  
 `(?!`alt *ifade*`)`  
  
 Burada alt *ifade* herhangi bir normal ifade deseninin olduğu yerdir. Eşleşmenin başarılı olması için, eşleşen dize eşleşme sonucuna dahil olmasa da giriş dizesinin alt *ifade*içindeki normal ifade düzeniyle eşleşmesi gerekir.  
  
 Sıfır genişlikli negatif ileri yönlü onaylama genellikle normal bir ifadenin başında veya sonunda kullanılır. Normal bir ifadenin başlangıcında, normal ifadenin başlangıcı eşleşmesi gereken benzer ancak daha fazla genel bir model tanımladığı zaman eşleştirileceği belirli bir model tanımlayabilir. Bu durumda, genellikle geri izlemeyi sınırlandırmak için kullanılır. Normal bir ifadenin sonunda, bir eşleşmenin sonunda gerçekleşmeyecek bir alt ifade tanımlayabilir.  
  
 Aşağıdaki örnek, "un" ile başlamayan kelimeleri eşleştirmek için normal ifadenin başlangıcında sıfır genişlikli ileri yönlü bir onaylama işlemi kullanan bir normal ifade tanımlar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Normal ifade `\b(?!un)\w+\b` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?!un)`|Sonraki iki karakterin "un" olup olmadığını belirleme. Aksi takdirde eşleşme mümkündür.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Aşağıdaki örnek, bir noktalama karakteriyle bitolmayan kelimeleri eşleştirmek için normal ifadenin sonunda sıfır genişlikli ileri bir onaylama işlemi kullanan bir normal ifade tanımlar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Normal ifade `\b\w+\b(?!\p{P})` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
|`\p{P})`|Sonraki karakter bir noktalama simgesi (nokta veya virgül gibi) değilse, eşleşme başarılı olur.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>
## <a name="zero-width-positive-lookbehind-assertions"></a>Sıfır Genişlik Pozitif Geriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır genişlikli pozitif geriye yönelik bir onaylama işlemi tanımlar:  
  
 `(?<=`alt *ifade*`)`  
  
 Burada alt *ifade* herhangi bir normal ifade deseninin olduğu yerdir. Bir eşleşmenin başarılı olması için, alt *ifade* geçerli konumun solundaki giriş dizesinde gerçekleşmelidir, ancak bu `subexpression` , eşleşme sonucuna dahil değildir. Sıfır genişlikli pozitif geriye yönelik onaylama işlemi geri izlememez.  
  
 Sıfır genişlikli pozitif geriye yönelik Onaylamalar genellikle normal ifadelerin başlangıcında kullanılır. Tanımladıkları model, eşleşme sonucunun bir parçası olmasa da bir eşleşmenin ön koşuludur.  
  
 Örneğin, aşağıdaki örnek, yirmi ilk yüzyıl için yılın son iki basamağıyla eşleşir (yani, "20" basamağının eşleşen dizeden önce gelmesini gerektirir).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Normal ifade deseninin `(?<=\b20)\d{2}\b` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`(?<=\b20)`|İki ondalık basamak bundan önce bir sözcük sınırında "20" ondalık haneleri içeriyorsa eşleştirmeye devam edin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Sıfır genişlikli pozitif geriye yönelik onaylar Ayrıca, yakalanan bir gruptaki son karakter veya karakterlerin, bu grubun normal ifade düzeniyle eşleşen karakterlerin bir alt kümesi olması gerektiğinde geri izlemeyi sınırlandırmak için de kullanılır. Örneğin, bir grup tüm ardışık kelime karakterlerini yakaladığında, son karakterin alfabetik olmasını gerektirmek için sıfır genişlikli pozitif geriye yönelik bir onaylama işlemi kullanabilirsiniz.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>
## <a name="zero-width-negative-lookbehind-assertions"></a>Sıfır Genişlik Negatif Geriye Yönelik Onaylar  
 Aşağıdaki gruplandırma yapısı sıfır Genişlik negatif geriye yönelik bir onaylama işlemi tanımlar:  
  
 `(?<!`alt *ifade*`)`  
  
 Burada alt *ifade* herhangi bir normal ifade deseninin olduğu yerdir. Bir eşleşmenin başarılı olması için alt *ifade* , geçerli konumun solundaki giriş dizesinde gerçekleşmemelidir. Ancak eşleşmeyen herhangi bir alt dize, `subexpression` eşleşme sonucuna dahil edilmez.  
  
 Sıfır Genişlik negatif geriye yönelik onaylar genellikle normal ifadelerin başlangıcında kullanılır. Tanımladıkları model, izleyen dizedeki bir eşleşmeyi daha fazla haline aşıyor. Ayrıca, yakalanan bir gruptaki son karakter veya karakterlerin, bu grubun normal ifade düzeniyle eşleşen bir veya daha fazla karakter olmaması gerektiğinde geri izlemeyi sınırlandırmak için de kullanılır. Örneğin, bir grup tüm ardışık kelime karakterlerini yakaladığında, son karakterin alt çizgi () olmaması için sıfır genişlikli pozitif geriye yönelik bir onaylama işlemi kullanabilirsiniz \_ .  
  
 Aşağıdaki örnek, hafta sonu olmayan (yani, Cumartesi veya Pazar olmayan) haftanın herhangi bir gününe ait tarihle eşleşir.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Normal ifade deseninin `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri ve ardından bir boşluk karakteri eşleştirin.|  
|`\d{1,2},`|Bir veya iki ondalık basamakla, sonra da boşluk karakteri ve virgül ile eşleştirin.|  
|`\d{4}\b`|Dört ondalık basamağı eşleştirin ve eşleşmeyi bir sözcük sınırında sonlandırın.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Eşleşmeden önce "Cumartesi" veya "Pazar" dizelerinden sonra bir boşluk gelmesi durumunda eşleşme başarılı olur.|  
  
<a name="atomic_groups"></a>
## <a name="atomic-groups"></a>Atomik gruplar  
 Aşağıdaki gruplandırma yapısı bir atomik grubu temsil eder (diğer bazı normal ifade altyapılarında geri alma olmayan alt ifade, atomik alt ifade veya yalnızca bir kez alt ifade olarak bilinir):
  
 `(?>`alt *ifade*`)`  
  
 Burada alt *ifade* herhangi bir normal ifade deseninin olduğu yerdir.  
  
 Genellikle, normal bir ifade isteğe bağlı veya alternatif eşleşen bir model içeriyorsa ve bir eşleşme başarılı olmazsa, normal ifade altyapısı, bir giriş dizesiyle bir Düzenle eşleştirmek için birden çok yönde Dalla çalışabilir. İlk dalı aldığında bir eşleşme bulunamazsa, normal ifade altyapısı ilk eşleşmeyi geçen noktaya yedekleyebilir veya geri izleyebilir ve ikinci dalı kullanarak eşleşmeyi dener. Bu işlem, tüm dallar denenene kadar devam edebilir.  
  
 Alt `(?>` *ifade* `)` dil yapısı geri izlemeyi devre dışı bırakır. Normal ifade altyapısı, giriş dizesindeki gibi çok sayıda karakterle eşleştirecektir. Başka bir eşleşme mümkün olmadığında, alternatif kalıp eşleşmelerini denemek için geri izlemecektir. (Yani, alt ifade yalnızca alt ifade tarafından eşleştirilecek dizeleriyle eşleşir; alt ifadeyi ve bunu izleyen tüm alt ifadeleri temel alan bir dizeyle eşleştirmeye çalışmaz.)  
  
 Geri izlemenin başarısız olacağını biliyorsanız bu seçenek önerilir. Normal ifade altyapısının gereksiz arama gerçekleştirmesini önlemek performansı geliştirir.  
  
 Aşağıdaki örnek, bir atomik grubun bir model eşleşme sonuçlarını nasıl değiştirdiği gösterilmektedir. Geri izleme normal ifadesi, bir dizi yinelenen karakterle başarıyla eşleşir, ancak bir sözcük sınırında aynı karakterin daha fazla tekrarı gelir, ancak geri dönüş olmayan normal ifade değildir.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Geri dönüş olmayan normal ifadesi `(?>(\w)\1+).\b` Aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`(\w)`|Tek bir sözcük karakteriyle eşleştirin ve ilk yakalama grubuna atayın.|  
|`\1+`|İlk yakalanan alt dizenin değerini bir veya daha fazla kez eşleştirin.|  
|`.`|Herhangi bir karakterle eşleştirin.|  
|`\b`|Eşleşmeyi bir sözcük sınırında sonlandır.|  
|`(?>(\w)\1+)`|Yinelenen bir sözcük karakterinin bir veya daha fazla tekrarı ile eşleşir, ancak bir sözcük sınırının son karakteriyle eşleşecek şekilde geri izlememeyin.|  
  
<a name="Objects"></a>
## <a name="grouping-constructs-and-regular-expression-objects"></a>Yapıları ve Normal İfade Nesnelerini Gruplandırma  
 Normal bir ifade yakalama grubuyla eşleşen alt dizeler <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> , <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> özelliği tarafından döndürülen nesneden alınabilecek nesneler tarafından temsil edilir <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> . <xref:System.Text.RegularExpressions.GroupCollection>Nesnesi aşağıdaki gibi doldurulur:  
  
- Koleksiyondaki ilk <xref:System.Text.RegularExpressions.Group> nesne (sıfır dizinindeki nesne) tüm eşleşmeyi temsil eder.  
  
- Sonraki <xref:System.Text.RegularExpressions.Group> nesne kümesi adlandırılmamış (numaralandırılmış) yakalama gruplarını temsil eder. Bunlar, soldan sağa doğru normal ifadede tanımlandıkları sırada görünürler. Bu grupların Dizin değerleri 1 ' den koleksiyondaki adlandırılmamış yakalama grupları sayısına göre değişir. (Belirli bir grubun dizini numaralandırılmış geribaşvuruya eşdeğerdir. Geri başvurular hakkında daha fazla bilgi için bkz. [Backreference yapıları](backreference-constructs-in-regular-expressions.md).)  
  
- Son nesne kümesi, <xref:System.Text.RegularExpressions.Group> adlandırılmış yakalama gruplarını temsil eder. Bunlar, soldan sağa doğru normal ifadede tanımlandıkları sırada görünürler. İlk adlandırılmış yakalama grubunun dizin değeri, son adlandırılmamış yakalama grubunun dizininden bir daha büyük. Normal ifadede adlandırılmamış bir yakalama grubu yoksa, ilk adlandırılmış yakalama grubunun dizin değeri bir olur.  
  
 Bir yakalama grubuna nicelik belirteci uygularsanız, karşılık gelen <xref:System.Text.RegularExpressions.Group> nesnenin <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> , <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> özellikleri bir yakalama grubu tarafından yakalanan son alt dizeyi yansıtır. <xref:System.Text.RegularExpressions.CaptureCollection>Özelliği tarafından döndürülen nesneden nicelik belirteçleri olan gruplar tarafından yakalanan tüm alt dizeler kümesini alabilirsiniz <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> .  
  
 Aşağıdaki örnek, ve nesneleri arasındaki ilişkiyi açıklar <xref:System.Text.RegularExpressions.Group> <xref:System.Text.RegularExpressions.Capture> .  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Normal ifade deseninin `(\b(\w+)\W+)+` tek tek kelimeleri bir dizeden ayıklar. Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Birlikte, bu karakterler bir kelime oluşturur. Bu ikinci yakalama grubudur.|  
|`\W+`|Bir veya daha fazla sözcük olmayan karakteri eşleştirin.|  
|`(\b(\w+)\W+)`|Bir veya daha fazla sözcük karakteri ve ardından bir veya daha fazla sözcük olmayan karakter örüntüsünün bir veya daha fazla kez eşleşmesini eşleştirin. Bu ilk yakalama grubudur.|  
  
 İkinci yakalama grubu, cümlenin her sözcüğüyle eşleşir. İlk yakalama grubu, sözcüğü izleyen noktalama ve boşluk ile birlikte her sözcükle eşleşir. <xref:System.Text.RegularExpressions.Group>Dizini 2 olan nesne ikinci yakalama grubuyla eşleşen metin hakkında bilgi sağlar. Yakalama grubu tarafından yakalanan tüm sözcüklerin kümesi <xref:System.Text.RegularExpressions.CaptureCollection> , özelliği tarafından döndürülen nesneden kullanılabilir <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](regular-expression-language-quick-reference.md)
- [Geri Dönüş](backtracking-in-regular-expressions.md)
