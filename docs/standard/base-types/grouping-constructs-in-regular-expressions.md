---
title: "Normal İfadelerdeki Gruplandırma Yapıları"
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
- lookbehinds
- regular expressions, grouping constructs
- lookaheads
- .NET Framework regular expressions, grouping constructs
- constructs, grouping
- grouping constructs
ms.assetid: 0fc18634-f590-4062-8d5c-f0b71abe405b
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b6e0b9d3482bbfc3dabeee1f6b7fce7a93364dfb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="grouping-constructs-in-regular-expressions"></a>Normal İfadelerdeki Gruplandırma Yapıları
Gruplandırma yapıları normal ifadenin alt ifadelerin tanımlamak ve bir Giriş dizesinin alt dizeler yakalayın. Aşağıdakileri yapmak için gruplandırma yapıları kullanabilirsiniz:  
  
-   Giriş dizesi içinde yinelenen bir alt eşleşir.  
  
-   Bir niceleyici birden çok normal ifade dili öğesi içeren bir alt uygulayın. Miktar belirleyiciler hakkında daha fazla bilgi için bkz: [nicelik](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
-   Bir alt tarafından döndürülen dize dahil <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemleri.  
  
-   Tek tek alt ifadelerin gelen almak <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği ve bunları ayrı ayrı bir bütün olarak eşleşen metinden işlem.  
  
 Aşağıdaki tabloda .NET normal ifade altyapısı tarafından desteklenen gruplandırma yapıları listeler ve bunlar yakalama yakalama dışı mı olduğunu gösterir.  
  
|Yapıyı gruplandırma|Yakalama veya Yakalama yapmayan|  
|------------------------|-------------------------------|  
|[Eşleşen alt ifadelerin](#matched_subexpression)|Yakalama|  
|[Eşleşen alt ifadelerin adlı](#named_matched_subexpression)|Yakalama|  
|[Grup tanımlarını Dengeleme](#balancing_group_definition)|Yakalama|  
|[Yakalama yapmayan grupları](#noncapturing_group)|Yakalama yapmayan|  
|[Grup seçenekleri](#group_options)|Yakalama yapmayan|  
|[Pozitif ileri yönlü Sıfır Genişlik onayları](#zerowidth_positive_lookahead_assertion)|Yakalama yapmayan|  
|[Negatif ileri yönlü Sıfır Genişlik onayları](#zerowidth_negative_lookahead_assertion)|Yakalama yapmayan|  
|[Pozitif geriye ilerleme Sıfır Genişlik onayları](#zerowidth_positive_lookbehind_assertion)|Yakalama yapmayan|  
|[Negatif geriye ilerleme Sıfır Genişlik onayları](#zerowidth_negative_lookbehind_assertion)|Yakalama yapmayan|  
|[Nonbacktracking alt ifadelerin](#nonbacktracking_subexpression)|Yakalama yapmayan|  
  
 Gruplar ve normal ifade nesnesi modeli hakkında daha fazla bilgi için bkz: [gruplandırma yapıları ve normal ifade nesneleri](#Objects).  
  
<a name="matched_subexpression"></a>   
## <a name="matched-subexpressions"></a>Eşleşen Alt İfadeler  
 Aşağıdaki gruplama yapısı eşleşen alt yakalar:  
  
 `(`*alt*`)`  
  
 Burada *alt* herhangi geçerli bir normal ifade deseni. Ayraç kullanın otomatik olarak soldan sağa normal ifadede bir başlangıç açılış parantez terabayt dayalı numaralandırılır olduğunu yakalar. Numaralı sıfır yakalama tüm normal ifade deseni ile eşleşen metindir.  
  
> [!NOTE]
>  Varsayılan olarak, `(` *alt* `)` language öğesi eşleşen alt yakalar. Ancak <xref:System.Text.RegularExpressions.RegexOptions> yöntemi eşleşen bir normal ifade deseni parametresinin içerir <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> bayrağı veya `n` seçeneği, bu alt uygulandığında (bkz [Grup Seçenekleri](#group_options) bu konuda daha sonra), eşleşen alt sayılmaz.  
  
 Yakalanan gruplar dört farklı şekilde erişebilirsiniz:  
  
-   Yeniden başvuru kullanarak normal ifade içinde oluşturun. Eşleşen alt aynı normal ifadede sözdizimi kullanılarak başvurulur `\` *numarası*, burada *numarası* yakalanan alt sıra sayısı.  
  
-   Adlandırılmış yeniden başvuru kullanarak normal ifade içinde oluşturun. Eşleşen alt aynı normal ifadede sözdizimi kullanılarak başvurulur `\k<` *adı*`>`, burada *adı* yakalama bir grubun adı veya `\k<` *numarası*`>`, burada *numarası* bir yakalama grubunu sıra sayısı. Bir yakalama grubunu, sıra numarası aynı olan bir varsayılan adı vardır. Daha fazla bilgi için bkz: [adlandırılmış eşleşen alt ifadelerin](#named_matched_subexpression) bu konuda daha sonra.  
  
-   Kullanarak `$` *numarası* değiştirme sırayla bir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntem çağrısı, burada *numarası* yakalanan alt sıra sayısı.  
  
-   Kullanarak programlı olarak <xref:System.Text.RegularExpressions.GroupCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği. Üye koleksiyonda sıfır konumundaki tüm normal ifade eşleştirmesi temsil eder. Sonraki her üye bir eşleşen alt temsil eder. Daha fazla bilgi için bkz: [gruplandırma oluşturur ve normal ifade nesnelerini](#Objects) bölümü.  
  
 Aşağıdaki örnek metin içinde yinelenen sözcüklerin tanımlayan bir normal ifade gösterilmektedir. Normal ifade deseninin iki yakalama grupları yinelenen word iki örneğini temsil eder. İkinci örneği, giriş dizesi içindeki başlangıç konumunu bildirmek için yakalanır.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Normal ifade deseni aşağıda verilmiştir:  
  
```  
(\w+)\s(\1)\W  
```  
  
 Aşağıdaki tabloda, normal ifade deseni nasıl yorumlanacağını gösterir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\1)`|İlk yakalanan grubundaki dize eşleşmesi. Bu ikinci yakalama grubudur. Örnek böylece yinelenen Word başlangıç konumu hizmetinden alınan yakalanan bir gruba atar `Match.Index` özelliği.|  
|`\W`|Boşluk veya noktalama gibi bir sözcük olmayan karakter eşleşmesi. Bu, normal ifade deseni ilk yakalanan grubundan başlayan bir sözcük eşleşen önler.|  
  
<a name="named_matched_subexpression"></a>   
## <a name="named-matched-subexpressions"></a>Adlandırılmış Eşleşen Alt İfadeler  
 Aşağıdaki gruplama yapısı eşleşen alt yakalar ve ad numarasını arayarak veya erişmesine olanak tanır:  
  
```  
(?<name>subexpression)  
```  
  
 veya:  
  
```  
(?'name'subexpression)  
```  
  
 Burada *adı* geçerli grup adı ve *alt* herhangi geçerli bir normal ifade deseni. *ad* herhangi bir noktalama karakteri içermemelidir ve bir rakamla başlayamaz.  
  
> [!NOTE]
>  Varsa <xref:System.Text.RegularExpressions.RegexOptions> yöntemi eşleşen bir normal ifade deseni parametresinin içerir <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> bayrağı veya `n` seçeneği, bu alt uygulandığında (bkz [Grup Seçenekleri](#group_options) bu konuda daha sonra), yalnızca bir alt yakalamak için açıkça adı yakalama gruplarını yoludur.  
  
 Adlandırılmış yakalanan gruplar aşağıdaki yöntemlerle erişebilirsiniz:  
  
-   Adlandırılmış yeniden başvuru kullanarak normal ifade içinde oluşturun. Eşleşen alt aynı normal ifadede sözdizimi kullanılarak başvurulur `\k<` *adı*`>`, burada *adı* yakalanan alt adıdır.  
  
-   Yeniden başvuru kullanarak normal ifade içinde oluşturun. Eşleşen alt aynı normal ifadede sözdizimi kullanılarak başvurulur `\` *numarası*, burada *numarası* yakalanan alt sıra sayısı. Adlandırılmış eşleşen alt ifadelerin art arda soldan sağa sonra eşleşen alt ifadelerin numaralandırılır.  
  
-   Kullanarak `${` *adı* `}` değiştirme sırayla bir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntem çağrısı, burada *adı* yakalanan alt adıdır.  
  
-   Kullanarak `$` *numarası* değiştirme sırayla bir <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntem çağrısı, burada *numarası* yakalanan alt sıra sayısı.  
  
-   Kullanarak programlı olarak <xref:System.Text.RegularExpressions.GroupCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği. Üye koleksiyonda sıfır konumundaki tüm normal ifade eşleştirmesi temsil eder. Sonraki her üye bir eşleşen alt temsil eder. Adlandırılmış yakalanan gruplar numaralı yakalanan gruplar sonra koleksiyonunda depolanır.  
  
-   Alt adına sağlayarak programlı olarak <xref:System.Text.RegularExpressions.GroupCollection> nesnenin dizin oluşturucu (C# ' ta) veya kendi <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> özelliği (Visual Basic).  
  
 Basit normal ifade deseni gösterilmektedir nasıl (adlandırılmamış) numaralı ve adlandırılmış gruplar program aracılığıyla veya normal ifade dili sözdizimini kullanarak başvurulabilir. Normal ifade `((?<One>abc)\d+)?(?<Two>xyz)(.*)` aşağıdaki yakalama grubu sayısı ve ada göre üretir. İlk Grup (sayı 0) her zaman yakalama tüm düzeni başvuruyor.  
  
|Sayı|Ad|Desen|  
|------------|----------|-------------|  
|0|0 (varsayılan adı)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1.|1 (varsayılan adı)|`((?<One>abc)\d+)`|  
|2|2 (varsayılan adı)|`(.*)`|  
|3|Bir|`(?<One>abc)`|  
|4|iki|`(?<Two>xyz)`|  
  
 Aşağıdaki örnek, yinelenen sözcükler ve hemen her çoğaltılmış word izleyen word tanımlayan bir normal ifade gösterilmektedir. Normal ifade deseni iki adlandırılmış alt ifadelerin tanımlar: `duplicateWord`, yinelenen word; temsil eder ve `nextWord`, yinelenen word izleyen word temsil eder.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Normal ifade deseni aşağıdaki gibidir:  
  
```  
(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)  
```  
  
 Aşağıdaki tabloda, normal ifade nasıl yorumlanacağını gösterir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunu adlandırın `duplicateWord`.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`\k<duplicateWord>`|Adlı yakalanan grubundan bir dizeyle eşleştir `duplicateWord`.|  
|`\W`|Boşluk veya noktalama gibi bir sözcük olmayan karakter eşleşmesi. Bu, normal ifade deseni ilk yakalanan grubundan başlayan bir sözcük eşleşen önler.|  
|`(?<nextWord>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunu adlandırın `nextWord`.|  
  
 Bir grup adı normal ifadede yinelenebilir unutmayın. Örneğin, birden fazla Grup adlandırılması mümkündür `digit`aşağıdaki örnekte gösterildiği gibi. Yinelenen adları, değeri söz konusu olduğunda <xref:System.Text.RegularExpressions.Group> nesne giriş dizesi son başarılı yakalama tarafından belirlenir. Ayrıca, <xref:System.Text.RegularExpressions.CaptureCollection> yalnızca, grup adını değil yinelenen olduğu gibi her yakalama hakkında bilgi ile doldurulur.  
  
 Aşağıdaki örnekte, normal ifade `\D+(?<digit>\d+)\D+(?<digit>\d+)?` adlı bir grup iki oluşumu içeren `digit`. İlk `digit` bir veya daha fazla rakamlı karakter grubu yakalamaları adlı. İkinci `digit` adlandırılmış grubu bir veya daha fazla rakamlı karakter sıfır veya bir örneğini yakalar. İkinci yakalama başarıyla grup, örnekte gösterildiği çıktısını metinle eşleşen gibi bu metin değeri değerini tanımlar <xref:System.Text.RegularExpressions.Group> nesnesi. İkinci yakalama grubunu ayarlanmamışsa son başarılı eşleşme değerini giriş dizesi değerini tanımlar eşleşmiyor <xref:System.Text.RegularExpressions.Group> nesnesi.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 Aşağıdaki tabloda, normal ifade nasıl yorumlanacağını gösterir.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\D+`|Bir veya daha fazla ondalık olmayan basamak karakter eşleşmesi.|  
|`(?<digit>\d+)`|Bir veya daha fazla ondalık basamak karakter eşleşmesi. Eşleşen atamak `digit` Grup adlı.|  
|\D+|Bir veya daha fazla ondalık olmayan basamak karakter eşleşmesi.|  
|`(?<digit>\d+)?`|Bir veya daha fazla ondalık basamak karakter sıfır veya bir örneğini Bul. Eşleşen atamak `digit` Grup adlı.|  
  
<a name="balancing_group_definition"></a>   
## <a name="balancing-group-definitions"></a>Grup Tanımlarını Dengeleme  
 Dengeleme Grup tanımında önceden tanımlanmış bir grup ve geçerli grubu, önceden tanımlanmış grubu geçerli grubu arasındaki aralığı depoları tanımını siler. Bu gruplandırma yapıyı aşağıdaki biçime sahiptir:  
  
```  
(?<name1-name2>subexpression)  
```  
  
 veya:  
  
```  
(?'name1-name2' subexpression)  
```  
  
 Burada *Ad1* geçerli (isteğe bağlı), grubudur *ad2* önceden tanımlanmış bir grup ve *alt* herhangi geçerli bir normal ifade deseni. Dengeleme grubu tanımı tanımını siler *ad2* arasındaki aralığı ve depolar *ad2* ve *Ad1* içinde *Ad1*. Öyle değilse *ad2* Grup tanımlanır, eşleşme backtracks. Son tanımı silme çünkü *ad2* önceki tanımını gösterir *ad2*, bu yapıyı yakalamaları yığınını grubu için kullanmanıza olanak sağlayan *ad2* olarak bir parantez gibi iç içe geçmiş yapılar izlemek veya açmak ve ayraç sayacı.  
  
 Dengeleme grubu tanımını kullanan *ad2* bir yığın olarak. Her iç içe geçmiş yapı başlangıç karakteri grubu hem de yerleştirilir kendi <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> koleksiyonu. Kendi karakter karşılık gelen açma kapatma karakterini eşleştiğinde grubundan kaldırılır ve <xref:System.Text.RegularExpressions.Group.Captures%2A> koleksiyon tarafından düşer. Açma ve kapatma karakterini tüm iç içe geçmiş yapılar eşleşen sonra *Ad1* boş.  
  
> [!NOTE]
>  Sonra uygun açma kullanmak için aşağıdaki örnekte normal ifadeyi değiştirin ve iç içe geçmiş bir yapı karakterinin kapatmadan önce bunu matematiksel ifadeleri veya program kodunun içeren satırları gibi en iç içe geçmiş yapılar işlemek için kullanabilirsiniz birden çok iç içe geçmiş yöntemi çağırır.  
  
 Aşağıdaki örnekte bir dengeleme Grup tanımı sol ve sağ açılı ayraç (<>) bir giriş dizesini eşleştirmek için kullanır. Adlandırılmış iki grup örnek tanımlar `Open` ve `Close`, yığın gibi köşeli eşleşen çiftlerini izlemek için kullanılır. Her yakalanan Sol açılı ayraç yakalama koleksiyonunu gönderilen `Open` grubu ve her yakalanan sağ açılı ayraç yakalama koleksiyonunu gönderilen `Close` grubu. Dengeleme grubu tanımı her sol açılı ayraç için eşleşen bir sağ açılı ayraç olmasını sağlar. Yoksa son desenin `(?(Open)(?!))`, yalnızca hesaplanan `Open` grubu boş değil (ve bu nedenle, tüm iç içe geçmiş yapılar yoksa kapatılmış). Son desenin değerlendirildiğinde eşleşmesi, çünkü başarısız `(?!)` desenin olduğundan her zaman başarısız Sıfır Genişlik negatif ileri yönlü onaylama.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Normal ifade deseni aşağıdaki gibidir:  
  
```  
^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$  
```  
  
 Normal ifade şu şekilde yorumlanır:  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Dizenin başında başlar.|  
|`[^<>]*`|Sol veya sağ açılı ayraç olmayan sıfır veya daha fazla karakteri eşleştirmek.|  
|`(?'Open'<)`|Adlı bir gruba atamak ve Sol açılı ayraç eşleşiyor `Open`.|  
|`[^<>]*`|Sol veya sağ açılı ayraç olmayan sıfır veya daha fazla karakteri eşleştirmek.|  
|`((?'Open'<)[^<>]*) +`|Sol veya sağ açılı ayraç olmayan sıfır veya daha fazla karakterle devam etmelidir Sol açılı ayraç bir veya daha fazla oluşumları eşleşir. Bu ikinci yakalama grubudur.|  
|`(?'Close-Open'>)`|Sağ açılı ayraç eşleşen, alt dizeyi arasında Ata `Open` grubu ve geçerli grubu `Close` grup ve tanımını silin `Open` grubu.|  
|`[^<>]*`|Türünün bir sol veya sağ açılı ayraç değil herhangi bir karakter, sıfır veya daha fazla tekrarı eşleşir.|  
|`((?'Close-Open'>)[^<>]*)+`|Bir veya daha fazla oluşumları sağ açılı ayraç eşleşmiyor, herhangi bir karakterin sıfır veya daha çok tekrarı tarafından izlenen bir sol ne sağ açılı ayraç olmasıdır. Sağ açılı ayraç eşleştirme yapılırken arasında alt dizeyi atamak `Open` grubu ve geçerli grubu `Close` grup ve tanımını silin `Open` grubu. Bu, üçüncü yakalama grubudur.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Sıfır veya daha fazla deseninin aşağıdaki eşleşen: yineleme sağ açılı ayraç bir veya daha fazla izlenen sıfır veya daha fazla açılı ayraç olmayan karakter ve ardından sol açılı ayraç, bir veya daha çok tekrarı sıfır veya daha çok tekrarı tarafından izlenen olmayan-açılı ayraçları. Sağ açılı ayraç eşleştirme yapılırken tanımını silmek `Open` grup ve alt dizeyi arasında atayın `Open` grubu ve geçerli gruba `Close` grubu. Bu ilk yakalama grubudur.|  
|`(?(Open)(?!))`|Varsa `Open` grubu var, boş bir dize eşleşmesi gereken ancak dizedeki normal ifade altyapısı ilerletmek değil eşleşme bırakın. Bu, sıfır Genişlik negatif ileri yönlü onayı ifade eder. Boş bir dize her zaman bir giriş dizesi içinde örtük olarak mevcut olduğundan, bu eşleşme her zaman başarısız olur. Bu eşleşme hatası köşeli değil dengeli gösterir.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
 Son alt `(?(Open)(?!))`, içinde iç içe geçme yapıları olup olmadığını giriş dizesi düzgün Dengeli (örneğin, her sol açılı ayraç sağ açılı ayraç tarafından eşleşen olup olmadığını) gösterir. Geçerli bir yakalanmış grubuna göre koşullu eşleşen kullanır; Daha fazla bilgi için bkz: [değişim yapıları](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md). Varsa `Open` Grup tanımlanır, normal ifade altyapısı alt eşleştirmeyi dener `(?!)` giriş dizesi içinde. `Open` Yalnızca iç içe geçmiş yapılar dengesiz ise Grup tanımlanmalıdır. Bu nedenle, girdi dizesindeki eşleştirilecek desen her zaman eşleştirme başarısız olmasına neden olan bir olmalıdır. Bu durumda, `(?!)` boş bir dize her zaman giriş dizesi sonraki konumda örtük olarak mevcut Sıfır Genişlik negatif ileri yönlü onaylama her zaman başarısız olduğundan.  
  
 Örnekte, normal ifade altyapısı giriş dizesi değerlendirir "\<abc >< mno\<xyz >>" aşağıdaki tabloda gösterildiği gibi.  
  
|Adım|Desen|Sonuç|  
|----------|-------------|------------|  
|1.|`^`|Giriş dizesi başındaki eşleşme başlatır|  
|2|`[^<>]*`|Sol açılı ayraç önce açılı ayraç karakterler arar; herhangi bir eşleşme bulur.|  
|3|`(((?'Open'<)`|Sol açılı ayraç içinde eşleşen "\<abc >" ve atar `Open` grubu.|  
|4|`[^<>]*`|"Abc" ile eşleşir.|  
|5|`)+`|"< abc" ikinci yakalanan grubu değeri.<br /><br /> Normal ifade altyapısı geri döngü değil giriş dizesi sonraki karakteri Sol açılı ayraç olmadığından `(?'Open'<)[^<>]*)` desenin.|  
|6|`((?'Close-Open'>)`|Sağ açılı ayraç içinde eşleşen "\<abc >", alt dizesidir "abc" atar arasında `Open` grubu ve sağ açılı ayraç, çok `Close` grup ve geçerli değeri siler ("<"), `Open` grubu boş bırakın.|  
|7|`[^<>]*`|Açılı ayraç karakterleri sağ açılı ayraç sonra arar; herhangi bir eşleşme bulur.|  
|8|`)+`|Üçüncü yakalanan grubu değeri ">".<br /><br /> Normal ifade altyapısı geri döngü değil giriş dizesi sonraki karakteri sağ açılı ayraç olmadığından `((?'Close-Open'>)[^<>]*)` desenin.|  
|9|`)*`|İlk yakalanan grup değeri "\<abc >".<br /><br /> Giriş dizisinde sonraki karakteri normal ifade altyapısı geri döngü Sol açılı ayraç kitabıdır `(((?'Open'<)` desenin.|  
|10|`(((?'Open'<)`|Sol açılı ayraç içinde eşleşen "\<mno >" ve atar `Open` grubu. Kendi <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> şimdi gruplandırmasında tek bir değer "<".|  
|11|`[^<>]*`|"Mno" eşleşir.|  
|12|`)+`|"< mno" ikinci yakalanan grubu değeri.<br /><br /> Normal ifade altyapısı geri döngü Sol açılı ayraç, giriş dizesi sonraki karakteri olduğundan `(?'Open'<)[^<>]*)` desenin.|  
|13|`(((?'Open'<)`|Sol açılı ayraç içinde eşleşen "\<xyz >" ve atar `Open` grubu. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Koleksiyonu `Open` grubu şimdi iki yakalamaları içerir: sol açılı ayraç gelen "\<mno >" ve Sol açılı ayraç gelen "\<xyz >".|  
|14|`[^<>]*`|"Xyz" eşleşir.|  
|15|`)+`|"< xyz" ikinci yakalanan grubu değeri.<br /><br /> Normal ifade altyapısı geri döngü değil giriş dizesi sonraki karakteri Sol açılı ayraç olmadığından `(?'Open'<)[^<>]*)` desenin.|  
|16|`((?'Close-Open'>)`|Sağ açılı ayraç içinde eşleşen "\<xyz >". "xyz" atar arasında alt dizeyi `Open` grubu ve sağ açılı ayraç için `Close` grup ve geçerli değeri siler `Open` grubu. Önceki yakalama değerini (sol açılı ayraç içinde "\<mno >") geçerli değeri olur `Open` grubu. <xref:System.Text.RegularExpressions.Group.Captures%2A> Koleksiyonu `Open` grubu artık tek bir yakalama, gelen Sol açılı ayraç içerir "\<xyz >".|  
|17|`[^<>]*`|Açılı ayraç karakterleri arar; herhangi bir eşleşme bulur.|  
|18|`)+`|Üçüncü yakalanan grubu değeri ">".<br /><br /> Giriş dizisinde sonraki karakteri normal ifade altyapısı geri döngü sağ açılı ayraç kitabıdır `((?'Close-Open'>)[^<>]*)` desenin.|  
|19|`((?'Close-Open'>)`|Son sağ açılı ayraç içinde eşleşen "xyz >>", atar "mno\<xyz >" (alt dizeyi arasında `Open` grubu ve sağ açılı ayraç) için `Close` grup ve geçerli değeri siler `Open` grubu. `Open` Grup boşsa şimdi.|  
|20|`[^<>]*`|Açılı ayraç karakterleri arar; herhangi bir eşleşme bulur.|  
|21|`)+`|Üçüncü yakalanan grubu değeri ">".<br /><br /> Normal ifade altyapısı geri döngü değil giriş dizesi sonraki karakteri sağ açılı ayraç olmadığından `((?'Close-Open'>)[^<>]*)` desenin.|  
|22|`)*`|İlk yakalanan grup değeri "< mno\<xyz >>".<br /><br /> Normal ifade altyapısı geri döngü değil giriş dizesi sonraki karakteri Sol açılı ayraç olmadığından `(((?'Open'<)` desenin.|  
|23|`(?(Open)(?!))`|`Open` Grup tanımlı değil, eşleşme denenmesi için.|  
|24|`$`|Giriş dizesi sonu ile eşleşir.|  
  
<a name="noncapturing_group"></a>   
## <a name="noncapturing-groups"></a>Yakalama Yapmayan Gruplar  
 Aşağıdaki gruplama yapısı, bir alt tarafından eşleşen alt dizeyi yakalama değil:  
  
```  
(?:subexpression)  
```  
  
 Burada *alt* herhangi geçerli bir normal ifade deseni. Yakalama yapmayan grup yapısı, genellikle bir niceleyici bir gruba uygulanır, ancak hiçbir ilgilendiğiniz grubu tarafından yakalanan alt dizeler kullanılır.  
  
> [!NOTE]
>  Normal bir ifade iç içe gruplandırma yapıları içeriyorsa, bir dış Yakalama yapmayan grup yapısıyla iç içe geçmiş Grup yapıları için geçerli değildir.  
  
 Aşağıdaki örnek, Yakalama yapmayan gruplarını kapsayan bir normal ifade gösterilmektedir. Çıktı yakalanan tüm grupları içermiyorsa unutmayın.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Normal ifade `(?:\b(?:\w+)\W*)+\.` bir döneme göre sonlandırıldı bir cümle eşleşir. Normal ifade cümleleri ve değil ayrı ayrı sözcükleri odaklanan, gruplandırma yapıları özel olarak nicelik kullanılır. Normal ifade deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?:\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Eşleşen metin yakalanan grubuna atamayın.|  
|`\W*`|Sıfır veya daha fazla word olmayan karakterler eşleşiyor.|  
|`(?:\b(?:\w+)\W*)+`|Sıfır veya daha fazla sözcük olmayan karakterleri tarafından izlenen bir word sınır başlayarak bir veya daha fazla sözcük karakterleri deseni, bir veya birden çok kez eşleşir. Eşleşen metin yakalanan grubuna atamayın.|  
|`\.`|Bir süre aynı.|  
  
<a name="group_options"></a>   
## <a name="group-options"></a>Grup Seçenekleri  
 Aşağıdaki gruplama yapısı uygular veya bir alt içinde belirtilen seçeneklerini devre dışı bırakır:  
  
 `(?imnsx-imnsx:`*alt*`)`  
  
 Burada *alt* herhangi geçerli bir normal ifade deseni. Örneğin, `(?i-s:)` büyük/küçük harfe üzerinde kapatır ve tek satırlı modunu devre dışı bırakır. Belirtebilirsiniz satır içi seçenekleri hakkında daha fazla bilgi için bkz: [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
>  Kullanarak bir alt yerine tüm normal ifadenin geçerli seçenekleri belirtmek bir <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıf oluşturucu veya bir statik yöntem. Kullanarak bir normal ifade içinde belirli bir noktaya sonra geçerli satır içi seçenekleri de belirtebilirsiniz `(?imnsx-imnsx)` dil yapısı.  
  
 Grup seçenekleri yapı yakalama bir grup değil. Diğer bir deyişle, ancak herhangi bir kısmının tarafından yakalanan bir dize *alt* eklenmiştir eşlemesinde onu değil bir yakalanan grubunda yer alan ve doldurmak için kullanılan <xref:System.Text.RegularExpressions.GroupCollection> nesnesi.  
  
 Örneğin, normal ifade `\b(?ix: d \w+)\s` büyük küçük harf duyarsız eşleştirmeyi etkinleştir ve "d" harfiyle başlayan tüm sözcükleri tanımlayan içinde düzeni boşluk yoksaymak için aşağıdaki örnekte satır içi seçeneklerini bir gruplama yapısı kullanır. Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?ix: d \w+)`|Büyük küçük harf duyarsız eşleşen ve boşluk bu modelinde yoksayılıyor kullanarak, bir veya daha fazla sözcük karakterlerini tarafından izlenen bir "d" eşleşir.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>   
## <a name="zero-width-positive-lookahead-assertions"></a>Sıfır Genişlik Pozitif İleriye Yönelik Onaylar  
 Aşağıdaki gruplama yapısı Sıfır Genişlik pozitif ileri yönlü onaylama tanımlar:  
  
 `(?=`*alt*`)`  
  
 Burada *alt* herhangi normal ifade deseni. Bir eşleşme başarılı olması normal ifade deseni giriş dizesi eşleşmelidir *alt*, eşleşen alt dizeyi eşleştir sonucunda almamakla. Sıfır Genişlik pozitif ileri yönlü onaylama geri izlemeyi değil.  
  
 Genellikle, sıfır genişlik pozitif ileri yönlü onaylama bir normal ifade deseni sonunda yer alır. Bir dize gerçekleşmesi bir eşleşme sonunda bulunması gereken ancak, eşlemesinde dahil edilmemesi gereken bir alt dizesi tanımlar. Aşırı geri dönüş önlemek için yararlıdır. Belirli bir yakalanan grubun bir alt kümesini yakalanan o grup için tanımlanmış düzeni eşleşen metni ile başlayan emin olmak için sıfır genişlik pozitif ileri yönlü onaylama kullanabilirsiniz. Örneğin, bir yakalama grubunu ardışık sözcük karakterlerini eşleşirse, ilk karakter alfabetik bir büyük harf karakter olmasını gerektirecek şekilde Sıfır Genişlik pozitif ileri yönlü onaylama kullanabilirsiniz.  
  
 Fiili önündeki word eşleşecek şekilde Sıfır Genişlik pozitif ileri yönlü onaylama "giriş dizesi" aşağıdaki örnekte kullanır.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Normal ifade `\b\w+(?=\sis\b)` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`(?=\sis\b)`|Sözcük karakterlerini sonrasında bir boşluk karakteri ve dize "olan" word sınırında hangi uçları olup olmadığını belirler. Bu durumda, başarılı bir eşleşmedir.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>   
## <a name="zero-width-negative-lookahead-assertions"></a>Sıfır Genişlik Negatif İleriye Yönelik Onaylar  
 Aşağıdaki gruplama yapısı Sıfır Genişlik negatif ileri yönlü onaylama tanımlar:  
  
 `(?!`*alt*`)`  
  
 Burada *alt* herhangi normal ifade deseni. Eşleşme başarılı olması giriş dizesi normal ifade deseni eşleşmemelidir *alt*, eşleşen dize eşleştirme sonucunda almamakla.  
  
 Sıfır Genişlik negatif ileri yönlü onaylama genellikle başında veya sonunda normal bir ifade yer kullanılır. Normal bir ifade başlangıcında, normal ifade başlangıcını eşleştirilmesini benzerdir, ancak daha genel bir desen tanımladığında eşleştirilmesi gerektiğini değil belirli bir desen tanımlayabilirsiniz. Bu durumda, bu genellikle geri dönüş sınırlamak için kullanılır. Normal bir ifade sonunda bir eşleşme sonunda gerçekleşemez bir alt tanımlayabilirsiniz.  
  
 Aşağıdaki örnekte, "Çalıştır" ile başlamayan sözcükleri eşleştirmeye normal ifade başında sıfır genişlik ileri yönlü onaylama kullanan normal bir ifade tanımlar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Normal ifade `\b(?!un)\w+\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(?!un)`|Sonraki iki karakter "Çalıştır" olup olmadığını belirleyin. Değilse, bir eşleşme mümkündür.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Aşağıdaki örnek, bir noktalama karakteri ile bitmeyen sözcükleri eşleştirmeye normal ifade sonunda Sıfır Genişlik ileri yönlü onaylama kullanan normal bir ifade tanımlar.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Normal ifade `\b\w+\b(?!\p{P})` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
|`\p{P})`|Sonraki karakteri bir noktalama işareti sembolü (örneğin, bir nokta veya virgül) değilse, eşleştirmenin başarılı olur.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>   
## <a name="zero-width-positive-lookbehind-assertions"></a>Sıfır Genişlik Pozitif Geriye Yönelik Onaylar  
 Aşağıdaki gruplama yapısı Sıfır Genişlik pozitif geriye ilerleme onaylama tanımlar:  
  
 `(?<=`*alt*`)`  
  
 Burada *alt* herhangi normal ifade deseni. Başarılı olması bir eşleşme *alt* giriş dizesi geçerli konumlarından sola rağmen ortaya `subexpression` eşleşme sonucunda dahil edilmez. Sıfır Genişlik pozitif geriye ilerleme onaylama geri izlemeyi değil.  
  
 Pozitif geriye ilerleme Sıfır Genişlik onayları genellikle normal ifadeler başında kullanılır. Bunlar tanımlamak desen bir eşleştirme için önkoşul olsa eşleşen sonuç bir parçası değil.  
  
 Örneğin, aşağıdaki örnekte yirmi birinci yüzyıl için yılın son iki basamak eşleştirir (diğer bir deyişle, bunu "20" basamak eşleşen dize koyun gerektirir).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Normal ifade deseni `(?<=\b20)\d{2}\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\d{2}`|İki ondalık basamak eşleşir.|  
|`{?<=\b20)`|İki ondalık basamak word sınırında ondalık basamak "20" öncesinde eşleşme devam edin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Sıfır Genişlik pozitif geriye ilerleme onaylar, o grubun normal ifade ile eşleşen karakter kümesini son karakteri veya yakalanan grubu karakter olması gerektiğinde geri dönüş sınırlamak için de kullanılır. Örneğin, bir grup tüm ardışık sözcük karakterlerini yakalar, son karakter alfabetik gerektirecek şekilde Sıfır Genişlik pozitif geriye ilerleme onaylama kullanabilirsiniz.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>   
## <a name="zero-width-negative-lookbehind-assertions"></a>Sıfır Genişlik Negatif Geriye Yönelik Onaylar  
 Aşağıdaki gruplama yapısı Sıfır Genişlik negatif geriye ilerleme onaylama tanımlar:  
  
 `(?<!`*alt*`)`  
  
 Burada *alt* herhangi normal ifade deseni. Başarılı olması bir eşleşme *alt* giriş dizesi geçerli konumlarından sola oluşamaz. Ancak, herhangi bir eşleşmeyen substring `subexpression` eşleşme sonucunda dahil edilmez.  
  
 Negatif geriye ilerleme Sıfır Genişlik onayları genellikle normal ifadeler başında kullanılır. Bunlar tanımlamak deseni izler dizesindeki bir eşleşme olanağını engeller. Son karakteri veya karakterleri yakalanan grubundaki bir veya daha fazla grubun normal ifade ile eşleşen karakter olmamalıdır, geri dönüş sınırlamak için de kullanılır. Örneğin, bir grup tüm ardışık sözcük karakterlerini yakalar, son karakter bir alt çizgi (_) olmaması gerektirecek şekilde Sıfır Genişlik pozitif geriye ilerleme onaylama kullanabilirsiniz.  
  
 Aşağıdaki örnekte herhangi bir hafta sonu değil haftanın gününü tarihini eşleşen (diğer bir deyişle, Cumartesi ne Pazar olmasıdır).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Normal ifade deseni `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakterlerini sonrasında bir boşluk karakteri eşleşmesi.|  
|`\d{1,2},`|Ardından bir boşluk karakteri ve virgül bir veya iki ondalık basamak eşleşir.|  
|`\d{4}\b`|Eşleşen bir word sınır en son ve dört ondalık basamak eşleşmiyor.|  
|`(?<!(Saturday&#124;Sunday) )`|Eşleşen dizeler "Cumartesi" veya "bir boşluk bırakarak Pazar" dışında bir şey öncesinde, başarılı bir eşleşmedir.|  
  
<a name="nonbacktracking_subexpression"></a>   
## <a name="nonbacktracking-subexpressions"></a>Geri Dönüşlü Olmayan Alt İfadeler  
 Aşağıdaki gruplama yapısı nonbacktracking alt ("Hızlı" alt olarak da bilinir) temsil eder:  
  
 `(?>`*alt*`)`  
  
 Burada *alt* herhangi normal ifade deseni.  
  
 Normalde, normal bir ifade isteğe bağlı bir içerir veya desen ve bir eşleşme eşleşen alternatif başarılı olmaz, normal ifade altyapısı giriş dizesi bir desen ile eşleştirmek için birden çok yönde dal. İlk şube yönlendirdiğinde bir eşleşme bulunmazsa, normal ifade altyapısı yedekleyebilir veya burada ilk eşleşmeye sürdü noktasına geri izlemeyi ve ikinci şube kullanarak Eşleştir dener. Bu işlem, tüm dalları deneninceye kadar devam edebilirsiniz.  
  
 `(?>` *Alt* `)` dil oluşturmak geri dönüş devre dışı bırakır. Normal ifade altyapısı giriş dizesi mümkün olduğunca çok karakter ile eşleşir. Daha fazla eşleşme mümkün olduğunda, bu alternatif desen eşleşmeleri girişiminde geri izlemeyi değil. (Diğer bir deyişle, alt alt ifade ile eşleşen dizeleri eşleşen; alt ve onu izleyen hiçbir alt ifadelerin dayalı bir dizeyi eşleştirmek çalışmaz.)  
  
 Geri dönüş başarılı olmaz olduğunu biliyorsanız, bu seçenek önerilir. Normal ifade altyapısı gereksiz arama gerçekleştirmesini engelleyen performansı artırır.  
  
 Aşağıdaki örnek, nasıl bir desen eşleştirme sonuçlarını nonbacktracking alt değiştirir gösterilmektedir. Birden çok oluşum aynı karakterin tarafından word sınırında yinelenen karakterlik bir dizi başarıyla kırıntıları oluşturma normal ifadeyle eşleşen ancak nonbacktracking normal ifade içermiyor.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Nonbacktracking normal ifade `(?>(\w)\1+).\b` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(\w)`|İlk yakalama grubuna atayın ve tek bir sözcük karakteriyle eşleşmiyor.|  
|`\1+`|İlk yakalanan alt dize değeri bir veya birden çok kez aynı.|  
|`.`|Herhangi bir karakter eşleşmesi.|  
|`\b`|Son bir word sınırında eşleşmiyor.|  
|`(?>(\w)\1+)`|Bir veya daha fazla karakterin yineleme sayısını bir yinelenen word eşleşen ancak word sınır son karakteri eşleştirmek için geri izlemeyi değil.|  
  
<a name="Objects"></a>   
## <a name="grouping-constructs-and-regular-expression-objects"></a>Yapıları ve Normal İfade Nesnelerini Gruplandırma  
 Grup yakalama normal bir ifadeyle eşleşen alt dizeler temsil ettiği <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> kaynağından alınan nesneleri <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği. <xref:System.Text.RegularExpressions.GroupCollection> Nesnesi gibi doldurulmuş:  
  
-   İlk <xref:System.Text.RegularExpressions.Group> (sıfır dizininde bulunan nesne) koleksiyon nesnesinde tüm eşleşme temsil eder.  
  
-   Sonraki kümesi <xref:System.Text.RegularExpressions.Group> nesneleri adlandırılmamış (numaralı) yakalama gruplarını temsil eder. Normal ifadede soldan sağa içinde tanımlı oldukları sırada görünürler. 1 adlandırılmamış sayısı ile bu gruplar arasında dizin değerini koleksiyonu gruplarında yakalama. (Kendi numaralı yeniden başvuru için belirli bir grubun dizinini eşdeğerdir. Yeniden başvurular hakkında daha fazla bilgi için bkz: [yeniden başvuru yapıları](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)  
  
-   En son kümesi <xref:System.Text.RegularExpressions.Group> nesneler adlandırılmış yakalama gruplarını temsil eder. Normal ifadede soldan sağa içinde tanımlı oldukları sırada görünürler. Yakalama grubunu adlı ilk dizin değerini son adlandırılmamış yakalama grubunu dizin büyük biridir. Varsa normal ifade gruplarında yakalama adlandırılmamış, yakalama grubunu adlı ilk dizin değerini biridir.  
  
 Bir niceleyici karşılık gelen bir yakalama grubuna uygularsanız <xref:System.Text.RegularExpressions.Group> nesnenin <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>, <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType>, ve <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> özellikleri yakalama grubu tarafından yakalanan son alt dizeyi yansıtır. Nicelik alanından grupları tarafından yakalanan alt dizeler eksiksiz bir kümesini alabilirsiniz <xref:System.Text.RegularExpressions.CaptureCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği.  
  
 Aşağıdaki örnek arasındaki ilişkiyi açıklar <xref:System.Text.RegularExpressions.Group> ve <xref:System.Text.RegularExpressions.Capture> nesneleri.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Normal ifade deseni `\b(\w+)\W+)+` sözcükleri tek tek bir dizeden ayıklar. Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Birlikte, bu karakterler bir sözcük oluştururlar. Bu ikinci yakalama grubudur.|  
|`\W+`|Bir veya daha fazla word olmayan karakter eşleşmesi.|  
|`(\w+)\W+)+`|Tarafından izlenen bir veya daha fazla sözcük karakterlerini desenle eşleşen veya daha fazla word olmayan bir veya birden çok kez karakter. Bu ilk yakalama grubudur.|  
  
 İlk yakalama grubunu her sözcüğün tümcenin eşleşir. İkinci yakalama grubunu noktalama işaretleri ve word izleyin boşluk birlikte her sözcüğün eşleşir. <xref:System.Text.RegularExpressions.Group> Dizinini 2 olan nesne ikinci yakalama grubu tarafından eşleşen metni hakkında bilgi sağlar. Yakalama grubu tarafından yakalanan sözcükler tamamını web'da <xref:System.Text.RegularExpressions.CaptureCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
