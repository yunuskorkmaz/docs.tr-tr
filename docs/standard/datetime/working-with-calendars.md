---
title: Takvimlerle çalışma
ms.date: 04/01/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
ms.openlocfilehash: d15bafd097c72515a33bed7dd85d88aef54246ba
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280900"
---
# <a name="work-with-calendars"></a>Takvimlerle çalışma

Tarih ve saat değeri zaman içinde bir anı gösterse de, dize gösterimi kültüre duyarlıdır ve hem belirli bir kültür saat tarafından saat ve tarih değerlerini görüntülemek için kullanılan kurallara, hem de kültür tarafından kullanılan takvime dayalıdır. Bu konu, .NET 'teki takvimlere yönelik desteği araştırır ve tarih değerleriyle çalışırken takvim sınıflarının kullanımını açıklar.

## <a name="calendars-in-net"></a>.NET 'teki takvimler

.NET 'teki tüm takvimler <xref:System.Globalization.Calendar?displayProperty=nameWithType> , temel takvim uygulamasını sağlayan sınıfından türetilir. Sınıfından devralan sınıflardan biri <xref:System.Globalization.Calendar> <xref:System.Globalization.EastAsianLunisolarCalendar> , tüm lunizki takvimlerinin temel sınıfı olan sınıftır. .NET aşağıdaki takvim uygulamalarını içerir:

- <xref:System.Globalization.ChineseLunisolarCalendar>, Çince lunizki takvimini temsil eder.

- <xref:System.Globalization.GregorianCalendar>, Gregoryen takvimini temsil eder. Bu takvim, sabit listesi tarafından tanımlanan alt türler (Arapça ve Orta Doğu Fransızca gibi) içine bölünür <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> . <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType>Özelliği, Gregoryen takvimin alt türünü belirtir.

- <xref:System.Globalization.HebrewCalendar>Ibranice takvimini temsil eder.

- <xref:System.Globalization.HijriCalendar>Hicri takvimi temsil eder.

- <xref:System.Globalization.JapaneseCalendar>Japonca takvimi temsil eder.

- <xref:System.Globalization.JapaneseLunisolarCalendar>, Japonca ay Güneş takvimini temsil eder.

- <xref:System.Globalization.JulianCalendar>, Jülyen takvimini temsil eder.

- <xref:System.Globalization.KoreanCalendar>Korece takvimini temsil eder.

- <xref:System.Globalization.KoreanLunisolarCalendar>, Kore ay Güneş takvimini temsil eder.

- <xref:System.Globalization.PersianCalendar>, Farsça takvimini temsil eder.

- <xref:System.Globalization.TaiwanCalendar>, Tayvan takvimini temsil eder.

- <xref:System.Globalization.TaiwanLunisolarCalendar>, Tayvan ay Güneş takvimini temsil eder.

- <xref:System.Globalization.ThaiBuddhistCalendar>, Tay Budist takvimini temsil eder.

- <xref:System.Globalization.UmAlQuraCalendar>Bu, um Al Qura takvimini temsil eder.

Bir takvim iki şekilde kullanılabilir:

- Belirli bir kültür tarafından kullanılan takvim olarak. Her <xref:System.Globalization.CultureInfo> nesne, nesnenin şu anda kullandığı takvim olan geçerli bir takvime sahiptir. Tüm tarih ve saat değerlerinin dize gösterimleri, otomatik olarak geçerli kültürü ve onun geçerli takvimini yansıtır. Genellikle, geçerli takvim kültürün varsayılan takvimidir. <xref:System.Globalization.CultureInfo>nesneler Ayrıca, kültürün kullanabileceği ek takvimler dahil olmak üzere isteğe bağlı takvimlere sahiptir.

- Belirli bir takvimden bağımsız tek başına bir takvim olarak. Bu durumda, <xref:System.Globalization.Calendar> tarihleri takvimi yansıtan değerler olarak ifade etmek için yöntemler kullanılır.

- <xref:System.Globalization.ChineseLunisolarCalendar> , <xref:System.Globalization.JapaneseLunisolarCalendar> , <xref:System.Globalization.JulianCalendar> , <xref:System.Globalization.KoreanLunisolarCalendar> , Ve – altı takvim sınıfının <xref:System.Globalization.PersianCalendar> <xref:System.Globalization.TaiwanLunisolarCalendar> yalnızca tek başına takvimler olarak kullanılabileceğini unutmayın. Herhangi bir kültür tarafından varsayılan takvim olarak veya isteğe bağlı bir takvim olarak kullanılmazlar.

