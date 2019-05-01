---
title: System.DateTime Yöntemleri
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: 85af6f252362b811356d68a3ae220df2bb813882
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876778"
---
# <a name="systemdatetime-methods"></a>System.DateTime Yöntemleri
LINQ to SQL sorguları kullanmak, aşağıdaki LINQ to SQL desteklenen yöntem, işleçler ve özellikleri kullanılabilir. Yöntemi, işleci veya özelliği desteklenmeyen olduğunda, LINQ to SQL üyesi için SQL Server üzerinde yürütme çeviremez. Kodunuzda bu üyeleri kullanabilir, Transact-SQL veya veritabanından sonuçları alındıktan sonra sorgu çevrilir önce ancak bunlar değerlendirilmelidir.  
  
## <a name="supported-systemdatetime-members"></a>Desteklenen System.DateTime üyeleri  
 Nesne modeli ya da dış eşleme dosyası eşlenen sonra LINQ to SQL aşağıdaki çağırmanızı sağlar <xref:System.DateTime?displayProperty=nameWithType> to SQL sorgularında LINQ içinde üyeleri.  
  
|Desteklenen <xref:System.DateTime> yöntemleri|Desteklenen <xref:System.DateTime> işleçleri|Desteklenen <xref:System.DateTime> özellikleri|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a>LINQ to SQL tarafından desteklenmeyen üyeleri  
 Aşağıdaki üyeleri LINQ içinde SQL sorguları desteklenmez.  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a>Çeviri örnek yöntemi  
 SQL Server için göndermeden önce tüm yöntemleri LINQ to SQL tarafından desteklenen Transact-SQL çevrilir. Örneğin, aşağıdaki desenin göz önünde bulundurun.  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 Tanındığında, SQL Server için doğrudan bir çağrı çevrilir `DATEDIFF` işlev, şu şekilde:  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods tarih ve saat yöntemleri  
 Tarafından sunulan yöntemlerine ek olarak <xref:System.DateTime> yapısı, LINQ to SQL sunar ve aşağıdaki tablodan listelenen yöntemleri <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> tarih ve saat ile çalışmak için sınıf.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
