---
title: gRPC
description: gRPC, bulut tasire uygulamalarındaki rolü ve HTTP RESTful iletişiminden nasıl farklı olduğu hakkında bilgi edinin.
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 28a07ad5ec105d3fc5b65e4cf0ac0cd85eb16627
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80524175"
---
# <a name="grpc"></a>gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Şimdiye kadar bu kitapta, biz [REST tabanlı](https://docs.microsoft.com/azure/architecture/best-practices/api-design) iletişim üzerinde duruldu. REST'in, varlık kaynaklarına karşı CRUD tabanlı işlemleri tanımlayan esnek bir mimari stil olduğunu gördük. İstemciler, bir istek/yanıt iletişim modeliyle HTTP genelindeki kaynaklarla etkileşimkurar. REST yaygın olarak uygulansa da, daha yeni bir iletişim teknolojisi olan gRPC, bulut-yerli topluluk genelinde muazzam bir ivme kazanmıştır.

## <a name="what-is-grpc"></a>gRPC nedir?

gRPC, asırlık [uzaktan yordam çağrısı (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) protokolünü geliştiren modern, yüksek performanslı bir çerçevedir. Uygulama düzeyinde, gRPC istemciler ve arka uç hizmetleri arasındaki iletileri kolaylaştırır. Google kaynaklı gRPC, açık kaynak kodludur ve bulut ahalisi teklifleri [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) ekosisteminin bir parçasıdır. CNCF gRPC bir [kuluçka projesi](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc)olarak kabul eder. Kuluçka, son kullanıcıların üretim uygulamalarında teknolojiyi kullandığı anlamına gelir ve projede sağlıklı sayıda katılımcı vardır.

Tipik bir gRPC istemci uygulaması, bir iş işlemini uygulayan yerel, süreç içi bir işlevi ortaya çıkarır. Kapakların altında, bu yerel işlev uzak bir makinede başka bir işlevi çağırır. Yerel bir çağrı gibi görünen şey, aslında uzak bir hizmete yapılan saydam bir işlem dışı çağrı haline gelir. RPC tesisat, bilgisayarlar arasındaki noktadan noktaya ağ iletişimini, serileştirmeyi ve yürütmeyi özetler.

Bulut ait uygulamalarda, geliştiriciler genellikle programlama dilleri, çerçeveler ve teknolojiler arasında çalışır. Bu *birlikte çalışabilirlik,* ileti sözleşmelerini ve platform ötesi iletişim için gereken tesisatı karmaşıklaştırır.  gRPC bu endişeleri özetleyen bir "tek düze katman" sağlar. Geliştiriciler kendi kendi platformunda kod iş işlevselliği üzerinde duruldu, gRPC iletişim sıhhi tesisat işler.

gRPC, Java, JavaScript, C#, Go, Swift ve NodeJS gibi en popüler geliştirme yığınları arasında kapsamlı destek sunar.

## <a name="grpc-benefits"></a>gRPC Avantajları

gRPC, taşıma protokolü için HTTP/2 kullanır. HTTP 1.1 ile uyumlu olsa da, HTTP/2 birçok gelişmiş özellik sunar:

- Veri aktarım için ikili bir protokol - http 1.1'in aksine, verileri açık metin olarak gönderir.
- Aynı bağlantı üzerinden birden çok paralel istek göndermek için çok yönlü destek - HTTP 1.1 aynı anda bir istek/yanıt iletisi ile işlemeyi sınırlar.
- Aynı anda hem istemci isteklerini hem de sunucu yanıtlarını göndermek için çift yönlü tam çift yönlü iletişim.
- Büyük veri kümelerini eş zamanlı olarak akışa göre istekleri ve yanıtları etkinleştiren yerleşik akış.

gRPC hafif ve yüksek performanslı. %60-80 daha küçük iletilerle JSON serileştirmesinden 8 kata kadar daha hızlı olabilir. Microsoft [Windows Communication Foundation (WCF)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) deyimiyle, gRPC performansı son derece optimize edilmiş [NetTCP bağlamalarının](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8)hızını ve verimliliğini aşıyor. Microsoft yığınını destekleyen NetTCP'nin aksine, gRPC çapraz platformdur.

## <a name="protocol-buffers"></a>Protokol Arabellekleri

gRPC [Protokol Tamponlar](https://developers.google.com/protocol-buffers/docs/overview)adlı bir açık kaynak teknolojisi kucaklar. Hizmetlerin birbirine gönderdiği yapılandırılmış iletileri seri hale getirmek için son derece verimli ve platformdan bağımsız bir serileştirme biçimi sağlarlar. Geliştiriciler, platformlar arası Arabirim Tanımı Dili (IDL) kullanarak her bir mikro hizmet için bir hizmet sözleşmesi tanımlar. Metin tabanlı `.proto` bir dosya olarak uygulanan sözleşmede, her hizmetin yöntemleri, girişleri ve çıktıları açıklanır. Aynı sözleşme dosyası, farklı geliştirme platformlarında oluşturulmuş gRPC istemcileri ve hizmetleri için kullanılabilir.

Proto dosyasını kullanarak, Protobuf `protoc`derleyicisi, hedef platformunuz için hem istemci hem de hizmet kodu oluşturur. Kod aşağıdaki bileşenleri içerir:

- İstemci ve hizmet tarafından paylaşılan ve iletinin hizmet işlemlerini ve veri öğelerini temsil eden güçlü bir şekilde yazılan nesneler.
- Uzak gRPC hizmetinin devralabileceği ve genişletebileceği gerekli ağ tesisatı ile güçlü bir şekilde yazılan taban sınıfı.
- Uzaktan gRPC hizmetini çağırmak için gerekli sıhhi tesisatı içeren bir istemci saplaması.

Çalışma zamanında, her ileti standart bir Protobuf gösterimi olarak serihale edilir ve istemci ile uzak hizmet arasında değiştirilir. JSON veya XML'in aksine, Protobuf iletileri derlenmiş ikili baytlar olarak seri hale getirilmiştir.

Kitap, [WCF Geliştiriciler için gRPC](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/), Microsoft Architecture sitesinden kullanılabilir, gRPC ve Protokol Arabellekleri derinlemesine kapsama sağlar.

## <a name="grpc-support-in-net"></a>.NET'te gRPC desteği

gRPC .NET Core 3.0 SDK veya daha sonra entegre edilmiştir. Aşağıdaki araçlar bunu destekler:

- Visual Studio 2019, sürüm 16.3 veya daha sonra, web geliştirme iş yükü yüklü.
- Visual Studio Code
- nokta CLI

SDK uç nokta yönlendirme, yerleşik IoC ve günlük için takım içerir. Açık kaynak kestrel web sunucusu HTTP/2 bağlantılarını destekler. Şekil 4-20, bir gRPC hizmeti için iskelet projesini iskeleleyen visual studio 2019 şablonlarını gösterir. .NET Core'un Windows, Linux ve macOS'u nasıl tam olarak desteklediğine dikkat edin.

![Visual Studio 2019'da gRPC Desteği](./media/visual-studio-2019-grpc-template.png)

**Şekil 4-20**. Visual Studio 2019'da gRPC desteği
  
Şekil 4-21, Visual Studio 2019'da yer alan yerleşik iskeleden üretilen iskelet gRPC hizmetini göstermektedir.  

![Visual Studio 2019'da gRPC projesi](./media/grpc-project.png  )

**Şekil 4-21**. Visual Studio 2019'da gRPC projesi

Önceki şekilde, proto açıklama dosyası ve servis koduna dikkat edin. Kısa bir süre sonra göreceğiniz gibi, Visual Studio hem Başlangıç sınıfında hem de altta yatan proje dosyasında ek yapılandırma oluşturur.

## <a name="grpc-usage"></a>gRPC kullanımı

Aşağıdaki senaryolar için gRPC'yi tercih edin:

- İşleme devam etmek için anında yanıt alınması gereken synchronous backend microservice-to-microservice iletişimi.
- Karma programlama platformlarını desteklemesi gereken çok dilli ortamlar.
- Performansın kritik olduğu düşük gecikme sonu ve yüksek iş letimatif iletişim.
- Noktadan noktaya gerçek zamanlı iletişim - gRPC, anketler yapmadan iletileri gerçek zamanlı olarak itebilir ve çift yönlü akış için mükemmel bir desteğe sahiptir.
- Ağ kısıtlı ortamlar – ikili gRPC iletileri her zaman eşdeğer metin tabanlı JSON iletisinden daha küçüktür.

O zaman, bu yazı, gRPC öncelikle arka uç hizmetleri ile kullanılır. Çoğu modern tarayıcı, bir ön uç gRPC istemcisini desteklemek için gereken HTTP/2 denetim düzeyini sağlayamaz. Bununla birlikte, JavaScript veya Blazor WebAssembly teknolojileri ile oluşturulmuş tarayıcı tabanlı uygulamalardan gRPC iletişimini sağlayan erken bir [girişim](https://devblogs.microsoft.com/aspnet/grpc-web-experiment/) vardır. [.NET için gRPC-Web,](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md) tarayıcı uygulamalarındaki gRPC özelliklerini desteklemek için ASP.NET core gRPC uygulamasına olanak tanır:

- Güçlü bir şekilde kod oluşturulan istemciler
- Kompakt Protobuf mesajları
- Sunucu akışı

## <a name="grpc-implementation"></a>gRPC uygulaması

Microservice başvuru mimarisi, [eShop on Containers](https://github.com/dotnet-architecture/eShopOnContainers), Microsoft, gRPC hizmetlerinin .NET Core uygulamalarında nasıl uygulanacağını gösterir. Şekil 4-22 arka uç mimarisini sunar.

![Konteynerlerde eShop için arka uç mimarisi](./media/eshop-with-aggregators.png)

**Şekil 4-22**. Konteynerlerde eShop için arka uç mimarisi

Önceki şekilde, eShop'un birden çok API ağ geçidini ortaya çıkararak [Frontends deseni](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) (BFF) için Arka Uç'u nasıl kucakladığını not edin. Bu bölümde BFF modelini daha önce tartıştık. Web-Alışveriş API Ağ Geçidi ile arka uç Alışveriş microservices arasında yer alan Toplayıcı microservice'e (gri renkte) dikkat edin. Toplayıcı, bir istemciden tek bir istek alır, çeşitli mikro hizmetlere gönderir, sonuçları toplar ve bunları isteyen istemciye geri gönderir. Bu tür işlemler genellikle hemen yanıt üretmek için eşzamanlı iletişim gerektirir. eShop'ta, Toplayıcı'dan gelen arka uç aramaları Şekil 4-23'te gösterildiği gibi gRPC kullanılarak gerçekleştirilir.

![konteynerlerde eShop'ta gRPC](./media/grpc-implementation.png)

**Şekil 4-23**. konteynerlerde eShop'ta gRPC

gRPC iletişimi hem istemci hem de sunucu bileşenlerini gerektirir. Önceki şekilde, Alışveriş Toplayıcısı'nın bir gRPC istemcisini nasıl uyguladığına dikkat edin. İstemci, her biri bir gRPC sunucusu uygulayan mikro hizmetleri arka dan amaçlamak için eşzamanlı gRPC çağrıları (kırmızı) yapar. Hem istemci hem de sunucu .NET Core 3.0 SDK'dan yerleşik gRPC tesisatından yararlanır. İstemci tarafı *saplamalar* uzak gRPC aramaları çağırmak için sıhhi tesisat sağlar. Sunucu tarafındaki bileşenler, özel hizmet sınıflarının devralıp tüketebileceği gRPC tesisatı sağlar.

Hem RESTful API hem de gRPC iletişimini ortaya çıkaran microservices, trafiği yönetmek için birden çok uç nokta gerektirir. RESTful aramaları için HTTP trafiğini dinleyen bir bitiş noktası ve gRPC aramaları için başka bir bitiş noktası açarsınız. gRPC bitiş noktası, gRPC iletişimi için gerekli olan HTTP/2 protokolü için yapılandırılmalıdır.

Biz asynchronous iletişim kalıpları ile mikro hizmetleri ayırmak için çalışırken, bazı işlemler doğrudan aramalar gerektirir. gRPC mikro hizmetler arasında doğrudan senkron iletişim için birincil seçim olmalıdır. HTTP/2 ve protokol arabelleklerine dayalı yüksek performanslı iletişim protokolü, mükemmel bir seçim dir.

## <a name="looking-ahead"></a>İleriye bakmak

İleriye baktığımızda, gRPC bulut-yerli sistemler için çekiş kazanmaya devam edecektir. Performans avantajları ve gelişim kolaylığı ilgi çekicidir. Ancak, REST büyük olasılıkla uzun bir süre için etrafında olacaktır. Genel olarak açıklanmış API'ler ve geriye dönük uyumluluk nedenleriyle öne çıkmaktadır.

>[!div class="step-by-step"]
>[Önceki](service-to-service-communication.md)
>[Sonraki](service-mesh-communication-infrastructure.md)
