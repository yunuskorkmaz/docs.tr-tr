---
title: Ağ protokolleri-WCF geliştiricileri için gRPC
description: GRPC ağ protokollerine genel bakış.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: cf99b2608d576765856c992679b93b6f21e796cf
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846391"
---
# <a name="network-protocols"></a>Ağ protokolleri

WCF 'den farklı olarak, gRPC, ağı için bir taban olarak HTTP/2 kullanır. Bu, WCF ve SOAP üzerinde yalnızca HTTP/1.1 üzerinde çalışan önemli avantajlar sağlar. GRPC 'yi kullanmak isteyen geliştiriciler için, HTTP/2 için başka bir seçenek olmadığından, HTTP/2 ' yi daha ayrıntılı bir şekilde incelemek ve gRPC 'yi kullanmaya yönelik ek avantajları belirlemek için ideal bir süre görünür.

2015 ' de Internet Mühendisliği görev gücü tarafından yayınlanan HTTP/2, zaten Google tarafından kullanılmakta olan deneysel SPDY protokolünden türetilmiştir. Özellikle HTTP/1.1 'den daha verimli, daha hızlı ve daha güvenli olacak şekilde tasarlanmıştır.

## <a name="key-features-of-http2"></a>HTTP/2 ' nin önemli özellikleri

Aşağıdaki listede HTTP/2 ' nin bazı temel özellikleri ve avantajları gösterilmektedir:

### <a name="binary-protocol"></a>İkili protokol

İstek/yanıt döngülerinde artık metin komutlarına gerek yok. Bu, komutların uygulanmasını basitleştirir ve hızlandırır. Özellikle, verileri ayrıştırmak daha hızlıdır ve daha az bellek kullanır, ağ gecikmesi, hızsız ilgili açık geliştirmeler ve ağ kaynaklarının genel olarak daha iyi kullanıldığı bir şekilde azaltılır.

### <a name="streams"></a>Akışlar

Akışlar, birden fazla ileti veya çerçevenin zaman uyumsuz olarak gönderilebileceği gönderici ve alıcı arasında uzun süreli bağlantılar oluşturulmasına izin verir. Birden çok akış, tek bir HTTP/2 bağlantısı üzerinden bağımsız olarak çalışabilir.

### <a name="request-multiplexing-over-a-single-tcp-connection"></a>Tek bir TCP bağlantısı üzerinden çoğullama isteme

Bu özellik HTTP/2 ' nin en önemli yeniliklerinden biridir. Veriler için birden çok paralel isteğe izin vererek, Web dosyalarını aynı anda tek bir sunucudan indirmek mümkündür. Web siteleri daha hızlı yüklenir ve iyileştirme gereksinimi azaltılır. Daha önceki bir istek tamamlanana kadar, izin verilen yanıtların gönderilmesi bekleneceği, satır başı (HOL) engelleme, daha önce de azaltılmalıdır (ancak, HOL engelleme yine de TCP Aktarım düzeyinde gerçekleşecektir).

### <a name="nettcp-like-performance-cross-platform"></a>NetTCP benzeri performans, platformlar arası

Temel olarak, gRPC ve HTTP/2 ' nin birleşimi, geliştiricilerin WCF için NetTCP bağlamalarının en az hızını ve verimliliğini ve bazı durumlarda daha da hızlı ve verimlilik sağlar. Ancak NetTCP 'nin aksine, HTTP/2 üzerinden gRPC, .NET uygulamalarıyla sınırlı değildir.

>[!div class="step-by-step"]
>[Önceki](interface-definition-language.md)
>[İleri](why-grpc.md)
