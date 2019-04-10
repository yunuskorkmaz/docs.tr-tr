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
ms.openlocfilehash: 224e8e82b7e71d7efbfdf0ce26cc4bd783cce3c8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313313"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Nasıl yapılır: Miladi Olmayan Takvimlerde Tarihleri Görüntüleme
<xref:System.DateTime> Ve <xref:System.DateTimeOffset> türleri Gregoryen takvim kendi varsayılan takvim olarak kullanın. Bu, tarih ve saat değerinin çağırma anlamına gelir `ToString` yöntemi, o tarih dize gösterimini görüntüler ve saat, tarih ve saat olsa bile Gregoryen takvimindeki başka bir takvimi kullanılarak oluşturuldu. Bu tarih ve saat değeri ile Fars takvimiyle oluşturmak için iki farklı şekilde kullanır, ancak yine de bu tarih ve saat değerleri Gregoryen takvimindeki görüntüler çağırdığında, aşağıdaki örnekte gösterilmiştir <xref:System.DateTime.ToString%2A> yöntemi. Bu örnek, belirli bir takvimde tarihi görüntülemek için iki yaygın olarak kullanılan ama yanlış teknikleri yansıtır.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 İki farklı teknikleri, belirli bir takvimde tarihi görüntülemek için kullanılabilir. İlk takvim belirli bir kültürün varsayılan takvimi olmasını gerektirir. İkinci herhangi bir takvim ile kullanılabilir.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Bir kültürün varsayılan takvim tarihini görüntülemek için  
  
1. Türetilen bir takvim nesnesinin örneğini oluşturma <xref:System.Globalization.Calendar> kullanılacak takvimi temsil eden sınıf.  
  
2. Örneği bir <xref:System.Globalization.CultureInfo> tarihini görüntülemek için biçimlendirmesi kullanılacak kültürü temsil eden nesne.  
  
3. Çağrı <xref:System.Array.Exists%2A?displayProperty=nameWithType> Takvim nesnesi tarafından döndürülen dizinin bir üyesi olup olmadığını belirlemek için yöntemi <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özelliği. Bu takvim için varsayılan takvim olarak verebilen gösterir <xref:System.Globalization.CultureInfo> nesne. Dizinin bir üyesi değilse, "Görüntü tarih içinde Any takvimi" bölümündeki yönergeleri izleyin.  
  
4. Takvim nesneye atamak <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> özelliği <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği.  
  
    > [!NOTE]
    >  <xref:System.Globalization.CultureInfo> Sınıfı de sahip bir <xref:System.Globalization.CultureInfo.Calendar%2A> özelliği. Ancak, salt okunur ve sabit değildir; atanan yeni varsayılan takvimi yansıtan değiştirmez <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> özelliği.  
  
5. Çağırın ya da <xref:System.DateTime.ToString%2A> veya <xref:System.DateTime.ToString%2A> yöntemi ve geçirin <xref:System.Globalization.CultureInfo> varsayılan takvimini, önceki adımda değiştirildiği nesne.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Herhangi bir takvimde tarihi görüntülemek için  
  
1. Türetilen bir takvim nesnesinin örneğini oluşturma <xref:System.Globalization.Calendar> kullanılacak takvimi temsil eden sınıf.  
  
2. Belirlemek, tarih ve saat öğeleri tarih ve saat değerini dize gösterimini görünmelidir.  
  
3. Takvim nesnenin görüntülemek istediğiniz her tarih ve saat öğesi için çağrı `Get`... yöntem. Aşağıdaki yöntemleri kullanılabilir:  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>, uygun takvimde yıl görüntülenecek.  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>, uygun Takvim ayı görüntülemek için.  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, uygun takvimindeki ayın gününü sayısını görüntülemek için.  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>, uygun takvimde günün saati görüntülenecek.  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>, uygun takvimde saatteki dakika görüntülenecek.  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>, uygun takvimde dakika içinde saniye görüntülenecek.  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A> , uygun takvimde ikinci milisaniye görüntülenecek.  
  
