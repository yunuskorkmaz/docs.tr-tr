---
title: SQL Server’da Kimlik Doğrulaması
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 0fb92f9e854e2a7a800335390d0195243a749b33
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959976"
---
# <a name="authentication-in-sql-server"></a>SQL Server’da Kimlik Doğrulaması
SQL Server, Windows kimlik doğrulama modu ve karma mod olmak üzere iki kimlik doğrulama modunu destekler.  
  
- Windows kimlik doğrulaması varsayılandır ve genellikle tümleşik güvenlik olarak adlandırılır çünkü bu SQL Server güvenlik modeli Windows ile sıkı bir şekilde tümleşiktir. Belirli Windows Kullanıcı ve grup hesaplarının SQL Server oturum açması için güvenilir. Önceden yetkilendirilmiş olan Windows kullanıcılarının ek kimlik bilgileri sunmak zorunda değildir.  
  
- Karma mod, hem Windows hem de SQL Server tarafından kimlik doğrulamasını destekler. Kullanıcı adı ve parola çiftleri SQL Server içinde tutulur.  
  
> [!IMPORTANT]
> Mümkün olan yerlerde Windows kimlik doğrulaması kullanmanızı öneririz. Windows kimlik doğrulaması, SQL Server kullanıcıların kimliğini doğrulamak için bir dizi şifrelenmiş ileti kullanır. SQL Server oturumlar kullanıldığında, SQL Server oturum açma adları ve şifreli parolalar ağ üzerinden geçirilir ve bu da daha az güvenli hale gelir.  
  
 Windows kimlik doğrulaması ile kullanıcılar zaten Windows 'da oturum açar ve SQL Server için ayrı olarak oturum açmanız gerekmez. Aşağıdaki `SqlConnection.ConnectionString`, kullanıcıların Kullanıcı adı veya parola sağlamasına gerek kalmadan Windows kimlik doğrulamasını belirtir.  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
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
> SQL Server, `sa` ("Sistem Yöneticisi" kısaltması) adlı SQL Server bir oturum açma ile yüklenir. `sa` oturum açma için güçlü bir parola atayın ve uygulamanızda `sa` oturum açma kullanmayın. `sa` oturum açma, tüm sunucuda yönetici kimlik bilgilerini geri alınamaz olan `sysadmin` sabit sunucu rolüne eşlenir. Bir saldırgan sistem yöneticisi olarak erişim kazanırsa olası hasara yönelik bir sınır yoktur. Windows `BUILTIN\Administrators` grubunun tüm üyeleri (yerel yönetici grubu) varsayılan olarak `sysadmin` rolünün üyeleridir, ancak bu rolden kaldırılabilir.  
  
 SQL Server, SQL Server oturum açma işlemleri için Windows parola ilke mekanizmaları sağlar. Parola karmaşıklığı ilkeleri, olası parola sayısını artırarak deneme yanılma saldırılarını ortadan kaldırır. SQL Server, SQL Server içinde kullanılan parolalara aynı karmaşıklık ve süre sonu ilkelerini uygulayabilir.  
  
> [!IMPORTANT]
> Bağlantı dizelerini Kullanıcı girişinden bitiştirme, bağlantı dizesi ekleme saldırısına karşı savunmasız bırakabilir. Çalışma zamanında sözdizimsel olarak geçerli bağlantı dizeleri oluşturmak için <xref:System.Data.SqlClient.SqlConnectionStringBuilder> kullanın. Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](../connection-string-builders.md).  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Sorumlusu](/sql/relational-databases/security/authentication-access/principals-database-engine)|SQL Server oturum açma işlemlerini ve diğer güvenlik sorumlularını açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)
- [Veri Kaynağına Bağlanma](../connecting-to-a-data-source.md)
- [Bağlantı Dizeleri](../connection-strings.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
