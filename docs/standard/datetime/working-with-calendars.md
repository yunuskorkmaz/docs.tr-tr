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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b683784489cd68b66b4f9660f0df5e63b676a91c
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921357"
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

* Belirli bir kültür tarafından kullanılan takvim olarak. Her <xref:System.Globalization.CultureInfo> nesne, nesnenin kullanmakta olduğu Takvim olan geçerli bir takvimi vardır. Tüm tarih ve saat değerlerinin dize gösterimleri, otomatik olarak geçerli kültürü ve onun geçerli takvimini yansıtır. Genellikle, geçerli takvim kültürün varsayılan takvimidir. <xref:System.Globalization.CultureInfo> nesnelerin kültürün kullanabileceği ek takvimleri içeren isteğe bağlı takvimleri de vardır.

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

> [!IMPORTANT]
>  Reiwa dönemi, yeni bir dönemde <xref:System.Globalization.JapaneseCalendar> ve <xref:System.Globalization.JapaneseLunisolarCalendar>, 1 Mayıs 2019 üzerinde başlar. Bu değişiklik bu takvimler kullanan tüm uygulamaları etkiler. Daha fazla bilgi için aşağıdaki makalelere bakın:
> - [. NET'te Japonca takvimde yeni bir dönemi işleme](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/), hangi desteklemek için. NET'e eklenen özellikler belgeleri ile birden çok dönemi takvimler ve birden çok dönemi takvimler işlerken kullanılacak en iyi uygulamalar ele alınmaktadır.
> - [Uygulamanız için Japonca era değişikliği hazırlama](/windows/uwp/design/globalizing/japanese-era-change), dönem değiştirmek için kendi hazırlık emin olmak için Windows üzerinde uygulamalarınızı test etme hakkında bilgi sağlar.
> - [Yeni Japonca dönemi özeti için .NET Framework güncelleştirmeleri](https://support.microsoft.com/en-us/help/4477957/new-japanese-era-updates-for-net-framework), yeni Japonca takvimi dönemi ilgili ayrı Windows sürümleri için .NET Framework güncelleştirmeleri listeleyen birden çok dönemi desteği için .NET Framework yenilikleri notlar ve içerir uygulamalarınızı test etme aranacak şeyler.

Çoğu takvimler bir dönemde son derece uzun bir süre gösterir. Gregoryen takvimindeki, örneğin, birden fazla iki bin geçerli dönem yayılır. İçin <xref:System.Globalization.JapaneseCalendar> ve <xref:System.Globalization.JapaneseLunisolarCalendar>, birden çok dönemi destekleyen iki takvimler, bu durum geçerli değildir. Bir dönem için bir ın İmparatorluk dönemin karşılık gelir. Geçerli dönem sayısı üst sınırı bilinmeyen olduğunda özellikle birden çok dönemi için destek, özel zorlukları doğurur. 

### <a name="eras-and-era-names"></a>Dönemler ve dönem adları

. NET'te, belirli bir takvim uygulamasıyla desteklenen dönemleri gösteren tamsayılar ters sırada depolanır <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> dizisi. (Aynı dönemi en son zaman aralığı ile) geçerli dönem dizin ve içindir <xref:System.Globalization.Calendar> destekleyen birden çok dönemi, art arda gelen her dizin sınıfları önceki dönemi yansıtır. Statik <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> özelliği geçerli dönemin dizinini tanımlar <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> dizi; bir sabit değeri olan her zaman sıfır olan. Tek tek <xref:System.Globalization.Calendar> sınıfları da geçerli dönemin değerini döndüren statik alanlar içerir. Bunlar aşağıdaki tabloda listelenmiştir.

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

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

Ek olarak, "g" özel tarih ve saat biçimi dizisi, bir tarih ve saatin dize gösteriminde bir takvimin dönem adını içerir. Daha fazla bilgi için [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Bir tarihi bir dönemle örnekleme

İki <xref:System.Globalization.Calendar> birden çok dönemi destekleyen sınıflar, bir belirli bir yıl, ay ve gün, ay değeri içeren bir tarih belirsiz olabilir. Örneğin, tarafından desteklenen tüm Arial <xref:System.Globalization.JapaneseCalendar> yıllar numarası 1'dir. Normalde, bir dönem belirtilmezse, tarih ve saat ve takvim yöntemleri değerlerin geçerli döneme ait olduğunu varsayar. Bu doğru <xref:System.DateTime.%23ctor%2A> ve <xref:System.DateTimeOffset.%23ctor%2A> parametreleri türü oluşturucuları <xref:System.Globalization.Calendar>, hem de [JapaneseCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) ve [JapaneseLunisolarCalendar.ToDateTime ](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) yöntemleri. Aşağıdaki örnek, belirtilmeyen bir dönem, ikinci yılın 1 Ocak temsil eden bir tarih oluşturur. Örnekte gösterildiği çıktısı, tarih, ikinci yılın Heisei dönemi, bu örnekte yürütülmesi zaman geçerli dönem olarak yorumlanır. Tarafından döndürülen dizede yıl Çağ, 平成, önündeki <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> yöntemi ve 1 Ocak 1990 için de Gregoryen takvimindeki karşılık gelir. (Heisei dönemi aralığını 1989, Gregoryen takvimindeki 2019 sağlamaktır.)

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Ancak, dönemi değişirse, bu kodun amacı belirsiz hale gelir. Tarih, iki yıl geçerli dönemin temsil etmek için amaçlanmamıştır veya Heisei dönemi ikinci yılın göstermek için tasarlanmıştır? Bu belirsizlik işlemler sırasında önlemek için iki yolu vardır:

- Varsayılan tarih ve saat değeri örneklemek <xref:System.Globalization.GregorianCalendar> sınıfı. Ardından, aşağıdaki örnekte gösterildiği gibi bir tarih dize gösterimini için Japonca takvimi veya Japonca Ay Güneş takvimini kullanabilirsiniz.

   [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
   [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Bir dönemi açıkça belirten bir tarih ve saat yöntemini çağırın. Bu, aşağıdaki yöntemleri içerir:

   - <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> Yöntemi <xref:System.Globalization.JapaneseCalendar> veya <xref:System.Globalization.JapaneseLunisolarCalendar> sınıfı.

   - A <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemi gibi ayrıştırma <xref:System.DateTime.Parse%2A>, <xref:System.DateTime.TryParse%2A>, <xref:System.DateTime.ParseExact%2A>, veya <xref:System.DateTime.TryParseExact%2A>, ayrıştırılacak dize içerir ve isteğe bağlı olarak bir <xref:System.Globalization.DateTimeStyles> geçerli kültür Japonca-Japonya ise bağımsız değişken (" ja-JP") ve bu kültürün takvimini <xref:System.Globalization.JapaneseCalendar>. Ayrıştırılacak dize dönemi içermelidir.

   - A <xref:System.DateTime> veya <xref:System.DateTimeOffset> içeren yöntemi ayrıştırılırken bir `provider` türünde parametre <xref:System.IFormatProvider>. `provider` aşağıdakilerden biri olması gereken bir <xref:System.Globalization.CultureInfo> Japonca-Japonya ("ja-JP") kültürü geçerli takvimini temsil eden nesne <xref:System.Globalization.JapaneseCalendar> veya <xref:System.Globalization.DateTimeFormatInfo> nesnesi <xref:System.Globalization.DateTimeFormatInfo.Calendar> özelliği <xref:System.Globalization.JapaneseCalendar>. Ayrıştırılacak dize dönemi içermelidir.

   Aşağıdaki örnek bir tarih ve saat 8 Eylül 1868 üzerinde başladı ve 29 Temmuz 1912 sonlandı Meiji dönemi içinde örneklemek için üç bu yöntemleri kullanır. 

   [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
   [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Birden çok dönemi destekleyen takvimlerle çalışırken *her zaman* bir tarihi örneklemek için Miladi kullanın veya ne zaman örneği bir tarih ve saat o takvime dayalı dönemi belirtin.

Bir dönem için belirtilirken <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> yöntem, takvimin dönem dizinini sağlamak <xref:System.Globalization.Calendar.Eras> özelliği. Takvimler, dönemleri değişikliğe tabi olduğu için ancak bu dizinleri sabit değerlerdir değil; Geçerli dönem dizin 0 olduğundan ve eski dönemi dizindeki `Eras.Length - 1`. Takvime yeni bir dönemi eklendiğinde, önceki dönemleri dizinleri birer birer artırır. İlgili dönem dizin şu şekilde belirtebilirsiniz:

- Geçerli dönem içinde tarihler için her zaman Takvim kullanın <xref:System.Globalization.Calendar.CurrentEra> özelliği.

- Belirtilen bir dönem içinde tarihler için kullanmak <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> belirtilen dönem adına karşılık gelen dizine almak için yöntemi. Bunu gerektiren <xref:System.Globalization.JapaneseCalendar> geçerli takvimi olması <xref:System.Globalization.CultureInfo> ja-JP kültürü temsil eden nesne.  (Bu tekniği çalışır <xref:System.Globalization.JapaneseLunisolarCalendar> de beri destekliyorsa aynı dönemi olarak <xref:System.Globalization.JapaneseCalendar>.) Önceki örnekte, bu yaklaşımı gösterir.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Takvimleri, dönemleri ve tarih aralıkları: Gevşek aralığı denetimleri

Çok fazla bağımsız takvimler tarih aralıkları desteklenen gibi dönemi içinde <xref:System.Globalization.JapaneseCalendar> ve <xref:System.Globalization.JapaneseLunisolarCalendar> sınıfları de aralık desteklenen. Daha önce .NET katı dönem dönem özel tarih aralığı bu dönem içinde olduğunu emin olmak için aralığı denetler kullanılır. Diğer bir deyişle, bir tarih belirtilen dönem aralığının dışında ise çağırılıyorsa yöntem bir <xref:System.ArgumentOutOfRangeException>. Şu anda .NET gevşek aralıklı varsayılan denetimini kullanır. Tüm .NET sürümlerini gevşek era sunulan güncelleştirmeler denetimleri aralığı; örneğini belirtilen dönem aralığının dışında bir dönem özgü tarih girişimi "aşağıdaki dönemi taşmaları" ve hiçbir özel durum.

Aşağıdaki örnek, bir tarihi 25 aralık 1926 üzerinde başladı ve 7 Ocak 1989 sonlandı Showa dönemi 65th yılında örneklemek çalışır. Bu tarihin 9 Ocak 1990 için karşılık gelen Showa dönem aralığının dışında olan <xref:System.Globalization.JapaneseCalendar>. Örneğin çıktısında gösterildiği gibi örnek tarafından görüntülenen 9 Ocak 1990 Heisei dönemi ikinci yılında tarihtir.

   [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
   [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

İstenmeyen gevşek aralığı denetimleri katı bir aralık girişinde, uygulamanızın üzerinde çalıştığı .NET sürümüne bağlı olarak çeşitli yollarla geri yükleyebilirsiniz:

- **.NET core:** Şu şekilde ekleyebilirsiniz *. netcore.runtime.json* yapılandırma dosyası:

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
      } 
   }
   ```

- **.NET framework 4.6 veya üzeri:** Aşağıdaki AppContext anahtarı ayarlayabilirsiniz:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
     </runtime>
   </configuration>
   ```

- **.NET framework 4.5.2 veya önceki sürümleri:** Aşağıdaki kayıt defteri değerini ayarlayabilirsiniz:

   |  |  |
   |--|--|
   |Anahtar | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |Ad | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
   |Tür | REG_SZ |
   |Değer | 1. |

Önceki örnekte etkin katı aralığı denetimleri ile oluşturur bir <xref:System.ArgumentOutOfRangeException> ve aşağıdaki çıkışı görüntüler:

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="representing-dates-in-calendars-with-multiple-eras"></a>Tarihleri takvimlerde birden çok dönemlerle gösterme

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

Japonca takvimlerinde ilk yıllık bir dönem Gannen (元年) olarak adlandırılır. Örneğin, Heisei 1 yerine Heisei dönemi, ilk yıl Heisei Gannen açıklanabilir. .NET, biçimlendirme işlemleri tarihler için içinde bu kuralı devralır ve kez biçimlendirilmiş aşağıdaki standart veya özel bir tarih ve saat biçimi dizeleri ile kullanıldığında bir <xref:System.Globalization.CultureInfo> ileJaponca-Japonya("ja-JP")kültürütemsiledennesne<xref:System.Globalization.JapaneseCalendar> sınıfı:

- [Uzun tarih deseni](../base-types/standard-date-and-time-format-strings.md#LongDate), "D" standart tarih ve saat biçim dizesi tarafından belirtilen.
- [Tam tarih uzun saat deseni](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime), "F" standart tarih ve saat biçim dizesi tarafından belirtilen.
- [Tam tarih kısa saat deseni](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime), "f" standart tarih ve saat biçim dizesi tarafından belirtilen.
- [Yıl/ay desen](../base-types/standard-date-and-time-format-strings.md#YearMonth), Y belirttiği "veya"y"standart tarih ve saat biçimi.
- ["Ggy '年'" veya "ggy年" [özel tarih ve saat biçim dizesi](../base-types/custom-date-and-time-format-strings.md).

Örneğin, aşağıdaki örnekte ilk yılında Heisei dönem bir tarih görüntüler <xref:System.Globalization.JapaneseCalendar> .

   [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
   [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Bu davranış istenmeyen biçimlendirme işlemlerinde, her zaman ilk yıllık bir dönem "1" olarak .NET sürümüne bağlı olarak aşağıdakileri yaparak "Gannen yerine" temsil önceki davranışı geri yükleyebilirsiniz:

- **.NET core:** Şu şekilde ekleyebilirsiniz *. netcore.runtime.json* yapılandırma dosyası:

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
      } 
   }
   ```

- **.NET framework 4.6 veya üzeri:** Aşağıdaki AppContext anahtarı ayarlayabilirsiniz:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
     </runtime>
   </configuration>
   ```

- **.NET framework 4.5.2 veya önceki sürümleri:** Aşağıdaki kayıt defteri değerini ayarlayabilirsiniz:

   |  |  |
   |--|--|
   |Anahtar | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |Ad | Switch.System.Globalization.FormatJapaneseFirstYearAsANumber |
   |Tür | REG_SZ |
   |Değer | 1. |

Biçimlendirme işlemleri devre dışı olarak gannen desteği sayesinde, önceki örnek aşağıdaki çıkışı görüntüler:

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

Tarih ve saat ayrıştırma işlemlerinde, "1" veya Gannen olarak yıl içeren dizeleri destekler, böylece .NET de güncelleştirildi. Bunu yapmanız ancak tanıdığı için "1" yalnızca bir dönem ilk yıl önceki davranışı geri yükleyebilirsiniz. Aşağıdaki gibi .NET sürümüne bağlı olarak bunu yapabilirsiniz:

- **.NET core:** Şu şekilde ekleyebilirsiniz *. netcore.runtime.json* yapılandırma dosyası:

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
      } 
   }
   ```

- **.NET framework 4.6 veya üzeri:** Aşağıdaki AppContext anahtarı ayarlayabilirsiniz:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
     </runtime>
   </configuration>
   ```

- **.NET framework 4.5.2 veya önceki sürümleri:** Aşağıdaki kayıt defteri değerini ayarlayabilirsiniz:

   |  |  |
   |--|--|  
   |Anahtar | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |Ad | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
   |Tür | REG_SZ |
   |Değer | 1. | 

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Miladi olmayan takvimlerde tarihleri görüntüleme](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Örnek: Takvim haftası aralığının yardımcı programı](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Takvim sınıfı](xref:System.Globalization.Calendar)
