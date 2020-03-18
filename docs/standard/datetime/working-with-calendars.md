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
ms.openlocfilehash: de8e5a03c769a22f3320c7785706555898bf8c1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400591"
---
# <a name="work-with-calendars"></a>Takvimlerle çalışma

Tarih ve saat değeri zaman içinde bir anı gösterse de, dize gösterimi kültüre duyarlıdır ve hem belirli bir kültür saat tarafından saat ve tarih değerlerini görüntülemek için kullanılan kurallara, hem de kültür tarafından kullanılan takvime dayalıdır. Bu konu,.NET'teki takvimdesteğini inceler ve tarih değerleriyle çalışırken takvim sınıflarının kullanımını tartışır.

## <a name="calendars-in-net"></a>.NET'teki takvimler

.NET'teki tüm takvimler, <xref:System.Globalization.Calendar?displayProperty=nameWithType> temel takvim uygulamasını sağlayan sınıftan türetilmiştir. <xref:System.Globalization.Calendar> Sınıftan devralan sınıflardan biri, <xref:System.Globalization.EastAsianLunisolarCalendar> tüm lunisolar takvimler için temel sınıf olan sınıftır. .NET aşağıdaki takvim uygulamalarını içerir:

- <xref:System.Globalization.ChineseLunisolarCalendar>, Hangi Çin lunisolar takvim temsil eder.

- <xref:System.Globalization.GregorianCalendar>, Gregoryen takvimini temsil eder. Bu takvim, numaralandırma tarafından <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> tanımlanan alt türlere (Arapça ve Orta Doğu Fransızcası gibi) ayrılır. Özellik, <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> Gregoryen takviminin alt türünü belirtir.

- <xref:System.Globalization.HebrewCalendar>, İbranice takvimi temsil eder.

- <xref:System.Globalization.HijriCalendar>, Hicri takvimi temsil eder.

- <xref:System.Globalization.JapaneseCalendar>, Japon takvimini temsil eder.

- <xref:System.Globalization.JapaneseLunisolarCalendar>, Japon lunisolar takvimini temsil eder.

- <xref:System.Globalization.JulianCalendar>, Jülyen takvimini temsil eder.

- <xref:System.Globalization.KoreanCalendar>, Kore takvimini temsil eder.

- <xref:System.Globalization.KoreanLunisolarCalendar>, Kore lunisolar takvimini temsil eder.

- <xref:System.Globalization.PersianCalendar>Farsça takvimi temsil eder.

- <xref:System.Globalization.TaiwanCalendar>, Tayvan takvimini temsil eder.

- <xref:System.Globalization.TaiwanLunisolarCalendar>, Tayvan lunisolar takvimini temsil eder.

- <xref:System.Globalization.ThaiBuddhistCalendar>, Tay Budist takvimini temsil eder.

- <xref:System.Globalization.UmAlQuraCalendar>, Umal Kur'an takvimini temsil eder.

Bir takvim iki şekilde kullanılabilir:

- Belirli bir kültür tarafından kullanılan takvim olarak. Her <xref:System.Globalization.CultureInfo> nesnenin geçerli bir takvimi vardır, bu da nesnenin şu anda kullanmakta olduğu takvimdir. Tüm tarih ve saat değerlerinin dize gösterimleri, otomatik olarak geçerli kültürü ve onun geçerli takvimini yansıtır. Genellikle, geçerli takvim kültürün varsayılan takvimidir. <xref:System.Globalization.CultureInfo>nesnelerin, kültürün kullanabileceği ek takvimler içeren isteğe bağlı takvimleri de vardır.

- Belirli bir takvimden bağımsız tek başına bir takvim olarak. Bu durumda, <xref:System.Globalization.Calendar> yöntemleri takvim yansıtan değerler olarak tarihleri ifade etmek için kullanılır.

Altı takvim sınıfının <xref:System.Globalization.ChineseLunisolarCalendar> <xref:System.Globalization.JapaneseLunisolarCalendar>– <xref:System.Globalization.JulianCalendar> <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar>, <xref:System.Globalization.TaiwanLunisolarCalendar> , , ve - yalnızca bağımsız takvimler olarak kullanılabileceğini unutmayın. Herhangi bir kültür tarafından varsayılan takvim olarak veya isteğe bağlı bir takvim olarak kullanılmazlar.

