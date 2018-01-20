---
title: "Mikro hizmet odaklı bir uygulama tasarlama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet odaklı bir uygulama tasarlama"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 116ddb44655f0a9708a6496cbe7fb4fbc608300b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="designing-a-microservice-oriented-application"></a>Mikro hizmet odaklı bir uygulama tasarlama

Bu bölümde, kuramsal sunucu tarafı kuruluş uygulaması geliştirme odaklanır.

## <a name="application-specifications"></a>Uygulama özellikleri

Kuramsal uygulama iş mantığını yürütme veritabanlarına erişme ve HTML, JSON ve XML yanıtları döndürme isteklerini işler. Uygulama istemciler, tek sayfa uygulamaları (SPAs), geleneksel web uygulamaları, mobil web uygulamaları ve yerel mobil uygulamalar çalıştıran masaüstü tarayıcıları dahil olmak üzere çeşitli desteklemelidir dediğimiz. Uygulamanın, ayrıca bir API kullanmak için üçüncü taraf için doğurabilir. Böylece yaklaşım kısmi hatası durumunda mikro esnekliğini yardımcı olur, ayrıca kendi mikro veya dış uygulamalar zaman uyumsuz olarak tümleştirebilir olmalıdır.

Uygulama bileşenlerinin bu tür oluşur:

-   Sunu bileşenleri. Bu UI işleme ve uzak Hizmetleri kullanma sorumludur.

-   Etki alanı veya iş mantığı. Uygulama etki alanı mantığı budur.

-   Veritabanı erişim mantığı. Bu, veri erişimi bileşenleri veritabanları (SQL veya NoSQL) erişmek için sorumlu oluşur.

-   Uygulama Tümleştirme mantığı. Bu, çoğunlukla ileti aracıları dayalı bir Mesajlaşma kanalı içerir.

Uygulama yüksek ölçeklenebilirlik, belirli alt sistemleri diğerlerinden daha fazla ölçeklenebilirlik gerektireceğinden sınırlarına, genişletilecek dikey onun alt sistemleri verirken gerektirir.

Uygulama birden çok alt yapısı (birden çok genel Bulutlar ve şirket içi) ortamlarında kullanılabilir kurabilmesi gerekir ve ideal olmalıdır platformlar arası, Windows (veya tersi) Linux kolayca taşımak kullanabilirsiniz.

## <a name="development-team-context"></a>Geliştirme ekibi bağlamı

Ayrıca uygulama geliştirme süreci hakkında aşağıdakileri varsayıyoruz:

-   Uygulama farklı iş alanlarının odaklanan birden çok geliştirme ekipleri sahip.

-   Yeni ekip üyelerinin hızla üretken gerekir ve uygulama anlamak ve değiştirilmesi kolay olmalıdır.

-   Uygulama, uzun vadeli bir evrimi ve sürekli değişen iş kurallarını sahip olur.

-   Gelecekte yeni değişiklikler diğer alt sistemleri üzerinde en az etki ile birden çok alt sistemleri güncelleştirmek kullanabilmeye devam ederken uygularken çeviklik sahip olmak anlamına gelir iyi uzun süreli bakım gerekir.

-   Alıştırma sürekli tümleştirme ve uygulamanın sürekli dağıtımını istediğiniz.

-   Ortaya çıkan teknolojilerden (çerçeveler programlama dilleri, vb.) uygulama gelişen sırasında istediğiniz. Uygulamanın tam geçişler yüksek maliyetlerinin azalmasına neden ve öngörülebilirlik ve uygulama kararlılığını etkisi olduğundan yeni teknolojileri için taşırken hale getirmek istiyor musunuz.

## <a name="choosing-an-architecture"></a>Bir mimari seçme

Uygulama dağıtım mimarisi ne olmalı? Bu iş mikro ve kapsayıcıları, biçiminde otonom alt sistemleri içine bir mikro hizmet burada ayırma tarafından uygulama mimari geliştirme bağlam birlikte uygulama özelliklerini kesinlikle önerir bir kapsayıcıdır.

