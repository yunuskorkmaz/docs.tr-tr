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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084198"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Nasıl yapılır: Belirli bir Tarihten Haftanın Gününü Çıkarma
.NET Framework, belirli bir tarih için haftanın ordinal gününü belirlemeyi ve belirli bir tarih için yerelleştirilmiş hafta içi adını görüntülemeyi kolaylaştırır. Belirli bir tarihe karşılık gelen haftanın gününü gösteren numaralandırılmış bir <xref:System.DateTime.DayOfWeek%2A> değer, özellikten kullanılabilir. <xref:System.DateTimeOffset.DayOfWeek%2A> Buna karşılık, hafta içi adını almak, tarih ve saat değeri `ToString` yöntemi veya <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi gibi bir biçimlendirme yöntemi çağırılarak gerçekleştirilebilecek bir biçimlendirme işlemidir. Bu konu, bu biçimlendirme işlemlerinin nasıl gerçekleştirilini gösterir.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Belirli bir tarihten haftanın gününü gösteren bir sayı ayıklamak için  
  
1. Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2. Haftanın <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> gününü gösteren <xref:System.DayOfWeek> bir değer almak için özelliği veya özelliği kullanın.  
  
3. Gerekirse, dökümü (C#) veya <xref:System.DayOfWeek> değeri (Visual Basic'te) bir karşıcıya dönüştürün.  
  
 Aşağıdaki örnek, belirli bir tarihin haftanın gününü temsil eden bir tamsayı görüntüler.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Kısaltılmış hafta içi adını belirli bir tarihten ayıklamak için  
  
1. Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2. Geçerli kültürün veya belirli bir kültürün kısaltılmış hafta içi adını ayıklayabilirsiniz:  
  
    1. Geçerli kültür için kısaltılmış hafta içi adını ayıklamak için tarih <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> ve saat değerinin veya örnek yöntemini çağırın ve "ddd" dizesini `format` parametre olarak geçirin. Aşağıdaki örnekte <xref:System.DateTime.ToString%28System.String%29> yönteme çağrı gösterin.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Belirli bir kültür için kısaltılmış hafta içi adını ayıklamak için <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> tarih ve saat değerinin veya örnek yöntemini arayın. "ddd" dizesini `format` parametre olarak geçirin. Hafta içi <xref:System.Globalization.CultureInfo> adını <xref:System.Globalization.DateTimeFormatInfo> parametre olarak almak istediğiniz kültürü temsil eden `provider` bir veya nesneyi geçirin. Aşağıdaki kod fr-FR kültürünü <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> temsil <xref:System.Globalization.CultureInfo> eden bir nesne kullanarak yönteme bir çağrı göstermektedir.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Hafta içi adın tamamını belirli bir tarihten ayıklamak için  
  
1. Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.  
  
2. Geçerli kültürün veya belirli bir kültürün tam hafta içi adını ayıklayabilirsiniz:  
  
    1. Geçerli kültürün hafta içi adını ayıklamak için tarih ve <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> saat <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> değerinin veya örnek yöntemini çağırın ve `format` "dddd" dizesini parametre olarak geçirin. Aşağıdaki örnekte <xref:System.DateTime.ToString%28System.String%29> yönteme çağrı gösterin.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Belirli bir kültürün hafta içi adını ayıklamak için tarih <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> saat değerinin veya örnek yöntemini arayın. "dddd" dizesini `format` parametre olarak geçirin. Hafta içi <xref:System.Globalization.CultureInfo> adını <xref:System.Globalization.DateTimeFormatInfo> parametre olarak almak istediğiniz kültürü temsil eden `provider` bir veya nesneyi geçirin. Aşağıdaki kod, es-ES <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> kültürünü temsil <xref:System.Globalization.CultureInfo> eden bir nesne kullanarak yönteme yapılan çağrıyı göstermektedir.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Örnek  
 Örnek, <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> haftanın gününü, <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> kısaltılmış <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> hafta içi adını ve belirli bir tarihin tam hafta içi adını temsil eden sayıyı almak için yapılan aramaları ve özellikleri ve yöntemleri gösterir.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Tek tek diller,.NET Framework tarafından sağlanan işlevselliği yineleyen veya tamamlayan işlevsellik sağlayabilir. Örneğin, Visual Basic bu tür iki işlevi içerir:  
  
- `Weekday`, belirli bir tarihin haftanın gününü gösteren bir sayı döndürür. Bu haftanın ilk gününün ordinal değeri biri olarak kabul <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> ederken, özellik sıfır olarak kabul eder.  
  
- `WeekdayName`, belirli bir hafta içi numarasına karşılık gelen geçerli kültürde haftanın adını döndürür.  
  
 Aşağıdaki örnek, Visual Basic `Weekday` ve `WeekdayName` işlevlerin kullanımını göstermektedir.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Ayrıca, belirli bir tarihin <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> hafta içi adını almak için özellik tarafından döndürülen değeri de kullanabilirsiniz. Bu özellik tarafından döndürülen <xref:System.Enum.ToString%2A> <xref:System.DayOfWeek> değer üzerinde yöntem için yalnızca bir çağrı gerektirir. Ancak, bu teknik, aşağıdaki örnekte gösterildiği gibi, geçerli kültür için yerelleştirilmiş bir hafta içi adı üretmez.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
