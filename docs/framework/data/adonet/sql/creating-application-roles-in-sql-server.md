---
title: "SQL Server uygulama rolleri oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
caps.latest.revision: "9"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a6c8027e3cbf7bcef3bbe36ba381a08b650516bc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="creating-application-roles-in-sql-server"></a>SQL Server uygulama rolleri oluşturma
Uygulama rolleri veritabanı rolü veya kullanıcı yerine bir uygulama izinleri atamak için bir yol sağlar. Kullanıcılar veritabanına bağlanmak, uygulama rolünü etkinleştirmek ve uygulamaya verilen izinler varsayalım. Uygulama rolü verilen izinler yürürlükte bağlantısı süresince değil.  
  
> [!IMPORTANT]
>  Bir istemci uygulaması bir uygulama rolü adı ve parola bağlantı dizesindeki sağlayan olduğunda uygulama rolleri etkinleştirilir. Parola istemci bilgisayarda depolanması gerekir çünkü iki katmanlı uygulamada bir güvenlik açığı sunar. Böylece uygulama kullanıcılar tarafından erişilemez, bir üç katmanlı uygulama parolası depolayabilirsiniz.  
  
## <a name="application-role-features"></a>Uygulama rolü özellikleri  
 Uygulama rolleri aşağıdaki özelliklere sahiptir:  
  
-   Veritabanı rolleri farklı olarak, hiçbir üyeleri uygulama rolleri içerir.  
  
-   Uygulama rolleri uygulama rol adı ve parola için uygulamanın sağladığı olduğunda etkinleşir `sp_setapprole` sistem saklı yordamı.  
  
-   Parola istemci bilgisayarda depolanan ve çalışma zamanında sağlanan; bir uygulama rolü içinde SQL Server etkinleştirilemiyor.  
  
-   Parola şifrelenmez. Parametre parolası tek yönlü bir karma depolanır.  
  
-   Etkinleştirilen sonra uygulama rolü edinilen izinleri bağlantı boyunca etkin kalır.  
  
-   Uygulama rolü verilen izinler devralır `public` rol.  
  
-   Bir üyesi değilse `sysadmin` sabit sunucu rolünün bir uygulama rolü etkinleştirir, güvenlik bağlamı, uygulama rolü bağlantı boyunca geçer.  
  
-   Oluşturursanız, bir `guest` hesap bir uygulama rolü olan bir veritabanında, uygulama rolü veya onu çağırma oturumlarının herhangi bir veritabanı kullanıcı hesabı oluşturma gerekmez. Uygulama rolleri başka bir veritabanı yalnızca IF doğrudan erişebileceği bir `guest` hesap ikinci veritabanında var  
  
-   Oturum açma adları, SYSTEM_USER gibi dönüş yerleşik işlevler uygulama rolü çağrılan oturum açma adını döndürür. Veritabanı kullanıcı adlarını döndürmek yerleşik işlevler uygulama rolün adını döndürür.  
  
### <a name="the-principle-of-least-privilege"></a>En az ayrıcalık prensibi  
 Parola ihlal edilmesi durumunda uygulama rolleri yalnızca gerekli izinleri verilmelidir. İzinleri `public` rol bir uygulama rolü kullanarak herhangi bir veritabanında iptal. Devre dışı `guest` herhangi bir veritabanı hesabı erişmesini Arayanların uygulama rolünün istemiyorsanız.  
  
### <a name="application-role-enhancements"></a>Uygulama rolü geliştirmeleri  
 Yürütme bağlamı bağlantı havuzu devre dışı bırakmak için gereken kaldırma bir uygulama rolü etkinleştirdikten sonra özgün çağırana değiştirilebilir. `sp_setapprole` Yordamı çağıran hakkında bağlam bilgilerini içeren bir tanımlama bilgisi oluşturur Yeni bir seçenek vardır. Çağırarak oturum döndürebilirsiniz `sp_unsetapprole` yordamı, tanımlama bilgisi geçirme.  
  
## <a name="application-role-alternatives"></a>Uygulama rolü alternatifleri  
 Uygulama rolleri olası bir güvenlik açığı sunan bir parola güvenlik üzerinde bağlıdır. Parolalar uygulama kodunda katıştırılmış tarafından kullanıma sunulan veya diske kaydedilir.  
  
 Aşağıdaki alternatifleri isteyebilirsiniz.  
  
-   Kullanım bağlam EXECUTE AS değiştirme NO REVERT ve tanımlama bilgisi ile onun yan tümceleri deyimiyle. Bir oturum eşlenmemiş bir veritabanında bir kullanıcı hesabı oluşturabilirsiniz. Ardından bu hesap için izinleri atayın. Çünkü izni tabanlı, parola tabanlı oturum açma daha az kullanıcıyla EXECUTE AS kullanarak daha güvenlidir. Daha fazla bilgi için bkz: [kimliğe bürünme SQL Server'daki özelleştirme izinlerle](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
-   Saklı yordamlar yordamları yürütmek için yalnızca izin verme sertifikaları ile oturum açın. Daha fazla bilgi için bkz: [imzalama saklı yordamlar SQL Server'daki](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Uygulama rolleri](http://msdn.microsoft.com/library/ms190998.aspx) SQL Server Çevrimiçi Kitapları'nda|Oluşturmayı ve SQL Server 2008'de uygulama rolleri kullanmayı açıklar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
