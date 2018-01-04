---
title: "Takvimlerle çalışma"
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
- globalization [.NET Framework], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET Framework], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c3a54d5222edca0b42f30c33584f0f62aa96f9e2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="working-with-calendars"></a>Takvimlerle çalışma

Tarih ve saat değeri zaman içinde bir anı gösterse de, dize gösterimi kültüre duyarlıdır ve hem belirli bir kültür saat tarafından saat ve tarih değerlerini görüntülemek için kullanılan kurallara, hem de kültür tarafından kullanılan takvime dayalıdır. Bu konu, .NET takvimlerinde desteği inceler ve Takvim sınıfların tarih değerleri ile çalışırken kullanmayı açıklar.

## <a name="calendars-in-net"></a>.NET takvimlerinde

.NET tüm takvimlerde türetin <xref:System.Globalization.Calendar?displayProperty=nameWithType> Takvim uygulaması sağlayan sınıf. Öğesinden devralınan sınıflarından <xref:System.Globalization.Calendar> sınıfı <xref:System.Globalization.EastAsianLunisolarCalendar> tüm Ay Güneş takvimleri için temel sınıf olan sınıf. .NET aşağıdaki Takvim uygulamaları içerir:

* <xref:System.Globalization.ChineseLunisolarCalendar>, Çince Ay Güneş Takvim temsil eder.

* <xref:System.Globalization.GregorianCalendar>, Gregoryen takvim temsil eder. Bu takvimi tarafından tanımlanan alt türleri (örneğin, Arapça ve Ortadoğu Fransızca) daha fazla bölünmüştür <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> numaralandırması. <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> Özelliği, alt Gregoryen takvim türünü belirtir.

* <xref:System.Globalization.HebrewCalendar>, İbranice Takvim temsil eder.

* <xref:System.Globalization.HijriCalendar>, Hicri takvimin temsil eder.

* <xref:System.Globalization.JapaneseCalendar>, Japonca Takvim temsil eder.

* <xref:System.Globalization.JapaneseLunisolarCalendar>, Japonca Ay Güneş Takvim temsil eder.

* <xref:System.Globalization.JulianCalendar>, Jülyen takvimi temsil eder.

* <xref:System.Globalization.KoreanCalendar>, Kore dili Takvim temsil eder.

* <xref:System.Globalization.KoreanLunisolarCalendar>, Kore dili Ay Güneş Takvim temsil eder.

* <xref:System.Globalization.PersianCalendar>, Farsça Takvim temsil eder.

* <xref:System.Globalization.TaiwanCalendar>, Tayvan Takvim temsil eder.

* <xref:System.Globalization.TaiwanLunisolarCalendar>, Tayvan Ay Güneş Takvim temsil eder.

* <xref:System.Globalization.ThaiBuddhistCalendar>, Tay Budist takvimi temsil eder.

* <xref:System.Globalization.UmAlQuraCalendar>, Um Al Qura Takvim temsil eder.

Bir takvim iki şekilde kullanılabilir:

* Belirli bir kültür tarafından kullanılan takvim olarak. Her <xref:System.Globalization.CultureInfo> nesnesi nesne şu anda kullandığı takvim geçerli bir takvim sahiptir. Tüm tarih ve saat değerlerinin dize gösterimleri, otomatik olarak geçerli kültürü ve onun geçerli takvimini yansıtır. Genellikle, geçerli takvim kültürün varsayılan takvimidir. <xref:System.Globalization.CultureInfo>nesneler de kültüre kullanabilirsiniz ek takvimler dahil isteğe bağlı takvimleri vardır.

* Belirli bir takvimden bağımsız tek başına bir takvim olarak. Bu durumda, <xref:System.Globalization.Calendar> yöntemleri tarih Takvim yansıtacak değerleri olarak ifade etmek için kullanılır.

Altı sınıfları – Takvim Not <xref:System.Globalization.ChineseLunisolarCalendar>, <xref:System.Globalization.JapaneseLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar>, ve <xref:System.Globalization.TaiwanLunisolarCalendar> – yalnızca tek başına takvimler kullanılabilir. Herhangi bir kültür tarafından varsayılan takvim olarak veya isteğe bağlı bir takvim olarak kullanılmazlar.

## <a name="calendars-and-cultures"></a>Takvim ve kültürler

