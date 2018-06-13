---
title: 'Nasıl yapılır: Belirli bir Tarihten Haftanın Gününü Çıkarma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- DateTime.DayOfWeek property
- DateTime.ToString method
- dates [.NET Framework], retrieving week information
- DateTimeOffset.DayOfWeek property
- dates [.NET Framework], day of week
- Weekday function
- day of week [.NET Framework]
- extracting day of week
- weekday names
- WeekdayName function
- numbers [.NET Framework], day of week
- formatting [.NET Framework], time
- DateTimeOffset.ToString method
- full weekday names
ms.assetid: 1c9bef76-5634-46cf-b91c-9b9eb72091d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bd4066fe0a2d9f26505976c13ac80e03554e0aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575733"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Nasıl yapılır: Belirli bir Tarihten Haftanın Gününü Çıkarma
.NET Framework sıralı haftanın belirli bir tarih için belirlemek ve yerelleştirilmiş haftanın günü için belirli bir tarih görünen ad için kolaylaştırır. Belirli bir tarihe kadar karşılık gelen haftanın gününü gösteren bir Enum değeri kullanılabilir <xref:System.DateTime.DayOfWeek%2A> veya <xref:System.DateTimeOffset.DayOfWeek%2A> özelliği. Buna karşılık, haftanın günü adı alınırken tarih ve saat değerinin gibi bir biçimlendirme yöntemini çağırarak gerçekleştirilebilen bir biçimlendirme işlemdir `ToString` yöntemi veya <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi. Bu konu, bu biçimlendirme işlemlerini gerçekleştirme gösterir.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Belirli bir tarihten haftanın gününü gösteren bir sayı ayıklamak için  
  
1.  Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2.  Kullanım <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> almak için özelliğini bir <xref:System.DayOfWeek> haftanın gününü gösteren değer.  
  
3.  Gerekirse, atama (C# ') veya (Visual Basic'te) dönüştürmek <xref:System.DayOfWeek> bir tamsayı değeri.  
  
 Aşağıdaki örnek, belirli bir tarihten haftanın gününü temsil eden bir tamsayı görüntüler.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Belirli bir tarihten itibaren kısaltılmış haftanın günü adı ayıklanamıyor  
  
1.  Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2.  Geçerli kültür veya belirli bir kültür kısaltılmış haftanın günü adı ayıklayabilirsiniz:  
  
    1.  Geçerli kültür için kısaltılmış haftanın günü ad ayıklamak için tarih ve saat değerinin çağrısı <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> örnek yöntemi ve "ggg" dize olarak geçirin `format` parametresi. Aşağıdaki örnek çağrısı gösterilmektedir <xref:System.DateTime.ToString%28System.String%29> yöntemi.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2.  Belirli bir kültür için kısaltılmış haftanın günü ad ayıklamak için tarih ve saat değerinin çağrısı <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemi. Bir dizeyi "ggg" olarak geçirmek `format` parametresi. Ya da geçirmek bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.DateTimeFormatInfo> hafta içi adı olarak almak istediğiniz kültür temsil eden nesnesi `provider` parametresi. Aşağıdaki kod bir çağrı gösterilmektedir <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemini kullanarak bir <xref:System.Globalization.CultureInfo> fr-FR kültür temsil eden nesne.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Belirli bir tarihten itibaren tam haftanın günü adı ayıklanamıyor  
  
1.  Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2.  Tam haftanın günü adı geçerli kültürü veya belirli bir kültür ayıklayabilirsiniz:  
  
    1.  Geçerli kültür için haftanın günü ad ayıklamak için tarih ve saat değerinin çağrısı <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> örnek yöntemi ve "dddd" dize olarak geçirin `format` parametresi. Aşağıdaki örnek çağrısı gösterilmektedir <xref:System.DateTime.ToString%28System.String%29> yöntemi.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2.  Belirli bir kültür için haftanın günü ad ayıklamak için tarih ve saat değerinin çağrısı <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemi. Bir dizeyi "dddd" olarak geçirmek `format` parametresi. Ya da geçirmek bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.DateTimeFormatInfo> hafta içi adı olarak almak istediğiniz kültür temsil eden nesnesi `provider` parametresi. Aşağıdaki kod bir çağrı gösterilmektedir <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemini kullanarak bir <xref:System.Globalization.CultureInfo> es-ES kültür temsil eden nesne.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Örnek  
 Örnek çağrıları gösterir <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> özellikleri ve <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> haftanın, kısaltılmış haftanın günü adını ve tam haftanın günü adını gününü temsil eden sayı almak için yöntemleri bir Belirli tarih.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Tek tek dilleri yineleme veya tarafından sağlanan işlevleri tamamlayan işlevselliği sağlayabilir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Örneğin, Visual Basic iki tür işlevler içerir:  
  
-   `Weekday`, belirli bir tarihten haftanın gününü gösteren bir sayı döndürür. Ancak, biri için haftanın ilk günü sıra değerini dikkate <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> özelliği sıfır olarak dikkate alır.  
  
-   `WeekdayName`, döndüğü haftanın adını karşılık gelen geçerli kültürün belirli hafta içi günü sayıya.  
  
 Aşağıdaki örnek Visual Basic kullanımını göstermektedir `Weekday` ve `WeekdayName` işlevleri.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Tarafından döndürülen değer de kullanabilirsiniz <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> belirli bir tarihten haftanın günü adını almak için özellik. Bu sadece bir çağrı gerektirir <xref:System.Enum.ToString%2A> yöntemi <xref:System.DayOfWeek> özellik tarafından döndürülen değer. Ancak, aşağıdaki örnekte gösterildiği gibi bu teknik geçerli kültür için yerelleştirilen hafta içi adı üretmez.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
