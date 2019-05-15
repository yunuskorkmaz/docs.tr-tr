---
title: .NET Framework Veri Sağlayıcıları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: 9fead8a5d54fba7232831bba349f27b7eed4657b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583792"
---
# <a name="net-framework-data-providers"></a>.NET Framework Veri Sağlayıcıları
.NET Framework veri sağlayıcısı, bir veritabanına bağlanma, komutları çalıştırarak ve sonuçları almak için kullanılır. Sonuçları ya da doğrudan yerleştirilen işlenen bir <xref:System.Data.DataSet> gerektiğinde kullanıcıya birden çok kaynaktan veri ile birleştirilmiş veya katmanları arasında düğümlerde açığa için. .NET framework veri sağlayıcıları basit, kod ve veri kaynağı arasındaki en az bir katmanda işlevselliği ödün vermeden performansı artırma oluşturma.  
  
 Aşağıdaki tablo, .NET Framework'e dahil edilen veri sağlayıcıları listeler.  
  
|.NET framework veri sağlayıcısı|Açıklama|  
|-------------------------------------------------------------------------------|-----------------|  
|SQL Server için .NET framework veri sağlayıcısı|Microsoft SQL Server için veri erişim sağlar. Kullanan <xref:System.Data.SqlClient> ad alanı.|  
|OLE DB için .NET framework veri sağlayıcısı|OLE DB kullanılarak kullanıma sunulan veri kaynakları. Kullanan <xref:System.Data.OleDb> ad alanı.|  
|ODBC için .NET framework veri sağlayıcısı|ODBC kullanarak kullanıma sunulan veri kaynakları. Kullanan <xref:System.Data.Odbc> ad alanı.|  
|Oracle için .NET framework veri sağlayıcısı|Oracle veri kaynakları için. Oracle için .NET Framework veri sağlayıcısı, Oracle istemci version 8.1.7 destekler ve daha sonra ve kullandığı <xref:System.Data.OracleClient> ad alanı.|  
|EntityClient sağlayıcısı|Varlık veri modeli (EDM) uygulamaları için veri erişim sağlar. Kullanan <xref:System.Data.EntityClient> ad alanı.|  
|.NET framework veri sağlayıcısı için SQL Server Compact 4.0.|Microsoft SQL Server Compact 4.0 için veri erişim sağlar. Kullanan [System.Data.SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) ad alanı.|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>Çekirdek nesnelerin .NET Framework veri sağlayıcıları  
 Aşağıdaki tabloda dört çekirdek nesnelerini bir .NET Framework veri sağlayıcısı özetlenmektedir.  
  
|Nesne|Açıklama|  
|------------|-----------------|  
|`Connection`|Belirli bir veri kaynağına bağlantı kurar. Tüm taban sınıfı `Connection` nesnelerin <xref:System.Data.Common.DbConnection> sınıfı.|  
|`Command`|Bir veri kaynağında bir komutu yürütür. Kullanıma sunan `Parameters` ve kapsamında yürütebilir bir `Transaction` gelen bir `Connection`. Tüm taban sınıfı `Command` nesnelerin <xref:System.Data.Common.DbCommand> sınıfı.|  
|`DataReader`|Verilerin yalnızca iletme, salt okunur bir akış veri kaynağından okur. Tüm taban sınıfı `DataReader` nesnelerin <xref:System.Data.Common.DbDataReader> sınıfı.|  
|`DataAdapter`|Dolduran bir `DataSet` ve güncelleştirmeleri veri kaynağı ile çözümlendi. Tüm taban sınıfı `DataAdapter` nesnelerin <xref:System.Data.Common.DbDataAdapter> sınıfı.|  
  
 Bu belgedeki daha önceki tabloda listelenen temel sınıflarının yanı sıra, bir .NET Framework veri sağlayıcısı aşağıdaki tabloda listelenen sınıfların de içerir.  
  
