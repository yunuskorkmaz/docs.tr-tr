---
title: 'Azaltma: Havuzu engelleme süresi'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e402ba9cb5de8e85ce6912e2e5b760ef340c2cf4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389960"
---
# <a name="mitigation-pool-blocking-period"></a>Azaltma: Havuzu engelleme süresi
Dönem engelleme bağlantı havuzu bağlantılar Azure SQL veritabanları için kaldırılmıştır.  
  
## <a name="additional-description"></a>Ek açıklama  
 İçinde [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve önceki sürümlerinde, bir uygulama, bir veritabanına bağlanırken bir geçici bağlantı hatası karşılaştığında, çünkü bağlantı havuzu hata önbelleğe alır ve bunu 1 dak 5 saniye için yeniden oluşturur, hızlı bir şekilde, bağlantı girişimi denenemiyor. Daha fazla bilgi için bkz: [SQL Server bağlantı havuzu (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md). Bu bağlantılar genellikle genellikle gelen birkaç saniye içinde kurtarılan geçici hataları ile başarısız Azure SQL veritabanları için sorunlu davranıştır. Veritabanı kullanılabilir olsa bile bağlantı havuzu engelleme özelliği, uygulama kapsamlı bir dönem için veritabanına bağlanılamıyor anlamına gelir. Bu davranış, Azure SQL veritabanlarına bağlanmak ve, birkaç saniye içinde işlemek gereken web uygulamaları için özellikle sorunlu oluşturur.  
  
 İle başlayarak [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], bağlantıyı açmak için bilinen Azure SQL veritabanları için istekleri (*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), Bağlantı açık hatalarını önbelleğe alınmaz. Diğer tüm bağlantı girişimleri için bağlantı havuzunu engelleme süresi zorlanacak devam eder.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, böylece bulut özellikli uygulamalar performansını iyileştirme Azure SQL veritabanları için hemen denenmesi bağlantı açık denemesi sağlar.  
  
## <a name="mitigation"></a>Azaltma  
 Yeni ayarlayarak bağlantı havuzu engelleme süresi olumsuz bu değişiklikten etkilenen uygulamalar için yapılandırılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliği.  Özelliğinin değeri bir üyesidir <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> numaralandırması üç değerden birini alabilir:  
  
-   `PoolBlockingPeriod.AlwaysBlock` 
  
-   `PoolBlockingPeriod.Auto`  
  
-   `PoolBlockingPeriod.NeverBlock` 
  
 Önceki davranış ayarlayarak geri yüklenebilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliğine `PoolBlockingPeriod.AlwaysBlock`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
