---
title: SQL Server'da veritabanı yansıtması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: 90357b96d570ec1b2f80f8809ccfde69977bbc25
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481916"
---
# <a name="database-mirroring-in-sql-server"></a>SQL Server'da veritabanı yansıtması
SQL Server veritabanı yansıtma, bir kopya veya yansıtma, bir yedek sunucu üzerinde bir SQL Server veritabanının tutmanızı sağlar. Yansıtma, verilerin iki ayrı kopyasını süreleri ve yüksek düzeyde kullanılabilirlik sağladığınızdan hiç var ve veri yedekliği tamamlamak sağlar. Geliştirici herhangi bir eylemde bulunmanız veya bir SQL Server veritabanı için yapılandırıldıktan sonra kod yazmaya gerek yoktur, böylece SQL Server için .NET veri sağlayıcısı, veritabanı yansıtması için örtük desteği sağlar. Ayrıca, <xref:System.Data.SqlClient.SqlConnection> nesne destekleyen bir yük devretme iş ortağı sunucu adını sağlayan sağlayan bir açık bir bağlantı modu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 İçin Basitleştirilmiş aşağıdaki olaylar dizisi gerçekleşir bir <xref:System.Data.SqlClient.SqlConnection> yansıtma için yapılandırılmış bir veritabanını hedefler nesnesi:  
  
1.  İstemci uygulaması başarıyla asıl veritabanına bağlanır ve sunucunun daha istemcide önbelleğe ortak sunucu adını geri gönderir.  
  
2.  Asıl veritabanı içeren bir sunucu başarısız olursa veya bağlantı kesildi, bağlantı ve işlem durumu kaybolur. İstemci uygulama, asıl veritabanına bir bağlantı kurmayı yeniden dener ve başarısız olur.  
  
3.  İstemci uygulama, iş ortağı sunucusunda yansıtma veritabanına bir bağlantı kurmak şeffaf bir şekilde çalışır. Başarılı olursa, ardından yeni asıl veritabanı haline gelir yansıtma veritabanına bağlantı yönlendirilir.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Yük devretme ortağı bağlantı dizesindeki belirtme  
 Bağlantı dizesindeki bir yük devretme iş ortağı sunucu adı sağlarsanız, istemci uygulaması ilk kez bağlandığında asıl veritabanı kullanılamıyorsa istemci saydam yük devretme iş ortağı ile bağlantı dener.  
  
```  
";Failover Partner=PartnerServerName"  
```  
  
 Yük devretme iş ortağı sunucunun adını çıkarın ve asıl veritabanı yoksa istemci uygulaması ilk bağlandığında sonra bir <xref:System.Data.SqlClient.SqlException> tetiklenir.  
  
 Olduğunda bir <xref:System.Data.SqlClient.SqlConnection> başarıyla açıldı, yük devretme iş ortağı adı sunucu tarafından döndürülür ve bağlantı dizesinde sağlanan herhangi bir değer yerine geçer.  
  
> [!NOTE]
>  Veritabanı yansıtma senaryoları için bağlantı dizesindeki ilk kataloğun veya veritabanının adı açıkça belirtmeniz gerekir. İstemci bir açıkça belirtilen ilk kataloğun veya veritabanının sahip olmayan bir bağlantı üzerinde yük devretme bilgileri alırsa, yük devretme bilgileri önbelleğe alınmaz ve uygulama birincil sunucu başarısız olursa, yük devretme çalışmaz. Bir bağlantı dizesi, yük devretme iş ortağı, ancak ilk katalog veya veritabanı için bir değer için bir değer varsa bir `InvalidArgumentException` tetiklenir.  
  
## <a name="retrieving-the-current-server-name"></a>Geçerli sunucu adını alma  
 Bir yük devretme durumunda, geçerli bağlantının gerçekten bağlı kullanarak sunucu adını alabilirsiniz <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> özelliği bir <xref:System.Data.SqlClient.SqlConnection> nesne. Aşağıdaki kod parçası, bağlantı değişkeni açık başvuran varsayılarak etkin sunucunun adını alır. <xref:System.Data.SqlClient.SqlConnection>.  
  
 Bir yük devretme gerçekleştiğinde ve yansıtma sunucusu için bağlantı anahtarlanır **DataSource** özelliği yansıtma adını yansıtacak şekilde güncelleştirilir.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>SqlClient yansıtmayı davranışı  
 İstemci, geçerli bir asıl sunucuya bağlanmak her zaman çalışır. Başarısız olursa, yük devretme iş ortağı çalışır. Yansıtma veritabanının asıl ortak sunucu rolüne zaten geçirildi, bağlantı başarılı olur ve yeni bir yansıtma asıl eşlemesi istemciye gönderilen ve arama ömrü boyunca önbelleğe <xref:System.AppDomain>. Kalıcı depolama alanında depolanır ve farklı bir sonraki bağlantılar için kullanılabilir değil **AppDomain** veya işlemi. Ancak aynı sonraki bağlantılar için **AppDomain**. Not, başka bir **AppDomain** veya kendi havuzundaki bağlantıların her zaman aynı veya farklı bir bilgisayarda çalışan işlemi vardır ve bu bağlantılar sıfırlanmadı. Her durumda, birincil veritabanı kalırsa, işlem veya **AppDomain** kez başarısız olur ve havuzu otomatik olarak temizlenir.  
  
> [!NOTE]
>  Destek sunucuda yansıtma veritabanı başına temelinde yapılandırılır. Bu, başka bir veritabanına değişiklikleri hatası durumunda yayılmaz, veri işleme işlemleri çok bölümlü adlarını kullanarak ya da geçerli veritabanı değiştirerek sorumlusu/yansıtma kümesinde yer almayan diğer veritabanlarına karşı yürütülür. Veri yok yansıtılmış bir veritabanında değiştirildiğinde bir hata oluşturulmaz. Geliştirici, bu işlemler olası etkisini değerlendirmeniz gerekir.  
  
## <a name="database-mirroring-resources"></a>Veritabanı yansıtma kaynakları  
 Kavramsal belgeler ve yapılandırma hakkında bilgi için dağıtma ve yönetme yansıtma, SQL Server belgelerinde aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Veritabanı yansıtma](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|Ayarlama ve SQL Server yansıtma yapılandırma açıklar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
