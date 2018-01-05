---
title: "Nasıl yapılır: Miladi Olmayan Takvimlerde Tarihleri Görüntüleme"
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
- formatting [.NET Framework], dates
- dates [.NET Framework], formatting
- calendars [.NET Framework], displaying dates
- displaying date and time data
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1a9e45fe43e38be3c618df37a639d63a6a0a5349
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Nasıl yapılır: Miladi Olmayan Takvimlerde Tarihleri Görüntüleme
<xref:System.DateTime> Ve <xref:System.DateTimeOffset> türleri Gregoryen takvim kendi varsayılan takvim olarak kullanın. Bu tarih ve saat değerinin çağırma yani `ToString` yöntemi, tarihin dize gösterimini görüntüler ve saati, tarih ve saat olsa bile Gregoryen takvim, başka bir takvim kullanılarak oluşturulmuş. Bu tarih ve saat değeri ile Farsça takvim oluşturmak için iki farklı şekilde kullanır, ancak hala çağırdığında Gregoryen takvim bu tarih ve saat değerleri görüntüler aşağıdaki örnekte gösterilmiştir <xref:System.DateTime.ToString%2A> yöntemi. Bu örnek belirli bir takvim tarihi görüntüleme için iki yaygın olarak kullanılan ancak yanlış teknikleri yansıtır.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 İki farklı teknikleri, belirli bir takvimde tarihini görüntülemek için kullanılabilir. İlk takvim belirli bir kültür için varsayılan takvim olmasını gerektirir. İkinci bir takvim ile kullanılabilir.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Bir kültürün varsayılan takvim tarihini görüntülemek için  
  
1.  Türetilen bir takvim nesnesi <xref:System.Globalization.Calendar> kullanılacak takvimi temsil eden sınıf.  
  
2.  Örneği bir <xref:System.Globalization.CultureInfo> tarihini görüntülemek için biçimlendirmesini kullanılacak kültürü temsil eden nesne.  
  
3.  Çağrı <xref:System.Array.Exists%2A?displayProperty=nameWithType> Takvim nesnesi tarafından döndürülen dizi üyesi olup olmadığının yöntemi <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> özelliği. Bu takvimi varsayılan takvim olarak hizmet verebilir gösterir <xref:System.Globalization.CultureInfo> nesnesi. Dizinin bir üyesi değilse, "Görünen tarih içinde herhangi Takvim" bölümündeki yönergeleri izleyin.  
  
4.  Takvim nesnesine atama <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> özelliği <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği.  
  
    > [!NOTE]
    >  <xref:System.Globalization.CultureInfo> Sınıfı ayrıca sahip bir <xref:System.Globalization.CultureInfo.Calendar%2A> özelliği. Ancak, salt okunur ve sabit değildir; atanan yeni varsayılan takvim yansıtacak şekilde değiştirmez <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> özelliği.  
  
5.  Ya da çağrısı <xref:System.DateTime.ToString%2A> veya <xref:System.DateTime.ToString%2A> yöntemi ve bu geçirin <xref:System.Globalization.CultureInfo> varsayılan takvimini, önceki adımda değiştirildiği nesnesi.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Herhangi bir takvimde tarihi görüntülemek için  
  
1.  Türetilen bir takvim nesnesi <xref:System.Globalization.Calendar> kullanılacak takvimi temsil eden sınıf.  
  
2.  Hangi tarih belirlemek ve süresi öğelerini tarih ve saat değeri dize gösterimini görünmelidir.  
  
3.  Takvim nesnenin görüntülenmesini istediğiniz her tarih ve saat öğesi için arama `Get`... yöntem. Aşağıdaki yöntemleri kullanılabilir:  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>, uygun takvim yılı görüntülemek için.  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>, uygun Takvim ayı görüntülemek için.  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, uygun takvimde ayın günü sayısını görüntülemek için.  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>, uygun takvimde günün saati görüntülemek için.  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>, uygun takvimindeki saatteki dakika görüntülenecek.  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>, uygun takvimindeki dakika içinde saniye görüntülemek için.  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A>, uygun takvimindeki ikinci milisaniye görüntülenecek.  
  
