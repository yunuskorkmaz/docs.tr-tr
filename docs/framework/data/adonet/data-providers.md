---
title: ".NET framework veri sağlayıcıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ff16c00f1e0e87c9f046c1f5944e11a9111f6e1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-data-providers"></a>.NET framework veri sağlayıcıları
A [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı, bir veritabanına bağlanma, komutları çalıştırma ve sonuçları için kullanılır. Bu sonuçlar ya da doğrudan yerleştirilen işlenir bir <xref:System.Data.DataSet> gerektiğinde kullanıcıya birden fazla kaynaktan veri ile birleştirilmiş veya katmanları arasında düğümlerde açığa çıkarılması için. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]veri sağlayıcıları basit, kod ve veri kaynağı arasındaki en az bir katman işlevselliği ödün vermeden performansı artırma oluşturma.  
  
 Aşağıdaki tabloda yer alan veri sağlayıcılarını listeler [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]veri sağlayıcısı|Açıklama|  
|-------------------------------------------------------------------------------|-----------------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]İçin veri sağlayıcısı[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]|Microsoft Veri erişim sağlayan [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Kullanan <xref:System.Data.SqlClient> ad alanı.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]OLE DB veri sağlayıcısı|OLE DB kullanılarak tarafından kullanıma sunulan veri kaynakları için. Kullanan <xref:System.Data.OleDb> ad alanı.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ODBC için veri sağlayıcısı|ODBC kullanılarak tarafından kullanıma sunulan veri kaynakları için. Kullanan <xref:System.Data.Odbc> ad alanı.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]Oracle için veri sağlayıcısı|Oracle veri kaynakları için. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Veri sağlayıcısı Oracle için Oracle istemci yazılımı 8.1.7 destekler ve daha sonra ve kullandığı <xref:System.Data.OracleClient> ad alanı.|  
|EntityClient sağlayıcısı|Varlık veri modeli (EDM) uygulamaları için veri erişim sağlar. Kullanan <xref:System.Data.EntityClient> ad alanı.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]Veri sağlayıcısı için [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] Compact 4.0.|Microsoft Veri erişim sağlayan [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] Compact 4.0. Kullanan [System.Data.SqlServerCe](http://msdn.microsoft.com/library/system.data.sqlserverce.aspx) ad alanı.|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>.NET Framework veri sağlayıcıları çekirdek nesneleri  
 Aşağıdaki tabloda oluşturan dört çekirdek nesneleri özetlenmektedir bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı.  
  
|Nesne|Açıklama|  
|------------|-----------------|  
|`Connection`|Belirli bir veri kaynağına bağlantı kurar. Tümü için temel sınıf `Connection` nesnelerin <xref:System.Data.Common.DbConnection> sınıfı.|  
|`Command`|Bir veri kaynağında bir komut yürütür. Sunan `Parameters` ve kapsamında yürütebilir bir `Transaction` gelen bir `Connection`. Tümü için temel sınıf `Command` nesnelerin <xref:System.Data.Common.DbCommand> sınıfı.|  
|`DataReader`|Veri salt iletme, salt okunur bir akış veri kaynağından okur. Tümü için temel sınıf `DataReader` nesnelerin <xref:System.Data.Common.DbDataReader> sınıfı.|  
|`DataAdapter`|Dolduran bir `DataSet` ve veri kaynağı ile güncelleştirmeleri giderir. Tümü için temel sınıf `DataAdapter` nesnelerin <xref:System.Data.Common.DbDataAdapter> sınıfı.|  
  
 Daha önce bu belgede, tabloda listelenen temel sınıfları yanı sıra bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı aşağıdaki tabloda listelenen sınıfların de içerir.  
  
|Nesne|Açıklama|  
|------------|-----------------|  
|`Transaction`|Veri kaynağında işlemlerde komutları kaydeder. Tümü için temel sınıf `Transaction` nesnelerin <xref:System.Data.Common.DbTransaction> sınıfı. ADO.NET de destek sağlar sınıflarda kullanarak işlemler için <xref:System.Transactions> ad alanı.|  
|`CommandBuilder`|Komut özelliklerini otomatik olarak oluşturan bir yardımcı nesnesi bir `DataAdapter` ya da bir saklı yordamdan parametre bilgilerini türetilen ve doldurur `Parameters` koleksiyonu bir `Command` nesnesi. Tümü için temel sınıf `CommandBuilder` nesnelerin <xref:System.Data.Common.DbCommandBuilder> sınıfı.|  
|`ConnectionStringBuilder`|Oluşturup tarafından kullanılan bağlantı dizeleri içeriğini yönetmek için basit bir yol sağlayan bir yardımcı nesnesi `Connection` nesneleri. Tümü için temel sınıf `ConnectionStringBuilder` nesnelerin <xref:System.Data.Common.DbConnectionStringBuilder> sınıfı.|  
|`Parameter`|Giriş, çıkış ve komutları ve saklı yordamlar için dönüş değeri parametreleri tanımlar. Tümü için temel sınıf `Parameter` nesnelerin <xref:System.Data.Common.DbParameter> sınıfı.|  
|`Exception`|Veri kaynağında bir hata oluştuğunda döndürdü. İstemcide karşılaşılan bir hata için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcıları throw bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] özel durum. Tümü için temel sınıf `Exception` nesnelerin <xref:System.Data.Common.DbException> sınıfı.|  
|`Error`|Bir uyarı veya bir veri kaynağı tarafından döndürülen hata bilgilerini gösterir.|  
|`ClientPermission`|İçin sağlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı kod erişim güvenliği öznitelikleri. Tümü için temel sınıf `ClientPermission` nesnelerin <xref:System.Data.Common.DBDataPermission> sınıfı.|  
  
