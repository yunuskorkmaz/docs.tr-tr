---
title: SQL Server veri türleri ve ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 878bbe41f259f1e50cd0a41669c7a352e78bc0f1
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46320887"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server veri türleri ve ADO.NET
SQL Server ve .NET Framework, olası veri kaybına neden farklı tür sistemlerde temel alır. SQL Server için .NET Framework veri sağlayıcısı veri bütünlüğünü korumak için (<xref:System.Data.SqlClient>) SQL Server verilerle çalışmak için belirlenmiş erişimci yöntemlerini sağlar. Numaralandırmalara kullanabileceğiniz <xref:System.Data.SqlDbType> belirtmek için sınıflar <xref:System.Data.SqlClient.SqlParameter> veri türleri.  
  
 Daha fazla bilgi ve verileri tanımlayan türü SQL Server ve .NET Framework veri türleri arasında eşlemeleri bir tablo için bkz: [SQL Server veri türü eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).  
  
 SQL Server 2008, yapılandırılmış, yarı yapılandırılmış ve yapılandırılmamış verileri tarih ve saat ile çalışmak için iş gereksinimlerini karşılamak için tasarlanan yeni veri türlerini tanıtır. Bu, SQL Server 2008 Books Online içinde belirtilmiştir.  
  
 Uygulamanızda kullanmak için mevcut SQL Server veri türleri, kullanmakta olduğunuz SQL Server'ın sürümüne bağlıdır. SQL Server Books Online'nın ilgili sürümü aşağıdaki tabloda daha fazla bilgi için bkz.  
  
 **SQL Server Çevrimiçi Kitapları**  
  
1.  [Veri türleri (veritabanı altyapısı)](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SqlTypes ve DataSet](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 Tür desteğini açıklar `SqlTypes` içinde `DataSet`.  
  
 [Null Değerleri İşleme](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 Null değerler ve üç değerli mantığı ile nasıl çalışacağınızı gösterir.  
  
 [GUID ve uniqueidentifier Değerlerini Karşılaştırma](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 GUID ve uniqueidentifier değerlerini SQL Server ve .NET Framework ile nasıl çalışılacağını gösterir.  
  
 [Tarih ve Saat Verileri](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 SQL Server 2008'de kullanıma sunulan yeni tarih ve saat veri türleri kullanmayı açıklar.  
  
 [Büyük UDT’ler](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 SQL Server 2008'de tanıtılan Udt'ler büyük değerinden veri almayı gösterir.  
  
 [SQL Server'da XML Verileri](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 SQL Server'dan alınan XML verileri ile nasıl çalışılacağını açıklar.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
