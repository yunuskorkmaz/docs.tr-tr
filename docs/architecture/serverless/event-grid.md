---
title: Azure Event Grid-sunucusuz uygulamalar
description: Azure Event Grid, güvenilir olay teslimi için sunucusuz bir çözümdür ve olay başına ödeme modelinde çok büyük ölçekli ölçekte yönlendirme yapın.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 30937bafd8069eb4508dce18351964103421373a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171890"
---
# <a name="event-grid"></a>Event Grid

[Azure Event Grid](/azure/event-grid/overview) , olay tabanlı uygulamalar için sunucusuz altyapı sağlar. Herhangi bir kaynaktaki Event Grid yayımlayabilir ve herhangi bir platformdan ileti kullanabilirsiniz. Event Grid Ayrıca, uygulamalarınızla tümleştirme sağlamak için Azure kaynaklarından gelen olaylar için yerleşik desteğe sahiptir. Örneğin, bir dosya karşıya yüklendiğinde uygulamanızı bilgilendirmek için BLOB depolama olaylarına abone olabilirsiniz. Uygulamanız daha sonra diğer bulut veya şirket içi uygulamalar tarafından tüketilen özel bir olay Kılavuzu iletisi yayımlayabilir. Event Grid, büyük ölçekli ölçeği güvenilir bir şekilde işlemek için oluşturulmuştur. Gerekli altyapıyı ayarlama ek yükü olmadan iletilere yayımlama ve abone olma avantajlarına sahip olursunuz.

![Event Grid logosu](./media/event-grid-logo.png)

Event Grid 'in başlıca özellikleri şunlardır:

- Tam olarak yönetilen olay yönlendirme.
- Ölçekteki neredeyse gerçek zamanlı olay teslimi.
- Azure 'un içinde ve dışında geniş kapsamlı kapsam.

## <a name="scenarios"></a>Senaryolar

Event Grid birkaç farklı senaryoya yöneliktir. Bu bölümde en yaygın olanlardan üçü ele alınmaktadır.

### <a name="ops-automation"></a>İşlem otomasyonu

![İşlem otomasyonu](./media/ops-automation.png)

Event Grid, altyapı sağlandığında [Azure Otomasyonu](/azure/automation) bilgilendirerek Otomasyon ve ilke zorlamayı basitleştirmeye yardımcı olabilir.

### <a name="application-integration"></a>Uygulama tümleştirme

![Uygulama tümleştirme](./media/app-integration.png)

Uygulamanızı diğer hizmetlere bağlamak için Event Grid kullanabilirsiniz. Standart HTTP protokollerini kullanarak, eski uygulamalar bile Event Grid iletileri yayımlamak üzere kolayca değiştirilebilir. Web kancaları, diğer hizmet ve platformların Event Grid iletileri kullanması için kullanılabilir.

### <a name="serverless-apps"></a>Sunucusuz uygulamalar

![Sunucusuz uygulamalar](./media/serverless-apps.png)

Event Grid, Azure Işlevlerini, Logic Apps veya kendi özel kodunuzu tetikleyebilirler. Event Grid kullanmanın önemli bir avantajı, olaylar gerçekleştiğinde ileti göndermek için bir *itme* mekanizması kullanmadır. Gönderim mimarisi daha az kaynak tüketir ve *yoklama* mekanizmalarından daha iyi ölçeklendirir. Yoklama, düzenli aralıklarla güncelleştirmeleri denetmelidir.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Event Grid ve diğer Azure mesajlaşma hizmetleri karşılaştırması

Azure, [Event Hubs](/azure/event-hubs) ve [Service Bus](/azure/service-bus-messaging)dahil olmak üzere birkaç mesajlaşma hizmeti sağlar. Her biri belirli bir kullanım durumları kümesini ele almak için tasarlanmıştır. Aşağıdaki diyagramda hizmetler arasındaki farklılıklara ilişkin üst düzey bir genel bakış sunulmaktadır.

![Azure mesajlaşma karşılaştırması](./media/azure-messaging-services.png)

Daha ayrıntılı bir karşılaştırma için bkz. [mesajlaşma hizmetlerini karşılaştırma](/azure/event-grid/compare-messaging-services).

## <a name="performance-targets"></a>Performans hedefleri

Event Grid kullanarak, aşağıdaki performans garantisi avantajlarından yararlanabilirsiniz:

- 99. yüzdebirlik 'teki ikinci saniyelik uçtan uca gecikme süresi.
- %99,99 kullanılabilirlik.
- Her bölge için saniyede 10.000.000 olay.
- Bölge başına 100.000.000 abonelikleri.
- 50-MS yayımcı gecikmesi.
- 1 günlük pencerede garantili teslim için üstel geri ile 24 saat yeniden deneyin.
- Saydam bölgesel yük devretme.

## <a name="event-grid-schema"></a>Olay Kılavuz şeması

Event Grid, özel olayları kaydırmak için standart bir şema kullanır. Şema, özel veri öğesini sarmalayan bir zarfa benzer. Aşağıda bir örnek Event Grid iletisi verilmiştir:

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

İletiyle ilgili her şey, özellik haricinde standarttır `data` . İletiyi inceleyebilir ve öğesini kullanarak `eventType` `dataVersion` yükün özel kısmını seri durumdan çıkarılamıyor.

## <a name="azure-resources"></a>Azure kaynakları

