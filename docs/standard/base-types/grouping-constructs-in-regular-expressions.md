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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2aa7c35ebc06fb67d9cf6216233d2bed65ae76ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645905"
---
# <a name="grouping-constructs-in-regular-expressions"></a>Normal İfadelerdeki Gruplandırma Yapıları
Yapıları gruplandırma, normal ifade alt ifadeler tanımlamak ve bir Giriş dizesinin alt dizeler yakalayın. Yapıları gruplandırma, aşağıdakileri yapmak için kullanabilirsiniz:  
  
-   Giriş dizesinde yinelenen bir alt ifade eşleştirin.  
  
-   Bir miktar belirleyiciyi, birden çok normal ifade dil öğeleri olan bir alt ifade için geçerlidir. Miktar Belirleyicileri hakkında daha fazla bilgi için bkz: [miktar belirleyiciler](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
-   Bir alt ifade tarafından döndürülen dize dahil <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemleri.  
  
-   Tek tek alt ifadeler gelen almak <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği ve bunları ayrı ayrı işlemek bir bütün olarak eşleşen metin.  
  
 Aşağıdaki tablo, .NET normal ifade motoru tarafından desteklenen gruplandırma yapıları listeler ve bunların yakalama yakalamasız mı olduğunu gösterir.  
  
|Yapıyı gruplandırma|Yakalama veya yakalamayan|  
|------------------------|-------------------------------|  
|[Eşleşen alt ifadeler](#matched_subexpression)|Yakalama|  
|[Adlandırılmış eşleşen alt ifadeler](#named_matched_subexpression)|Yakalama|  
|[Grup tanımlarını Dengeleme](#balancing_group_definition)|Yakalama|  
|[Yakalama yapmayan gruplar](#noncapturing_group)|Yakalama yapmayan|  
|[Grup seçenekleri](#group_options)|Yakalama yapmayan|  
|[Sıfır Genişlik pozitif ileriye yönelik onaylar](#zerowidth_positive_lookahead_assertion)|Yakalama yapmayan|  
|[Sıfır Genişlik negatif ileriye yönelik onaylar](#zerowidth_negative_lookahead_assertion)|Yakalama yapmayan|  
|[Sıfır Genişlik pozitif geriye yönelik onaylar](#zerowidth_positive_lookbehind_assertion)|Yakalama yapmayan|  
|[Sıfır Genişlik negatif geriye yönelik onaylar](#zerowidth_negative_lookbehind_assertion)|Yakalama yapmayan|  
|[Geri dönüşlü olmayan alt ifadeler](#nonbacktracking_subexpression)|Yakalama yapmayan|  
  
 Gruplar ve normal ifade nesnesi modeli hakkında daha fazla bilgi için bkz: [yapıları ve normal ifade nesnelerini gruplandırma](#Objects).  
  
<a name="matched_subexpression"></a>   
## <a name="matched-subexpressions"></a>Eşleşen Alt İfadeler  
 Aşağıdaki gruplama yapısında bir eşleşen alt ifadeyi yakalar:  
  
 `(` *Alt ifade* `)`  
  
 Burada *subexpression* herhangi geçerli bir normal ifade deseni. Parantez kullanın otomatik olarak soldan sağa normal ifadede bir başlangıç sol parantezler bazında tabanlı numaralandırılır, yakalar. Numaralandırılmış sıfır yakalama tüm normal ifade deseni ile eşleşen bir metindir.  
  
> [!NOTE]
>  Varsayılan olarak, `(` *subexpression* `)` dil öğesi, eşleşen alt ifadeyi yakalar. Ancak <xref:System.Text.RegularExpressions.RegexOptions> içeren bir normal ifade deseni eşleştirme yöntemi parametresinin <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> bayrağı veya `n` seçeneği, bu alt ifade için uygulanır (bkz [gruplamak seçenekleri](#group_options) bu konunun devamındaki), eşleşen alt ifadeyi yakalanmaz.  
  
 Yakalanan gruplar dört farklı şekilde erişebilir:  
  
-   Yeniden başvuru kullanarak normal bir ifade içinde oluşturun. Eşleşen alt ifadeyi aynı normal ifadede sözdizimi kullanılarak başvurulur `\` *numarası*burada *numarası* yakalanan alt sıra sayısı.  
  
-   Adlandırılan yeniden başvuru kullanarak normal bir ifade içinde oluşturun. Eşleşen alt ifadeyi aynı normal ifadede sözdizimi kullanılarak başvurulur `\k<` *adı*`>`burada *adı* bir yakalama grubu adı veya `\k<` *numarası*`>`burada *numarası* bir yakalama grubunu sıra sayısı. Bir yakalama grubu, bir sıra numarası aynı olan bir varsayılan ada sahip. Daha fazla bilgi için [adlandırılmış eşleşen alt ifadeler](#named_matched_subexpression) bu konuda.  
  
-   Kullanarak `$` *numarası* değiştirme sırayla bir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi çağrısı, burada *numarası* yakalanan alt sıra sayısı.  
  
-   Kullanarak programlama yoluyla <xref:System.Text.RegularExpressions.GroupCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği. Üye koleksiyonda sıfır konumundaki tüm normal ifade eşleştirmesi temsil eder. Sonraki her üye bir eşleşen alt ifadeyi temsil eder. Daha fazla bilgi için [Grouping Constructs ve normal ifade nesneleri](#Objects) bölümü.  
  
 Yinelenen metindeki sözcükleri tanımlayan bir normal ifade aşağıdaki örnekte gösterilmektedir. Normal ifade deseninin iki yakalama grupları yinelenen sözcük iki örneğini temsil eder. İkinci örnek, başlangıç konumuna giriş dizesinde bildirmek için yakalanır.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Normal ifade deseni aşağıdaki gibidir:  
  
```  
(\w+)\s(\1)\W  
```  
  
 Aşağıdaki tabloda, normal ifade deseni nasıl yorumlanacağını gösterilmektedir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\1)`|Dizenin ilk yakalanan grubu eşleştirin. Bu ikinci yakalama grubudur. Böylece yinelenen sözcük başlangıç konumunu alınabilir örnek, bir yakalanan gruba atar `Match.Index` özelliği.|  
|`\W`|Boşluk ve noktalama işareti gibi bir sözcük olmayan karakterle eşleş. Bu, normal ifade deseni ilk yakalanan grubu Word'den ile başlayan bir sözcük eşleştirmeden engeller.|  
  
<a name="named_matched_subexpression"></a>   
## <a name="named-matched-subexpressions"></a>Adlandırılmış Eşleşen Alt İfadeler  
 Aşağıdaki gruplama yapısında bir eşleşen alt ifadeyi yakalar ve adına veya numarasına göre erişmenizi sağlar:  
  
```  
(?<name>subexpression)  
```  
  
 veya:  
  
```  
(?'name'subexpression)  
```  
  
 Burada *adı* bir geçerli grup adı ve *subexpression* herhangi geçerli bir normal ifade deseni. *adı* bir sayı ile başlayamaz ve herhangi bir noktalama karakteri içermemelidir.  
  
> [!NOTE]
>  Varsa <xref:System.Text.RegularExpressions.RegexOptions> içeren bir normal ifade deseni eşleştirme yöntemi parametresinin <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> bayrağı, veya `n` seçeneği, bu alt ifade için uygulanır (bkz [gruplamak seçenekleri](#group_options) bu konunun devamındaki), yalnızca bir alt ifade yakalama açıkça adı yakalama grupları yoludur.  
  
 Adlandırılmış yakalanan gruplar aşağıdaki yöntemlerle erişebilirsiniz:  
  
-   Adlandırılan yeniden başvuru kullanarak normal bir ifade içinde oluşturun. Eşleşen alt ifadeyi aynı normal ifadede sözdizimi kullanılarak başvurulur `\k<` *adı*`>`burada *adı* yakalanan alt adıdır.  
  
-   Yeniden başvuru kullanarak normal bir ifade içinde oluşturun. Eşleşen alt ifadeyi aynı normal ifadede sözdizimi kullanılarak başvurulur `\` *numarası*burada *numarası* yakalanan alt sıra sayısı. Adlandırılmış eşleşen alt ifadeler sırayla soldan sağa eşleşen alt ifadeler sonra numaralandırılır.  
  
-   Kullanarak `${` *adı* `}` değiştirme sırayla bir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi çağrısı, burada *adı* yakalanan alt adıdır.  
  
-   Kullanarak `$` *numarası* değiştirme sırayla bir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi çağrısı, burada *numarası* yakalanan alt sıra sayısı.  
  
-   Kullanarak programlama yoluyla <xref:System.Text.RegularExpressions.GroupCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği. Üye koleksiyonda sıfır konumundaki tüm normal ifade eşleştirmesi temsil eder. Sonraki her üye bir eşleşen alt ifadeyi temsil eder. Adlandırılmış yakalanan gruplar numaralı yakalanan gruplar sonra koleksiyondaki depolanır.  
  
-   Alt ifade adına sağlayarak programlı olarak <xref:System.Text.RegularExpressions.GroupCollection> nesnenin dizin oluşturucu (C#) veya kendi <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> özelliği (Visual Basic'te).  
  
 Basit bir normal ifade deseni gösterilmektedir nasıl (adlandırılmamış) numaralı ve adlandırılmış gruplara programlama yoluyla veya normal ifade dili söz dizimi kullanılarak başvurulabilir. Normal ifade `((?<One>abc)\d+)?(?<Two>xyz)(.*)` aşağıdaki yakalama grupları ve ada göre sayı üretir. İlk ifade eder ve tüm desen için her zaman yakalama grubu (sayı 0).  
  
|Sayı|Ad|Desen|  
|------------|----------|-------------|  
|0|0 (varsayılan adı)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1.|1 (varsayılan adı)|`((?<One>abc)\d+)`|  
|2|2 (varsayılan adı)|`(.*)`|  
|3|Bir|`(?<One>abc)`|  
|4|İki|`(?<Two>xyz)`|  
  
 Yinelenen sözcükler ve hemen her yinelenen sözcük izleyen word tanımlayan bir normal ifade aşağıdaki örnekte gösterilmektedir. İki adlandırılmış alt ifadeler normal ifade desenini tanımlar: `duplicateWord`, yinelenen sözcük; temsil eder ve `nextWord`, yinelenen sözcük izleyen sözcüğü temsil eder.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Normal ifade deseni aşağıdaki gibidir:  
  
```  
(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)  
```  
  
 Aşağıdaki tabloda, normal ifade nasıl yorumlanacağını gösterilmektedir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubu adı `duplicateWord`.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`\k<duplicateWord>`|Adlı yakalanan grubu dizeden eşleşen `duplicateWord`.|  
|`\W`|Boşluk ve noktalama işareti gibi bir sözcük olmayan karakterle eşleş. Bu, normal ifade deseni ilk yakalanan grubu Word'den ile başlayan bir sözcük eşleştirmeden engeller.|  
|`(?<nextWord>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubu adı `nextWord`.|  
  
 Bir grup adı bir normal ifadede yinelenebilir unutmayın. Örneğin, birden fazla grubu adı için olası `digit`, aşağıdaki örnekte gösterildiği gibi. Yinelenen adları, değeri söz konusu olduğunda <xref:System.Text.RegularExpressions.Group> nesnesi, giriş dizesindeki son başarılı yakalama göre belirlenir. Ayrıca, <xref:System.Text.RegularExpressions.CaptureCollection> yalnızca, grup adını değil yinelenen olduğu gibi her yakalama hakkında bilgilerle doldurulur.  
  
 Aşağıdaki örnekte, normal ifade `\D+(?<digit>\d+)\D+(?<digit>\d+)?` adlı bir grubu iki örneğini içeren `digit`. İlk `digit` Grup yakalamalarını adlı bir veya daha fazla basamak karakterleri. İkinci `digit` adlandırılmış grup, bir veya daha fazla basamak karakterleri sıfır veya bir oluşumunu yakalar. İkinci yakalama grubu başarıyla değiştirilirse örnekte gösterildiği çıkışı metinle eşleşen gibi bu metin değerini değeri tanımlar <xref:System.Text.RegularExpressions.Group> nesne. İkinci yakalama grubu yapamazsa, değerin son başarılı eşleşmenin Giriş dizesinin değerini tanımlar eşleşmiyor <xref:System.Text.RegularExpressions.Group> nesne.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 Aşağıdaki tabloda, normal ifade nasıl yorumlanacağını gösterilmektedir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\D+`|Bir veya daha fazla ondalık olmayan basamak işaretleriyle eşleş.|  
|`(?<digit>\d+)`|Bir veya daha fazla ondalık basamak işaretleriyle eşleş. Eşleşen atama `digit` grubunun adı.|  
|`\D+`|Bir veya daha fazla ondalık olmayan basamak işaretleriyle eşleş.|  
|`(?<digit>\d+)?`|Bir veya daha fazla ondalık basamak karakterleri sıfır veya bir oluşumunu eşleştirin. Eşleşen atama `digit` grubunun adı.|  
  
<a name="balancing_group_definition"></a>   
## <a name="balancing-group-definitions"></a>Grup Tanımlarını Dengeleme  
 Bir dengeleme grubu tanımını önceden tanımlanmış bir grup ve geçerli grubu, daha önce tanımlanmış Grup geçerli grubu arasındaki aralık depoları tanımını siler. Bu gruplandırma yapı aşağıdaki biçime sahiptir:  
  
```  
(?<name1-name2>subexpression)  
```  
  
 veya:  
  
```  
(?'name1-name2' subexpression)  
```  
  
 Burada *name1* (isteğe bağlı), geçerli grubu, *name2* önceden tanımlanmış bir grup ve *subexpression* herhangi geçerli bir normal ifade deseni. Bir dengeleme grubu tanımını tanımını siler *name2* aralığını depolar *name2* ve *name1* içinde *name1*. Hayır ise *name2* grubu tanımlanır, eşleşme provided. Son tanımını silme çünkü *name2* önceki tanımını ortaya çıkarır *name2*, bu yapı için Grup yakalamaları yığınını kullanmanıza olanak tanıyan *name2* gibi bir parantezler gibi iç içe geçmiş yapılar izlemek veya açma ve kapatma köşeli ayraçlar sayacı.  
  
 Bir dengeleme grubu tanımını kullanan *name2* yığını olarak. Her iç içe geçmiş yapısı başlangıç karakteri grubunda ve yerleştirilir, <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> koleksiyonu. Kendi karakter açma karşılık gelen kapanış karakter eşleştiğinde grubundan kaldırılır ve <xref:System.Text.RegularExpressions.Group.Captures%2A> koleksiyonu bir azaltılır. Açılış ve kapanış karakterlerini tüm iç içe yapılar, eşleşen sonra *name1* boştur.  
  
> [!NOTE]
>  Sonra normal ifadeye uygun açma kullanmak için aşağıdaki örneği değiştirin ve bir iç içe geçmiş yapısı karakterinin kapatmadan önce matematik deyimlerde ya da içeren satırları program kod gibi en iç içe geçmiş yapılar işlemek için kullanabilirsiniz birden çok iç içe geçmiş yöntemi çağırır.  
  
 Aşağıdaki örnek bir dengeleme grubu tanımını sol ve sağ açılı ayraç (<>) bir giriş dizesinde eşleştirilecek kullanır. İki adlandırılmış gruplar, örneğin tanımlar `Open` ve `Close`, bir yığın gibi köşeli ayraç eşleştirme çiftlerini izlemek için kullanılan. Her yakalanan Sol açılı ayraç yakalama koleksiyonunu gönderildiğinde `Open` grup ve her yakalanan sağ açılı ayraç yakalama koleksiyonunu gönderilen `Close` grubu. Bir dengeleme grubu tanımını her sol açılı ayraç için'eşleşen bir sağ açılı ayraç olmasını sağlar. Yok, ise son desenin `(?(Open)(?!))`, yalnızca değerlendirilir `Open` grubu boş değil (ve bu nedenle, tüm iç içe geçmiş yapılar tamamlamadıysanız kapalı). Son desenin değerlendirildiği taktirde eşleşme olduğundan başarısız `(?!)` desenin olduğundan her zaman başarısız olan bir sıfır Genişlik negatif ileriye yönelik onaylar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Normal ifade deseni şöyledir:  
  
```  
^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$  
```  
  
 Normal ifade şu şekilde yorumlanır:  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Dize başlangıcında başlar.|  
|`[^<>]*`|Sol veya sağ açılı ayraçlar olmayan sıfır veya daha fazla karakterini eşleştirin.|  
|`(?'Open'<)`|Adlı bir gruba atayın ve Sol açılı ayraç eşleşen `Open`.|  
|`[^<>]*`|Sol veya sağ açılı ayraçlar olmayan sıfır veya daha fazla karakterini eşleştirin.|  
|`((?'Open'<)[^<>]*) +`|Sol veya sağ açılı ayraçlar olmayan sıfır veya daha fazla karakterlerinin izlediği bir sol açılı ayraç bir veya daha fazla oluşumunu eşleyin. Bu ikinci yakalama grubudur.|  
|`(?'Close-Open'>)`|Sağ açılı ayraç eşleşmiyor, alt dizenin arasında atama `Open` grubu ile geçerli grup için `Close` grup ve tanımını silme `Open` grubu.|  
|`[^<>]*`|Sol ya da bir sağ açılı ayraç değil herhangi bir karakter sıfır veya daha fazla oluşumunu eşleyin.|  
|`((?'Close-Open'>)[^<>]*)+`|Sağ açılı ayraç bir veya daha çok tekrarı ile eşleştir, herhangi bir karakterin sıfır veya daha çok tekrarı tarafından izlenen bir sol ne bir sağ açılı ayraç olmasıdır. Dik Açılı köşeli ayraç eşleştirme, alt dizenin arasında atama `Open` grubu ile geçerli grup için `Close` grup ve tanımını silme `Open` grubu. Bu, üçüncü yakalama grubudur.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Şu desene sıfır veya daha çok tekrarı ile eşleştir: bir veya daha çok tekrarı bir sağ açılı ayraç bir veya daha çok tekrarı ile ardından sıfır veya daha fazla açılı ayraç karakteri arkasından bir sol açılı ayraç, ardından sıfır veya daha çok tekrarı ile olmayan-açılı ayraçlar. Dik Açılı köşeli ayraç eşleştirme, tanımını silmek `Open` grup ve alt dizeyi arasında atama `Open` grubu ile geçerli grup için `Close` grubu. Bu ilk yakalama grubudur.|  
|`(?(Open)(?!))`|Varsa `Open` grubu varsa, boş bir dize eşlenebilen kullanılabilir, ancak normal ifade motoru dize içindeki konumu ilerlemeyin eşleşme bırak. Bir sıfır Genişlik negatif ileriye yönelik onaydır budur. Boş bir dize her zaman örtük olarak bir giriş dizesinde olduğu için bu eşleşme her zaman başarısız olur. Bu eşleşme başarısız, açılı ayraçlar değil dengelendiğinden gösterir.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 Son alt ifade `(?(Open)(?!))`, içinde iç içe yapıları olmadığını giriş dizesi düzgün Dengeli (örneğin, her sol açılı ayraç bir sağ açılı ayraç tarafından eşleştirilen olup olmadığını) gösterir. Yakalanan geçerli bir gruba göre koşullu eşleştirme kullanır; Daha fazla bilgi için [değişim yapıları](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md). Varsa `Open` grubu tanımlanır, normal ifade altyapısı, alt ifade eşleştirmeyi dener `(?!)` giriş dizesinde. `Open` Yalnızca iç içe geçmiş yapılar dengesiz, Grup tanımlanmalıdır. Bu nedenle, giriş dizesinde eşleştirilecek desen her zaman eşleşme başarısız olmasına neden olan bir olmalıdır. Bu durumda, `(?!)` boş bir dize her zaman giriş dizesindeki sonraki konuma örtük olarak mevcut bir sıfır Genişlik negatif ileriye yönelik onaydır her zaman başarısız olduğundan.  
  
 Örnekte, Giriş dizesinin normal ifade altyapısı değerlendirir "\<abc >< mno\<xyz >>" aşağıdaki tabloda gösterildiği gibi.  
  
|Adım|Desen|Sonuç|  
|----------|-------------|------------|  
|1.|`^`|Giriş dizesinin başında eşleşmeye başlatır|  
|2|`[^<>]*`|Açılı ayraç karakterleri Sol açılı ayraç önce arar; herhangi bir eşleşme bulur.|  
|3|`(((?'Open'<)`|Sol açılı ayraç içinde eşleşen "\<abc >" ve buna atayan `Open` grubu.|  
|4|`[^<>]*`|"Abc" ile eşleşir.|  
|5|`)+`|"< abc" ikinci yakalanan grubun değeri.<br /><br /> Normal ifade altyapısı geri döngü değil giriş dizesindeki sonraki karakteri bir sol açılı ayraç değil, bu nedenle `(?'Open'<)[^<>]*)` desenin.|  
|6|`((?'Close-Open'>)`|Dik Açılı köşeli ayraç içinde eşleşen "\<abc >", alt dizedir "abc" atar arasında `Open` grubu ve dik açılı ayraç, çok `Close` grup ve geçerli değerini siler ("<"), `Open` grubu boş bırakın.|  
|7|`[^<>]*`|Sağ açılı ayraç sonra açılı ayraç karakterleri arar; herhangi bir eşleşme bulur.|  
|8|`)+`|Üçüncü yakalanan grubun değeri ">".<br /><br /> Normal ifade altyapısı geri döngü değil giriş dizesindeki sonraki karakteri bir sağ açılı ayraç değil, bu nedenle `((?'Close-Open'>)[^<>]*)` desenin.|  
|9|`)*`|İlk yakalanan grubun değeri "\<abc >".<br /><br /> Normal ifade altyapısı geri döngüsü giriş dizesindeki sonraki karakteri bir sol açılı ayraç olduğundan `(((?'Open'<)` desenin.|  
|10|`(((?'Open'<)`|Sol açılı ayraç içinde eşleşen "\<mno >" ve buna atayan `Open` grubu. Kendi <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> koleksiyonu artık tek bir değer olan "<".|  
|11|`[^<>]*`|"Mno" eşleşir.|  
|12|`)+`|"< mno" ikinci yakalanan grubun değeri.<br /><br /> Normal ifade altyapısı geri döngü Sol açılı ayraç, giriş dizesindeki sonraki karakterle olduğundan `(?'Open'<)[^<>]*)` desenin.|  
|13|`(((?'Open'<)`|Sol açılı ayraç içinde eşleşen "\<xyz >" ve buna atayan `Open` grubu. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Koleksiyonunu `Open` grubu artık iki yakalamaları içerir: gelen Sol açılı ayraç "\<mno >" ve Sol açılı ayraç gelen "\<xyz >".|  
|14|`[^<>]*`|"Xyz" eşleşir.|  
|15|`)+`|"< xyz" ikinci yakalanan grubun değeri.<br /><br /> Normal ifade altyapısı geri döngü değil giriş dizesindeki sonraki karakteri bir sol açılı ayraç değil, bu nedenle `(?'Open'<)[^<>]*)` desenin.|  
|16|`((?'Close-Open'>)`|Dik Açılı köşeli ayraç içinde eşleşen "\<xyz >". "xyz" alt dizesini arasında atar `Open` grubu ve dik açılı ayraç için `Close` grup ve geçerli değerini siler `Open` grubu. Önceki yakalama değerini (sol açılı ayraç içinde "\<mno >") geçerli değeri `Open` grubu. <xref:System.Text.RegularExpressions.Group.Captures%2A> Koleksiyonunu `Open` grup artık içeren tek bir yakalama, gelen Sol açılı ayraç "\<xyz >".|  
|17|`[^<>]*`|Açılı ayraç karakterleri arar; herhangi bir eşleşme bulur.|  
|18|`)+`|Üçüncü yakalanan grubun değeri ">".<br /><br /> Normal ifade altyapısı geri döngüsü giriş dizesindeki sonraki karakteri bir sağ açılı ayraç olduğundan `((?'Close-Open'>)[^<>]*)` desenin.|  
|19|`((?'Close-Open'>)`|Son sağ açılı ayraç içinde eşleşen "xyz >>", atar "mno\<xyz >" (alt dizeyi arasında `Open` grubu ve sağ açılı ayraç) için `Close` grup ve geçerli değerini siler `Open` grubu. `Open` Grup boşsa şimdi.|  
|20|`[^<>]*`|Açılı ayraç karakterleri arar; herhangi bir eşleşme bulur.|  
|21|`)+`|Üçüncü yakalanan grubun değeri ">".<br /><br /> Normal ifade altyapısı geri döngü değil giriş dizesindeki sonraki karakteri bir sağ açılı ayraç değil, bu nedenle `((?'Close-Open'>)[^<>]*)` desenin.|  
|22|`)*`|İlk yakalanan grubun değeri "< mno\<xyz >>".<br /><br /> Normal ifade altyapısı geri döngü değil giriş dizesindeki sonraki karakteri bir sol açılı ayraç değil, bu nedenle `(((?'Open'<)` desenin.|  
|23|`(?(Open)(?!))`|`Open` Grubu tanımlı değil, eşleşme denenmesi için.|  
|24|`$`|Giriş dizesinin sonuyla eşleşir.|  
  
<a name="noncapturing_group"></a>   
## <a name="noncapturing-groups"></a>Yakalama Yapmayan Gruplar  
 Aşağıdaki gruplama yapısında bir alt ifade tarafından eşleştirilen alt dizeyi yakalamaz:  
  
```  
(?:subexpression)  
```  
  
 Burada *subexpression* herhangi geçerli bir normal ifade deseni. Yakalama yapmayan grubu yapısı, genellikle bir miktar belirleyici bir gruba uygulanır, ancak grubu tarafından yakalanan alt dizeler ilgili değildir kullanılır.  
  
> [!NOTE]
>  Normal bir ifade, iç içe gruplama yapıları içeriyorsa, bir dış yakalamayan Grup yapısı iç iç içe geçmiş Grup yapıları için geçerli değildir.  
  
 Yakalama yapmayan gruplar içeren bir normal ifade aşağıdaki örnekte gösterilmektedir. Çıkış herhangi bir yakalanan gruba içerip içermediğini unutmayın.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Normal ifade `(?:\b(?:\w+)\W*)+\.` bir nokta sonlandırılmış bir cümle ile eşleşir. Normal ifade cümleler üzerinde değil kelimeler odaklanır çünkü gruplama yapıları yalnızca miktar belirleyiciler kullanılır. Normal ifade deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?:\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Eşleşen metnin bir yakalanan gruba atamayın.|  
|`\W*`|Sıfır veya daha fazla sözcük olmayan karakterle eşleş.|  
|`(?:\b(?:\w+)\W*)+`|Bir sözcük sınırında ardından sıfır veya daha fazla sözcük olmayan karakterle başlayan bir veya daha fazla sözcük karakteri desenini, bir veya daha fazla kez eşleştirin. Eşleşen metnin bir yakalanan gruba atamayın.|  
|`\.`|Bir noktayı eşleştirin.|  
  
<a name="group_options"></a>   
## <a name="group-options"></a>Grup Seçenekleri  
 Aşağıdaki bir gruplama kurgusu uygular veya bir alt ifade dahilinde belirlenen seçenekleri devre dışı bırakır:  
  
 `(?imnsx-imnsx:` *Alt ifade* `)`  
  
 Burada *subexpression* herhangi geçerli bir normal ifade deseni. Örneğin, `(?i-s:)` büyük/küçük harfe üzerinde açar ve tek satır modunu devre dışı bırakır. Belirtebileceğiniz satır içi seçenekler hakkında daha fazla bilgi için bkz. [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
>  Kullanarak bir alt ifade yerine normal bir ifadenin geçerli seçenekleri belirtebilirsiniz bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıfı oluşturucusunun veya statik bir yöntem. Normal bir ifade içinde belirli bir noktaya sonra kullanarak geçerli satır içi seçenekleri belirtebilirsiniz `(?imnsx-imnsx)` dil yapısı.  
  
 Grup seçenekleri yapısı bir yakalama grubu değil. Diğer bir deyişle, ancak tarafından yakalanan bir dizenin herhangi bir kısmını *subexpression* dahildir değiştirme dizininde eşleşmenin, onu değil bir yakalanan gruba dahil ve doldurmak için kullanılan <xref:System.Text.RegularExpressions.GroupCollection> nesne.  
  
 Örneğin, normal ifade `\b(?ix: d \w+)\s` büyük küçük harf duyarsız eşleşmeyi etkinleştirmek ve "d" harfi ile başlayan tüm sözcükleri tanımlamak, desen beyaz boşluğu yok saymak için Gruplandırma yapısında aşağıdaki örnekte satıriçi seçeneklerini kullanır. Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?ix: d \w+)`|Büyük küçük harf duyarsız eşleştirme ve boşluk Bu düzendeki yoksayılıyor kullanarak, bir veya daha fazla sözcük karakteri ve ardından bir "d" eşleştirin.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>   
## <a name="zero-width-positive-lookahead-assertions"></a>Sıfır Genişlik Pozitif İleriye Yönelik Onaylar  
 Aşağıdaki gruplama yapısında bir sıfır genişlik pozitif ileriye yönelik onaydır tanımlar:  
  
 `(?=` *Alt ifade* `)`  
  
 Burada *subexpression* tüm normal ifade deseni. Eşleşmenin başarılı olması için Giriş dizesinin normal ifade deseninde eşleşmelidir *subexpression*, ancak eşleşen alt dizenin eşleşme sonuca dahil değildir. Bir sıfır genişlik pozitif ileriye yönelik onaydır geri izleme yapmaz.  
  
 Genellikle bir sıfır genişlik pozitif ileriye yönelik onaydır bir normal ifade deseni sonunda bulunur. Bu, eşleşmenin gerçekleşmesi bir dizenin sonunda bulunması gereken ancak, değiştirme dizininde eşleşmenin dahil edilmemesi gereken bir alt dizeyi tanımlar. Aşırı geri izleme önlemek için yararlıdır. Belirli bir yakalanan gruba bir alt kümesini yakalanan o grup için tanımlanan örnekle eşleşen metin ile başladığından emin olmak için bir sıfır genişlik pozitif ileriye yönelik onaydır kullanabilirsiniz. Örneğin, bir yakalama grubu art arda sözcük karakterlerinden eşleşirse, ilk karakteri alfabetik bir büyük harf karakter olmasını gerekli kılmak için bir sıfır genişlik pozitif ileriye yönelik onaydır kullanabilirsiniz.  
  
 Aşağıdaki örnek, giriş dizesinde bir sıfır genişlik pozitif ileriye yönelik onaydır fiili önündeki word eşleşecek şekilde "is" kullanır.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Normal ifade `\b\w+(?=\sis\b)` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`(?=\sis\b)`|Sözcük karakterlerinden sonrasında bir boşluk karakteri ve dizeyi "is", bir sözcük sınırında biteceği olup olmadığını belirler. Bu durumda, eşleşme başarılı olur.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>   
## <a name="zero-width-negative-lookahead-assertions"></a>Sıfır Genişlik Negatif İleriye Yönelik Onaylar  
 Aşağıdaki gruplama yapısında bir sıfır Genişlik negatif ileriye yönelik onaydır tanımlar:  
  
 `(?!` *Alt ifade* `)`  
  
 Burada *subexpression* tüm normal ifade deseni. Eşleşmenin başarılı olması Giriş dizesinin normal ifade deseninde eşleşmemelidir *subexpression*, eşleştirilen dizeyi eşleşme sonucu yer almamakla birlikte.  
  
 Bir sıfır Genişlik negatif ileriye yönelik onaydır genellikle başında veya sonunda, normal ifade kullanılır. Normal bir ifadenin başında, normal ifadenin başına eşleştirilecek benzer, ancak daha genel bir desen tanımladığında eşleştirilmesi gerektiğini değil belirli bir desenle tanımlayabilirsiniz. Bu durumda, geri izlemenin sınırlamak için genellikle kullanılır. Normal bir ifadenin sonunda, bunu bir eşleşme sonunda oluşamaz bir alt ifade tanımlayabilirsiniz.  
  
 Aşağıdaki örnek, "Çalıştır" ile başlamayan sözcükleri eşleştirmeye normal ifadenin başında sıfır genişlikli ileri yönlü onaylama işlemi kullanan bir normal ifade tanımlar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Normal ifade `\b(?!un)\w+\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?!un)`|Sonraki iki karakter "Çalıştır" olup olmadığını belirler. Bir eşleşme yoksa, mümkündür.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Aşağıdaki örnek, bir noktalama karakteri ile bitmemelidir sözcükleri eşleştirmeye normal ifadenin sonunda bir sıfır genişlikli ileriye yönelik onaydır kullanan bir normal ifade tanımlar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Normal ifade `\b\w+\b(?!\p{P})` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
|`\p{P})`|Sonraki karakterin bir noktalama işareti sembolü (örneğin, bir nokta veya virgül) değil ise, eşleşme başarılı olur.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>   
## <a name="zero-width-positive-lookbehind-assertions"></a>Sıfır Genişlik Pozitif Geriye Yönelik Onaylar  
 Aşağıdaki gruplama yapısında bir sıfır genişlik pozitif geriye yönelik onayı tanımlar:  
  
 `(?<=` *Alt ifade* `)`  
  
 Burada *subexpression* tüm normal ifade deseni. Eşleşmenin başarılı olması *subexpression* giriş dizesini geçerli konumlarından sola olmalıdır, ancak `subexpression` eşleşme sonuca dahil değildir. Bir sıfır genişlik pozitif geriye yönelik onaydır geri izleme yapmaz.  
  
 Sıfır Genişlik pozitif geriye yönelik onaylar, genellikle normal ifadeler başında kullanılır. Eşleşme sonucu bir parçası olmasa da bunlar tanımlayan bir eşleşme için önkoşul modelidir.  
  
 Örneğin, aşağıdaki örnek yirmi birinci yüzyıl yılın son iki basamak eşleşir (diğer bir deyişle, "20" basamak eşleşen dizeyi önünde gerektirir).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Normal ifade deseni `(?<=\b20)\d{2}\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`(?<=\b20)`|İki ondalık basamak bir sözcük sınırında "20" ondalık basamak tarafından öncelenen ise eşleştirmeyi devam ettirin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Sıfır Genişlik pozitif geriye yönelik onaylar, aynı zamanda son karakterle veya karakterlerle yakalanan grubu o grubun normal ifade deseniyle eşleşen karakterleri bir alt kümesi olmalıdır, geri izlemenin sınırlamak için kullanılır. Örneğin, tüm ardışık sözcük karakterlerini bir gruba yakalar, son karakter alfabetik olmasını gerekli kılmak için bir sıfır genişlik pozitif geriye yönelik onaydır kullanabilirsiniz.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>   
## <a name="zero-width-negative-lookbehind-assertions"></a>Sıfır Genişlik Negatif Geriye Yönelik Onaylar  
 Aşağıdaki gruplama yapısında bir sıfır Genişlik negatif geriye yönelik onayı tanımlar:  
  
 `(?<!` *Alt ifade* `)`  
  
 Burada *subexpression* tüm normal ifade deseni. Eşleşmenin başarılı olması *subexpression* giriş dizesini geçerli konumlarından sola gerçekleşmemelidir. Ancak, tüm eşleşmeyen alt dize `subexpression` eşleşme sonuca dahil değildir.  
  
 Sıfır Genişlik negatif geriye yönelik onaylar, genellikle normal ifadeler başında kullanılır. Tanımlarlar deseni izleyen dizesini eşleşmeyi ışığının. Bunlar ayrıca son karakterle veya karakterlerle yakalanan grubu bir veya daha fazla grubun normal ifade deseniyle eşleşen karakter olmamalıdır, geri izlemenin sınırlamak için kullanılır. Örneğin, tüm ardışık sözcük karakterlerini bir gruba yakalar, son karakter bir alt çizgi (_) olmaması gerektirecek şekilde bir sıfır genişlik pozitif geriye yönelik onaydır kullanabilirsiniz.  
  
 Aşağıdaki örnek tarihi hafta değil haftanın her günü için eşleşir (diğer bir deyişle, Cumartesi ne Pazar değil).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Normal ifade deseni `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Sonrasında bir beyaz alan karakteri bir veya daha fazla sözcük karakterini eşleştirin.|  
|`\d{1,2},`|Bir boşluk karakteri ve virgül tarafından izlenen bir veya iki ondalık basamağı eşleştirin.|  
|`\d{4}\b`|Dört ondalık basamağı eşleştirin ve eşlemeyi bir sözcük sınırında bitmelidir.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Eşleşme "Saturday" veya "Sunday" ardından bir boşluk dizeler dışında bir şey tarafından öncesinde, eşleşme başarılı olur.|  
  
<a name="nonbacktracking_subexpression"></a>   
## <a name="nonbacktracking-subexpressions"></a>Geri Dönüşlü Olmayan Alt İfadeler  
 Aşağıdaki bir gruplama kurgusu geri dönüşlü olmayan alt ifade ("greedy" alt olarak da bilinir) temsil eder:  
  
 `(?>` *Alt ifade* `)`  
  
 Burada *subexpression* tüm normal ifade deseni.  
  
 Normalde, normal bir ifade isteğe bağlı içerir ya da alternatif eşleşen deseni ve bir eşleşme başarılı olmaz, normal ifade altyapısının bir Giriş dizesinin desenle eşleşecek şekilde birden çok yönlü dallara ayırabilirsiniz. İlk dalı çektiğinde bir eşleşme bulunmazsa, normal ifade altyapısı yedekleyebilir veya ilk eşleşme burada sürdüğünü noktasına geri izleme ve ikinci dalı kullanılarak eşleşme çalışır. Bu işlem, tüm dalları deneninceye kadar devam eder.  
  
 `(?>` *Subexpression* `)` dil oluşturmak geri izlemeyi devre dışı bırakır. Normal ifade altyapısı giriş dizesinde mümkün olduğunca kadar çok karakterle eşleşir. Daha fazla eşleşme mümkün olduğunda, bunu alternatif desen denemek için geri izleme değil. (Diğer bir deyişle, yalnızca alt ifade ile eşleşen dizeler alt ifade ile eşleşir; subexpression ve onu izleyen tüm alt ifadeler temelinde bir dizeyle eşleştirme yapmayı denemez.)  
  
 Geri izlemenin değil başarılı olur biliyorsanız, bu seçenek önerilir. Normal ifade altyapısı, gereksiz arama gerçekleştirmesini engelleyen performansını artırır.  
  
 Aşağıdaki örnek, bir geri dönüşlü olmayan alt ifade deseni eşleştirmesini sonuçlarını nasıl değiştirdiğini gösterir. Geri izlemenin normal ifade başarılı bir şekilde bir daha fazla oluşumunu aynı karakter tarafından bir sözcük sınırında yinelenen karakterlik bir dizi eşleşir ancak geri dönüşlü olmayan normal ifade yok.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Geri dönüşlü olmayan normal ifade `(?>(\w)\1+).\b` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(\w)`|Bir tek bir sözcük karakteri Eşleştir ve ilk yakalama gruba atayın.|  
|`\1+`|İlk yakalanan alt dizeyi değeri, bir veya daha fazla kez eşleştirin.|  
|`.`|Herhangi bir karakterle eşleş.|  
|`\b`|Eşleşme bir sözcük sınırında sonlandır.|  
|`(?>(\w)\1+)`|Yinelenen sözcük karakteri bir veya daha çok tekrarı ile eşleştir, ancak son karakter bir sözcük sınırında eşleştirmek için dönüş gerçekleştirmeyin.|  
  
<a name="Objects"></a>   
## <a name="grouping-constructs-and-regular-expression-objects"></a>Yapıları ve Normal İfade Nesnelerini Gruplandırma  
 Yakalama grubu normal bir ifadeyle eşleşen alt dizeler tarafından temsil edilir <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> alınabilir nesneleri <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği. <xref:System.Text.RegularExpressions.GroupCollection> Nesnesini şu şekilde doldurulur:  
  
-   İlk <xref:System.Text.RegularExpressions.Group> (dizin nesnesi) koleksiyon nesnesinde tüm eşleşmeyi temsil eder.  
  
-   Sonraki kümesi <xref:System.Text.RegularExpressions.Group> nesneleri adlandırılmamış (numaralandırılmış) yakalama grupları temsil eder. Normal ifadede, soldan sağa doğru tanımlandıkları sırayla görünürler. 1 ile adlandırılmamış sayısı bu grupları arasında dizin değerlerini yakalama grupları koleksiyondaki. (Belirli bir grubun dizini için numaralandırılmış alt ifadeye yeniden başvur eşdeğerdir. Yeniden başvurular hakkında daha fazla bilgi için bkz. [yeniden başvuru yapıları](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)  
  
-   En son kümesi <xref:System.Text.RegularExpressions.Group> nesneler adlandırılmış yakalama grupları temsil eder. Normal ifadede, soldan sağa doğru tanımlandıkları sırayla görünürler. Adlandırılmış yakalama grubu ilk dizin değerini yakalama son adlandırılmamış grubun dizininin bir biridir. Varsa yakalama grupları normal ifadede adlandırılmamış adlı yakalama grubu ilk dizin değerini biridir.  
  
 Karşılık gelen bir yakalama grubu için bir miktar belirleyiciyi uygularsanız <xref:System.Text.RegularExpressions.Group> nesnenin <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>, <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType>, ve <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> özellikleri bir yakalama grubu tarafından yakalanan son alt dizeyi yansıtır. Eksiksiz bir miktar belirleyiciler gelen olan grupları tarafından yakalanan alt dizeler alabilirsiniz <xref:System.Text.RegularExpressions.CaptureCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği.  
  
 Aşağıdaki örnekte arasındaki ilişkiyi açıklar <xref:System.Text.RegularExpressions.Group> ve <xref:System.Text.RegularExpressions.Capture> nesneleri.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Normal ifade deseni `\b(\w+)\W+)+` kelimeler bir dizeden ayıklar. Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Birlikte, bu karakterler bir sözcük formu. Bu ikinci yakalama grubudur.|  
|`\W+`|Bir veya daha fazla sözcük olmayan karakterle eşleş.|  
|`(\w+)\W+)+`|Ardından bir veya daha fazla sözcük karakteri deseniyle eşleşen veya bir veya daha fazla kez daha fazla sözcük olmayan karakter. Bu ilk yakalama grubudur.|  
  
 Cümlenin her sözcüğün ilk yakalama grubuyla eşleşir. İkinci yakalama grubu kelimenin izleyen boşluk ve noktalama işaretleri ile birlikte her bir sözcüğü eşleştirir. <xref:System.Text.RegularExpressions.Group> Dizini 2 nesnenin ikinci yakalama grubuyla eşleşen metin hakkında bilgi sağlar. Eksiksiz bir kelimelerin yakalama grubu tarafından yakalanan web'da <xref:System.Text.RegularExpressions.CaptureCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
