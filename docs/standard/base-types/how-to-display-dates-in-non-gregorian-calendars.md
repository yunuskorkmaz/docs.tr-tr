---
title: 'Nasıl yapılır: Miladi Olmayan Takvimlerde Tarihleri Görüntüleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- dates [.NET Framework], formatting
- calendars [.NET Framework], displaying dates
- displaying date and time data
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
ms.openlocfilehash: 455996d091f92367667e7077a4524898cd8face6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138748"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Nasıl yapılır: Miladi Olmayan Takvimlerde Tarihleri Görüntüleme
<xref:System.DateTime> ve <xref:System.DateTimeOffset> türleri varsayılan takvim olarak Gregoryen takvimi kullanır. Bu, bir tarih ve saat değerinin `ToString` yönteminin, bu tarih ve saat başka bir takvim kullanılarak oluşturulmuş olsa bile, Gregoryen takvimdeki tarih ve saatin dize gösterimini gösterdiği anlamına gelir. Bu, Farsça takvimi ile bir tarih ve saat değeri oluşturmak için iki farklı yol kullanan aşağıdaki örnekte gösterilmiştir, ancak hala <xref:System.DateTime.ToString%2A> yöntemini çağırdığında Gregoryen takvimdeki tarih ve saat değerlerini görüntüler. Bu örnek, belirli bir takvimdeki tarihi görüntülemek için yaygın olarak kullanılan iki ancak yanlış tekniği yansıtır.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Belirli bir takvimdeki tarihi göstermek için iki farklı teknik kullanılabilir. İlki, takvimin belirli bir kültürün varsayılan takvimi olmasını gerektirir. İkincisi herhangi bir takvimle birlikte kullanılabilir.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Bir kültürün varsayılan takvim tarihini görüntülemek için  
  
1. Kullanılacak takvimi temsil eden <xref:System.Globalization.Calendar> sınıfından türetilmiş bir takvim nesnesi örneği oluşturun.  
  
2. Biçimlendirmeyi göstermek için kullanılacak olan kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi örneği oluşturun.  
  
3. Takvim nesnesinin, <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özelliği tarafından döndürülen dizinin bir üyesi olup olmadığını öğrenmek için <xref:System.Array.Exists%2A?displayProperty=nameWithType> yöntemini çağırın. Bu, takvimin <xref:System.Globalization.CultureInfo> nesnesi için varsayılan takvim olarak işlev görebilir olduğunu gösterir. Dizinin bir üyesi değilse, "herhangi bir takvime tarihi görüntüleme" bölümündeki yönergeleri izleyin.  
  
4. Takvim nesnesini <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Globalization.DateTimeFormatInfo> nesnesinin <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> özelliğine atayın.  
  
    > [!NOTE]
    > <xref:System.Globalization.CultureInfo> sınıfında bir <xref:System.Globalization.CultureInfo.Calendar%2A> özelliği de vardır. Ancak, salt okunurdur ve sabittir; <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> özelliğine atanan yeni varsayılan takvimi yansıtacak şekilde değişmez.  
  
5. <xref:System.DateTime.ToString%2A> veya <xref:System.DateTime.ToString%2A> yöntemini çağırın ve önceki adımda varsayılan takvimi değiştirilen <xref:System.Globalization.CultureInfo> nesnesine geçirin.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Herhangi bir takvimde tarihi görüntülemek için  
  
1. Kullanılacak takvimi temsil eden <xref:System.Globalization.Calendar> sınıfından türetilmiş bir takvim nesnesi örneği oluşturun.  
  
2. Tarih ve saat değerinin dize gösteriminde hangi tarih ve saat öğelerinin görüneceğini belirleme.  
  
3. Göstermek istediğiniz her bir tarih ve saat öğesi için, takvim nesnesinin `Get`... öğesini çağırın. yöntemidir. Aşağıdaki yöntemler mevcuttur:  
  
    - uygun takvimdeki yılı göstermek için <xref:System.Globalization.Calendar.GetYear%2A>.  
  
    - uygun takvimdeki ayı göstermek için <xref:System.Globalization.Calendar.GetMonth%2A>.  
  
    - uygun takvimdeki ayın gün sayısını göstermek için <xref:System.Globalization.Calendar.GetDayOfMonth%2A>.  
  
    - <xref:System.Globalization.Calendar.GetHour%2A>, uygun takvimdeki günün saatini görüntüler.  
  
    - <xref:System.Globalization.Calendar.GetMinute%2A>, uygun takvimdeki saat cinsinden dakikaları görüntüler.  
  
    - <xref:System.Globalization.Calendar.GetSecond%2A>, saniyeyi uygun takvimdeki dakika cinsinden görüntüler.  
  
    - <xref:System.Globalization.Calendar.GetMilliseconds%2A>, saniyeyi uygun takvimde göstermek için.  
  