## <a name="calendars-and-cultures"></a>Takvimler ve kültürler

Her kültürün, özelliği tarafından tanımlanan varsayılan bir takvimi vardır <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> . <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>Özelliği <xref:System.Globalization.Calendar> , söz konusu kültürün varsayılan takvimi de dahil olmak üzere belirli bir kültür tarafından desteklenen tüm takvimleri belirten nesne dizisini döndürür.

Aşağıdaki örnek, <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> ve özelliklerini gösterir <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> . `CultureInfo`Tay dili (Tayland) ve Japonca (Japonya) kültürleri için nesneler oluşturur ve bunların varsayılan ve isteğe bağlı takvimlerini görüntüler. Her iki durumda da, kültürün varsayılan takviminin koleksiyona dahil edildiğini unutmayın <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> .

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Belirli bir nesne tarafından kullanılmakta olan takvim, <xref:System.Globalization.CultureInfo> kültürün özelliği tarafından tanımlanır <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> . Bir kültürün <xref:System.Globalization.DateTimeFormatInfo> nesnesi, özelliği tarafından döndürülür <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> . Bir kültür oluşturulduğunda, varsayılan değeri özelliğin değeriyle aynıdır <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> . Ancak, kültürün geçerli takvimini özelliği tarafından döndürülen dizide yer alan herhangi bir takvimle değiştirebilirsiniz <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> . Geçerli takvimi özellik değerine dahil olmayan bir takvime ayarlamaya çalışırsanız <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> , bir oluşturulur <xref:System.ArgumentException> .

Aşağıdaki örnekte, Arap (Suudi Arabistan) kültürü tarafından kullanılan takvim değiştirilmektedir. İlk olarak bir <xref:System.DateTime> değer oluşturur ve geçerli kültürü kullanarak görüntüler; bu durumda İngilizce (Birleşik Devletler) ve geçerli kültürün takvimi (Bu durumda, Gregoryen takvimidir). Ardından, geçerli kültürü Arapça (Suudi Arabistan) olacak şekilde değiştirir ve kendi varsayılan Ümmül Kura takvimini kullanarak tarihi görüntüler. Daha sonra `CalendarExists` Hicri takvimin Arapça (Suudi Arabistan) kültürü tarafından desteklenip desteklenmediğini anlamak için yöntemini çağırır. Takvim desteklendiğinden, geçerli takvimi Hicri olacak şekilde değiştirir ve yine tarihi görüntüler. Her bir durumda, tarih geçerli kültürün geçerli takvimi kullanılarak görüntülenir.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Tarihler ve takvimler

Türünde bir parametre içeren <xref:System.Globalization.Calendar> ve bir tarih (yani, ay, gün ve yıl) öğelerinin belirtilen takvimdeki değerleri yansıtması için, her ikisi <xref:System.DateTime> ve <xref:System.DateTimeOffset> değer her zaman Gregoryen takvime dayalıdır. Bu, örneğin, <xref:System.DateTime.Year%2A?displayProperty=nameWithType> özelliğinin Gregoryen takvimdeki yılı döndürdüğü, <xref:System.DateTime.Day%2A?displayProperty=nameWithType> özelliğin ise Gregoryen takvimdeki ayın gününü döndürdüğü anlamına gelir.

> [!IMPORTANT]
> Bir tarih değeri ile onun dize gösterimi arasında bir fark olduğunu unutmamak önemlidir. İlki Gregoryen takvime dayalıdır; ikincisi ise belirli bir kültürün geçerli takvimine dayalıdır.