Her kültür tarafından tanımlanan varsayılan takvim sahip <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> özelliği. <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> Özelliği bir dizi döndürür <xref:System.Globalization.Calendar> nesneleri bu kültürün varsayılan takvim dahil olmak üzere belirli bir kültür tarafından desteklenen tüm takvimleri belirtir.

Aşağıdaki örnek gösterilmektedir <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özellikleri. Oluşturduğu `CultureInfo` nesneleri Tay dili (Tayland) ve Japonca (Japonya) kültürler için ve, varsayılan ve isteğe bağlı takvimleriyle görüntüler. Her iki durumda da kültürün varsayılan takvim de dahil edilmesini Not <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> koleksiyonu.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Belirli bir tarafından kullanılmakta Takvim <xref:System.Globalization.CultureInfo> nesne kültürün tarafından tanımlanan <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> özelliği. Bir kültürün <xref:System.Globalization.DateTimeFormatInfo> nesnesi tarafından döndürülen <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği. Bir kültür oluşturulduğunda, varsayılan değeri değeri ile aynı olduğu <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> özelliği. Ancak, tarafından döndürülen dizi içinde yer alan herhangi bir takvime kültürün geçerli Takvim değiştirebilirsiniz <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özelliği. Geçerli Takvim dahil değilse bir takvime ayarlamaya çalışırsanız <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özellik değeri bir <xref:System.ArgumentException> oluşturulur.

Aşağıdaki örnekte, Arap (Suudi Arabistan) kültürü tarafından kullanılan takvim değiştirilmektedir. İlk başlatır bir <xref:System.DateTime> değeri ve - olan, bu durumda, İngilizce (ABD) - geçerli kültür ve (Bu, bu durumda, Gregoryen takvim) geçerli kültürün takvim kullanarak görüntüler. Ardından, geçerli kültürü Arapça (Suudi Arabistan) olacak şekilde değiştirir ve kendi varsayılan Ümmül Kura takvimini kullanarak tarihi görüntüler. Daha sonra çağırır `CalendarExists` Arapça (Suudi Arabistan) kültür tarafından Hicri takvimin desteklenip desteklenmediğini belirlemek için yöntem. Takvim desteklendiğinden, geçerli takvimi Hicri olacak şekilde değiştirir ve yine tarihi görüntüler. Her bir durumda, tarih geçerli kültürün geçerli takvimi kullanılarak görüntülenir.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Tarih ve Takvim

Türünde bir parametre içeren oluşturucular dışında <xref:System.Globalization.Calendar> ve atanmış bir takvim değerleri yansıtacak şekilde bir tarih (diğer bir deyişle, ay, gün ve yıl) öğelerini izin her ikisi de <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri her zaman Gregoryen takvim üzerinde temel. Bu, örneğin, anlamına <xref:System.DateTime.Year%2A?displayProperty=nameWithType> özelliği Gregoryen takvim yılı döndürür ve <xref:System.DateTime.Day%2A?displayProperty=nameWithType> özelliği Gregoryen takvim ayın günü döndürür.

> [!IMPORTANT]
> Bir tarih değeri ile onun dize gösterimi arasında bir fark olduğunu unutmamak önemlidir. İlki Gregoryen takvime dayalıdır; ikincisi ise belirli bir kültürün geçerli takvimine dayalıdır.

Aşağıdaki örnek arasındaki bu farklılık gösterir <xref:System.DateTime> özellikleri ve bunların karşılık gelen <xref:System.Globalization.Calendar> yöntemleri. Örnekte, geçerli kültür Arapça (Mısır) ve geçerli Takvim Ümmül Kura'dır. A <xref:System.DateTime> değeri 2011 yedinci ayın on beşinci günün için ayarlanır. Bu aynı değerleri tarafından döndürülen çünkü bu bir Gregoryen tarih olarak yorumlanır Temizle <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> sabit kültür kuralları kullandığında yöntemi. Geçerli kültürün kuralları kullanılarak biçimlendirilen tarihin dize gösterimi, Ümmül Kura takvimindeki denk tarih olan 14/08/32'dir. Ardından, üyeleri `DateTime` ve `Calendar` gün, ay ve yıl değerini döndürmek için kullanılan <xref:System.DateTime> değeri. Her durumda, değerleri tarafından döndürülen <xref:System.DateTime> üyeleri tarafından döndürülen ancak Gregoryen takvim değerleri yansıtacak <xref:System.Globalization.UmAlQuraCalendar> üyeleri Uum al Qura takvimde değerleri yansıtacak.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiating-dates-based-on-a-calendar"></a>Bir takvime göre tarihleri örnek oluşturma

