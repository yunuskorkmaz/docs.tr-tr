---
title: 'Azaltma: Havuz engelleme süresi'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1021cf66c7091e699efac72fc9e614f30910398b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645112"
---
# <a name="mitigation-pool-blocking-period"></a>Azaltma: Havuz engelleme süresi
Azure SQL veritabanlarına bağlantı için süre engelleme bağlantı havuzu kaldırıldı.  
  
## <a name="additional-description"></a>Ek açıklama  
 İçinde [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve önceki sürümlerinde, bir uygulama, bir veritabanına bağlanırken geçici bağlantı hatası karşılaşırsa, çünkü bağlantı havuzu hata önbelleğe alır ve 1 dakika için 5 saniye boyunca yeniden harekete bağlantı denemesi hızlı bir şekilde yeniden denenemez. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md). Bu sorunlu bağlantılar için genellikle gelen birkaç saniye içinde kurtarıldığı geçici hatalar çoğunlukla başarısız Azure SQL veritabanları, davranıştır. Bağlantı havuzu engelleme özelliği veritabanı kullanılabilir olsa bile, uygulama kapsamlı bir dönem için veritabanına bağlanamıyor anlamına gelir. Bu, Azure SQL veritabanlarına bağlanmak ve birkaç saniye içinde işlemek gereken web apps için özellikle sorunlu, davranıştır.  
  
 İle başlayarak [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]bağlantıyı açmak için bilinen bir Azure SQL veritabanlarına istekleri (*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), Bağlantı açık hataları önbelleğe alınmaz. Diğer tüm bağlantı girişimleri için bağlantı havuzu engelleme süresi zorlanmaya devam eder.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, böylece bulut özellikli uygulamalar performansını iyileştirme, Azure SQL veritabanları için hemen yeniden denenmesi bağlantı açık denemesi sağlar.  
  
## <a name="mitigation"></a>Azaltma  
 Yeni ayarlayarak, olumsuz bu değişiklikten etkilenen uygulamaları için bağlantı havuzu engelleme süresi yapılandırılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliği.  Özelliğinin değeri bir üyesidir <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> numaralandırmadan üç değerden birini alabilir:  
  
-   `PoolBlockingPeriod.AlwaysBlock` 
  
-   `PoolBlockingPeriod.Auto`  
  
-   `PoolBlockingPeriod.NeverBlock` 
  
 Ayarlayarak önceki davranış geri yüklenebilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliğini `PoolBlockingPeriod.AlwaysBlock`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