## <a name="calendars-and-cultures"></a>Takvimler ve kültürler

Her <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> kültürün, özellik tarafından tanımlanan varsayılan bir takvimi vardır. Özellik, <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> bu kültürün <xref:System.Globalization.Calendar> varsayılan takvimi de dahil olmak üzere belirli bir kültür tarafından desteklenen tüm takvimleri belirten bir dizi nesne döndürür.

Aşağıdaki örnekte özellikleri <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> ve özellikleri gösteriş tir. Tayland (Tayland) ve Japon (Japonya) kültürleri için `CultureInfo` nesneler oluşturur ve varsayılan ve isteğe bağlı takvimleri görüntüler. Her iki durumda da kültürün varsayılan takviminin <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> koleksiyona dahil edildiğini unutmayın.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Şu anda belirli <xref:System.Globalization.CultureInfo> bir nesne tarafından kullanılmakta <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> olan takvim, kültürün özelliği tarafından tanımlanır. Bir kültürün <xref:System.Globalization.DateTimeFormatInfo> nesnesi <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özellik tarafından döndürülür. Bir kültür oluşturulduğunda, varsayılan değeri <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> özelliğin değeriyle aynıdır. Ancak, kültürün geçerli takvimini <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özellik tarafından döndürülen dizide bulunan herhangi bir takvimle değiştirebilirsiniz. Geçerli takvimi özellik değerine dahil olmayan bir takvime <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> ayarlamaya çalışırsanız, bir takvim <xref:System.ArgumentException> atılır.

Aşağıdaki örnekte, Arap (Suudi Arabistan) kültürü tarafından kullanılan takvim değiştirilmektedir. İlk olarak bir <xref:System.DateTime> değeri anlık olarak gösterir ve mevcut kültürü kullanarak görüntüler - ki bu durumda, İngilizce (ABD) - ve geçerli kültürün takvimi (bu durumda, Gregoryen takvimi). Ardından, geçerli kültürü Arapça (Suudi Arabistan) olacak şekilde değiştirir ve kendi varsayılan Ümmül Kura takvimini kullanarak tarihi görüntüler. Daha sonra `CalendarExists` Hicri takvimin Arap (Suudi Arabistan) kültürü tarafından desteklenip desteklenmediğini belirlemek için bu yöntemi çağırır. Takvim desteklendiğinden, geçerli takvimi Hicri olacak şekilde değiştirir ve yine tarihi görüntüler. Her bir durumda, tarih geçerli kültürün geçerli takvimi kullanılarak görüntülenir.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Tarihler ve takvimler

Bir tür <xref:System.Globalization.Calendar> parametresi içeren ve bir tarihin öğelerinin (yani ay, gün ve yıl) belirli bir takvimdeki değerleri yansıtmasına izin <xref:System.DateTime> <xref:System.DateTimeOffset> veren yapıcılar dışında, her iki ve değerler her zaman Gregoryen takvimine dayanır. Bu, örneğin, özelliğin <xref:System.DateTime.Year%2A?displayProperty=nameWithType> Gregoryen takviminde yılı döndürdüğü ve özelliğin <xref:System.DateTime.Day%2A?displayProperty=nameWithType> Gregoryen takviminde ay günü döndüRdüğü anlamına gelir.

> [!IMPORTANT]
> Bir tarih değeri ile onun dize gösterimi arasında bir fark olduğunu unutmamak önemlidir. İlki Gregoryen takvime dayalıdır; ikincisi ise belirli bir kültürün geçerli takvimine dayalıdır.

