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
# <a name="encryption-and-network-security"></a><span data-ttu-id="23abc-103">Şifreleme ve ağ güvenliği</span><span class="sxs-lookup"><span data-stu-id="23abc-103">Encryption and network security</span></span>

<span data-ttu-id="23abc-104">Windows Communication Foundation (WCF) için ağ güvenlik modeli kapsamlı ve karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="23abc-104">The network security model for Windows Communication Foundation (WCF) is extensive and complex.</span></span> <span data-ttu-id="23abc-105">Tek tek iletileri şifrelemek için WS-Security belirtimini kullanarak HTTPS veya TLS üzerinden TCP ve ileti düzeyinde güvenlik kullanarak aktarım düzeyi güvenliği içerir.</span><span class="sxs-lookup"><span data-stu-id="23abc-105">It includes transport-level security by using HTTPS or TLS-over-TCP, and message-level security by using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="23abc-106">gRPC, TLS sertifikalarını kullanarak güvenli hale getirerek, temel alınan HTTP/2 protokolüne güvenli ağ bırakır.</span><span class="sxs-lookup"><span data-stu-id="23abc-106">gRPC leaves secure networking to the underlying HTTP/2 protocol, which you can secure by using TLS certificates.</span></span>

<span data-ttu-id="23abc-107">Web tarayıcıları, HTTP/2 için TLS bağlantılarını, ancak dahil olmak üzere çoğu programlı istemciyi insist. NET `HttpClient`, şifrelenmemiş bağlantılar üzerinden HTTP/2 kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="23abc-107">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="23abc-108">`HttpClient` varsayılan olarak şifreleme gerektirir, ancak bunu bir <xref:System.AppContext> anahtarı kullanarak geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23abc-108">`HttpClient` does require encryption by default, but you can override this by using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="23abc-109">Ortak API 'Ler için, her zaman TLS bağlantıları kullanmalı ve uygun bir SSL yetkilisinden hizmetleriniz için geçerli sertifikalar sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="23abc-109">For public APIs, you should always use TLS connections, and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="23abc-110">[Letsencrypt](https://letsencrypt.org) , ücretsiz, otomatik SSL sertifikaları sağlar ve çoğu barındırma altyapısı, ortak eklentiler veya uzantılar ile letecrypt standardını destekler.</span><span class="sxs-lookup"><span data-stu-id="23abc-110">[LetsEncrypt](https://letsencrypt.org) provides free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="23abc-111">Kurumsal ağ genelindeki iç hizmetler için, gRPC hizmetlerinize gelen ve giden ağ trafiğinin güvenliğini sağlamak için TLS kullanmayı göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="23abc-111">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="23abc-112">Kubernetes 'te çalışan hizmetler arasında açık TLS kullanmanız gerekiyorsa, küme içi bir sertifika yetkilisi ve [CERT Manager](https://docs.cert-manager.io/en/latest/)gibi bir sertifika yöneticisi denetleyicisi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="23abc-112">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster certificate authority and a certificate manager controller like [cert-manager](https://docs.cert-manager.io/en/latest/).</span></span> <span data-ttu-id="23abc-113">Daha sonra, dağıtım zamanında hizmetlere otomatik olarak sertifika atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23abc-113">You can then automatically assign certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="23abc-114">[Önceki](channel-credentials.md)
>[İleri](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="23abc-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
