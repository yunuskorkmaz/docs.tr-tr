---
title: "Zaman uyumsuz ileti tabanlı iletişim"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Zaman uyumsuz ileti tabanlı iletişim"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ed0f12c5eca1ed45dabe94661f84216e07476ebd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="asynchronous-message-based-communication"></a>Zaman uyumsuz ileti tabanlı iletişim

Zaman uyumsuz ileti gönderme ve olay denetimli iletişimi değişiklikleri birden çok mikro ve bunların ilişkili etki alanı modelleri arasında yayılıyor olduğunda önemlidir. Daha önce tartışma mikro ve ilişkisindeki bağlamları (BCs) belirtildiği gibi modelleri (kullanıcı, müşteri, ürün, hesap, vb.) farklı mikro veya BCs farklı işlemler anlamına gelebilir. Bu değişiklikler olduğunda, değişiklikleri farklı modeli üzerinden mutabık kılmak için bazı yol gerektiği anlamına gelir. Bir, nihai tutarlılık ve olay denetimli iletişimi zaman uyumsuz ileti tabanlı çözümdür.

İleti kullanırken, işlemler iletileri zaman uyumsuz olarak değiştirerek iletişim kurar. Bir istemci bir komutu veya bir istek için bir hizmet bir ileti göndererek yapar. Hizmet yanıt vermesi, istemciye farklı bir ileti gönderir. İleti tabanlı iletişim olduğundan, istemci yanıt hemen alınmaz olduğunu ve olabileceğini yanıt hiç varsayar.

Bir ileti başlığı (meta verileri tanımlama veya güvenlik bilgileri gibi) ve gövde tarafından oluşur. İletiler genellikle AMQP gibi zaman uyumsuz protokolleri üzerinden gönderilir.

Tercih edilen mikro topluluk iletişiminde bu tür için büyük aracıların ve SOA içinde kullanılan orchestrators farklı bir basit ileti Aracısı altyapısıdır. Bir basit ileti Aracısı "yalnızca RabbitMQ veya Azure Service Bus gibi bulutta ölçeklenebilir service bus gibi basit uygulamalarıyla birlikte bir ileti Aracısı işlevi gören genellikle dumb," altyapısıdır. Bu senaryoda, "Akıllı" düşünmeye çoğunu hala oluşturan ve iletileri tüketen uç noktalardan yaşadığı — diğer bir deyişle, mikro içinde.

İzleyin, mümkün olduğunca denemelisiniz başka bir dahili hizmetleri arasında yalnızca zaman uyumsuz Mesajlaşma kullanın ve zaman uyumlu iletişimi (HTTP gibi) yalnızca istemci uygulamalardan (API ağ geçitleri ve ilk düzeyi ön uç hizmetleri kullanan kuralıdır mikro).

Zaman uyumsuz Mesajlaşma iletişim iki tür vardır: tek alıcı ileti tabanlı iletişim ve birden çok alıcıya ileti tabanlı iletişim. Aşağıdaki bölümlerde bunlarla ilgili ayrıntıları sağlayın.

## <a name="single-receiver-message-based-communication"></a>Tek alıcı ileti tabanlı iletişim 

Tek bir alıcı ile zaman uyumsuz iletişim ileti tabanlı bir iletiyi kanaldan okuma ve ileti yalnızca bir kez işlenir tüketicilere tam olarak birine teslim noktadan noktaya iletişim anlamına gelir. Ancak, özel durumlar vardır. Örneğin, hatadan otomatik olarak kurtarma denediğinde bir bulut sistemde, aynı iletiyi birden çok kez gönderilebilir. Ağ veya diğer hatalar nedeniyle istemci iletileri gönderme yeniden denemek, ve sunucunun belirli bir ileti yalnızca bir kez işlemek için ıdempotent olması için bir işlemi uygulamak sahiptir.

Tek alıcı ileti tabanlı iletişim, özellikle de başka bir Şekil 4-Bu yaklaşım gösteren 18'de gösterildiği gibi zaman uyumsuz komutları bir mikro göndermek için uygundur.

İleti tabanlı iletişim (ya da komutları veya olay ile) gönderme başladığınızda, zaman uyumlu HTTP iletişimi ile ileti tabanlı iletişim karıştırma kaçınmalısınız.

![](./media/image18.PNG)

**Şekil 4-18**. Zaman uyumsuz ileti alma tek bir mikro hizmet

Komutları istemci uygulamalarından geldiğinizde, bunlar HTTP zaman uyumlu komutlar olarak uygulanabilir olduğunu unutmayın. Daha yüksek ölçeklenebilirlik gerektiğinde veya bir ileti tabanlı iş işlemde zaten olduğunda ileti tabanlı komutları kullanmanız gerekir.

