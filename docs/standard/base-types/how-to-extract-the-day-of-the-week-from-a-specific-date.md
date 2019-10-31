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
ms.openlocfilehash: 771bd0276310eecb534fb80836faadb1a8aa10bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084198"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Nasıl yapılır: Belirli bir Tarihten Haftanın Gününü Çıkarma
.NET Framework belirli bir tarih için haftanın sıralı gününü belirlemeyi ve belirli bir tarih için yerelleştirilmiş iş günü adını görüntülemeyi kolaylaştırır. <xref:System.DateTime.DayOfWeek%2A> veya <xref:System.DateTimeOffset.DayOfWeek%2A> özelliğinden belirli bir tarihe karşılık gelen haftanın gününü gösteren numaralandırılmış bir değer. Buna karşılık, hafta içi adı alma, tarih ve saat değerinin `ToString` yöntemi veya <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi gibi bir biçimlendirme yöntemi çağırarak gerçekleştirilebilecek biçimlendirme işlemidir. Bu konuda, bu biçimlendirme işlemlerinin nasıl gerçekleştirileceği gösterilmektedir.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Belirli bir tarihten itibaren haftanın gününü gösteren bir sayı ayıklamak için  
  
1. Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2. Haftanın gününü gösteren bir <xref:System.DayOfWeek> değeri almak için <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> özelliğini kullanın.  
  
3. Gerekirse, cast (ın C#) veya convert (Visual Basic) <xref:System.DayOfWeek> değerini bir tamsayıya dönüştürür.  
  
 Aşağıdaki örnek, belirli bir tarihin haftanın gününü temsil eden bir tamsayı görüntüler.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Kısaltılmış iş günü adını belirli bir tarihten ayıklamak için  
  
1. Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2. Geçerli kültürün kısaltılmış iş günü adını veya belirli bir kültürü ayıklayabilirsiniz:  
  
    1. Geçerli kültür için kısaltılmış iş günü adını ayıklamak için, tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> örnek yöntemini çağırın ve "ddd" dizesini `format` parametresi olarak geçirin. Aşağıdaki örnek <xref:System.DateTime.ToString%28System.String%29> yöntemine yapılan çağrıyı gösterir.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Belirli bir kültür için kısaltılmış hafta içi adı ayıklamak üzere, tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemini çağırın. "Ddd" dizesini `format` parametresi olarak geçirin. İş günü adı `provider` parametresi olarak almak istediğiniz kültürü temsil eden bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.DateTimeFormatInfo> nesnesi geçirin. Aşağıdaki kod, fr-FR kültürünü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi kullanarak <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemine yapılan çağrıyı gösterir.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Belirli bir tarihten itibaren tam hafta içi adı ayıklamak için  
  
1. Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2. Geçerli kültürün veya belirli bir kültürün tam iş günü adını ayıklayabilirsiniz:  
  
    1. Geçerli kültürün hafta içi adını ayıklamak için, tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> örnek yöntemini çağırın ve "gggg" dizesini `format` parametresi olarak geçirin. Aşağıdaki örnek <xref:System.DateTime.ToString%28System.String%29> yöntemine yapılan çağrıyı gösterir.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Belirli bir kültürün hafta içi adını ayıklamak için tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemini çağırın. "Gggg" dizesini `format` parametresi olarak geçirin. İş günü adı `provider` parametresi olarak almak istediğiniz kültürü temsil eden bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.DateTimeFormatInfo> nesnesi geçirin. Aşağıdaki kod, ES-ES kültürünü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi kullanarak <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemine yapılan çağrıyı gösterir.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Örnek  
 Örnek, <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> özelliklerine ve <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> yöntemlerine, haftanın gününü, kısaltılmış iş günü adını ve belirli bir tarih için tam gün adını temsil eden sayıyı almak için kullanılan çağrıları gösterir.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Tek tek diller .NET Framework tarafından belirtilen işlevleri çoğaltan veya tamamlayan işlevselliği sağlayabilir. Örneğin, Visual Basic iki işlevi de içerir:  
  
- `Weekday`, belirli bir tarihin haftanın gününü gösteren bir sayı döndürür. Haftanın ilk gününün sıra değerini bir olarak değerlendirir, <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> özelliği bunu sıfır olarak değerlendirir.  
  
- geçerli kültürün belirli bir iş günü numarasına karşılık gelen haftanın adını döndüren `WeekdayName`.  
  
 Aşağıdaki örnek Visual Basic `Weekday` ve `WeekdayName` işlevlerinin kullanımını gösterir.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Belirli bir tarihin hafta içi adını almak için <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> özelliği tarafından döndürülen değeri de kullanabilirsiniz. Bu, özelliği tarafından döndürülen <xref:System.DayOfWeek> değerindeki <xref:System.Enum.ToString%2A> yöntemine yönelik bir çağrı gerektirir. Ancak, bu teknik, aşağıdaki örnekte gösterildiği gibi geçerli kültür için yerelleştirilmiş bir iş günü adı üretmez.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
