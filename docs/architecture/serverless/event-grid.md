---
title: Azure Olay Grid - Sunucusuz uygulamalar
description: Azure Olay İzlemi, etkinlik başına ödeme modelinde büyük ölçekte güvenilir olay teslimi ve yönlendirme için sunucusuz bir çözümdür.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3c577139c12567e762aabd58c9dc29457fa37aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522722"
---
# <a name="event-grid"></a>Event Grid

[Azure Olay Ağıt,](/azure/event-grid/overview) olay tabanlı uygulamalar için sunucusuz altyapı sağlar. Herhangi bir kaynaktan Olay Izgara'da yayımlayabilir ve herhangi bir platformdan iletiler tüketebilirsiniz. Olay Izgarası, uygulamalarınız ile tümleştirmeyi kolaylaştırmak için Azure kaynaklarından gelen etkinlikler için yerleşik desteğe de sahiptir. Örneğin, bir dosya yüklendiğinde uygulamanızı bilgilendirmek için blob depolama olaylarına abone olabilirsiniz. Uygulamanız daha sonra diğer bulut veya şirket içi uygulamalar tarafından tüketilen özel bir olay ızgara iletisi yayımlayabilirsiniz. Olay Izgara güvenilir büyük ölçekli işlemek için inşa edilmiştir. Gerekli altyapıyı kurmanın genel yükü olmadan iletileri yayımlamanın ve iletilere abone olma avantajlarından yararlanırsınız.

![Olay Izgara logosu](./media/event-grid-logo.png)

Olay ızgarasının başlıca özellikleri şunlardır:

- Tam olarak yönetilen olay yönlendirmesi.
- Ölçekte gerçek zamanlı etkinlik teslimatına yakın.
- Azure'un hem içinde hem de dışında geniş kapsama alanı.

## <a name="scenarios"></a>Senaryolar

Olay Izgara birkaç farklı senaryoları giderir. Bu bölüm en yaygın olanlardan üçünü kapsamaktadır.

### <a name="ops-automation"></a>İşlem otomasyonu

![İşlem otomasyonu](./media/ops-automation.png)

