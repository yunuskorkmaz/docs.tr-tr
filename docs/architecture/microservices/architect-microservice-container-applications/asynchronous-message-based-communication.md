---
title: Zaman uyumsuz ileti tabanlı iletişim
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Zaman uyumsuz ileti tabanlı iletişimler mikro hizmetler mimarisinde önemli bir kavramdır, çünkü mikro hizmetleri bir diğerinden bağımsız tutmanın en iyi yolu, Ayrıca, sonunda da eşzamanlı olarak eşitlenmektir.
ms.date: 09/20/2018
ms.openlocfilehash: 84eaf70178cce91a86dae8a55badb0b4ddd6a7c1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454239"
---
# <a name="asynchronous-message-based-communication"></a>Zaman uyumsuz ileti tabanlı iletişim

Zaman uyumsuz mesajlaşma ve olay odaklı iletişim, değişiklikler birden çok mikro hizmette ve ilgili etki alanı modelleriyle yayılırken kritik öneme sahiptir. Daha önce tartışma mikro hizmetleri ve sınırlanmış bağlamlar (IBH), modeller (Kullanıcı, müşteri, ürün, hesap, vb.), farklı mikro hizmetler veya BCs farklı şeyler anlamına gelebilir. Bu, değişiklikler gerçekleştiğinde farklı modellerdeki değişiklikleri mutabık kılmak için bir yol yapmanız gerektiği anlamına gelir. Bir çözüm, zaman uyumsuz mesajlaşmaya göre nihai tutarlılık ve olay odaklı iletişimdir.

Mesajlaşma kullanılırken, işlem zaman uyumsuz olarak ileti değiş tokuşu yaparak iletişim kurar. İstemci bir ileti göndererek bir komut veya hizmet isteği yapar. Hizmetin yanıt vermesi gerekiyorsa, istemciye başka bir ileti gönderilir. İleti tabanlı bir iletişim olduğundan, istemci yanıtın hemen alınmayabileceğini ve hiç yanıt alınmadığını varsayar.

Bir ileti, bir üst bilgi (tanımlama veya güvenlik bilgileri gibi meta veriler) ve bir gövde ile oluşur. İletiler genellikle AMQP gibi zaman uyumsuz protokoller aracılığıyla gönderilir.

Mikro hizmetler topluluğundaki bu iletişim türü için tercih edilen altyapı, SOA 'de kullanılan büyük aracılardan ve düzenleyicilerinden farklı olan hafif bir ileti aracısıdır. Hafif bir ileti aracısından altyapı genellikle "Dumb", yalnızca bir ileti Aracısı olarak davranan, bulutta ırbbitmq veya ölçeklenebilir bir hizmet veri yolu gibi basit uygulamalarla (Azure Service Bus gibi). Bu senaryoda, "akıllı" düşünmenin çoğu, iletileri üreten ve kullanan uç noktalarda (mikro hizmetlerde) devam etmektedir.

İzlemeniz gereken diğer bir kural, iç hizmetler arasında yalnızca zaman uyumsuz mesajlaşma kullanmak ve yalnızca istemci uygulamalarından ön uç hizmetlerine (HTTP gibi) zaman uyumlu iletişim (API ağ geçitleri ve ilk düzey) kullanmak için kullanılır. veya mikro hizmetler).

İki tür zaman uyumsuz mesajlaşma iletişimi vardır: tek alıcı ileti tabanlı iletişim ve birden çok alıcı ileti tabanlı iletişim. Aşağıdaki bölümlerde bunlarla ilgili ayrıntılar sağlanmaktadır.

## <a name="single-receiver-message-based-communication"></a>Tek ahize ileti tabanlı iletişim

