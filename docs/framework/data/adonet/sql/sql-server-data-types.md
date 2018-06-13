---
title: SQL Server veri türleri ve ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: da98ac72fab0bc3934cef79aeec9b12d003b6888
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363508"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server veri türleri ve ADO.NET
SQL Server ve .NET Framework olası veri kaybına yol açabilir farklı tür sistemlerde temel alır. Veri bütünlüğü, SQL Server için .NET Framework veri sağlayıcısı korumak için (<xref:System.Data.SqlClient>) SQL Server verilerle çalışmak için yazılan erişimci yöntemleri sağlar. Numaralandırmalara kullanabilirsiniz <xref:System.Data.SqlDbType> belirtmek için sınıflar <xref:System.Data.SqlClient.SqlParameter> veri türleri.  
  
 Daha fazla bilgi ve verileri tanımlayan SQL Server ve .NET Framework veri türleri arasındaki eşlemeleri yazın bir tablo için bkz: [SQL Server veri türü eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).  
  
 SQL Server 2008 yapılandırılmış, yarı yapılandırılmış ve yapılandırılmamış veri tarih ve saat ile çalışmak için iş gereksinimlerini karşılamak için tasarlanmış yeni veri türleri tanıtır. Bu SQL Server 2008 Books Online içinde belgelenmiştir.  
  
 Uygulamanızda kullanılabilir SQL Server veri türleri, kullanmakta olduğunuz SQL Server sürümüne bağlıdır. Daha fazla bilgi için SQL Server Books Online'nın ilgili sürümü aşağıdaki tabloda bakın.  
  
 **SQL Server Çevrimiçi Kitapları**  
  
1.  [Veri türleri (veritabanı altyapısı)](http://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SqlTypes ve DataSet](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 Türü desteğini açıklar `SqlTypes` içinde `DataSet`.  
  
 [Null Değerleri İşleme](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 Null değerler ve üç değerli mantığı ile nasıl çalışılacağı gösterir.  
  
 [GUID ve uniqueidentifier Değerlerini Karşılaştırma](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 SQL Server ve .NET Framework GUID ve uniqueidentifier değerlerle çalışma gösterir.  
  
 [Tarih ve Saat Verileri](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 SQL Server 2008'de sunulan yeni tarih ve saat veri türleri kullanmayı açıklar.  
  
 [Büyük UDT’ler](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 SQL Server 2008'de sunulan atama büyük değerinden veri almayı gösterir.  
  
 [SQL Server'da XML Verileri](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 SQL Server'dan alınan XML veri ile nasıl çalışılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Data.DataSet>  
 Açıklar `DataSet` sınıfı ve tüm üyeleri.  
  
 <xref:System.Data.SqlTypes>  
 Açıklar `SqlTypes` ad alanı ve tüm üyeleri.  
  
 <xref:System.Data.SqlDbType>  
 Açıklar `SqlDbType` numaralandırma ve tüm üyeleri.  
  
 <xref:System.Data.DbType>  
 Açıklar `DbType` numaralandırma ve tüm üyeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Veri Türü Eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Tablo Değerli Parametreler](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [SQL Server İkili ve Büyük Değerli Veriler](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
