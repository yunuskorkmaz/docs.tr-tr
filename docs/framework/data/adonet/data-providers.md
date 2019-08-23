---
title: .NET Framework Veri Sağlayıcıları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: fc338b176ee0b20800b83febe05ed2fe695cecb0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949821"
---
# <a name="net-framework-data-providers"></a>.NET Framework Veri Sağlayıcıları
Bir .NET Framework veri sağlayıcısı, bir veritabanına bağlanmak, komutları yürütmek ve sonuçları almak için kullanılır. Bu sonuçlar doğrudan işlenirler, gerektiğinde kullanıcıya sunulmak <xref:System.Data.DataSet> üzere, birden fazla kaynaktaki verilerle birlikte veya katmanlar arasında uzaktan bir şekilde yerleştirilir. .NET Framework veri sağlayıcıları hafif, veri kaynağı ve kod arasında en az bir katman oluşturarak, işlevselliği ödün vermeden performansı artırır.  
  
 Aşağıdaki tabloda .NET Framework dahil edilen veri sağlayıcıları listelenmektedir.  
  
|.NET Framework veri sağlayıcısı|Açıklama|  
|-------------------------------------------------------------------------------|-----------------|  
|SQL Server için .NET Framework Veri Sağlayıcısı|Microsoft SQL Server için veri erişimi sağlar. <xref:System.Data.SqlClient> Ad alanını kullanır.|  
|OLE DB için .NET Framework Veri Sağlayıcısı|OLE DB kullanılarak sunulan veri kaynakları için. <xref:System.Data.OleDb> Ad alanını kullanır.|  
|ODBC için .NET Framework Veri Sağlayıcısı|ODBC kullanılarak sunulan veri kaynakları için. <xref:System.Data.Odbc> Ad alanını kullanır.|  
|Oracle için .NET Framework Veri Sağlayıcısı|Oracle veri kaynakları için. Oracle için .NET Framework veri sağlayıcısı Oracle istemci yazılımı sürümü 8.1.7 ve üstünü destekler ve <xref:System.Data.OracleClient> ad alanını kullanır.|  
|EntityClient sağlayıcı|Varlık Veri Modeli (EDM) uygulamaları için veri erişimi sağlar. <xref:System.Data.EntityClient> Ad alanını kullanır.|  
|SQL Server Compact 4,0 için Veri Sağlayıcısı .NET Framework.|Microsoft SQL Server Compact 4,0 için veri erişimi sağlar. [System. Data. SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) ad alanını kullanır.|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>.NET Framework veri sağlayıcılarının temel nesneleri  
 Aşağıdaki tabloda .NET Framework veri sağlayıcısı oluşturan dört çekirdekli nesne özetlenmektedir.  
  
|Nesne|Açıklama|  
|------------|-----------------|  
|`Connection`|Belirli bir veri kaynağına bağlantı kurar. Tüm `Connection` nesneler için temel sınıf <xref:System.Data.Common.DbConnection> sınıfındır.|  
|`Command`|Bir veri kaynağına karşı bir komut yürütür. ' `Parameters` `Transaction` Dan`Connection`bir öğesinin kapsamında sunar ve çalıştırılabilir. Tüm `Command` nesneler için temel sınıf <xref:System.Data.Common.DbCommand> sınıfındır.|  
|`DataReader`|Bir veri kaynağından salt ileri, salt okunur bir veri akışını okur. Tüm `DataReader` nesneler için temel sınıf <xref:System.Data.Common.DbDataReader> sınıfındır.|  
|`DataAdapter`|Bir `DataSet` ' i doldurur ve veri kaynağıyla güncelleştirmeleri çözümler. Tüm `DataAdapter` nesneler için temel sınıf <xref:System.Data.Common.DbDataAdapter> sınıfındır.|  
  
 Bu belgede daha önce açıklanan tabloda listelenen çekirdek sınıflarının yanı sıra, bir .NET Framework veri sağlayıcısı aşağıdaki tabloda listelenen sınıfları da içerir.  
  