Çünkü <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerler Gregoryen takvim üzerinde temel, türünde bir parametre içeren bir aşırı yüklü Oluşturucu çağırmalısınız <xref:System.Globalization.Calendar> gün, ay veya yıl değerleri kullanmak istiyorsanız bir tarih değeri örneklemek için bir farklı takvim. Ayrıca belirli takvimi aşırı birini çağırabilirsiniz <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> yöntemi örneği oluşturmak için bir <xref:System.DateTime> nesne belirli bir takvim değerlerine bağlı.

Aşağıdaki örnekte bir örneğini oluşturur <xref:System.DateTime> geçirerek değeri bir <xref:System.Globalization.HebrewCalendar> nesnesine bir <xref:System.DateTime> oluşturucusu ve ikinci bir örneğini oluşturur <xref:System.DateTime> çağırarak değeri <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> yöntemi. İki değer İbranice aynı değerlerle oluşturulduğundan takvim, çağrısı <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> yöntemi gösterilir, iki <xref:System.DateTime> değerleri eşit.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>Geçerli Takvimdeki tarihleri temsil eden

Tarih ve saat biçimlendirme yöntemleri, tarihleri dizelere dönüştürürken her zaman geçerli takvimi kullanır. Bu, yılın, ayın ve ayın gününün dize gösteriminin geçerli takvimi yansıttığı ve Gregoryen takvimini yansıtmasının gerekli olmadığı anlamına gelir.

Aşağıdaki örnek, geçerli takvimin bir tarihin dize gösterimini nasıl etkilediğini göstermektedir. Geçerli kültürü Çince (Geleneksel, Tayvan) olarak değiştirir ve bir tarih değerini örnekler. Bunu daha sonra geçerli takvim ve tarihi görüntüler, geçerli Takvim değiştirir <xref:System.Globalization.TaiwanCalendar>ve tarih ve geçerli Takvim yine görüntüler. Tarih ilk kez görüntülendiğinde, Gregoryen takvimdeki bir tarih olarak gösterilir. İkinci kez görüntülendiğinde, Tayvan takvimindeki bir tarih olarak gösterilir.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>Geçerli olmayan Takvimdeki tarihleri temsil eden

Belirli bir kültür geçerli Takvim değil takvimden bir tarih temsil etmek için yöntemlerini çağırın <xref:System.Globalization.Calendar> nesnesi. Örneğin, <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, ve <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> yöntemleri, belirli bir takvim yansıtan değerlere yıl, ay ve gün Dönüştür.

> [!WARNING]
> Bazı takvimler herhangi kültürün isteğe bağlı takvimleri olmadığından, bu takvimlerde tarihleri göstermek, her zaman takvim yöntemlerini çağırmanızı gerektirir. Bu öğesinden türetilen tüm takvimlerdeki geçerlidir <xref:System.Globalization.EastAsianLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, ve <xref:System.Globalization.PersianCalendar> sınıfları.

Aşağıdaki örnek kullanan bir <xref:System.Globalization.JulianCalendar> bir tarih 9 Ocak 1905 Jülyen takvimi örneği oluşturmak için nesne. Bu tarih varsayılan (Gregoryen) takvimi kullanılarak görüntülendiğinde, 22 Ocak 1905 olarak gösterilir. Bağımsız çağırır <xref:System.Globalization.JulianCalendar> yöntemleri etkinleştirme tarihi Jülyen takvimi temsil edilebilir.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Takvim ve tarih aralıkları

Bir takvim tarafından desteklenen en erken tarihi bu takvimi tarafından gösterilen <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> özelliği. İçin <xref:System.Globalization.GregorianCalendar> tarih 1 Ocak 0001 C.E. olduğunu sınıfı Bir .NET takvimlerinde çoğunu sonraki bir tarihte destekler. Bir takvim önündeki tarih ve saat değeri ile çalışmaya çalışırken erken desteklenen tarih atar bir <xref:System.ArgumentOutOfRangeException> özel durum.