Aşağıdaki örnek, <xref:System.DateTime> özellikleri ve bunlara karşılık gelen yöntemleri arasındaki bu farkı gösterir <xref:System.Globalization.Calendar> . Örnekte, geçerli kültür Arapça (Mısır) ve geçerli Takvim Ümmül Kura'dır. <xref:System.DateTime>Değer, 2011 değerinin yedinci ayının on beşinci gününe ayarlanır. Aynı değerler, <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> sabit kültürün kurallarını kullandığında yöntemi tarafından döndürüldüğünden, bu, Gregoryen bir tarih olarak yorumlanır. Geçerli kültürün kuralları kullanılarak biçimlendirilen tarihin dize gösterimi, Ümmül Kura takvimindeki denk tarih olan 14/08/32'dir. Sonra, ve üyeleri `DateTime` , `Calendar` değerinin gün, ay ve yılını döndürmek için kullanılır <xref:System.DateTime> . Her durumda, Üyeler tarafından döndürülen değerler <xref:System.DateTime> Gregoryen takvimdeki değerleri yansıtır, ancak Üyeler tarafından döndürülen değerler <xref:System.Globalization.UmAlQuraCalendar> uum Al-Qura takvimindeki değerleri yansıtır.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiate-dates-based-on-a-calendar"></a>Takvime göre tarihleri oluşturma

<xref:System.DateTime>Ve <xref:System.DateTimeOffset> değerleri Gregoryen takvimini temel alıyorsa, <xref:System.Globalization.Calendar> farklı bir takvimden gün, ay veya yıl değerlerini kullanmak istiyorsanız bir tarih değeri örneği oluşturmak için türünde bir parametre içeren aşırı yüklenmiş bir Oluşturucu çağırmanız gerekir. Belirli bir <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> takvimin değerlerine göre bir nesne örneği oluşturmak için belirli bir takvimin aşırı yüklerinden birini de çağırabilirsiniz <xref:System.DateTime> .

Aşağıdaki örnek bir değeri bir <xref:System.DateTime> oluşturucuya geçirerek bir değer örnekleyerek <xref:System.Globalization.HebrewCalendar> <xref:System.DateTime> <xref:System.DateTime> yöntemi çağırarak ikinci bir değer oluşturur <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> . İki değer Ibranice takvimdeki özdeş değerlerle oluşturulduğundan, yöntemine yapılan çağrı <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> iki <xref:System.DateTime> değerin eşit olduğunu gösterir.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="represent-dates-in-the-current-calendar"></a>Geçerli takvimdeki tarihleri temsil etme

Tarih ve saat biçimlendirme yöntemleri, tarihleri dizelere dönüştürürken her zaman geçerli takvimi kullanır. Bu, yılın, ayın ve ayın gününün dize gösteriminin geçerli takvimi yansıttığı ve Gregoryen takvimini yansıtmasının gerekli olmadığı anlamına gelir.

Aşağıdaki örnek, geçerli takvimin bir tarihin dize gösterimini nasıl etkilediğini göstermektedir. Geçerli kültürü Çince (Geleneksel, Tayvan) olarak değiştirir ve bir tarih değerini örnekler. Ardından geçerli takvimi ve tarihi görüntüler, geçerli takvimi olarak değiştirir <xref:System.Globalization.TaiwanCalendar> ve geçerli takvimi ve tarihi bir kez daha görüntüler. Tarih ilk kez görüntülendiğinde, Gregoryen takvimdeki bir tarih olarak gösterilir. İkinci kez görüntülendiğinde, Tayvan takvimindeki bir tarih olarak gösterilir.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="represent-dates-in-a-non-current-calendar"></a>Geçerli olmayan bir takvimdeki tarihleri temsil etme

Belirli bir kültürün geçerli takvimi olmayan bir takvimi kullanarak bir tarihi temsil etmek için, bu nesnenin yöntemlerini çağırmanız gerekir <xref:System.Globalization.Calendar> . Örneğin,, <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType> <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> ve <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> yöntemleri yılı, ayı ve günü belirli bir takvimi yansıtan değerlere dönüştürür.

> [!WARNING]
> Bazı takvimler herhangi kültürün isteğe bağlı takvimleri olmadığından, bu takvimlerde tarihleri göstermek, her zaman takvim yöntemlerini çağırmanızı gerektirir. Bu,, ve sınıflarından türetilen tüm takvimlerde geçerlidir <xref:System.Globalization.EastAsianLunisolarCalendar> <xref:System.Globalization.JulianCalendar> <xref:System.Globalization.PersianCalendar> .

