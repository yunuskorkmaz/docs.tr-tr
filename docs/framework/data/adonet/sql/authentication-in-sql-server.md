---
title: SQL Server kimlik doğrulaması
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: f2d290d22d27c43cf7fb3250bf7898e8260dce2b
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472393"
---
# <a name="authentication-in-sql-server"></a>SQL Server kimlik doğrulaması
SQL Server iki kimlik doğrulama modu, Windows kimlik doğrulama modu ve karma mod destekler.  
  
-   Windows kimlik doğrulaması varsayılandır ve bu SQL Server güvenlik modeli sıkı bir şekilde Windows ile tümleşik olduğundan genellikle tümleşik güvenlik adlandırılır. Belirli Windows kullanıcı ve grup hesaplarını SQL Server'da oturum açma için güvenilir. Önceden doğrulanmış Windows kullanıcılar ek kimlik bilgileri sunmak gerekmez.  
  
-   Karma mod hem Windows hem SQL Server kimlik doğrulamasını destekler. Kullanıcı adı ve parola çiftleri SQL Server'ın içinde saklanır.  
  
> [!IMPORTANT]
>  Mümkün olduğunda Windows kimlik doğrulaması kullanmanızı öneririz. Windows kimlik doğrulaması şifrelenmiş iletileri bir dizi SQL Server'da kullanıcıların kimliklerini doğrulamak için kullanır. SQL Server oturumları kullanıldığında, SQL Server oturum açma adları ve şifrelenmiş parolalar daha az güvenli hale getirir ağ üzerinden iletilir.  
  
 Windows kimlik doğrulaması, kullanıcıların zaten Windows'da oturum ve ayrı olarak SQL Server'da oturum gerekmez. Aşağıdaki `SqlConnection.ConnectionString` gerek kalmadan Windows kimlik doğrulaması belirtir bir kullanıcı adı veya parola.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Oturum açma bilgileri, veritabanı kullanıcıları farklıdır. Veritabanı kullanıcılar ya da ayrı bir işlemle roller için oturum açma veya Windows grupları eşlemeniz gerekir. Veritabanı nesneleri erişmek için kullanıcı veya rol ardından izinleri verin.  
  
## <a name="authentication-scenarios"></a>Kimlik doğrulama senaryoları  
 Windows kimlik doğrulaması, genellikle en iyi seçenek aşağıdaki durumlarda şöyledir:  
  
-   Bir etki alanı denetleyicisi yoktur.  
  
-   Uygulama ve veritabanı aynı bilgisayarda bulunur.  
  
-   SQL Server Express veya yerel veritabanı örneği kullanıyor.  
  
 SQL Server oturumları genellikle aşağıdaki durumlarda kullanılır:  
  
-   Bir çalışma grubu varsa.  
  
-   Kullanıcılar farklı, güvenilmeyen etki alanlarından bağlanır.  
  
-   Internet uygulamaları gibi [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  Belirterek Windows kimlik doğrulaması, SQL Server oturumları devre dışı bırakmaz. ALTER oturum açma devre dışı kullanmak [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] yüksek ayrıcalıklı SQL Server oturumları devre dışı bırakmak için deyimi.  
  
## <a name="login-types"></a>Oturum açma türleri  
 SQL Server oturumu açma üç türlerini destekler:  
  
-   Yerel Windows kullanıcı hesabı veya güvenilen etki alanı hesabı. SQL Server, Windows kullanıcı hesaplarının kimliğini doğrulamak amacıyla Windows kullanır.  
  
-   Windows grubu. Bir Windows grubuna erişim verilirken grubunun üyesi olan tüm Windows kullanıcı oturumları erişim verir.  
  
-   SQL Server oturum açma. SQL Server kullanıcı adı ve parola karmasını ana veritabanında oturum açma denemesi doğrulamak için iç kimlik doğrulama yöntemlerini kullanarak depolar.  
  
> [!NOTE]
>  SQL Server, sertifikalar veya yalnızca kod imzalama için kullanılan asimetrik anahtarlar oluşturulan oturum açma bilgileri sağlar. SQL Server'a bağlanmak için kullanılamaz.  
  
## <a name="mixed-mode-authentication"></a>Karma mod kimlik doğrulaması  
 Karma mod kimlik doğrulaması kullanmanız gerekiyorsa, SQL sunucusunda depolanan SQL Server oturumları oluşturmanız gerekir. Ardından çalışma zamanında SQL Server kullanıcı adı ve parolasını sağlamanız gerekir.  
  
> [!IMPORTANT]
>  SQL Server adlandırılmış bir SQL Server oturum açma ile yükler `sa` ("sistem yöneticisinin" kısaltma). Güçlü bir parola atayın `sa` oturum açma ve kullanmayın `sa` uygulamanızda oturum açma. `sa` Oturum açma eşlendiğini `sysadmin` tüm sunucuda değiştirilemeyen yönetici kimlik bilgilerine sahip sabit sunucu rolü. Bir saldırganın bir sistem yöneticisi olarak erişim sağlarsa potansiyel hasarı herhangi bir sınırı vardır. Tüm üyeleri Windows `BUILTIN\Administrators` grubu (yerel yönetici'nin grup) üyeleri olan `sysadmin` rol varsayılan olarak, ancak bu rolden kaldırılabilir.  
  
 SQL Server çalışırken SQL Server oturumları için Windows parola ilkesi mekanizmaları sağlar [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] veya sonraki sürümler. Parola karmaşıklık ilkeleri, deneme yanılma saldırıları mümkün olan parola sayısını artırarak engellenmesine için tasarlanmıştır. SQL Server kullanılan aynı karmaşıklık ve sona erme tarihi ilkeleri uygulayabilir [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] için SQL Server içinde kullanılan parolalar.  
  
> [!IMPORTANT]
>  Bağlantı dizeleri kullanıcı girişinden birleştirme bir bağlantı dizesi ekleme saldırısına karşı savunmasız bırakabilir. Kullanım <xref:System.Data.SqlClient.SqlConnectionStringBuilder> çalışma zamanında sözdizimsel olarak geçerli bir bağlantı dizesi oluşturmak için. Daha fazla bilgi için bkz: [bağlantı dizesi oluşturucular](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Asıl adlar](http://msdn.microsoft.com/library/bb543165.aspx) SQL Server Çevrimiçi Kitapları'nda|Oturum açma bilgileri ve SQL Server'daki diğer güvenlik sorumluları açıklar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Veri Kaynağına Bağlanma](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Bağlantı Dizeleri](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