## <a name="net-framework-data-provider-for-includessnoversionincludesssnoversion-mdmd-sqlclient"></a>.NET framework veri sağlayıcısı için [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] (SqlClient)  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçin veri sağlayıcı [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] (SqlClient) ile iletişim kurmak için kendi protokolünü kullanır [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Basit olduğundan ve iyi iyileştirilmiş çünkü gerçekleştirir erişmek için bir [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] bir OLE DB veya açık veritabanı bağlantısı (ODBC) katmanı eklemeden doğrudan. Aşağıdaki çizimde çelişir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için veri sağlayıcı [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] ile [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için OLE DB veri sağlayıcısı. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçin OLE DB veri sağlayıcısı iletişim kuran bir OLE DB veri kaynağına bağlantı havuzu ve işlem Hizmetleri ve OLE DB sağlayıcısı için veri kaynağı sağlayan iki OLE DB hizmet bileşeni, aracılığıyla.  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC için veri sağlayıcısı için benzer bir mimariye sahip [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı için OLE DB; Örneğin, bir ODBC hizmet bileşeni çağırır.  
  
 ![Veri sağlayıcıları](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
SQL Server için .NET Framework veri sağlayıcısı ve OLE DB için .NET Framework veri sağlayıcısı karşılaştırması  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçin veri sağlayıcı [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] sınıfları içinde bulunur <xref:System.Data.SqlClient> ad alanı.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçin veri sağlayıcı [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] hem yerel hem de dağıtılmış işlemleri destekler. Dağıtılmış işlemler için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için veri sağlayıcı [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], varsayılan olarak, bir işlem içinde otomatik olarak kaydeder ve Windows bileşen hizmetlerinden işlem ayrıntılarını alır veya <xref:System.Transactions>. Daha fazla bilgi için bkz: [işlemleri ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Aşağıdaki kod örneğinde nasıl ekleneceği gösterilmiştir `System.Data.SqlClient` uygulamalarınızda ad alanı.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>OLE DB için .NET framework veri sağlayıcısı  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] OLE DB (OleDb) için veri sağlayıcısı, veri erişimi etkinleştirmek için yerel OLE DB aracılığıyla COM birlikte çalışma kullanır. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçin OLE DB veri sağlayıcısı hem yerel hem de dağıtılmış işlemleri destekler. Dağıtılmış işlemler için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı için OLE DB, varsayılan olarak, otomatik olarak bir işlem içinde kaydeder ve Windows bileşen hizmetlerinden işlem ayrıntılarını alır. Daha fazla bilgi için bkz: [işlemleri ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 İle test sağlayıcıları aşağıdaki tabloda gösterilmektedir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Sürücü|Sağlayıcı|  
|------------|--------------|  
|SQLOLEDB|İçin Microsoft OLE DB sağlayıcısı[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]|  
|MSDAORA|Oracle için Microsoft OLE DB sağlayıcısı|  
|Microsoft.Jet.OLEDB.4.0|Microsoft Jet için OLE DB sağlayıcısı|  
  
> [!NOTE]
>  Birden çok iş parçacıklı uygulamalar için bir veri kaynağı olarak bir erişim (Jet) veritabanı gibi kullanılarak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamalar, önerilmez. Jet için veri kaynağı olarak kullanıyorsanız gerekir bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama, fark [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Access veritabanına bağlanan uygulamaları bağlantı sorunlarını karşılaşır.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçin OLE DB veri sağlayıcısı, OLE DB sürüm 2.5 arabirimleri desteklemiyor. OLE DB OLE DB 2.5 arabirimleri için destek gerektiren sağlayıcıları çalışmayan doğru ile [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için OLE DB veri sağlayıcısı. Bu Exchange ve Internet yayımlama için Microsoft OLE DB sağlayıcısı için Microsoft OLE DB Sağlayıcısı'nı içerir.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçin OLE DB veri sağlayıcısı, OLE DB sağlayıcısı için ODBC (MSDASQL) ile çalışmaz. Bir ODBC veri kaynağını kullanarak erişmek için [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], kullanmak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC için veri sağlayıcısı.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]OLE DB sınıfları için veri sağlayıcı içinde bulunur <xref:System.Data.OleDb> ad alanı. Aşağıdaki kod örneğinde nasıl ekleneceği gösterilmiştir `System.Data.OleDb` uygulamalarınızda ad alanı.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>ODBC için .NET framework veri sağlayıcısı  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC (Odbc) için veri sağlayıcısı, veri erişimi etkinleştirmek için yerel ODBC Sürücü Yöneticisi (DM) kullanır. ODBC veri sağlayıcısı hem yerel hem de dağıtılmış işlemleri destekler. Dağıtılmış işlemler için ODBC veri sağlayıcısı, varsayılan olarak, otomatik olarak bir işlem içinde kaydeder ve Windows bileşen hizmetlerinden işlem ayrıntılarını alır. Daha fazla bilgi için bkz: [işlemleri ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Aşağıdaki tabloda ile test ODBC sürücüleri gösterir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Sürücü|  
|------------|  
|[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]|  
|Oracle için Microsoft ODBC|  
|Microsoft Access sürücüsü (*.mdb)|  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ODBC sınıfları için veri sağlayıcı içinde bulunur <xref:System.Data.Odbc> ad alanı.  
  
 Aşağıdaki kod örneğinde nasıl ekleneceği gösterilmiştir `System.Data.Odbc` uygulamalarınızda ad alanı.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC veri sağlayıcısı, MDAC 2.6 veya sonraki bir sürümünü gerektirir ve MDAC 2.8 SP1 önerilir. MDAC 2.8 SP1'den indirebilirsiniz [veri erişimi ve depolama Geliştirici Merkezi](http://go.microsoft.com/fwlink/?linkid=4173).  
  
## <a name="net-framework-data-provider-for-oracle"></a>Oracle için .NET framework veri sağlayıcısı  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Veri sağlayıcısı (OracleClient) Oracle için Oracle veri kaynaklarını Oracle istemci bağlantısı yazılımı aracılığıyla veri erişim sağlar. Veri sağlayıcısı, Oracle istemci yazılımı 8.1.7 veya sonraki bir sürümünü destekler. Veri sağlayıcısı hem yerel hem de dağıtılmış işlemleri destekler. Daha fazla bilgi için bkz: [işlemleri ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Veri sağlayıcısı Oracle için Oracle veri kaynağına bağlanabilmesi için önce bu Oracle istemci yazılımını (sürüm 8.1.7 veya sonraki bir sürümünü) sistemde gerektirir.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]Oracle sınıfları için veri sağlayıcı içinde bulunur <xref:System.Data.OracleClient> ad alanı ve misiniz yer alan `System.Data.OracleClient.dll` derleme. Her ikisi de başvurmalıdır `System.Data.dll` ve `System.Data.OracleClient.dll` derleme ne zaman veri sağlayıcısını kullanan bir uygulama.  
  
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
 Tercih ettiğiniz uygulamanız için tasarım ve veri kaynağı bağlı olarak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı, performans, yetenek ve uygulamanızı bütünlüğünü geliştirebilir. Aşağıdaki tabloda avantajları ve sınırlamaları her anlatılmaktadır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı.  
  
|Sağlayıcı|Notlar|  
|--------------|-----------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]İçin veri sağlayıcısı[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]|Microsoft kullanan Orta katman uygulamalar için önerilen [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].<br /><br /> Microsoft veritabanı altyapısı (MSDE) kullanan tek katmanlı uygulamalar için önerilen veya [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].<br /><br /> OLE DB sağlayıcısı kullanımını üzerinden önerilen [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] (SQLOLEDB) ile [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için OLE DB veri sağlayıcısı.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]OLE DB veri sağlayıcısı|İçin [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için veri sağlayıcı [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] yerine bu sağlayıcı önerilir.<br /><br /> Microsoft Access veritabanları kullanan tek katmanlı uygulamalar için önerilir. Orta katman bir uygulama için bir Access veritabanı kullanılması önerilmez.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]'' ODBC için veri sağlayıcısı|ODBC veri kaynakları için Orta ve tek katmanlı uygulamaları önerilir.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]'' İçin Oracle veri sağlayıcısı|Oracle veri kaynaklarını kullanmak Orta ve tek katmanlı uygulamalar için önerilir.|  
  
## <a name="entityclient-provider"></a>EntityClient sağlayıcısı  
 EntityClient sağlayıcısı, varlık veri modeli (EDM) tabanlı verilerine erişmek için kullanılır. Diğer .NET Framework veri sağlayıcıları farklı olarak, bu veri kaynağı ile doğrudan etkileşime girmez. Bunun yerine, temel alınan veri sağlayıcı ile iletişim kurmak için varlık SQL kullanır. Daha fazla bilgi için bkz: [EntityClient ve varlık SQL](http://msdn.microsoft.com/en-us/49202ab9-ac98-4b4b-a05c-140e422bf527).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
