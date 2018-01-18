---
title: "Veritabanı SQL Server yansıtma"
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
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8a955f62aa1e7b2f025a621840753e2213fcefe7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="database-mirroring-in-sql-server"></a>Veritabanı SQL Server yansıtma
SQL Server veritabanı yansıtma kopyalama veya yansıtma, bir SQL Server veritabanının bir yedek sunucu üzerinde tutmanızı sağlar. Yansıtma, verilerin iki ayrı kopyalarının süreleri ve yüksek düzeyde kullanılabilirlik sağladığınızdan hiç var ve veri artıklığı tamamlamak sağlar. Geliştirici herhangi bir eylemde veya SQL Server veritabanı için yapılandırıldıktan sonra herhangi bir kod yazmaya gerek yoktur, böylece SQL Server için .NET veri sağlayıcısı, veritabanı yansıtması için örtülü destek sağlar. Ayrıca, <xref:System.Data.SqlClient.SqlConnection> nesne destekleyen bir yük devretme iş ortağı sunucu adı sağladığını sağlayan bir açık bir bağlantı modu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Basitleştirilmiş aşağıdaki olaylar dizisi gerçekleşir bir <xref:System.Data.SqlClient.SqlConnection> yansıtma için yapılandırılmış bir veritabanını hedefleyip nesnesi:  
  
1.  İstemci uygulaması başarıyla asıl veritabanına bağlanır ve ardından istemcide önbelleğe ortak sunucu adını sunucu geri gönderir.  
  
2.  Asıl veritabanı içeren sunucu başarısız olursa veya bağlantı kesildi, bağlantı ve işlem durumu kaybolur. İstemci uygulaması asıl veritabanı yeniden bağlantı kurmayı dener ve başarısız olur.  
  
3.  İstemci uygulama iş ortağı sunucusunda yansıtma veritabanına bir bağlantı kurmak şeffaf bir şekilde çalışır. Bağlantı başarılı olursa yeni asıl veritabanı haline gelir yansıtma veritabanına yönlendirilir.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Yük devretme ortağı bağlantı dizesinde belirtme  
 Bağlantı dizesindeki bir yük devretme iş ortağı sunucu adı sağlarsanız, istemci uygulaması ilk bağlandığında asıl veritabanı kullanılamıyorsa, istemci saydam yük devretme ortağı bağlantı dener.  
  
```  
";Failover Partner=PartnerServerName"  
```  
  
 Yük devretme iş ortağı sunucu adı atlayın ve asıl veritabanı kullanılamıyorsa, istemci uygulaması ilk bağlandığında sonra bir <xref:System.Data.SqlClient.SqlException> tetiklenir.  
  
 Zaman bir <xref:System.Data.SqlClient.SqlConnection> başarıyla açıldı, yük devretme ortak adı sunucu tarafından döndürülen ve bağlantı dizesinde sağlanan tüm değerleri yerini alır.  
  
> [!NOTE]
>  Veritabanı yansıtma senaryoları için bağlantı dizesinde açıkça ilk kataloğun veya veritabanının adı belirtmeniz gerekir. İstemci bir açıkça belirtilen ilk kataloğun veya veritabanının sahip olmayan bir bağlantı üzerine yük devretme bilgi alırsa, yük devretme bilgileri önbelleğe alınmaz ve uygulama asıl sunucu başarısız olursa devretmek çalışmaz. Bir bağlantı dizesi, yük devretme ortağı, ancak ilk katalog veya veritabanı için herhangi bir değer için bir değer varsa bir `InvalidArgumentException` tetiklenir.  
  
## <a name="retrieving-the-current-server-name"></a>Geçerli sunucu adı alınıyor  
 Bir yük devretme durumunda olduğu için geçerli bağlantı gerçekte bağlı kullanarak sunucu adını alabilir <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> özelliği bir <xref:System.Data.SqlClient.SqlConnection> nesnesi. Aşağıdaki kod parçası, bağlantı değişkeni açık başvuran varsayılarak etkin sunucunun adını alır. <xref:System.Data.SqlClient.SqlConnection>.  
  
 Bir yük devretme olayı oluşur ve yansıtma sunucuya bağlantı anahtarlanır **DataSource** özelliği yansıtma yansıtacak şekilde güncelleştirilir.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>SqlClient yansıtma davranışı  
 İstemci, her zaman geçerli asıl sunucusuna bağlanmaya çalışır. Başarısız olursa, yük devretme ortağı çalışır. Yansıtma veritabanının asıl ortak sunucu rolüne zaten geçildi varsa bağlantı başarılı olur ve yeni bir yansıtma asıl eşleme istemciye gönderilen ve arama ömrü boyunca önbelleğe <xref:System.AppDomain>. Kalıcı depolama alanına depolanmaz ve farklı bir sonraki bağlantılar için kullanılabilir değil **AppDomain** veya işlemi. Ancak, aynı içinde sonraki bağlantılar için kullanılabilir **AppDomain**. Not, başka bir **AppDomain** veya her zaman aynı veya farklı bir bilgisayarda çalışan işlemi, havuzunda bağlantılarının var ve bu bağlantılar değil sıfırlanır. Her durumda, birincil veritabanı devre dışı kalırsa, işlem veya **AppDomain** kez başarısız olur ve havuzu otomatik olarak temizlenir.  
  
> [!NOTE]
>  Sunucusunda desteğini yansıtma veritabanı başına temelinde yapılandırılır. Çok bölümlü adları kullanarak veya geçerli veritabanı değiştirme asıl/yansıtmanın kümesinde yer almayan diğer veritabanlarında veri işleme işlemleri çalıştırıldığında bu diğer veritabanlarına yapılan değişikliklerin hatası durumunda yayılmamasını. Veri değil yansıtılmış bir veritabanında değiştirildiğinde bir hata oluşturulmaz. Geliştirici gibi işlemleri olası etkisini değerlendirmeniz gerekir.  
  
## <a name="database-mirroring-resources"></a>Veritabanı yansıtma kaynakları  
 Kavramsal belgeler ve yapılandırma hakkında bilgi için dağıtma ve yönetme yansıtma, SQL Server Çevrimiçi Kitapları'nda aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Veritabanı yansıtma](http://msdn.microsoft.com/library/bb934127.aspx) SQL Server Çevrimiçi Kitapları'nda|Ayarlama ve SQL Server yansıtma yapılandırma açıklar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
