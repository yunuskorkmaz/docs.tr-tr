---
title: WCF geliştiricileri için şifreleme ve ağ güvenliği-gRPC
description: GRPC 'de ağ güvenliğine ve şifrelemeye ilişkin bazı notlar
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 8a115b59337003669b4e5436edffe239489ca79e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184465"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="2f938-103">Şifreleme ve ağ güvenliği</span><span class="sxs-lookup"><span data-stu-id="2f938-103">Encryption and network security</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="2f938-104">WCF 'nin ağ güvenlik modeli, tek tek iletileri şifrelemek için WS-Security belirtimini kullanarak HTTPS veya TLS üzerinden TLS veya ileti düzeyinde güvenlik kullanarak aktarım düzeyi güvenlik dahil olmak üzere kapsamlı ve karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="2f938-104">WCF's network security model is extensive and complex, including transport-level security using HTTPS or TLS-over-TCP, and message-level security using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="2f938-105">gRPC, normal TLS sertifikaları kullanılarak güvenliği sağlanabilen, temel alınan HTTP/2 protokolüne güvenli ağ bırakır.</span><span class="sxs-lookup"><span data-stu-id="2f938-105">gRPC leaves secure networking to the underlying HTTP/2 protocol, which can be secured using regular TLS certificates.</span></span>

<span data-ttu-id="2f938-106">Web tarayıcıları, HTTP/2 için TLS bağlantılarını, ancak dahil olmak üzere çoğu programlı istemciyi insist. `HttpClient`Net, şifrelenmemiş bağlantılar üzerinden HTTP/2 kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2f938-106">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="2f938-107">`HttpClient`Varsayılan olarak *şifreleme gerektirir,* ancak bunu <xref:System.AppContext> anahtar kullanarak geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f938-107">`HttpClient` *does* require encryption by default, but you can override this using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="2f938-108">Ortak API 'Ler için, her zaman TLS bağlantıları kullanmalı ve uygun bir SSL yetkilisinden hizmetleriniz için geçerli sertifikalar sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2f938-108">For public APIs, you should always use TLS connections and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="2f938-109">[Letsencrypt](https://letsencrypt.org) , ücretsiz, otomatik SSL sertifikaları sağlar ve çoğu barındırma altyapısı, ortak eklentiler veya uzantılar ile Letecrypt standardını destekler.</span><span class="sxs-lookup"><span data-stu-id="2f938-109">[LetsEncrypt](https://letsencrypt.org) provide free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="2f938-110">Kurumsal ağ genelindeki iç hizmetler için, gRPC hizmetlerinize gelen ve giden ağ trafiğinin güvenliğini sağlamak için TLS kullanmayı göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f938-110">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="2f938-111">Kubernetes veya Docker Sısınma gibi bir kümedeki mikro hizmetler arasındaki iletişim genel olarak kapsayıcı ağ katmanı tarafından otomatik olarak şifrelenir; bu nedenle, bu tür bir kümede özel olarak çalışan hizmetlerde TLS uygulamak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2f938-111">Communication between microservices in a cluster like Kubernetes or Docker Swarm is in general automatically encrypted by the container networking layer, so implementing TLS in services running exclusively in such a cluster isn't necessary.</span></span> <span data-ttu-id="2f938-112">Bu konu, sonraki bölümde "hizmet ağı" bölümünde daha fazla olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2f938-112">There will be more on this subject in the "Service Mesh" section of the next chapter.</span></span>

<span data-ttu-id="2f938-113">Kubernetes 'te çalışan hizmetler arasında açık TLS kullanmanız gerekiyorsa, dağıtım zamanında hizmetlere otomatik olarak sertifika atamak için bir küme içi sertifika yetkilisi ve [CERT](https://docs.cert-manager.io/en/latest/) Manager gibi bir sertifika yöneticisi denetleyicisi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="2f938-113">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster Certificate Authority and a Certificate Manager Controller like [cert-manager](https://docs.cert-manager.io/en/latest/) to assign automatically certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2f938-114">[Önceki](channel-credentials.md)
>[İleri](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="2f938-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
