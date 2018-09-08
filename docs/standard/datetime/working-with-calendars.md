---
title: Takvimlerle çalışma
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fca25786096ebeb97c133d306129f33f2bb4580
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44181056"
---
# <a name="working-with-calendars"></a>Takvimlerle çalışma

Tarih ve saat değeri zaman içinde bir anı gösterse de, dize gösterimi kültüre duyarlıdır ve hem belirli bir kültür saat tarafından saat ve tarih değerlerini görüntülemek için kullanılan kurallara, hem de kültür tarafından kullanılan takvime dayalıdır. Bu konuda, .NET takvimler için destek incelenmekte ve tarih değerleriyle çalışırken Takvim sınıflarının kullanılması açıklanmaktadır.

## <a name="calendars-in-net"></a>. NET'te takvimler

. NET'te tüm takvimleri türetilmesi <xref:System.Globalization.Calendar?displayProperty=nameWithType> temel takvim uygulamasını sağlayan sınıf. Devralan sınıflardan birini <xref:System.Globalization.Calendar> sınıfı <xref:System.Globalization.EastAsianLunisolarCalendar> tüm Ay Güneş takvimleri için temel sınıf olan sınıf. .NET aşağıdaki Takvim uygulamalarını içerir:

* <xref:System.Globalization.ChineseLunisolarCalendar>, Çince Ay Güneş takvimini temsil eder.

* <xref:System.Globalization.GregorianCalendar>, Gregoryen takvim temsil eder. Bu takvimi tarafından tanımlanan alt türlere (örneğin, Arapça ve Orta Doğu Fransızcası) daha fazla bölünmüştür <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> sabit listesi. <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> Özelliği Gregoryen takviminin alt türünü belirtir.

* <xref:System.Globalization.HebrewCalendar>, İbranice takvimi temsil eder.

* <xref:System.Globalization.HijriCalendar>, Hicri takvimi temsil eder.

* <xref:System.Globalization.JapaneseCalendar>, Japonca takvimi temsil eder.

* <xref:System.Globalization.JapaneseLunisolarCalendar>, Japonca Ay Güneş takvimini temsil eder.

* <xref:System.Globalization.JulianCalendar>, Jülyen takvimini temsil eder.

* <xref:System.Globalization.KoreanCalendar>, Korece takvimi temsil eder.

* <xref:System.Globalization.KoreanLunisolarCalendar>, Korece Ay Güneş takvimini temsil eder.

* <xref:System.Globalization.PersianCalendar>, Farsça takvimi temsil eder.

* <xref:System.Globalization.TaiwanCalendar>, Tayvan takvimini temsil eder.

* <xref:System.Globalization.TaiwanLunisolarCalendar>, Tayvan Ay Güneş takvimini temsil eder.

* <xref:System.Globalization.ThaiBuddhistCalendar>, içeren Thai Budist takvimi temsil eder.

* <xref:System.Globalization.UmAlQuraCalendar>, Ümmül kura takvimini temsil eder.

Bir takvim iki şekilde kullanılabilir:

* Belirli bir kültür tarafından kullanılan takvim olarak. Her <xref:System.Globalization.CultureInfo> nesne, nesnenin kullanmakta olduğu Takvim olan geçerli bir takvimi vardır. Tüm tarih ve saat değerlerinin dize gösterimleri, otomatik olarak geçerli kültürü ve onun geçerli takvimini yansıtır. Genellikle, geçerli takvim kültürün varsayılan takvimidir. <xref:System.Globalization.CultureInfo> nesneleri ayrıca, bu kültürün kullanabileceği ek takvimleri içeren isteğe bağlı takvimleri de vardır.

* Belirli bir takvimden bağımsız tek başına bir takvim olarak. Bu durumda, <xref:System.Globalization.Calendar> yöntemleri, tarihleri takvimi yansıtan değerler olarak ifade etmek için kullanılır.

