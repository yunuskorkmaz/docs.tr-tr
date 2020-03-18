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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138748"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Nasıl yapılır: Miladi Olmayan Takvimlerde Tarihleri Görüntüleme
Ve <xref:System.DateTime> <xref:System.DateTimeOffset> türleri varsayılan takvim olarak Gregoryen takvimini kullanır. Bu, tarih ve saat değerinin `ToString` yöntemini çağırmanın, o tarih ve saat başka bir takvim kullanılarak oluşturulmuş olsa bile, o tarih ve saatin Gregoryen takviminde dize gösterimini gösterdiği anlamına gelir. Bu, Farsça takvimle tarih ve saat değeri oluşturmak için iki farklı yol kullanan, ancak <xref:System.DateTime.ToString%2A> yöntemi aradığında Gregoryen takviminde yine de bu tarih ve saat değerlerini görüntüleyen aşağıdaki örnekte gösterilmiştir. Bu örnek, belirli bir takvimde tarihi görüntülemek için yaygın olarak kullanılan ancak yanlış iki tekniği yansıtır.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Tarihi belirli bir takvimde görüntülemek için iki farklı teknik kullanılabilir. İlki, takvimin belirli bir kültür için varsayılan takvim olmasını gerektirir. İkincisi herhangi bir takvimle kullanılabilir.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Bir kültürün varsayılan takvim tarihini görüntülemek için  
  
1. Kullanılacak takvimi temsil eden <xref:System.Globalization.Calendar> sınıftan türetilen bir takvim nesnesini anında anlayın.  
  
2. Tarihi görüntülemek için <xref:System.Globalization.CultureInfo> biçimlendirme kullanılacak olan kültürü temsil eden bir nesneyi anında görüntüleyin.  
  
3. Takvim <xref:System.Array.Exists%2A?displayProperty=nameWithType> nesnesinin <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özellik tarafından döndürülen dizinin bir üyesi olup olmadığını belirlemek için yöntemi arayın. Bu, takvimin <xref:System.Globalization.CultureInfo> nesne için varsayılan takvim olarak hizmet ebileceğini gösterir. Dizinin bir üyesi değilse, "Tarihi Takvimde Görüntülemek" bölümündeki yönergeleri izleyin.  
  
4. Takvim nesnesini, özellik <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> tarafından <xref:System.Globalization.DateTimeFormatInfo> döndürülen nesnenin özelliğine <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> atayın.  
  
    > [!NOTE]
    > Sınıfın <xref:System.Globalization.CultureInfo> da bir <xref:System.Globalization.CultureInfo.Calendar%2A> özelliği vardır. Ancak, salt okunur ve sabittir; <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> özelliğe atanan yeni varsayılan takvimi yansıtacak şekilde değişmez.  
  
5. Yöntemi <xref:System.DateTime.ToString%2A> veya yöntemi <xref:System.DateTime.ToString%2A> arayın ve varsayılan <xref:System.Globalization.CultureInfo> takvimi önceki adımda değiştirilen nesneyi geçirin.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Herhangi bir takvimde tarihi görüntülemek için  
  
1. Kullanılacak takvimi temsil eden <xref:System.Globalization.Calendar> sınıftan türetilen bir takvim nesnesini anında anlayın.  
  
2. Tarih ve saat değerinin dize gösteriminde hangi tarih ve saat öğelerinin görünmesi gerektiğini belirleyin.  
  
3. Görüntülemek istediğiniz her tarih ve saat öğesi için takvim `Get`nesnesinin ... Yöntem. Aşağıdaki yöntemler kullanılabilir:  
  
    - <xref:System.Globalization.Calendar.GetYear%2A>, yılı uygun takvimde görüntülemek için.  
  
    - <xref:System.Globalization.Calendar.GetMonth%2A>, ayı uygun takvimde görüntülemek için.  
  
    - <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, ayın gün sayısını uygun takvimde görüntülemek için.  
  
    - <xref:System.Globalization.Calendar.GetHour%2A>, günün saatini uygun takvimde görüntülemek için.  
  
    - <xref:System.Globalization.Calendar.GetMinute%2A>, dakikaları saat içinde uygun takvimde görüntülemek için.  
  
    - <xref:System.Globalization.Calendar.GetSecond%2A>, dakikadaki saniyeleri uygun takvimde görüntülemek için.  
  
    - <xref:System.Globalization.Calendar.GetMilliseconds%2A>, milisaniyeleri ikinci takvimde görüntülemek için.  
  
