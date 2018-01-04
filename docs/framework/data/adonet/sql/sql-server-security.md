---
title: "SQL Server güvenlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4b8eafeedd03097488b1493b5654db360eab94fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="sql-server-security"></a>SQL Server güvenlik
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]Güvenli veritabanı uygulamaları oluşturmak destekleyen birçok özelliğe sahiptir.  
  
 Veri hırsızlığı veya vandalism, gibi genel güvenlik konuları sürümü bağımsız olarak geçerli [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] kullanmakta olduğunuz. Veri bütünlüğü bir güvenlik sorunu da dikkate alınmalıdır. Veri korumalı değilse, geçici veri işleme izin verilir ve verileri yanlışlıkla ise worthless hale gelebilir veya kötü amaçlı olarak yanlış değerlerle değiştirilmiş veya tamamen silinmiş olduğunu mümkündür. Ayrıca, genellikle, için gizli bilgileri doğru depolama gibi bağlı yasal gereksinimi vardır. Bazı tür kişisel veri depolama tamamen içinde belirli bir dairesi uygulamak yasalarına bağlı olarak proscribed.  
  
 Her sürümü [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] her Windows sürümüyle, Öncekini Gelişmiş işlevlere sonraki sürümlerinde olduğu gibi farklı güvenlik özellikleri vardır. Güvenlik özellikleri tek başına güvenli veritabanı uygulaması garanti edemez anlamak önemlidir. Her veritabanı uygulaması, kendi gereksinimleri, yürütme ortamı, dağıtım modeli, fiziksel konumu ve kullanıcı nüfusu benzersizdir. Diğer yerel uygulamalar veya Internet üzerinden dağıtılan uygulamalar sıkı güvenlik önlemleri ve devam eden izleme ve değerlendirme gerektirebilir ancak yerel kapsamındaki bazı uygulamalar yalnızca en düşük güvenlik gerekebilir.  
  
 Güvenlik gereksinimlerine göre bir [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] veritabanı uygulaması olarak kabul edilmelidir tasarım zamanında bir sonradan akla olarak değil. Erken geliştirme döngüsü tehditleri değerlendirme bir güvenlik açığı algıladı her yerde potansiyel hasarı azaltmak olanağı sağlar.  
  
 Bir uygulamanın başlangıç tasarımı ses olsa bile, sistem geliştikçe yeni tehditleri ortaya. Veritabanınızı geçici savunma çok satırlı oluşturarak, bir güvenlik ihlali tarafından şiddet zarar en aza indirebilirsiniz. İlk savunma hattı saldırı yüzeyini alan tarafından hiçbir zaman kesinlikle gerekli olandan daha fazla izin vermeye azaltmaktır.  
  
 Bu bölümdeki konular, güvenlik özellikleri kısaca açıklayan [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] geliştiricilere ilgili konulara bağlantılar için ilgili olan [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online ve daha ayrıntılı kapsamı sağlayan diğer kaynakları.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 Mimari ve güvenlik özelliklerini açıklayan [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 ADO.NET için çeşitli güvenlik senaryolarını ele konuları içerir ve [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] uygulamalar.  
  
 [SQL Server Express Güvenliği](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 Güvenlik konuları açıklanmaktadır [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Güvenlik ve koruma (veritabanı altyapısı)](http://msdn2.microsoft.com/library/bb510589\(SQL.100\).aspx.)  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]Books Online güvenlik konuları.  
  
 [SQL Server için güvenlik konuları](http://go.microsoft.com/fwlink/?LinkId=98587)  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]Books Online güvenlik konuları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
