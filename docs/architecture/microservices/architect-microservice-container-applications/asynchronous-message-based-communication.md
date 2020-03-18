---
title: Zaman uyumsuz ileti tabanlı iletişim
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Asynchronous mesaj tabanlı iletişim mikrohizmetler mimarisinde önemli bir kavramdır, çünkü mikro hizmetleri birbirinden bağımsız tutmanın en iyi yoludur ve aynı zamanda sonunda senkronize edilir.
ms.date: 09/20/2018
ms.openlocfilehash: 84eaf70178cce91a86dae8a55badb0b4ddd6a7c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73454239"
---
# <a name="asynchronous-message-based-communication"></a>Zaman uyumsuz ileti tabanlı iletişim

Asynchronous mesajlaşma ve olay odaklı iletişim, değişiklikleri birden çok mikro hizmet ve ilgili etki alanı modellerinde yayırken çok önemlidir. Daha önce tartışma mikroservices ve Bounded Contexts (CS) belirtildiği gibi, modeller (Kullanıcı, Müşteri, Ürün, Hesap, vb) farklı mikrohizmetler veya DC'ler için farklı şeyler anlamına gelebilir. Bu, değişiklikler oluştuğunda, değişiklikleri farklı modeller arasında bağdaştırmak için bir yol gerektiğini anlamına gelir. Çözüm, eşzamanlı mesajlaşmaya dayalı nihai tutarlılık ve olay odaklı iletişimdir.

İleti kullanırken, işlemler iletileri eşit bir şekilde değiştirerek iletişim kurar. İstemci, bir ileti göndererek bir hizmete bir komut veya istekte bulunur. Hizmetin yanıtlaması gerekiyorsa, istemciye farklı bir ileti gönderir. İleti tabanlı bir iletişim olduğundan, istemci yanıtın hemen alınamayacağını ve hiçbir yanıt verilmeyeceğini varsayar.

İleti, üstbilgi (kimlik veya güvenlik bilgileri gibi meta veriler) ve bir gövde tarafından oluşturulur. İletiler genellikle AMQP gibi eşzamanlı protokoller aracılığıyla gönderilir.

Mikro hizmetler topluluğunda bu tür iletişim için tercih edilen altyapı, SOA'da kullanılan büyük broker ve orkestratörlerden farklı olan hafif bir mesaj aracısIdır. Hafif bir ileti aracısında, altyapı genellikle "aptal"dır ve Yalnızca bir mesaj aracısı olarak hareket eder ve TavşanMQ gibi basit uygulamalar veya Azure Servis Veri Servisi gibi bulutta ölçeklenebilir servis veri neşrısı ile hareket eder. Bu senaryoda, "akıllı" düşünmenin çoğu hala mikro hizmetlerde mesaj üreten ve tüketen uç noktalarda yaşamaktadır.

İzlemeye çalışmanız gereken bir diğer kural da, dahili hizmetler arasında yalnızca eşzamanlı mesajlaşma kullanmak ve yalnızca istemci uygulamalarından ön uç hizmetlerine (API Ağ Geçitleri artı birinci düzey) eşzamanlı iletişim kullanmaktır. mikro hizmetler).

İki tür eşzamanlı ileti iletişimi vardır: tek alıcılı ileti tabanlı iletişim ve birden çok alıcı ileti tabanlı iletişim. Aşağıdaki bölümlerde onlar hakkında ayrıntılı bilgi verilmiştir.

## <a name="single-receiver-message-based-communication"></a>Tek alıcılı ileti tabanlı iletişim

Tek bir alıcıyla ileti tabanlı eşzamanlı iletişim, kanaldan okuyan tüketicilerden tam olarak birine ileti gönderen ve iletinin sadece bir kez işlendiği noktadan noktaya iletişim anlamına gelir. Ancak, özel durumlar vardır. Örneğin, hataları otomatik olarak kurtarmaya çalışan bir bulut sisteminde, aynı ileti birden çok kez gönderilebilir. Ağ veya diğer hatalar nedeniyle istemcinin ileti göndermeyi yeniden denemesi gerekir ve sunucunun belirli bir iletiyi yalnızca bir kez işlemek için idempotent olması için bir işlem uygulaması gerekir.

Tek alıcılı ileti tabanlı iletişim, şekil 4-18'de gösterildiği gibi, bir mikro hizmetten diğerine asenkron komutlar göndermek için özellikle uygundur.

İleti tabanlı iletişim göndermeye başladığınızda (komutlar veya olaylarla), ileti tabanlı iletişimi eşzamanlı HTTP iletişimiyle karıştırmaktan kaçınmalısınız.

![Eşzamanlı mesaj alan tek bir mikro hizmet](./media/asynchronous-message-based-communication/single-receiver-message-based-communication.png)

**Şekil 4-18**. Eşzamanlı mesaj alan tek bir mikro hizmet

Komutlar istemci uygulamalarından geldiğinde, http senkron komutları olarak uygulanabileceğini unutmayın. Daha yüksek ölçeklenebilirliğe ihtiyacınız olduğunda veya ileti tabanlı bir iş sürecindeolduğunuzda ileti tabanlı komutlar kullanmalısınız.

