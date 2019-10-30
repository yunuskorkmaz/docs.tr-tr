---
title: SQL Server'da Veritabanları Arası Erişimi Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: bf46d43f5ac9b0a385e9bc6da1546af1d67a282d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040239"
---
# <a name="enabling-cross-database-access-in-sql-server"></a>SQL Server'da Veritabanları Arası Erişimi Etkinleştirme
Veritabanları arası sahiplik zinciri, bir veritabanındaki bir yordam başka bir veritabanındaki nesnelere bağımlıysa oluşur. Veritabanları arası sahiplik zinciri, tek bir veritabanı içindeki sahiplik zinciriyle aynı şekilde çalışarak, bozuk bir sahiplik zinciri, tüm nesne sahiplerinin aynı oturum açma hesabıyla eşlenmesini gerektirmesidir. Kaynak veritabanındaki kaynak nesne ve hedef veritabanlarındaki hedef nesneler aynı oturum açma hesabına aitse, SQL Server hedef nesnelerdeki izinleri denetlemez.  
  
## <a name="off-by-default"></a>Varsayılan olarak kapalı  
 Veritabanları arasında sahiplik zinciri varsayılan olarak kapalıdır. Microsoft, aşağıdaki güvenlik risklerini size gösterdiğinden, veritabanları arası sahiplik zincirlemeyi devre dışı bırakmanızı önerir:  
  
- Veritabanı sahipleri ve `db_ddladmin` veya `db_owners` veritabanı rollerinin üyeleri, diğer kullanıcılara ait nesneleri oluşturabilir. Bu nesneler, diğer veritabanlarındaki nesneleri hedefleyebilir. Bu, veritabanları arası sahiplik zincirlemeyi etkinleştirirseniz bu kullanıcılara tüm veritabanlarındaki verilerle tam olarak güvenmeniz gerektiğini gösterir.  
  
- VERITABANı oluştur iznine sahip kullanıcılar yeni veritabanları oluşturabilir ve var olan veritabanlarını ekleyebilir. Veritabanları arası sahiplik zinciri etkinse, bu kullanıcılar, oluşturdukları yeni oluşturulan veya eklenen veritabanlarından ayrıcalıklarına sahip olmadıkları diğer veritabanlarındaki nesnelere erişebilir.  
  
## <a name="enabling-cross-database-ownership-chaining"></a>Veritabanları arası sahiplik zincirlemeyi etkinleştirme  
 Veritabanları arası sahiplik zinciri yalnızca yüksek ayrıcalıklı kullanıcılara tam güvenebileceğiniz ortamlarda etkinleştirilmelidir. Tüm veritabanları için kurulum sırasında ya da Transact-SQL komutları `sp_configure` ve `ALTER DATABASE`kullanılarak belirli veritabanlarına seçmeli olarak yapılandırılabilir.  
  
 Veritabanları arası sahiplik zincirlemeyi seçmeli olarak yapılandırmak için `sp_configure` kullanarak sunucu için devre dışı bırakın. Ardından, tek yapmanız gereken veritabanları için veritabanları arası sahiplik zincirlemesini yapılandırmak üzere SET DB_CHAINING ON ile ALTER DATABASE komutunu kullanın.  
  
 Aşağıdaki örnek, tüm veritabanları için çapraz veritabanı sahiplik zincirlemesini etkinleştirir:  
  
```sql
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 Aşağıdaki örnek, belirli veritabanları için veritabanları arası sahiplik zincirlemeyi etkinleştirir:  
  
```sql
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a>Dinamik SQL  
 Veritabanları arası sahiplik zinciri, aynı kullanıcı her iki veritabanında da mevcut olmadığı takdirde dinamik olarak oluşturulan SQL deyimlerinin yürütüldüğü durumlarda çalışmaz. Başka bir veritabanındaki verilere erişen ve yordamı her iki veritabanında bulunan bir sertifikayla imzalayan bir saklı yordam oluşturarak bu SQL Server geçici bir çözüm bulabilirsiniz. Bu, kullanıcılara veritabanı erişimi veya izinleri vermeden yordam tarafından kullanılan veritabanı kaynaklarına erişim sağlar.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|FARKLı ÇALıŞTıR ve [çapraz veritabanı sahiplik zinciri seçeneğini](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option) [kullanarak veritabanı kimliğe bürünme özelliğini genişletme](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) .|Makaleler, bir SQL Server örneği için veritabanları arası sahiplik zincirinin nasıl yapılandırılacağını açıklamaktadır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server Güvenliğine Genel Bakış](overview-of-sql-server-security.md)
- [SQL Server'da Saklı Yordam İzinlerini Yönetme](managing-permissions-with-stored-procedures-in-sql-server.md)
- [SQL Server’da Secure Dynamic SQL Yazma](writing-secure-dynamic-sql-in-sql-server.md)
- [SQL Server'da Saklı Yordam İmzalama](signing-stored-procedures-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