## <a name="example"></a>Örnek  
 Örneğin, iki farklı takvimler kullanma tarihi görüntüler. Ar-JO kültür için varsayılan takvim olarak Hicri takvimin tanımlama sonra tarihi görüntüler ve isteğe bağlı bir takvim olarak fa IR kültür tarafından desteklenmeyen Farsça takvimden tarihi görüntüler.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Her <xref:System.Globalization.CultureInfo> nesnesi tarafından belirtilen bir veya daha fazla takvimleri destekleyebilmesi <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> özelliği. Bunlardan birini kültürün varsayılan takvim olarak atanır ve salt okunur tarafından döndürülen <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> özelliği. Varsayılan olarak başka bir isteğe bağlı takvimleri belirlenebilir atayarak bir <xref:System.Globalization.Calendar> bu takvime temsil eden nesnesi <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> özellik tarafından döndürülen <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği. Ancak, bazı takvimler, tarafından temsil edilen Farsça takvim gibi <xref:System.Globalization.PersianCalendar> sınıfı, tüm kültür için isteğe bağlı takvimleri olarak sunmaz.  
  
 Örneği yeniden kullanılabilir takvim yardımcı sınıf tanımlar `CalendarUtility`, belirli bir takvimden bir tarih dize gösterimini oluşturmanın ayrıntılarına işlemek için. `CalendarUtility` Sınıfı aşağıdaki üyeleri sahiptir:  
  
-   Tek parametresi parametreli Oluşturucusu bir <xref:System.Globalization.Calendar> bir tarih olduğu gösterilemeyecek kadar nesnesi. Bu sınıf için bir özel alan atanır.  
  
-   `CalendarExists`, Takvim tarafından temsil edilen olup olmadığını gösteren bir Boole değeri döndürür özel bir yöntem `CalendarUtility` nesnesi tarafından desteklenen <xref:System.Globalization.CultureInfo> yönteme parametre olarak geçirilen nesne. Yöntem çağrısı sarmalar <xref:System.Array.Exists%2A?displayProperty=nameWithType> geçirir, yöntem, <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> dizi.  
  
-   `HasSameName`, atanan özel bir yöntem <xref:System.Predicate%601> bir parametre olarak geçirilen temsilci <xref:System.Array.Exists%2A?displayProperty=nameWithType> yöntemi. Yöntem dönene kadar her bir üyesi dizi yönteme geçirilen `true`. Yöntemi, isteğe bağlı bir takvim adını tarafından temsil edilen takvim ile aynı olup olmadığını belirler `CalendarUtility` nesnesi.  
  
-   `DisplayDate`, iki parametreye geçirilen aşırı yüklenmiş bir genel yöntem: ya bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değeri tarafından temsil edilen takvimindeki express `CalendarUtility` nesnesi; ve biçimlendirme kuralları kullanılacak kültür. Bir tarih dize gösterimini döndürme içinde davranışını olup biçimlendirme kuralları kullanılacak kültür tarafından hedef Takvim desteklenen bağlıdır.  
  
 Oluşturmak için kullanılan takvim bakılmaksızın bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> değeri bu örnekte, değer genellikle Miladi ifade edilir. Bunun nedeni, <xref:System.DateTime> ve <xref:System.DateTimeOffset> türleri herhangi bir takvim bilgi koruma değil. Dahili olarak, bunlar 0001 gece yarısından 1 Ocak bu yana geçen çizgilerine sayı olarak temsil edilir. Bu sayıyı yorumu takvimde bağlıdır. Çoğu kültürler için varsayılan takvim Gregoryen takvim ' dir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek, bir başvuru System.Core.dll gerektirir.  
  
 Kodu, csc.exe veya vb.exe kullanarak komut satırında derleyin. Kodu [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] içinde derlemek için, bir konsol uygulaması projesi şablonu içine koyun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
