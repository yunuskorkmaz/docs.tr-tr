---
title: System.TimeSpan Yöntemleri
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: dd693a64550293d6894e1d2abc3f651a53fc17fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126951"
---
# <a name="systemtimespan-methods"></a>System.TimeSpan Yöntemleri
Üye desteği <xref:System.TimeSpan?displayProperty=nameWithType> kullanmakta olduğunuz bir Microsoft SQL Server ve .NET Framework sürümlerinde büyük ölçüde bağlıdır.  
  
 Bir yöntemi, işleci veya özelliği desteklenmiyor.; LINQ to SQL üyesi için SQL Server üzerinde yürütme çeviremez anlamına gelir. Hala kodunuzda bu üyeleri kullanmanız mümkün olabilir. Ancak, sorgu Transact-SQL veya veritabanından sonuçları alındıktan sonra çevrilir önce bunlar değerlendirilmelidir.  
  
## <a name="previous-limitations"></a>Önceki sınırlamaları  
 .NET Framework 3.5 SP1'den önce .NET Framework sürümleri ile LINQ to SQL kullanırken SQL Server veritabanı alanlarına eşlenemez <xref:System.TimeSpan?displayProperty=nameWithType>. Ancak, işlemleri <xref:System.TimeSpan> desteklenmez <xref:System.TimeSpan> değerleri sağlayıcıdan döndürülen <xref:System.DateTime> çıkarma veya değişmez değer veya ilişkili bir değişkeni olarak bir ifade içinde tanıtılan.  
  
## <a name="supported-systemtimespan-member-support"></a>Desteklenen System.TimeSpan üye desteği

 Aşağıdaki LINQ to SQL desteklenen yöntem, işleçler ve özelliklerini, LINQ to SQL sorgularında kullanabilmeniz için kullanılabilir. Nesne modeli ya da dış eşleme dosyası eşlenen sonra LINQ to SQL birçok çağırmanızı sağlar <xref:System.TimeSpan?displayProperty=nameWithType> üyeleri, LINQ to SQL sorguları içinde.  
  
|Desteklenen <xref:System.TimeSpan> yöntemleri|Desteklenen <xref:System.TimeSpan> işleçleri|Desteklenen <xref:System.TimeSpan> özellikleri|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
>  Eşleme özelliğini <xref:System.TimeSpan?displayProperty=nameWithType> bir SQL `TIME` sütun LINQ to SQL ile .NET Framework 3.5 SP1 gerektirir ve sonraki süreci desteleyen. SQL `TIME` veri türüdür yalnızca Microsoft SQL Server 2008'de ve sonrasında kullanılabilir.  
  
### <a name="addition-and-subtraction"></a>Toplama ve çıkarma  
 Ancak CLR <xref:System.TimeSpan?displayProperty=nameWithType> türü, toplama ve çıkarma, SQL desteklemez `TIME` türü yenilenmez. SQL eşleştirildiğinde toplama ve çıkarma bunlar çalışırsanız, bu nedenle, LINQ to SQL sorgularında hata oluşturur `TIME` türü. Diğer değerlendirmeler SQL tarih ve saat türleri ile çalışmak için bulabilirsiniz [SQL-CLR tür eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
