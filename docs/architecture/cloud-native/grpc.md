---
title: gRPC
description: GRPC, bulutta yerel uygulamalardaki rolü ve HTTP ile gerçekleşen iletişimin nasıl farklı olduğunu öğrenin.
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 01dd4c934f0b39041ea377691067edf4dbe20378
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895561"
---
# <a name="grpc"></a>gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Şimdiye kadar bu kitapta, [REST tabanlı](https://docs.microsoft.com/azure/architecture/best-practices/api-design) iletişime odaklandık. REST 'in varlık kaynaklarına karşı CRUD tabanlı işlemleri tanımlayan esnek bir mimari stili olduğunu gördük. İstemciler, istek/yanıt iletişim modeliyle HTTP genelindeki kaynaklarla etkileşime geçin. DIĞER bir deyişle, daha yeni bir iletişim teknolojisi olan gRPC, buluta özgü topluluk genelinde inanılmaz itici güç elde etti.

## <a name="what-is-grpc"></a>GRPC nedir?

gRPC, yaş-eski [uzak yordam çağrısı (RPC) protokolünü gelişten](https://en.wikipedia.org/wiki/Remote_procedure_call) modern ve yüksek performanslı bir çerçevedir. Uygulama düzeyinde, gRPC istemciler ve arka uç hizmetleri arasında ileti gönderimi kolaylaştırır. Google 'dan kaynaklanan gRPC, bulutta yerel [Bilgi Işlem altyapısı (CNCF)](https://www.cncf.io/) ekosisteminin açık kaynak ve bir parçasıdır. CNCF gRPC 'yi bir [ınubating projesi](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc)olarak değerlendirir. Inubating, son kullanıcıların, üretim uygulamalarında teknolojiyi kullandığı ve projenin sağlıklı sayıda katkıda bulunanın olduğu anlamına gelir.

Tipik bir gRPC istemci uygulaması, bir iş işlemi uygulayan yerel, işlem içi bir işlev sergilecektir. Bu yerel işlev, ' ın altında, uzak bir makinede başka bir işlevi çağırır. Yerel bir çağrı olarak görünen, uzak bir hizmete bir saydam işlem dışı çağrısı olur. RPC sıhhi tesisat, bilgisayarlar arasında noktadan noktaya ağ iletişimini, Serileştirmeyi ve yürütmeyi soyutlar.

Bulutta yerel uygulamalarda, geliştiriciler genellikle programlama dilleri, çerçeveler ve teknolojilerde çalışır. Bu *birlikte çalışabilirlik* , platformlar arası iletişim için gereken ileti sözleşmelerini ve sıhhi tesisat 'yi karmaşıklaştırır.  gRPC, bu kaygıları soyutlayan bir "Tekdüzen yatay katman" sağlar. Yerel platformlarda bulunan geliştiriciler iş işlevselliğine odaklanırken, gRPC iletişim sıhhi tesisat ile ilgilenir.

gRPC, Java, JavaScript, C#, Go, Swift ve NodeJS dahil birçok popüler geliştirme yığını genelinde kapsamlı destek sunar.

## <a name="grpc-benefits"></a>gRPC avantajları

gRPC, Aktarım Protokolü için HTTP/2 kullanır. HTTP 1,1 ile uyumlu olmakla birlikte, HTTP/2 özellikleri birçok gelişmiş özelliğe sahiptir:

- Verileri düz metin olarak gönderen HTTP 1,1 'nin aksine veri aktarımı için bir ikili protokol.
- Aynı bağlantı üzerinden birden çok paralel istek göndermek için çoğullama desteği-HTTP 1,1, işleme bir kerede tek bir istek/yanıt iletisi ile sınırlar.
- Hem istemci isteklerini hem de sunucu yanıtlarını aynı anda göndermek için çift yönlü tam çift yönlü iletişim.
- Zaman uyumsuz akış büyük veri kümelerine yönelik istekleri ve yanıtları etkinleştiren yerleşik akış.

gRPC hafif ve yüksek performanslı. % 60-80 daha küçük iletilerle JSON serileştirmesine kadar daha hızlı olabilir. Microsoft [Windows Communication Foundation (WCF)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) ayrıştırmasına göre, GRPC performansı, yüksek oranda Iyileştirilmiş [NetTcp bağlamalarının](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8)hızını ve verimliliğini aşmaktadır. Microsoft Stack ' i tercih eden NetTCP 'nin aksine gRPC platformlar arası bir platformdur.

## <a name="protocol-buffers"></a>Protokol Arabellekleri

gRPC, [protokol arabellekleri](https://developers.google.com/protocol-buffers/docs/overview)adlı açık kaynaklı bir teknolojinin ayraçları. Hizmetlerin birbirlerine gönderdikleri yapılandırılmış iletileri serileştirmek için yüksek düzeyde etkili ve platformdan bağımsız bir serileştirme biçimi sağlar. Platformlar arası arabirim tanım dili (IDL) kullanarak, geliştiriciler her mikro hizmet için bir hizmet sözleşmesi tanımlar. Metin tabanlı `.proto` dosya olarak uygulanan sözleşme, her hizmet için yöntemleri, girişleri ve çıkışları açıklar. Aynı sözleşme dosyası, farklı geliştirme platformları üzerine inşa olan gRPC istemcileri ve hizmetleri için de kullanılabilir.

Prototiparabelleği derleyicisi `protoc`olan proto dosyasını kullanarak, hedef platformunuz için hem istemci hem de hizmet kodu üretir. Kod aşağıdaki bileşenleri içerir:

- İstemci ve hizmet tarafından paylaşılan, bir ileti için hizmet işlemlerini ve veri öğelerini temsil eden türü kesin belirlenmiş nesneler.
- Uzak gRPC hizmetinin devralmasını ve uzatabtiği, gerekli ağ tesisat gerektiren, kesin olarak belirtilmiş bir temel sınıf.
- Uzak gRPC hizmetini çağırmak için gereken sıhhi tesisat 'yi içeren bir istemci saplaması.

Çalışma zamanında, her ileti standart bir Prototipme temsili olarak serileştirilir ve istemci ile uzak hizmet arasında değiş tokuş yapılır. JSON veya XML 'den farklı olarak, prototipli mesajlar derlenmiş ikili bayt olarak serileştirilir.

Microsoft mimari sitesinden sunulan [WCF geliştiricileri Için GRPC](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)Rehberi, GRPC ve protokol arabelleklerinin ayrıntılı kapsamını sağlar.

## <a name="grpc-support-in-net"></a>.NET ' te gRPC desteği

gRPC, .NET Core 3,0 SDK ve sonraki sürümleriyle tümleşiktir. Aşağıdaki araçlar bunu destekler:

- Web geliştirme iş yükü yüklüyken Visual Studio 2019, sürüm 16,3 veya üzeri.
- Visual Studio Code
- DotNet CLı

SDK, Endpoint Routing, yerleşik IOC ve günlüğe kaydetme için araç içerir. Açık kaynaklı Kestrel Web sunucusu HTTP/2 bağlantılarını destekler. Şekil 4-20, bir gRPC hizmeti için iskelet bir projeyi dolandırıcılara bağlayan bir Visual Studio 2019 şablonunu gösterir. .NET Core 'un Windows, Linux ve macOS 'ı tam olarak nasıl desteklediğini aklınızda yapın.

![Visual Studio 2019 ' de gRPC desteği](./media/visual-studio-2019-grpc-template.png)

**Şekil 4-20**. Visual Studio 2019 ' de gRPC desteği
  
Şekil 4-21, Visual Studio 2019 ' de yer alan yerleşik yapı iskelesi tarafından oluşturulan iskelet gRPC hizmetini gösterir.  

![Visual Studio 2019 ' de gRPC projesi](./media/grpc-project.png  )

**Şekil 4-21**. Visual Studio 2019 ' de gRPC projesi

Önceki şekilde, Proto Description dosyası ve hizmet kodu ' na göz önünde. Kısa süre içinde gördüğünüz gibi, Visual Studio hem başlangıç sınıfında hem de temel alınan proje dosyasında ek yapılandırma oluşturur.

## <a name="grpc-usage"></a>gRPC kullanımı

GRPC 'yi aşağıdaki senaryolar için tercih edin:

- İşleme devam etmek için anında yanıtın gerekli olduğu, zaman uyumlu arka uç mikro hizmetten mikro hizmet iletişimi.
- Karma programlama platformlarını desteklemesi gereken çok yönlü ortamları.
- Performansın kritik olduğu düşük gecikme süresi ve yüksek aktarım hızı iletişimi.
- Noktadan noktaya gerçek zamanlı iletişim-gRPC, yoklama yapmadan iletileri gerçek zamanlı olarak gönderebilir ve iki yönlü akış için mükemmel destek sağlar.
- Ağ kısıtlamalı ortamlar – ikili gRPC iletileri her zaman eşdeğer bir metin tabanlı JSON iletisinden küçüktür.

Bu yazma sırasında, gRPC öncelikle arka uç hizmetleriyle birlikte kullanılır. Modern tarayıcıların çoğu, ön uç gRPC istemcisini desteklemek için gereken HTTP/2 denetimi düzeyini sağlayamaz. Yani, JavaScript veya Blazor WebAssembly teknolojileriyle oluşturulmuş tarayıcı tabanlı uygulamalardan gRPC iletişimini sağlayan [erken bir girişim](https://devblogs.microsoft.com/aspnet/grpc-web-experiment/) vardır. [.Net Için GRPC-Web](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md) , ASP.NET Core GRPC uygulamasının tarayıcı uygulamalarında GRPC özelliklerini desteklemesini sağlar:

- Kesin tür belirtilmiş kod tarafından oluşturulan istemciler
- Küçük mesajlar
- Sunucu akışı

## <a name="grpc-implementation"></a>gRPC uygulama

Microsoft 'un [kapsayıcılarındaki](https://github.com/dotnet-architecture/eShopOnContainers)mikro hizmet başvuru mimarisi, .NET Core uygulamalarında GRPC hizmetlerinin nasıl uygulanacağını gösterir. Şekil 4-22 arka uç mimarisini gösterir.

![Kapsayıcılarda eShop için arka uç mimarisi](./media/eshop-with-aggregators.png)

**Şekil 4-22**. Kapsayıcılarda eShop için arka uç mimarisi

Önceki şekilde, birden çok API ağ geçidini açığa çıkararak eShop 'nin ön uç (BFF) [Için arka](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) ucunu nasıl atdığını aklınızda bir yere aklınızda Bu bölümün önceki kısımlarında BFF modelini tartıştık. Web-alışveriş API ağ geçidi ve arka uç alışverişi mikro hizmetleri arasında yer alan toplayıcı mikro hizmetine (gri) yakın bir ilgi ödeyin. Toplayıcı bir istemciden tek bir istek alır, bunu çeşitli mikro hizmetlere dağıtır, sonuçları toplar ve bunları istek istemcisine geri gönderir. Bu işlemler genellikle anında yanıt üretmek için zaman uyumlu iletişim gerektirir. EShop 'de, Şekil 4-23 ' de gösterildiği gibi, toplayıcıdan arka uç çağrıları gRPC kullanılarak gerçekleştirilir.

![Kapsayıcılar üzerinde eShop içinde gRPC](./media/grpc-implementation.png)

**Şekil 4-23**. Kapsayıcılar üzerinde eShop içinde gRPC

gRPC iletişimi hem istemci hem de sunucu bileşenleri gerektirir. Önceki şekilde, alışveriş toplayıcısı 'nın gRPC istemcisini nasıl uyguladığı hakkında daha fazla. İstemci, her biri gRPC sunucusunu uygulayan, arka uç mikro hizmetleri için zaman uyumlu gRPC çağrıları (kırmızı) yapar. Hem istemci hem de sunucu, .NET Core SDK yerleşik gRPC tesisat özelliğinden faydalanır. İstemci tarafı *saplamaları* , uzak GRPC çağrılarını çağırma için bir sıhhi tesisat sağlar. Sunucu tarafı bileşenleri, özel hizmet sınıflarının devralması ve tükettiği gRPC sıhhi tesisat sağlar.

Hem yeniden takip eden bir API 'yi hem de gRPC iletişimini sunan mikro hizmetler, trafiği yönetmek için birden çok uç nokta gerektirir. Yeniden yapılan çağrılar için HTTP trafiğini dinleyen bir uç nokta ve farklı gRPC çağrıları için bir tane açarsınız. GRPC uç noktasının, gRPC iletişimi için gerekli olan HTTP/2 Protokolü için yapılandırılması gerekir.

Bağımsız olarak, mikro hizmetleri zaman uyumsuz iletişim desenleriyle ayırarak, bazı işlemler doğrudan çağrı gerektirir. gRPC, mikro hizmetler arasında doğrudan zaman uyumlu iletişim için birincil seçim olmalıdır. HTTP/2 ve protokol arabelleklerine bağlı olarak yüksek performanslı iletişim protokolü, bunu kusursuz bir seçim yapın.

## <a name="looking-ahead"></a>Öne bakıyor

İleriye bakarak, gRPC, bulutta yerel sistemler için bir işlem yapmaya devam edecektir. Performans avantajları ve geliştirme kolaylığı etkileyici. Ancak REST büyük olasılıkla uzun bir süre içinde olabilir. Bu, genel kullanıma açık API 'Ler ve geriye dönük uyumluluk nedenleriyle daha fazla.

>[!div class="step-by-step"]
>[Önceki](service-to-service-communication.md)
>[İleri](service-mesh-communication-infrastructure.md)
