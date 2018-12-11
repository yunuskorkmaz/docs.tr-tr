---
title: Application Insights - sunucusuz uygulamalar
description: Application Insights, geliştiricilerin belirleme, Önceliklendirme ve web uygulamaları, mobil uygulamaları, Masaüstü uygulamaları ve mikro hizmetler sorunları tanılamanıza olanak sağlayan bir sunucusuz tanılama platformudur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4884d483de07c1c2077f7280b6b77c6059572c0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154269"
---
# <a name="telemetry-with-application-insights"></a>Application Insights ile telemetri

[Application Insights](https://docs.microsoft.com/azure/application-insights) algılamak, önceliklendirmek ve web uygulamaları, mobil uygulamaları, Masaüstü uygulamaları ve mikro hizmetler sorunları tanılamak geliştiricilerin sağlayan bir sunucusuz tanılama platformudur. Portalda yalnızca bir anahtar döndürerek işlev uygulamaları için Application Insights kapatabilirsiniz. Application Insights sunar bu özelliklerin tümünü gerek kalmadan bir sunucuyu yapılandırmak veya kendi veritabanınızı ayarlayın. Application Insights özelliklerin tümünü ile uygulamalarınızı otomatik olarak hizmeti olarak sağlanır.

![Application Insights logosu](./media/application-insights-logo.png)

Mevcut uygulamaları için Application Insights ekleme, bir izleme anahtarı, uygulamanızın ayarlar eklemek kadar kolaydır. Application Insights ile şunları yapabilirsiniz:

* Özel grafikler ve işlev çağrılarını sayısı gibi ölçümlere göre uyarılar oluşturun, bir işlev ve özel durumlar çalıştırmak için geçen süre
* Hataları ve sunucu özel durumları analiz edin
* Bir performans sağladığını işlemiyle ayrıntıya ve üçüncü taraf bağımlılıklarının çağırmak için gereken süreyi ölçün
* CPU kullanımı, bellek ve oranları işlev uygulamalarınızı barındıran tüm sunucular arasında izleyin
* İstek sayısı ve gecikme süresi, işlev uygulamalarınızı da dahil seçilen ölçümlerin Canlı akışı görüntüleyin
* Kullanım [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) aramak için sorgu ve işlev verileriniz üzerinde özel grafikler oluşturma

![Ölçüm Gezgini](./media/metrics-explorer.png)

Yerleşik telemetri yanı sıra, ayrıca özel telemetri oluşturmak mümkündür. Aşağıdaki kod parçacığı, işlev uygulaması için izleme anahtarını kullanarak özel telemetri istemcisi oluşturur:

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

Yeni bir satır eklemek için ne kadar sürer, aşağıdaki kodu ölçer bir [Azure tablo depolama](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) örneği:

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

Ortaya çıkan performans grafiği gösterilmektedir:

![Özel telemetri](./media/custom-telemetry.png)

Özel telemetri için yeni bir satır eklemek için geçen ortalama süre 32.6 milisaniyedir gösterir.

Application Insights, sunucusuz uygulamalarınız hakkında daha ayrıntılı telemetri oturum güçlü, kullanışlı bir yol sağlar. İzleme düzeyi üzerinde tam denetime sahiptir ve günlük sağlanır. Olaylar, bağımlılıklar ve sayfa görüntüleme gibi özel istatistikleri takip edebilirsiniz. Son olarak, güçlü analiz, önemli soru sorun ve grafikler ve Gelişmiş Öngörüler oluşturmak sorgular yazmaya olanak tanır.

Daha fazla bilgi için [İzleyici Azure işlevleri](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).

>[!div class="step-by-step"]
>[Önceki](azure-functions.md)
>[İleri](logic-apps.md)