Aşağıdaki örnek, özellikler ve <xref:System.DateTime> bunların karşılık <xref:System.Globalization.Calendar> gelen yöntemleri arasındaki bu farkı göstermektedir. Örnekte, geçerli kültür Arapça (Mısır) ve geçerli Takvim Ümmül Kura'dır. Bir <xref:System.DateTime> değer, 2011 yılının yedinci ayının on beşinci gününe ayarlanır. Değişmez kültürün kurallarını kullanırken bu aynı değerler <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemle döndürüldeğinden, bunun Gregoryen tarihi olarak yorumlandığı açıktır. Geçerli kültürün kuralları kullanılarak biçimlendirilen tarihin dize gösterimi, Ümmül Kura takvimindeki denk tarih olan 14/08/32'dir. Daha sonra, `DateTime` `Calendar` üyeleri ve gün, ay ve <xref:System.DateTime> değer yılı dönmek için kullanılır. Her durumda, üyeler tarafından <xref:System.DateTime> döndürülen değerler Gregoryen takvimindeki değerleri <xref:System.Globalization.UmAlQuraCalendar> yansıtırken, üyeler tarafından döndürülen değerler Uum al-Qura takvimindeki değerleri yansıtır.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiate-dates-based-on-a-calendar"></a>Tarihleri takvime göre anında

Değerler Gregoryen takvimine dayandığından, farklı bir takvimdeki gün, ay veya <xref:System.Globalization.Calendar> yıl değerlerini kullanmak istiyorsanız, tarih değerini anlık olarak kullanmak için bir tür parametresi içeren aşırı yüklü bir oluşturucu çağırmanız gerekir. <xref:System.DateTimeOffset> <xref:System.DateTime> Bir <xref:System.DateTime> nesneyi belirli bir takvimin değerlerini temel <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> alan anlık olarak anmak için belirli bir takvim yönteminin aşırı yüklerinden birini de arayabilirsiniz.

Aşağıdaki örnek, bir nesneyi <xref:System.DateTime> <xref:System.Globalization.HebrewCalendar> <xref:System.DateTime> bir oluşturucuya geçirerek bir değeri anında <xref:System.DateTime> ani bir <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> şekilde ve yöntemi çağırarak ikinci bir değeri anında alamet eder. İki değer İbranice takvimden aynı değerlerle oluşturulduğundan, <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> yönteme <xref:System.DateTime> çağrı iki değerin eşit olduğunu gösterir.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="represent-dates-in-the-current-calendar"></a>Geçerli takvimdeki tarihleri temsil et

Tarih ve saat biçimlendirme yöntemleri, tarihleri dizelere dönüştürürken her zaman geçerli takvimi kullanır. Bu, yılın, ayın ve ayın gününün dize gösteriminin geçerli takvimi yansıttığı ve Gregoryen takvimini yansıtmasının gerekli olmadığı anlamına gelir.

Aşağıdaki örnek, geçerli takvimin bir tarihin dize gösterimini nasıl etkilediğini göstermektedir. Geçerli kültürü Çince (Geleneksel, Tayvan) olarak değiştirir ve bir tarih değerini örnekler. Daha sonra geçerli takvimi ve tarihi görüntüler, <xref:System.Globalization.TaiwanCalendar>geçerli takvimi değiştirir ve geçerli takvimi ve tarihi bir kez daha görüntüler. Tarih ilk kez görüntülendiğinde, Gregoryen takvimdeki bir tarih olarak gösterilir. İkinci kez görüntülendiğinde, Tayvan takvimindeki bir tarih olarak gösterilir.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="represent-dates-in-a-non-current-calendar"></a>Geçerli olmayan bir takvimdeki tarihleri temsil et

Belirli bir kültürün geçerli takvimi olmayan bir takvimi kullanan bir tarihi temsil <xref:System.Globalization.Calendar> etmek için, bu nesnenin yöntemlerini çağırmanız gerekir. Örneğin, <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> ve yöntemler, yıl, ay ve gün belirli bir takvimi yansıtan değerlere dönüştürür.

> [!WARNING]
> Bazı takvimler herhangi kültürün isteğe bağlı takvimleri olmadığından, bu takvimlerde tarihleri göstermek, her zaman takvim yöntemlerini çağırmanızı gerektirir. Bu, <xref:System.Globalization.EastAsianLunisolarCalendar>, , <xref:System.Globalization.JulianCalendar>ve <xref:System.Globalization.PersianCalendar> sınıflartintin tüm takvimler için geçerlidir.

