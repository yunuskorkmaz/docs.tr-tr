---
title: Sunucusuz tasarım örnekleri - sunucusuz uygulamalar
description: Sunucusuz mimarileri, zamanlama ve olay-tabanlı işleme dosya Tetikleyicileri ve akış işlemi tarafından desteklenen senaryoları çeşitli anlayın.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: cf46c601ac6aa401c7c37bd64c1f8981589ebd2e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146718"
---
# <a name="serverless-design-examples"></a>Sunucusuz tasarım örnekleri

Mevcut birçok tasarım desenleri vardır sunucusuz. Bu bölümde, sunucusuz kullanın bazı yaygın senaryolar yakalar. Ne tüm örnekleri ortak olan bir olay tetikleyicisi ve iş mantığı temel birleşimi.

## <a name="scheduling"></a>Zamanlama

Görevleri zamanlama ortak bir işlevdir. Aşağıdaki diyagramda, uygun bütünlük denetimi sahip olmayan eski bir veritabanı gösterilmektedir. Veritabanını düzenli aralıklarla tersten gerekir. Sunucusuz bir işlev geçersiz verileri bulur ve temizler. Kod bir zamanlamaya göre çalışan bir zamanlayıcı tetikleyicisi var.

![Sunucusuz zamanlama](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Komut ve sorgu sorumluluğu ayrımı (CQRS)

Komut ve sorgu sorumluluğu ayrımı (CQRS), farklı arabirimler okuma (veya sorgulama) için veri ve veri değiştirme işlemleri sağlayan bir düzeni olduğunu. Bu, bazı yaygın sorunlar ele alınmaktadır. Geleneksel oluşturma okuma güncelleştirme Sil (temel CRUD) sistemleri, aynı veri deposuna hem okuma hem de yazma işlemleri yüksek birimden çakışmalar ortaya çıkabilir. Kilitleme sık oluşur ve okuma önemli ölçüde yavaşlatabilir. Genellikle, birden fazla etki alanı nesnelerini ve okuma işlemleri bileşimini farklı varlıklar verileri birleştirmeniz gerekir gibi veriler sunulur.

CQRS modelini, okuma tüketildiği şekilde veri modelleri özel bir "Düz" varlık gerektirebilir. Salt okunur farklı nasıl depolandığını ele alınır. Örneğin, veritabanı alt adresi kaydını bir üst bilgi kayıt bir kişi depolayabilir ancak salt okunur üstbilgi ve adres özelliklerini içeren bir varlık gerekebilir. Okuma modeli oluşturmak için çok yaklaşım vardır. Görünümleri gerçekleştirilmiş. Güncelleştirme işlemleri, ardından iki farklı modellere güncelleştirmeleri tetiklemeye yalıtılmış olaylar olarak kapsüllenmiş. Okuma ve yazma için ayrı bir model yok.

![CQRS örneği](./media/cqrs-example.png)

Sunucusuz CQRS modelinin oluşturmazsınız uç noktaları sağlayarak barındırabilir. Sunucusuz bir işlev sorguları veya okuma modeli sağlar ve farklı bir sunucusuz işlev veya işlevler kümesi güncelleştirme işlemleri gerçekleştirir. Sunucusuz bir işlev de okuma modeli güncel tutmak için sorumlu olabilir ve veritabanı tarafından tetiklenen [değişiklik akışını](https://docs.microsoft.com/azure/cosmos-db/change-feed). Ön uç geliştirme gerekli Uç noktalara bağlanmak için basitleştirilmiştir. Olay işleme, arka uçta ele alınır. Farklı ekipler farklı işlemlerin çalışabilir olduğundan bu modeli de büyük projeler için de ölçeklendirir.

## <a name="event-based-processing"></a>Olay tabanlı işleme

İleti tabanlı sistemlerde olayları, kuyruklar veya yayımcı/abone konuları üzerinde yapılmasının genellikle toplanır. Bu olaylar, iş mantığı bir parçasını yürütmek için sunucusuz işlevler tetikleyebilirsiniz. Olay tabanlı işleme olay kaynaklı sistemlerini örneğidir. "Olay", bir görevi tamamlandı olarak işaretlemek için tetiklenir. Olayı tarafından tetiklenen bir sunucusuz işlev uygun veritabanı belgeyi güncelleştirir. İkinci bir sunucusuz işlev olay sistemin okuma modeli güncelleştirmek için kullanabilirsiniz. [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) olayları aboneleri olarak işlevleri ile tümleştirmek için bir yol sağlar.

> Bilgi iletilerini olaylardır. Daha fazla bilgi için [olay kaynağını belirleme düzeni](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Dosya Tetikleyicileri ve dönüştürmeler

Ayıklama, dönüştürme ve yükleme (ETL) bir ortak iş işlevidir. Harika bir çözüm için ETL sunucusuz bir işlem hattı bir parçası olarak tetiklenmesi için kod izin verdiğinden. Tek bir kod bileşenleri farklı yönlerden ele alabilirsiniz. Sunucusuz bir işlev dosyayı yükleyebilirsiniz, başka bir dönüştürme uygulanır ve başka verileri yükler. Kod test ve bağımsız olarak, dağıtılan korumak ve gerektiğinde ölçeği kolaylaştırır.

![Sunucusuz dosya Tetikleyicileri ve dönüştürmeler](./media/serverless-file-triggers.png)

Diyagramda, "seyrek erişimli depolama" olarak ayrıştırılır veri sağlayan [Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics). Veri akışında karşılaşılan sorunlardan anomali adresi için bir Azure işlevi tetikleyin.

## <a name="asynchronous-background-processing-and-messaging"></a>Zaman uyumsuz bir arka plan işleme ve mesajlaşma

Zaman uyumsuz Mesajlaşma ve arka plan işleme uygulamaları beklemek zorunda kalmadan işlemleri devre dışı başlatmasını sağlar. Zaman uyumsuz işleme OCR uygulama örneğidir. Görüntü gönderildi ve işlenmek üzere kuyruğa alındı. Metin ayıklamak için görüntü tarama zaman alabilir ve bildirim tamamlandıktan sonra gönderilir. Sunucusuz çağırma hem sonucu bu senaryoda başa çıkabilir.

## <a name="web-apps-and-apis"></a>Web uygulamaları ve API'ler

Yaygın bir senaryo için sunucusuz N katmanlı uygulamalar, en yaygın olarak olanları UI katmanında bir web uygulaması olduğu. Tek sayfa uygulamaları (SPA) popülerliği son uyarımız. SPA uygulamaları tek bir sayfayı oluşturmak ve ardından API çağrılarının ve döndürülen verileri tam bir sayfayı yeniden yüklemeyi olmadan yeni kullanıcı arabirimini dinamik olarak işlenecek dayanır. İstemci tarafı işleme son kullanıcılara daha hızlı ve daha duyarlı bir uygulama sağlar.

Sunucusuz uç noktaları HTTP çağrıları tarafından tetiklenen API isteklerini işlemek için kullanılabilir. Örneğin, bir ad Hizmetleri şirket özel reklam istemek için kullanıcı profili bilgilerini içeren bir sunucusuz işlev çağırabilir. Özel ad sunucusuz bir işlev döndürür ve bu web sayfasını işler.

![Sunucusuz web API'si](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Veri işlem hattı

Sunucusuz İşlevler, veri işlem hattı kolaylaştırmak için kullanılabilir. Bu örnekte, bir dosya, bir tablodaki veri satırlarına bir CSV dosyasındaki verileri çevirmek için bir işlev tetikler. Düzenlenmiş tablonun son kullanıcıya analiz sunmak bir Power BI Pano sağlar.

![Sunucusuz bir veri işlem hattı](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Akış işleme

Genellikle cihazlardan ve sensörlerden işlenmesi gereken veri akışlarını gerçek zamanlı olarak oluşturur. Birçok iletileri ve akışlardan yakalayabilirsiniz teknolojilerinin [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) ve [IOT hub'ı](https://docs.microsoft.com/azure/iot-hub) için [Service Bus](/service-bus). Aktarım bağımsız olarak, gelen veri akışları ve iletileri işlemeyi bir ideal sunucusuz mekanizmadır. Sunucusuz, büyük hacimli verileri talebi karşılamak için hızla ölçeklendirebilirsiniz. Sunucusuz kod, eylem ve analiz için yapılandırılmış bir biçimde çıkış ve verileri ayrıştırmak için iş mantığını uygulayabilirsiniz.

![Sunucusuz bir akış işleme](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>API ağ geçidi

Bir API ağ geçidi, istemciler için tek bir giriş noktası sağlar ve istekleri arka uç Hizmetleri için akıllı bir şekilde yönlendirir. Hizmetlerin büyük kümelerini yönetmek kullanışlıdır. Ayrıca sürüm işlemek ve istemciler farklı ortamlar için kolayca bağlantı kurarak Geliştirme işlemini basitleştirin. Sunucusuz bir API ağ geçidi aracılığıyla tek bir ön uç sunarken her bir mikro hizmetin arka uç ölçeklendirme başa çıkabilir.

![Sunucusuz API ağ geçidi](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Önerilen kaynaklar

* [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
* [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub)
* [Dağıtılmış veri yönetimi için sorunlar ve çözümler](../microservices-architecture/architect-microservice-container-applications/distributed-data-management.md)
* [Mikro hizmetler tasarlama: mikro hizmet sınırlarını tanımlama](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
* [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
* [Olay kaynağını belirleme düzeni](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
* [Devre Kesici desenini uygulama](../microservices-architecture/implement-resilient-applications/implement-circuit-breaker-pattern.md)
* [IoT Hub’ı](https://docs.microsoft.com/azure/iot-hub)
* [Service Bus](https://docs.microsoft.com/azure/service-bus)
* [Azure Cosmos DB'de destek akış değişiklik ile çalışma](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Önceki](serverless-architecture-considerations.md)
>[İleri](azure-serverless-platform.md)