Bu yaklaşımda, her hizmetin (kapsayıcı) bağlı ve dar ilgili işlevler kümesi uygular. Örneğin, bir uygulama, hizmet, sepet hizmeti, kullanıcı profili hizmeti, vb. sıralama katalog hizmeti gibi hizmetlerin oluşabilir.

Mikro iletişim protokolleri tür olarak HTTP (REST), ancak ayrıca zaman uyumsuz olarak kullanarak (örneğin, AMQP kullanarak) mümkün olduğunda, özellikle zaman yayılıyor güncelleştirmeleri tümleştirme olaylarla.

Mikro geliştirilen ve kapsayıcı birbirinden bağımsız olarak dağıtılabilir. Bu geliştirme ekibi kullanılabilir geliştirme ve diğer alt sistemleri etkilemeden bir belirli mikro hizmet dağıtma olduğunu anlamına gelir.

Her mikro hizmet tam olarak diğer mikro ayrılmış izin veren kendi veritabanı vardır. Gerektiğinde, farklı mikro veritabanlarından arasında tutarlılığı (aracılığıyla bir mantıksal olay bus), uygulama düzeyinde tümleştirme olaylarını kullanarak komut ve sorgu sorumluluk ayrımı (CQRS) işlenmiş olarak sağlanır. İş kısıtlamalarını birden çok mikro arasında nihai tutarlılık, nedeniyle çekirdeğin gerekir ve ilgili veritabanları.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: .NET Core ve kapsayıcılar kullanılarak dağıtılan mikro hizmetler için bir başvuru uygulaması

