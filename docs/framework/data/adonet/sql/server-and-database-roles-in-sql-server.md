---
title: SQL Server’da Sunucu ve Veritabanı Rolleri
ms.date: 03/30/2017
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
ms.openlocfilehash: 97ad04b1d081e5635104bdadb2d1a54402ffcca2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961094"
---
# <a name="server-and-database-roles-in-sql-server"></a>SQL Server’da Sunucu ve Veritabanı Rolleri
Tüm SQL Server sürümleri rol tabanlı güvenliği kullanır ve bu sayede, bireysel kullanıcılar yerine bir role veya kullanıcı grubuna izinler atayabilirsiniz. Sabit sunucu ve sabit veritabanı rollerinin, bunlara atanmış sabit bir izin kümesi vardır.  
  
## <a name="fixed-server-roles"></a>Sabit sunucu rolleri  
 Sabit sunucu rollerinin, sabit bir izin ve sunucu genelindeki kapsam kümesi vardır. SQL Server yönetiminde kullanılmak üzere tasarlanmıştır ve bunlara atanan izinler değiştirilemez. Oturum açma işlemleri, bir veritabanında kullanıcı hesabı olmadan sabit sunucu rollerine atanabilir.  
  
> [!IMPORTANT]
> `sysadmin` Sabit sunucu rolü diğer tüm rolleri kapsar ve sınırsız kapsama sahiptir. Bu role, son derece güvenilmediği durumlar dışında sorumluları eklemeyin. `sysadmin`rol üyeleri tüm sunucu veritabanları ve kaynakları üzerinde yönetici ayrıcalıklarına geri alınamaz.  
  
 Kullanıcıları sabit sunucu rollerine eklediğinizde seçmeli olun. Örneğin, `bulkadmin` bu rol, kullanıcıların herhangi bir yerel dosyanın içeriğini bir tabloya eklemesini sağlar ve bu da veri bütünlüğünü tehlikeye atabiliriz. Sabit sunucu rollerinin ve izinlerinin tamamı listesi için bkz. SQL Server Books Online.  
  
## <a name="fixed-database-roles"></a>Düzeltilen veritabanı rolleri  
 Sabit veritabanı rollerinin, izin gruplarını kolayca yönetmenizi sağlamak için tasarlanan önceden tanımlanmış bir izin kümesi vardır. `db_owner` Rolün üyeleri veritabanında tüm yapılandırma ve bakım etkinliklerini gerçekleştirebilir.  
  
 Önceden tanımlı SQL Server roller hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Sunucu düzeyi roller](/sql/relational-databases/security/authentication-access/server-level-roles)|SQL Server ' de sabit sunucu rollerini ve bunlarla ilişkili izinleri açıklar.|  
|[Veritabanı düzeyindeki roller](/sql/relational-databases/security/authentication-access/database-level-roles)|Sabit veritabanı rollerini ve bunlarla ilişkili izinleri açıklar|  
  
## <a name="database-roles-and-users"></a>Veritabanı rolleri ve kullanıcılar  
 Veritabanı nesneleriyle çalışabilmek için, oturum açma bilgilerinin veritabanı kullanıcı hesaplarıyla eşlenmesi gerekir. Daha sonra veritabanı kullanıcıları, bu rollerle ilişkili izin kümelerini devralarak veritabanı rollerine eklenebilir. Tüm izinler verilebilir.  
  
 Uygulamanız için güvenlik tasarlarken `public` rolü `dbo` , `guest` Kullanıcı hesabını ve hesabı da göz önünde bulundurmanız gerekir.  
  
### <a name="the-public-role"></a>Ortak rol  
 `public` Rol, sistem veritabanlarını içeren her veritabanında bulunur. Bırakılamaz ve bundan Kullanıcı ekleyemez veya kaldıramazsınız. `public` Role verilen izinler, `public` varsayılan olarak role ait olduklarından diğer tüm kullanıcılar ve roller tarafından devralınır. Yalnızca `public` tüm kullanıcıların sahip olmasını istediğiniz izinleri verin.  
  
### <a name="the-dbo-user-account"></a>Dbo kullanıcı hesabı  
 `dbo`Veya veritabanı sahibi, veritabanındaki tüm etkinlikleri gerçekleştirmek için izinleri kapsanan bir kullanıcı hesabıdır. Sabit sunucu rolünün üyeleri otomatik olarak öğesine `dbo`eşlenir. `sysadmin`  
  
> [!NOTE]
> `dbo`Ayrıca, SQL Server ' de [sahiplik ve Kullanıcı şeması ayrımı](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)bölümünde açıklandığı gibi bir şemanın adıdır.  
  
 Kullanıcı hesabı, `db_owner` sabit veritabanı rolüyle genellikle karıştırılır. `dbo` Kapsamı `db_owner` bir veritabanıdır; `sysadmin` kapsamı tüm sunucu olur. Roldeki üyelik `dbo` kullanıcı ayrıcalıklarını karşılamıyor. `db_owner`  
  
### <a name="the-guest-user-account"></a>Konuk Kullanıcı hesabı  
 Bir kullanıcının kimliği doğrulandıktan ve bir SQL Server örneğinde oturum açmasına izin verildiğinde, kullanıcının erişmesi gereken her veritabanında ayrı bir kullanıcı hesabının olması gerekir. Her veritabanında bir kullanıcı hesabının gerekli olması, kullanıcıların bir SQL Server örneğine bağlanmasını ve bir sunucudaki tüm veritabanlarına erişmelerini engeller. Veritabanındaki bir `guest` Kullanıcı hesabının varlığı, veritabanı kullanıcı hesabı olmadan bir veritabanına erişmek için bir oturum açmaya izin vererek bu gereksinimi ortadan kaldırarak.  
  
 `guest` Hesap, tüm SQL Server sürümlerindeki yerleşik bir hesaptır. Varsayılan olarak, yeni veritabanlarında devre dışıdır. Etkinleştirilirse, Transact-SQL REVOKE CONNECT FROM KONUĞUNU yürüterek bağlantı iznini iptal ederek devre dışı bırakabilirsiniz.  
  
> [!IMPORTANT]
> `guest` Hesabı kullanmaktan kaçının; kendi veritabanı izinleri olmayan tüm oturumlar, bu hesaba verilen veritabanı izinlerini elde eder. `guest` Hesabı kullanmanız gerekiyorsa, en düşük izinleri verin.  
  
 SQL Server oturum açma bilgileri, kullanıcılar ve roller hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Veritabanı altyapısı Izinleri ile çalışmaya başlama](/sql/relational-databases/security/authentication-access/getting-started-with-database-engine-permissions)|Sorumluları, rolleri, kimlik bilgilerini, securables ve izinleri tanımlayan konuların bağlantılarını içerir.|  
|[Sorumlusu](/sql/relational-databases/security/authentication-access/principals-database-engine)|Sorumluları açıklar ve sunucu ve veritabanı rollerini açıklayan konuların bağlantılarını içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [SQL Server’da Kimlik Doğrulaması](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)
- [SQL Server’da Yetkilendirme ve İzinler](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
