---
title: Zaman uyumsuz ileti tabanlı iletişim
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Zaman uyumsuz ileti tabanlı iletişim
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 865966a70f18c9023e4c733d82ea90aba9478753
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50757445"
---
# <a name="asynchronous-message-based-communication"></a>Zaman uyumsuz ileti tabanlı iletişim

Zaman uyumsuz Mesajlaşma ve olay odaklı iletişimi değişiklikleri birden çok mikro hizmetler ve bunların ilgili etki alanı modelleri arasında yayma, kritik öneme sahiptir. Tartışma mikro hizmetler ve sınırlanmış Bağlamlar (İBH) daha önce belirtildiği gibi modelleri (kullanıcı, müşteri, ürün, hesap, vb.) farklı bir mikro hizmetler veya BCs farklı öğelere anlamına gelebilir. Bu, değişiklikler olduğunda, farklı modelleri arasında değişiklikleri mutabık kılınacak şekilde gerektiği anlamına gelir. Bir son tutarlılık ve zaman uyumsuz Mesajlaşma temel olay temelli iletişim çözümüdür.

Mesajlaşma kullanırken, işlemleri mesaj alışverişleri tarafından zaman uyumsuz olarak iletişim kurar. Bir istemci bir komutu veya bir istek için bir hizmet bir ileti göndererek yapar. Hizmet yanıt vermesi durumunda farklı bir ileti istemciye geri gönderir. Bir ileti tabanlı iletişim olduğundan, istemci yanıtı hemen alınmaz, ve olabileceğini yanıt hiç varsayar.

Bir ileti üst bilgisi (kimlik veya güvenlik bilgileri gibi meta veriler) ile bir gövde oluşur. İletileri, genellikle AMQP gibi zaman uyumsuz protokolleri üzerinden gönderilir.

Bu tür bir mikro hizmetler topluluğundaki iletişimi için tercih edilen altyapı büyük aracıları ve SOA içinde kullanılan düzenleyicileri farklı basit ileti aracısıdır. Bir basit ileti Aracısı "yalnızca RabbitMQ veya Azure Service Bus gibi bulut ortamındaki bir ölçeklenebilir service bus gibi basit uygulamaları ile bir ileti aracısı olarak işlev gören genellikle dumb," altyapısıdır. Bu senaryoda, çoğu "Akıllı" düşünce hala oluşturan ve iletileri kullanmaya uç noktaların yaşadığı — diğer bir deyişle, mikro hizmetler.

İç hizmetleri arasında yalnızca zaman uyumsuz mesajlaşmayı kullanın ve zaman uyumlu iletişimini (HTTP gibi) istemci uygulamalardan yalnızca ön uç hizmetlerine (API ağ geçitleri ayrıca ilk düzeyi kullanmak için başka bir kural uygulayın, mümkün olduğunca denemelisiniz sağlamaktır mikro).

Zaman uyumsuz Mesajlaşma iletişim iki tür vardır: tek bir alıcı ileti tabanlı iletişim ve birden çok alıcıya ileti tabanlı iletişim. Aşağıdaki bölümlerde bunlarla ilgili ayrıntıları sunuyoruz.

## <a name="single-receiver-message-based-communication"></a>Tek bir alıcı ileti tabanlı iletişim 

İleti tabanlı zaman uyumsuz iletişim ile tek bir alıcı, tam olarak bir kanaldan okuma ve ileti yalnızca bir kez işlenir tüketici için bir iletiyi teslim noktadan noktaya iletişim anlamına gelir. Ancak, özel durumlar vardır. Örneğin, otomatik olarak hatalardan kurtarmak için çalışan bir bulut sisteminde aynı iletiyi birden çok kez gönderilebilir. Ağ veya diğer hatalar nedeniyle istemci iletileri gönderme yeniden deneme yapabilmek varsa ve sunucunun belirli bir iletiyi yalnızca bir kez işlemek için bir kere etkili olacak şekilde bir işlemi uygulamak.

Tek bir alıcı ileti tabanlı iletişim, özellikle de Şekil 4-Bu yaklaşım gösteren 18'de gösterildiği gibi başka bir zaman uyumsuz komutları bir mikro hizmet göndermek için uygundur.

İleti tabanlı iletişim (ya da komutları veya olayları) gönderme başlattıktan sonra ileti tabanlı iletişim zaman uyumlu HTTP iletişimi ile karıştırma kaçınmanız gerekir.

![](./media/image18.PNG)

**Şekil 4-18**. Tek bir mikro hizmet zaman uyumsuz ileti alma