## <a name="multiple-receivers-message-based-communication"></a>Birden çok alıcıya ileti tabanlı iletişim 

Daha esnek bir yaklaşım gönderenden iletişimi ek abone mikro veya dış uygulamalar için kullanılabilir olacak bir yayımlama/abonelik mekanizması kullanılacak isteyebilirsiniz. Bu nedenle, izlemek için yardımcı [açık/kapalı İlkesi](https://en.wikipedia.org/wiki/Open/closed_principle) gönderen hizmet. Böylece, ek aboneleri gönderen hizmet değiştirmek zorunda kalmadan gelecekte eklenebilir.

Yayımla ve abone iletişimi kullandığınızda, tüm abone Yayımla olayları olay bus arabirim kullanıyor olabilir.

## <a name="asynchronous-event-driven-communication"></a>Olay tabanlı zaman uyumsuz iletişim

Olay tabanlı zaman uyumsuz iletişim kullanırken, bir mikro hizmet kendi etki alanı içinde bir şey ve başka bir mikro hizmet bunun farkında ürün kataloğu mikro fiyat değişikliği gibi olması gerektiğinde bir tümleştirme olay yayımlar. Bunlar zaman uyumsuz olarak alabilir şekilde ek mikro olaylara abone olma. Bu durum oluştuğunda alıcılar yayımlanmasını daha fazla tümleştirme olaylarını neden olabilir, kendi etki alanı varlıkları güncelleştirebilir. Bu yayımlama/abonelik sistem genellikle bir olay veri yolu uygulaması kullanılarak gerçekleştirilir. Olay veri yolu bir soyutlama ya da arabirimle abone veya olayları aboneliği ve olayları yayımlamak için gereken API olarak tasarlanmış olabilir. Olay bus de sahip olabilir veya daha fazla uygulamaları bir ileti sırası veya zaman uyumsuz iletişim ve publish/subscribe modelini destekleyen hizmet veri yolu gibi tüm işlemler arası ve mesajlaşma Aracısı göre.

Bir sistem tümleştirme olaylar tarafından yönlendirilen nihai tutarlılık kullanıyorsa, bu yaklaşım son kullanıcıya tamamen temizleyin yapılması önerilir. Sistem SignalR veya istemci yoklama sistemlerden gibi tümleştirme olaylarını taklit eden bir yaklaşım kullanmamanız gerekir. Son kullanıcı ve işletme sahibi açıkça nihai tutarlılık sistemde çekirdeğin ve çoğu durumda bu yaklaşım herhangi bir sorun iş yok açık olduğu sürece farkına sahiptir.

Daha önce belirtildiği gibi [sorunları ve çözümleri için Dağıtılmış veri yönetimi](#challenges-and-solutions-for-distributed-data-management) bölümünde, birden çok mikro span iş görevlerini uygulamak için tümleştirme olaylarını kullanabilirsiniz. Bu nedenle bu hizmetleri arasında nihai tutarlılık sahip olur. Sonuçta tutarlı bir işlem dağıtılmış işlemlerin koleksiyonu yapılır. Her bir eylemde ilgili mikro hizmet bir etki alanı varlığı güncelleştirir ve aynı uçtan uca iş görevi içinde bir sonraki eylem başlatır başka bir tümleştirme olay yayımlar.

Önemli bir aynı olaya abone olduğunuz birden çok mikro iletişim isteyebilirsiniz noktadır. Yayımla/abone ol kullanabilirsiniz, bunun için ileti üzerinde olay denetimli iletişimi, Şekil 4-19'gösterildiği gibi temel. Bu yayımlama/abonelik mekanizması mikro hizmet mimarisi için özel değildir. Benzer şekilde [ilişkisindeki bağlamları](http://martinfowler.com/bliki/BoundedContext.html) içinde DDD iletişim veya şekilde okunur bir veritabanına yazma veritabanından güncelleştirmeleri yayılması [komut ve sorgu sorumluluk ayrımı (CQRS)](http://martinfowler.com/bliki/CQRS.html)mimarisi düzeni. Dağıtılmış sisteminizi arasında birden çok veri kaynaklarına arasında nihai tutarlılık sağlamak için belirtilir.

![](./media/image19.png)

**Şekil 4-19**. Olay tabanlı zaman uyumsuz ileti iletişimi

Uygulamanızın hangi olay denetimli, ileti tabanlı iletişim için kullanılacak protokolü belirler. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) güvenilir kuyruğa alınan iletişim elde etmeye yardımcı olabilir.

Bir olay veri yoluna kullandığınızda, sınıflardaki ilgili bir uygulama gibi bir ileti aracısından API'sini kullanarak kod ile temel bir özet düzeyi (örneğin, bir olay veri yolu arabirimi) kullanmak isteyebilirsiniz [RabbitMQ](https://www.rabbitmq.com/) ya da hizmet veri yolu gibi[Azure Service Bus konuları ile](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Alternatif olarak, olay veri yolu iyileştirir ve yayımlama/abonelik sistem NServiceBus, MassTransit veya Brighter gibi daha üst düzey bir hizmet veri yolu kullanmak isteyebilirsiniz.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Üretim sistemleri için teknolojileri Mesajlaşma hakkında bir Not

İleti, soyut olay bus uygulamak için kullanılabilir farklı düzeylerde teknolojilerdir. Örneğin, diğer ürünler gibi NServiceBus, MassTransit veya RabbitMQ ve Azure Service Bus üzerinde çalışabilirsiniz Brighter'den daha düşük düzeydeki RabbitMQ (Mesajlaşma Aracısı aktarım) ve Azure Service Bus gibi ürün sit. Tercih ettiğiniz kaç Zengin özellikleri uygulama düzeyinde ve uygulamanız için gereksinim duyduğunuz Giden kutusu ölçeklenebilirlik bağlıdır. Biz eShopOnContainers örnek yaptığınız gibi yeni bir kavram kanıtı olay veri yolu için geliştirme ortamınızı uygulamak için basit bir uygulama Docker kapsayıcısı üzerinde çalışan RabbitMQ üstünde yeterli olabilir.

Ancak, kritik ve hiper ölçeklenebilirlik gereken üretim sistemlerine Azure Service Bus değerlendirmek isteyebilirsiniz. Üst düzey soyutlamalar ve dağıtılmış uygulamaların geliştirilmesini kolaylaştırır özellikler için NServiceBus, MassTransit ve Brighter gibi diğer ticari ve açık kaynak hizmeti yollarına değerlendirmek öneririz. Elbette, kendi hizmet veri yolu özellikleri üzerinde alt düzey teknolojileri RabbitMQ ve Docker gibi oluşturabilirsiniz. Ancak bu tesisat iş özel Kurumsal uygulama için çok fazla maliyeti.

## <a name="resiliently-publishing-to-the-event-bus"></a>Olay yoluna resiliently yayımlama

Resiliently kendi ilgili tümleştirme olay şekilde göre olay veri yolu içine yayımlanırken özgün mikro hizmet durumunda otomatik olarak güncelleştirmek nasıl bir olay denetimli mimari arasında birden çok mikro uygularken zor olduğu işlemler. Ek yaklaşımlar de olabilir ancak bunu yapmanın birkaç yolu verilmiştir.

-   İşlem (DTC tabanlı) sırası MSMQ gibi kullanma. (Ancak, eski bir yaklaşım budur.)

-   Kullanarak [işlem oturum araştırma](http://www.scoop.it/t/sql-server-transaction-log-mining).

-   Tam kullanarak [olay kaynak Hizmeti'nden](https://msdn.microsoft.com/en-us/library/dn589792.aspx) düzeni.

-   Kullanarak [Giden kutusu düzeni](http://gistlabs.com/2014/05/the-outbox/): bir işlemsel veritabanı tablosu olay oluşturun ve yayımlamadan bir olayı oluşturan bileşen temeli olacak bir ileti sırası olarak.

Zaman uyumsuz iletişim kullanırken dikkate alınması gereken ek ileti idempotence ve ileti yinelenenleri kaldırma konulardır. Bu konular bölümünde ele alınmıştır [mikro (tümleştirme olayları) arasındaki iletişimi olay tabanlı uygulama](#implementing_event_based_comms_microserv) bu kılavuzda daha sonra.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Olay tabanlı Mesajlaşma**
    [*http://soapatterns.org/design\_desen/olay\_güdümlü\_Mesajlaşma*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Kanal yayımlama/abonelik**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **UDI Dahan. Açıklığa kavuşturuldu CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **Komut ve sorgu sorumluluk ayrımı (CQRS)**
    [*https://docs.microsoft.com/azure/architecture/patterns/cqrs*](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

-   **Sınırlanmış bağlamları arasında iletişim**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **Nihai tutarlılık**
    [*https://en.wikipedia.org/wiki/Eventual\_tutarlılık*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Jimmy Bogard. Esnekliği doğru yeniden düzenleme: Bağlantı değerlendirme**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)


>[!div class="step-by-step"]
[Önceki] (iletişimi-içinde-mikro hizmet-architecture.md) [sonraki] (korumak-mikro hizmet-apis.md)
