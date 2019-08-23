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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdd500d8eda81708d67254cbc5dc8da701ae4e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963350"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Nasıl yapılır: Miladi Olmayan Takvimlerde Tarihleri Görüntüleme
<xref:System.DateTime> Ve<xref:System.DateTimeOffset> türleri varsayılan takvim olarak Gregoryen takvimi kullanır. Bu, bir tarih ve saat değerinin `ToString` yönteminin, bu tarih ve saat başka bir takvim kullanılarak oluşturulmuş olsa bile, Gregoryen takvimdeki tarih ve saatin dize gösterimini gösterdiği anlamına gelir. Bu, Farsça takvimi ile bir tarih ve saat değeri oluşturmak için iki farklı yol kullanan aşağıdaki örnekte gösterilmiştir, ancak yine de bu tarih ve saat değerlerini, <xref:System.DateTime.ToString%2A> yöntemi çağırdığında Gregoryen takviminde görüntüler. Bu örnek, belirli bir takvimdeki tarihi görüntülemek için yaygın olarak kullanılan iki ancak yanlış tekniği yansıtır.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Belirli bir takvimdeki tarihi göstermek için iki farklı teknik kullanılabilir. İlki, takvimin belirli bir kültürün varsayılan takvimi olmasını gerektirir. İkincisi herhangi bir takvimle birlikte kullanılabilir.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Bir kültürün varsayılan takvim tarihini görüntülemek için  
  
1. Kullanılacak takvimi temsil eden <xref:System.Globalization.Calendar> sınıftan türetilmiş bir takvim nesnesi örneği oluşturun.  
  
2. Tarih görüntülemek <xref:System.Globalization.CultureInfo> için biçimlendirme kullanılacak kültürü temsil eden bir nesne oluşturun.  
  
3. Takvim nesnesinin, <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özelliği tarafından döndürülen dizinin bir üyesi olup olmadığını anlamak için yönteminiçağırın.<xref:System.Array.Exists%2A?displayProperty=nameWithType> Bu, takvimin <xref:System.Globalization.CultureInfo> nesne için varsayılan takvim olarak işlev görebilir olduğunu gösterir. Dizinin bir üyesi değilse, "herhangi bir takvime tarihi görüntüleme" bölümündeki yönergeleri izleyin.  
  
4. Takvim nesnesini <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> , <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Globalization.DateTimeFormatInfo> nesnenin özelliğine atayın.  
  
    > [!NOTE]
    > Sınıfın Ayrıca bir <xref:System.Globalization.CultureInfo.Calendar%2A> özelliği de vardır. <xref:System.Globalization.CultureInfo> Ancak, salt okunurdur ve sabittir; <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> özelliğe atanmış olan yeni varsayılan takvimi yansıtacak şekilde değişmez.  
  
5. Ya da yöntemini çağırın ve önceki adımda varsayılan takvimi değiştirilmiş olan <xref:System.Globalization.CultureInfo> nesneyi geçirin. <xref:System.DateTime.ToString%2A> <xref:System.DateTime.ToString%2A>  
  
### <a name="to-display-the-date-in-any-calendar"></a>Herhangi bir takvimde tarihi görüntülemek için  
  
1. Kullanılacak takvimi temsil eden <xref:System.Globalization.Calendar> sınıftan türetilmiş bir takvim nesnesi örneği oluşturun.  
  
2. Tarih ve saat değerinin dize gösteriminde hangi tarih ve saat öğelerinin görüneceğini belirleme.  
  
3. Göstermek istediğiniz her bir tarih ve saat öğesi için, takvim nesnesinin `Get`... öğesini çağırın. yöntemidir. Aşağıdaki yöntemler mevcuttur:  
  
    - <xref:System.Globalization.Calendar.GetYear%2A>, uygun takvimdeki yılı görüntüleme.  
  
    - <xref:System.Globalization.Calendar.GetMonth%2A>, ayı uygun takvimde göstermek için.  
  
    - <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, uygun takvimdeki ayın gün sayısını görüntüler.  
  
    - <xref:System.Globalization.Calendar.GetHour%2A>, uygun takvimdeki günün saatini görüntüler.  
  
    - <xref:System.Globalization.Calendar.GetMinute%2A>, dakikaları uygun takvimdeki saat cinsinden görüntüler.  
  
    - <xref:System.Globalization.Calendar.GetSecond%2A>, saniyeyi uygun takvimdeki dakika cinsinden görüntüler.  
  
    - <xref:System.Globalization.Calendar.GetMilliseconds%2A>, milisaniye cinsinden uygun takvimdeki milisaniyeyi görüntüler.  
  
