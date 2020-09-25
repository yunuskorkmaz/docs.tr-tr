---
title: SQL Server’da Veritabanı Yansıtması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: 7e2c1c8ea1cbc1bb22452b9ef9d1f250c96118ea
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173542"
---
# <a name="database-mirroring-in-sql-server"></a>SQL Server’da Veritabanı Yansıtması

SQL Server veritabanı yansıtma, bir SQL Server veritabanının kopyasını veya yansıtmasını bekleyen bir sunucuda tutmanıza olanak sağlar. Yansıtma, verilerin iki ayrı kopyasının her zaman olmasını sağlar ve yüksek kullanılabilirlik ve tamamen veri artıklığı sağlar. SQL Server için .NET Veri Sağlayıcısı, veritabanı yansıtma için örtülü destek sağlar; böylece Geliştirici, bir SQL Server veritabanı için yapılandırıldıktan sonra herhangi bir eylemde bulunan veya herhangi bir kod yazmanıza gerek kalmaz. Ayrıca, <xref:System.Data.SqlClient.SqlConnection> nesnesi, içinde bir yük devretme ortağı sunucusunun adı sağlamaya izin veren bir açık bağlantı modunu destekler <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> .  
  
 <xref:System.Data.SqlClient.SqlConnection>Yansıtma için yapılandırılmış bir veritabanını hedefleyen bir nesne için aşağıdaki Basitleştirilmiş olay dizisi oluşur:  
  
1. İstemci uygulaması başarıyla asıl veritabanına bağlanır ve sunucu daha sonra istemci üzerinde önbelleğe alınmış olan ortak sunucunun adını geri gönderir.  
  
2. Asıl veritabanını içeren sunucu başarısız olursa veya bağlantı kesintiye uğrarsa bağlantı ve işlem durumu kaybedilir. İstemci uygulaması, asıl veritabanıyla bir bağlantıyı yeniden kurmaya çalışır ve başarısız olur.  
  
3. İstemci uygulaması daha sonra, ortak sunucusundaki yansıtma veritabanıyla bir bağlantı kurmaya çalışır. Başarılı olursa bağlantı, yansıtma veritabanına yönlendirilir ve bu da yeni sorumlu veritabanı olur.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Bağlantı dizesinde yük devretme ortağını belirtme  

 Bağlantı dizesinde bir yük devretme iş ortağı sunucusunun adını sağlarsanız, istemci uygulaması ilk kez bağlanırken asıl veritabanı kullanılamadığında, istemci, yük devretme ortağıyla birlikte bir bağlantı kurmayı dener.  
  
```csharp
";Failover Partner=PartnerServerName"  
```  
  
 Yük devretme ortağı sunucusunun adını atlarsanız ve istemci uygulaması ilk kez bağlandığında asıl veritabanı kullanılabilir değilse, bir oluşturulur <xref:System.Data.SqlClient.SqlException> .  
  
 Bir <xref:System.Data.SqlClient.SqlConnection> başarıyla açıldığında, yük devretme ortağı adı sunucu tarafından döndürülür ve bağlantı dizesinde sağlanan tüm değerlerin yerini alır.  
  
> [!NOTE]
> Veritabanı yansıtma senaryoları için bağlantı dizesinde başlangıç kataloğunu veya veritabanı adını açıkça belirtmeniz gerekir. İstemci, açıkça belirtilen bir başlangıç kataloğu veya veritabanına sahip olmayan bir bağlantıda yük devretme bilgileri alırsa, yük devretme bilgileri önbelleğe alınmaz ve asıl sunucu başarısız olursa uygulama yük devretmeye çalışmaz. Bir bağlantı dizesinde yük devretme ortağı için bir değer varsa, ancak ilk katalog veya veritabanı için değer yoksa bir `InvalidArgumentException` oluşturulur.  
  
## <a name="retrieving-the-current-server-name"></a>Geçerli sunucu adı alınıyor  

 Yük devretme durumunda, geçerli bağlantının gerçekten bağlı olduğu sunucu adını <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> bir nesnenin özelliğini kullanarak alabilirsiniz <xref:System.Data.SqlClient.SqlConnection> . Aşağıdaki kod parçası, bağlantı değişkeninin açık bir başvuru olduğunu varsayarak, etkin sunucunun adını alır <xref:System.Data.SqlClient.SqlConnection> .  
  
 Bir yük devretme olayı gerçekleştiğinde ve bağlantı yansıtma sunucusuna dönüştürüldüğünde, **DataSource** özelliği yansıtma adını yansıtacak şekilde güncelleştirilir.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>SqlClient yansıtma davranışı  

 İstemci her zaman geçerli asıl sunucuya bağlanmayı dener. Başarısız olursa, yük devretme ortağını dener. Yansıtma veritabanı zaten ortak sunucusunda sorumlu rolüne geçdiyse, bağlantı başarılı olur ve yeni asıl yansıtma eşlemesi istemciye gönderilir ve çağırmanın ömrü boyunca önbelleğe alınır <xref:System.AppDomain> . Kalıcı depolamada depolanmaz ve farklı bir **AppDomain** veya işlemdeki sonraki bağlantılarda kullanılamaz. Ancak, aynı **AppDomain**içindeki sonraki bağlantılar için de kullanılabilir. Aynı ya da farklı bir bilgisayar üzerinde çalışan başka bir **AppDomain** veya işlemin her zaman bağlantı havuzu olduğunu ve bu bağlantıların sıfırlanmadığını unutmayın. Bu durumda, birincil veritabanı kapalıysa, her işlem veya **AppDomain** bir kez başarısız olur ve havuz otomatik olarak temizlenir.  
  
> [!NOTE]
> Sunucuda yansıtma desteği, veritabanı başına temelinde yapılandırılır. Veri işleme işlemleri sorumlu/yansıtma kümesine dahil olmayan diğer veritabanlarına karşı yürütülürse, çok parçalı adlar kullanarak veya geçerli veritabanını değiştirerek, diğer veritabanlarında yapılan değişiklikler hata durumunda yayılmaz. Yansıtılmış olmayan bir veritabanında veri değiştirildiğinde hiçbir hata oluşturulmaz. Geliştirici, bu işlemlerin olası etkisini değerlendirmelidir.  
  
## <a name="database-mirroring-resources"></a>Veritabanı yansıtma kaynakları  

 Yansıtma yapılandırma, dağıtma ve yönetme hakkında kavramsal belgeler ve bilgiler için SQL Server belgelerine bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Veritabanı Yansıtması](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|SQL Server yansıtma ayarlamayı ve yapılandırmayı açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
