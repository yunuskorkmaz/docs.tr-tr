---
title: WCF geliştiricileri için şifreleme ve ağ güvenliği-gRPC
description: GRPC 'de ağ güvenliğine ve şifrelemeye ilişkin bazı notlar
ms.date: 09/02/2019
ms.openlocfilehash: f8a7aeaf2a65e4ff56ac33d728e40f09a436f7a6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542786"
---
# <a name="encryption-and-network-security"></a>Şifreleme ve ağ güvenliği

Windows Communication Foundation (WCF) için ağ güvenlik modeli kapsamlı ve karmaşıktır. Tek tek iletileri şifrelemek için WS-Security belirtimini kullanarak HTTPS veya TLS üzerinden TCP ve ileti düzeyinde güvenlik kullanarak aktarım düzeyi güvenliği içerir.

gRPC, TLS sertifikalarını kullanarak güvenli hale getirerek, temel alınan HTTP/2 protokolüne güvenli ağ bırakır.

Web tarayıcıları, HTTP/2 için TLS bağlantılarını, ancak dahil olmak üzere çoğu programlı istemciyi insist. NET `HttpClient`, şifrelenmemiş bağlantılar üzerinden HTTP/2 kullanabilir. `HttpClient` varsayılan olarak şifreleme gerektirir, ancak bunu bir <xref:System.AppContext> anahtarı kullanarak geçersiz kılabilirsiniz.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Ortak API 'Ler için, her zaman TLS bağlantıları kullanmalı ve uygun bir SSL yetkilisinden hizmetleriniz için geçerli sertifikalar sağlamalısınız. [Letsencrypt](https://letsencrypt.org) , ücretsiz, otomatik SSL sertifikaları sağlar ve çoğu barındırma altyapısı, ortak eklentiler veya uzantılar ile letecrypt standardını destekler.

Kurumsal ağ genelindeki iç hizmetler için, gRPC hizmetlerinize gelen ve giden ağ trafiğinin güvenliğini sağlamak için TLS kullanmayı göz önünde bulundurmanız gerekir.

Kubernetes 'te çalışan hizmetler arasında açık TLS kullanmanız gerekiyorsa, küme içi bir sertifika yetkilisi ve [CERT Manager](https://docs.cert-manager.io/en/latest/)gibi bir sertifika yöneticisi denetleyicisi kullanmayı düşünün. Daha sonra, dağıtım zamanında hizmetlere otomatik olarak sertifika atayabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](channel-credentials.md)
>[İleri](grpc-in-production.md)
