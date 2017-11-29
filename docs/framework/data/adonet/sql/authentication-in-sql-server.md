---
title: "SQL Server kimlik doğrulaması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e3b597d04ee53a094d9c50dff406f57e5fd57b00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="authentication-in-sql-server"></a>SQL Server kimlik doğrulaması
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]iki kimlik doğrulama modu, Windows kimlik doğrulama modu ve karma mod destekler.  
  
-   Windows kimlik doğrulaması varsayılandır ve genellikle tümleşik güvenlik nedeniyle adlandırılır bu [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] güvenlik modeli, Windows ile sıkı bir şekilde tümleşiktir. Belirli Windows kullanıcı ve grup hesaplarını SQL Server'da oturum açma için güvenilir. Önceden doğrulanmış Windows kullanıcılar ek kimlik bilgileri sunmak gerekmez.  
  
-   Karma mod kullanarak ve Windows tarafından kimlik doğrulaması her iki destekler [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Kullanıcı adı ve parola çiftleri içinde korunur [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]
>  Mümkün olduğunda Windows kimlik doğrulaması kullanmanızı öneririz. Windows kimlik doğrulaması, kullanıcıların kimliğini doğrulamak için bir dizi şifrelenmiş iletileri kullanır [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Zaman [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] oturumları kullanılır, [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] oturum açma adları ve parolalar daha az güvenli hale getirir ağ üzerinden geçirilir.  
  
 Windows kimlik doğrulaması, kullanıcıların zaten Windows'da oturum ve ayrı olarak çok oturum açmak zorunda değilsiniz [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Aşağıdaki `SqlConnection.ConnectionString` gerek kalmadan Windows kimlik doğrulaması belirtir bir kullanıcı adı veya parola.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Oturum açma bilgileri, veritabanı kullanıcıları farklıdır. Veritabanı kullanıcılar ya da ayrı bir işlemle roller için oturum açma veya Windows grupları eşlemeniz gerekir. Veritabanı nesneleri erişmek için kullanıcı veya rol ardından izinleri verin.  
  
## <a name="authentication-scenarios"></a>Kimlik doğrulama senaryoları  
 Windows kimlik doğrulaması, genellikle en iyi seçenek aşağıdaki durumlarda şöyledir:  
  
-   Bir etki alanı denetleyicisi yoktur.  
  
-   Uygulama ve veritabanı aynı bilgisayarda bulunur.  
  
-   Bir örneği kullanılarak [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] hızlı veya yerel veritabanı.  
  
 SQL Server oturumları genellikle aşağıdaki durumlarda kullanılır:  
  
-   Bir çalışma grubu varsa.  
  
-   Kullanıcılar farklı, güvenilmeyen etki alanlarından bağlanır.  
  
-   Internet uygulamaları gibi [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  Windows kimlik doğrulamasını devre dışı bırakmayın belirtme [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] oturum açma bilgileri. ALTER oturum açma devre dışı kullanmak [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] yüksek ayrıcalıklı devre dışı bırakmak için deyimi [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] oturum açma bilgileri.  
  
## <a name="login-types"></a>Oturum açma türleri  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]oturum açma bilgileri üç türlerini destekler:  
  
-   Yerel Windows kullanıcı hesabı veya güvenilen etki alanı hesabı. [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]Windows kullanıcı hesaplarının kimliğini doğrulamak amacıyla Windows kullanır.  
  
-   Windows grubu. Bir Windows grubuna erişim verilirken grubunun üyesi olan tüm Windows kullanıcı oturumları erişim verir.  
  
-   [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]oturum açma. [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]Kullanıcı adı ve parola karmasını oturum açma denemesi doğrulamak için iç kimlik doğrulama yöntemlerini kullanarak ana veritabanında depolar.  
  
> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]Sertifikalar veya yalnızca kod imzalama için kullanılan asimetrik anahtarlar oluşturulan oturum açma bilgileri sağlar. Bağlanmak için kullanılamaz [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
## <a name="mixed-mode-authentication"></a>Karma mod kimlik doğrulaması  
 Karma mod kimlik doğrulaması kullanmanız gerekiyorsa, oluşturmalısınız [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] SQL Server'da depolanan oturum açma. Ardından sağlamak zorunda [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] kullanıcı adı ve parola çalışma zamanında.  
  
> [!IMPORTANT]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]ile yükleyen bir [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] adlı oturum açma `sa` ("sistem yöneticisinin" kısaltma). Güçlü bir parola atayın `sa` oturum açma ve kullanmayın `sa` uygulamanızda oturum açma. `sa` Oturum açma eşlendiğini `sysadmin` tüm sunucuda değiştirilemeyen yönetici kimlik bilgilerine sahip sabit sunucu rolü. Bir saldırganın bir sistem yöneticisi olarak erişim sağlarsa potansiyel hasarı herhangi bir sınırı vardır. Tüm üyeleri Windows `BUILTIN\Administrators` grubu (yerel yönetici'nin grup) üyeleri olan `sysadmin` rol varsayılan olarak, ancak bu rolden kaldırılabilir.  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]Windows parola ilkesi mekanizmalar sağlar [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] çalışırken oturumları [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] veya sonraki sürümler. Parola karmaşıklık ilkeleri, deneme yanılma saldırıları mümkün olan parola sayısını artırarak engellenmesine için tasarlanmıştır. [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]kullanılan aynı karmaşıklık ve süre sonu ilkelerini uygulayabilirsiniz [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] içinde kullanılan parolalar için [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]
>  Bağlantı dizeleri kullanıcı girişinden birleştirme bir bağlantı dizesi ekleme saldırısına karşı savunmasız bırakabilir. Kullanım <xref:System.Data.SqlClient.SqlConnectionStringBuilder> çalışma zamanında sözdizimsel olarak geçerli bir bağlantı dizesi oluşturmak için. Daha fazla bilgi için bkz: [bağlantı dizesi oluşturucular](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Asıl adlar](http://msdn.microsoft.com/library/bb543165.aspx) içinde [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Çevrimiçi Kitapları|Oturum açma bilgileri ve diğer güvenlik sorumluları açıklar [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET uygulamalarının güvenliğini sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server'daki uygulama güvenlik senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Bir veri kaynağına bağlanma](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Bağlantı dizeleri](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