Altı Takvim sınıflarının – Not <xref:System.Globalization.ChineseLunisolarCalendar>, <xref:System.Globalization.JapaneseLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar>, ve <xref:System.Globalization.TaiwanLunisolarCalendar> – yalnızca bağımsız takvimler olarak kullanılabilir. Herhangi bir kültür tarafından varsayılan takvim olarak veya isteğe bağlı bir takvim olarak kullanılmazlar.

## <a name="calendars-and-cultures"></a>Takvimler ve kültürler

Her bir kültür tarafından tanımlanan varsayılan bir takvimi vardır <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> özelliği. <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> Özelliği, bir dizi döndürür <xref:System.Globalization.Calendar> , kültürün varsayılan takvimi dahil olmak üzere belirli bir kültür tarafından desteklenen tüm takvimleri belirten nesneleri.

Aşağıdaki örnekte gösterilmiştir <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özellikleri. Oluşturur `CultureInfo` Tay (Tayland), Japonca (Japonya) kültürleri için nesneleri ve onların varsayılan ve isteğe bağlı takvimlerini görüntüler. Her iki durumda da kültürün varsayılan takvimini de eklendiğini unutmayın <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> koleksiyonu.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Şu anda kullanımda belirli bir takvim <xref:System.Globalization.CultureInfo> nesne kültürün tarafından tanımlanan <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> özelliği. Bir kültürün <xref:System.Globalization.DateTimeFormatInfo> nesnesi tarafından döndürülen <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği. Bir kültür oluşturulduğunda, varsayılan değerine değerini aynıdır <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> özelliği. Ancak, döndürdüğü dizide yer alan herhangi bir takvim kültürün geçerli takvimi değiştirebilirsiniz <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özelliği. Yer almayan bir takvime geçerli takvimi ayarlamaya çalışırsanız <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özellik değeri bir <xref:System.ArgumentException> oluşturulur.

Aşağıdaki örnekte, Arap (Suudi Arabistan) kültürü tarafından kullanılan takvim değiştirilmektedir. İlk örnekleyen bir <xref:System.DateTime> değer ve - Turkish (Turkey) Bu durumda, - geçerli kültürü ve (Bu, bu durumda, Gregoryen takvimi) geçerli kültürün takvimini kullanarak görüntüler. Ardından, geçerli kültürü Arapça (Suudi Arabistan) olacak şekilde değiştirir ve kendi varsayılan Ümmül Kura takvimini kullanarak tarihi görüntüler. Ardından `CalendarExists` Hicri takvimin Arapça (Suudi Arabistan) kültürü tarafından desteklenip desteklenmediğini belirlemek için yöntemi. Takvim desteklendiğinden, geçerli takvimi Hicri olacak şekilde değiştirir ve yine tarihi görüntüler. Her bir durumda, tarih geçerli kültürün geçerli takvimi kullanılarak görüntülenir.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Tarihler ve takvimler

Türünde bir parametre içeren oluşturucular dışında <xref:System.Globalization.Calendar> ve belirlenen bir takvimdeki değerleri yansıtacak şekilde bir tarihin (diğer bir deyişle, ay, gün ve yıl) öğelerinin her ikisi de <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerler her zaman Gregoryen takvimini temel. Bu, örneğin, anlamına <xref:System.DateTime.Year%2A?displayProperty=nameWithType> özelliği, Gregoryen takvimindeki yılı döndürür ve <xref:System.DateTime.Day%2A?displayProperty=nameWithType> özelliği, Gregoryen takvimindeki ayın gününü döndürür.

> [!IMPORTANT]
> Bir tarih değeri ile onun dize gösterimi arasında bir fark olduğunu unutmamak önemlidir. İlki Gregoryen takvime dayalıdır; ikincisi ise belirli bir kültürün geçerli takvimine dayalıdır.

