---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 255ef115e6851b5f1d93744b54ec88990746d9cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543548"
---
# <a name="dbproviderfactories"></a>DbProviderFactories
<xref:System.Data.Common> Ad alanı oluşturmak için sınıflar sağlar <xref:System.Data.Common.DbProviderFactory> belirli veri kaynakları ile çalışmak için örnekleri. Oluştururken bir <xref:System.Data.Common.DbProviderFactory> örneği ve veri sağlayıcısı hakkında bilgi geçirmek `DbProviderFactory` , verilen bilgilere göre tabanlı döndürmek için doğru türü kesin belirlenmiş bir bağlantı nesnesi belirleyebilirsiniz.  
  
 .NET Framework sürüm 4, veri sağlayıcıları gibi olarak başlayan <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, ve <xref:System.Data.OracleClient> machine.config dosyasının, ancak özel artık listelenen sağlayıcıları devam listelenmesi vardır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Fabrika Modeline Genel Bakış](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 Fabrika tasarım deseni ve programlama arabirimi genel bir bakış sağlar.  
  
 [DbProviderFactory Alma](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 Yüklü veri sağlayıcıları listeleme ve oluşturma yapmayı gösteren bir <xref:System.Data.Common.DbConnection> gelen bir `DbProviderFactory`.  
  
 [DbConnection, DbCommand ve DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 Nasıl oluşturulacağını gösterir bir <xref:System.Data.Common.DbCommand> ve <xref:System.Data.Common.DbDataReader>ve veri hatalarını kullanarak işleme <xref:System.Data.Common.DbException>.  
  
 [DbDataAdapter ile Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 Nasıl kullanılacağını gösteren bir <xref:System.Data.Common.DbCommandBuilder> ile bir <xref:System.Data.Common.DbDataAdapter> almak ve verileri değiştirme.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