Aşağıdaki örnek, <xref:System.Globalization.JulianCalendar> Jülyen takviminde 9 Ocak 1905'te bir tarihi anlık olarak bir nesneyi kullanır. Bu tarih varsayılan (Gregoryen) takvimi kullanılarak görüntülendiğinde, 22 Ocak 1905 olarak gösterilir. Tek tek <xref:System.Globalization.JulianCalendar> yöntemlere yapılan çağrılar, tarihin Jülyen takviminde temsil edilmesini sağlar.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Takvimler ve tarih aralıkları

Takvim tarafından desteklenen en erken tarih, bu takvimin <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> özelliğiyle gösterilir. <xref:System.Globalization.GregorianCalendar> Sınıf için bu tarih 1 Ocak 0001 C.E. .NET'teki diğer takvimlerin çoğu daha sonraki bir tarihi destekler. Bir takvimin en erken desteklenen tarihinden önce bir tarih ve saat değeri <xref:System.ArgumentOutOfRangeException> ile çalışmaya çalışmak bir özel durum atar.

Ancak, önemli bir istisna vardır. Nesne ve <xref:System.DateTime> <xref:System.DateTimeOffset> nesnenin varsayılan (başharfsüz) değeri <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> değere eşittir. Bu tarihi 1 Ocak 0001 C.E.'yi desteklemeyen bir takvimde biçimlendirmeye çalışırsanız. ve bir biçim belirtimi sağlamazsanız, biçimlendirme yöntemi "G" (genel tarih/saat deseni) biçim belirtici yerine "s" (sıralanabilir tarih/saat deseni) biçim belirticisini kullanır. Sonuç olarak, biçimlendirme işlemi bir <xref:System.ArgumentOutOfRangeException> özel durum atmaz. Bunun yerine, desteklenmeyen tarihi döndürür. Bu, mevcut kültürün Japonca takvimiyle Japonca <xref:System.DateTime.MinValue?displayProperty=nameWithType> (Japonya) ve Umal Kur'an takvimiile Arapça (Mısır) olarak ayarlandığı zaman değerini gösteren aşağıdaki örnekte gösterilmiştir. Ayrıca, geçerli kültürü İngilizce 'ye (ABD) <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> ayarlar ve <xref:System.Globalization.CultureInfo> bu nesnelerin her biriyle yöntemi çağırır. Her durumda, tarih sıralanabilir tarih/saat deseni kullanılarak görüntülenir.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="work-with-eras"></a>Eras ile çalışma

Takvimler genellikle tarihleri dönemlere ayırır. Ancak, <xref:System.Globalization.Calendar> .NET'teki sınıflar takvimtarafından tanımlanan her dönemi desteklemez <xref:System.Globalization.Calendar> ve sınıfların çoğu yalnızca tek bir dönemi destekler. Yalnızca <xref:System.Globalization.JapaneseCalendar> ve <xref:System.Globalization.JapaneseLunisolarCalendar> sınıflar birden çok farklı zamanları destekler.

> [!IMPORTANT]
> Reiwa dönemi, yeni bir <xref:System.Globalization.JapaneseCalendar> dönem <xref:System.Globalization.JapaneseLunisolarCalendar>ve , 1 Mayıs 2019 tarihinde başlar. Bu değişiklik, bu takvimleri kullanan tüm uygulamaları etkiler. Daha fazla bilgi için aşağıdaki makalelere bakın:
>
> - [Japonca takvimde yeni bir dönemi ele alan .NET,](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/)birden çok dönemli takvimleri desteklemek için .NET'e eklenen özellikleri ve çok aylık takvimleri işlerken kullanılacak en iyi uygulamaları tartışıyor.
> - [Uygulamanızı,](/windows/uwp/design/globalizing/japanese-era-change)dönem değişikliğine hazır olmalarını sağlamak için Windows'da uygulamalarınızın test edilmesi hakkında bilgi sağlayan Japon dönemi değişikliği için hazırlayın.
> - Yeni Japon takvim dönemiyle ilgili tek tek Windows sürümleri için .NET Framework güncelleştirmelerini listeleyen [.NET Framework için yeni Japon Dönemi güncelleştirmelerinin özeti,](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework)çok aylık destek için yeni .NET Framework özelliklerine dikkat çekiyor ve uygulamalarınızı test edince dikkat edilmesi gerekenleri içeriyor.