Ancak, önemli bir istisna vardır. (Başlatılmadı) varsayılan değerini bir <xref:System.DateTime> nesne ve <xref:System.DateTimeOffset> nesnesidir eşit <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> değeri. Bu tarih 1 Ocak 0001 C.E. desteklemeyen bir takvimdeki biçiminde çalışırsanız ve bir biçim belirticisi sağlamaz, "G" (genel tarih düzeni) biçim belirteci yerine "s" (sıralanabilir tarih düzeni) biçim belirticisi biçimlendirme yöntemi kullanır. Sonuç olarak, biçimlendirme işlem olmayan özel durum bir <xref:System.ArgumentOutOfRangeException> özel durum. Bunun yerine, desteklenmeyen tarihi döndürür. Bu değeri görüntüler aşağıdaki örnekte gösterilmiştir <xref:System.DateTime.MinValue?displayProperty=nameWithType> geçerli kültürü ayarlandığında Japonca (Japonya) Japonca takvimle ve Arapça (Mısır) için Um Al Qura takvimle. Ayrıca geçerli kültürü İngilizce (ABD) ve aramalar için ayarlar <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> her birinde yöntemiyle <xref:System.Globalization.CultureInfo> nesneleri. Her durumda, tarih sıralanabilir tarih/saat deseni kullanılarak görüntülenir.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>Eras ile çalışma

Takvimler genellikle tarihleri dönemlere ayırır. Ancak, <xref:System.Globalization.Calendar> .NET sınıfları bir takvim ve çoğu tarafından tanımlanan her dönem desteklemez <xref:System.Globalization.Calendar> sınıfları yalnızca tek bir dönem destekler. Yalnızca <xref:System.Globalization.JapaneseCalendar> ve <xref:System.Globalization.JapaneseLunisolarCalendar> sınıfları birden çok eras destekler.

### <a name="eras-and-era-names"></a>Eras ve dönem adları

.NET içinde belirli takvimi uygulaması tarafından desteklenen eras temsil eden tamsayılar ters sırada depolanır <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> dizi. Geçerli dönem ve sıfır dizininde içindir <xref:System.Globalization.Calendar> destekleyen birden çok eras, art arda gelen her dizin sınıfları önceki dönem yansıtır. Statik <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> özelliği tanımlar geçerli dönem için dizin <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> dizi; değeri olan her zaman sıfır bir sabit değer. Tek tek <xref:System.Globalization.Calendar> sınıfları ayrıca geçerli dönem değerini döndüren statik alanları içerir. Bunlar aşağıdaki tabloda listelenmiştir.

| Takvim sınıfı                                        | Geçerli dönem alanı                                                 |
| ----------------------------------------------------- | ----------------------------------------------------------------- |
| <xref:System.Globalization.ChineseLunisolarCalendar>  | <xref:System.Globalization.ChineseLunisolarCalendar.ChineseEra>   |
| <xref:System.Globalization.GregorianCalendar>         | <xref:System.Globalization.GregorianCalendar.ADEra>               |
| <xref:System.Globalization.HebrewCalendar>            | <xref:System.Globalization.HebrewCalendar.HebrewEra>              |
| <xref:System.Globalization.HijriCalendar>             | <xref:System.Globalization.HijriCalendar.HijriEra>                |
| <xref:System.Globalization.JapaneseLunisolarCalendar> | <xref:System.Globalization.JapaneseLunisolarCalendar.JapaneseEra> |
| <xref:System.Globalization.JulianCalendar>            | <xref:System.Globalization.JulianCalendar.JulianEra>              |
| <xref:System.Globalization.KoreanCalendar>            | <xref:System.Globalization.KoreanCalendar.KoreanEra>              |
| <xref:System.Globalization.KoreanLunisolarCalendar>   | <xref:System.Globalization.KoreanLunisolarCalendar.GregorianEra>  |
| <xref:System.Globalization.PersianCalendar>           | <xref:System.Globalization.PersianCalendar.PersianEra>            |
| <xref:System.Globalization.ThaiBuddhistCalendar>      | <xref:System.Globalization.ThaiBuddhistCalendar.ThaiBuddhistEra>  |
| <xref:System.Globalization.UmAlQuraCalendar>          | <xref:System.Globalization.UmAlQuraCalendar.UmAlQuraEra>          |

