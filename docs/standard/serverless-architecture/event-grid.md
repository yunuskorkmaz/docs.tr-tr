---
title: Azure Event Grid - sunucusuz uygulamalar
description: Azure Event Grid, güvenilir olay teslimi ve çok büyük ölçekte olay başına ödeme modeli yönlendirme için sunucusuz bir çözümdür.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 240542014a34235aea9fd0f8162748749f23eacf
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143668"
---
# <a name="event-grid"></a>Event Grid

[Azure Event Grid](/azure-event-grid/overview) olay tabanlı uygulamalar için sunucusuz bir altyapı sağlar. Event Grid için herhangi bir kaynaktan yayımlayabilir ve herhangi bir platform gelen iletileri kullanır. Event Grid, ayrıca uygulamalarınız ile tümleştirmeyi kolaylaştırmak için Azure kaynaklardan gelen olaylar için yerleşik destek sunmaktadır. Örneğin, bir dosya yüklendiğinde uygulamanızı bildirmek için blob depolama olaylarına abone olabilirsiniz. Uygulamanızı daha sonra diğer bulut tarafından tüketilen ya da şirket içi uygulamaların bir özel olay Kılavuzu ileti yayımlayabilirsiniz. Event Grid, çok büyük ölçekte güvenilir bir şekilde yönetmek amacıyla oluşturulmuştur. Yayımlama ve gerekli altyapı Kurulumu ek yükü olmadan iletilerine abone avantajları sahip olursunuz.

![Event Grid logosu](./media/event-grid-logo.png)

Event grid önemli özellikleri şunlardır:

* Tam olarak yönetilen olay yönlendirme.
* Uygun ölçekte gerçek zamanlı Olay teslimi.
* Geniş kapsamı hem Azure içindeki ve dışındaki.

## <a name="scenarios"></a>Senaryolar

Olay Kılavuzu birkaç farklı senaryolar ele alır. Bu bölüm, en yaygın olanlarından üçünün kapsar.

### <a name="ops-automation"></a>OPS Otomasyonu

![OPS Otomasyonu](./media/ops-automation.png)

