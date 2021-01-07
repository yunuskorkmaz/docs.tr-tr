---
title: WCF geliştiricileri için şifreleme ve ağ güvenliği-gRPC
description: GRPC 'de ağ güvenliğine ve şifrelemeye ilişkin bazı notlar
ms.date: 01/06/2021
ms.openlocfilehash: cf4d30ff862e64aadfeacf45ed3768fc14737800
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970147"
---
# <a name="encryption-and-network-security"></a>Şifreleme ve ağ güvenliği

Windows Communication Foundation (WCF) için ağ güvenlik modeli kapsamlı ve karmaşıktır. Tek tek iletileri şifrelemek için WS-Security belirtimini kullanarak HTTPS veya TLS üzerinden TCP ve ileti düzeyi güvenlik kullanarak aktarım düzeyi güvenliği içerir.

gRPC, TLS sertifikalarını kullanarak güvenli hale getirerek, temel alınan HTTP/2 protokolüne güvenli ağ bırakır.

Web tarayıcıları, HTTP/2 için TLS bağlantılarını, ancak dahil olmak üzere çoğu programlı istemciyi insist. NET `HttpClient` , şifrelenmemiş bağlantılar ÜZERINDEN http/2 kullanabilir.

Ortak API 'Ler için, her zaman TLS bağlantıları kullanmalı ve uygun bir SSL yetkilisinden hizmetleriniz için geçerli sertifikalar sağlamalısınız. [Letsencrypt](https://letsencrypt.org) , ücretsiz, otomatik SSL sertifikaları sağlar ve çoğu barındırma altyapısı, ortak eklentiler veya uzantılar ile letecrypt standardını destekler.

Kurumsal ağ genelindeki iç hizmetler için, gRPC hizmetlerinize gelen ve giden ağ trafiğinin güvenliğini sağlamak için TLS kullanmayı göz önünde bulundurmanız gerekir.

Kubernetes 'te çalışan hizmetler arasında açık TLS kullanmanız gerekiyorsa, küme içi bir sertifika yetkilisi ve [CERT Manager](https://docs.cert-manager.io/en/latest/)gibi bir sertifika yöneticisi denetleyicisi kullanmayı düşünün. Daha sonra, dağıtım zamanında hizmetlere otomatik olarak sertifika atayabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](channel-credentials.md) 
> [Sonraki](grpc-in-production.md)