Çoğu takvimdeki bir dönem son derece uzun bir zamanı gösterir. Örneğin Gregoryen takviminde, geçerli dönem iki bin yıldan fazladır. <xref:System.Globalization.JapaneseCalendar> Birden çok ayı destekleyen iki takvim için durum böyle <xref:System.Globalization.JapaneseLunisolarCalendar>değildir. Bir dönem, imparatorun hükümdarlık dönemine karşılık gelir. Özellikle mevcut dönemin üst sınırı bilinmiyorsa, birden fazla döneme destek özel zorluklar teşkil etmektedir.

### <a name="eras-and-era-names"></a>Çağlar ve dönem isimleri

.NET'te, belirli bir takvim uygulaması tarafından desteklenen dönemleri temsil eden tamsayılar <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> dizide ters sırada depolanır. Geçerli dönem (en son zaman aralığıile dönem) dizin sıfır <xref:System.Globalization.Calendar> ve birden çok dönemi destekleyen sınıflar için, her ardışık dizin önceki dönemi yansıtır. Statik <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> özellik dizideki geçerli dönemin dizisini <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> tanımlar; değeri her zaman sıfır olan bir sabittir. Tek <xref:System.Globalization.Calendar> tek sınıflar, geçerli dönemin değerini döndüren statik alanları da içerir. Bunlar aşağıdaki tabloda listelenmiştir.

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

Belirli bir dönem numarasına karşılık gelen ad, dönem numarasını veya <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> metoduna geçerek alınabilir. Aşağıdaki örnek, <xref:System.Globalization.GregorianCalendar> sınıftaki dönem desteği hakkında bilgi almak için bu yöntemleri çağırır. Geçerli dönemin ikinci yılının 1 Ocak'ına karşılık gelen Gregoryen takvim tarihini ve desteklenen her Japon takvim döneminin ikinci yılının 1 Ocak'ına karşılık gelen Gregoryen takvim tarihini görüntüler.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

Ek olarak, "g" özel tarih ve saat biçimi dizisi, bir tarih ve saatin dize gösteriminde bir takvimin dönem adını içerir. Daha fazla bilgi için [özel tarih ve saat biçimi dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)bakın.

### <a name="instantiatie-a-date-with-an-era"></a>Instantiatie bir dönem ile bir tarih

Birden çok <xref:System.Globalization.Calendar> dönemdestekleyen iki sınıf için, belirli bir yıl, ay ve ayın gününden oluşan bir tarih belirsiz olabilir. Örneğin, sayısı 1 olan yıllar <xref:System.Globalization.JapaneseCalendar> tarafından desteklenen tüm eralar. Normalde, bir dönem belirtilmezse, tarih ve saat ve takvim yöntemleri değerlerin geçerli döneme ait olduğunu varsayar. Bu <xref:System.Globalization.Calendar>tür parametreleri <xref:System.DateTimeOffset.%23ctor%2A> içeren <xref:System.DateTime.%23ctor%2A> ve yapıcılar için de geçerlidir, yanı sıra [JapaneseCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) ve [JapaneseLunisolarCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) yöntemleri. Aşağıdaki örnek, belirtilmemiş bir dönemin ikinci yılının 1 Ocak'ını temsil eden bir tarihi anında gösterir. Reiwa döneminin geçerli dönem olduğu bir örneği uygularsanız, tarih Reiwa döneminin ikinci yılı olarak yorumlanır. Dönem, <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> yöntem tarafından döndürülen dize yıl öncesinde ve Gregoryen takviminde, 1 Ocak 2020 karşılık gelir. (Reiwa dönemi Gregoryen takviminin 2019 yılında başlar.)

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Ancak, dönem değişirse, bu kodun amacı belirsiz hale gelir. Tarih, geçerli dönemin ikinci yılını mı temsil edecek, yoksa Heisei döneminin ikinci yılını mı temsil edecek? Bu belirsizliği önlemenin iki yolu vardır:

