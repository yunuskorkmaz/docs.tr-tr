---
title: WCF geliştiricileri için GRPC neden önerilir
description: GRPC 'nin neden modern mimarilere ve platformlara geçiş yapmak isteyen WCF geliştiricileri için iyi bir uyum olduğuna ilişkin bir tartışma.
ms.date: 09/02/2019
ms.openlocfilehash: da712e1ceee92f0a1a2661252dcda602f5dde9a0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966942"
---
# <a name="why-grpc-is-recommended-for-wcf-developers"></a>WCF geliştiricilerine neden gRPC önerilir?

GRPC 'nin diline ve tekniklerine ek olarak, gRPC 'nin .NET Core 'a geçiş yapmak isteyen WCF geliştiricilerine yönelik doğru çözüm olmasının yanı sıra, kullanılabilir alternatifler vardır.

## <a name="similarity-to-wcf"></a>WCF benzerliği

Uygulama ve yaklaşım farklı olsa da, gRPC ile hizmetleri geliştirme ve kullanma konusunda gerçek deneyim, WCF geliştiricileri için çok sezgisel olmalıdır. İstemci ve sunucu aynı platformda olsa da, ağ iletişimi konusunda endişelenmenize gerek kalmadan, kodunuzun temel amacı aynı. Her iki platform da, bu arabirimi bildirme işlemi farklı olsa da, bir arabirimi oluşturma ve uygulama ilkesini paylaşır. Ayrıca, Bölüm 5 ' te gösterildiği gibi, gRPC eşlemesi tarafından desteklenen farklı RPC çağrısı türleri, WCF Hizmetleri için kullanılabilen farklı bağlamalara çok uygundur.

## <a name="benefits-of-grpc"></a>GRPC 'nin avantajları

Aşağıda, gRPC 'nin diğer çözümlerin üzerinde neden olduğu ek nedenler:

### <a name="performance"></a>Performans

Daha önce anlatıldığı gibi http/1.1 yerine HTTP/2 kullanılması, insan tarafından okunabilen iletiler gereksinimini ortadan kaldırır ve bunun yerine daha hızlı bir ikili protokolü kullanır. Bu, bilgisayarların ayrıştırılmasında daha etkilidir. HTTP/2 Ayrıca, bir kuyrukta beklenmeden (HTTP/1.1 'de "satır başı (HOL) engelleme" olarak bilinen bir sorun olması gerekmeden), yanıtları tek bir bağlantı üzerinden aynı anda göndermek için de destekler. GRPC kullanılırken daha az kaynak olması gerekir ve bu, mobil cihazlarda ve yavaş ağlarda kullanılması iyi bir çözüm haline gelir.

### <a name="interoperability"></a>Birlikte çalışabilirlik

.NET, Java, Python, Go, C++, Node. js, Swift, Dart, Ruby ve php dahil tüm büyük programlama dilleri ve platformları Için GRPC araçları ve kitaplıkları vardır. Her platform için protokol arabelleklerinin ikili kablo biçimi ve verimli kod üretimi sayesinde, geliştiriciler, tam platformlar arası destekten hala keyif alırken performanslı uygulamalar oluşturabilir.

### <a name="usability-and-productivity"></a>Kullanılabilirlik ve üretkenlik

gRPC, kapsamlı bir RPC çözümüdür. Düzenli olarak birden çok dilde ve platformda çalışır ve gerekli ortak kod kodu otomatik olarak üretilmeden harika araçlar sağlar, böylece iş mantığına odaklanmak için daha fazla geliştirici saati serbest bırakılır.

### <a name="streaming"></a>Akış

gRPC 'de, WCF 'nin tam çift yönlü hizmetlerine çok benzer işlevler sağlayan tam çift yönlü akış vardır. gRPC akışı, normal internet bağlantıları, yük dengeleyiciler ve hizmet kafesleri üzerinden çalışabilir.

### <a name="deadlinetimeouts-and-cancellation"></a>Son tarih/zaman aşımları ve iptal

gRPC, istemcilerin bir RPC 'nin tamamlaması için en uzun süreyi belirtmesini sağlar. Belirtilen son tarih aşılırsa sunucu, işlemi istemciden bağımsız olarak iptal edebilir. Son tarihler ve iptaller, kaynak kullanım sınırlarını zorlamaya yardımcı olmak için ek gRPC çağrıları aracılığıyla yayılamaz. İstemciler, son tarih aşıldığında veya daha önce (örn. Kullanıcı etkileşimi nedeniyle) işlemleri iptal edebilir.

### <a name="security"></a>Güvenlik

bir TLS uçtan uca şifreli bağlantı üzerinden HTTP/2 kullanılırken gRPC, örtülü olarak güvenlidir. Istemci sertifikası kimlik doğrulaması desteği (bkz. Bölüm 6) istemci ve sunucu arasındaki güvenliği ve güveni daha da artırır.

>[!div class="step-by-step"]
>[Önceki](network-protocols.md)
>[İleri](protocol-buffers.md)
