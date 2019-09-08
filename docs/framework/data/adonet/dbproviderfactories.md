---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: e3ea9e3d083314f8df25f9edadbd1a18f1227293
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784095"
---
# <a name="dbproviderfactories"></a>DbProviderFactories
Ad <xref:System.Data.Common> alanı, belirli veri kaynaklarıyla <xref:System.Data.Common.DbProviderFactory> çalışacak örnekler oluşturmak için sınıflar sağlar. Bir <xref:System.Data.Common.DbProviderFactory> örnek oluşturup veri sağlayıcısına `DbProviderFactory` ilişkin bilgileri geçirdiğinizde, sağlandığı bilgilere göre döndürülecek doğru ve kesin belirlenmiş bağlantı nesnesini belirleyebilir.  
  
 .NET Framework sürüm 4 ' ten başlayarak, <xref:System.Data.Odbc>, ve <xref:System.Data.OracleClient> gibi <xref:System.Data.OleDb> <xref:System.Data.SqlClient>veri sağlayıcıları artık Machine. config dosyasında listelenmemiştir, ancak özel sağlayıcılar burada listelenmeye devam edecektir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Fabrika Modeline Genel Bakış](factory-model-overview.md)  
 Fabrika tasarımı düzenine ve programlama arabirimine genel bir bakış sağlar.  
  
 [DbProviderFactory Alma](obtaining-a-dbproviderfactory.md)  
 Yüklü veri sağlayıcılarının nasıl ekleneceğini ve <xref:System.Data.Common.DbConnection> `DbProviderFactory`kaynağından bir oluşturma işlemlerinin nasıl yapılacağını gösterir.  
  
 [DbConnection, DbCommand ve DbException](dbconnection-dbcommand-and-dbexception.md)  
 <xref:System.Data.Common.DbCommand> <xref:System.Data.Common.DbException>Ve 'ninnasıloluşturulduğunuvekullanarakverihatalarınınnasılişleneceğinigösterir.<xref:System.Data.Common.DbDataReader>  
  
 [DbDataAdapter ile Verileri Değiştirme](modifying-data-with-a-dbdataadapter.md)  
 Verileri almak ve değiştirmek <xref:System.Data.Common.DbCommandBuilder> <xref:System.Data.Common.DbDataAdapter> için ile birlikte nasıl kullanılacağını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