- Varsayılan <xref:System.Globalization.GregorianCalendar> sınıfı kullanarak tarih ve saat değerini anında anons edin. Daha sonra, aşağıdaki örnekte görüldüğü gibi, tarihlerin dize gösterimi için Japonca takvimi veya Japon Lunisolar takvimini kullanabilirsiniz.

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Bir dönemi açıkça belirten bir tarih ve saat yöntemini çağırın. Bu, aşağıdaki yöntemleri içerir:

  - Veya <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> <xref:System.Globalization.JapaneseLunisolarCalendar> sınıfın <xref:System.Globalization.JapaneseCalendar> yöntemi.

  - Mevcut <xref:System.DateTime> <xref:System.DateTimeOffset> kültür Japonca-Japonya ("ja-JP") <xref:System.DateTime.Parse%2A>ise ve kültürün takvimi <xref:System.DateTime.TryParse%2A> <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A> <xref:System.Globalization.JapaneseCalendar>ise, <xref:System.Globalization.DateTimeStyles> ayrıştırılması ve isteğe bağlı olarak bir argüman olarak ayrıştırılacak dize yi içeren bir veya ayrıştırma yöntemi. Ayrıştılacak dize dönemi içermelidir.

  - Bir <xref:System.DateTime> <xref:System.DateTimeOffset> tür <xref:System.IFormatProvider>parametresi içeren `provider` bir veya ayrıştma yöntemi. `provider`geçerli takvimi <xref:System.Globalization.CultureInfo> olan Japon-Japonya ("ja-JP") kültürünü temsil eden <xref:System.Globalization.JapaneseCalendar> bir <xref:System.Globalization.DateTimeFormatInfo> nesne <xref:System.Globalization.DateTimeFormatInfo.Calendar> veya <xref:System.Globalization.JapaneseCalendar>özelliği . Ayrıştılacak dize dönemi içermelidir.

  Aşağıdaki örnek, 8 Eylül 1868'de başlayan ve 29 Temmuz 1912'de sona eren Meiji döneminde bir tarih ve saati anlık olarak başlatmak için bu yöntemlerden üçünü kullanmaktadır.

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Birden çok dönemi destekleyen takvimlerle çalışırken, bir tarihi anlık olarak belirlemek veya bu takvime göre bir tarih ve saati anında belirttiğiniz dönemi belirtmek için *her zaman* Gregoryen tarihini kullanın.

<xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> Yönteme bir dönem belirtirken, takvimin <xref:System.Globalization.Calendar.Eras> özelliğinde dönemin dizinini sağlarsınız. Ancak, geçişe tabi olan takvimler için bu dizinler sabit değerler değildir; geçerli dönem endeks 0'da, en eski `Eras.Length - 1`dönem ise indekstedir. Takvime yeni bir dönem eklendiğinde, önceki dönemin dizinleri bir artar. Uygun dönem dizini aşağıdaki gibi sağlayabilirsiniz:

- Geçerli dönemdeki tarihler için her zaman <xref:System.Globalization.Calendar.CurrentEra> takvimin özelliğini kullanın.

- Belirli bir dönemdeki tarihler <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> için, belirtilen bir dönem adına karşılık gelen dizini almak için yöntemi kullanın. Bu, ja-JP kültürünü temsil <xref:System.Globalization.CultureInfo> eden nesnenin geçerli takvimi <xref:System.Globalization.JapaneseCalendar> olmasını gerektirir.  (Bu teknik de <xref:System.Globalization.JapaneseLunisolarCalendar> çalışır, çünkü aynı eritmeleri <xref:System.Globalization.JapaneseCalendar>destekler .) Önceki örnekbu yaklaşımı göstermektedir.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Takvimler, erler ve tarih aralıkları: Rahat aralık denetimleri

Çok bireysel takvimler gibi tarih aralıkları desteklenen var, <xref:System.Globalization.JapaneseLunisolarCalendar> ve sınıflarda <xref:System.Globalization.JapaneseCalendar> eras da aralıkları destekledi. Daha önce,.NET, döneme özgü bir tarihin o dönemin aralığında olduğundan emin olmak için sıkı era aralığı denetimleri kullansın. Diğer bir tarihte, belirtilen dönemin aralığının dışında bir tarih varsa, yöntem bir <xref:System.ArgumentOutOfRangeException>. Şu anda,.NET varsayılan olarak gevşek aralıklı denetim kullanır. .NET'in tüm sürümlerinde yapılan güncellemeler, rahat dönem aralığı denetimlerini tanıttı; belirtilen dönemin aralığı dışında bir döneme özgü tarih ivedilik girişimi "taşar" aşağıdaki döneme ve hiçbir istisna atılır.