Mimari ve teknolojileri göz önünde bulundurulması değil bilirsiniz hypothetic iş etki alanı yerine odaklanabilirsiniz böylece, bilinen iş etki alanı seçmiş olduğunuz — yani, kataloğunu sunan bir Basitleştirilmiş e-ticaret (e-Atölye) uygulama ürünler, siparişler müşterilerden alır, Envanter doğrular ve diğer iş işlevleri gerçekleştirir. Bu kapsayıcı tabanlı uygulama kaynak koduna kullanılabilir [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub depo.

Uygulamayı birkaç deposu UI ön uçlar (bir Web uygulaması ve yerel bir mobil uygulama), tüm gereken sunucu tarafı işlemleri için kapsayıcılar ve arka uç mikro birlikte dahil olmak üzere birden çok alt sistemleri oluşur. Şekil 8-1 başvuru uygulaması mimarisini gösterir.

![](./media/image1.png)

**Şekil 8-1**. Uygulama, doğrudan bir istemci mikro hizmet iletişim ve olay bus gösteren eShopOnContainers başvurusu

**Barındırma ortamı**. Şekil 8-1'de çok kapsayıcı içindeki tek bir Docker ana bilgisayara dağıtılan bakın. Olacaktır durum docker ile tek bir Docker ana bilgisayara dağıtırken-komutu oluşturun. Ancak, kullanıyorsanız bir orchestrator veya kapsayıcı küme, her kapsayıcı kullanarak farklı bir konak (düğüm) içinde çalışıyor olabilecek ve biz mimarisi bölümünde daha önce açıklandığı gibi herhangi bir düğümün kapsayıcıları, herhangi bir sayıda çalışıyor.

**İletişim mimarisi**. EShopOnContainers uygulama (sorgular güncelleştirmeler ve işlemleri karşı) işlevsel eylem türünü bağlı olarak iki iletişim türlerini kullanır:

-   Doğrudan istemci mikro hizmet iletişim. Bu sorguları ve güncelleştirme veya istemci uygulamalardan işlem komutları kabul ederken kullanılır.

-   Zaman uyumsuz olay tabanlı iletişim. Mikro arasında güncelleştirmeleri yayılmasına veya dış uygulamalarla tümleştirmek için bir olay veri yolu üzerinden gerçekleşir. Olay veri yolu RabbitMQ veya Azure Service Bus, NServiceBus, MassTransit veya Brighter gibi daha üst düzey hizmet yollarına kullanarak gibi tüm Mesajlaşma Aracısı altyapı teknolojilerde uygulanabilir.

Uygulama kapsayıcıları biçiminde mikro kümesi olarak dağıtılır. İstemci uygulamaları Bu kapsayıcılar ile iletişim yanı sıra mikro iletişim. Bu ilk mimarisi belirtildiği gibi bir istemci uygulaması istekleri her mikro doğrudan yapabileceğini anlamına gelir bir doğrudan istemci mikro hizmet iletişim mimarisi kullanıyor. Her mikro hizmet https://servicename.applicationname.companyname gibi genel bir uç nokta vardır. Gerekirse, her mikro hizmet farklı bir TCP bağlantı noktası kullanabilirsiniz. URL mikro yük dengeleyici ile eşleyin üretim, hangi isteklerini kullanılabilir mikro hizmet örnekleri arasında dağıtır.

**Önemli Not API ağ geçidi vs üzerinde. EShopOnContainers doğrudan iletişime.** Büyük ve karmaşık mikro hizmet tabanlı bir uygulama oluştururken bu kılavuzu mimarisi bölümünde açıklandığı gibi doğrudan istemci mikro hizmet iletişim mimarisi dezavantajları olabilir. Ancak eShopOnContainers olduğu hedef bir basit odaklanın uygulama, Docker kapsayıcısı tabanlı uygulama başlatıldı ve bir tek tek yapılı API etkileyebilir ağ geçidi oluşturmak istemediğinize gibi küçük bir uygulama için yeterince iyi olabilir mikro geliştirme otonomisi.

Ancak, mikro düzinelerce bulunan büyük mikro hizmet tabanlı uygulamaları tasarlamak için kullanacaksanız, biz mimarisi bölümünde açıklandığı gibi API ağ geçidi düzeni dikkate almanız önerilir.
Bu mimari karar üretime hazır uygulamalar ve özel olarak yapılan cepheleri hakkında uzak istemciler için düşünüyorum sonra bulunanad. İstemci uygulamaları form faktörü bağlı olarak özel birden çok API ağ geçidi sahip istemci uygulaması başına farklı veri toplama in regard to faydaları sağlayabilir artı iç mikro veya API için istemci uygulamaları gizleme ve bu tek katmanında yetkilendirin. 

Ancak ve sözü edilen, olarak büyük ve tek yapılı API, mikro geliştirme otonomisi KILL ağ geçitleri karşı dikkatli olun.

### <a name="data-sovereignty-per-microservice"></a>Mikro hizmet başına veri egemenliği

Örnek uygulamadaki her mikro hizmet kendi veritabanı veya veri kaynağı ile her veritabanı sahibi veya veri kaynağı başka bir kapsayıcı olarak dağıtılır. Bu tasarım kararına yalnızca kodu Github'dan alma, kopyalayın ve Visual Studio veya Visual Studio Code açmak bir geliştirici kolaylaştırmak üzere yapılmıştır. Veya alternatif olarak, .NET Core CLI ve Docker CLI kullanarak özel Docker görüntülerinizi derleyin ve ardından dağıtmak ve Docker geliştirme ortamında çalıştırmak kolaylaştırır. Her iki durumda da kapsayıcıları için verileri kullanarak, geliştiriciler oluşturun ve birkaç dakika içinde dış veritabanı veya başka bir veri kaynağını altyapısı (Bulut veya şirket içi) sabit bağımlılıkları olan sağlamak zorunda kalmadan dağıtmanıza olanak tanır kaynakları.

Gerçek üretim ortamında, yüksek kullanılabilirlik ve ölçeklenebilirlik için veritabanlarını veritabanı sunucularında bulutta veya şirket içi, ancak kapsayıcıları bağlı olmalıdır.

Bu nedenle, Docker kapsayıcıları birimleridir mikro hizmetler için (ve bu uygulamada veritabanları için bile) dağıtım ve başvuru uygulaması mikro ilkeleri kapsayan bir çok kapsayıcı uygulamasıdır.

### <a name="additional-resources"></a>Ek kaynaklar

-   **GitHub depo eShopOnContainers. Kaynak kodu başvuru uygulaması için**
    *https://aka.ms/eShopOnContainers/*

## <a name="benefits-of-a-microservice-based-solution"></a>Mikro hizmet tabanlı bir çözüme yararları

Mikro hizmet tabanlı çözüm bu gibi birçok avantaj vardır:

**Her mikro hizmet görece küçük — gelişmesi ve yönetmek kolay**. Özellikle:

-   Anlamak ve iyi verimliliğini hızlıca başlamak bir geliştirici kolaydır.

-   Kapsayıcıları, geliştiricilerin daha verimli hale getirir Hızlı Başlat.

-   Visual Studio gibi bir IDE küçük projeleri hızlı, geliştiricilerin üretken yapmadan yükleyebilir.

-   Her mikro hizmet tasarlanmış, geliştirilmiş ve çeviklik mikro yeni sürümlerini sık dağıtmak daha kolay olduğundan sağlayan diğer mikro bağımsız olarak dağıtılabilir.

**Uygulamanın tek tek alanlarda genişletme mümkündür**. Örneği için katalog hizmeti veya Sepeti hizmeti çıkışı, sipariş sürecini değil ölçeklendirilmesi gerekebilir. Mikro altyapı tek yapılı bir mimari daha ölçeğini genişletme sırasında kullanılan kaynaklara göre çok daha etkili olacaktır.

**Birden çok ekibin arasındaki geliştirme iş bölebilirsiniz**. Her hizmet tek geliştirme ekibi tarafından ait olabilir. Her takım yönetmek, geliştirmek, dağıtmak ve takımlar kalan bağımsız olarak kendi hizmet ölçeklendirin.

**Sorunları daha yalıtılmış**. Bir hizmetinde bir sorun varsa, yalnızca bu hizmet, başlangıçta (yanlış tasarım, mikro arasında doğrudan bağımlılıkları ile kullanıldığında dışında) etkilenir ve diğer hizmetleri istekleri işlemeye devam edebilirsiniz. Buna karşılık, özellikle bir bellek sızıntısı gibi kaynaklar gerektirdiğinde tek yapılı dağıtım mimarisi düzgün çalışmayan bir bileşenin tüm sistemin kullanıma sunabilirsiniz. Ayrıca, bir mikro hizmet bir sorun çözüldüğünde, uygulamanın geri kalanına etkilemeden yalnızca etkilenen mikro dağıtabilirsiniz.

**En yeni teknolojileri kullanabilirsiniz**. Hizmetleri bağımsız olarak geliştirmeye başlayın ve yan yana (kapsayıcılar ve .NET Core sayesinde) çalıştırmak için en yeni teknolojileri ve çerçeveleri expediently çerçevesi için tam veya eski bir yığın sıkışan yerine kullanmaya başlayabilmeniz için uygulama.

## <a name="downsides-of-a-microservice-based-solution"></a>Mikro hizmet tabanlı bir çözüme downsides

Bu gibi bir temel mikro hizmet çözümü, ayrıca bazı sakıncaları vardır:

**Dağıtılmış uygulama**. Tasarlarken ve hizmetler oluşturma uygulaması dağıtma karmaşıklığını geliştiriciler için ekler. Örneğin, geliştiricilerin HTTP ya da test ve özel durum işleme için karmaşıklık ekler AMPQ gibi protokolleri kullanılarak interservice iletişim uygulamalıdır. Aynı zamanda gecikme sisteme ekler.

**Dağıtım karmaşıklığını**. Mikro türleri düzinelerce sahiptir ve yüksek ölçeklenebilirlik (Bu hizmeti başına çok sayıda örnekleri oluşturmak ve bu hizmetleri pek çok konak genelinde dengelemek gerekir) gerekiyor bir uygulama dağıtım karmaşıklığını yüksek derecede BT işlemleri ve yönetimi için anlamına gelir. Mikro hizmet odaklı bir altyapı (örneğin, bir orchestrator ve Zamanlayıcı) kullanmıyorsanız, bu ek karmaşıklık iş uygulaması daha çok daha fazla geliştirme çaba gerektirebilir.

**Atomik işlemleri**. Genellikle birden çok mikro arasındaki atomik işlemleri mümkün değildir. Birden çok mikro arasında nihai tutarlılık kapsayacak şekilde iş gereksinimleri vardır.

**Genel kaynak gereksinimlerini artan** (toplam bellek, sürücüler ve ağ kaynakları tüm sunucuları veya ana bilgisayarlar için). Mikro yaklaşımda, tek yapılı bir uygulamayı değiştirdiğinizde çoğu durumda, yeni mikro hizmet tabanlı uygulama tarafından gerek duyulan Genel kaynaklar miktarı özgün tek yapılı uygulama Altyapı gereksinimlerini büyük olacaktır. Ayrıntı düzeyi ve Dağıtılmış hizmetler yüksek ölçüde daha genel kaynaklar gerektirdiğinden budur. Ancak, düşük maliyetli genel ve yalnızca belirli alanları tek yapılı uygulamaları gelişen, uzun vadeli maliyetleri karşılaştırıldığında uygulamanın ölçeğini yapamamasına yararı kaynakların verildiğinde, artan kaynaklar için genellikle iyi bir kolaylığını kullanımıdır büyük uzun vadeli uygulamalar.

**Doğrudan client‑to‑microservice iletişimle ilgili sorunlar**. Uygulama mikro düzinelerce ile büyük olduğunda olup olmadığını zorluklar ve sınırlamalar doğrudan istemci mikro hizmet iletişimleri uygulama gerektiriyor. İstemci gereksinimlerini ve her mikro tarafından sunulan API'lerde olası eşleşmiyorsa bir sorundur. Bazı durumlarda, istemci uygulaması Internet üzerinden verimsiz olabilir ve bir mobil ağ üzerinden pratik kullanıcı Arabirimi oluşturmak için birçok ayrı istekleri yapmanız gerekebilir. Bu nedenle, arka uç sistem istemci uygulamaya gelen istekleri en aza.

Başka bir doğrudan istemci mikro hizmet iletişimi bazı mikro Web dostu olmayan protokolleri kullanarak sorunudur. AMQP ileti başka bir hizmet kullanırken bir hizmet ikili bir protokol kullanıyor olabilir. Bu protokoller firewall‑friendly değildir ve en iyi dahili olarak kullanılır. Genellikle, bir uygulama güvenlik duvarı dışında iletişim için HTTP ve WebSockets gibi protokoller kullanmanız gerekir.

Henüz bu doğrudan client‑to‑service yaklaşım ile başka bir dezavantajı, onu bu mikro sözleşmeleri yeniden düzenlemeniz zor yapmasıdır. Zaman içinde geliştiriciler Sistem Hizmetleri içine nasıl bölümlenmiş değiştirmek isteyebilirsiniz. Örneğin, bunlar iki hizmet birleştirme veya iki veya daha fazla hizmetlerine bir hizmet bölme. İstemciler doğrudan hizmetlerle iletişim kurar, ancak bu tür yeniden düzenleme gerçekleştirme İstemci uygulamalarıyla uyumluluk bozulabilir.

Tasarlarken ve mikro üzerinde temel karmaşık bir uygulama oluşturma mimarisi bölümünde belirtildiği gibi basit bir doğrudan client‑to‑microservice iletişimi yaklaşım yerine hassas birden çok API ağ geçidi kullanımını düşünebilirsiniz.

**Mikro bölümleme**. Son olarak, mikro hizmet mimarisi için atmanız hangi yaklaşımın olsun, başka bir sınama birden çok mikro uçtan uca uygulamasına bölümlemek nasıl karar vermektir. Kılavuzu mimarisi bölümünde belirtildiği gibi çeşitli teknikleri ve uygulayabileceğiniz bir yaklaşım vardır. Temel olarak, uygulamanın diğer alanlarından ayrılmış ve az sayıda sabit bağımlılıkları olan alanlarında tanımlamanız gerekir. Çoğu durumda, bu hizmetleri bölümleme için kullanım örneği tarafından hizalanır. Örneğin, e-Atölye uygulamamız sırası işlemi ile ilgili tüm iş mantığı sorumlu olduğu bir sıralama hizmeti sunuyoruz. Biz de katalog hizmeti ve diğer özellikleri uygulamak Sepeti hizmetine sahip. İdeal olarak, her hizmetin sorumlulukları küçük bir kümesini olmalıdır. Bu, bir sınıf değiştirmek için bir sebep yalnızca olması gerektiğini bildiren sınıfa uygulanan tek sorumluluk ilkeye (SRP) benzer. Ancak bu durumda, kapsamı tek bir sınıf büyük olacak şekilde mikro hakkında değil. En önemlisi, bir mikro hizmet tamamen otonom, uçtan uca, kendi veri kaynakları için sorumluluk dahil olmak zorundadır.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Dış iç mimarisi ve tasarım desenleri karşılaştırması

Bu kılavuz mimarisi bölümünde açıklanan ilkeler aşağıdaki birden fazla hizmet tarafından oluşan mikro hizmet mimarisi dış mimarisidir. Ancak, yapısı her mikro hizmet ve üst düzey mikro hizmet mimarisi seçtiğiniz bağımsız olarak, bağlı olarak ortak ve bazen önerilir farklı iç mimari sağlamak için, her için farklı düzenlerini esas alarak farklı mikro. Mikro bile farklı teknolojiler ve programlama dilleri kullanabilirsiniz. Şekil 8-2 Bu seviyelerine gösterilmektedir.

![](./media/image2.png)

**Şekil 8-2**. Dış iç mimarisi ve tasarım karşılaştırması

Örneğin, bizim *eShopOnContainers* örnek, kataloğu, sepet ve kullanıcı profil mikro basit (temel olarak, CRUD alt sistemleri). Bu nedenle, kendi iç mimari ve tasarım kolay. Ancak, daha karmaşık ve etki alanı karmaşıklık yüksek derecede ile sürekli değişen iş kurallarını gösteren sıralama mikro gibi diğer mikro olabilir. Bu gibi durumlarda, biz yaptıklarını olarak etki alanı Odaklı Tasarım (DDD) yaklaşımlar ile tanımlanan olanlar gibi belirli bir mikro hizmet içinde daha gelişmiş desen uygulamak isteyebilirsiniz *eShopOnContainers* sıralama mikro hizmet. (Bu DDD desenleri uygulanması açıklayan bölümünde daha sonra gözden geçireceğiz *eShopOnContainers* mikro hizmet sıralama.)

Mikro hizmet başına farklı bir teknoloji başka bir nedenle her mikro hizmet yapısını olabilir. Örneğin, F gibi işlevsel bir programlama dili kullanmak daha iyi olabilir\#, hatta R gibi bir dili AI ve machine learning C gibi daha fazla nesne odaklı programlama dili yerine etki alanları hedefliyorsanız\#.

Alt çizgi, farklı tasarım desenleri esas alarak farklı bir iç mimari her mikro hizmet sahip olabilmesidir. Bunları aşırı mühendislik çünkü tüm mikro Gelişmiş DDD desenler kullanılarak uygulanmalıdır. Benzer şekilde, sürekli değişen iş mantığı ile karmaşık mikro CRUD bileşenleri olarak uygulanmamalıdır veya düşük kaliteli koduyla düşebilir.



## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Yeni bir dünya: birden fazla mimari desenleri ve polyglot mikro hizmetler

Yazılım mimarları ve geliştiricileri tarafından kullanılan birçok mimari desenleri vardır. Birkaç verilmiştir (mimarisi stilleri ve mimari desenleri karıştırma):

-   Basit CRUD, tek katmanlı tek katmanlı.

-   [Geleneksel N katmanlı](https://msdn.microsoft.com/library/ee658109.aspx#Layers).

-   [Etki alanı tasarım N katmanlı temelli](https://blogs.msdn.microsoft.com/cesardelatorre/2011/07/03/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

-   [Mimari temiz](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (ile kullanılmak üzere [eShopOnWeb](http://aka.ms/WebAppArchitecture))

-   [Komut ve sorgu sorumluluk ayrımı](https://martinfowler.com/bliki/CQRS.html) (CQRS).

-   [Olay kaynaklı mimarisi](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Ayrıca, pek çok teknolojileri ve ASP.NET Core Web API'leri, NancyFx, ASP.NET Core SignalR (.NET Core 2 ile de kullanılabilir), F gibi dilleri mikro oluşturabilirsiniz\#, Node.js, Python, Java, C++, GoLang ve daha fazlası.

En önemli nokta belirli mimarisi düzeni veya stili ya da belirli bir teknoloji tüm durumlarda doğru olmasıdır. Şekil 8-3 bazı yaklaşımlar ve gösterir teknolojileri (değil, belirli bir sıraya rağmen) farklı mikro kullanılabilirdi.

![](./media/image3.png)

**Şekil 8-3**. Birden çok mimari desenleri ve polyglot mikro world

Gösterildiği gibi Şekil 8-3, uygulamalarda birçok mikro (ilişkisindeki her mikro hizmet farklı bir şekilde uygulayabilir bağlamlarda etki alanı Odaklı Tasarım terminolojisi ya da yalnızca "alt" otonom mikro olarak) oluşur. Her farklı mimari düzeni sahip ve farklı diller ve veritabanları uygulamanın yapısı, iş gereksinimlerini ve öncelikler bağlı olarak kullanabilirsiniz. Bazı durumlarda, mikro benzer olabilir. Ancak, her alt sisteminin bağlam sınır ve gereksinimleri genellikle farklı olduğundan, genellikle, geçerli değildir.

Örneği için bir basit CRUD bakım uygulama için bunu DDD desenleri tasarlayıp için anlamlı olmayabilir. Ancak çekirdek etki alanı veya çekirdek iş için iş karmaşıklık sürekli değişen iş kuralları ile üstesinden gelmek için daha gelişmiş desenleri uygulamanız gerekebilir.

Özellikle, birden çok alt sistemleri tarafından oluşan büyük uygulamalar ile dağıttığınızda, bir tek mimarisi deseni temel alınarak tek bir üst düzey mimari geçerli. Örneğin, CQRS tüm uygulama için bir en üst düzey mimari olarak uygulanmamalıdır, ancak belirli bir hizmetler kümesini için yararlı olabilir.

Gümüş madde işareti yok veya verilen her durum için doğru mimari desen yoktur. "Tümünü kural için bir mimari desen." sahip olamaz Her mikro Hizmet öncelikleri bağlı olarak, farklı bir yaklaşım her biri için aşağıdaki bölümlerde açıklandığı gibi seçmeniz gerekir.


>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (veri-güdümlü-crud-microservice.md)
