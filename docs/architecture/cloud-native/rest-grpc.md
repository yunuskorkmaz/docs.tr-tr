---
title: REST ve gRPC
description: Bkz. The The The The The The The The the Cloud-Native Applications ve HTTP REST 'den farklı
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: f5725106b251a7e62ef74ea36a63c663e5db36de
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781060"
---
# <a name="rest-and-grpc"></a>REST ve gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Şimdiye kadar bu kitapta, [REST tabanlı](https://docs.microsoft.com/azure/architecture/best-practices/api-design) iletişime odaklandık. REST, dağıtılmış bilgisayar sistemleri arasında birlikte çalışabilirliği tanıtan bir mimari stillidir. Sunucudan gelen her yanıtın istemciden bir istek olduğu bir istek/yanıt modeli kullanır. Yaygın olarak popüler olsa da, REST her sorun için mükemmel bir uyum değildir. GRPC 'ye yönelik daha yeni bir iletişim teknolojisi, çok popülerlik elde etmek ve bulut Yerel dünyasına kendi şeklini yapıyor.

## <a name="grpc"></a>gRPC

gRPC, Google 'dan kaynaklanan açık kaynaklı bir iletişimdir. Dağıtılmış bilgi işlem bölümünde popüler olan, [uzak yordam çağrısı (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) modeli üzerine kurulmuştur. Bu modelin ardından, yerel bir istemci programı bir işlemi yürütmek için işlem içi bir yöntem sunar. Arka planda, bu çağrı dağıtılmış bir ağ üzerinden işlem dışı bir mikro hizmette çağrılır. Geliştirici işlemi bir yerel yordam çağrısı olarak kodlar. Temel alınan Platform, noktadan noktaya ağ iletişimini, Serileştirmeyi ve yürütmeyi soyutlar.

gRPC, hafif ve yüksek performanslı bir modern RPC çerçevesidir. Aktarım Protokolü için HTTP/2 kullanır. HTTP 1,1 ile uyumlu olmakla birlikte, HTTP/2 özellikleri birçok gelişmiş özelliğe sahiptir:

- HTTP 1,1, verileri şifresiz metin olarak gönderirken HTTP/2 bir ikili protokoldür. Daha az bellek kullanarak verileri daha hızlı ayrıştırır, hız için ilgili iyileştirmelerle ağ gecikmesini azaltır ve ağ kaynaklarını daha verimli bir şekilde yönetir.
- HTTP 1,1 tek seferde bir gidiş dönüş isteği/yanıtı işlemeyle sınırlı olsa da, HTTP/2 aynı bağlantı üzerinden çoğullama veya birden çok paralel isteği destekler.
- HTTP/2 tam çift yönlü veya çift yönlü iletişimi destekler, burada hem istemci hem de sunucu aynı anda iletişim kurabilir. İstemci, istek verilerini sunucu tarafından yanıt verileri gönderilirken aynı anda karşıya yükleyebilir.
- Akış, HTTP/2 ' de yerleşik olarak bulunur ve isteklerin ve yanıtların zaman uyumsuz olarak büyük veri kümeleri akışını sağlayabilir.
- GRPC ve HTTP/2 birleştirme performansı önemli ölçüde artar. [Windows Communication Foundation (WCF)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) Pari 'de, GRPC performansı, [NetTcp bağlamalarının](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8)hızını ve verimliliğini karşılar ve bunları aşar. Ancak, NetTCP 'nin aksine gRPC, C# veya Visual Basic gibi Microsoft dilleri ile sınırlı değildir.

gRPC, Java, C#, golang ve NodeJS dahil olmak üzere en popüler platformlar arasında desteklenir.

## <a name="protocol-buffers"></a>Protokol Arabellekleri