|Nesne|Açıklama|  
|------------|-----------------|  
|`Transaction`|İşlemleri veri kaynağında komutlarında kaydedicileri listeler. Tüm taban sınıfı `Transaction` nesnelerin <xref:System.Data.Common.DbTransaction> sınıfı. ADO.NET de destek sağlar sınıflarında kullanma işlemlerinde <xref:System.Transactions> ad alanı.|  
|`CommandBuilder`|Komut özelliklerini otomatik olarak oluşturduğu bir yardımcı nesnesi bir `DataAdapter` doldurur ve türeyen bir saklı yordam parametre bilgilerini `Parameters` koleksiyonunu bir `Command` nesne. Tüm taban sınıfı `CommandBuilder` nesnelerin <xref:System.Data.Common.DbCommandBuilder> sınıfı.|  
|`ConnectionStringBuilder`|Oluşturup tarafından kullanılan bağlantı dizeleri içeriğini yönetmek için basit bir yol sağlayan bir yardımcı nesnesi `Connection` nesneleri. Tüm taban sınıfı `ConnectionStringBuilder` nesnelerin <xref:System.Data.Common.DbConnectionStringBuilder> sınıfı.|  
|`Parameter`|Giriş ve çıkış komutları ve saklı yordamlar için dönüş değeri parametreleri tanımlar. Tüm taban sınıfı `Parameter` nesnelerin <xref:System.Data.Common.DbParameter> sınıfı.|  
|`Exception`|Veri kaynağında bir hata ile karşılaşıldığında döndürdü. İstemcide karşılaşılan bir hata için .NET Framework veri sağlayıcıları bir .NET Framework özel durum. Tüm taban sınıfı `Exception` nesnelerin <xref:System.Data.Common.DbException> sınıfı.|  
|`Error`|Bir uyarı ya da bir veri kaynağı tarafından döndürülen hata bilgileri sunar.|  
|`ClientPermission`|.NET Framework veri sağlayıcısı kod erişim güvenlik öznitelikleri için sağlanır. Tüm taban sınıfı `ClientPermission` nesnelerin <xref:System.Data.Common.DBDataPermission> sınıfı.|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>SQL Server (SqlClient) için .NET framework veri sağlayıcısı  
 SQL Server (SqlClient) için .NET Framework veri sağlayıcısı, SQL Server ile iletişim kurmak için kendi protokolünü kullanır. Bu basit ve iyi bir SQL Server bir OLE DB veya açık veritabanı bağlantısı (ODBC) katmanı eklemenize gerek kalmadan doğrudan erişmek için iyileştirildiği için gerçekleştirir. Aşağıdaki çizim .NET Framework veri sağlayıcısı OLE DB için .NET Framework Veri Sağlayıcısı ile SQL Server için karşılaştırır. OLE DB için .NET Framework veri sağlayıcısı, OLE DB veri kaynağına OLE DB hizmet bileşeni, bağlantı havuzu sağlar ve işlem hizmetleri hem veri kaynağı için OLE DB sağlayıcısı üzerinden iletişim kurar.  
  