## <a name="example"></a>Örnek  
 Örnek iki farklı takvimi kullanarak bir tarih görüntüler. Bu, AR-JO kültürü için varsayılan takvim olarak Hicri takvimini tanımladıktan sonra tarihi görüntüler ve SK-IR kültürüne göre isteğe bağlı bir takvim olarak desteklenmeyen Farsça takvimini kullanarak tarihi görüntüler.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Her <xref:System.Globalization.CultureInfo> nesnesi, <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> özelliği tarafından belirtilen bir veya daha fazla takvimi destekleyebilir. Bunlardan biri, kültürün varsayılan takvimi olarak atanır ve salt okunurdur <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> özelliği tarafından döndürülür. İsteğe bağlı takvimlerin bir diğeri, bu takvimi temsil eden bir <xref:System.Globalization.Calendar> nesnesi, <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> özelliğinde atanarak varsayılan olarak belirlenebilir. Ancak, <xref:System.Globalization.PersianCalendar> sınıfı tarafından temsil edilen Farsça takvimi gibi bazı takvimler, herhangi bir kültür için isteğe bağlı takvimler olarak görev almaz.  
  
 Örnek, belirli bir takvimi kullanarak tarihin dize gösterimini oluşturma ayrıntılarının çoğunu işlemek için `CalendarUtility`yeniden kullanılabilir bir takvim yardımcı sınıfı tanımlar. `CalendarUtility` sınıfı aşağıdaki üyelere sahiptir:  
  
- Tek parametresi, bir tarihin temsil edildiği <xref:System.Globalization.Calendar> nesne olan parametreli bir Oluşturucu. Bu, sınıfının özel bir alanına atanır.  
  
- `CalendarExists`, `CalendarUtility` nesnesinin temsil ettiği takvimin, yönteme parametre olarak geçirilen <xref:System.Globalization.CultureInfo> nesnesi tarafından desteklenip desteklenmediğini belirten bir Boole değeri döndüren özel bir yöntemdir. Yöntemi, <xref:System.Array.Exists%2A?displayProperty=nameWithType> yöntemine bir çağrı sarmalar ve <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> dizisini geçirir.  
  
- <xref:System.Array.Exists%2A?displayProperty=nameWithType> yöntemine parametre olarak geçirilen <xref:System.Predicate%601> temsilcisine atanan özel bir yöntem `HasSameName`. Yöntemin her üyesi, yöntem `true`dönene kadar yöntemine geçirilir. Yöntemi, isteğe bağlı bir takvimin adının `CalendarUtility` nesnesi tarafından temsil edilen takvimle aynı olup olmadığını belirler.  
  
- `DisplayDate`, iki parametre geçen aşırı yüklenmiş bir genel yöntem: `CalendarUtility` nesnesi tarafından temsil edilen takvimde ifade etmek için bir <xref:System.DateTime> ya da <xref:System.DateTimeOffset> değeri; ve biçimlendirme kuralları kullanılacak olan kültür. Bir tarihin dize gösterimini döndürme davranışındaki davranışı, hedef takvimin biçimlendirme kuralları kullanılacak kültürün desteklenip desteklenmediğini bağlıdır.  
  
 Bu örnekte bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değeri oluşturmak için kullanılan takvime bakılmaksızın, bu değer genellikle bir Gregoryen tarih olarak ifade edilir. Bunun nedeni <xref:System.DateTime> ve <xref:System.DateTimeOffset> türlerinin herhangi bir takvim bilgisini korumidir. Dahili olarak, 1 Ocak 0001 gece yarısından beri geçen onay işareti sayısı olarak temsil edilir. Bu sayının yorumu takvime göre değişir. Çoğu kültürde varsayılan takvim, Gregoryen takvimidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
