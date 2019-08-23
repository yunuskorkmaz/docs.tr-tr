---
title: System.TimeSpan Yöntemleri
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: ec27f8f17a6709efef1a8230b521778095ae1257
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947085"
---
# <a name="systemtimespan-methods"></a>System.TimeSpan Yöntemleri
İçin <xref:System.TimeSpan?displayProperty=nameWithType> üye desteği büyük ölçüde kullandığınız .NET Framework ve Microsoft SQL Server sürümlerine bağlıdır.  
  
 Bir yöntem, işleç veya özellik desteklenmiyorsa; LINQ to SQL, SQL Server yürütme için üyeyi çeviremediği anlamına gelir. Kodunuzda bu üyeleri yine de kullanabilirsiniz. Ancak, sorgu Transact-SQL ' e çevrilmeden veya sonuçlar veritabanından alındıktan sonra değerlendirilmelidir.  
  
## <a name="previous-limitations"></a>Önceki sınırlamalar  
 .NET Framework 3,5 SP1 'den önceki .NET Framework sürümleriyle LINQ to SQL kullanırken, SQL Server veritabanı alanlarını <xref:System.TimeSpan?displayProperty=nameWithType>ile eşleyemezsiniz. Ancak, değerler çıkarma <xref:System.TimeSpan> işleminden <xref:System.DateTime> döndürülebilecek <xref:System.TimeSpan> veya bir ifadenin bir sabit değer ya da bağlı değişken olarak tanıtıldığı için üzerinde işlemler desteklenir.  
  
## <a name="supported-systemtimespan-member-support"></a>Desteklenen System. TimeSpan üye desteği

 Aşağıdaki LINQ to SQL desteklenen yöntemler, işleçler ve Özellikler LINQ to SQL sorgularda kullanabileceğiniz şekilde kullanılabilir. Nesne modelinde veya dış eşleme dosyasında eşlendikten sonra, LINQ to SQL LINQ to SQL Sorgularınızdaki birçok <xref:System.TimeSpan?displayProperty=nameWithType> üyeyi çağırabilmeniz için izin verir.  
  
|Desteklenen <xref:System.TimeSpan> Yöntemler|Desteklenen <xref:System.TimeSpan> işleçler|Desteklenen <xref:System.TimeSpan> Özellikler|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
> LINQ to SQL ile bir SQL <xref:System.TimeSpan?displayProperty=nameWithType> `TIME` sütunuyla eşleme özelliği, .NET Framework 3,5 SP1 ve daha fazlasını gerektirir. SQL `TIME` veri türü yalnızca Microsoft SQL Server 2008 ve daha ötesi bir sürümünde kullanılabilir.  
  
### <a name="addition-and-subtraction"></a>Toplama ve çıkarma  
 CLR <xref:System.TimeSpan?displayProperty=nameWithType> türü ekleme ve çıkarma desteği sağlasa da, SQL `TIME` türü değildir. Bu nedenle, LINQ to SQL sorgularınız, SQL `TIME` türüne eşlendiklerinde ekleme ve çıkarma işlemi gerçekleştirmeye çalıştıklarında hatalar oluşturur. SQL [-CLR tür EŞLEMESINDE](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)SQL tarih ve saat türleriyle çalışmaya yönelik başka hususlar bulabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
