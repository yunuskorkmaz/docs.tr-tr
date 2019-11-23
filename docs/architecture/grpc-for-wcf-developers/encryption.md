---
title: WCF geliştiricileri için şifreleme ve ağ güvenliği-gRPC
description: GRPC 'de ağ güvenliğine ve şifrelemeye ilişkin bazı notlar
ms.date: 09/02/2019
ms.openlocfilehash: fd993a2d75e97011c6c92cee02c24c5358a211ad
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967773"
---
# <a name="encryption-and-network-security"></a>Şifreleme ve ağ güvenliği

WCF 'nin ağ güvenlik modeli, tek tek iletileri şifrelemek için WS-Security belirtimini kullanarak HTTPS veya TLS üzerinden TLS veya ileti düzeyinde güvenlik kullanarak aktarım düzeyi güvenlik dahil olmak üzere kapsamlı ve karmaşıktır.

gRPC, normal TLS sertifikaları kullanılarak güvenliği sağlanabilen, temel alınan HTTP/2 protokolüne güvenli ağ bırakır.

Web tarayıcıları, HTTP/2 için TLS bağlantılarını, ancak dahil olmak üzere çoğu programlı istemciyi insist. NET `HttpClient`, şifrelenmemiş bağlantılar üzerinden HTTP/2 kullanabilir. `HttpClient` *varsayılan* olarak şifreleme gerektirir, ancak bunu bir <xref:System.AppContext> anahtarı kullanarak geçersiz kılabilirsiniz.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Ortak API 'Ler için, her zaman TLS bağlantıları kullanmalı ve uygun bir SSL yetkilisinden hizmetleriniz için geçerli sertifikalar sağlamalısınız. [Letsencrypt](https://letsencrypt.org) , ücretsiz, otomatik SSL sertifikaları sağlar ve çoğu barındırma altyapısı, ortak eklentiler veya uzantılar ile Letecrypt standardını destekler.

Kurumsal ağ genelindeki iç hizmetler için, gRPC hizmetlerinize gelen ve giden ağ trafiğinin güvenliğini sağlamak için TLS kullanmayı göz önünde bulundurmanız gerekir.

Kubernetes veya Docker Sısınma gibi bir kümedeki mikro hizmetler arasındaki iletişim genel olarak kapsayıcı ağ katmanı tarafından otomatik olarak şifrelenir; bu nedenle, bu tür bir kümede özel olarak çalışan hizmetlerde TLS uygulamak gerekli değildir. Bu konu, sonraki bölümde "hizmet ağı" bölümünde daha fazla olacaktır.

Kubernetes 'te çalışan hizmetler arasında açık TLS kullanmanız gerekiyorsa, dağıtım zamanında hizmetlere otomatik olarak sertifika atamak için bir küme içi sertifika yetkilisi ve [CERT](https://docs.cert-manager.io/en/latest/) Manager gibi bir sertifika yöneticisi denetleyicisi kullanmayı düşünün.

>[!div class="step-by-step"]
>[Önceki](channel-credentials.md)
>[İleri](grpc-in-production.md)
