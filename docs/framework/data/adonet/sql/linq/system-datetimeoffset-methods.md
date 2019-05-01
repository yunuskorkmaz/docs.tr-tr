---
title: System.DateTimeOffset Yöntemleri
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 288a0d99feecdeccc0d215ec3c14ec31bb3ccb54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876908"
---
# <a name="systemdatetimeoffset-methods"></a>System.DateTimeOffset Yöntemleri
Nesne modeli ya da dış eşleme dosyası eşlenen sonra LINQ to SQL çoğunu çağırmanızı sağlar <xref:System.DateTimeOffset?displayProperty=nameWithType> yöntemleri, işleçler ve LINQ içinde özellikleri SQL sorguları.  
  
 Desteklenmeyen yalnızca bu devralınan gelen yöntemlerdir <xref:System.Object?displayProperty=nameWithType> , mantıklı değildir LINQ bağlamında SQL sorguları gibi: `Finalize`, `GetHashCode`, `GetType`, ve `MemberwiseClone`. LINQ to SQL için SQL Server üzerinde yürütme çevirmek olamaz çünkü bu yöntemler desteklenmez.  
  
> [!NOTE]
>  Ortak dil çalışma zamanı (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> yapısı ve bir SQL eşleme özelliğini `DATETIMEOFFSET` sütun LINQ to SQL ile .NET Framework 3.5 SP1 gerektirir veya sonrasını. SQL `DATETIMEOFFSET` sütundur yalnızca Microsoft SQL Server 2008'de ve sonrasında kullanılabilir.  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods tarih ve saat yöntemleri  
 Tarafından sunulan yöntemlerine ek olarak <xref:System.DateTimeOffset> yapısı, LINQ to SQL sunar ve aşağıdaki tablodan listelenen yöntemleri <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> tarih ve saat ile çalışmak için sınıf.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