Tek bir alıcı ile ileti tabanlı zaman uyumsuz iletişim, kanaldan okuyan tüketicilerden tam olarak birine bir ileti sunan noktadan noktaya iletişim ve iletinin yalnızca bir kez işlendiğini gösterir. Ancak, özel durumlar vardır. Örneğin, hatalardan otomatik olarak kurtarmaya çalışan bir bulut sisteminde, aynı ileti birden çok kez gönderilebilir. Ağ veya diğer hatalardan dolayı istemcinin iletileri göndermeyi yeniden denemesi gerekir ve sunucunun belirli bir iletiyi yalnızca bir kez işlemesi için ıdempotent olmak üzere bir işlem uygulaması gerekir.

Tek alıcıdaki ileti tabanlı iletişim, bu yaklaşımı gösteren şekil 4-18 ' de gösterildiği gibi, bir mikro hizmetten diğerine zaman uyumsuz komutların gönderilmesi için özellikle idealdir.

İleti tabanlı iletişim göndermeye başladıktan sonra (komutları veya olayları kullanarak), zaman uyumlu HTTP iletişimi ile ileti tabanlı iletişimi karıştırmaktan kaçının.

![Tek bir mikro hizmet zaman uyumsuz ileti alıyor](./media/asynchronous-message-based-communication/single-receiver-message-based-communication.png)

**Şekil 4-18**. Tek bir mikro hizmet zaman uyumsuz ileti alıyor

Komutların istemci uygulamalardan geldiği durumlarda, bunların HTTP zaman uyumlu komutları olarak uygulanmaları gerektiğini unutmayın. Daha yüksek ölçeklenebilirlik gerektiğinde veya ileti tabanlı bir iş sürecinizdeki ileti tabanlı komutları kullanmanız gerekir.

## <a name="multiple-receivers-message-based-communication"></a>Birden çok alıcılar ileti tabanlı iletişim