Aşağıdaki örnekte arasındaki bu fark gösterilmektedir <xref:System.DateTime> özellikleri ve bunlara karşılık gelen <xref:System.Globalization.Calendar> yöntemleri. Örnekte, geçerli kültür Arapça (Mısır) ve geçerli Takvim Ümmül Kura'dır. A <xref:System.DateTime> değeri, 2011 yedinci ayının on beşinci gününe ayarlanır. Tarafından aynı değerler döndürüldüğünden, bunun bir Gregoryen tarihi olarak yorumlandığı <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> sabit kültürün kurallarını kullandığında yöntemi. Geçerli kültürün kuralları kullanılarak biçimlendirilen tarihin dize gösterimi, Ümmül Kura takvimindeki denk tarih olan 14/08/32'dir. Ardından, üyelerinin `DateTime` ve `Calendar` gün, ay ve yılını döndürmek için kullanılan <xref:System.DateTime> değeri. Her durumda, değerler tarafından döndürülen <xref:System.DateTime> üyeleri tarafından döndürülen ise Gregoryen takvimindeki değerleri yansıtacak <xref:System.Globalization.UmAlQuraCalendar> üyeleri yansıtırken ümmül kura takvimindeki değerleri yansıtır.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiating-dates-based-on-a-calendar"></a>Bir takvime dayalı olarak tarihleri örnekleme

Çünkü <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri Gregoryen takvimine dayalı, türünde bir parametre içeren fazla yüklenmiş bir oluşturucu çağırmanız gerekir <xref:System.Globalization.Calendar> gün, ay veya yıl değerlerini kullanmak istiyorsanız, bir tarih değeri örneklemek için bir farklı takvim. Belirli bir takvimin aşırı de çağırabilirsiniz <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> örneklemek için yöntemi bir <xref:System.DateTime> nesne belirli bir takvimin değerlerine dayalı.

Aşağıdaki örnek bir örneğini oluşturur. <xref:System.DateTime> geçirerek değeri bir <xref:System.Globalization.HebrewCalendar> nesnesini bir <xref:System.DateTime> oluşturucusu ve ikinci bir örneğini oluşturur <xref:System.DateTime> çağırarak değeri <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> yöntemi. İki değer İbranice özdeş değerlerle oluşturulduğundan takvim, çağrı <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> yöntemi gösterir, iki <xref:System.DateTime> değerler eşit.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>Tarihleri geçerli takvimde temsil eden

Tarih ve saat biçimlendirme yöntemleri, tarihleri dizelere dönüştürürken her zaman geçerli takvimi kullanır. Bu, yılın, ayın ve ayın gününün dize gösteriminin geçerli takvimi yansıttığı ve Gregoryen takvimini yansıtmasının gerekli olmadığı anlamına gelir.

Aşağıdaki örnek, geçerli takvimin bir tarihin dize gösterimini nasıl etkilediğini göstermektedir. Geçerli kültürü Çince (Geleneksel, Tayvan) olarak değiştirir ve bir tarih değerini örnekler. Ardından, geçerli takvimi ve tarihi görüntüler, geçerli takvim olarak değiştirir <xref:System.Globalization.TaiwanCalendar>ve geçerli takvimi ve tarihi bir kez daha görüntüler. Tarih ilk kez görüntülendiğinde, Gregoryen takvimdeki bir tarih olarak gösterilir. İkinci kez görüntülendiğinde, Tayvan takvimindeki bir tarih olarak gösterilir.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>Geçerli olmayan bir takvimde tarihleri gösterme

Belirli bir kültürün geçerli takvimi olmayan bir takvim kullanarak bir tarihi temsil etmek için söz konusu yöntemlerini aramalıdır <xref:System.Globalization.Calendar> nesne. Örneğin, <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, ve <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> yöntemleri yıl, ay ve gün belirli bir takvimi yansıtan değerlere dönüştürür.

> [!WARNING]
> Bazı takvimler herhangi kültürün isteğe bağlı takvimleri olmadığından, bu takvimlerde tarihleri göstermek, her zaman takvim yöntemlerini çağırmanızı gerektirir. Öğesinden türetilen tüm takvimler, böyle <xref:System.Globalization.EastAsianLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, ve <xref:System.Globalization.PersianCalendar> sınıfları.

