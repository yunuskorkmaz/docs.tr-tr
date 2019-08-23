---
title: SQL Server’da Kimlik Doğrulaması
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 1723552a48ebfa41e8d6a0f963154fc3b864119d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957488"
---
# <a name="authentication-in-sql-server"></a>SQL Server’da Kimlik Doğrulaması
SQL Server, Windows kimlik doğrulama modu ve karma mod olmak üzere iki kimlik doğrulama modunu destekler.  
  
- Windows kimlik doğrulaması varsayılandır ve genellikle tümleşik güvenlik olarak adlandırılır çünkü bu SQL Server güvenlik modeli Windows ile sıkı bir şekilde tümleşiktir. Belirli Windows Kullanıcı ve grup hesaplarının SQL Server oturum açması için güvenilir. Önceden yetkilendirilmiş olan Windows kullanıcılarının ek kimlik bilgileri sunmak zorunda değildir.  
  
- Karma mod, hem Windows hem de SQL Server tarafından kimlik doğrulamasını destekler. Kullanıcı adı ve parola çiftleri SQL Server içinde tutulur.  
  
> [!IMPORTANT]
> Mümkün olan yerlerde Windows kimlik doğrulaması kullanmanızı öneririz. Windows kimlik doğrulaması, SQL Server kullanıcıların kimliğini doğrulamak için bir dizi şifrelenmiş ileti kullanır. SQL Server oturumlar kullanıldığında, SQL Server oturum açma adları ve şifreli parolalar ağ üzerinden geçirilir ve bu da daha az güvenli hale gelir.  
  
 Windows kimlik doğrulaması ile kullanıcılar zaten Windows 'da oturum açar ve SQL Server için ayrı olarak oturum açmanız gerekmez. Aşağıda `SqlConnection.ConnectionString` , kullanıcıların bir Kullanıcı adı veya parola sağlaması gerekmeden Windows kimlik doğrulaması belirtilir.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
> Oturum açmalar veritabanı kullanıcılarından farklıdır. Ayrı bir işlemde veritabanı kullanıcıları veya rolleri için oturum açma işlemlerini veya Windows gruplarını eşlemeniz gerekir. Daha sonra kullanıcılara veya rollere veritabanı nesnelerine erişim izni verirsiniz.  
  
## <a name="authentication-scenarios"></a>Kimlik doğrulama senaryoları  
 Windows kimlik doğrulaması, genellikle aşağıdaki durumlarda en iyi seçenektir:  
  
- Bir etki alanı denetleyicisi vardır.  
  
- Uygulama ve veritabanı aynı bilgisayarlardır.  
  
- SQL Server Express veya LocalDB örneğini kullanıyorsunuz.  
  
 SQL Server oturum açma işlemleri genellikle aşağıdaki durumlarda kullanılır:  
  
- Bir çalışma grubunuz varsa.  
  
- Kullanıcılar farklı, güvenilir olmayan etki alanlarından bağlanır.  
  
- ASP.NET gibi Internet uygulamaları.  
  
> [!NOTE]
> Windows kimlik doğrulamasının belirtilmesi SQL Server oturum açma işlemlerini devre dışı bırakmaz. Yüksek ayrıcalıklı SQL Server oturumlarını devre dışı bırakmak için ALTER LOGıN DISABLE Transact-SQL deyimini kullanın.  
  
## <a name="login-types"></a>Oturum açma türleri  
 SQL Server üç oturum açma türünü destekler:  
  
- Yerel bir Windows Kullanıcı hesabı veya güvenilen etki alanı hesabı. SQL Server Windows Kullanıcı hesaplarının kimliğini doğrulamak için Windows 'a bağımlıdır.  
  
- Windows grubu. Bir Windows grubuna erişim verilmesi, grubun üyesi olan tüm Windows kullanıcı oturumlarına erişim verir.  
  
- SQL Server oturum açma. SQL Server, oturum açma girişimlerini doğrulamak için iç kimlik doğrulama yöntemlerini kullanarak hem Kullanıcı adını hem de parolanın karmasını ana veritabanında depolar.  
  
> [!NOTE]
> SQL Server, sertifikalardan veya yalnızca kod imzalama için kullanılan asimetrik anahtarlardan oluşturulan oturum açma işlemleri sağlar. SQL Server bağlanmak için kullanılamaz.  
  
## <a name="mixed-mode-authentication"></a>Karma mod kimlik doğrulaması  
 Karma mod kimlik doğrulaması kullanmanız gerekiyorsa, SQL Server depolanan SQL Server oturum açma bilgileri oluşturmanız gerekir. Daha sonra çalışma zamanında SQL Server Kullanıcı adı ve parola sağlamalısınız.  
  
> [!IMPORTANT]
> SQL Server, ("Sistem Yöneticisi" `sa` kısaltması) adlı SQL Server bir oturum açma ile yüklenir. `sa` Oturum açmak için güçlü bir parola atayın ve uygulamanızdaki `sa` oturum açma bilgilerini kullanmayın. Oturum açma, tüm sunucuda `sysadmin` yönetici kimlik bilgilerini geri alınamaz olan sabit sunucu rolüyle eşlenir. `sa` Bir saldırgan sistem yöneticisi olarak erişim kazanırsa olası hasara yönelik bir sınır yoktur. Windows `BUILTIN\Administrators` grubunun (yerel yönetici grubu) tüm üyeleri, varsayılan olarak `sysadmin` rolün üyeleridir, ancak bu rolden kaldırılabilir.  
  
 SQL Server, [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] veya sonraki sürümlerde çalışırken SQL Server oturum açma işlemleri için Windows parola ilkesi mekanizmaları sağlar. Parola karmaşıklığı ilkeleri, olası parola sayısını artırarak deneme yanılma saldırılarını ortadan kaldırır. SQL Server, ' de [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] kullanılan karmaşıklık ve süre sonu ilkelerini SQL Server içinde kullanılan parolalara uygulayabilir.  
  
> [!IMPORTANT]
> Bağlantı dizelerini Kullanıcı girişinden bitiştirme, bağlantı dizesi ekleme saldırısına karşı savunmasız bırakabilir. Çalışma zamanında sözdizimsel olarak geçerli bağlantı dizeleri oluşturmak için öğesini kullanın. <xref:System.Data.SqlClient.SqlConnectionStringBuilder> Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Sorumlusu](/sql/relational-databases/security/authentication-access/principals-database-engine)|SQL Server oturum açma işlemlerini ve diğer güvenlik sorumlularını açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Veri Kaynağına Bağlanma](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Bağlantı Dizeleri](../../../../../docs/framework/data/adonet/connection-strings.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
