---
title: "SQL Server'da veritabanları arası erişimini etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 720c4c8eecc20b971eb9ecf1abb85da1e72e3c54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-cross-database-access-in-sql-server"></a>SQL Server'da veritabanları arası erişimini etkinleştirme
Veritabanları arası sahiplik zincirleme nesneleri başka bir veritabanındaki bir veritabanı yordamda bağlı olduğunda oluşur. Tüm nesne sahiplerini aynı oturum açma hesabıyla eşlenir kırık sahiplik zinciri gerektirir veritabanları arası sahiplik zinciri içinde tek bir veritabanı, sahipliği zincirleme olarak aynı şekilde çalışır. Kaynak veritabanındaki kaynak nesnesi ve hedef veritabanlarına hedef nesneleri aynı oturum açma hesabı tarafından sahip olunan, SQL Server hedef nesneler üzerindeki izinleri denetlemez.  
  
## <a name="off-by-default"></a>Varsayılan olarak kapalıdır  
 Veritabanları arasında sahipliği zincirleme varsayılan olarak kapalıdır. Microsoft, aşağıdaki güvenlik risklerini kullanıma sunan çünkü veritabanları arası sahiplik zincirleme devre dışı bırakmak önerir:  
  
-   Veritabanı sahipleri ve üyeleri `db_ddladmin` veya `db_owners` veritabanı rolleri, diğer kullanıcılar tarafından sahip olunan nesneler oluşturabilir. Bu nesneler, büyük olasılıkla diğer veritabanlarındaki nesneler hedefleyebilirsiniz. Bu veritabanları arası sahiplik zincirleme etkinleştirirseniz, bu kullanıcılar tüm veritabanlarındaki veriler ile tam olarak güvenmelidir anlamına gelir.  
  
-   CREATE DATABASE iznine sahip kullanıcılar, yeni veritabanları oluşturabilir ve varolan veritabanları ekleyebilirsiniz. Veritabanları arası sahiplik zincirleme etkinse, bu kullanıcılar oluşturdukları yeni oluşturulan veya ekli veritabanlarından bunlar ayrıcalıklara sahip olmayabilir diğer veritabanlarındaki nesnelere erişebilir.  
  
## <a name="enabling-cross-database-ownership-chaining"></a>Veritabanları arası sahiplik zincirleme etkinleştirme  
 Veritabanları arası sahiplik zincirleme yüksek ayrıcalıklı kullanıcıların tam olarak güvenebildiğiniz ortamlarda yalnızca etkinleştirilmiş olmalıdır. Tüm veritabanları için veya seçmeli olarak kullanarak belirli veritabanları için Kurulum sırasında yapılandırılabilir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] komutları `sp_configure` ve `ALTER DATABASE`.  
  
 Veritabanları arası sahiplik zincirleme seçmeli olarak yapılandırmak için kullanın `sp_configure` sunucu için devre dışı bırakma. Ardından yalnızca gerektiren veritabanları için zincirleme veritabanları arası sahiplik yapılandırmak için SET DB_CHAINING ON ile ALTER DATABASE komutunu kullanın.  
  
 Aşağıdaki örnek veritabanları arası sahiplik tüm veritabanları için zincirleme açar:  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 Aşağıdaki örnek veritabanları arası sahiplik belirli veritabanları için zincirleme açar:  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a>Dinamik SQL  
 Veritabanları arası sahiplik zincirleme, aynı kullanıcı her iki veritabanı olmadığı sürece dinamik olarak oluşturulan SQL deyimlerini yürütüldüğü durumlarda çalışmaz. Bu geçici çözüm [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] başka bir veritabanındaki verilere erişen bir saklı yordam oluşturarak ve yordam her iki veritabanlarınızda var olan bir sertifika ile imzalama. Bu kullanıcılar veritabanı erişimi ya da izin vermeden yordamı tarafından kullanılan veritabanı kaynaklarına erişmenizi sağlar.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[EXECUTE AS kullanarak veritabanı kimliğe bürünme genişletme](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) ve [arası seçeneği zincirleme DB sahipliği](http://msdn.microsoft.com/library/ms188694.aspx) [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Çevrimiçi Kitapları.|Konular açıklayan bir örneği için veritabanları arası sahiplik zincirleme yapılandırma [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET uygulamalarının güvenliğini sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server güvenlik genel bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Saklı yordamlar SQL Server'daki izinlerle yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [SQL Server'da güvenli dinamik SQL yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Saklı yordamlar SQL Server'daki imzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
