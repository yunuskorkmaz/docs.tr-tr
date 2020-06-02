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
ms.openlocfilehash: 128ff4887601431f75981f13b51a11469e65d65c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290480"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Nasıl yapılır: Belirli bir Tarihten Haftanın Gününü Çıkarma
.NET Framework belirli bir tarih için haftanın sıralı gününü belirlemeyi ve belirli bir tarih için yerelleştirilmiş iş günü adını görüntülemeyi kolaylaştırır. Belirli bir tarihe karşılık gelen haftanın gününü gösteren numaralandırılmış bir değer <xref:System.DateTime.DayOfWeek%2A> veya <xref:System.DateTimeOffset.DayOfWeek%2A> özellikten kullanılabilir. Buna karşılık, hafta içi adının alınması, tarih ve saat değerinin yöntemi ya da yöntemi gibi bir biçimlendirme yöntemi çağırarak gerçekleştirilebilecek biçimlendirme işlemidir `ToString` <xref:System.String.Format%2A?displayProperty=nameWithType> . Bu konuda, bu biçimlendirme işlemlerinin nasıl gerçekleştirileceği gösterilmektedir.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Belirli bir tarihten itibaren haftanın gününü gösteren bir sayı ayıklamak için  
  
1. Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2. <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> Haftanın gününü gösteren bir değer almak için veya özelliğini kullanın <xref:System.DayOfWeek> .  
  
3. Gerekirse, (C# ' de) cast veya değeri (Visual Basic olarak) <xref:System.DayOfWeek> bir tamsayıya dönüştürün.  
  
 Aşağıdaki örnek, belirli bir tarihin haftanın gününü temsil eden bir tamsayı görüntüler.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Kısaltılmış iş günü adını belirli bir tarihten ayıklamak için  
  
1. Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2. Geçerli kültürün kısaltılmış iş günü adını veya belirli bir kültürü ayıklayabilirsiniz:  
  
    1. Geçerli kültür için kısaltılmış iş günü adını ayıklamak için, tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> örnek yöntemini çağırın ve "ddd" dizesini parametre olarak geçirin `format` . Aşağıdaki örnek yöntemine yapılan çağrıyı gösterir <xref:System.DateTime.ToString%28System.String%29> .  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Belirli bir kültür için kısaltılmış iş günü adını ayıklamak için tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemi çağırın. "Ddd" dizesini parametre olarak geçirin `format` . <xref:System.Globalization.CultureInfo> <xref:System.Globalization.DateTimeFormatInfo> Hafta içi adı parametre olarak almak istediğiniz kültürü temsil eden bir veya bir nesnesi geçirin `provider` . Aşağıdaki kod, <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> <xref:System.Globalization.CultureInfo> FR-fr kültürünü temsil eden bir nesnesi kullanarak yöntemine yapılan çağrıyı gösterir.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Belirli bir tarihten itibaren tam hafta içi adı ayıklamak için  
  
1. Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2. Geçerli kültürün veya belirli bir kültürün tam iş günü adını ayıklayabilirsiniz:  
  
    1. Geçerli kültürün hafta içi adını ayıklamak için, tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> örnek yöntemini çağırın ve "gggg" dizesini parametre olarak geçirin `format` . Aşağıdaki örnek yöntemine yapılan çağrıyı gösterir <xref:System.DateTime.ToString%28System.String%29> .  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Belirli bir kültürün hafta içi adını ayıklamak için tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemi çağırın. "Gggg" dizesini parametre olarak geçirin `format` . <xref:System.Globalization.CultureInfo> <xref:System.Globalization.DateTimeFormatInfo> Hafta içi adı parametre olarak almak istediğiniz kültürü temsil eden bir veya bir nesnesi geçirin `provider` . Aşağıdaki kod, <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> <xref:System.Globalization.CultureInfo> ES-es kültürünü temsil eden bir nesnesini kullanarak yöntemine yapılan çağrıyı gösterir.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Örnek  
 Örnek, <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> ve özelliklerinin yanı sıra, <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> belirli bir tarih için haftanın gününü, kısaltılmış iş günü adını ve tam gün adını temsil eden sayıyı almak için ve yöntemlerine ve yöntemlere yönelik çağrıları gösterir.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Tek tek diller .NET Framework tarafından belirtilen işlevleri çoğaltan veya tamamlayan işlevselliği sağlayabilir. Örneğin, Visual Basic iki işlevi de içerir:  
  
- `Weekday`, belirli bir tarihin haftanın gününü gösteren bir sayı döndürür. Haftanın ilk gününün sıra değerini bir kabul eder, ancak <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> özellik onu sıfır olarak değerlendirir.  
  
- `WeekdayName`Bu, geçerli kültürün belirli bir iş günü numarasına karşılık gelen haftanın adını döndürür.  
  
 Aşağıdaki örnek, Visual Basic `Weekday` ve işlevlerinin kullanımını gösterir `WeekdayName` .  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType>Belirli bir tarihin hafta içi adını almak için özelliği tarafından döndürülen değeri de kullanabilirsiniz. Bu, yalnızca <xref:System.Enum.ToString%2A> <xref:System.DayOfWeek> özelliği tarafından döndürülen değer üzerinde yöntemine bir çağrı gerektirir. Ancak, bu teknik, aşağıdaki örnekte gösterildiği gibi geçerli kültür için yerelleştirilmiş bir iş günü adı üretmez.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [Standart Tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md)
- [Özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)
