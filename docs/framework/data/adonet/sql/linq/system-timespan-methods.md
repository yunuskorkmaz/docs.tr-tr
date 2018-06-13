---
title: System.TimeSpan yöntemleri
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: 2cb7201c113fe72ce03d0308ab8f97dca585e602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358323"
---
# <a name="systemtimespan-methods"></a>System.TimeSpan yöntemleri
Üye desteği <xref:System.TimeSpan?displayProperty=nameWithType> büyük ölçüde .NET Framework ve kullandığınız Microsoft SQL Server sürümlerinde bağlıdır.  
  
 Bir yöntemi, işleci veya özelliği desteklenmiyor; Bu üye için SQL Server üzerinde yürütme LINQ-SQL çeviremez anlamına gelir. Hala bu üyeler, kodunuzda kullanmak mümkün olabilir. Ancak, sorgu Transact-SQL veya veritabanından sonuçları alındıktan sonra çevrilmesi önce bunlar değerlendirilmelidir.  
  
## <a name="previous-limitations"></a>Önceki sınırlamaları  
 LINQ-SQL, .NET Framework 3.5 SP1 önce .NET Framework sürümleri ile kullanırken, SQL Server veritabanı alanlarına eşlenemiyor <xref:System.TimeSpan?displayProperty=nameWithType>. Ancak, üzerinde işlem <xref:System.TimeSpan> olduğundan desteklenmektedir <xref:System.TimeSpan> değerleri gelen döndürülmesi <xref:System.DateTime> çıkarma veya değişmez değer veya bağlı bir değişken olarak bir ifade halinde sunulan.  
  
## <a name="supported-systemtimespan-method-support"></a>Desteklenen System.TimeSpan yöntemi desteği  
 Aşağıdaki LINQ SQL desteklenen yöntem, işleçler ve özellikler, LINQ to SQL sorguları kullanmak için kullanılabilir. Nesne modeli ya da dış eşleme dosyası eşlenen sonra LINQ-SQL birçok çağrı sayesinde <xref:System.TimeSpan?displayProperty=nameWithType> üyeleri, LINQ to SQL sorguları içinde.  
  
|Desteklenen <xref:System.TimeSpan> yöntemleri|Desteklenen <xref:System.TimeSpan> işleçleri|Desteklenen <xref:System.TimeSpan> özellikleri|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<!--zz <xref:System.TimeSpan.MinValue%2A>-->|  
  
> [!NOTE]
>  Eşleme özelliğini <xref:System.TimeSpan?displayProperty=nameWithType> bir SQL `TIME` sütunu LINQ-SQL ile .NET Framework 3.5 SP1 gerektirir ve ötesine. SQL `TIME` veri türüdür yalnızca Microsoft SQL Server 2008 ve sonrasındaki kullanılabilir.  
  
### <a name="addition-and-subtraction"></a>Toplama ve çıkarma  
 Ancak CLR <xref:System.TimeSpan?displayProperty=nameWithType> türünü destekleyen toplama ve çıkarma, SQL `TIME` türünü desteklemez. SQL eşlendiğinde toplama ve çıkarma bunlar çalışırsanız, bu nedenle, LINQ to SQL sorguları hataları oluşturacak `TIME` türü. SQL tarih ve saat türleri ile çalışmak için diğer konular bulabilirsiniz [SQL CLR türü eşleme](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