|Nesne|Açıklama|  
|------------|-----------------|  
|`Transaction`|İşlemler içindeki komutları veri kaynağında listeler. Tüm `Transaction` nesneler için temel sınıf <xref:System.Data.Common.DbTransaction> sınıfındır. ADO.net Ayrıca, <xref:System.Transactions> ad alanındaki sınıfları kullanan işlemler için destek sağlar.|  
|`CommandBuilder`|Saklı bir yordamdan bir `DataAdapter` veya türetilmiş parametre bilgisinin otomatik olarak oluşturduğu ve bir `Command` nesnenin `Parameters` koleksiyonunu dolduran yardımcı nesne. Tüm `CommandBuilder` nesneler için temel sınıf <xref:System.Data.Common.DbCommandBuilder> sınıfındır.|  
|`ConnectionStringBuilder`|`Connection` Nesneler tarafından kullanılan bağlantı dizelerinin içeriğini oluşturmak ve yönetmek için basit bir yol sağlayan yardımcı nesne. Tüm `ConnectionStringBuilder` nesneler için temel sınıf <xref:System.Data.Common.DbConnectionStringBuilder> sınıfındır.|  
|`Parameter`|Komutlar ve saklı yordamlar için giriş, çıkış ve dönüş değeri parametrelerini tanımlar. Tüm `Parameter` nesneler için temel sınıf <xref:System.Data.Common.DbParameter> sınıfındır.|  
|`Exception`|Veri kaynağında bir hata ile karşılaşıldığında döndürülür. İstemcide karşılaşılan bir hata için .NET Framework veri sağlayıcıları bir .NET Framework özel durumu oluşturur. Tüm `Exception` nesneler için temel sınıf <xref:System.Data.Common.DbException> sınıfındır.|  
|`Error`|Bir veri kaynağı tarafından döndürülen bir uyarı veya hatadan bilgileri gösterir.|  
|`ClientPermission`|.NET Framework veri sağlayıcısı kod erişimi güvenlik öznitelikleri için verilmiştir. Tüm `ClientPermission` nesneler için temel sınıf <xref:System.Data.Common.DBDataPermission> sınıfındır.|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı  
 SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı, SQL Server ile iletişim kurmak için kendi protokolünü kullanır. Hafif ve bir OLE DB ya da açık veritabanı bağlantısı (ODBC) katmanı eklemeden SQL Server doğrudan erişmek için iyileştirildi. Aşağıdaki çizim, Veri Sağlayıcısı için .NET Framework OLE DB ile SQL Server için .NET Framework Veri Sağlayıcısı karşıttır. OLE DB .NET Framework Veri Sağlayıcısı, bağlantı havuzu oluşturma ve işlem hizmetleri ve veri kaynağı için OLE DB sağlayıcı sağlayan OLE DB hizmeti bileşeni aracılığıyla bir OLE DB veri kaynağına iletişim kurar.  
  