Komutlar istemci uygulamalarından geldiğinizde, bunlar HTTP zaman uyumlu komutları uygulanabilir olduğunu unutmayın. Daha yüksek ölçeklenebilirlik gerektiğinde veya zaten bir ileti tabanlı iş süreci içinde olduğunda ileti tabanlı komutları kullanmanız gerekir.

## <a name="multiple-receivers-message-based-communication"></a>Birden çok alıcıya ileti tabanlı iletişim 

Daha esnek bir yaklaşım da iletişiminizin gönderenden ek abone mikro hizmetler veya dış uygulamalar için kullanılabilir olması bir yayımlama/abonelik mekanizması kullanmak isteyebilirsiniz. Bu nedenle, izlemek için yardımcı [açık/kapalı ilkesine](https://en.wikipedia.org/wiki/Open/closed_principle) gönderen hizmetinde. Bu şekilde, gönderen hizmeti değiştirmek zorunda kalmadan gelecekte ek aboneleri eklenebilir.

Bir yayımlama/abone olma iletişimi kullandığınızda, yayımlama olaylarına hiçbir abone için bir olay veri yolu arabirimi kullanıyor olabilir.

## <a name="asynchronous-event-driven-communication"></a>Olay tabanlı zaman uyumsuz iletişim

Zaman uyumsuz olay temelli iletişim kullanırken, bir mikro hizmet kendi etki alanı içinde bir şey ve başka bir mikro hizmet ve ürün kataloğu olan bir mikro hizmet, fiyat değişikliği gibi unutmayın gerektiğinde bir tümleştirme olayı yayımlar. Bunları bir zaman uyumsuz olarak alabilmesi için ek bir mikro hizmetler olaylara abone olun. Alıcılar, bu durum oluştuğunda daha fazla tümleştirme olayları yayımlanacak neden olabilir, kendi etki alanı varlıklarının güncelleştirebilir. Bu yayımlama/abone olma sistem, genellikle bir olay veri yolu uygulaması kullanılarak gerçekleştirilir. Olay veri yolu, bir Özet ya da arabirimle abone olmak veya abonelikten olayları ve olayları yayımlamak için gereken API olarak tasarlanabilir. Daha fazla uygulamaları tüm işlemler arası ve mesajlaşma Aracısı, bir ileti kuyruğu veya zaman uyumsuz iletişim ve bir yayımlama/abone olma modelini destekleyen bir service bus gibi temel veya olay veri yolu biri de olabilir.

Bir sistem tümleştirme olayları tarafından yönetilen son tutarlılık kullanıyorsa, bu yaklaşım son kullanıcıya tamamen açık yapılması önerilir. Sistem SignalR veya istemci yoklama sistemlerden gibi tümleştirme olayları taklit eden bir yaklaşım kullanmanız gerekir. Son kullanıcı ve işletme sahibi açıkça sistemde nihai tutarlılık yaklaşımını benimseyin ve açık olduğu sürece, çoğu durumda bu yaklaşımla, herhangi bir sorun iş yok fark gerekir.

Daha önce belirtildiği gibi [Dağıtılmış veri yönetimi için sorunlar ve çözümler](#challenges-and-solutions-for-distributed-data-management) bölümünde birden çok mikro hizmetler span iş görevlerini uygulamak için tümleştirme olayları kullanabilirsiniz. Bu nedenle, bu hizmetler arasındaki son tutarlılık gerekir. Sonunda tutarlı bir işlem, dağıtılmış işlemlerin bir koleksiyonu yapılır. Her eylem ilgili mikro hizmet etki alanı varlığı güncelleştirir ve sonraki eylem içinde aynı uçtan uca iş görevi başlatan başka bir tümleştirme olay yayımlar.

Önemli bir aynı olaya abone birden fazla mikro hizmetin iletişim kurmak isteyebilirsiniz noktadır. Yayımlama/abone olma kullanabilirsiniz. Bunu yapmak için Mesajlaşma iletişimi olay odaklı, Şekil 4-19'gösterildiği gibi temel. Bu yayımlama/abonelik mekanizması mikro hizmet mimarisi için özel değildir. Benzer şekilde [sınırlanmış Bağlamlar](https://martinfowler.com/bliki/BoundedContext.html) içinde DDD iletişim veya şekilde veritabanına okuma yazma veritabanından güncelleştirmeleri yaymak [komut ve sorgu sorumluluğu ayrımı (CQRS)](https://martinfowler.com/bliki/CQRS.html)mimari deseni. Nihai tutarlılık, dağıtılmış sisteme birden çok veri kaynağında sanal makineye sahip olmaktır.

![](./media/image19.png)

**Şekil 4-19**. Zaman uyumsuz olay temelli ileti iletişimi

Uygulamanız hangi olay odaklı, ileti tabanlı iletişim için kullanılacak protokolü belirler. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) güvenilir kuyruğa alınan iletişim elde etmeye yardımcı olabilir.

Bir olay veri yolu kullandığınızda, sınıflarda ilgili bir uygulama gibi bir ileti Aracısı API'den kullanarak kod ile temel bir özet düzeyi (örneğin, bir olay veri yolu arabirimi) kullanmak isteyebilirsiniz [RabbitMQ](https://www.rabbitmq.com/) veya gibibirservicebus[Azure Service Bus konuları ile](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Alternatif olarak, olay veri yolu ortaya çıkaran ve yayımlama/abonelik sistem NServiceBus, MassTransit veya Brighter gibi daha üst düzey bir hizmet veri yolu kullanmak isteyebilirsiniz.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Üretim sistemlerine yönelik teknolojileri Mesajlaşma hakkında bir Not

Mesajlaşma, soyut olay veri yolu uygulamak için kullanılabilen farklı düzeylerde teknolojilerdir. Örneğin, diğer ürünler gibi NServiceBus, MassTransit ya da RabbitMQ ve Azure Service Bus üzerinde çalışabilirsiniz Brighter, daha düşük bir düzeyde RabbitMQ (bir Mesajlaşma Aracısı taşıma) ve Azure Service Bus gibi ürünleri durur. Seçtiğiniz uygulama düzeyinde ve kullanıma hazır ölçeklenebilirlik, uygulamanız için gereken kaç Zengin özellikleri bağlıdır. Hizmetine örnek uyguladığımız yalnızca bir kavram kanıtı olay veri yolu için geliştirme ortamınızı uygulamak için basit bir uygulama üzerinde bir Docker kapsayıcısı üzerinde çalışırken RabbitMQ yeterli olabilir.

Ancak, görev açısından kritik ve ölçeklenebilirlik hyper gereken üretim sistemlerine Azure Service Bus değerlendirmek isteyebilirsiniz. Yüksek düzeyde soyutlama ve dağıtılmış uygulamaların geliştirilmesini kolaylaştıran özellikler için NServiceBus MassTransit ve Brighter gibi diğer ticari ve açık kaynak hizmeti yollarına değerlendirmek öneririz. Elbette, kendi hizmet veri yolu özellikleri RabbitMQ ve Docker gibi alt düzey teknolojileri üzerine oluşturabilir. Ancak bu tesisat iş özel Kurumsal uygulama için çok fazla maliyeti.

## <a name="resiliently-publishing-to-the-event-bus"></a>Dayanıklı olay yoluna yayımlama

Atomik olarak özgün mikro hizmet durumunda dayanıklı kendi ilgili tümleştirme olay şekilde göre olay veri yolu içine yayımlanırken güncelleştirmek nasıl bir olay denetimli mimari birden fazla mikro hizmetler arasında uygularken zor olduğu işlem. Ek yaklaşımları de olabilir ancak bunu yapmanın birkaç yolu şunlardır:

-   MSMQ gibi bir işlem (DTC tabanlı) kuyruğu kullanarak. (Ancak, eski bir yaklaşım budur.)

-   Kullanarak [işlem oturum araştırma](https://www.scoop.it/t/sql-server-transaction-log-mining).

-   Tam kullanarak [olay kaynağını belirleme](https://msdn.microsoft.com/library/dn589792.aspx) deseni.

-   Kullanarak [giden deseni](http://gistlabs.com/2014/05/the-outbox/): işlemsel veritabanı tablo olarak olay oluşturmak ve yayımlamak bir olay oluşturan bileşen temeli olacak bir ileti sırası.

Zaman uyumsuz iletişim kullanırken dikkate alınması gereken ek konuları ileti Eşkuvvetlilik ve ileti yinelenen verileri kaldırma ' dir. Bu konulara bölümünde ele alınmıştır [(tümleştirme olayları) mikro hizmetler arasında olay tabanlı iletişim uygulama](#implementing_event_based_comms_microserv) bu kılavuzun sonraki.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Mesajlaşma typu EventDriven**
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Kanal yayımlama/abone olma**
    [*https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **UDI Dahan. Açıklanan CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **Komut ve sorgu sorumluluğu ayrımı (CQRS)**
    [*https://docs.microsoft.com/azure/architecture/patterns/cqrs*](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

-   **Sınırlanmış Bağlamlar arasında iletişim kurma**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **Son tutarlılık**
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Jimmy Bogard. Dayanıklılığı yeniden düzenleme: Bağlantı değerlendirme**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)


>[!div class="step-by-step"]
[Önceki](communication-in-microservice-architecture.md)
[İleri](maintain-microservice-apis.md)
