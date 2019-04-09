---
title: SQL Server Güvenliği
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: 4aa4feadb6305f8a0ea6f99c2add780d6fca95cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080780"
---
# <a name="sql-server-security"></a>SQL Server Güvenliği
SQL Server güvenli veritabanı uygulamaları oluşturma desteği çok sayıda özelliğe sahiptir.  
  
 Veri hırsızlığına veya vandalism, gibi genel güvenlik değerlendirmeleri, kullanmakta olduğunuz SQL Server sürümünden bağımsız olarak geçerlidir. Veri bütünlüğü da bir güvenlik sorunu kabul edilmelidir. Veri korumalı değilse, geçici veri işleme izin verilir ve verilerin yanlışlıkla işe yaramaz hale gelebilir veya kötü amaçlı olarak hatalı değerler ile değiştirilmiş veya tamamen silinmiş olduğunu mümkündür. Ayrıca, genellikle, için gizli bilgilerin doğru depolama gibi bağlı yasal gereksinimi vardır. Bazı tür kişisel veri depolama tamamen, belirli bir yargılama alanında yasalara bağlı olarak proscribed.  
  
 Windows, her sürümü ile öncekileri Gelişmiş işlevlere sonraki sürümlerinde olduğu gibi SQL Server'ın her sürümünü farklı güvenlik özellikleri vardır. Güvenlik özellikleri tek başına güvenli bir veritabanında uygulama garanti edemez anlamak önemlidir. Her bir veritabanı uygulama, gereksinimleri, yürütme ortamı, dağıtım modeli, fiziksel konuma ve kullanıcı kitlesiyle benzersizdir. Diğer yerel uygulamaları veya Internet üzerinden dağıtılan uygulamaları katı güvenlik önlemleri ve devam eden izleme ve değerlendirme gerektirebilir ise yerel kapsamda olan bazı uygulamalar yalnızca en düşük güvenlik gerekebilir.  
  
 Bir SQL Server veritabanı uygulaması, güvenlik gereksinimlerini akla olarak değil, tasarım zamanında kabul edilmelidir. Geliştirme döngüsünün başlarında tehditleri değerlendirme bir güvenlik açığı algılanan her yerde durumdaki potansiyel hasarı azaltmak olanağı sağlar.  
  
 İlk tasarımın bir uygulamanın ses olsa bile sistem geliştikçe yeni tehditleri ortaya çıkan. Birden çok savunma veritabanınızı geçici satırlarını oluşturarak, bir güvenlik ihlali tarafından şiddet hasarı en aza indirebilirsiniz. İlk savunma hattınızdır saldırı yüzeyi alan tarafından hiçbir zaman gerekli olan daha fazla izin vermeye azaltmaktır.  
  
 Bu bölümdeki konular, SQL Server Books Online'ı ve daha ayrıntılı kapsamı sağlayan diğer kaynakların ilgili konulara bağlantılar sahip olan geliştiriciler için uygun olan SQL Server güvenlik özellikleri kısaca açıklayın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 SQL Server'ın mimarisi ve güvenlik özelliklerini açıklar.  
  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 ADO.NET ve SQL Server uygulamaları için çeşitli uygulama güvenliği senaryoları açıklayan konulara içerir.  
  
 [SQL Server Express Güvenliği](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 SQL Server Express için güvenlik konuları açıklanmaktadır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
[SQL Server veritabanı altyapısı ve Azure SQL veritabanı için Güvenlik Merkezi](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
SQL Server ve Azure SQL veritabanı için güvenlik konuları açıklanmaktadır.

[Bir SQL Server yüklemesi için güvenlik konuları](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
SQL Server'ı yüklemeden önce dikkate alınması gereken güvenlik konuları açıklanmaktadır.

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
