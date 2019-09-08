---
title: SQL Server Veri Türleri ve ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 642fe0d541aca01d6ffb2d9279c4d0fa91eadb63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780853"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server Veri Türleri ve ADO.NET
SQL Server ve .NET Framework, farklı tür sistemlerine dayalıdır, bu da olası veri kaybına neden olabilir. Veri bütünlüğünü korumak için, SQL Server (<xref:System.Data.SqlClient>) için .NET Framework veri sağlayıcısı, SQL Server verileriyle çalışmak üzere türsüz erişimci yöntemleri sağlar. Veri türlerini belirtmek <xref:System.Data.SqlDbType> <xref:System.Data.SqlClient.SqlParameter> için sınıflardaki numaralandırmalar kullanabilirsiniz.  
  
 SQL Server ve .NET Framework veri türleri arasındaki veri türü eşlemelerini açıklayan bir tablo ve daha fazla bilgi için bkz. [SQL Server veri türü eşlemeleri](../sql-server-data-type-mappings.md).  
  
 SQL Server 2008; tarih ve saat, yapılandırılmış, yarı yapılandırılmış ve yapılandırılmamış verilerle çalışması için iş ihtiyaçlarını karşılamak üzere tasarlanan yeni veri türlerini tanıtır. Bunlar SQL Server 2008 Books Online 'da belgelenmiştir.  
  
 Uygulamanızda kullanıma sunulan SQL Server veri türleri, kullanmakta olduğunuz SQL Server sürümüne bağlıdır. Daha fazla bilgi için aşağıdaki tabloda SQL Server Books Online 'ın ilgili sürümüne bakın.  
  
 **Books Online SQL Server**  
  
1. [Veri türleri (veritabanı altyapısı)](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SqlTypes ve DataSet](sqltypes-and-the-dataset.md)  
 İçinde için `SqlTypes` tür desteğini açıklar. `DataSet`  
  
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
 `DataSet` Sınıfını ve tüm üyelerini açıklar.  
  
 <xref:System.Data.SqlTypes>  
 `SqlTypes` Ad alanını ve tüm üyelerini açıklar.  
  
 <xref:System.Data.SqlDbType>  
 `SqlDbType` Listelemeyi ve tüm üyelerini açıklar.  
  
 <xref:System.Data.DbType>  
 `DbType` Listelemeyi ve tüm üyelerini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türü Eşlemeleri](../sql-server-data-type-mappings.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../configuring-parameters-and-parameter-data-types.md)
- [Tablo Değerli Parametreler](table-valued-parameters.md)
- [SQL Server İkili ve Büyük Değerli Veriler](sql-server-binary-and-large-value-data.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