Aşağıdaki örnek, 25 Aralık 1926'da başlayan ve 7 Ocak 1989'da sona eren Showa döneminin 65. Bu tarih 9 Ocak 1990, hangi Showa döneminin aralığı dışında <xref:System.Globalization.JapaneseCalendar>karşılık gelir. Örnekteki çıktının da gösterdiği gibi, örnektarafından görüntülenen tarih, Heisei döneminin ikinci yılında, 9 Ocak 1990'dır.

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

Rahat aralık denetimleri istenmeyen durumdaysa, uygulamanızın yürütüldettiği .NET sürümüne bağlı olarak, katı aralık denetimlerini çeşitli şekillerde geri yükleyebilirsiniz:

- **.NET Çekirdek:** *.netcore.runtime.json* config dosyasına aşağıdakileri ekleyin:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **.NET Framework 4.6 veya sonrası:** *app.config* dosyasında aşağıdaki AppContext anahtarını ayarlayın:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 veya önceki:** Aşağıdaki kayıt defteri değerini ayarlayın:

   |  |  |
   |--|--|
   | **Anahtar** | **HKEY_LOCAL_MACHINE\Yazılım\Microsoft\\. NETFramework\AppContext** |
   | **Adı** | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
   | **Tür** | REG_SZ |
   | **Değer** | true |

Sıkı aralık denetimleri etkinken, önceki <xref:System.ArgumentOutOfRangeException> örnek bir çıkış atar ve aşağıdaki çıktıyı görüntüler:

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="represent-dates-in-calendars-with-multiple-eras"></a>Tarihleri birden çok kez takvimlerde temsil eder

Bir <xref:System.Globalization.Calendar> nesne dönemleri destekliyorsa ve <xref:System.Globalization.CultureInfo> bir nesnenin geçerli takvimiyse, dönem tam tarih ve saat, uzun tarih ve kısa tarih desenleri için bir tarih ve saat değerinin dize gösterimine eklenir. Aşağıdaki örnekte, geçerli kültür Japonya (Japonca) ve geçerli takvim Japon takvimi olduğunda bu tarih desenleri görüntülenmektedir.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> Sınıf, <xref:System.Globalization.JapaneseCalendar> .NET'te her ikisi de birden fazla dönemdetarihleri destekleyen ve bir <xref:System.Globalization.CultureInfo> nesnenin geçerli takvimi <xref:System.Globalization.CultureInfo> olan , özellikle Japonca (Japonya) kültürünü temsil eden bir nesnenin tek takvim sınıfıdır.

Tüm takvimler için, "g" özel biçim belirleyicisi, sonuç dizesinde dönemi içerir. Aşağıdaki örnekte, geçerli takvim Gregoryen takvim olduğunda dönemi sonuç dizesine eklemek için "AA-gg-yyyy g" özel biçimi kullanılmaktadır.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

