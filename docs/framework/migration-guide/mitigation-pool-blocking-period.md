---
title: Mayı Havuz engelleme süresi
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71f1b06e53b3851ca3f65edc1755527779b42a67
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789964"
---
# <a name="mitigation-pool-blocking-period"></a>Mayı Havuz engelleme süresi
Bağlantı havuzu engelleme süresi Azure SQL veritabanlarına bağlantılar için kaldırılmıştır.  
  
## <a name="additional-description"></a>Ek açıklama  
 .NET Framework 4.6.1 ve önceki sürümlerde, bir uygulama bir veritabanına bağlanırken geçici bir bağlantı hatasıyla karşılaştığında bağlantı girişimi hızlı bir şekilde yeniden denenemez, çünkü bağlantı havuzu hatayı önbelleğe alır ve 5 saniye ile 1 ' e yeniden atar Min. Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../data/adonet/sql-server-connection-pooling.md). Bu davranış, genellikle birkaç saniye içinde kurtarılan geçici hatalarla başarısız olan Azure SQL veritabanlarına bağlantı için sorunlu olur. Bağlantı havuzu engelleme özelliği, uygulamanın veritabanı kullanılabilir olsa bile kapsamlı bir süre için veritabanına bağlanamamasıdır. Bu davranış, Azure SQL veritabanlarına bağlanan ve birkaç saniye içinde işlenmesi gereken Web uygulamaları için özellikle sorunlu olur.  
  
 .NET Framework 4.6.2 ile başlayarak, bilinen Azure SQL veritabanlarına yönelik bağlantı açık istekleri (*. Database.Windows.net, \*. Database.chinacloudapi.cn, \*. Database.usgovcloudapi.net, \*. Database.cloudapi.de) ), bağlantı açma hataları önbelleğe alınmaz. Diğer tüm bağlantı girişimleri için, bağlantı havuzu engelleme süresi zorlanmaya devam eder.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, bağlantı açma denemesinin Azure SQL veritabanları için hemen yeniden denenmeye olanak tanır ve böylece bulut özellikli uygulamaların performansını geliştirir.  
  
## <a name="mitigation"></a>Azaltma  
 Bu değişiklikten olumsuz etkilenen uygulamalar için, bağlantı havuzu engelleme süresi yeni <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> özellik ayarlanarak yapılandırılabilir.  Özelliğinin değeri, üç değerden birini ele alan <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> numaralandırmanın bir üyesidir:  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 Önceki davranış <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliği olarak <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>ayarlanarak geri yüklenebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Değişiklikleri](runtime-changes-in-the-net-framework-4-6-2.md)
