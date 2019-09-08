---
title: SQL Server Güvenliği
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: c5fd9cc82a3b1e4ffa217d65c542376fe067db06
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791626"
---
# <a name="sql-server-security"></a>SQL Server Güvenliği
SQL Server, güvenli veritabanı uygulamaları oluşturmayı destekleyen birçok özelliğe sahiptir.  
  
 Veri hırsızlığı veya vandalroni gibi yaygın güvenlik konuları, kullandığınız SQL Server sürümünden bağımsız olarak uygulanır. Veri bütünlüğü Ayrıca bir güvenlik sorunu olarak ele alınmalıdır. Veriler korunmuşsa, geçici veri işlemeye izin verildiğinde ve veriler yanlışlıkla veya kötü amaçlı olarak yanlış değerlerle değiştirilmişse veya tamamen siliniyorsa, daha az olabilme olasılığı vardır. Bunlara ek olarak, gizli bilgilerin doğru depolanması gibi genellikle, ' ye uymak gereken yasal gereksinimler vardır. Belirli bir vergi dairesine uygulanan kanunlarına bağlı olarak, bazı kişisel veri türlerinin depolanması tamamen tamamen yapılır.  
  
 Her bir SQL Server sürümünde, Windows 'un her sürümü, daha sonraki sürümlerde daha önce gelişmiş işlevlere sahip olduğu gibi farklı güvenlik özellikleri vardır. Güvenlik özelliklerinin tek başına güvenli bir veritabanı uygulamasını garanti edemediği anlamak önemlidir. Her veritabanı uygulaması gereksinimler, yürütme ortamı, dağıtım modeli, fiziksel konum ve Kullanıcı popülasyonu içinde benzersizdir. Kapsamda yerel olan bazı uygulamalar yalnızca en az güvenlik gerektirebilir, ancak Internet üzerinden dağıtılan diğer yerel uygulamalar veya uygulamalar sıkı güvenlik ölçüleri ve sürekli izleme ve değerlendirme gerektirebilir.  
  
 Bir SQL Server veritabanı uygulamasının güvenlik gereksinimleri, daha sonra değil, tasarım zamanında göz önünde bulundurulmalıdır. Geliştirme döngüsünün başlarında tehditleri değerlendirmek, bir güvenlik açığının algılanmasından bağımsız olarak olası zararları azaltma fırsatı sağlar.  
  
 Uygulamanın ilk tasarımı ses olsa bile, sistem geliştikçe yeni tehditler ortaya çıkabilir. Veritabanınızda daha fazla savunma satırı oluşturarak, bir güvenlik ihlalinin verdiği hasar olasılığını en aza indirgeyin. İlk savunma hattınız, kesinlikle gerekli olandan daha fazla izin vermeden saldırı yüzeyi alanını azaltmaktır.  
  
 Bu bölümdeki konular, SQL Server Books Online 'daki ilgili konuların ve daha ayrıntılı tedarik sağlayan diğer kaynakların bağlantılarıyla ilgili SQL Server, geliştiriciler için uygun olan güvenlik özelliklerini kısaca anlatmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Güvenliğine Genel Bakış](overview-of-sql-server-security.md)  
 SQL Server mimarisini ve güvenlik özelliklerini açıklar.  
  
 [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)  
 ADO.NET ve SQL Server uygulamalarına yönelik çeşitli uygulama güvenliği senaryolarına yönelik konular içerir.  
  
 [SQL Server Express Güvenliği](sql-server-express-security.md)  
 SQL Server Express yönelik güvenlik konularını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
[SQL Server veritabanı altyapısı ve Azure SQL veritabanı için Güvenlik Merkezi](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
SQL Server ve Azure SQL veritabanı için güvenlik konularını açıklar.

[SQL Server yüklemesine yönelik güvenlik konuları](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
SQL Server yüklemeden önce dikkate alınması gereken güvenlik konularını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server ve ADO.NET](index.md)
