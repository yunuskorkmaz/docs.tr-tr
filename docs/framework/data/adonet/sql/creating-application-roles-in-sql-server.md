---
title: SQL Server’da Uygulama Rolleri Oluşturma
ms.date: 03/30/2017
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
ms.openlocfilehash: 7934c58f837cd5a4b01f823701025190be3dfe6d
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910720"
---
# <a name="creating-application-roles-in-sql-server"></a>SQL Server’da Uygulama Rolleri Oluşturma
Uygulama rolleri, bir veritabanı rolü ya da kullanıcı yerine bir uygulama için izinler atamak için bir yol sağlar. Kullanıcılar veritabanına bağlanmak, uygulama rolü etkinleştirmek ve uygulamaya verilen izinler varsayılır. Uygulama rolü için verilen izinler bağlantı süresi boyunca yürürlükte değil.  
  
> [!IMPORTANT]
>  Bir istemci uygulama bir uygulama rolü adı ve bağlantı dizesinde parola sağlayan olduğunda uygulama rolleri etkinleştirilir. Parola, istemci bilgisayarda depolanan gerekir çünkü iki katmanlı uygulamada bir güvenlik açığı sunar. Bir üç katmanlı uygulamada, uygulamanın kullanıcılar tarafından erişilemez böylece parola depolayabilirsiniz.  
  
## <a name="application-role-features"></a>Uygulama rolü özellikleri  
 Uygulama rolleri aşağıdaki özelliklere sahiptir:  
  
- Veritabanı rolünden farklı olarak, uygulama rolleri hiç üye içerir.  
  
- Uygulama rolleri, uygulamanın uygulama rolü adı ve parola sağlayan olduğunda etkinleşir `sp_setapprole` sistem saklı yordamı.  
  
- Parola istemci bilgisayarında depolanır ve çalışma zamanında sağlanan; bir uygulama rolü içinde SQL Server etkinleştirilemiyor.  
  
- Parola şifrelenmez. Parola parametresi tek yönlü bir karma depolanır.  
  
- Sonra uygulama rolü edinilen izinleri bağlantı süresi boyunca yürürlükte kalır.  
  
- Uygulama rolü için izinleri devralır `public` rol.  
  
- Bir üyesi değilse `sysadmin` sabit sunucu rolünün bir uygulama rolü etkinleştirir, güvenlik bağlamı, uygulama rolü için bağlantının süresi boyunca geçer.  
  
- Oluşturursanız, bir `guest` hesabı uygulama rolü olan bir veritabanında herhangi birinin, çağırma oturum açma bilgileri veya uygulama rolü için bir veritabanı kullanıcı hesabı oluşturmanız gerekmez. Uygulama rolleri başka bir veritabanı yalnızca Eğer doğrudan erişebileceği bir `guest` hesap ikinci veritabanında var  
  
- Oturum açma adları, SYSTEM_USER gibi döndüren yerleşik işlevler uygulama rolü çağrılan oturum açma adını döndürür. Veritabanı kullanıcı adları döndüren yerleşik işlevler uygulama rolü adını döndürür.  
  
### <a name="the-principle-of-least-privilege"></a>En düşük öncelik ilkesini  
 Parola tehlikeye durumunda uygulama rolleri yalnızca gerekli izinleri verilmelidir. İzinleri `public` rol uygulama rolü kullanarak herhangi bir veritabanında iptal. Devre dışı `guest` uygulama rolü arayanlar erişmesini istemediğiniz herhangi bir veritabanı hesabında.  
  
### <a name="application-role-enhancements"></a>Uygulama rolü geliştirmeleri  
 Bağlantı havuzu devre dışı bırakmak için gereğini ortadan kaldıran bir uygulama rolü etkinleştirdikten sonra özgün çağrıyı yapana tekrar yürütme bağlamı değiştirilebilir. `sp_setapprole` Yordamının çağrıda bulunanı hakkında bağlam bilgilerini içeren bir tanımlama bilgisi oluşturur, yeni bir seçenek vardır. Çağırarak oturum döndürebilirsiniz `sp_unsetapprole` yordamı, tanımlama bilgisi geçirme.  
  
## <a name="application-role-alternatives"></a>Uygulama rolü alternatifleri  
 Uygulama rolleri, güvenlik olası bir güvenlik açığı sunan bir parolanın bağlıdır. Parolalar uygulama koduna katıştırılmış tarafından kullanıma sunulan veya diskte kaydedildi.  
  
 Aşağıdaki alternatifleri isteyebilirsiniz.  
  
- EXECUTE AS ile değiştirmeyi kullanın bağlamı ile tanımlama bilgisi NO REVERT ve onun yan tümceleri deyimiyle. Bir kullanıcı hesabı için bir oturum açma eşlenmemiş bir veritabanı oluşturabilirsiniz. Ardından bu hesap için izinleri atayın. Çünkü bu izni tabanlı, parola tabanlı oturum açma daha az kullanıcı ile EXECUTE AS kullanarak daha güvenlidir. Daha fazla bilgi için [ile SQL Server'da kimliğe bürünme izinlerini özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Saklı yordamlar yalnızca yordamları yürütme için izin verme sertifikalarla oturum açın. Daha fazla bilgi için [SQL Server'da saklı yordam imzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Uygulama rolleri](/sql/relational-databases/security/authentication-access/application-roles)|SQL Server 2008'de uygulama rolleri oluşturma ve açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
