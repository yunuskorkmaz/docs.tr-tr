---
title: WCF geliştiricileri için neden gRPC öneriyoruz - WCF geliştiricileri için gRPC
description: GRPC'nin modern mimarilere ve platformlara göç etmek isteyen WCF geliştiricileri için neden uygun olduğu tartışması.
ms.date: 09/02/2019
ms.openlocfilehash: 664781e94c24c1796eafa6a70eb28d453b530d66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147652"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>WCF geliştiricileri için gRPC’yi neden öneriyoruz?

gRPC'nin dili ve tekniklerine derinlemesine dalmadan önce, gRPC'nin .NET Core'a geçiş yapmak isteyen Windows Communication Foundation (WCF) geliştiricileri için neden doğru çözüm olduğunu tartışmaya değer.

## <a name="similarity-to-wcf"></a>WCF ile benzerlik

Uygulama ve yaklaşım gRPC için farklı olsa da, gRPC ile hizmet geliştirme ve tüketme deneyimi WCF geliştiricileri için sezgisel olmalıdır. Temel amaç aynıdır: istemci ve sunucu ağ konusunda endişelenmenize gerek kalmadan, aynı platformda ymış gibi kodlamayı mümkün kılar.

Her iki platform da, arabirimi bildirme işlemi farklı olsa da, bir arabirimi bildirme ve uygulama ilkesini paylaşır. Ve bölüm 5'te göreceğiniz gibi, gRPC'nin WCF hizmetlerinin kullanabileceği ciltler için haritayı iyi desteklediği farklı RPC çağrıları.

## <a name="benefits-of-grpc"></a>gRPC'nin Faydaları

gRPC aşağıdaki nedenlerle diğer çözümlerin üzerinde direnir.

### <a name="performance"></a>Performans

HTTP/1.1 yerine HTTP/2 kullanmak, insan tarafından okunabilir iletiler gereksinimini ortadan kaldırır ve bunun yerine daha küçük, daha hızlı ikili protokolü kullanır. Bu, bilgisayarların ayrıştırması için daha etkilidir. HTTP/2 ayrıca tek bir bağlantı üzerinden çoklama isteklerini destekler. Bu destek, yanıtların kuyrukta beklemeye gerek kalmadan hazır olur olmaz gönderilmesini sağlar. (HTTP/1.1'de bu sorun "head-of-line (HOL) engelleme" olarak bilinir.) gRPC kullanırken daha az kaynağa ihtiyacınız vardır, bu da mobil cihazlar da ve daha yavaş ağlarda kullanılmasını iyi bir çözüm haline getirir.

### <a name="interoperability"></a>Birlikte çalışabilirlik

.NET, Java, Python, Go, C++, Node.js, Swift, Dart, Ruby ve PHP dahil olmak üzere tüm büyük programlama dilleri ve platformları için gRPC araçları ve kitaplıkları vardır. Protokol Arabellekleri ikili tel biçimi ve her platform için verimli kod oluşturma sayesinde, geliştiriciler tam çapraz platform desteğinin keyfini çıkarırken performansuygulamaları oluşturabilirler.

### <a name="usability-and-productivity"></a>Kullanılabilirlik ve üretkenlik

gRPC kapsamlı bir RPC çözümüdür. Birden çok dil ve platformda tutarlı bir şekilde çalışır. Ayrıca, gerekli kazanın kodunun büyük bir kısmı otomatik olarak oluşturulurken mükemmel bir takımlama sağlar. Yani daha fazla geliştirici zaman kadar iş mantığı odaklanmak için serbest bırakılır.

### <a name="streaming"></a>Akış

gRPC, WCF'nin tam çift yönlü hizmetlerine benzer işlevsellik sağlayan tam çift yönlü akışa sahiptir. gRPC akışı normal internet bağlantıları, yük dengeleyicileri ve servis meshes üzerinden çalışabilir.

### <a name="deadlinetimeouts-and-cancellation"></a>Son tarih/zaman ları ve iptal

gRPC istemciler bir RPC bitirmek için maksimum süre belirtmek için izin verir. Belirtilen son tarih aşılırsa, sunucu istemciden bağımsız olarak işlemi iptal edebilir. Son tarihler ve iptaller, kaynak kullanım sınırlarının uygulanmasına yardımcı olmak için daha fazla gRPC çağrıları aracılığıyla yayılabilir. İstemciler, son tarih aşıldığında veya gerekirse daha erken olduğunda (örneğin, kullanıcı etkileşimi nedeniyle) işlemleri durdurabilir.

### <a name="security"></a>Güvenlik

gRPC, TLS uçlardan uca şifreli bir bağlantı üzerinden HTTP/2 kullanırken örtülü olarak güvenlidir. İstemci sertifikası kimlik doğrulaması desteği [(bkz. bölüm 6)](security.md)istemci ve sunucu arasındaki güvenliği ve güveni daha da artırır.

>[!div class="step-by-step"]
>[Önceki](network-protocols.md)
>[Sonraki](protocol-buffers.md)
