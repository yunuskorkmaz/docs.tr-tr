---
title: SQL Server Veri Türleri ve ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: db4618ac624ea8401cab682a8c21d8f23c253d05
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155464"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server Veri Türleri ve ADO.NET

SQL Server ve .NET Framework, farklı tür sistemlerine dayalıdır, bu da olası veri kaybına neden olabilir. Veri bütünlüğünü korumak için, SQL Server () için .NET Framework Veri Sağlayıcısı, <xref:System.Data.SqlClient> SQL Server verileriyle çalışmak üzere türsüz erişimci yöntemleri sağlar. <xref:System.Data.SqlDbType>Veri türlerini belirtmek için sınıflardaki numaralandırmalar kullanabilirsiniz <xref:System.Data.SqlClient.SqlParameter> .  
  
 SQL Server ve .NET Framework veri türleri arasındaki veri türü eşlemelerini açıklayan bir tablo ve daha fazla bilgi için bkz. [SQL Server veri türü eşlemeleri](../sql-server-data-type-mappings.md).  
  
 SQL Server 2008; tarih ve saat, yapılandırılmış, yarı yapılandırılmış ve yapılandırılmamış verilerle çalışması için iş ihtiyaçlarını karşılamak üzere tasarlanan yeni veri türlerini tanıtır. Bunlar SQL Server 2008 Books Online 'da belgelenmiştir.  
  
 Uygulamanızda kullanıma sunulan SQL Server veri türleri, kullanmakta olduğunuz SQL Server sürümüne bağlıdır. Daha fazla bilgi için aşağıdaki tabloda SQL Server Books Online 'ın ilgili sürümüne bakın.  
  
 **SQL Server belgeleri**  
  
1. [Veri türleri (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [SqlTypes ve DataSet](sqltypes-and-the-dataset.md)  
 İçinde için tür desteğini açıklar `SqlTypes` `DataSet` .  
  
 [Null Değerleri İşleme](handling-null-values.md)  
 Null değerlerle ve üç değerli mantığın nasıl çalıştığını gösterir.  
  
 [GUID ve uniqueidentifier Değerlerini Karşılaştırma](comparing-guid-and-uniqueidentifier-values.md)  
 SQL Server ve .NET Framework GUID ve uniqueidentifier değerleriyle nasıl çalışabileceğinizi gösterir.  
  
 [Tarih ve Saat Verileri](date-and-time-data.md)  
 SQL Server 2008 ' de tanıtılan yeni tarih ve saat veri türlerinin nasıl kullanılacağını açıklar.  
  
 [Büyük UDT’ler](large-udts.md)  
 SQL Server 2008 ' de tanıtılan büyük değerden verilerin nasıl alınacağını gösterir.  
  
 [SQL Server'da XML Verileri](xml-data-in-sql-server.md)  
 SQL Server alınan XML verileriyle nasıl çalışabileceğinizi açıklar.  
  
## <a name="reference"></a>Başvuru  

 <xref:System.Data.DataSet>  
 `DataSet`Sınıfını ve tüm üyelerini açıklar.  
  
 <xref:System.Data.SqlTypes>  
 `SqlTypes`Ad alanını ve tüm üyelerini açıklar.  
  
 <xref:System.Data.SqlDbType>  
 Listelemeyi `SqlDbType` ve tüm üyelerini açıklar.  
  
 <xref:System.Data.DbType>  
 Listelemeyi `DbType` ve tüm üyelerini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türü Eşlemeleri](../sql-server-data-type-mappings.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../configuring-parameters-and-parameter-data-types.md)
- [Tablo Değerli Parametreler](table-valued-parameters.md)
- [SQL Server İkili ve Büyük Değerli Veriler](sql-server-binary-and-large-value-data.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