Daha esnek bir yaklaşım olarak, gönderenden iletişimin ek abone mikro hizmetleri veya dış uygulamalar tarafından kullanılabilmesi için bir yayımlama/abone olma mekanizması kullanmak da isteyebilirsiniz. Bu nedenle, gönderme hizmetindeki [açık/kapalı ilkesini](https://en.wikipedia.org/wiki/Open/closed_principle) izlemenize yardımcı olur. Bu şekilde, gönderen hizmetini değiştirme gereksinimi olmadan gelecekte ek aboneler eklenebilir.

Yayımla/abone ol iletişimi kullandığınızda, olayları herhangi bir aboneye yayımlamak için bir olay veri yolu arabirimi kullanıyor olabilirsiniz.

## <a name="asynchronous-event-driven-communication"></a>Zaman uyumsuz olay temelli iletişim

Zaman uyumsuz olay temelli iletişim kullanılırken, mikro hizmet, etki alanı içinde bir şeyler olduğunda bir tümleştirme olayı yayınlar ve bir ürün kataloğu mikro hizmetindeki fiyat değişikliği gibi başka bir mikro hizmetin bunu farkında olması gerekir. Ek mikro hizmetler, olayları zaman uyumsuz olarak alabilmesi için olaylara abone olur. Bu durumda alıcılar kendi etki alanı varlıklarını güncelleştirebilir ve bu da daha fazla tümleştirme olayının yayımlanmasına neden olabilir. Bu yayımlama/abone olma sistemi genellikle bir olay veri yolunun uygulanması kullanılarak gerçekleştirilir. Olay veri yolu, bir soyutlama veya arabirim olarak tasarlanabilir ve olaylara abone olmak ya da aboneliği kaldırmak ve olayları yayımlamak için gereken API 'yi kullanabilir. Olay veri yolu, zaman uyumsuz iletişimi ve bir yayımlama/abonelik modelini destekleyen bir mesajlaşma kuyruğu ya da hizmet veri yolu gibi işlem tabanlı ve mesajlaşma aracısına dayalı bir veya daha fazla uygulama içerebilir.

Bir sistem, tümleştirme olayları tarafından yönetilen nihai tutarlılığı kullanıyorsa, bu yaklaşımın son kullanıcıya tamamen açık olması önerilir. Sistem, istemci tarafından SignalR veya yoklama sistemleri gibi tümleştirme olaylarını taklit eden bir yaklaşım kullanmamalıdır. Son Kullanıcı ve işletme sahibi sistemde nihai tutarlılığı açıkça benimsemek ve birçok durumda, açık olduğu sürece bu yaklaşım ile ilgili herhangi bir sorun olmadığını fark ediyor. Kullanıcılar bazı sonuçları hemen görmeyi beklediği için bu önemlidir ve bu durum nihai tutarlılık ile gerçekleşmeyebilir.

Daha önce [Dağıtılmış veri yönetimi sorunları ve çözümleri](distributed-data-management.md) bölümünde belirtildiği gibi, birden fazla mikro hizmete yayılan iş görevlerini uygulamak için tümleştirme olaylarını kullanabilirsiniz. Bu nedenle, bu hizmetler arasında nihai tutarlılık olacaktır. Sonuçta tutarlı bir işlem, dağıtılmış eylemler koleksiyonundan oluşur. Her eylemde, ilgili mikro hizmet bir etki alanı varlığını güncelleştirir ve aynı uçtan uca iş göreviyle sonraki eylemi başlatan başka bir tümleştirme olayı yayımlar.

Önemli bir nokta, aynı olaya abone olan birden fazla mikro hizmet ile iletişim kurmak isteyebileceğiniz bir noktasıdır. Bunu yapmak için Şekil 4-19 ' de gösterildiği gibi, olay odaklı iletişime göre yayımla/abone ol iletilerini kullanabilirsiniz. Bu yayımla/abone olma mekanizması mikro hizmet mimarisine özel değildir. Bu, DDD 'daki [sınırlı bağlamların](https://martinfowler.com/bliki/BoundedContext.html) iletişim kurması veya [komut ve sorgu sorumluluklarının ayrılığı (CQRS)](https://martinfowler.com/bliki/CQRS.html) mimari deseninin yazma veritabanındaki okuma veritabanına nasıl yayılacağından benzerdir. Amaç, dağıtılmış sisteminizde birden çok veri kaynağı arasında nihai tutarlılık sağlamaktır.

![Zaman uyumsuz olay odaklı iletişimleri gösteren diyagram.](./media/asynchronous-message-based-communication/asynchronous-event-driven-communication.png)

**Şekil 4-19**. Zaman uyumsuz olay odaklı ileti iletişimi

Zaman uyumsuz olay odaklı iletişimde, bir mikro hizmet olayları bir olay veri yoluna yayımlar ve çok sayıda mikro hizmet bu hizmete abone olabilir ve bu, bildirim alabilir ve üzerinde işlem yapabilir. Uygulamanız, olay odaklı ileti tabanlı iletişimler için kullanılacak protokolü tespit eder. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) , güvenilir sıraya alınmış iletişimin sağlanmasına yardımcı olabilir.

Bir olay veri yolu kullandığınızda, [Kbbitmq](https://www.rabbitmq.com/) gibi bir ileti ARACıSıDıR API kullanarak kod içeren bir soyutlama düzeyi (bir olay veri yolu arabirimi gibi) ve [konularla birlikte Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)gibi bir hizmet veri yolu kullanmak isteyebilirsiniz. Alternatif olarak, Event Bus ve Yayımla/abone ol sisteminizi ifade etmek için NServiceBus, Masstransıya ya da daha parlak gibi daha yüksek düzeyde bir Service Bus kullanmak isteyebilirsiniz.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Üretim sistemleri için mesajlaşma teknolojileri hakkında bir göz

Özet olay veri yolundan uygulama için kullanılabilen mesajlaşma teknolojileri farklı düzeylerde. Örneğin, Kbbitmq (bir mesajlaşma Aracısı taşıması) ve Azure Service Bus daha düşük bir düzeyde, NServiceBus, Masstransıya veya daha parlaktır. Bu, Kbbitmq ve Azure Service Bus üzerinde çalışabilir. Seçiminiz, uygulama düzeyinde ve uygulamanız için ihtiyaç duyduğunuz çok sayıda zengin özellik sayısına bağlıdır. Geliştirme ortamınız için yalnızca bir kavram kanıtı olay veri yolu uygulamak üzere eShopOnContainers örneğinde yapıldığı gibi, bir Docker kapsayıcısında çalışan kbbitmq üzerinde basit bir uygulama yeterince olabilir.

Ancak, Hyper-ölçeklenebilirlik gerektiren görev açısından kritik ve üretim sistemlerinde Azure Service Bus değerlendirmek isteyebilirsiniz. Dağıtılmış uygulamaların geliştirilmesine daha kolay bir şekilde sahip olan üst düzey soyutlamalar ve özellikler için NServiceBus, Masstransıya ve daha parlak gibi diğer ticari ve açık kaynaklı hizmet veri yollarını değerlendirmeniz önerilir. Tabii ki, Kbbitmq ve Docker gibi alt düzey teknolojilerin üzerine kendi hizmet veri yolu özelliklerinizi oluşturabilirsiniz. Ancak, bu sıhhi tesisat işi özel bir kurumsal uygulama için çok fazla maliyetli olabilirler.

## <a name="resiliently-publishing-to-the-event-bus"></a>Dayanıklı bağlantısı olay veri yoluna yayımlama

Birden fazla mikro hizmette olay odaklı bir mimari uygulamaya yönelik bir zorluk, dayanıklı bağlantısı ilişkili tümleştirme olayını olay veri yoluna yayımlarken, buna bağlı olarak, özgün mikro hizmette durumu otomatik olarak güncelleştirme hareket. Aşağıda, ek yaklaşımlar da dahil olmak üzere, bunu yapmanın birkaç yolu verilmiştir.

- MSMQ gibi bir işlem (DTC tabanlı) kuyruğu kullanma. (Ancak, bu eski bir yaklaşımdır.)

- [İşlem günlüğü madenciliği](https://www.scoop.it/t/sql-server-transaction-log-mining)kullanılıyor.

- Tam [olay](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing) kaynağını belirleme düzenini kullanma.

- [Giden kutusu deseninin](https://www.kamilgrzybek.com/design/the-outbox-pattern/)kullanımı: bir işlem veritabanı tablosu, olayı oluşturacak ve yayınlayacak bir olay Oluşturucu bileşeni için temel olacak bir ileti kuyruğu olarak.

Zaman uyumsuz iletişimin kullanılması sırasında göz önünde bulundurmanız gereken ek konular Message Eşkuvvetlilik ve iletiyi yinelenenleri kaldırma. Bu konular, bu kılavuzun ilerleyen kısımlarında [mikro hizmetler (Tümleştirme olayları) arasındaki olay tabanlı Iletişimi uygulama](../multi-container-microservice-net-applications/integration-event-based-microservice-communications.md) bölümünde ele alınmıştır.

## <a name="additional-resources"></a>Ek kaynaklar

- **Olay odaklı mesajlaşma** \
  <https://soapatterns.org/design_patterns/event_driven_messaging>

- **Yayımla/abone ol kanal** \
  <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **UDI Dahan. Açıklanan CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

- **Komut ve sorgu sorumluluklarının ayrılığı (CQRS)**  \
  <https://docs.microsoft.com/azure/architecture/patterns/cqrs>

- **Sınırlanmış bağlamlar arasında iletişim** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Nihai tutarlılık** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Jimmy Bogard. Esnekliği 'e yeniden düzenleme: kup \ değerlendirilirken**
  <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

> [!div class="step-by-step"]
> [Önceki](communication-in-microservice-architecture.md)
> [İleri](maintain-microservice-apis.md)