Belirli bir dönem sayıya karşılık gelen ad dönem sayıya geçirerek alınabilir <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> veya <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> yöntemi. Aşağıdaki örnek dönem desteği hakkında bilgi almak için bu yöntemleri çağırır <xref:System.Globalization.GregorianCalendar> sınıfı.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

Ek olarak, "g" özel tarih ve saat biçimi dizisi, bir tarih ve saatin dize gösteriminde bir takvimin dönem adını içerir. Daha fazla bilgi için bkz: [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Bir tarih dönemi ile örnek oluşturma

İki için <xref:System.Globalization.Calendar> birden çok eras destekleyen sınıflar, bir belirli yıl, ay ve değeri olabilir belirsiz, örneğin, ayın günü, tüm dört eras oluşan tarih <xref:System.Globalization.JapaneseCalendar> sahip 15 ' 1'den numaralı yıl. Normalde, bir dönem belirtilmezse, tarih ve saat ve takvim yöntemleri değerlerin geçerli döneme ait olduğunu varsayar. Dönem açıkça belirtmek için bir tarih başlatılırken bir <xref:System.Globalization.Calendar> , birden çok eras destekleyen sınıfı çağırabilirsiniz <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> yöntemi. Bu yöntem, takvimin yılı, ayı, günü, saati, dakikası, saniyesi ve milisaniyesiyle birlikte bir dönemi açıkça belirtmenize olanak tanır.

Aşağıdaki örnek kullanır <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> yöntemi tarafından desteklenen her dönem ikinci yılın ilk gününü ilk ayın aynı tarih örneği <xref:System.Globalization.JapaneseCalendar> sınıfı. Ardından, tarihi hem Japonca hem de Gregoryen takvimlerinde görüntüler. Ayrıca çağıran bir <xref:System.DateTime> bir dönem belirtmeden tarih değerlerini oluşturma yöntemleri geçerli dönem için tarihleri oluşturmak göstermeye Oluşturucusu.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

### <a name="representing-dates-in-calendars-with-eras"></a>Eras takvimlerle tarihleri temsil eden

Varsa bir <xref:System.Globalization.Calendar> nesne eras destekler ve geçerli takvimine durumda bir <xref:System.Globalization.CultureInfo> nesnesi, dönem tam tarihi ve saati, uzun tarih ve kısa tarih desenler için bir tarih ve saat değeri dize gösterimini yer almaktadır. Aşağıdaki örnekte, geçerli kültür Japonya (Japonca) ve geçerli takvim Japon takvimi olduğunda bu tarih desenleri görüntülenmektedir.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> <xref:System.Globalization.JapaneseCalendar> Birden fazla dönemi ve her iki destekler tarih geçerli takvimine olabilir .NET içinde yalnızca takvim sınıftır bir <xref:System.Globalization.CultureInfo> nesnesi - özellikle, bir <xref:System.Globalization.CultureInfo> Japonca (Japonya) kültür temsil eden nesne.

Tüm takvimler için, "g" özel biçim belirleyicisi, sonuç dizesinde dönemi içerir. Aşağıdaki örnekte, geçerli takvim Gregoryen takvim olduğunda dönemi sonuç dizesine eklemek için "AA-gg-yyyy g" özel biçimi kullanılmaktadır.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

Burada bir tarih dize gösterimini ifade edilir geçerli Takvim değil bir takvimindeki durumlarda <xref:System.Globalization.Calendar> sınıfı içerir bir <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> ile birlikte kullanılan yöntem <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, ve <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> yöntemleri belirsizliğe ait olduğu dönem yanı sıra bir tarih belirtin. Aşağıdaki örnek kullanır <xref:System.Globalization.JapaneseLunisolarCalendar> sınıfı bir çizim verilmektedir. Ancak, sonuç dizesinde dönemi, örneği gerektirir, anlamlı bir ad veya bir tamsayı yerine kısaltması dahil olmak üzere not bir <xref:System.Globalization.DateTimeFormatInfo> nesne ve olun <xref:System.Globalization.JapaneseCalendar> geçerli takvime. ( <xref:System.Globalization.JapaneseLunisolarCalendar> Takvim herhangi kültür geçerli Takvim olamaz, ancak bu durumda aynı eras iki takvimleri paylaşın.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

## <a name="see-also"></a>Ayrıca bkz.

[Nasıl yapılır: Miladi olmayan takvimlerde tarihleri görüntüleme](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
[örnek: Takvim hafta aralığını yardımcı programı](http://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