> [!NOTE]
>  ODBC için .NET Framework veri sağlayıcısı, OLE DB için .NET Framework veri sağlayıcısı için benzer bir mimariye sahiptir; Örneğin, bir ODBC hizmet bileşeni çağırır.  
  
 ![Veri sağlayıcıları](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
SQL Server için .NET Framework veri sağlayıcısı ve OLE DB için .NET Framework veri sağlayıcısı karşılaştırması  
  
 SQL Server sınıflar için .NET Framework veri sağlayıcısı yerleştirilir <xref:System.Data.SqlClient> ad alanı.  
  
 SQL Server için .NET Framework veri sağlayıcısı, hem yerel hem de dağıtılmış işlemleri destekler. Dağıtılmış işlemler için varsayılan olarak, SQL Server için .NET Framework veri sağlayıcısı otomatik olarak bir işlemde kaydeder ve Windows bileşeni hizmetlerinden işlem ayrıntılarını alır veya <xref:System.Transactions>. Daha fazla bilgi için [işlemler ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Aşağıdaki kod örneğinde nasıl ekleneceği gösterilmiştir `System.Data.SqlClient` uygulamalarınızda ad alanı.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>OLE DB için .NET framework veri sağlayıcısı  
 OLE DB (OleDb) için .NET Framework veri sağlayıcısı, veri erişimi için yerel OLE DB aracılığıyla COM birlikte çalışma kullanır. OLE DB için .NET Framework veri sağlayıcısı, hem yerel hem de dağıtılmış işlemleri destekler. Dağıtılmış işlemler için .NET Framework veri sağlayıcısı için OLE DB, varsayılan olarak, otomatik olarak bir işlemde kaydeder ve Windows bileşeni hizmetlerinden işlem ayrıntılarını alır. Daha fazla bilgi için [işlemler ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Aşağıdaki tablo ile test edilmiştir sağlayıcılarını gösterir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Sürücü|Sağlayıcı|  
|------------|--------------|  
|SQLOLEDB|SQL Server için Microsoft OLE DB sağlayıcısı|  
|MSDAORA|Oracle için Microsoft OLE DB sağlayıcısı|  
|Microsoft.Jet.OLEDB.4.0|Microsoft Jet OLE DB sağlayıcısı|  
  
> [!NOTE]
>  Çok iş parçacıklı uygulamalar için veri kaynağı olarak erişim (Jet) veritabanı gibi kullanarak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamaları önerilmez. Veri kaynağı olarak Jet kullanmalıdır, bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama fark [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamaları bir Access veritabanına bağlanmak, bağlantı sorunlarını karşılaşabilir.  
  
 OLE DB için .NET Framework veri sağlayıcısı, OLE DB sürüm 2.5 arabirimlerini desteklemiyor. OLE DB OLE DB 2.5 arabirimleri için destek gerektiren sağlayıcıları OLE DB için .NET Framework Veri Sağlayıcısı ile düzgün şekilde çalışmaz. Bu, Exchange ve Internet yayımlama için Microsoft OLE DB sağlayıcısı için Microsoft OLE DB sağlayıcısı içerir.  
  
 OLE DB için .NET Framework veri sağlayıcısı, OLE DB sağlayıcısı için ODBC (MSDASQL) ile çalışmaz. Bir ODBC veri kaynağı kullanarak erişmeye [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], ODBC için .NET Framework veri sağlayıcısı kullanın.  
  
 OLE DB sınıfları için .NET framework veri sağlayıcısı yerleştirilir <xref:System.Data.OleDb> ad alanı. Aşağıdaki kod örneğinde nasıl ekleneceği gösterilmiştir `System.Data.OleDb` uygulamalarınızda ad alanı.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>ODBC için .NET framework veri sağlayıcısı  
 ODBC (Odbc) için .NET Framework veri sağlayıcısı, veri erişimi etkinleştirmek için yerel bir ODBC Sürücü Yöneticisi'ni (DM) kullanır. ODBC veri sağlayıcısı, hem yerel hem de dağıtılmış işlemleri destekler. Dağıtılmış işlemler için varsayılan olarak, ODBC veri sağlayıcısı otomatik olarak bir işlemde kaydeder ve Windows bileşeni hizmetlerinden işlem ayrıntılarını alır. Daha fazla bilgi için [işlemler ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Aşağıdaki tablo ile test ODBC sürücüleri gösterir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Sürücü|  
|------------|  
|SQL Server|  
|Oracle için Microsoft ODBC|  
|Microsoft Access sürücüsü (*.mdb)|  
  
 ODBC sınıfları için .NET framework veri sağlayıcısı yerleştirilir <xref:System.Data.Odbc> ad alanı.  
  
 Aşağıdaki kod örneğinde nasıl ekleneceği gösterilmiştir `System.Data.Odbc` uygulamalarınızda ad alanı.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  ODBC için .NET Framework veri sağlayıcısı MDAC 2.6 veya sonraki bir sürümünü gerektirir ve MDAC 2.8 SP1 önerilir. MDAC 2.8 SP1'den indirebilirsiniz [veri erişimi ve depolama Geliştirici Merkezi](https://go.microsoft.com/fwlink/?linkid=4173).  
  
## <a name="net-framework-data-provider-for-oracle"></a>Oracle için .NET framework veri sağlayıcısı  
 .NET Framework veri sağlayıcısı (OracleClient) Oracle için Oracle veri kaynaklarına Oracle istemci bağlantısı yazılımı aracılığıyla veri erişimi sağlar. Veri sağlayıcısı, Oracle istemci version 8.1.7 veya sonraki bir sürümünü destekler. Veri sağlayıcısı, hem yerel hem de dağıtılmış işlemleri destekler. Daha fazla bilgi için [işlemler ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Bir Oracle veri kaynağına bağlanabilmesi için Oracle için .NET Framework veri sağlayıcısı sistem üzerinde Oracle istemci yazılımı (8.1.7 sürümü veya sonraki bir sürüm) gerektirir.  
  
 Oracle sınıfları için .NET framework veri sağlayıcısı yerleştirilir <xref:System.Data.OracleClient> yer alır ve bu ad alanı `System.Data.OracleClient.dll` derleme. Her ikisi de başvuru `System.Data.dll` ve `System.Data.OracleClient.dll` veri sağlayıcısı kullanan bir uygulama derleme yaptığınızda.  
  
 Aşağıdaki kod örneğinde nasıl ekleneceği gösterilmiştir `System.Data.OracleClient` uygulamalarınızda ad alanı.  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>.NET Framework veri sağlayıcısı seçme  
 Tasarım ve veri kaynağına bağlı olarak uygulamanız için seçtiğiniz .NET Framework veri sağlayıcısı, performans, özellik ve uygulamanızı bütünlüğünü artırabilir. Aşağıdaki tabloda, her .NET Framework veri sağlayıcısı kısıtlamaları ve avantajları anlatılmaktadır.  
  
|Sağlayıcı|Notlar|  
|--------------|-----------|  
|SQL Server için .NET framework veri sağlayıcısı|Microsoft SQL Server kullanan Orta katman uygulamaları için önerilir.<br /><br /> Microsoft Database Engine (MSDE) veya SQL Server'ı kullanan tek katmanlı uygulamalar için önerilir.<br /><br /> OLE DB sağlayıcısının kullanım için SQL Server (SQLOLEDB) .NET Framework Veri Sağlayıcısı ile OLE DB için önerilir.|  
|OLE DB için .NET framework veri sağlayıcısı|SQL Server için SQL Server için .NET Framework veri sağlayıcısı yerine bu sağlayıcı önerilir.<br /><br /> Microsoft Access veritabanlarına kullanan tek katmanlı uygulamalar için önerilir. Orta katmanlı bir uygulama için bir Access veritabanının kullanılması önerilmez.|  
|ODBC için .NET framework veri sağlayıcısı|ODBC veri kaynakları kullanan Orta ve tek katmanlı uygulamalar için önerilir.|  
|Oracle için .NET framework veri sağlayıcısı|Oracle veri kaynakları kullanan Orta ve tek katmanlı uygulamalar için önerilir.|  
  
## <a name="entityclient-provider"></a>EntityClient sağlayıcısı  
 EntityClient sağlayıcısı, varlık veri modeli (EDM) tabanlı verilere erişmek için kullanılır. Diğer .NET Framework veri sağlayıcıları, bu veri kaynağı ile doğrudan etkileşime girmez. Bunun yerine, temel alınan veri sağlayıcısı ile iletişim kurmak için varlık SQL kullanır. Daha fazla bilgi için [Entity Framework için EntityClient sağlayıcısı](./ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
