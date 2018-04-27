---
title: SQL Server güvenlik
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: eb9eb073eb2227ce98d4adb93b8f4b60575cf1b7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="sql-server-security"></a>SQL Server güvenlik
SQL Server güvenli veritabanı uygulamaları oluşturmak destekleyen birçok özelliğe sahiptir.  
  
 Veri hırsızlığı veya vandalism, gibi genel güvenlik konuları, kullanmakta olduğunuz SQL Server sürümünden bağımsız olarak uygulanır. Veri bütünlüğü bir güvenlik sorunu da dikkate alınmalıdır. Veri korumalı değilse, geçici veri işleme izin verilir ve verileri yanlışlıkla ise worthless hale gelebilir veya kötü amaçlı olarak yanlış değerlerle değiştirilmiş veya tamamen silinmiş olduğunu mümkündür. Ayrıca, genellikle, için gizli bilgileri doğru depolama gibi bağlı yasal gereksinimi vardır. Bazı tür kişisel veri depolama tamamen içinde belirli bir dairesi uygulamak yasalarına bağlı olarak proscribed.  
  
 Windows her sürümü Öncekini Gelişmiş işlevlere sonraki sürümleri ile olduğu gibi farklı güvenlik özellikleri, SQL Server'ın her bir sürümü vardır. Güvenlik özellikleri tek başına güvenli veritabanı uygulaması garanti edemez anlamak önemlidir. Her veritabanı uygulaması, kendi gereksinimleri, yürütme ortamı, dağıtım modeli, fiziksel konumu ve kullanıcı nüfusu benzersizdir. Diğer yerel uygulamalar veya Internet üzerinden dağıtılan uygulamalar sıkı güvenlik önlemleri ve devam eden izleme ve değerlendirme gerektirebilir ancak yerel kapsamındaki bazı uygulamalar yalnızca en düşük güvenlik gerekebilir.  
  
 Tasarım zamanında bir sonradan akla olarak değil bir SQL Server veritabanı uygulamasının güvenlik gereksinimlerini dikkate alınmalıdır. Erken geliştirme döngüsü tehditleri değerlendirme bir güvenlik açığı algıladı her yerde potansiyel hasarı azaltmak olanağı sağlar.  
  
 Bir uygulamanın başlangıç tasarımı ses olsa bile, sistem geliştikçe yeni tehditleri ortaya. Veritabanınızı geçici savunma çok satırlı oluşturarak, bir güvenlik ihlali tarafından şiddet zarar en aza indirebilirsiniz. İlk savunma hattı saldırı yüzeyini alan tarafından hiçbir zaman kesinlikle gerekli olandan daha fazla izin vermeye azaltmaktır.  
  
 Bu bölümdeki konular, SQL Server Books Online ve daha ayrıntılı kapsamı sağlayan diğer kaynakları ilgili konulara bağlantılar ile geliştiriciler için uygun olan SQL Server güvenlik özellikleri kısaca açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 SQL Server'ın mimarisi ve güvenlik özellikleri açıklar.  
  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 ADO.NET ve SQL Server uygulamaları için çeşitli uygulama güvenlik senaryolarını ele konuları içerir.  
  
 [SQL Server Express Güvenliği](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 SQL Server Express için güvenlik konuları açıklanmaktadır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
[SQL Server veritabanı altyapısı ve Azure SQL veritabanı için Güvenlik Merkezi](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
SQL Server ve Azure SQL veritabanı için güvenlik konuları açıklanmaktadır.

[Bir SQL Server yüklemesi için güvenlik konuları](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
SQL Server yüklemeden önce dikkate alınması gereken güvenlik konuları açıklanmaktadır.

## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
