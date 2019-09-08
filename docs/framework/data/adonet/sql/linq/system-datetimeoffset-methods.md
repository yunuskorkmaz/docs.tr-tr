---
title: System.DateTimeOffset Yöntemleri
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 2e29cf02d4f7e8004782264bf940bb1faf393269
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781555"
---
# <a name="systemdatetimeoffset-methods"></a>System.DateTimeOffset Yöntemleri
Nesne modelinde veya dış eşleme dosyasında eşlendikten sonra LINQ to SQL, LINQ to SQL Sorgularınızdaki <xref:System.DateTimeOffset?displayProperty=nameWithType> yöntemlerin, işleçlerin ve özelliklerin çoğunu çağırabilmeniz için izin verir.  
  
 Desteklenmeyen tek Yöntemler <xref:System.Object?displayProperty=nameWithType> ,: `Finalize`, `GetHashCode` `GetType`, ve`MemberwiseClone`gibi LINQ to SQL sorgularının bağlamında anlamayan Devralınanlar. LINQ to SQL SQL Server yürütülmek üzere çevrilemediğinden bu yöntemler desteklenmez.  
  
> [!NOTE]
> Ortak dil çalışma zamanı (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> yapısı ve LINQ to SQL ile bir SQL `DATETIMEOFFSET` sütunuyla eşleme özelliği .NET Framework 3,5 SP1 veya daha fazlasını gerektirir. SQL `DATETIMEOFFSET` sütunu yalnızca Microsoft SQL Server 2008 ve sonraki bir sürümünde kullanılabilir.  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods tarih ve saat yöntemleri  
 <xref:System.DateTimeOffset> Yapı tarafından sunulan yöntemlerin yanı sıra, LINQ to SQL tarih ve saat ile çalışmaya yönelik <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> sınıftan aşağıdaki tabloda listelenen yöntemleri sunar.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
- [Nesne Modeli Oluşturma](creating-the-object-model.md)
- [SQL-CLR Tür Eşlemesi](sql-clr-type-mapping.md)