Event Grid kullanmanın önemli bir avantajı, Azure tarafından üretilen otomatik iletilerdir. Azure 'da kaynaklar, çeşitli olaylara abone olmanızı sağlayan bir *konuya* otomatik olarak yayımlar. Aşağıdaki tabloda, otomatik olarak kullanılabilen kaynak türleri, ileti türleri ve olaylar listelenmektedir.

| Azure kaynağı | Olay türü | Açıklama |
| -------------- | ---------- | ----------- |
| Azure aboneliği | Microsoft. resources. ResourceWriteSuccess | Kaynak oluşturma veya güncelleştirme işlemi başarılı olduğunda tetiklenir. |
| | Microsoft. resources. ResourceWriteFailure | Kaynak oluşturma veya güncelleştirme işlemi başarısız olduğunda tetiklenir. |
| | Microsoft. resources. ResourceWriteCancel | Kaynak oluşturma veya güncelleştirme işlemi iptal edildiğinde tetiklenir. |
|  | Microsoft. resources. ResourceDeleteSuccess | Kaynak silme işlemi başarılı olduğunda tetiklenir. |
|  | Microsoft. resources. ResourceDeleteFailure | Kaynak silme işlemi başarısız olduğunda tetiklenir. |
| | Microsoft. resources. ResourceDeleteCancel | Bir kaynak silme işlemi iptal edildiğinde tetiklenir. Bu olay, bir şablon dağıtımı iptal edildiğinde oluşur. |
| Blob depolama | Microsoft. Storage. Bloboluşturuldu | Bir blob oluşturulduğunda tetiklenir. |
| | Microsoft. Storage. BlobDeleted | Blob silindiğinde tetiklenir. |
| Event Hubs | Microsoft. EventHub. CaptureFileCreated | Bir yakalama dosyası oluşturulduğunda tetiklenir.
| IoT Hub | Microsoft.Devices.DeviceCreated | Bir cihaz IoT Hub 'ına kaydedildiğinde yayımlandı. |
| | Microsoft.Devices.DeviceDeleted | IoT Hub 'ından bir cihaz silindiğinde yayımlandı. |
| Kaynak grupları | Microsoft. resources. ResourceWriteSuccess | Kaynak oluşturma veya güncelleştirme işlemi başarılı olduğunda tetiklenir. |
| | Microsoft. resources. ResourceWriteFailure | Kaynak oluşturma veya güncelleştirme işlemi başarısız olduğunda tetiklenir. |
| | Microsoft. resources. ResourceWriteCancel | Kaynak oluşturma veya güncelleştirme işlemi iptal edildiğinde tetiklenir. |
| | Microsoft. resources. ResourceDeleteSuccess | Kaynak silme işlemi başarılı olduğunda tetiklenir. |
| | Microsoft. resources. ResourceDeleteFailure | Kaynak silme işlemi başarısız olduğunda tetiklenir. |
| | Microsoft. resources. ResourceDeleteCancel | Bir kaynak silme işlemi iptal edildiğinde tetiklenir. Bu olay, bir şablon dağıtımı iptal edildiğinde oluşur. |

Daha fazla bilgi için bkz. [Azure Event Grid olay şeması](/azure/event-grid/event-schema).

Şirket içinde çalışan bir tür uygulamadan Event Grid erişebilirsiniz.

## <a name="conclusion"></a>Sonuç

Bu bölümde, Azure Işlevleri, Logic Apps ve Event Grid oluşan Azure sunucusuz platformu hakkında bilgi edindiniz. Bu kaynakları tamamen sunucusuz bir uygulama mimarisi oluşturmak veya diğer bulut kaynaklarıyla ve şirket içi sunucularla etkileşim kuran bir karma çözüm oluşturmak için kullanabilirsiniz. [Azure SQL](/azure/sql-database) veya [cosmosdb](/azure/cosmos-db/introduction)gibi sunucusuz bir veri platformu ile birlikte kullanıldığında tamamen yönetilen bulut Yerel uygulamaları oluşturabilirsiniz.

## <a name="recommended-resources"></a>Önerilen Kaynaklar

- [App Service planları](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [Uygulama Bilgileri](/azure/application-insights)
- [Application Insights Analizi](/azure/application-insights/app-insights-analytics)
- [Azure: sunucusuz Azure Işlevleri ile Uygulamanızı buluta taşıyın](https://channel9.msdn.com/events/Connect/2017/E102)
- [Azure Event Grid](/azure/event-grid/overview)
- [Azure Event Grid olay şeması](/azure/event-grid/event-schema)
- [Azure Event Hubs](/azure/event-hubs)
- [Azure İşlevleri belgeleri](/azure/azure-functions)
- [Azure İşlevleri tetikleyicileri ve bağlama kavramları](/azure/azure-functions/functions-triggers-bindings)
- [Azure Logic Apps](/azure/logic-apps)
- [Azure Service Bus](/azure/service-bus-messaging)
- [Azure Table Storage](/azure/cosmos-db/table-storage-overview)
- [Azure Şirket İçi Veri Ağ Geçidi ile şirket içi veri kaynaklarına bağlanma](/azure/analysis-services/analysis-services-gateway)
- [Azure portalında ilk işlevinizi oluşturma](/azure/azure-functions/functions-create-first-azure-function)
- [Azure CLI kullanarak ilk işlevinizi oluşturma](/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [Visual Studio kullanarak ilk işlevinizi oluşturma](/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [İşlevlerin desteklediği diller](/azure/azure-functions/supported-languages)
- [Azure İşlevlerini İzleme](/azure/azure-functions/functions-monitoring)

>[!div class="step-by-step"]
>[Önceki](logic-apps.md) 
> [Sonraki](durable-azure-functions.md)