Aşağıdaki örnek, <xref:System.Globalization.JulianCalendar> Jülyen takviminde 9 ocak 1905 tarihi bir tarih örneğini oluşturmak için bir nesnesi kullanır. Bu tarih varsayılan (Gregoryen) takvimi kullanılarak görüntülendiğinde, 22 Ocak 1905 olarak gösterilir. Bağımsız yöntemlere yapılan çağrılar <xref:System.Globalization.JulianCalendar> , tarihin Jülyen takviminde gösterilmesine olanak sağlar.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Takvimler ve tarih aralıkları

Takvimin desteklediği en erken tarih, bu takvimin özelliği tarafından belirtilir <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> . Sınıf için <xref:System.Globalization.GregorianCalendar> Bu tarih 1 Ocak 0001 C.E. .NET 'teki diğer takvimlerin çoğu daha sonraki bir tarihi destekler. Takvimin en erken desteklenen tarihinden önce gelen Tarih ve saat değeriyle çalışmaya çalışılması bir <xref:System.ArgumentOutOfRangeException> özel durum oluşturur.

Ancak, önemli bir istisna vardır. Bir nesnenin varsayılan (başlatılmamış) değeri <xref:System.DateTime> ve bir <xref:System.DateTimeOffset> nesnesi <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> değerine eşittir. Bu tarihi 1 Ocak 0001 desteklemeyen bir takvimde biçimlendirmeye çalışırsanız C.E. ve bir Biçim belirleyicisi sağlamazsanız, biçimlendirme yöntemi "G" (genel tarih/saat deseninin) Biçim belirleyicisi yerine "s" (sıralanabilir tarih/saat deseninin) biçim belirticisini kullanır. Sonuç olarak biçimlendirme işlemi bir <xref:System.ArgumentOutOfRangeException> özel durum oluşturmaz. Bunun yerine, desteklenmeyen tarihi döndürür. Bu, <xref:System.DateTime.MinValue?displayProperty=nameWithType> geçerli kültürün Japonca (Japonya), Japonca takvim ve um Al Qura takvimi Ile Arapça (Mısır) olarak ayarlandığı zaman değerini gösteren aşağıdaki örnekte gösterilmiştir. Ayrıca, geçerli kültürü Ingilizce (Birleşik Devletler) olarak ayarlar ve <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> Bu nesnelerin her biri ile yöntemi çağırır <xref:System.Globalization.CultureInfo> . Her durumda, tarih sıralanabilir tarih/saat deseni kullanılarak görüntülenir.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="work-with-eras"></a>Dönemi ile çalışma

Takvimler genellikle tarihleri dönemlere ayırır. Ancak, <xref:System.Globalization.Calendar> .NET içindeki sınıflar bir takvim tarafından tanımlanan her dönemi desteklemez ve <xref:System.Globalization.Calendar> sınıfların çoğu yalnızca tek bir dönemi destekler. Yalnızca <xref:System.Globalization.JapaneseCalendar> ve <xref:System.Globalization.JapaneseLunisolarCalendar> sınıfları birden çok eras destekler.

