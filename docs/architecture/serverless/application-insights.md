---
title: Application Insights-sunucusuz uygulamalar
description: Application Insights, geliştiricilerin Web Apps, mobil uygulamalar, masaüstü uygulamaları ve mikro hizmetlerde sorunları algılamasını, önceliklendirme ve tanılamalarını sağlayan sunucusuz bir tanılama platformudur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 42791b052ebb068c9b7109291e66b30b47e5821f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173327"
---
# <a name="telemetry-with-application-insights"></a>Application Insights ile telemetri

[Application Insights](/azure/application-insights) , geliştiricilerin Web Apps, mobil uygulamalar, masaüstü uygulamaları ve mikro hizmetlerde sorunları algılamasını, önceliklendirme ve tanılamalarını sağlayan sunucusuz bir tanılama platformudur. Yalnızca portalda bir anahtarı açarak işlev uygulamaları için Application Insights açabilirsiniz. Application Insights, bir sunucu yapılandırmanıza veya kendi veritabanınızı ayarlamanıza gerek kalmadan tüm bu özellikleri sağlar. Tüm Application Insights ' özellikleri, uygulamalarınızla otomatik olarak tümleştirilen bir hizmet olarak sağlanır.

![Application Insights logosu](./media/application-insights-logo.png)

Mevcut uygulamalara Application Insights eklemek, uygulamanızın ayarlarına bir izleme anahtarı eklemek kadar kolaydır. Application Insights ile şunları yapabilirsiniz:

- İşlev etkinleştirmeleri sayısı, bir işlev çalıştırmak için geçen süre ve özel durumlar gibi ölçümleri temel alarak özel grafikler ve uyarılar oluşturun
- Sorunları ve sunucu özel durumlarını çözümleme
- İşleme göre performans ile detaya gitme ve üçüncü taraf bağımlılıklarını çağırmak için geçen süreyi ölçme
- İşlev uygulamalarınızı barındıran tüm sunuculardaki CPU kullanımını, belleği ve fiyatları izleyin
- İşlev uygulamalarınız için istek sayısı ve gecikme süresi dahil olmak üzere ölçümlerin canlı bir akışını görüntüleyin
- İşlev verileriniz üzerinde özel grafikler aramak, sorgulamak ve oluşturmak için [Analizi](/azure/application-insights/app-insights-analytics) kullanın

![Ölçüm gezgini](./media/metrics-explorer.png)

Yerleşik telemetriye ek olarak, özel telemetri oluşturmak da mümkündür. Aşağıdaki kod parçacığı, işlev uygulaması için ayarlanan izleme anahtarını kullanarak özel bir telemetri istemcisi oluşturur:

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

Aşağıdaki kod, bir [Azure Tablo depolama](/azure/cosmos-db/table-storage-overview) örneğine yeni bir satır eklemek için geçen süreyi ölçer:

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

Elde edilen performans grafiği görüntülenir:

![Özel telemetri](./media/custom-telemetry.png)

Özel telemetri, yeni bir satır eklemek için geçen ortalama süreyi 32,6 milisaniyedir.

Application Insights, sunucusuz uygulamalarınız hakkında ayrıntılı telemetri günlüğe kaydetmek için güçlü ve uygun bir yol sağlar. Belirtilen izleme ve günlüğe kaydetme düzeyi üzerinde tam denetime sahip olursunuz. Olaylar, bağımlılıklar ve sayfa görünümü gibi özel istatistikleri izleyebilirsiniz. Son olarak, güçlü analizler önemli sorular sorduğu ve grafikler ve gelişmiş Öngörüler üreten sorgular yazmanızı sağlar.

Daha fazla bilgi için bkz. [Azure Işlevlerini izleme](/azure/azure-functions/functions-monitoring).

>[!div class="step-by-step"]
>[Önceki](azure-functions.md) 
> [Sonraki](logic-apps.md)
