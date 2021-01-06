---
title: WCF geliştiricileri için şifreleme ve ağ güvenliği-gRPC
description: GRPC 'de ağ güvenliğine ve şifrelemeye ilişkin bazı notlar
ms.date: 12/15/2020
ms.openlocfilehash: 0735158ed69ce425c4f00eed6c42689b888a1885
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938630"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="2aeae-103">Şifreleme ve ağ güvenliği</span><span class="sxs-lookup"><span data-stu-id="2aeae-103">Encryption and network security</span></span>

<span data-ttu-id="2aeae-104">Windows Communication Foundation (WCF) için ağ güvenlik modeli kapsamlı ve karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="2aeae-104">The network security model for Windows Communication Foundation (WCF) is extensive and complex.</span></span> <span data-ttu-id="2aeae-105">Tek tek iletileri şifrelemek için WS-Security belirtimini kullanarak HTTPS veya TLS üzerinden TCP ve ileti düzeyi güvenlik kullanarak aktarım düzeyi güvenliği içerir.</span><span class="sxs-lookup"><span data-stu-id="2aeae-105">It includes transport-level security by using HTTPS or TLS-over-TCP, and message-level security by using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="2aeae-106">gRPC, TLS sertifikalarını kullanarak güvenli hale getirerek, temel alınan HTTP/2 protokolüne güvenli ağ bırakır.</span><span class="sxs-lookup"><span data-stu-id="2aeae-106">gRPC leaves secure networking to the underlying HTTP/2 protocol, which you can secure by using TLS certificates.</span></span>

<span data-ttu-id="2aeae-107">Web tarayıcıları, HTTP/2 için TLS bağlantılarını, ancak dahil olmak üzere çoğu programlı istemciyi insist. NET `HttpClient` , şifrelenmemiş bağlantılar ÜZERINDEN http/2 kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2aeae-107">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="2aeae-108">`HttpClient` Varsayılan olarak şifreleme gerektirir, ancak bir anahtar kullanarak bu davranışı geçersiz kılabilirsiniz <xref:System.AppContext> .</span><span class="sxs-lookup"><span data-stu-id="2aeae-108">`HttpClient` does require encryption by default, but you can override this behavior by using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="2aeae-109">Ortak API 'Ler için, her zaman TLS bağlantıları kullanmalı ve uygun bir SSL yetkilisinden hizmetleriniz için geçerli sertifikalar sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2aeae-109">For public APIs, you should always use TLS connections, and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="2aeae-110">[Letsencrypt](https://letsencrypt.org) , ücretsiz, otomatik SSL sertifikaları sağlar ve çoğu barındırma altyapısı, ortak eklentiler veya uzantılar ile letecrypt standardını destekler.</span><span class="sxs-lookup"><span data-stu-id="2aeae-110">[LetsEncrypt](https://letsencrypt.org) provides free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="2aeae-111">Kurumsal ağ genelindeki iç hizmetler için, gRPC hizmetlerinize gelen ve giden ağ trafiğinin güvenliğini sağlamak için TLS kullanmayı göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2aeae-111">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="2aeae-112">Kubernetes 'te çalışan hizmetler arasında açık TLS kullanmanız gerekiyorsa, küme içi bir sertifika yetkilisi ve [CERT Manager](https://docs.cert-manager.io/en/latest/)gibi bir sertifika yöneticisi denetleyicisi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="2aeae-112">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster certificate authority and a certificate manager controller like [cert-manager](https://docs.cert-manager.io/en/latest/).</span></span> <span data-ttu-id="2aeae-113">Daha sonra, dağıtım zamanında hizmetlere otomatik olarak sertifika atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aeae-113">You can then automatically assign certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2aeae-114">[Önceki](channel-credentials.md) 
> [Sonraki](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="2aeae-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