## <a name="example"></a>Örnek  
 Örnek iki farklı takvimi kullanarak bir tarih görüntüler. Bu, AR-JO kültürü için varsayılan takvim olarak Hicri takvimini tanımladıktan sonra tarihi görüntüler ve SK-IR kültürüne göre isteğe bağlı bir takvim olarak desteklenmeyen Farsça takvimini kullanarak tarihi görüntüler.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Her <xref:System.Globalization.CultureInfo> nesne, <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> özelliği tarafından belirtilen bir veya daha fazla takvimi destekleyebilir. Bunlardan biri, kültürün varsayılan takvimi olarak atanır ve salt okunurdur <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> özelliği tarafından döndürülür. İsteğe bağlı takvimlerin bir diğeri, bu takvimi <xref:System.Globalization.Calendar> <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> temsil eden bir nesne, <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği tarafından döndürülen özelliğe atanarak varsayılan olarak belirlenebilir. Ancak, <xref:System.Globalization.PersianCalendar> sınıf tarafından temsil edilen Farsça takvimi gibi bazı takvimler, herhangi bir kültür için isteğe bağlı takvimler olarak görev almaz.  
  
 Örnek, belirli bir takvimi kullanarak tarihin dize gösterimini `CalendarUtility`oluşturma ayrıntılarının çoğunu işlemek için yeniden kullanılabilir bir takvim yardımcı sınıfı tanımlar. `CalendarUtility` Sınıfı aşağıdaki üyelere sahiptir:  
  
- Tek parametresi, bir tarihin temsil edildiği bir <xref:System.Globalization.Calendar> nesne olan parametreli bir Oluşturucu. Bu, sınıfının özel bir alanına atanır.  
  
- `CalendarExists`, `CalendarUtility` nesne tarafından temsil edilen takvimin bir parametre olarak yönteme geçirilen <xref:System.Globalization.CultureInfo> nesne tarafından desteklenip desteklenmediğini belirten bir Boole değeri döndüren özel bir yöntem. Yöntemi, <xref:System.Array.Exists%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> Array öğesini geçtiği yöntemine bir çağrı sarar.  
  
- `HasSameName`, <xref:System.Array.Exists%2A?displayProperty=nameWithType> yönteme bir parametre olarak geçirilen özel <xref:System.Predicate%601> bir yöntem. Dizenin her üyesi, yöntem dönene `true`kadar yöntemine geçirilir. Yöntemi, isteğe bağlı bir takvimin adının `CalendarUtility` nesnenin gösterdiği takvimle aynı olup olmadığını belirler.  
  
- `DisplayDate`, iki parametre geçen aşırı yüklenmiş bir genel yöntem: ya da <xref:System.DateTime> `CalendarUtility` nesne tarafından <xref:System.DateTimeOffset> temsil edilen takvimde ifade edilecek bir veya değeri; ve biçimlendirme kuralları kullanılacak kültür. Bir tarihin dize gösterimini döndürme davranışındaki davranışı, hedef takvimin biçimlendirme kuralları kullanılacak kültürün desteklenip desteklenmediğini bağlıdır.  
  
 Bu örnekte bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değeri oluşturmak için kullanılan takvime bakılmaksızın, bu değer genellikle bir Gregoryen tarih olarak ifade edilir. Bunun nedeni, <xref:System.DateTime> ve <xref:System.DateTimeOffset> türlerinin herhangi bir takvim bilgisini korumidir. Dahili olarak, 1 Ocak 0001 gece yarısından beri geçen onay işareti sayısı olarak temsil edilir. Bu sayının yorumu takvime göre değişir. Çoğu kültürde varsayılan takvim, Gregoryen takvimidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