Aşağıdaki örnekte bir <xref:System.Globalization.JulianCalendar> 9 Ocak 1905 şeklinde bir tarihi Jülyen takviminde örneklemek için nesne. Bu tarih varsayılan (Gregoryen) takvimi kullanılarak görüntülendiğinde, 22 Ocak 1905 olarak gösterilir. İçin ayrı ayrı yapılan çağrılar <xref:System.Globalization.JulianCalendar> tarihin Jülyen takviminde yöntemleri sağlar.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Takvimler ve tarih aralıkları

Bir takvim tarafından desteklenen en erken tarih, o takvimin belirtilir <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> özelliği. İçin <xref:System.Globalization.GregorianCalendar> tarih 1 Ocak 0001 C.E.'dir olduğunu sınıfı . NET'te diğer takvimlerin çoğu daha sonraki bir tarihi destekler. Bir takvim önündeki bir tarih ve saat değeriyle çalışmayı denemek takvimin desteklenen en erken tarih oluşturur bir <xref:System.ArgumentOutOfRangeException> özel durum.

Ancak, önemli bir istisna vardır. Varsayılan (örneklenmemiş) değeri bir <xref:System.DateTime> nesnesi ve bir <xref:System.DateTimeOffset> nesne eşittir <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> değeri. Bu tarih 1 Ocak 0001 C.E.'yi desteklemeyen bir takvimde biçimlendirmeye çalışırsanız ve bir Biçim belirleyicisi sağlamazsanız, biçimlendirme yöntemi, "G" (genel tarih/saat deseni) Biçim belirleyicisi yerine "s" (sıralanabilir tarih/saat deseni) Biçim belirleyicisi kullanır. Sonuç olarak, biçimlendirme işlemi oluşturmaz bir <xref:System.ArgumentOutOfRangeException> özel durum. Bunun yerine, desteklenmeyen tarihi döndürür. Bu değeri görüntüler aşağıdaki örnekte gösterilmiştir <xref:System.DateTime.MinValue?displayProperty=nameWithType> geçerli kültürü ayarlandığında Japonca takvimle Japonca (Japonya) ve Arapça (Mısır) Ümmül kura takvimiyle. Ayrıca geçerli kültürü İngilizce (ABD) ve aramalar için ayarlar <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> yöntemi her biriyle <xref:System.Globalization.CultureInfo> nesneleri. Her durumda, tarih sıralanabilir tarih/saat deseni kullanılarak görüntülenir.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>Dönemlerle çalışma

Takvimler genellikle tarihleri dönemlere ayırır. Ancak, <xref:System.Globalization.Calendar> .NET sınıflarda, bir takvim ve çoğu tarafından tanımlanan her dönemi desteklemez <xref:System.Globalization.Calendar> sınıfları yalnızca bir dönemi destekler. Yalnızca <xref:System.Globalization.JapaneseCalendar> ve <xref:System.Globalization.JapaneseLunisolarCalendar> sınıfları birden çok dönemi destekler.

### <a name="eras-and-era-names"></a>Dönemler ve dönem adları

. NET'te, belirli bir takvim uygulamasıyla desteklenen dönemleri gösteren tamsayılar ters sırada depolanır <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> dizisi. Geçerli dönem dizin ve içindir <xref:System.Globalization.Calendar> destekleyen birden çok dönemi, art arda gelen her dizin sınıfları önceki dönemi yansıtır. Statik <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> özelliği geçerli dönemin dizinini tanımlar <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> dizi; bir sabit değeri olan her zaman sıfır olan. Tek tek <xref:System.Globalization.Calendar> sınıfları da geçerli dönemin değerini döndüren statik alanlar içerir. Bunlar aşağıdaki tabloda listelenmiştir.

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

Belirli bir dönem numarasına karşılık gelen ad dönem numarası geçirilerek alınabilir <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> veya <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> yöntemi. Aşağıdaki örnek dönem desteğiyle ilgili bilgileri almak için bu yöntemler çağrılmaktadır <xref:System.Globalization.GregorianCalendar> sınıfı.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

