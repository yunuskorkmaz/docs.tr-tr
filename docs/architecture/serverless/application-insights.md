---
title: Uygulama Öngörüleri - Sunucusuz uygulamalar
description: Application Insights, geliştiricilerin web uygulamaları, mobil uygulamalar, masaüstü uygulamaları ve mikro hizmetlerdeki sorunları algılamasını, triyajlamasını ve tanılamasını sağlayan sunucusuz bir tanılama platformudur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522739"
---
# <a name="telemetry-with-application-insights"></a>Application Insights ile telemetri

[Application Insights,](https://docs.microsoft.com/azure/application-insights) geliştiricilerin web uygulamaları, mobil uygulamalar, masaüstü uygulamaları ve mikro hizmetlerdeki sorunları algılamasını, triyajetmesini ve tanılamasını sağlayan sunucusuz bir tanılama platformudur. İşlev uygulamaları için Uygulama Öngörüleri'ni portaldaki bir anahtarı çevirerek açabilirsiniz. Application Insights, bir sunucuyu yapılandırmanız veya kendi veritabanınızı kurmanız gerekmeden tüm bu özellikleri sağlar. Application Insights'ın tüm özellikleri, uygulamalarınız ile otomatik olarak entegre olan bir hizmet olarak sağlanır.

![Uygulama Öngörüleri logosu](./media/application-insights-logo.png)

Mevcut uygulamalara Uygulama Öngörüleri eklemek, uygulamanızın ayarlarına bir enstrümantasyon anahtarı eklemek kadar kolaydır. Uygulama Öngörüleri ile şunları yapabilirsiniz:

- İşlev çağırma sayısı, bir işlevi çalıştırmak için gereken süre ve özel durumlar gibi ölçümlere göre özel grafikler ve uyarılar oluşturun
- Hataları ve sunucu özel durumlarını çözümleme
- Operasyonla performansa sondaj yapmak ve üçüncü taraf bağımlılıklarını aramak için gereken süreyi ölçün
- İşlev uygulamalarınızı barındıran tüm sunucularda CPU kullanımını, belleği ve oranları izleyin
- İşlev uygulamalarınız için istek sayısı ve gecikme sayısı da dahil olmak üzere canlı bir ölçüm akışını görüntüleyin
- İşlev verileriniz üzerinde arama yapmak, sorgulamak ve özel grafikler oluşturmak için [Analytics'i](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) kullanın

![Ölçümler gezgini](./media/metrics-explorer.png)

Dahili telemetriye ek olarak, özel telemetri de oluşturmak mümkündür. Aşağıdaki kod snippet işlevi uygulaması için enstrümantasyon anahtarı kümesini kullanarak özel bir telemetri istemcisi oluşturur:

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

Aşağıdaki kod, bir [Azure Tablo Depolama](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) örneğine yeni bir satır eklemenin ne kadar süreceğini ölçer:

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

Elde edilen performans grafiği gösterilir:

![Özel telemetri](./media/custom-telemetry.png)

Özel telemetri, yeni bir satır eklemek için ortalama süre 32,6 milisaniye olduğunu ortaya koymaktadır.

Application Insights, sunucusuz uygulamalarınız hakkında ayrıntılı telemetri günlüğe kaydetmek için güçlü ve kullanışlı bir yol sağlar. Sağlanan izleme ve günlüğe kaydetme düzeyi üzerinde tam denetime sahipsiniz. Olaylar, bağımlılıklar ve sayfa görünümü gibi özel istatistikleri izleyebilirsiniz. Son olarak, güçlü analitik, önemli sorular soran ve grafikler ve gelişmiş öngörüler oluşturan sorgular yazmanızı sağlar.

Daha fazla bilgi için [bkz.](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)

>[!div class="step-by-step"]
>[Önceki](azure-functions.md)
>[Sonraki](logic-apps.md)