## <a name="example"></a>Örnek  
 Örnek, iki farklı takvim kullanarak bir tarih görüntüler. Hicri takvimi ar-JO kültürü için varsayılan takvim olarak tanımladıktan sonraki tarihi görüntüler ve fa-IR kültürü tarafından isteğe bağlı takvim olarak desteklenmeyen Farsça takvimi kullanarak tarihi görüntüler.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Her <xref:System.Globalization.CultureInfo> nesne, <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> özellik tarafından belirtilen bir veya daha fazla takvimi destekleyebilir. Bunlardan biri kültürün varsayılan takvimi olarak belirlenir ve salt <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> okunur özellik tarafından döndürülür. İsteğe bağlı takvimlerden biri, bu takvimi temsil <xref:System.Globalization.Calendar> eden bir nesneyi <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özellik tarafından döndürülen özelliğe atayarak varsayılan olarak atanabilir. Ancak, <xref:System.Globalization.PersianCalendar> sınıf tarafından temsil edilen Farsça takvim gibi bazı takvimler, herhangi bir kültür için isteğe bağlı takvimler olarak hizmet vermez.  
  
 Örnek, `CalendarUtility`belirli bir takvim kullanarak bir tarihin dize gösterimi oluşturma ayrıntılarının çoğunu işlemek için yeniden kullanılabilir bir takvim yardımcı sınıfı tanımlar. Sınıfın `CalendarUtility` aşağıdaki üyeleri vardır:  
  
- Tek parametresi tarihin temsil edildiği <xref:System.Globalization.Calendar> bir nesne olan parametreli bir oluşturucu. Bu sınıfın özel bir alana atanır.  
  
- `CalendarExists`, `CalendarUtility` nesne tarafından temsil edilen takvimin yönteme parametre olarak geçirilen <xref:System.Globalization.CultureInfo> nesne tarafından desteklenip desteklenmediğini belirten bir Boolean değeri döndüren özel bir yöntem. Yöntem, <xref:System.Array.Exists%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> diziyi geçtiği yönteme bir çağrı yıkıyor.  
  
- `HasSameName`, <xref:System.Predicate%601> <xref:System.Array.Exists%2A?displayProperty=nameWithType> yönteme parametre olarak geçirilen temsilciye atanan özel bir yöntemdir. Dizinin her üyesi yöntem dönene `true`kadar yönteme geçirilir. Yöntem, isteğe bağlı bir takvimin adının `CalendarUtility` nesne tarafından temsil edilen takvimle aynı olup olmadığını belirler.  
  
- `DisplayDate`, iki parametreden geçirilen aşırı yüklenen <xref:System.DateTime> genel <xref:System.DateTimeOffset> yöntem: `CalendarUtility` nesne tarafından temsil edilen takvimde ifade edilecek bir veya değer; ve biçimlendirme kurallarının kullanılacağı kültür. Bir tarihin dize gösterimini döndürmedeki davranışı, hedef takvimin biçimlendirme kuralları kullanılacak kültür tarafından desteklenip desteklenmediğine bağlıdır.  
  
 Bu örnekte bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değer oluşturmak için kullanılan takvimden bağımsız olarak, bu değer genellikle Gregoryen tarihi olarak ifade edilir. Bunun nedeni, <xref:System.DateTime> <xref:System.DateTimeOffset> ve türlerinin herhangi bir takvim bilgisini korumamasıdır. Dahili olarak, 1 Ocak 0001 gece yarısından bu yana geçen kene sayısı olarak temsil edilir. Bu sayının yorumlanması takvime bağlıdır. Çoğu kültür için varsayılan takvim Gregoryen takvimidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