> [!NOTE]
> ODBC için .NET Framework Veri Sağlayıcısı, OLE DB için .NET Framework Veri Sağlayıcısı benzer bir mimariye sahiptir; Örneğin, bir ODBC hizmet bileşenine çağrı yapılır.  
  
 ![Veri sağlayıcıları](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
SQL Server için .NET Framework Veri Sağlayıcısı ve Veri Sağlayıcısı için .NET Framework OLE DB karşılaştırması  
  
 SQL Server sınıfları için .NET Framework veri sağlayıcısı <xref:System.Data.SqlClient> ad alanında bulunur.  
  
 SQL Server için .NET Framework Veri Sağlayıcısı hem yerel hem de dağıtılmış işlemleri destekler. Dağıtılmış işlemler için .NET Framework SQL Server Veri Sağlayıcısı, varsayılan olarak bir işlemde otomatik olarak aşağı listeler ve Windows Bileşen hizmetlerinden veya <xref:System.Transactions>işlem ayrıntılarını alır. Daha fazla bilgi için bkz. [işlemler ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Aşağıdaki kod örneği, uygulamalarınıza nasıl `System.Data.SqlClient` ad alanı ekleneceğini gösterir.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>OLE DB için .NET Framework Veri Sağlayıcısı  
 OLE DB (OleDb) için .NET Framework Veri Sağlayıcısı, veri erişimini etkinleştirmek için COM birlikte çalışma aracılığıyla yerel OLE DB kullanır. OLE DB için .NET Framework Veri Sağlayıcısı hem yerel hem de dağıtılmış işlemleri destekler. Dağıtılmış işlemler için .NET Framework OLE DB Veri Sağlayıcısı, varsayılan olarak bir işlemde otomatik olarak aşağı listeler ve Windows Bileşen hizmetlerinden işlem ayrıntılarını edinir. Daha fazla bilgi için bkz. [işlemler ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Aşağıdaki tabloda, ADO.NET ile test edilmiş sağlayıcılar gösterilmektedir.  
  
|Sürücü|Sağlayıcı|  
|------------|--------------|  
|SQLOLEDB|SQL Server için Microsoft OLE DB sağlayıcısı|  
|MSDAORA|Oracle için Microsoft OLE DB sağlayıcısı|  
|Microsoft.Jet.OLEDB.4.0|Microsoft Jet için OLE DB sağlayıcısı|  
  
> [!NOTE]
> ASP.NET uygulamaları gibi çok iş parçacıklı uygulamalar için bir veri kaynağı olarak erişim (Jet) veritabanı kullanılması önerilmez. Bir ASP.NET uygulaması için bir veri kaynağı olarak Jet kullanmanız gerekiyorsa, bir Access veritabanına bağlanan ASP.NET uygulamalarının bağlantı sorunlarıyla karşılaşabileceği farkında olun.  
  
 OLE DB için .NET Framework Veri Sağlayıcısı OLE DB sürüm 2,5 arabirimlerini desteklemez. OLE DB 2,5 arabirimleri için destek gerektiren OLE DB sağlayıcılar, OLE DB için .NET Framework Veri Sağlayıcısı ile düzgün çalışmaz. Bu, Exchange için Microsoft OLE DB sağlayıcısı ve Internet yayımlaması için Microsoft OLE DB sağlayıcısı içerir.  
  
 OLE DB için .NET Framework Veri Sağlayıcısı, ODBC için OLE DB sağlayıcısıyla (MSDASQL) çalışmaz. ADO.NET kullanarak bir ODBC veri kaynağına erişmek için, ODBC için .NET Framework Veri Sağlayıcısı kullanın.  
  
 OLE DB sınıfları için .NET Framework veri sağlayıcısı <xref:System.Data.OleDb> ad alanında bulunur. Aşağıdaki kod örneği, uygulamalarınıza nasıl `System.Data.OleDb` ad alanı ekleneceğini gösterir.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>ODBC için .NET Framework Veri Sağlayıcısı  
 ODBC için .NET Framework Veri Sağlayıcısı (ODBC), veri erişimini etkinleştirmek için yerel ODBC Sürücü Yöneticisi 'Ni (DM) kullanır. ODBC veri sağlayıcısı hem yerel hem de dağıtılmış işlemleri destekler. Dağıtılmış işlemler için, varsayılan olarak, ODBC veri sağlayıcısı bir işlem içinde otomatik olarak listeler ve Windows Bileşen hizmetlerinden işlem ayrıntılarını edinir. Daha fazla bilgi için bkz. [işlemler ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Aşağıdaki tabloda, ADO.NET ile sınanan ODBC sürücüleri gösterilmektedir.  
  
|Sürücü|  
|------------|  
|SQL Server|  
|Oracle için Microsoft ODBC|  
|Microsoft Access sürücüsü (*. mdb)|  
  
 ODBC sınıfları için .NET Framework veri sağlayıcısı <xref:System.Data.Odbc> ad alanında bulunur.  
  
 Aşağıdaki kod örneği, uygulamalarınıza nasıl `System.Data.Odbc` ad alanı ekleneceğini gösterir.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
> ODBC için .NET Framework Veri Sağlayıcısı, MDAC 2,6 veya sonraki bir sürümü gerektirir ve MDAC 2,8 SP1 önerilir. MDAC 2,8 SP1 'i [veri erişimi ve depolama Geliştirici Merkezi '](https://go.microsoft.com/fwlink/?linkid=4173)nden indirebilirsiniz.  
  
## <a name="net-framework-data-provider-for-oracle"></a>Oracle için .NET Framework Veri Sağlayıcısı  
 Oracle (OracleClient) için .NET Framework Veri Sağlayıcısı Oracle istemci bağlantı yazılımı aracılığıyla Oracle veri kaynaklarına veri erişimi sağlar. Veri sağlayıcısı, Oracle istemci yazılımı sürümü 8.1.7 veya sonraki bir sürümü destekler. Veri sağlayıcısı hem yerel hem de dağıtılmış işlemleri destekler. Daha fazla bilgi için bkz. [işlemler ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Oracle için .NET Framework Veri Sağlayıcısı, bir Oracle veri kaynağına bağlanabilmeniz için sistemde Oracle istemci yazılımı (sürüm 8.1.7 veya sonraki bir sürüm) gerektirir.  
  
 Oracle sınıfları için .NET Framework veri sağlayıcısı <xref:System.Data.OracleClient> ad alanında bulunur ve `System.Data.OracleClient.dll` derlemede yer alır. Veri sağlayıcısını kullanan bir uygulamayı `System.Data.dll` derlerken, `System.Data.OracleClient.dll` ve ' a başvurmanız gerekir.  
  
 Aşağıdaki kod örneği, uygulamalarınıza nasıl `System.Data.OracleClient` ad alanı ekleneceğini gösterir.  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>.NET Framework Veri Sağlayıcısı seçme  
 Uygulamanızın tasarım ve veri kaynağına bağlı olarak, .NET Framework veri sağlayıcısı seçiminiz uygulamanızın performansını, yeteneğini ve bütünlüğünü iyileştirebilir. Aşağıdaki tabloda her bir .NET Framework veri sağlayıcısının avantajları ve sınırlamaları ele alınmaktadır.  
  
|Sağlayıcı|Notlar|  
|--------------|-----------|  
|SQL Server için .NET Framework Veri Sağlayıcısı|Microsoft SQL Server kullanan orta katmanlı uygulamalar için önerilir.<br /><br /> Microsoft Database Engine (MSDE) veya SQL Server kullanan tek katmanlı uygulamalar için önerilir.<br /><br /> OLE DB için .NET Framework Veri Sağlayıcısı ile SQL Server için OLE DB sağlayıcısı 'nın (SQLOLEDB) kullanılması önerilir.|  
|OLE DB için .NET Framework Veri Sağlayıcısı|SQL Server için, bu sağlayıcı yerine SQL Server için .NET Framework Veri Sağlayıcısı önerilir.<br /><br /> Microsoft Access veritabanları kullanan tek katmanlı uygulamalar için önerilir. Bir orta katman uygulaması için Access veritabanı kullanılması önerilmez.|  
|ODBC için .NET Framework Veri Sağlayıcısı|ODBC veri kaynaklarını kullanan orta ve tek katmanlı uygulamalar için önerilir.|  
|Oracle için .NET Framework Veri Sağlayıcısı|Oracle veri kaynakları kullanan orta ve tek katmanlı uygulamalar için önerilir.|  
  
## <a name="entityclient-provider"></a>EntityClient sağlayıcı  
 EntityClient sağlayıcısı, Varlık Veri Modeli (EDM) tabanlı verilere erişmek için kullanılır. Diğer .NET Framework veri sağlayıcılarının aksine, bir veri kaynağıyla doğrudan etkileşime girmez. Bunun yerine, temel alınan veri sağlayıcısıyla iletişim kurmak için Entity SQL kullanır. Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](./ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