Ek olarak, "g" özel tarih ve saat biçimi dizisi, bir tarih ve saatin dize gösteriminde bir takvimin dönem adını içerir. Daha fazla bilgi için [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Bir tarihi bir dönemle örnekleme

İki <xref:System.Globalization.Calendar> birden çok dönemi destekleyen sınıflar, belirli bir yıl, ay ve değer belirsiz olabilir örneğin, ayın günü tüm dört döneminin yılları oluşan bir tarihi <xref:System.Globalization.JapaneseCalendar> sahip 1 ile 15 arasında numaralandırılmıştır. Normalde, bir dönem belirtilmezse, tarih ve saat ve takvim yöntemleri değerlerin geçerli döneme ait olduğunu varsayar. Dönemi açıkça belirtmek için bir tarih örneklerken bir <xref:System.Globalization.Calendar> , birden çok dönemi destekleyen sınıfı çağırabilirsiniz <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> yöntemi. Bu yöntem, takvimin yılı, ayı, günü, saati, dakikası, saniyesi ve milisaniyesiyle birlikte bir dönemi açıkça belirtmenize olanak tanır.

Aşağıdaki örnekte <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> aynı tarihi, desteklediği her bir dönemde ikinci yılın ilk gününün ilk ay örneklemek için yöntemi <xref:System.Globalization.JapaneseCalendar> sınıfı. Ardından, tarihi hem Japonca hem de Gregoryen takvimlerinde görüntüler. Ayrıca bir <xref:System.DateTime> bir dönem belirtmeden tarih değerlerini oluşturma yöntemleri geçerli dönemde tarihler oluşturduğunu göstermek için oluşturucu.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

### <a name="representing-dates-in-calendars-with-eras"></a>Tarihleri takvimlerde dönemlerle gösterme

Varsa bir <xref:System.Globalization.Calendar> nesnesi dönemleri destekliyorsa ve geçerli takvimi ise bir <xref:System.Globalization.CultureInfo> nesnesi, dönem bir tarih ve saat değerinin dize gösterimine tam tarih ve saat, uzun tarih ve kısa tarih desenleri için dahil edilmiştir. Aşağıdaki örnekte, geçerli kültür Japonya (Japonca) ve geçerli takvim Japon takvimi olduğunda bu tarih desenleri görüntülenmektedir.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> <xref:System.Globalization.JapaneseCalendar> NET'te tarihleri destekleyen hem de birden çok dönemdeki geçerli takvimi olabilecek tek takvim sınıfı bir <xref:System.Globalization.CultureInfo> nesnesi - özel olarak bir <xref:System.Globalization.CultureInfo> Japonca (Japonya) kültürünü temsil eden nesne.

Tüm takvimler için, "g" özel biçim belirleyicisi, sonuç dizesinde dönemi içerir. Aşağıdaki örnekte, geçerli takvim Gregoryen takvim olduğunda dönemi sonuç dizesine eklemek için "AA-gg-yyyy g" özel biçimi kullanılmaktadır.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

Bir tarih dize gösterimini geçerli takvimi olmayan bir takvimde açıklanır olduğu durumlarda <xref:System.Globalization.Calendar> sınıfı içeren bir <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> ile birlikte kullanılan yöntemi <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, ve <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> yöntemleri kesin bir şekilde ait olduğu dönemi yanı sıra, bir tarih belirtin. Aşağıdaki örnekte <xref:System.Globalization.JapaneseLunisolarCalendar> bir gösterim sağlamak için sınıf. Ancak, sonuç dizesinde dönemi gerektirdiğini için bu anlamlı bir ad veya kısaltma bir tamsayı yerine dahil olmak üzere unutmayın bir <xref:System.Globalization.DateTimeFormatInfo> nesnesi örneklemenizi ve <xref:System.Globalization.JapaneseCalendar> onun geçerli takvimini. ( <xref:System.Globalization.JapaneseLunisolarCalendar> Takvim herhangi bir kültürün geçerli takvimi olamaz, ancak bu durumda iki Takvim aynı dönemi paylaşır.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

## <a name="see-also"></a>Ayrıca bkz.

* [Nasıl yapılır: Miladi olmayan takvimlerde tarihleri görüntüleme](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
* [Örnek: Takvim haftası yardımcı programı aralığı.](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