## <a name="example"></a>Örnek  
 Örneğin, iki farklı takvim kullanarak bir tarih görüntüler. Ar JO kültürün varsayılan takvim olarak Hicri takvimin tanımlama sonra tarihi görüntüler ve isteğe bağlı bir takvim olarak SK-IR kültür tarafından desteklenmeyen Fars takvimiyle kullanarak tarihi görüntüler.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Her <xref:System.Globalization.CultureInfo> nesnesi tarafından belirtilen bir veya daha fazla takvimler destekleyebilir <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> özelliği. Bunlardan biri kültürün varsayılan takvim olarak atanır ve salt okunur tarafından döndürülen <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> özelliği. Varsayılan olarak başka bir isteğe bağlı takvimleri belirlenebilir atayarak bir <xref:System.Globalization.Calendar> için bu takvimi temsil eden nesne <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği. Ancak, bazı takvimler, tarafından temsil edilen Fars takvimi gibi <xref:System.Globalization.PersianCalendar> sınıfı, herhangi bir kültür için isteğe bağlı takvimleri olarak etkinleştiremezsiniz.  
  
 Örnek bir yeniden kullanılabilir takvim yardımcı program sınıfı tanımlar `CalendarUtility`, belirli bir takvimden bir tarih dize gösterimini oluşturma ayrıntıların birçoğu işlemek için. `CalendarUtility` Sınıfı aşağıdaki üyelere sahiptir:  
  
-   Parametreli bir kurucu, tek parametresi bir <xref:System.Globalization.Calendar> tarih olduğu gösterilemeyecek kadar nesne. Bu sınıfın özel bir alan atanır.  
  
-   `CalendarExists`, bir takvim tarafından temsil edilen olup olmadığını gösteren bir Boole değeri döndürür, özel bir yöntem `CalendarUtility` nesnesi tarafından desteklenen <xref:System.Globalization.CultureInfo> yöntemine bir parametre olarak geçirilen nesne. Yönteme bir çağrı sarılır <xref:System.Array.Exists%2A?displayProperty=nameWithType> yöntemi için Geçiren <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> dizisi.  
  
-   `HasSameName`, atanan özel bir yöntem <xref:System.Predicate%601> bir parametre olarak geçirilen temsilci <xref:System.Array.Exists%2A?displayProperty=nameWithType> yöntemi. Yöntem dönene kadar dizinin her üyesini yöntemine geçirilen `true`. Yöntemi, isteğe bağlı bir takvim adı tarafından temsil edilen takvim ile aynı olup olmadığını belirler `CalendarUtility` nesne.  
  
-   `DisplayDate`, iki parametre geçirilen aşırı yüklenmiş bir genel yöntem: ya bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değeri tarafından temsil edilen takvimde ifade `CalendarUtility` ; nesne ve biçimlendirme kuralları kullanılacak kültürü. İçinde bir tarih dize gösterimini döndürme davranışını olup biçimlendirme kuralları kullanılacak kültürü tarafından hedef takvimin desteklenen bağlıdır.  
  
 Oluşturmak için kullanılan takvim bakılmaksızın bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değeri bu örnekte, değer genellikle bir Gregoryen tarihi olarak ifade edilir. Bunun nedeni, <xref:System.DateTime> ve <xref:System.DateTimeOffset> türleri herhangi bir takvim bilgi korumak değil. Dahili olarak, bu yana gece yarısı, 1 Ocak 0001 geçen tıklarının sayısını temsil edilir. Bu sayının yorumu Takvim üzerinde bağlıdır. Çoğu kültürde için varsayılan takvim Gregoryen takvim ' dir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek, bir System.Core.dll başvurusu gerektirir.  
  
 Kodu, csc.exe veya vb.exe kullanarak komut satırında derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulaması projesi şablonu içine koyun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
