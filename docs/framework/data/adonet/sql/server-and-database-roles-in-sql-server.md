---
title: "Sunucusu ve SQL Server veritabanı rolleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ebae481ba2ab486066997b52d794d9bd631c8400
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="server-and-database-roles-in-sql-server"></a>Sunucusu ve SQL Server veritabanı rolleri
SQL Server'ın tüm sürümleri için tek tek kullanıcılar yerine bir rol veya grup kullanıcıya izinleri atayın izin veren rol tabanlı güvenlik kullanın. Sabit sunucu ve sabit veritabanı rollerinin atanmış izinleri sabit kümesine sahiptir.  
  
## <a name="fixed-server-roles"></a>Sabit sunucu rolleri  
 Sabit sunucu rolleri, izinler ve sunucu çapında kapsam sabit kümesine sahip. SQL Server yönetiminde kullanılmak için tasarlanmıştır ve atanmış izinleri değiştirilemez. Oturum açma bilgileri bir veritabanında bir kullanıcı hesabı olmadan sabit sunucu rollerine atanabilir.  
  
> [!IMPORTANT]
>  `sysadmin` Sabit sunucu rolünün diğer tüm rolleri kapsar ve sahip sınırsız kapsam. Yüksek oranda güvenilir olmadığı sürece bu role asıl adlar eklemeyin. `sysadmin`Rol üyeleri tüm server veritabanları ve kaynaklar değiştirilemeyen yönetici ayrıcalıklarına sahip.  
  
 Sabit sunucu rolleri için kullanıcılar eklediğinizde seçici olun. Örneğin, `bulkadmin` rol herhangi bir yerel dosya içeriğini veri bütünlüğü tehlikeye bir tabloya eklemek için kullanıcılara izin verir. Bkz: [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] sabit sunucu rolleri ve izinleri tam listesi için Books Online'a.  
  
## <a name="fixed-database-roles"></a>Sabit veritabanı rolleri  
 Sabit veritabanı rollerinin izinlerini grupları kolayca yönetmesine olanak tanımak için tasarlanmıştır izinleri önceden tanımlanmış kümesine sahiptir. Üyeleri `db_owner` rol veritabanı üzerinde tüm yapılandırma ve bakım etkinlikleri gerçekleştirebilir.  
  
 Önceden tanımlanmış roller, SQL Server hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Sunucu düzeyinde rolleri](http://msdn.microsoft.com/library/ms188659.aspx) ve [sabit sunucu rollerinin izinlerini](http://msdn.microsoft.com/library/ms175892.aspx) içinde [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Çevrimiçi Kitapları|Sabit sunucu rolleri ve onlarla ilişkili izinleri açıklar [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].|  
|[Veritabanı düzeyi rolleri](http://msdn.microsoft.com/library/ms189121.aspx) ve [sabit veritabanı rollerinin izinlerini](http://msdn.microsoft.com/library/ms189612.aspx) içinde [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Çevrimiçi Kitapları|Sabit veritabanı rollerinin ve bunlarla ilişkili izinleri açıklar|  
  
## <a name="database-roles-and-users"></a>Veritabanı rolleri ve kullanıcılar  
 Veritabanı nesneleri ile çalışması için oturum açma bilgileri veritabanı kullanıcı hesaplarına eşlenmesi gerekir. Veritabanı kullanıcıları, veritabanı rolleri için bu rol ile ilişkili tüm izin kümeleri devralma sonra eklenebilir. Tüm izinler verilebilir.  
  
 Da göz önüne almalısınız `public` rolü `dbo` kullanıcı hesabı ve `guest` hesap uygulamanız için güvenliği tasarlarken.  
  
### <a name="the-public-role"></a>Ortak rolünün  
 `public` Rolü sistem veritabanları içeren her veritabanında bulunan. Bırakılamaz ve ekleyebilir veya ondan kaldırabilirsiniz. Verilen izinler `public` rol devralındığı diğer tüm kullanıcılar ve roller tarafından ait olduklarından `public` varsayılan rol. GRANT `public` tüm kullanıcıların sahip olmasını istediğiniz izinleri yalnızca.  
  
### <a name="the-dbo-user-account"></a>Kullanıcı hesabına dbo  
 `dbo`, Veya veritabanı sahibi, kapsanan veritabanında tüm etkinlikleri gerçekleştirmek için izinlere bir kullanıcı hesabıdır. Üyeleri `sysadmin` sabit sunucu rolü için otomatik olarak eşlendi `dbo`.  
  
> [!NOTE]
>  `dbo`Ayrıca bir şema anlatıldığı gibi adıdır [sahipliği ve SQL Server'daki kullanıcı şema ayrımı](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md).  
  
 `dbo` Kullanıcı hesabı ile kafası sık `db_owner` sabit veritabanı rolü. Kapsamı `db_owner` bir veritabanı; kapsamını `sysadmin` tüm sunucusudur. Üyelik `db_owner` rol confer değil `dbo` kullanıcı ayrıcalıkları.  
  
### <a name="the-guest-user-account"></a>Konuk kullanıcı hesabı  
 Bir kullanıcı kimlik doğrulaması ve SQL Server örneğine oturum açmasına izin sonra ayrı bir kullanıcı hesabı kullanıcının sahip olduğu için her veritabanı bulunmalıdır erişim. Her veritabanında bir kullanıcı hesabı gerektiren SQL Server örneğine bağlanma ve bir sunucudaki tüm veritabanları erişen kullanıcıların engeller. Varlığını bir `guest` veritabanındaki kullanıcı hesabı, bir veritabanına erişmek için bir veritabanı kullanıcı hesabı olmadan oturum açma izin vererek bu gereksinim bozar.  
  
 `guest` SQL Server'ın tüm sürümlerinde yerleşik bir hesap hesabıdır. Varsayılan olarak, yeni veritabanları devre dışı. Etkinleştirilirse, onu Transact-SQL iptal BAĞLANMAK gelen KONUK deyimi yürüterek CONNECT izni ve iptal etme devre dışı bırakabilirsiniz.  
  
> [!IMPORTANT]
>  Kullanmaktan kaçının `guest` hesap; bu hesaba verilen veritabanı izinleri almak tüm oturumları kendi veritabanı izinleri olmadan. Kullanmanız gerekiyorsa `guest` hesap, minimum izinleri verin.  
  
 SQL Server oturum açma bilgileri, kullanıcıları ve rolleri hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Kimlik ve erişim denetimi](http://msdn.microsoft.com/library/bb510418.aspx) SQL Server Çevrimiçi Kitapları'nda|İlkeleri, roller, kimlik bilgileri, güvenliği sağlanabilir öğelerle ve izinleri açıklayan konulara bağlantılar içerir.|  
|[Asıl adlar](http://msdn.microsoft.com/library/ms181127.aspx) içinde [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Çevrimiçi Kitapları|Asıl adlar açıklar ve sunucu ve veritabanı rolleri açıklayan konulara bağlantılar içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server’da Kimlik Doğrulaması](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [SQL Server’da Yetkilendirme ve İzinler](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