## <a name="multiple-receivers-message-based-communication"></a>Çoklu alıcılar ileti tabanlı iletişim

Daha esnek bir yaklaşım olarak, gönderenden gelen iletişiminizin ek abone mikro hizmetleri veya harici uygulamalar için kullanılabileceğini bilmek için bir yayımlama/abone verme mekanizması da kullanmak isteyebilirsiniz. Böylece, gönderme hizmetinde [açık/kapalı ilkeyi](https://en.wikipedia.org/wiki/Open/closed_principle) izlemenize yardımcı olur. Bu şekilde, gönderen hizmetini değiştirmeye gerek kalmadan gelecekte ek aboneler eklenebilir.

Yayımla/abone iletişimi kullandığınızda, olayları herhangi bir aboneye yayımlamak için bir olay veri günü arabirimi kullanıyor olabilirsiniz.

## <a name="asynchronous-event-driven-communication"></a>Asynchronous olay odaklı iletişim

Eşzamanlı olay odaklı iletişim kullanırken, bir microservice kendi etki alanı içinde bir şey olduğunda bir entegrasyon olayı yayımlar ve başka bir microservice bunun farkında olması gerekir, bir ürün kataloğu microservice bir fiyat değişikliği gibi. Ek mikro hizmetler olaylara abone olur, böylece onları eşzamanlı olarak alabilirler. Bu durumda, alıcılar kendi etki alanı varlıklarını güncelleştirerek daha fazla tümleştirme olayının yayımlanmasını sağlayabilir. Bu yayımlama/abone etme sistemi genellikle bir olay veri ceminin inbir uygulaması kullanılarak gerçekleştirilir. Etkinlik veri veri mesuliyonu, etkinliklere abone olmak veya abone olmak ve olayları yayımlamak için gereken API ile bir soyutlama veya arabirim olarak tasarlanabilir. Olay veri yolunda ayrıca, eşzamanlı iletişimi ve yayımlama/abone etme modelini destekleyen bir mesajlaşma sırası veya servis veri cisi gibi herhangi bir işlem ve mesajlaşma aracısını temel alan bir veya daha fazla uygulama da olabilir.

Bir sistem tümleştirme olayları tarafından yönlendirilen nihai tutarlılık kullanıyorsa, bu yaklaşımın son kullanıcıya tamamen açık olması önerilir. Sistem, istemciden gelen SignalR veya yoklama sistemleri gibi tümleştirme olaylarını taklit eden bir yaklaşım kullanmamalıdır. Son kullanıcı ve işletme sahibi açıkça sistemde nihai tutarlılık kucaklamak ve birçok durumda iş bu yaklaşım ile herhangi bir sorun olmadığını fark etmek zorunda, sürece açık. Kullanıcılar hemen bazı sonuçlar görmeyi bekleyebilirsiniz ve bu nihai tutarlılık ile olmayabilir, çünkü bu önemlidir.

[Dağıtılmış veri yönetimi bölümüiçin Zorluklar ve çözümlerde](distributed-data-management.md) daha önce belirtildiği gibi, birden çok mikro hizmeti kapsayan iş görevlerini uygulamak için tümleştirme olaylarını kullanabilirsiniz. Böylece, bu hizmetler arasında nihai tutarlılık olacak. Sonunda tutarlı bir işlem dağıtılmış eylemler koleksiyonundan oluşur. Her eylemde, ilgili microservice bir etki alanı varlığını güncelleştirir ve aynı uçten uca iş görevi içinde bir sonraki eylemi yükselten başka bir tümleştirme olayı yayımlar.

Önemli bir nokta, aynı etkinliğe abone olan birden çok mikro hizmetle iletişim kurmak isteyebilirsiniz. Bunu yapmak için, Şekil 4-19'da gösterildiği gibi, olay odaklı iletişimi temel alan yayımla/abone ol iletisini kullanabilirsiniz. Bu yayımlama/abone verme mekanizması mikro hizmet mimarisine özel değildir. DDD'deki [Bağlı Bağlamların](https://martinfowler.com/bliki/BoundedContext.html) iletişim kurma biçimine veya yazma veritabanındaki güncelleştirmeleri [Komut ve Sorgu Sorumluluğu Ayrımı (CQRS)](https://martinfowler.com/bliki/CQRS.html) mimari desenindeki okuma veritabanına yayma şeklinize benzer. Amaç, dağıtılmış sisteminizdeki birden çok veri kaynağı arasında nihai tutarlılık sağlamaktır.

![Eşzamanlı olay odaklı iletişimi gösteren diyagram.](./media/asynchronous-message-based-communication/asynchronous-event-driven-communication.png)

**Şekil 4-19**. Asynchronous olay odaklı ileti iletişimi

Bir mikro hizmet, etkinlik odaklı iletişimde etkinlikleri bir etkinlik otobüsüne yayınlar ve birçok mikro hizmet, haberdar olmak ve harekete geçmek için bu servise abone olabilir. Uygulamanız, olay odaklı, ileti tabanlı iletişimler için hangi protokolün kullanılacağını belirler. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) güvenilir sıralı iletişim elde yardımcı olabilir.

Bir olay veri yolunda niçin kullandığınızda, [RabbitMQ](https://www.rabbitmq.com/) gibi bir ileti aracısının API'sini veya [Konularla Azure Servis Veri](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)Cebisi gibi bir servis veri yolundan gelen API'yi kullanarak kodiçeren sınıflardaki ilgili bir uygulamaya dayalı bir soyutlama düzeyi (olay veri birimi arabirimi gibi) kullanmak isteyebilirsiniz. Alternatif olarak, etkinlik veri topunuzu ve yayımlama/abone sisteminizi ifade etmek için NServiceBus, MassTransit veya Brighter gibi üst düzey bir servis veri cebisi kullanmak isteyebilirsiniz.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Üretim sistemleri için mesajlaşma teknolojileri hakkında bir not

Soyut etkinlik veri topunuzu uygulamak için kullanılabilen mesajlaşma teknolojileri farklı düzeylerdedir. Örneğin, RabbitMQ (mesajlaşma aracısı taşıma) ve Azure Servis Veri'si gibi ürünler, RabbitMQ ve Azure Hizmet Veri Yolunda'nın üzerinde çalışabilen NServiceBus, MassTransit veya Brighter gibi diğer ürünlerden daha düşük bir düzeyde yer alır. Seçiminiz, uygulama düzeyinde kaç zengin özellik ve uygulamanız için gereken kutudan kullanılabilirliğe bağlıdır. EShopOnContainers örneğinde yapıldığı gibi, geliştirme ortamınız için sadece bir kavram kanıtı olay otobüsü uygulamak için, Bir Docker konteyner üzerinde çalışan RabbitMQ üstüne basit bir uygulama yeterli olabilir.

Ancak, aşırı ölçeklenebilirliğe ihtiyaç duyan görev açısından kritik ve üretim sistemleri için Azure Hizmet Veri Tos'u değerlendirmek isteyebilirsiniz. Dağıtılmış uygulamaların gelişimini kolaylaştıran üst düzey soyutlamalar ve özellikler için, NServiceBus, MassTransit ve Brighter gibi diğer ticari ve açık kaynaklı hizmet veri merkezlerini değerlendirmenizi öneririz. Tabii ki, RabbitMQ ve Docker gibi alt düzey teknolojilerin üstüne kendi servis otobüsü özellikleri oluşturabilirsiniz. Ama bu sıhhi tesisat iş özel bir kurumsal uygulama için çok fazla mal olabilir.

## <a name="resiliently-publishing-to-the-event-bus"></a>Etkinlik otobüsüne esnek bir şekilde yayımlama

Birden çok mikro hizmet arasında olay odaklı bir mimari uygularken bir sorun, bir şekilde dayalı olay veri yolunda ilgili entegrasyon olay yayımlarken orijinal microservice içinde atomik durum güncellemek için nasıl Hareket. Ek yaklaşımlar da olsa, bunu başarmanın birkaç yolu şunlardır.

- MSMQ gibi işlem (DTC tabanlı) bir sıra kullanma. (Ancak, bu eski bir yaklaşımdır.)

- [İşlem günlüğü madenciliği kullanma.](https://www.scoop.it/t/sql-server-transaction-log-mining)

- Tam [Olay Kaynak](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing) deseni kullanma.

- Giden [Kutusu deseni](https://www.kamilgrzybek.com/design/the-outbox-pattern/)kullanma: olayı oluşturacak ve yayımlayacak bir olay oluşturucu bileşeninin temeli olacak bir ileti sırası olarak işlem veritabanı tablosu.

Eşzamanlı iletişim kullanırken göz önünde bulundurulması gereken ek konular ileti idempotence ve ileti deduplication vardır. Bu konular, daha sonra bu kılavuzda [mikro hizmetler (entegrasyon olayları) arasındaki olay tabanlı iletişimin uygulanması](../multi-container-microservice-net-applications/integration-event-based-microservice-communications.md) bölümünde ele alınmıştır.

## <a name="additional-resources"></a>Ek kaynaklar

- **Olay Odaklı Mesajlaşma** \
  <https://soapatterns.org/design_patterns/event_driven_messaging>

- **Yayınla/Abone Ol** \
  <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Udi Dahan. Netleştirilmiş CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

- **Komut ve Sorgu Sorumluluğu Ayrımı (CQRS)** \
  <https://docs.microsoft.com/azure/architecture/patterns/cqrs>

- **Sınırlı Bağlamlar Arasında İletişim** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Nihai tutarlılık** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Jimmy Bogard' ı. Esneklik Doğru Refactoring: Bağlantı Değerlendirme** \
  <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

> [!div class="step-by-step"]
> [Önceki](communication-in-microservice-architecture.md)
> [Sonraki](maintain-microservice-apis.md)