> [!IMPORTANT]
> Ve ' de yeni bir dönem olan Reiwa dönemi <xref:System.Globalization.JapaneseCalendar> , <xref:System.Globalization.JapaneseLunisolarCalendar> 1 Mayıs 2019 ' de başlar. Bu değişiklik, bu takvimleri kullanan tüm uygulamaları etkiler. Daha fazla bilgi için aşağıdaki makalelere bakın:
>
> - .Net [' te Japonca takvimdeki yeni bir dönemi işleme](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/), .net ' e eklenen ve çoklu dönem takvimlerini işlerken en iyi yöntemleri açıklayan özellikleri anlatmaktadır.
> - Uygulamanızı Windows üzerinde test etme hakkında bilgi sağlayan [Japonca dönem değişikliği için uygulamayı hazırlayın](/windows/uwp/design/globalizing/japanese-era-change)ve bu sayede, dönem değişikliğine yönelik hazırlık olanağı sağlanır.
> - Yeni Japonca [.NET Framework için yeni Japonca dönem güncelleştirmeleri](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework), yeni Japonca takvim dönemi ile ilgili .NET Framework güncelleştirmeleri listeleyen, çok satırlı destek için yeni .NET Framework özelliklerine Not veren ve uygulamalarınızın test edilmesine yönelik arama işlemleri içeren.

Birçok takvim içindeki bir dönem, son derece uzun bir süre gösterir. Gregoryen takviminde, örneğin, geçerli dönem iki Millennia fazlasına yaymıştır. Ve için <xref:System.Globalization.JapaneseCalendar> <xref:System.Globalization.JapaneseLunisolarCalendar> birden çok eras destekleyen iki takvim için bu durum değildir. Bir dönem, Emperor 'ın Reign 'ın dönemine karşılık gelir. Birden çok eras desteği, özellikle geçerli dönem üst sınırı bilinmiyorsa, özel güçlükler doğurur.

### <a name="eras-and-era-names"></a>Eras ve dönem adları

.Net ' te, belirli bir Takvim uygulamasının desteklediği dönemi 'i temsil eden tamsayılar dizide ters sırada depolanır <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> . Geçerli dönem (en son zaman aralığına sahip olan dönem) dizin sıfırdır ve <xref:System.Globalization.Calendar> birden çok eras destekleyen sınıflar için, birbirini izleyen her dizin önceki dönemi yansıtır. Static <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> özelliği dizideki geçerli dönem dizinini tanımlar <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> ; değeri her zaman sıfır olan bir sabittir. Tek <xref:System.Globalization.Calendar> sınıflar, geçerli dönem değerini döndüren statik alanlar da içerir. Bunlar aşağıdaki tabloda listelenmiştir.

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

Belirli bir dönem numarasına karşılık gelen ad, dönem numarası veya yöntemine geçirilerek alınabilir <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> . Aşağıdaki örnek, sınıfındaki dönem desteği hakkında bilgi almak için bu yöntemleri çağırır <xref:System.Globalization.GregorianCalendar> . Geçerli çağın ikinci yılının 1 Ocak ayına karşılık gelen Gregoryen takvim tarihini ve desteklenen her Japonca takvim dönemi 'nin ikinci yılının 1 Ocak ayına karşılık gelen Gregoryen takvim tarihini görüntüler.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

Ek olarak, "g" özel tarih ve saat biçimi dizisi, bir tarih ve saatin dize gösteriminde bir takvimin dönem adını içerir. Daha fazla bilgi için bkz. [özel tarih ve saat biçim dizeleri](../base-types/custom-date-and-time-format-strings.md).

### <a name="instantiatie-a-date-with-an-era"></a>Dönem ile Instantiatie bir tarih

<xref:System.Globalization.Calendar>Birden çok eras destekleyen iki sınıf için, ay değerinin belirli bir yılı, ayı ve gününü içeren bir tarih belirsiz olabilir. Örneğin, tarafından desteklenen tüm dönemi <xref:System.Globalization.JapaneseCalendar> sayıları 1 olan yıllar vardır. Normalde, bir dönem belirtilmezse, tarih ve saat ve takvim yöntemleri değerlerin geçerli döneme ait olduğunu varsayar. Bu, <xref:System.DateTime.%23ctor%2A> <xref:System.DateTimeOffset.%23ctor%2A> türü parametreleri ve <xref:System.Globalization.Calendar> [JapaneseCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) ve [JapaneseLunisolarCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) yöntemlerini içeren oluşturucuların ve oluşturucularının her biri için geçerlidir. Aşağıdaki örnek, belirtilmeyen bir dönem için ikinci yılın 1 Ocak ayını temsil eden bir tarihi örnekleyen bir tarih oluşturur. Reiwa dönemi geçerli dönem olduğunda örneği çalıştırırsanız, tarih Reiwa dönemi ikinci yılı olarak yorumlanır. 令和, yöntemi tarafından döndürülen dizedeki yıldan önce gelir <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> ve Gregoryen takviminde 1 ocak 2020 ' e karşılık gelir. (Reiwa dönemi, Gregoryen takvimdeki 2019 yılında başlar.)

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Ancak, dönem değişirse, bu kodun amacı belirsiz hale gelir. Geçerli çağın ikinci yılını temsil etmek mi yoksa Heiseı dönemi 'nin ikinci yılını temsil etmek mi amaçlanıyor? Bu belirsizliği önlemenin iki yolu vardır:

- Varsayılan sınıfı kullanarak tarih ve saat değerini örnekleyin <xref:System.Globalization.GregorianCalendar> . Daha sonra, aşağıdaki örnekte gösterildiği gibi, tarihlerin dize temsili için Japonca takvim veya Japonca Lunizde takvimini kullanabilirsiniz.

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Açık olarak bir dönem belirten tarih ve saat yöntemini çağırın. Bu, aşağıdaki yöntemleri içerir:

  - <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> <xref:System.Globalization.JapaneseCalendar> Veya <xref:System.Globalization.JapaneseLunisolarCalendar> sınıfının yöntemi.

  - <xref:System.DateTime> <xref:System.DateTimeOffset> <xref:System.DateTime.Parse%2A> <xref:System.DateTime.TryParse%2A> <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A> Ayrıştırılacak dizeyi ve isteğe bağlı olarak <xref:System.Globalization.DateTimeStyles> Japonca-Japonya ("ja-JP") ve bu kültürün takvimini içeren bir bağımsız değişkeni içeren,, veya gibi bir veya ayrıştırma yöntemi <xref:System.Globalization.JapaneseCalendar> . Ayrıştırılacak dize, dönem içermelidir.

  - Türünde bir parametre içeren bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> ayrıştırma yöntemi `provider` <xref:System.IFormatProvider> . `provider`<xref:System.Globalization.CultureInfo>geçerli takvimi <xref:System.Globalization.JapaneseCalendar> ya da özelliği olan bir nesne olan Japonca-Japonya ("ja-JP") kültürünü temsil eden bir nesne olmalıdır <xref:System.Globalization.DateTimeFormatInfo> <xref:System.Globalization.DateTimeFormatInfo.Calendar> <xref:System.Globalization.JapaneseCalendar> . Ayrıştırılacak dize, dönem içermelidir.

  Aşağıdaki örnek, 8 Eylül 1868 ' de başlayan ve 29 Temmuz 1912 tarihinde sona eriji dönemi içinde bir tarih ve saat örneği oluşturmak için bu yöntemlerin üçünü kullanır.

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Birden çok eras destekleyen takvimler ile çalışırken, bir tarih başlatmak için *her zaman* Gregoryen tarihini kullanın veya bu takvime göre bir tarih ve saat örneği oluşturduğunuzda dönemi belirtin.

Yöntemine bir dönem belirtirken, bu <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> Dönem dizinini takvimin <xref:System.Globalization.Calendar.Eras> özelliğinde sağlarsınız. Ancak, dönemi değişikliğine tabi olan takvimler için, bu dizinler sabit değerler değildir; geçerli dönem indeks 0 ' dır ve en eski dönem dizinydi `Eras.Length - 1` . Bir takvime yeni bir dönem eklendiğinde, önceki Erin dizinleri bir ile artar. Uygun dönem dizinini aşağıdaki şekilde sağlayabilirsiniz:

- Geçerli dönem içindeki tarihler için, her zaman takvimin <xref:System.Globalization.Calendar.CurrentEra> özelliğini kullanın.

- Belirli bir dönem içindeki tarihler için, <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> belirtilen dönem adına karşılık gelen dizini almak için yöntemini kullanın. Bunun için <xref:System.Globalization.JapaneseCalendar> <xref:System.Globalization.CultureInfo> ja-JP kültürünü temsil eden nesnenin geçerli takvimi olması gerekir.  (Bu teknik, ile aynı şekilde çalıştığı için <xref:System.Globalization.JapaneseLunisolarCalendar> aynı zamanda için de geçerlidir <xref:System.Globalization.JapaneseCalendar> .) Önceki örnekte bu yaklaşım gösterilmektedir.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Takvimler, eras ve tarih aralıkları: gevşek Aralık denetimleri

Tek bir takvimle benzer bir şekilde, ve sınıflarının içindeki dönemi desteklenen <xref:System.Globalization.JapaneseCalendar> <xref:System.Globalization.JapaneseLunisolarCalendar> aralıklar da vardır. Daha önce, .NET tarafından kullanılan katı dönem aralığı, dönem içinde belirli bir tarihin o dönem içinde olduğundan emin olmak için kontrol eder. Diğer bir deyişle, bir tarih belirtilen dönem aralığının dışındaysa, yöntemi bir oluşturur <xref:System.ArgumentOutOfRangeException> . Şu anda .NET varsayılan olarak gevşek aralıklı denetim kullanır. Tüm .NET sürümlerine yönelik güncelleştirmeler, gevşek dönem aralığı denetimlerini sunmuştur; Belirtilen dönem dışında bir dönem belirli bir tarih örneği oluşturma denemesi, aşağıdaki dönem içinde "taşmalar" ve hiçbir özel durum oluşturulmaz.

Aşağıdaki örnek, 25 Aralık 1926 ' de başlayan ve 7 Ocak 1989 tarihinde sona erildiği Showa Dönemi 'nin 65. yılında bir tarih örneğini oluşturmaya çalışır. Bu tarih, içindeki Showa Dönemi dışında 9 Ocak 1990 ' e karşılık gelir <xref:System.Globalization.JapaneseCalendar> . Örneğin çıktısında gösterildiği gibi, örnek tarafından görünen tarih, Heiseı dönemi 'nin ikinci yılında 9 Ocak 1990 ' dir.

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

Gevşek Aralık denetimleri istenmeyen ise, uygulamanızın çalıştırıldığı .NET sürümüne bağlı olarak katı Aralık denetimlerini bir dizi şekilde geri yükleyebilirsiniz:

- **.NET Core:** Aşağıdakini *. netcore. Runtime. JSON* yapılandırma dosyasına ekleyin:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **.NET Framework 4,6 veya üzeri:** *App. config* dosyasında aşağıdaki AppContext anahtarını ayarlayın:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 veya önceki sürümler:** Aşağıdaki kayıt defteri değerini ayarlayın:

   |  |  |
   |--|--|
   | **Anahtar** | **HKEY_LOCAL_MACHINE \Software\Microsoft \\ . NETFramework\AppContext** |
   | **Adı** | Switch. System. Globalization. EnforceJapaneseEraYearRanges |
   | **Tür** | REG_SZ |
   | **Değer** | true |

Katı Aralık denetimleri etkinken, önceki örnek bir oluşturur <xref:System.ArgumentOutOfRangeException> ve aşağıdaki çıktıyı görüntüler:

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="represent-dates-in-calendars-with-multiple-eras"></a>Birden çok dönemi ile takvimlerdeki tarihleri temsil etme

Bir <xref:System.Globalization.Calendar> nesne dönemi 'yi destekliyorsa ve bir nesnenin geçerli takvimiyse <xref:System.Globalization.CultureInfo> , dönem tam tarih ve saat, uzun tarih ve kısa tarih desenleri için bir tarih ve saat değerinin dize gösterimine dahil edilir. Aşağıdaki örnekte, geçerli kültür Japonya (Japonca) ve geçerli takvim Japon takvimi olduğunda bu tarih desenleri görüntülenmektedir.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> <xref:System.Globalization.JapaneseCalendar>Sınıfı, .net 'teki tek bir dönem içindeki tarihleri destekleyen ve tek bir nesnenin geçerli takvimi olabilecek <xref:System.Globalization.CultureInfo> , ancak <xref:System.Globalization.CultureInfo> Japonca (Japonya) kültürünü temsil eden bir nesne olan tek takvim sınıfıdır.

Tüm takvimler için, "g" özel biçim belirleyicisi, sonuç dizesinde dönemi içerir. Aşağıdaki örnekte, geçerli takvim Gregoryen takvim olduğunda dönemi sonuç dizesine eklemek için "AA-gg-yyyy g" özel biçimi kullanılmaktadır.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

Bir tarihin dize gösteriminin geçerli takvim olmayan bir takvimde ifade edildiği durumlarda, <xref:System.Globalization.Calendar> sınıfı <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> ,, <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType> <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> ve bir tarihi ve ait olduğu dönemi kesin olarak belirtmek için, ve yöntemleriyle birlikte kullanılabilecek bir yöntemi içerir <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> . Aşağıdaki örnek, <xref:System.Globalization.JapaneseLunisolarCalendar> bir çizim sağlamak için sınıfını kullanır. Ancak, sonuç dizesinde dönem için tamsayı yerine anlamlı bir ad veya kısaltma dahil edilmesi, bir nesne örneği oluşturmak <xref:System.Globalization.DateTimeFormatInfo> ve <xref:System.Globalization.JapaneseCalendar> geçerli takvimini yapmanız gerekir. ( <xref:System.Globalization.JapaneseLunisolarCalendar> Takvim herhangi bir kültürün geçerli takvimi olamaz, ancak bu durumda iki takvim aynı eras 'yi paylaşır.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

Japonca takvimlerinde, bir dönem ilk yılı gannen (元年) olarak adlandırılır. Örneğin Heisei 1 yerine HeII dönemi 'nin ilk yılı Heiseı gannen olarak açıklanabilir. .NET, şu standart veya özel tarih ve saat biçim dizeleri ile biçimlendirilen tarih ve saatler için biçimlendirme işlemlerinde bu kuralı <xref:System.Globalization.CultureInfo> , Japonca-Japonya ("ja-JP") kültürüne sahip kültür temsil eden bir nesneyle birlikte kullanıldığında kullanır <xref:System.Globalization.JapaneseCalendar> :

- "D" standart tarih ve saat biçimi dizesi tarafından belirtilen [uzun tarih deseninin](../base-types/standard-date-and-time-format-strings.md#LongDate).
- "F" standart tarih ve saat biçimi dizesi tarafından belirtilen [tam tarih uzun saat deseninin](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime).
- "F" standart tarih ve saat biçimi dizesi tarafından belirtilen [tam tarih kısa saat deseninin](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime).
- Y "veya" y "standart tarih ve saat biçimi dizesi tarafından belirtilen [yıl/ay deseninin](../base-types/standard-date-and-time-format-strings.md#YearMonth).
- ["Ggy ' 年 '" veya "ggy年" [özel tarih ve saat biçimi dizesi](../base-types/custom-date-and-time-format-strings.md).

Örneğin, aşağıdaki örnek, içindeki Heiseı dönemi 'nin ilk yılında bir tarih görüntüler <xref:System.Globalization.JapaneseCalendar> .

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Bu davranış biçimlendirme işlemlerinde istenmese, .NET sürümüne bağlı olarak aşağıdakileri yaparak her zaman bir çağın ilk yılını "gannen" yerine "1" olarak temsil eden önceki davranışı geri yükleyebilirsiniz:

- **.NET Core:** Aşağıdakini *. netcore. Runtime. JSON* yapılandırma dosyasına ekleyin:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **.NET Framework 4,6 veya üzeri:** *App. config* dosyasında aşağıdaki AppContext anahtarını ayarlayın:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 veya önceki sürümler:** Aşağıdaki kayıt defteri değerini ayarlayın:

   |  |  |
   |--|--|
   | **Anahtar** | **HKEY_LOCAL_MACHINE \Software\Microsoft \\ . NETFramework\AppContext** |
   | **Adı** | Switch. System. Globalization. FormatJapaneseFirstYearAsANumber |
   | **Tür** | REG_SZ |
   | **Değer** | true |

Biçimlendirme işlemlerinde gannen desteği devre dışı bırakıldığında, önceki örnek aşağıdaki çıktıyı görüntüler:

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

.NET ayrıca tarih ve saat ayrıştırma işlemlerinin, "1" veya gannen olarak gösterilen yılı içeren dizeleri desteklemesi için güncelleştirilmiştir. Bunu yapmanız gerekmese de, önceki davranışı bir dönem ilk yılı olarak yalnızca "1" tanıyacak şekilde geri yükleyebilirsiniz. Bunu, .NET sürümüne bağlı olarak aşağıdaki şekilde yapabilirsiniz:

- **.NET Core:** Aşağıdakini *. netcore. Runtime. JSON* yapılandırma dosyasına ekleyin:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **.NET Framework 4,6 veya üzeri:** *App. config* dosyasında aşağıdaki AppContext anahtarını ayarlayın:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 veya önceki sürümler:** Aşağıdaki kayıt defteri değerini ayarlayın:

   |  |  |
   |--|--|
   | **Anahtar** | **HKEY_LOCAL_MACHINE \Software\Microsoft \\ . NETFramework\AppContext** |
   | **Adı** | Switch. System. Globalization. EnforceLegacyJapaneseDateParsing |
   | **Tür** | REG_SZ |
   | **Değer** | true |

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Gregoryen olmayan takvimlerde tarihleri görüntüleme](../base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Örnek: Takvim haftası Aralık yardımcı programı](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Takvim sınıfı](xref:System.Globalization.Calendar)
