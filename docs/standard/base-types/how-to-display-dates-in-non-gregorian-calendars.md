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
ms.openlocfilehash: 8d02b74f63ec5b6260679ae4cea04791681ec238
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523922"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Nasıl yapılır: Miladi Olmayan Takvimlerde Tarihleri Görüntüleme
<xref:System.DateTime>Ve <xref:System.DateTimeOffset> türleri varsayılan takvim olarak Gregoryen takvimi kullanır. Bu, bir tarih ve saat değerinin yönteminin, bu tarih ve saat `ToString` başka bir takvim kullanılarak oluşturulmuş olsa bile, Gregoryen takvimdeki tarih ve saatin dize gösterimini gösterdiği anlamına gelir. Bu, Farsça takvimi ile bir tarih ve saat değeri oluşturmak için iki farklı yol kullanan aşağıdaki örnekte gösterilmiştir, ancak yine de bu tarih ve saat değerlerini, yöntemi çağırdığında Gregoryen takviminde görüntüler <xref:System.DateTime.ToString%2A> . Bu örnek, belirli bir takvimdeki tarihi görüntülemek için yaygın olarak kullanılan iki ancak yanlış tekniği yansıtır.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Belirli bir takvimdeki tarihi göstermek için iki farklı teknik kullanılabilir. İlki, takvimin belirli bir kültürün varsayılan takvimi olmasını gerektirir. İkincisi herhangi bir takvimle birlikte kullanılabilir.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Bir kültürün varsayılan takvim tarihini görüntülemek için  
  
1. Kullanılacak takvimi temsil eden sınıftan türetilmiş bir takvim nesnesi örneği oluşturun <xref:System.Globalization.Calendar> .  
  
2. <xref:System.Globalization.CultureInfo>Tarih görüntülemek için biçimlendirme kullanılacak kültürü temsil eden bir nesne oluşturun.  
  
3. <xref:System.Array.Exists%2A?displayProperty=nameWithType>Takvim nesnesinin, özelliği tarafından döndürülen dizinin bir üyesi olup olmadığını anlamak için yöntemini çağırın <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> . Bu, takvimin nesne için varsayılan takvim olarak işlev görebilir olduğunu gösterir <xref:System.Globalization.CultureInfo> . Dizinin bir üyesi değilse, "herhangi bir takvime tarihi görüntüleme" bölümündeki yönergeleri izleyin.  
  
4. Takvim nesnesini, <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> <xref:System.Globalization.DateTimeFormatInfo> özelliği tarafından döndürülen nesnenin özelliğine atayın <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> .  
  
    > [!NOTE]
    > <xref:System.Globalization.CultureInfo>Sınıfın Ayrıca bir özelliği de vardır <xref:System.Globalization.CultureInfo.Calendar%2A> . Ancak, salt okunurdur ve sabittir; özelliğe atanmış olan yeni varsayılan takvimi yansıtacak şekilde değişmez <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> .  
  
5. <xref:System.DateTime.ToString%2A>Ya da <xref:System.DateTime.ToString%2A> yöntemini çağırın ve <xref:System.Globalization.CultureInfo> önceki adımda varsayılan takvimi değiştirilmiş olan nesneyi geçirin.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Herhangi bir takvimde tarihi görüntülemek için  
  
1. Kullanılacak takvimi temsil eden sınıftan türetilmiş bir takvim nesnesi örneği oluşturun <xref:System.Globalization.Calendar> .  
  
2. Tarih ve saat değerinin dize gösteriminde hangi tarih ve saat öğelerinin görüneceğini belirleme.  
  
3. Göstermek istediğiniz her bir tarih ve saat öğesi için, takvim nesnesinin... öğesini çağırın `Get` . yöntemidir. Aşağıdaki yöntemler kullanılabilir:  
  
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
  
 Her <xref:System.Globalization.CultureInfo> nesne, özelliği tarafından belirtilen bir veya daha fazla takvimi destekleyebilir <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> . Bunlardan biri, kültürün varsayılan takvimi olarak atanır ve salt okunurdur özelliği tarafından döndürülür <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> . İsteğe bağlı takvimlerin bir diğeri, <xref:System.Globalization.Calendar> Bu takvimi temsil eden bir nesne <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> , özelliği tarafından döndürülen özelliğe atanarak varsayılan olarak belirlenebilir <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> . Ancak, sınıf tarafından temsil edilen Farsça takvimi gibi bazı takvimler, <xref:System.Globalization.PersianCalendar> herhangi bir kültür için isteğe bağlı takvimler olarak görev almaz.  
  
 Örnek, `CalendarUtility` belirli bir takvimi kullanarak tarihin dize gösterimini oluşturma ayrıntılarının çoğunu işlemek için yeniden kullanılabilir bir takvim yardımcı sınıfı tanımlar. `CalendarUtility`Sınıfı aşağıdaki üyelere sahiptir:  
  
- Tek parametresi, bir tarihin temsil edildiği bir nesne olan parametreli bir Oluşturucu <xref:System.Globalization.Calendar> . Bu, sınıfının özel bir alanına atanır.  
  
- `CalendarExists`, nesne tarafından temsil edilen takvimin `CalendarUtility` <xref:System.Globalization.CultureInfo> bir parametre olarak yönteme geçirilen nesne tarafından desteklenip desteklenmediğini belirten bir Boole değeri döndüren özel bir yöntem. Yöntemi, <xref:System.Array.Exists%2A?displayProperty=nameWithType> Array öğesini geçtiği yöntemine bir çağrı sarar <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> .  
  
- `HasSameName`, <xref:System.Predicate%601> yönteme bir parametre olarak geçirilen özel bir yöntem <xref:System.Array.Exists%2A?displayProperty=nameWithType> . Dizenin her üyesi, yöntem dönene kadar yöntemine geçirilir `true` . Yöntemi, isteğe bağlı bir takvimin adının nesnenin gösterdiği takvimle aynı olup olmadığını belirler `CalendarUtility` .  
  
- `DisplayDate`, iki parametre geçen aşırı yüklenmiş bir genel yöntem: ya da <xref:System.DateTime> <xref:System.DateTimeOffset> nesne tarafından temsil edilen takvimde ifade edilecek bir veya değeri `CalendarUtility` ; ve biçimlendirme kuralları kullanılacak kültür. Bir tarihin dize gösterimini döndürme davranışındaki davranışı, hedef takvimin biçimlendirme kuralları kullanılacak kültürün desteklenip desteklenmediğini bağlıdır.  
  
 Bu örnekte bir veya değeri oluşturmak için kullanılan takvime bakılmaksızın <xref:System.DateTime> <xref:System.DateTimeOffset> , bu değer genellikle bir Gregoryen tarih olarak ifade edilir. Bunun nedeni, <xref:System.DateTime> ve <xref:System.DateTimeOffset> türlerinin herhangi bir takvim bilgisini korumidir. Dahili olarak, 1 Ocak 0001 gece yarısından beri geçen onay işareti sayısı olarak temsil edilir. Bu sayının yorumu takvime göre değişir. Çoğu kültürde varsayılan takvim, Gregoryen takvimidir.
