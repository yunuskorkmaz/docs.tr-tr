---
title: 'Risk azaltma: havuz engelleme süresi'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 98396d4254975d1806a8477cbcd2380cb52ceaf3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457850"
---
# <a name="mitigation-pool-blocking-period"></a>Risk azaltma: havuz engelleme süresi
Bağlantı havuzu engelleme süresi Azure SQL veritabanlarına bağlantılar için kaldırılmıştır.  
  
## <a name="additional-description"></a>Ek açıklama  
 .NET Framework 4.6.1 ve önceki sürümlerde, bir uygulama bir veritabanına bağlanırken geçici bir bağlantı hatasıyla karşılaştığında bağlantı girişimi hızlı bir şekilde yeniden denenemez, çünkü bağlantı havuzu hatayı önbelleğe alır ve 5 saniye ile 1 ' e yeniden atar Min. Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../data/adonet/sql-server-connection-pooling.md). Bu davranış, genellikle birkaç saniye içinde kurtarılan geçici hatalarla başarısız olan Azure SQL veritabanlarına bağlantı için sorunlu olur. Bağlantı havuzu engelleme özelliği, uygulamanın veritabanı kullanılabilir olsa bile kapsamlı bir süre için veritabanına bağlanamamasıdır. Bu davranış, Azure SQL veritabanlarına bağlanan ve birkaç saniye içinde işlenmesi gereken Web uygulamaları için özellikle sorunlu olur.  
  
 .NET Framework 4.6.2 ile başlayarak, bilinen Azure SQL veritabanlarına yönelik bağlantı açık istekleri (*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), bağlantı Açık hatalar önbelleğe alınmaz. Diğer tüm bağlantı girişimleri için, bağlantı havuzu engelleme süresi zorlanmaya devam eder.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, bağlantı açma denemesinin Azure SQL veritabanları için hemen yeniden denenmeye olanak tanır ve böylece bulut özellikli uygulamaların performansını geliştirir.  
  
## <a name="mitigation"></a>Azaltma  
 Bu değişiklikten olumsuz etkilenen uygulamalar için, bağlantı havuzu engelleme süresi yeni <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> özelliği ayarlanarak yapılandırılabilir.  Özelliğinin değeri, üç değerden birini alan <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> numaralandırmanın bir üyesidir:  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 Önceki davranış <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliği <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>olarak ayarlanarak geri yüklenebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
