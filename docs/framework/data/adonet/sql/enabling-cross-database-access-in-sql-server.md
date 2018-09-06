---
title: SQL Server'da veritabanları arası erişimi etkinleştirme
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 7018a500f777935d35bac0010c07258a313b08fe
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742117"
---
# <a name="enabling-cross-database-access-in-sql-server"></a>SQL Server'da veritabanları arası erişimi etkinleştirme
Veritabanları arası sahiplik zinciri, başka bir veritabanındaki nesneleri bir yordamda bir veritabanına bağlı olduğunda gerçekleşir. Tüm nesne sahipleri için aynı oturum açma hesabı eşlenmiş bir kesintisiz sahiplik zinciri gerektirir veritabanları arası sahiplik zinciri tek bir veritabanı içinde sahiplik zinciri olarak aynı şekilde çalışır. Kaynak nesne kaynak veritabanında ve hedef nesnelerin hedef veritabanları aynı oturum açma hesabı sahip olur, SQL Server hedef nesneleri izinlerini kontrol etmez.  
  
## <a name="off-by-default"></a>Varsayılan olarak kapalı  
 Veritabanlarında sahiplik zinciri varsayılan olarak kapalıdır. Microsoft, aşağıdaki güvenlik riskleri kullanıma sunduğundan veritabanları arası sahiplik zinciri devre dışı bırakma önerir:  
  
-   Veritabanı sahipleri ve üyeleri `db_ddladmin` veya `db_owners` veritabanı rolleri, diğer kullanıcılar tarafından sahip olunan nesneler oluşturabilir. Bu nesneler, büyük olasılıkla diğer veritabanlarındaki nesneler hedefleyebilirsiniz. Bu veritabanları arası sahiplik zinciri etkinleştirirseniz, bu kullanıcılar tüm veritabanlarındaki verileri ile tam olarak güvenmelidir anlamına gelir.  
  
-   CREATE DATABASE iznine sahip kullanıcılar yeni veritabanları oluşturabilir ve mevcut veritabanlarını ekleyin. Veritabanları arası sahiplik zinciri etkinse, bu kullanıcıların kendi oluşturduğu yeni oluşturduğunuz veya eklenmiş veritabanlarından bunlar ayrıcalıklara sahip olmayabilir diğer veritabanlarındaki nesnelere erişebilir.  
  
## <a name="enabling-cross-database-ownership-chaining"></a>Veritabanları arası sahiplik zinciri etkinleştirme  
 Veritabanları arası sahiplik zinciri yalnızca üst düzeyde ayrıcalıklı kullanıcıların tam olarak nerede güvenebileceği ortamlarda etkinleştirilmelidir. Tüm veritabanları için veya seçmeli olarak kullanarak belirli veritabanları için Kurulum sırasında yapılandırılabilir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] komutları `sp_configure` ve `ALTER DATABASE`.  
  
 Veritabanları arası sahiplik zinciri seçmeli olarak yapılandırmak için kullanın `sp_configure` sunucu için devre dışı bırakmak. Ardından ALTER DATABASE komutu, yalnızca gerektiren veritabanları için zincirleme veritabanları arası sahiplik yapılandırmak için SET DB_CHAINING ON ile kullanın.  
  
 Aşağıdaki örnek, tüm veritabanları için veritabanları arası sahiplik zinciri üzerinde açar:  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 Aşağıdaki örnek, belirli veritabanları için veritabanları arası sahiplik zinciri üzerinde açar:  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a>Dinamik SQL  
 Veritabanları arası sahiplik zinciri, aynı kullanıcı her iki veritabanlarında mevcut değilse, dinamik olarak oluşturulan SQL deyimleri burada yürütülür durumlarda çalışmaz. Başka bir veritabanındaki verilere erişen bir saklı yordam oluşturarak ve yordamı hem veritabanlarınızda var olan bir sertifika imzalama SQL Server'da bu sorunu çalışabilir. Bu kullanıcılar veritabanı erişimi veya izinleri vermeden yordamı tarafından kullanılan veritabanı kaynaklarına erişmenizi sağlar.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[EXECUTE AS kullanarak veritabanı kimliğe bürünme genişletme](https://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) ve [çapraz seçeneği zincirleme DB sahipliği](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option)SQL Server Kitapları Çevrimiçi.|Veritabanları arası sahiplik zinciri için bir SQL Server örneğini yapılandırma konuları açıklanmaktadır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [SQL Server’da Secure Dynamic SQL Yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [SQL Server'da Saklı Yordam İmzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