Bir tarihin dize gösteriminin geçerli takvim olmayan bir takvimde <xref:System.Globalization.Calendar> ifade edildiği <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> durumlarda, <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>sınıf, ait <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>olduğu <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> dönemin yanı sıra bir tarihi de açıkça belirtmek için , ve yöntemlerle birlikte kullanılabilecek bir yöntem içerir. Aşağıdaki örnek, <xref:System.Globalization.JapaneseLunisolarCalendar> bir illüstrasyon sağlamak için sınıfı kullanır. Ancak, sonuç dizesinde dönem için bir tamsayı yerine anlamlı bir ad veya kısaltma eklenmesinin bir <xref:System.Globalization.DateTimeFormatInfo> nesneyi <xref:System.Globalization.JapaneseCalendar> anında incelemenizi ve geçerli takvimini yapmanızı gerektirdiğini unutmayın. (Takvim <xref:System.Globalization.JapaneseLunisolarCalendar> herhangi bir kültürün geçerli takvimi olamaz, ancak bu durumda iki takvim aynı sıraları paylaşır.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

Japon takvimlerinde, bir dönemin ilk yılı Gannen (Japonca) olarak adlandırılır. Örneğin, Heisei 1 yerine, Heisei döneminin ilk yılı Heisei Gannen olarak tanımlanabilir. .NET, sınıfla birlikte Japon-Japonya ("ja-JP") kültürünü temsil eden bir <xref:System.Globalization.CultureInfo> nesneyle kullanıldığında, aşağıdaki standart veya özel tarih ve saat biçimi <xref:System.Globalization.JapaneseCalendar> dizeleriyle biçimlendirilmiş tarih ve saatleriçin biçimlendirme işlemlerinde bu kuralı benimser:

- "D" standart tarih ve saat biçimi dizesi ile gösterilen [uzun tarih deseni.](../base-types/standard-date-and-time-format-strings.md#LongDate)
- [Tam tarih uzun zaman deseni,](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime)"F" standart tarih ve saat biçimi dizeile gösterilir.
- [Tam tarih kısa zaman deseni,](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime)"f" standart tarih ve saat biçimi dizeile gösterilir.
- Y" veya "y" standart tarih ve saat biçimi dizesi ile gösterilen [yıl/ay deseni.](../base-types/standard-date-and-time-format-strings.md#YearMonth)
- ["Ggy'' veya "ggy中" [özel tarih ve saat biçimi dize .](../base-types/custom-date-and-time-format-strings.md)

Örneğin, aşağıdaki örnekte Heisei döneminin ilk yılında bir tarih <xref:System.Globalization.JapaneseCalendar>görüntüler.

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Bu davranış biçimlendirme işlemlerinde istenmeyen bir davranışsa, .NET sürümüne bağlı olarak aşağıdakileri yaparak, bir dönemin ilk yılını "Gannen" yerine "1" olarak temsil eden önceki davranışı geri yükleyebilirsiniz:

- **.NET Çekirdek:** *.netcore.runtime.json* config dosyasına aşağıdakileri ekleyin:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **.NET Framework 4.6 veya sonrası:** *app.config* dosyasında aşağıdaki AppContext anahtarını ayarlayın:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 veya önceki:** Aşağıdaki kayıt defteri değerini ayarlayın:

   |  |  |
   |--|--|
   | **Anahtar** | **HKEY_LOCAL_MACHINE\Yazılım\Microsoft\\. NETFramework\AppContext** |
   | **Adı** | Switch.System.Globalization.FormatJapaneseFirstYearAsANumber |
   | **Tür** | REG_SZ |
   | **Değer** | true |

Biçimlendirme işlemleri devre dışı gannen desteği ile, önceki örnek aşağıdaki çıktıgörüntüler:

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

.NET ayrıca, "1" veya Gannen olarak temsil edilen yılı içeren tarih ve saat ayrıştırma işlemleri destek dizelerini destekleyecek şekilde de güncelleştirildi. Bunu yapmanız gerekmez, ancak önceki davranışı yalnızca "1" bir dönemin ilk yılı olarak tanımak için geri yükleyebilirsiniz. Bunu .NET sürümüne bağlı olarak aşağıdaki gibi yapabilirsiniz:

- **.NET Çekirdek:** *.netcore.runtime.json* config dosyasına aşağıdakileri ekleyin:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **.NET Framework 4.6 veya sonrası:** *app.config* dosyasında aşağıdaki AppContext anahtarını ayarlayın:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 veya önceki:** Aşağıdaki kayıt defteri değerini ayarlayın:

   |  |  |
   |--|--|
   | **Anahtar** | **HKEY_LOCAL_MACHINE\Yazılım\Microsoft\\. NETFramework\AppContext** |
   | **Adı** | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
   | **Tür** | REG_SZ |
   | **Değer** | true |

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Tarihleri Gregoryen olmayan takvimlerde görüntüleme](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Örnek: Takvim haftası aralığı yardımcı programı](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Takvim sınıfı](xref:System.Globalization.Calendar)
