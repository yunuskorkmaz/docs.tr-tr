---
title: SQL Server’da Sunucu ve Veritabanı Rolleri
description: Sabit sunucu ve sabit veritabanı rolleri hakkında bilgi edinin ve bunlara atanan bir dizi izin atanır. SQL Server rol tabanlı güvenliği kullanır.
ms.date: 03/30/2017
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
ms.openlocfilehash: 9c3725b0404a5b3c754a53fa56f4a22497afee70
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286250"
---
# <a name="server-and-database-roles-in-sql-server"></a>SQL Server’da Sunucu ve Veritabanı Rolleri
Tüm SQL Server sürümleri rol tabanlı güvenliği kullanır ve bu sayede, bireysel kullanıcılar yerine bir role veya kullanıcı grubuna izinler atayabilirsiniz. Sabit sunucu ve sabit veritabanı rollerinin, bunlara atanmış sabit bir izin kümesi vardır.  
  
## <a name="fixed-server-roles"></a>Sabit sunucu rolleri  
 Sabit sunucu rollerinin, sabit bir izin ve sunucu genelindeki kapsam kümesi vardır. SQL Server yönetiminde kullanılmak üzere tasarlanmıştır ve bunlara atanan izinler değiştirilemez. Oturum açma işlemleri, bir veritabanında kullanıcı hesabı olmadan sabit sunucu rollerine atanabilir.  
  
> [!IMPORTANT]
> `sysadmin`Sabit sunucu rolü diğer tüm rolleri kapsar ve sınırsız kapsama sahiptir. Bu role, son derece güvenilmediği durumlar dışında sorumluları eklemeyin. `sysadmin`rol üyeleri tüm sunucu veritabanları ve kaynakları üzerinde yönetici ayrıcalıklarına geri alınamaz.  
  
 Kullanıcıları sabit sunucu rollerine eklediğinizde seçmeli olun. Örneğin, `bulkadmin` Bu rol, kullanıcıların herhangi bir yerel dosyanın içeriğini bir tabloya eklemesini sağlar ve bu da veri bütünlüğünü tehlikeye atabiliriz. Sabit sunucu rollerinin ve izinlerinin tamamı listesi için bkz. SQL Server Books Online.  
  
## <a name="fixed-database-roles"></a>Düzeltilen veritabanı rolleri  
 Sabit veritabanı rollerinin, izin gruplarını kolayca yönetmenizi sağlamak için tasarlanan önceden tanımlanmış bir izin kümesi vardır. `db_owner`Rolün üyeleri veritabanında tüm yapılandırma ve bakım etkinliklerini gerçekleştirebilir.  
  
 Önceden tanımlı SQL Server roller hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Description|  
|--------------|-----------------|  
|[Sunucu düzeyi roller](/sql/relational-databases/security/authentication-access/server-level-roles)|SQL Server ' de sabit sunucu rollerini ve bunlarla ilişkili izinleri açıklar.|  
|[Veritabanı Düzeyindeki Roller](/sql/relational-databases/security/authentication-access/database-level-roles)|Sabit veritabanı rollerini ve bunlarla ilişkili izinleri açıklar|  
  
## <a name="database-roles-and-users"></a>Veritabanı rolleri ve kullanıcılar  
 Veritabanı nesneleriyle çalışabilmek için, oturum açma bilgilerinin veritabanı kullanıcı hesaplarıyla eşlenmesi gerekir. Daha sonra veritabanı kullanıcıları, bu rollerle ilişkili izin kümelerini devralarak veritabanı rollerine eklenebilir. Tüm izinler verilebilir.  
  
 `public` `dbo` Uygulamanız için güvenlik tasarlarken rolü, Kullanıcı hesabını ve hesabı da göz önünde bulundurmanız gerekir `guest` .  
  
### <a name="the-public-role"></a>Ortak rol  
 `public`Rol, sistem veritabanlarını içeren her veritabanında bulunur. Bırakılamaz ve bundan Kullanıcı ekleyemez veya kaldıramazsınız. Role verilen izinler `public` , varsayılan olarak role ait olduklarından diğer tüm kullanıcılar ve roller tarafından devralınır `public` . `public`Yalnızca tüm kullanıcıların sahip olmasını istediğiniz izinleri verin.  
  
### <a name="the-dbo-user-account"></a>Dbo kullanıcı hesabı  
 `dbo`Veya veritabanı sahibi, veritabanındaki tüm etkinlikleri gerçekleştirmek için izinleri kapsanan bir kullanıcı hesabıdır. `sysadmin`Sabit sunucu rolünün üyeleri otomatik olarak öğesine eşlenir `dbo` .  
  
> [!NOTE]
> `dbo`Ayrıca, SQL Server ' de [sahiplik ve Kullanıcı şeması ayrımı](ownership-and-user-schema-separation-in-sql-server.md)bölümünde açıklandığı gibi bir şemanın adıdır.  
  
 `dbo`Kullanıcı hesabı, `db_owner` sabit veritabanı rolüyle genellikle karıştırılır. Kapsamı `db_owner` bir veritabanıdır; kapsamı `sysadmin` tüm sunucu olur. `db_owner`Roldeki üyelik `dbo` kullanıcı ayrıcalıklarını karşılamıyor.  
  
### <a name="the-guest-user-account"></a>Konuk Kullanıcı hesabı  
 Bir kullanıcının kimliği doğrulandıktan ve bir SQL Server örneğinde oturum açmasına izin verildiğinde, kullanıcının erişmesi gereken her veritabanında ayrı bir kullanıcı hesabının olması gerekir. Her veritabanında bir kullanıcı hesabının gerekli olması, kullanıcıların bir SQL Server örneğine bağlanmasını ve bir sunucudaki tüm veritabanlarına erişmelerini engeller. Veritabanındaki bir kullanıcı hesabının varlığı, veritabanı `guest` Kullanıcı hesabı olmadan bir veritabanına erişmek için bir oturum açmaya izin vererek bu gereksinimi ortadan kaldırarak.  
  
 `guest`Hesap, tüm SQL Server sürümlerindeki yerleşik bir hesaptır. Varsayılan olarak, yeni veritabanlarında devre dışıdır. Etkinleştirilirse, Transact-SQL REVOKE CONNECT FROM KONUĞUNU yürüterek bağlantı iznini iptal ederek devre dışı bırakabilirsiniz.  
  
> [!IMPORTANT]
> Hesabı kullanmaktan kaçının `guest` ; kendi veritabanı izinleri olmayan tüm oturumlar, bu hesaba verilen veritabanı izinlerini elde eder. Hesabı kullanmanız gerekiyorsa `guest` , en düşük izinleri verin.  
  
 SQL Server oturum açma bilgileri, kullanıcılar ve roller hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Description|  
|--------------|-----------------|  
|[Veritabanı altyapısı Izinleri ile çalışmaya başlama](/sql/relational-databases/security/authentication-access/getting-started-with-database-engine-permissions)|Sorumluları, rolleri, kimlik bilgilerini, securables ve izinleri tanımlayan konuların bağlantılarını içerir.|  
|[Sorumlular](/sql/relational-databases/security/authentication-access/principals-database-engine)|Sorumluları açıklar ve sunucu ve veritabanı rollerini açıklayan konuların bağlantılarını içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)
- [SQL Server’da Kimlik Doğrulaması](authentication-in-sql-server.md)
- [SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı](ownership-and-user-schema-separation-in-sql-server.md)
- [SQL Server’da Yetkilendirme ve İzinler](authorization-and-permissions-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
