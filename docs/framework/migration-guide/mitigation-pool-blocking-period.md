---
title: 'Azaltma: Havuz Engelleme Dönemi'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 98396d4254975d1806a8477cbcd2380cb52ceaf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457850"
---
# <a name="mitigation-pool-blocking-period"></a>Azaltma: Havuz Engelleme Dönemi
Bağlantı havuzu engelleme süresi, Azure SQL veritabanlarına bağlantılar için kaldırıldı.  
  
## <a name="additional-description"></a>Ek açıklama  
 .NET Framework 4.6.1 ve önceki sürümlerinde, bir uygulama veritabanına bağlanırken geçici bir bağlantı hatasıyla karşılaştığında, bağlantı havuzu hatayı önbelleğe aldığından ve 5 saniye ile 1 dakika arasında yeniden attığından, bağlantı denemesi hızlı bir şekilde yeniden denenemez. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md)adresine bakın. Bu davranış, genellikle birkaç saniye içinde kurtarılan geçici hatalarla başarısız olan Azure SQL veritabanlarına bağlantılar için sorunludur. Bağlantı havuzu engelleme özelliği, veritabanı kullanılabilir olsa bile uygulamanın geniş bir süre veritabanına bağlanamayacağı anlamına gelir. Bu davranış, Azure SQL veritabanlarına bağlanan ve birkaç saniye içinde işlenmesi gereken web uygulamaları için özellikle sorunludur.  
  
 .NET Framework 4.6.2 ile başlayarak, bilinen Azure SQL veritabanlarına (*.database.windows.net, \*.database.chinacloudapi.cn, .database.usgovcloudapi.net, \* \*.database.cloudapi.de) bağlantı açık istekleri için bağlantı açık hataları önbelleğe alınmaz. Diğer tüm bağlantı denemeleri için bağlantı havuzu engelleme süresi zorlanmaya devam ediyor.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, bağlantı açık girişiminin Azure SQL veritabanları için hemen yeniden denenmesine ve böylece bulut özellikli uygulamaların performansını artırmasına olanak tanır.  
  
## <a name="mitigation"></a>Risk azaltma  
 Bu değişiklikten olumsuz etkilenen uygulamalar için bağlantı havuzu engelleme süresi yeni <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> özellik ayarlayarak yapılandırılabilir.  Özelliğin değeri, üç değerden <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> birini alabilecek numaralandırmanın bir üyesidir:  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 Önceki davranış <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliği ' ne <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>ayarlayarak geri yüklenebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