Event Grid yardımcı hızı otomasyon ve bildirerek ilke uygulamayı basitleştirmenizi [Azure Otomasyonu](https://docs.microsoft.com/azure/automation) altyapı zaman hazırlanır.

### <a name="application-integration"></a>Uygulama tümleştirme

![Uygulama tümleştirme](./media/app-integration.png)

Event Grid, uygulamanızı diğer hizmetlere bağlamak için kullanabilirsiniz. Standart HTTP protokolü kullanarak, daha eski uygulamaları kolayca Event Grid iletileri yayımlamak için değiştirilebilir. Web kancaları, diğer hizmetler ve Event Grid iletileri tüketmeye platformlar için kullanılabilir.

### <a name="serverless-apps"></a>Sunucusuz uygulamalar

![Sunucusuz uygulamalar](./media/serverless-apps.png)

Event Grid, Azure işlevleri, Logic Apps veya kendi özel kodunuzu tetikleyebilirsiniz. Event Grid kullanarak, önemli bir avantajı da kullanmasıdır bir *anında iletme* olaylar meydana geldiğinde ileti göndermek için bir mekanizma. Anında iletme mimarisi daha az kaynak kullanır ve daha iyi ölçeklenir *yoklama* mekanizmaları. Yoklama, düzenli aralıklarla güncelleştirmeleri işaretlemeniz gerekir.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Event grid'i ve diğer Azure Mesajlaşma Hizmetleri karşılaştırması

Azure dahil olmak üzere birden çok Mesajlaşma hizmetleri sağlayan [Event Hubs](https://docs.microsoft.com/azure/event-hubs) ve [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging). Her kullanım örnekleri belirli bir dizi yönelik olarak tasarlanmıştır. Aşağıdaki diyagramda, Hizmetleri arasındaki farklar üst düzey bir genel bakış sağlar.

![Azure Mesajlaşma karşılaştırma](./media/azure-messaging-services.png)

Daha ayrıntılı bir karşılaştırması için bkz. [Mesajlaşma hizmetlerini karşılaştırma](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).

## <a name="performance-targets"></a>Performans hedefleri

Aşağıdaki performans yararlanabilir Event Grid kullanarak garanti eder:

* 99. yüzdebirlik dilimde uçtan uca gecikme subsecond.
* %99,99 kullanılabilirlik.
* Bölge başına saniyede 10 milyon olay.
* 100 milyon bölge başına abonelik sayısı.
* Yayımcı gecikme 50 MS'den.
* 24 saatlik 1 gün penceresinde garantili teslim için üstel geri alma ile yeniden deneyin.
* Şeffaf bölgesel yük devretme.

## <a name="event-grid-schema"></a>Olay ızgarası şeması

Event Grid'e özel olaylar kaydırmak için standart bir şema kullanır. Şemadır Zarf gibi özel veri öğesini sarmalar. Bir örnek Event Grid iletisi aşağıda verilmiştir:

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

İleti hakkında her şeyi dışında standart `data` özelliği. İleti inceleyin ve kullanma `eventType` ve `dataVersion` seri durumdan çıkarılamıyor akıştaki özel bölümü için.

## <a name="azure-resources"></a>Azure kaynakları

Azure tarafından üretilen otomatik iletiler Event Grid kullanarak, önemli bir avantajdır. Azure'da kaynakları otomatik olarak yayımlamak bir *konu* çeşitli olaylar için abone izin verir. Aşağıdaki tabloda, kaynak türleri, ileti türleri ve otomatik olarak kullanılabilir olan olayları listeler.

| Azure kaynak | Olay türü | Açıklama |
| -------------- | ---------- | ----------- |
| Azure aboneliği | Microsoft.Resources.ResourceWriteSuccess | Oluşturulan, ne zaman bir kaynak oluşturma veya güncelleştirme işlemi başarılı olur. |
| | Microsoft.Resources.ResourceWriteFailure | Kaynak oluşturma veya güncelleştirme işlemi başarısız olduğunda oluşturulur. |
| | Microsoft.Resources.ResourceWriteCancel | Oluşturulan, ne zaman bir kaynak oluşturma veya güncelleştirme işlemi iptal edildi. |
|  | Microsoft.Resources.ResourceDeleteSuccess | Bir kaynak silme işlemi başarılı olduğunda oluşturulur. |
|  | Microsoft.Resources.ResourceDeleteFailure | Bir kaynak silme işlemi başarısız olduğunda oluşturulur. |
| | Microsoft.Resources.ResourceDeleteCancel | Bir kaynak silme işlemi iptal edildiğinde oluşturulur. Bu olay, bir şablon dağıtımı iptal edildiğinde gerçekleşir. |
| Blob depolama | Microsoft.Storage.BlobCreated | Bir blob oluşturulduğunda oluşturulur. |
| | Microsoft.Storage.BlobDeleted | Bir blob silindiğinde oluşturulur. |
| Event Hubs | Microsoft.EventHub.CaptureFileCreated | Yakalama dosyası oluşturulduğunda oluşturulur.
| IoT Hub | Microsoft.Devices.DeviceCreated | IOT hub'a bir cihaz kaydedildiğinde yayımladı. |
| | Microsoft.Devices.DeviceDeleted | Bir cihaz IOT hub'ından silindiğinde yayımladı. |
| Kaynak grupları | Microsoft.Resources.ResourceWriteSuccess | Oluşturulan, ne zaman bir kaynak oluşturma veya güncelleştirme işlemi başarılı olur. |
| | Microsoft.Resources.ResourceWriteFailure | Kaynak oluşturma veya güncelleştirme işlemi başarısız olduğunda oluşturulur. |
| | Microsoft.Resources.ResourceWriteCancel | Oluşturulan, ne zaman bir kaynak oluşturma veya güncelleştirme işlemi iptal edildi. |
| | Microsoft.Resources.ResourceDeleteSuccess | Bir kaynak silme işlemi başarılı olduğunda oluşturulur. |
| | Microsoft.Resources.ResourceDeleteFailure | Bir kaynak silme işlemi başarısız olduğunda oluşturulur. |
| | Microsoft.Resources.ResourceDeleteCancel | Bir kaynak silme işlemi iptal edildiğinde oluşturulur. Bu olay, bir şablon dağıtımı iptal edildiğinde gerçekleşir. |

Daha fazla bilgi için [Azure Event Grid olay şeması](https://docs.microsoft.com/azure/event-grid/event-schema).

Event Grid, her tür uygulama, şirket içinde çalışan bir bile erişebilirsiniz.

## <a name="conclusion"></a>Sonuç

Bu bölümde, Azure işlevleri, Logic Apps ve Event Grid oluşan Azure sunucusuz platform hakkında bilgi edindiniz. Tamamen sunucusuz uygulama mimarisi oluşturmak için bu kaynakları kullanın veya diğer bulut kaynaklarını ile etkileşime geçer ve şirket içi sunucuları karma çözümü oluşturun. Gibi bir sunucusuz bir veri platformu ile birlikte [Azure SQL](https://docs.microsoft.com/azure/sql-database) veya [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), tam olarak yönetilen bir bulutta yerel uygulamalar oluşturabilir.

## <a name="recommended-resources"></a>Önerilen kaynaklar

* [App service planları](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
* [Application Insights](https://docs.microsoft.com/azure/application-insights)
* [Application Insights Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
* [Azure: Uygulamanızı sunucusuz Azure işlevleri ile buluta taşıyın](https://channel9.msdn.com/events/Connect/2017/E102)
* [Azure Event Grid](https://docs.microsoft.com/azure/azure-event-grid/overview)
* [Azure Event Grid olay şeması](https://docs.microsoft.com/azure/event-grid/event-schema)
* [Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs)
* [Azure işlevleri belgeleri](https://docs.microsoft.com/azure/azure-functions)
* [Azure işlevleri Tetikleyicileri ve bağlamaları kavramları](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
* [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
* [Azure hizmet veri yolu](https://docs.microsoft.com/azure/service-bus-messaging)
* [Azure Tablo Depolama](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
* [1.x ve 2.x'i karşılaştırma işlevleri](https://docs.microsoft.com/azure/azure-functions/functions-versions)
* [Azure şirket içi veri ağ geçidi ile şirket içi veri kaynaklarına bağlanma](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
* [Azure portalında ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
* [Azure CLI kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
* [Visual Studio kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
* [İşlevleri desteklenen diller](https://docs.microsoft.com/azure/azure-functions/supported-languages)
* [Azure işlevlerini izleme](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
* [Azure işlev proxy'leri ile çalışma](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[Önceki](logic-apps.md)
>[İleri](durable-azure-functions.md)