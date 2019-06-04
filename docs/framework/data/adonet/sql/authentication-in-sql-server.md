---
title: SQL Server’da Kimlik Doğrulaması
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 5809a75dbadffbd2528f6882aa586aecd3232408
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490091"
---
# <a name="authentication-in-sql-server"></a>SQL Server’da Kimlik Doğrulaması
SQL Server, iki kimlik doğrulama modu, Windows kimlik doğrulama modu ve karma mod destekler.  
  
- Windows kimlik doğrulaması varsayılandır ve bu SQL Server güvenlik modeli, sıkı bir şekilde Windows ile tümleşik olduğundan genellikle tümleşik güvenlik adlandırılır. Belirli Windows kullanıcı ve grup hesapları için SQL Server oturum açma güvenilirdir. Ek kimlik bilgileri sunmak önceden doğrulanmış Windows kullanıcılar yok.  
  
- Karma mod kimlik doğrulaması hem Windows hem de SQL Server tarafından destekler. Kullanıcı adı ve parola çiftleri SQL Server'ın içinde saklanır.  
  
> [!IMPORTANT]
>  Mümkünse, Windows kimlik doğrulaması kullanmanızı öneririz. Windows kimlik doğrulaması, SQL Server'da kullanıcıların kimliğini doğrulamak için bir dizi şifrelenmiş iletileri kullanır. SQL Server oturumları kullanıldığında, SQL Server oturum açma adları ve şifrelenmiş parolalar daha az güvenli hale getirir ağ üzerinden geçirilir.  
  
 Windows kimlik doğrulaması, kullanıcılar Windows zaten oturum açmış ve SQL Server için ayrı ayrı oturum açmak izniniz yok. Aşağıdaki `SqlConnection.ConnectionString` Windows kimlik doğrulaması, kullanıcıların bir kullanıcı adı veya parola girmelerini gerek kalmadan belirtir.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Oturum açma bilgileri, veritabanı kullanıcılarından farklıdır. Veritabanı kullanıcıları ya da ayrı bir işlemde roller için oturum açma bilgileri veya Windows grupları eşlemeniz gerekir. Veritabanı nesneleri erişmek için kullanıcı veya rol ardından izinleri verin.  
  
## <a name="authentication-scenarios"></a>Kimlik doğrulama senaryoları  
 Windows kimlik doğrulaması genellikle en iyi aşağıdaki durumlarda seçimdir:  
  
- Bir etki alanı denetleyicisi yoktur.  
  
- Uygulama ve veritabanı aynı bilgisayarda var.  
  
- Örneği veya SQL Server Express LocalDB kullanıyor.  
  
 SQL Server oturum açma bilgileri, genellikle aşağıdaki durumlarda kullanılır:  
  
- Bir çalışma grubu zaten varsa.  
  
- Kullanıcılar farklı, güvenilmeyen etki alanlarından bağlanır.  
  
- ASP.NET gibi Internet uygulamaları.  
  
> [!NOTE]
>  Belirten Windows kimlik doğrulaması, SQL Server oturumu devre dışı bırakmaz. Üst düzeyde ayrıcalıklı SQL Server oturum açma devre dışı bırakmak için ALTER oturum açma devre dışı Transact-SQL deyimini kullanın.  
  
## <a name="login-types"></a>Oturum açma türleri  
 SQL Server oturumu açma üç türlerini destekler:  
  
- Yerel Windows kullanıcı hesabı veya güvenilen etki alanı hesabı. Windows kullanıcı hesaplarının kimliğini doğrulamak için Windows üzerinde SQL Server kullanır.  
  
- Windows grubu. Bir Windows grubuna erişim verme grubun üyesi olan tüm Windows kullanıcı oturumları erişim verir.  
  
- SQL Server oturum açma. SQL Server kullanıcı adı ve parola karmasını hem ana veritabanında oturum açma denemesi doğrulamak için iç kimlik doğrulama yöntemleri kullanarak depolar.  
  
> [!NOTE]
>  SQL Server, sertifikalar veya yalnızca kod imzalama için kullanılan asimetrik anahtarlar oluşturulan oturum açma bilgileri sağlar. SQL Server'a bağlanmak için kullanılamaz.  
  
## <a name="mixed-mode-authentication"></a>Karma mod kimlik doğrulaması  
 Karma mod kimlik doğrulaması kullanmanız gerekiyorsa, SQL Server'da depolanan SQL Server oturumu açma oluşturmanız gerekir. Ardından, çalışma zamanında SQL Server kullanıcı adı ve parola sağlamanız gerekmez.  
  
> [!IMPORTANT]
>  SQL Server adlandırılmış bir SQL Server oturum açma ile yükler `sa` (bir "Sistem Yöneticisi" kısaltması). İçin güçlü bir parola atayın `sa` oturum açma ve kullanma `sa` uygulamanızdaki oturum açma. `sa` Oturum açma eşlendiğini `sysadmin` sunucunun tamamı Dönülmez yönetici kimlik bilgilerine sahip sabit sunucu rolü. Bir saldırganın bir sistem yöneticisi olarak erişim sağlarsa durumdaki potansiyel hasarı için sınır yoktur. Tüm üyeleri Windows `BUILTIN\Administrators` (yerel Yönetici grubu) grubu üyeleridir `sysadmin` rolü varsayılan olarak, ancak bu rolden kaldırabilirsiniz.  
  
 SQL Server çalıştığı sırada SQL Server oturum açma bilgileri için Windows parola ilkesi mekanizmaları sağlar [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] veya sonraki sürümler. Parola karmaşıklığı ilkeleri, olası parola sayısını artırarak deneme yanılma saldırıları önüne geçilmesine şekilde tasarlanmıştır. SQL Server kullanılan aynı karmaşıklığı ve süre sonu ilkeleri uygulayabilir [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] için SQL Server içinde kullanılan parola.  
  
> [!IMPORTANT]
>  Kullanıcı girişi bağlantı dizeleri birleştirirken bir bağlantı dizesi ekleme saldırısına karşı savunmasız bırakabilirsiniz. Kullanım <xref:System.Data.SqlClient.SqlConnectionStringBuilder> sözdizimsel açıdan geçerli bağlantı dizeleri çalışma zamanında oluşturmak için. Daha fazla bilgi için [bağlantı dizesi oluşturucular](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[İlkeleri](/sql/relational-databases/security/authentication-access/principals-database-engine)|Oturum açma bilgileri ve SQL Server'daki diğer güvenlik sorumluları açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Veri Kaynağına Bağlanma](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Bağlantı Dizeleri](../../../../../docs/framework/data/adonet/connection-strings.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
