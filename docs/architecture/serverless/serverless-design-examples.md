---
title: Sunucusuz tasarım örnekleri - Sunucusuz uygulamalar
description: Zamanlama ve olay tabanlı işlemeden dosya tetikleyicilerine ve akış işlemine kadar sunucusuz mimariler tarafından desteklenen senaryoların çeşitliliğini anlayın.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4e8fda0c1423c881c0807602e11f7c49ff7cfe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093551"
---
# <a name="serverless-design-examples"></a>Sunucusuz tasarım örnekleri

Sunucusuzlar için var olan birçok tasarım delemi vardır. Bu bölümde, sunucusuz kullanan bazı yaygın senaryolar yakalar. Tüm örneklerin ortak noktası, bir olay tetikleyicisi ve iş mantığının temel birleşimidir.

## <a name="scheduling"></a>Zamanlama

Görevleri zamanlama ortak bir işlevdir. Aşağıdaki diyagram, uygun bütünlük denetimleri olmayan eski bir veritabanını gösterir. Veritabanı periyodik olarak temizlenmelidir. Sunucusuz işlev geçersiz verileri bulur ve temizler. Tetikleyici, kodu zamanlamada çalıştıran bir zamanlayıcıdır.

![Sunucusuz zamanlama](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Komut ve Sorgu Sorumluluğu Ayrımı (CQRS)

Komut ve Sorgu Sorumluluğu Ayrımı (CQRS), verileri ve verileri değiştiren işlemleri okumak (veya sorgulamak) için farklı arabirimler sağlayan bir desendir. Birkaç yaygın sorunları giderir. Geleneksel Oku Oku Silme (CRUD) tabanlı sistemlerde, aynı veri deposuna hem okuma hem de yazma hacminin yüksek hacminden çakışmalar ortaya çıkabilir. Kilitleme sık sık oluşabilir ve okumaları önemli ölçüde yavaşlatabilir. Genellikle, veriler birkaç etki alanı nesnelerinin birleşimi olarak sunulur ve okuma işlemleri farklı varlıklardan gelen verileri birleştirmelidir.

CQRS kullanarak, bir okuma, verileri tüketilen şekilde modelleyen özel bir "düzleştirilmiş" varlık içerebilir. Okuma, depolanan dan farklı işlenir. Örneğin, veritabanı bir kişi bir üstbilgi kaydı olarak bir alt adres kaydı ile depolar, ancak okuma hem üstbilgi ve adres özellikleri olan bir varlık içerebilir. Okuma modelini oluşturmak için sayısız yaklaşım vardır. Bu görünümlerden somutlaşmış olabilir. Güncelleştirme işlemleri, daha sonra iki farklı modele güncelleştirmeleri tetikleyen yalıtılmış olaylar olarak özetlenebilir. Okuma ve yazma için ayrı modeller vardır.

![CQRS örneği](./media/cqrs-example.png)

Sunucusuz, ayrılmış uç noktaları sağlayarak CQRS deseni barındırabilir. Sunucusuz bir işlev sorguları veya okumaları barındırır ve farklı bir sunucusuz işlev veya işlev kümesi güncelleştirme işlemlerini işler. Sunucusuz bir işlev, okuma modelini güncel tutmaktan da sorumlu olabilir ve veritabanının [değişiklik akışı](https://docs.microsoft.com/azure/cosmos-db/change-feed)tarafından tetiklenebilir. Ön uç geliştirme, gerekli uç noktalara bağlanmak için basitleştirilir. Olayların işlenmesi arka uçta işlenir. Farklı ekipler farklı işlemler üzerinde çalışabilir, çünkü bu model de büyük projeler için iyi ölçekler.

## <a name="event-based-processing"></a>Olay tabanlı işleme

İleti tabanlı sistemlerde, olaylar genellikle sıraya veya yayımcı/abone konuları üzerinde hareket edilecek şekilde toplanır. Bu olaylar, iş mantığının bir parçasını yürütmek için sunucusuz işlevleri tetikleyebilir. Olay tabanlı işlemenin bir örneği olay kaynaklı sistemlerdir. Bir görevi tamamlanmış olarak işaretlemek için bir "olay" yükseltilir. Olay tarafından tetiklenen sunucusuz bir işlev, uygun veritabanı belgesini güncelleştirir. İkinci bir sunucusuz işlev, sistem için okuma modelini güncelleştirmek için olayı kullanabilir. [Azure Olay Idamı,](https://docs.microsoft.com/azure/event-grid/overview) olayları abonesi olarak işlevleri olan tümleştirmenin bir yolunu sağlar.

> Olaylar bilgilendirme iletileridir. Daha fazla bilgi için olay [kaynak deseni](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)bakın.

## <a name="file-triggers-and-transformations"></a>Dosya tetikleyicileri ve dönüşümleri

Ayıklama, Dönüştürme ve Yükleme (ETL) ortak bir iş fonksiyonudur. Sunucusuz, kodun bir boru hattının parçası olarak tetiklenmelerine izin verdiği için ETL için harika bir çözümdür. Tek tek kod bileşenleri çeşitli yönlerini ele alabilir. Sunucusuz bir işlev dosyayı karşıdan yükleyebilir, diğeri dönüştürmeyi uygular ve diğeri verileri yükler. Kod bağımsız olarak sınanabilir ve dağıtılabilir, bu da gerektiğinde bakımı ve ölçeklendirmesini kolaylaştırır.

![Sunucusuz dosya tetikleyicileri ve dönüşümleri](./media/serverless-file-triggers.png)

Diyagramda "cool depolama", [Azure Akış Analizi'nde](https://docs.microsoft.com/azure/stream-analytics)ayrıştırılan veriler sağlar. Veri akışında karşılaşılan tüm sorunlar, anormalliği gidermek için bir Azure İşi tetikler.

## <a name="asynchronous-background-processing-and-messaging"></a>Asynchronous arka plan işleme ve mesajlaşma

Eşkron mesajlaşma ve arka plan işleme, uygulamaların beklemeye gerek kalmadan işlemleri başlatmasına olanak sağlar. Eşzamanlı işlemenin bir örneği bir OCR uygulamasıdır. Görüntü gönderilir ve işlenmek üzere sıraya alınır. Metni ayıklamak için görüntüyü taramak zaman alabilir ve tamamlandıktan sonra bir bildirim gönderilir. Sunucusuz, bu senaryoda hem çağırmayı hem de sonucu işleyebilir.

## <a name="web-apps-and-apis"></a>Web uygulamaları ve API'leri

Sunucusuzlar için popüler bir senaryo, kullanıcı arabirimi katmanının bir web uygulaması olduğu en yaygın uygulamalar olan N katmanlı uygulamalardır. Tek Sayfa Uygulamaları (SPA) popülaritesi son zamanlarda artmıştır. SPA uygulamaları tek bir sayfa yı işler, ardından tam sayfayı yeniden yüklemeden yeni ui'yi dinamik olarak işlemek için API çağrılarına ve döndürülen verilere güvenir. İstemci tarafı oluşturma, son kullanıcıya çok daha hızlı ve duyarlı bir uygulama sağlar.

HTTP çağrıları tarafından tetiklenen sunucusuz uç noktaları API isteklerini işlemek için kullanılabilir. Örneğin, bir reklam hizmetleri şirketi, özel reklam istemek için kullanıcı profili bilgilerini içeren sunucusuz bir işlev arayabilir. Sunucusuz işlev özel reklamı döndürür ve web sayfası onu işler.

![Sunucusuz web API](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Veri işlem hattı

Sunucusuz işlevler bir veri ardışık kolaylaştırmak için kullanılabilir. Bu örnekte, bir dosya, CSV dosyasındaki verileri tablodaki veri satırlarına çevirmek için bir işlev tetikler. Düzenlenen tablo, Power BI panosunun son kullanıcıya analiz sunmasını sağlar.

![Sunucusuz veri aktaremi](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Akış işleme

Aygıtlar ve sensörler genellikle gerçek zamanlı olarak işlenmesi gereken veri akışları oluşturur. [Olay Hub'larından](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) ve [IoT Hub'ından](https://docs.microsoft.com/azure/iot-hub) Servis Veri [Servisi'ne](https://docs.microsoft.com/azure/service-bus)ileti leri ve akışları yakalayabilen bir dizi teknoloji vardır. Aktarım dan bağımsız olarak, sunucusuz, iletileri ve veri akışlarını geldikleri gibi işlemek için ideal bir mekanizmadır. Sunucusuz, büyük hacimli verilerin talebini karşılamak için hızlı bir şekilde ölçeklenebilir. Sunucusuz kod, verileri ve çıktıları eylem ve analitik için yapılandırılmış bir biçimde ayrıştırmak için iş mantığı uygulayabilir.

![Sunucusuz akış işleme](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>API ağ geçidi

API ağ geçidi, istemciler için tek bir giriş noktası sağlar ve ardından istekleri arka uç hizmetlerine akıllıca yönlendirir. Büyük hizmet kümelerini yönetmek yararlıdır. Ayrıca, istemcileri birbirinden farklı ortamlara kolayca bağlayarak sürüm işlemlerini işleyebilir ve geliştirmeyi basitleştirebilir. Sunucusuz, api ağ geçidi üzerinden tek bir ön uç sunarken tek tek mikro hizmetlerin arka uç ölçekleme işleyebilir.

![Sunucusuz API ağ geçidi](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Önerilen kaynaklar

- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub)
- [Dağıtılmış veri yönetimi için sorunlar ve çözümler](../microservices/architect-microservice-container-applications/distributed-data-management.md)
- [Mikro hizmetlerin tasarlanması: mikrohizmet sınırlarının belirlenmesi](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
- [Etkinlik Hub'ları](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
- [Olay Kaynak deseni](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
- [Devre Kesici desenini uygulama](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
- [IoT Hub](https://docs.microsoft.com/azure/iot-hub)
- [Service Bus](https://docs.microsoft.com/azure/service-bus)
- [Azure Cosmos DB'de değişiklik akışı desteğiyle çalışma](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Önceki](serverless-architecture-considerations.md)
>[Sonraki](azure-serverless-platform.md)
