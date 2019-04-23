---
title: SQL Server’da Sunucu ve Veritabanı Rolleri
ms.date: 03/30/2017
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
ms.openlocfilehash: e2d0de08f23bc3767e11de31c4ded4a326d060a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087982"
---
# <a name="server-and-database-roles-in-sql-server"></a>SQL Server’da Sunucu ve Veritabanı Rolleri
Tüm SQL Server sürümleri için bireysel kullanıcılar yerine bir rol veya kullanıcı grubu için izinler atamak izin veren rol tabanlı güvenliği kullanın. Sabit sunucu ve sabit veritabanı rollerine atanmış izinler sabit kümesine sahiptir.  
  
## <a name="fixed-server-roles"></a>Sabit sunucu rolleri  
 Sabit sunucu rolleri, izinler ve sunucu çapında kapsam sabit kümesine sahiptir. SQL Server yönetiminde kullanılmak için tasarlanmıştır ve atanmış izinleri değiştirilemez. Oturum açma bilgileri, bir veritabanında bir kullanıcı hesabı zorunda kalmadan sabit sunucu rollerine atanabilir.  
  
> [!IMPORTANT]
>  `sysadmin` Sabit sunucu rolünün diğer tüm rolleri kapsar ve sahip sınırsız kapsam. Yüksek derecede güvenilen olmadıkları sürece bu role sorumluları eklemeyin. `sysadmin` Rol üyeleri, tüm server veritabanları ve kaynaklar değiştirilemeyen yönetici ayrıcalıklarına sahip.  
  
 Sabit sunucu rollerine kullanıcı ekleme, seçici olun. Örneğin, `bulkadmin` rolü, veri bütünlüğünü tehlikeye atabilir bir tabloya herhangi bir yerel dosya içeriğini eklemesini sağlar. Sabit sunucu rolleri ve izinleri tam listesi için SQL Server Books Online'a bakın.  
  
## <a name="fixed-database-roles"></a>Sabit veritabanı rolleri  
 İzinleri grupları kolayca yönetmesine olanak tanımak için tasarlanmıştır izinleri önceden tanımlı bir dizi sabit veritabanı rollerine sahip. Üyeleri `db_owner` rolü veritabanı üzerinde tüm yapılandırma ve bakım etkinlikleri gerçekleştirebilir.  
  
 Önceden tanımlanmış roller, SQL Server hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Sunucu düzeyinde roller](/sql/relational-databases/security/authentication-access/server-level-roles)|Sabit sunucu rolleri ve SQL Server'da bunlarla ilişkili izinleri açıklar.|  
|[Veritabanı düzeyinde roller](/sql/relational-databases/security/authentication-access/database-level-roles)|Sabit veritabanı rolleri ve bunlarla ilişkili izinleri açıklar.|  
  
## <a name="database-roles-and-users"></a>Veritabanı rolleri ve kullanıcıları  
 Veritabanı nesneleri ile çalışmak için oturum açma bilgileri veritabanı kullanıcı hesaplarına eşlenmesi gerekir. Veritabanı kullanıcıları, bu rolleri ile ilişkilendirilmiş tüm izin kümeleri devralan veritabanı rollerine sonra eklenebilir. Tüm izinler verilebilir.  
  
 De dikkate almanız gereken `public` rolü `dbo` kullanıcı hesabı ve `guest` hesap güvenliği için uygulamanızı tasarlarken.  
  
### <a name="the-public-role"></a>Ortak rol  
 `public` Rolü sistem veritabanları içeren her veritabanında yer alan. Bırakılamaz ve ekleyemez veya kullanıcıları kaldırın. Verilen izinler `public` rol devralınır diğer tüm kullanıcılar ve roller tarafından ait olduklarından `public` varsayılan rol. GRANT `public` tüm kullanıcıların sahip olmasını istediğiniz izinleri yalnızca.  
  
### <a name="the-dbo-user-account"></a>Kullanıcı hesabına dbo  
 `dbo`, Veya veritabanı sahibi, veritabanında tüm etkinlikleri gerçekleştirmek için gerekli izinlere örtük bir kullanıcı hesabıdır. Üyeleri `sysadmin` sabit sunucu rolü için otomatik olarak eşleştirilir `dbo`.  
  
> [!NOTE]
>  `dbo` Ayrıca bir şema içinde açıklandığı gibi adıdır [sahiplik ve kullanıcı şeması ayrımı SQL Server'da](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md).  
  
 `dbo` Kullanıcı hesabı ile yanıltıcı sık `db_owner` sabit veritabanı rolü. Kapsamı `db_owner` ; veritabanı kapsamı `sysadmin` tüm sunucusudur. Üyelik `db_owner` rol confer değil `dbo` kullanıcı ayrıcalıkları.  
  
### <a name="the-guest-user-account"></a>Konuk kullanıcı hesabı  
 Bir kullanıcı kimlik doğrulaması ve SQL Server örneğine oturum açmasına izin sonra ayrı bir kullanıcı hesabı kullanıcının sahip olduğu için her bir veritabanındaki bulunmalıdır erişim. Her veritabanında bir kullanıcı hesabı gerektiren SQL Server örneğine bağlanma ve bir sunucudaki tüm veritabanlarına erişmesini engeller. Varlığı bir `guest` veritabanındaki kullanıcı hesabı, bir veritabanına erişmek için bir veritabanı kullanıcı hesabı olmayan bir oturum açma sağlayarak bu gereksinim kaçınmanızı sağlar.  
  
 `guest` Yerleşik bir hesap SQL Server'ın tüm sürümlerinde hesabıdır. Varsayılan olarak, yeni veritabanlarında devre dışı. Etkinleştirilirse, size, Transact-SQL iptal BAĞLANMAK gelen KONUK deyimi yürüterek kendi CONNECT izni iptal etme devre dışı bırakabilirsiniz.  
  
> [!IMPORTANT]
>  Kullanmaktan kaçının `guest` hesabı; kendi veritabanı izinleri olmayan tüm oturumları bu hesap için veritabanı izinler alın. Kullanmanız gerekirse `guest` hesap, minimum izinleri verin.  
  
 SQL Server oturum açma bilgileri, kullanıcılar ve roller hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Veritabanı altyapısı izinleri ile çalışmaya başlama](/sql/relational-databases/security/authentication-access/getting-started-with-database-engine-permissions)|Sorumluları, rol, kimlik bilgileri, güvenliği sağlanabilir öğeler ve izinleri açıklayan konulara bağlantılar içerir.|  
|[İlkeleri](/sql/relational-databases/security/authentication-access/principals-database-engine)|İlkeleri açıklanır ve sunucu ve veritabanı rolleri açıklayan konulara bağlantılar içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [SQL Server’da Kimlik Doğrulaması](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)
- [SQL Server’da Yetkilendirme ve İzinler](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
