---
title: Sunucusuz tasarım örnekleri-sunucusuz uygulamalar
description: Zamanlama ve olay tabanlı işlemden dosya tetikleyicilerine ve akış işlemine kadar sunucusuz mimarilerin desteklediği çeşitli senaryoları anlayın.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 096dce6ef23bde5ef9c6ca65769f4dcc7e08a904
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676675"
---
# <a name="serverless-design-examples"></a>Sunucusuz tasarım örnekleri

Sunucusuz için mevcut birçok tasarım deseni vardır. Bu bölümde sunucusuz kullanan bazı yaygın senaryolar yakalar. Örneklerin hepsi ortak bir olay tetikleyicisi ve iş mantığının temel birleşimidir.

## <a name="scheduling"></a>Planlama

Zamanlama görevleri yaygın bir işlevdir. Aşağıdaki diyagramda, uygun bütünlük denetimlerine sahip olmayan eski bir veritabanı gösterilmektedir. Veritabanı düzenli aralıklarla yeniden oluşturulmalıdır. Sunucusuz işlevi geçersiz verileri bulur ve temizler. Tetikleyici, kodu bir zamanlamaya göre çalıştıran bir zamanlayıcıya sahiptir.

![Sunucusuz zamanlama](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Komut ve Sorgu Sorumluluklarının Ayrılığı (CQRS)

Komut ve Sorgu Sorumluluklarının Ayrılığı (CQRS), verileri değiştiren verileri ve işlemleri okumak (veya sorgulamak) için farklı arabirimler sağlayan bir modeldir. Yaygın olarak karşılaşılan birkaç sorunu ele alınmaktadır. Geleneksel olarak okuma güncelleştirme silme (CRUD) tabanlı sistemlerde, çakışmalar aynı veri deposuna hem okuma hem de yazma işlemlerinin yüksek haciminden kaynaklanabilir. Kilitleme sık sık meydana gelebilir ve çok önemli ölçüde yavaş okumalar. Veriler genellikle çeşitli etki alanı nesnelerinin bir bileşimi olarak sunulur ve okuma işlemleri farklı varlıklardaki verileri birleştirmelidir.

Bir okuma, CQRS kullanarak verileri tüketilen şekilde modelleyen özel bir "düzleştirilmiş" varlık içerebilir. Okuma, depolandıkları şekilde farklı şekilde işlenir. Örneğin, veritabanı bir kişiyi alt adres kaydıyla bir başlık kaydı olarak depolayabilse de, okuma hem üstbilgi hem de adres özelliklerine sahip bir varlık içerebilir. Okuma modelini oluşturmaya yönelik sayısız yaklaşımları vardır. Görünümlerden gerçekleştirilmiş olabilir. Güncelleştirme işlemleri, daha sonra güncelleştirmeleri iki farklı modele tetikleyen yalıtılmış olaylar olarak kapsüllenebilir. Okuma ve yazma için ayrı modeller var.

![CQRS örneği](./media/cqrs-example.png)

Sunucusuz, ayrılmış uç noktaları sağlayarak CQRS düzenine uyum sağlayabilir. Bir sunucusuz işlev sorguları veya okumaları, farklı bir sunucusuz işlevi veya işlev kümesini ise güncelleştirme işlemlerini işler. Sunucusuz bir işlev, okuma modelinin güncel tutulması için de sorumlu olabilir ve veritabanının [değişiklik akışı](https://docs.microsoft.com/azure/cosmos-db/change-feed)tarafından tetiklenebilir. Ön uç geliştirme, gerekli uç noktalara bağlanmak üzere basitleştirilmiştir. Olayların işlenmesi arka uçta işlenir. Farklı ekipler farklı işlemlerde çalışabileceğinden, bu model büyük projeler için de iyi ölçeklendiriyor.

## <a name="event-based-processing"></a>Olay tabanlı işleme

İleti tabanlı sistemlerde, olaylar genellikle daha sonra işlem yapmak için kuyruklarda veya yayımcı/abone konularında toplanır. Bu olaylar, bir iş mantığı parçasını yürütmek için sunucusuz işlevleri tetikleyebilir. Olay tabanlı işleme bir örnek olay kaynaklı sistemleridir. Bir görevi tamamlanmış olarak işaretlemek için bir "olay" tetiklenir. Olay tarafından tetiklenen sunucusuz bir işlev, uygun veritabanı belgesini günceller. İkinci sunucusuz bir işlev, sistem için okuma modelini güncelleştirmek üzere olayını kullanabilir. [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) , olaylarla olayları abone olarak tümleştirmenin bir yolunu sağlar.

> Olaylar bilgilendirme iletileridir. Daha fazla bilgi için bkz. olay kaynağını belirleme [stili](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Dosya Tetikleyicileri ve dönüştürmeleri

Ayıklama, dönüştürme ve yükleme (ETL) ortak bir iş işlevidir. Sunucusuz, kodun bir işlem hattının parçası olarak tetiklenmesini sağladığından ETL için harika bir çözümdür. Bağımsız kod bileşenleri çeşitli açılardan ele alabilir. Bir sunucusuz işlev dosyayı indirebilir, başka bir dönüşüm uygular ve başka bir veri yükler. Kod bağımsız olarak test edilebilir ve dağıtılabilir, böylece gerektiğinde daha kolay bir şekilde korunur ve ölçeklendirebilirsiniz.

![Sunucusuz dosya Tetikleyicileri ve dönüştürmeleri](./media/serverless-file-triggers.png)

Diyagramda, "seyrek erişimli depolama" [Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics)ayrıştırılabilen verileri sağlar. Veri akışında karşılaşılan sorunlar, anomali 'e yönelik bir Azure Işlevi tetikleyin.

## <a name="asynchronous-background-processing-and-messaging"></a>Zaman uyumsuz arka plan işleme ve mesajlaşma

Zaman uyumsuz mesajlaşma ve arka plan işleme, uygulamaların beklemeye girmeden işlemleri başlatma izni verir. Zaman uyumsuz işleme bir örnek OCR uygulamasıdır. Bir görüntü gönderilir ve işlenmek üzere sıraya alınır. Metnin ayıklanmasına ilişkin görüntünün taranması zaman alabilir ve bir bildirim gönderilir. Sunucusuz, Bu senaryodaki çağrıyı ve sonucu işleyebilir.

## <a name="web-apps-and-apis"></a>Web uygulamaları ve API 'Ler

Sunucusuz için popüler bir senaryo, çoğu genellikle UI katmanının bir Web uygulaması olduğu N katmanlı uygulamalardır. Tek sayfa uygulamalarının (SPA) popülerliği yakın zamanda ortaya çıktı. SPA uygulamaları tek bir sayfa oluşturup API çağrılarını ve döndürülen verileri, tam sayfayı yeniden yüklemeden Yeni Kullanıcı arabirimini dinamik olarak işlemek için kullanır. İstemci tarafı işleme, son kullanıcıya çok daha hızlı ve daha hızlı bir uygulama sağlar.

HTTP çağrıları tarafından tetiklenen sunucusuz uç noktalar, API isteklerini işlemek için kullanılabilir. Örneğin, bir ad hizmetleri şirketi özel tanıtım istemek için Kullanıcı profili bilgileriyle sunucusuz bir işlev çağırabilir. Sunucusuz işlevi özel ad döndürür ve Web sayfası onu işler.

![Sunucusuz Web API 'SI](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Veri işlem hattı

Sunucusuz işlevler, bir veri işlem hattını kolaylaştırmak için kullanılabilir. Bu örnekte, bir dosya bir CSV dosyasındaki verileri bir tablodaki veri satırlarına dönüştürmek için bir işlevi tetikler. Düzenlenmiş tablo, Power BI panosunun son kullanıcıya analiz sunmasını sağlar.

![Sunucusuz veri işlem hattı](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Akış işleme

Cihazlar ve algılayıcılar genellikle gerçek zamanlı olarak işlenmesi gereken verilerin akışlarını oluşturur. [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) ileti ve akışları yakalayabilir ve [Service Bus](https://docs.microsoft.com/azure/service-bus) [IoT Hub](https://docs.microsoft.com/azure/iot-hub) . Aktarımdan bağımsız olarak sunucusuz, içindeki iletileri ve veri akışlarını işlemek için ideal bir mekanizmadır. Sunucusuz, büyük hacime sahip verilerin taleplerini karşılamak için hızla ölçeklendirebilir. Sunucusuz kod, işlem ve analiz için yapılandırılmış bir biçimde verileri ve çıktıyı ayrıştırmaya yönelik iş mantığı uygulayabilir.

![Sunucusuz akış işleme](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>API ağ geçidi

Bir API ağ geçidi istemciler için tek bir giriş noktası sağlar ve istekleri arka uç hizmetlerine yönlendirir. Büyük hizmet kümelerini yönetmek faydalı olur. Ayrıca, istemcileri farklı ortamlara kolayca bağlayarak, sürüm oluşturma ve geliştirmeyi kolaylaştırma işlemlerini de işleyebilir. Sunucusuz, tek bir ön ucu bir API Gateway aracılığıyla sunarken tek bir mikro hizmetin arka uç ölçeklendirmesini işleyebilir.

![Sunucusuz API ağ geçidi](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Önerilen Kaynaklar

* [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
* [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub)
* [Dağıtılmış veri yönetimi için sorunlar ve çözümler](../microservices/architect-microservice-container-applications/distributed-data-management.md)
* [Mikro hizmetler tasarlama: mikro hizmet sınırlarını tanımlama](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
* [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
* [Olay kaynağını belirleme kalıbı](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
* [Devre Kesici desenini uygulama](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
* [IoT Hub’ı](https://docs.microsoft.com/azure/iot-hub)
* [Service Bus](https://docs.microsoft.com/azure/service-bus)
* [Azure Cosmos DB'de destek akış değişiklik ile çalışma](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Önceki](serverless-architecture-considerations.md)İleri
>[](azure-serverless-platform.md)