Olay Ağı, altyapı sağlandığında [Azure Otomasyonu'na](https://docs.microsoft.com/azure/automation) bildirimde bulunarak otomasyonu hızlandırmaya ve ilke zorlamayı basitleştirmeye yardımcı olabilir.

### <a name="application-integration"></a>Uygulama tümleştirme

![Uygulama tümleştirme](./media/app-integration.png)

Uygulamanızı diğer hizmetlere bağlamak için Olay Izgarasını kullanabilirsiniz. Standart HTTP protokolleri kullanılarak, eski uygulamalar bile Olay Izgara iletilerini yayımlayacak şekilde kolayca değiştirilebilir. Web kancaları, Olay Izgara iletilerini tüketen diğer hizmetler ve platformlar için kullanılabilir.

### <a name="serverless-apps"></a>Sunucusuz uygulamalar

![Sunucusuz uygulamalar](./media/serverless-apps.png)

Olay Izgarası Azure İşlerini, Mantık Uygulamalarını veya kendi özel kodunuzu tetikleyebilir. Olay Izgara'sını kullanmanın önemli bir yararı, olaylar oluştuğunda ileti göndermek için bir *itme* mekanizması kullanmasıdır. Push mimarisi daha az kaynak tüketir ve *yoklama* mekanizmalarından daha iyi ölçeklendirir. Yoklama, güncelleştirmeleri düzenli aralıklarla denetlemelidir.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Olay Grid ve diğer Azure mesajlaşma hizmetleri

Azure, [Etkinlik Hub'ları](https://docs.microsoft.com/azure/event-hubs) ve Servis [Veri Servisi](https://docs.microsoft.com/azure/service-bus-messaging)dahil olmak üzere çeşitli mesajlaşma hizmetleri sunar. Her biri belirli bir kullanım örnekleri kümesini ele almak üzere tasarlanmıştır. Aşağıdaki diyagram, hizmetler arasındaki farkların üst düzey bir genel görünümünü sağlar.

![Azure ileti karşılaştırması](./media/azure-messaging-services.png)

Daha ayrıntılı bir karşılaştırma [için, bkz.](https://docs.microsoft.com/azure/event-grid/compare-messaging-services)

## <a name="performance-targets"></a>Performans hedefleri

Olay Izgarasını kullanarak aşağıdaki performans garantilerinden yararlanabilirsiniz:

- 99. yüzdelik bölümde ikinci uç-uç gecikme.
- %99,99 kullanılabilirlik.
- Bölge başına saniyede 10 milyon olay.
- Bölge başına 100 milyon abonelik.
- 50 ms yayıncı gecikmesi.
- 1 günlük süre içinde garantili teslimat için üstel geri leme ile 24 saat yeniden deneme.
- Şeffaf bölgesel başarısızlık.

## <a name="event-grid-schema"></a>Olay Kılavuz şeması

Olay Grid özel olayları sarmak için standart bir şema kullanır. Şema, özel veri öğenizi saran bir zarf gibidir. Aşağıda örnek bir Olay Izgara iletisi verilmiştir:

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

İleti yle ilgili her `data` şey özellik dışında standarttır. İletiyi inceleyebilir ve `eventType` yükün özel kısmını seri den-serihale `dataVersion` getirmek için kullanabilirsiniz.

## <a name="azure-resources"></a>Azure kaynakları

Olay Izgara'sını kullanmanın en önemli avantajı Azure tarafından üretilen otomatik iletilerdir. Azure'da kaynaklar, çeşitli etkinlikler için abone olabileceğiniz bir *konuya* otomatik olarak yayımlanır. Aşağıdaki tabloda, otomatik olarak kullanılabilen kaynak türleri, ileti türleri ve olaylar listelenir.

| Azure kaynağı | Olay türü | Açıklama |
| -------------- | ---------- | ----------- |
| Azure aboneliği | Microsoft.Resources.ResourceWriteSuccess | Kaynak oluşturma veya güncelleştirme işlemi başarılı olduğunda yükseltilir. |
| | Microsoft.Resources.ResourceWriteFailure | Kaynak oluşturma veya güncelleştirme işlemi başarısız olduğunda yükseltildi. |
| | Microsoft.Resources.ResourceWriteCancel | Kaynak oluşturma veya güncelleştirme işlemi iptal edildiğinde yükseltilir. |
|  | Microsoft.Resources.ResourceDeleteSuccess | Kaynak silme işlemi başarılı olduğunda yükseltilir. |
|  | Microsoft.Resources.ResourceDeleteFailure | Kaynak silme işlemi başarısız olduğunda yükseltilir. |
| | Microsoft.Resources.ResourceDeleteCancel | Kaynak silme işlemi iptal edildiğinde yükseltilir. Bu olay, şablon dağıtımı iptal edildiğinde gerçekleşir. |
| Blob depolama | Microsoft.Storage.BlobCreated | Bir leke oluşturulduğunda yükseltilir. |
| | Microsoft.Storage.BlobDeleted | Bir leke silindiğinde yükseltilir. |
| Event Hubs | Microsoft.EventHub.CaptureFileCreated | Yakalama dosyası oluşturulduğunda yükseltilir.
| IoT Hub | Microsoft.Devices.DeviceCreated | Bir aygıt bir IoT hub'ına kaydedildiğinde yayımlanır. |
| | Microsoft.Devices.DeviceSilindi | Bir aygıt Bir IoT hub'ından silindiğinde yayımlanır. |
| Kaynak grupları | Microsoft.Resources.ResourceWriteSuccess | Kaynak oluşturma veya güncelleştirme işlemi başarılı olduğunda yükseltilir. |
| | Microsoft.Resources.ResourceWriteFailure | Kaynak oluşturma veya güncelleştirme işlemi başarısız olduğunda yükseltildi. |
| | Microsoft.Resources.ResourceWriteCancel | Kaynak oluşturma veya güncelleştirme işlemi iptal edildiğinde yükseltilir. |
| | Microsoft.Resources.ResourceDeleteSuccess | Kaynak silme işlemi başarılı olduğunda yükseltilir. |
| | Microsoft.Resources.ResourceDeleteFailure | Kaynak silme işlemi başarısız olduğunda yükseltilir. |
| | Microsoft.Resources.ResourceDeleteCancel | Kaynak silme işlemi iptal edildiğinde yükseltilir. Bu olay, şablon dağıtımı iptal edildiğinde gerçekleşir. |

Daha fazla bilgi için Azure [Olay Ağı etkinliği şemasına](https://docs.microsoft.com/azure/event-grid/event-schema)bakın.

Olay Izgara'ya şirket içinde çalışan her tür uygulamadan bile erişebilirsiniz.

## <a name="conclusion"></a>Sonuç

Bu bölümde, Azure İşlerinden, Mantık Uygulamaları'ndan ve Olay Izgaralarından oluşan Azure sunucusuz platformu hakkında bilgi edinebilirsiniz. Bu kaynakları tamamen sunucusuz bir uygulama mimarisi oluşturmak veya diğer bulut kaynakları ve şirket içi sunucularla etkileşimedebilen karma bir çözüm oluşturmak için kullanabilirsiniz. [Azure SQL](https://docs.microsoft.com/azure/sql-database) veya [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction)gibi sunucusuz bir veri platformuyla birlikte, tam olarak yönetilen bulut yerel uygulamaları oluşturabilirsiniz.

## <a name="recommended-resources"></a>Önerilen kaynaklar

- [Uygulama hizmeti planları](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [Uygulama Bilgileri](https://docs.microsoft.com/azure/application-insights)
- [Uygulama Öngörüleri Analizi](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
- [Azure: Sunucusuz Azure Fonksiyonları ile uygulamanızı buluta taşıyın](https://channel9.msdn.com/events/Connect/2017/E102)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure Olay Izgara olay şeması](https://docs.microsoft.com/azure/event-grid/event-schema)
- [Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs)
- [Azure Fonksiyonları belgeleri](https://docs.microsoft.com/azure/azure-functions)
- [Azure İşlevleri kavramları tetikler ve bağlar](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
- [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
- [Azure Servis Veri Servisi](https://docs.microsoft.com/azure/service-bus-messaging)
- [Azure Tablo Depolama](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
- [1.x ve 2.x fonksiyonlarını karşılaştırın](https://docs.microsoft.com/azure/azure-functions/functions-versions)
- [Azure Şirket İçi Veri Ağ Geçidi ile şirket içi veri kaynaklarına bağlanma](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
- [Azure portalında ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
- [Azure CLI kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [Visual Studio kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [Desteklenen işlevler](https://docs.microsoft.com/azure/azure-functions/supported-languages)
- [Azure İşlevlerini İzleme](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
- [Azure İşlevleri Proxies ile çalışma](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[Önceki](logic-apps.md)
>[Sonraki](durable-azure-functions.md)
