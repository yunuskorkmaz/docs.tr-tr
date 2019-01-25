---
title: 'Nasıl yapılır: Belirli bir tarihten haftanın gününü çıkarma'
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
ms.openlocfilehash: e2c422a75244302ae6433af933995b00bdfaa061
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537978"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Nasıl yapılır: Belirli bir tarihten haftanın gününü çıkarma
.NET Framework sıralı için belirli bir tarihten haftanın gününü belirlemek için ve belirli bir tarih için yerelleştirilmiş gün adını görüntülemek için kolaylaştırır. Belirli bir tarihe kadar karşılık gelen haftanın gününü gösteren numaralandırılmış değer kullanılabilir <xref:System.DateTime.DayOfWeek%2A> veya <xref:System.DateTimeOffset.DayOfWeek%2A> özelliği. Buna karşılık, haftanın günü adı alınırken tarih ve saat değerinin gibi bir biçimlendirme yöntemi çağırarak gerçekleştirilebilen bir biçimlendirme işlemdir `ToString` yöntemi veya <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi. Bu konu, bunlar biçimlendirme işlemleri gerçekleştirmeyi gösterir.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Belirli bir tarihten haftanın gününü gösteren bir sayı ayıklamak için  
  
1.  Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2.  Kullanım <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> almak için özellik bir <xref:System.DayOfWeek> haftanın gününü gösteren değer.  
  
3.  Gerekirse, dönüştürme (C# ') veya (Visual Basic'te) <xref:System.DayOfWeek> bir tamsayı değeri.  
  
 Aşağıdaki örnek, belirli bir tarihten haftanın gününü temsil eden bir tamsayı görüntüler.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Belirli bir tarihten itibaren kısaltılmış gün adını ayıklamak için  
  
1.  Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2.  Geçerli kültürün veya belirli bir kültürün kısaltılmış gün adını Ayıkla:  
  
    1.  Tarih ve saat değerinin geçerli kültür için kısaltılmış gün adını Ayıkla çağrısı <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> örnek yöntemi ve "ddd" dize olarak geçirin `format` parametresi. Aşağıdaki örnek yapılan çağrıyı gösterir <xref:System.DateTime.ToString%28System.String%29> yöntemi.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2.  Tarih ve saat değerinin belirli bir kültür için kısaltılmış gün adını Ayıkla çağrısı <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemi. "Ddd" dize olarak geçirin `format` parametresi. Ya da başarılı bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.DateTimeFormatInfo> haftanın günü adı olarak almak istediğiniz kültürü temsil eden bir nesne `provider` parametresi. Aşağıdaki kod bir çağrıyı gösterir <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemini kullanarak bir <xref:System.Globalization.CultureInfo> fr-FR kültürü temsil eden nesne.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Belirli bir tarihten itibaren tam haftanın günü adı ayıklanamıyor  
  
1.  Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2.  Tam haftanın günü adı geçerli kültürün veya belirli bir kültürün ayıklayabilirsiniz:  
  
    1.  Tarih ve saat değerinin haftanın günü adı geçerli kültür için ayıklamak için çağrı <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> yöntemi örneği ve ' % s'dizesi "dddd" olarak geçirin `format` parametresi. Aşağıdaki örnek yapılan çağrıyı gösterir <xref:System.DateTime.ToString%28System.String%29> yöntemi.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2.  Tarih ve saat değerinin haftanın günü adı belirli bir kültür için ayıklamak için çağrı <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemi. ' % S'dizesi "dddd" olarak geçirin `format` parametresi. Ya da başarılı bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.DateTimeFormatInfo> haftanın günü adı olarak almak istediğiniz kültürü temsil eden bir nesne `provider` parametresi. Aşağıdaki kod bir çağrıyı gösterir <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemini kullanarak bir <xref:System.Globalization.CultureInfo> es-ES kültürü temsil eden nesne.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Örnek  
 Çağrısına örnekte gösterildiği <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> özellikleri ve <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> haftanın kısaltılmış gün adını ve tam haftanın günü adı gününü temsil eden sayı almak için yöntemler bir Belirli tarih.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Tek tek dillerin yineleme veya tarafından sağlanan işlevselliği tamamlayan işlevselliği sağlayabilir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Örneğin, Visual Basic böyle iki işlevin içerir:  
  
-   `Weekday`, belirli bir tarihten haftanın gününü gösteren bir sayı döndürür. Oysa sıralı değeri, biri için haftanın ilk gününü dikkate <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> özelliği sıfır olarak değerlendirir.  
  
-   `WeekdayName`, döndüren hafta adını karşılık gelen geçerli kültürün belirli hafta içi sayıya.  
  
 Aşağıdaki örnek Visual Basic kullanışını `Weekday` ve `WeekdayName` işlevleri.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Tarafından döndürülen değer de kullanabilirsiniz <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> belirli bir tarihten haftanın günü adını almak için özellik. Bu yalnızca bir çağrı gerektirir <xref:System.Enum.ToString%2A> metodunda <xref:System.DayOfWeek> özellik tarafından döndürülen değer. Ancak aşağıdaki örnekte gösterildiği gibi bu teknik geçerli kültür için yerelleştirilmiş haftanın günü adları oluşturmaz.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