gRPC, veri göndermek ve almak için [protokol arabellekleri](https://developers.google.com/protocol-buffers/docs/overview) veya prototip iletiler adlı başka bir açık kaynaklı teknolojinin ayraçlarını alır. [WCF veri sözleşmesine](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-data-contracts)benzer şekilde, prototipleme sistemler için yapılandırılmış verileri okuma ve yazma olarak serileştirir. XML veya JSON gibi insan tarafından okunabilen biçimlerin yükünü azaltır.

Birçok nesne serileştirme tekniği, çalışma zamanında veri nesnelerinin yapısı genelinde yansıtır. Protobellek, yapıyı platformdan bağımsız bir dil (protokol arabellek dili) ile tanımlamanızı gerektirir. Her tanım bir ". proto" dosyasında depolanır. Daha sonra prototip derleyicisi, "proton" kullanımı, desteklenen platformlardan herhangi biri için istemci ve sunucu kodu oluşturur. Oluşturulan kod, verilerin hızlı seri hale getirilmesi/serileştirilmesi için iyileştirilmiştir. Çalışma zamanında, her ileti kesin türü belirtilmiş hizmet sözleşmesine sarmalanır ve standart bir prototipleme gösteriminde serileştirilir.

## <a name="grpc-support-in-net"></a>.NET ' te gRPC desteği

Microsoft .NET Core Framework 3,0, gRPC için araç ve yerel destek içerir. Şekil 4-20, GRPC iskelet projesini bir gRPC hizmeti için dolandırıcılara bağlayan Visual Studio 2019 şablonunu gösterir. .NET Core 'un Windows, Linux ve macOS platformlarını nasıl desteklediğine göz önünde.

![Visual Studio 2019 ' de gRPC desteği](./media/visual-studio-2019-grpc-template.png)

**Şekil 4-20**. Visual Studio 2019 ' de gRPC desteği

.NET Core 3,0, gRPC 'yi, uç nokta yönlendirme, yerleşik IOC desteği ve günlüğe kaydetme dahil olmak üzere kendi çerçevesiyle sorunsuzca tümleştirir. Açık kaynaklı Kestrel Web sunucusu HTTP/2 bağlantılarını tam olarak destekler.

Şekil 4-21, Visual Studio 2019 ' de bir gRPC hizmetinin yapısını gösterir. Klasör yapısının proto dosyaları ve hizmet kodu için klasörleri nasıl içerdiğini göz önünde bulundurur.

![Visual Studio 2019 ' de gRPC projesi](./media/grpc-project.png  )

**Şekil 4-21**. Visual Studio 2019 ' de gRPC projesi

## <a name="grpc-usage"></a>gRPC kullanımı

gRPC aşağıdaki senaryolar için uygundur:

- Düşük gecikme süresi ve yüksek aktarım hızı iletişimi. gRPC, verimlilik açısından kritik olan hafif mikro hizmetler için harika.
- Noktadan noktaya gerçek zamanlı iletişim. gRPC, iki yönlü akış için harika desteğe sahiptir. gRPC Hizmetleri, yoklama yapmadan iletileri gerçek zamanlı olarak gönderebilir.
- Çok yönlü ortamları – gRPC araçları, en popüler geliştirme dillerini destekler ve çok dilli ortamlar için iyi bir seçenek yapar.
- Ağ kısıtlamalı ortamlar – gRPC iletileri, hafif bir ileti biçimi olan Protoarabellek ile serileştirilir. GRPC iletisi her zaman denk bir JSON iletisinden daha küçüktür.

Bu kitabın yazıldığı sırada tarayıcıların çoğu, gRPC için sınırlı desteğe sahiptir. gRPC, HTTP/2 özelliklerini çok fazla kullanır ve tarayıcı, bir gRPC istemcisini desteklemek için Web istekleri üzerinde gerekli denetim düzeyini sağlar. gRPC, genellikle iç mikro hizmetin mikro hizmet iletişimine yönelik iletişim için kullanılır. Şekil 4-22 basit, ancak yaygın kullanım modelini gösterir.

![gRPC kullanım desenleri](./media/grpc-usage.png)

**Şekil 4-22**. gRPC kullanım desenleri

Önceki şekilde, ön uç trafiğinin HTTP ile nasıl çağrılacağını, mikro hizmet ile mikro hizmetin de gRPC 'yi kullanması durumunda göz önüne alın.

İleriye yönelik olarak, gRPC, bulutta yerel sistemler için geri kalanı önemli bir rol oynayabilir. Performans avantajları ve geliştirme kolaylığının geçmesi çok iyidir. Ancak, herhangi bir hata yapmayın, DIĞERLERI uzun bir süre içinde devam edecektir. Bu, genel kullanıma açık API 'Ler ve geriye dönük uyumluluk nedenleriyle hala daha fazla.

>[!div class="step-by-step"]
>[Önceki](service-to-service-communication.md)
>[İleri](service-mesh-communication-infrastructure.md)
