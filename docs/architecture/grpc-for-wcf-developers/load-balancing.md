---
title: WCF geliştiricileri için Yük Dengeleme gRPC-gRPC
description: GRPC hizmetleriyle çalışmak için bir yük dengeleyici seçme.
ms.date: 09/02/2019
ms.openlocfilehash: 215c0983146bbf9168f01956d64733f80cea6faf
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711171"
---
# <a name="load-balancing-grpc"></a><span data-ttu-id="ac5df-103">GRPC yük dengelemesi</span><span class="sxs-lookup"><span data-stu-id="ac5df-103">Load balancing gRPC</span></span>

<span data-ttu-id="ac5df-104">Bir gRPC uygulamasının tipik bir dağıtımı, hizmetin bir dizi özdeş örneğini içerir, bu da esnekliği ve yatay ölçeklenebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac5df-104">A typical deployment of a gRPC application includes a number of identical instances of the service, providing resilience and horizontal scalability.</span></span> <span data-ttu-id="ac5df-105">Yük Dengeleme, tüm kullanılabilir kaynakların tam kullanımını sağlamak için gelen istekleri bu örneklerde dağıtır.</span><span class="sxs-lookup"><span data-stu-id="ac5df-105">Load balancing distributes incoming requests across these instances to provide full usage of all available resources.</span></span> <span data-ttu-id="ac5df-106">Bu yük dengelemeyi istemcide görünmez hale getirmek için, istemcilerden gelen istekleri işlemek ve arka uç örneklerine yönlendirmek için bir proxy yük dengeleyici sunucusu kullanılması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="ac5df-106">To make this load balancing invisible to the client, it's common to use a proxy load balancer server to handle requests from clients and route them to back-end instances.</span></span>

<span data-ttu-id="ac5df-107">Yük dengeleyiciler üzerinde çalıştıkları *katmana* göre sınıflandırılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac5df-107">Load balancers are classified according to the *layer* they operate on.</span></span> <span data-ttu-id="ac5df-108">Katman 4 yük dengeleyiciler *Aktarım* düzeyinde (ÖRNEĞIN, TCP yuvaları, bağlantılar ve paketlerle) çalışır.</span><span class="sxs-lookup"><span data-stu-id="ac5df-108">Layer 4 load balancers work on the *transport* level, for example, with TCP sockets, connections, and packets.</span></span> <span data-ttu-id="ac5df-109">Katman 7 yük dengeleyiciler, özel olarak gRPC uygulamaları için HTTP/2 isteklerini işleyerek *uygulama* düzeyinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="ac5df-109">Layer 7 load balancers work at the *application* level, specifically handling HTTP/2 requests for gRPC applications.</span></span>

## <a name="l4-load-balancers"></a><span data-ttu-id="ac5df-110">L4 yük dengeleyiciler</span><span class="sxs-lookup"><span data-stu-id="ac5df-110">L4 load balancers</span></span>

<span data-ttu-id="ac5df-111">Bir L4 yük dengeleyici bir istemciden gelen TCP bağlantı isteğini kabul eder, arka uç örneklerinden birine başka bir bağlantı açar ve gerçek bir işleme olmadan iki bağlantı arasında verileri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="ac5df-111">An L4 load balancer accepts a TCP connection request from a client, opens another connection to one of the back-end instances, and copies data between the two connections with no real processing.</span></span> <span data-ttu-id="ac5df-112">L4 mükemmel performans ve düşük gecikme süresi, ancak çok az denetim veya zeka sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac5df-112">L4 offers excellent performance and low latency, but very little control or intelligence.</span></span> <span data-ttu-id="ac5df-113">İstemci bağlantıyı açık sakladığı sürece tüm istekler aynı arka uç örneğine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ac5df-113">As long as the client keeps the connection open, all requests will be directed to the same back-end instance.</span></span>

 <span data-ttu-id="ac5df-114">[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) , bir L4 yük dengeleyiciye bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="ac5df-114">[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) is an example of an L4 load balancer.</span></span>

## <a name="l7-load-balancers"></a><span data-ttu-id="ac5df-115">L7 yük dengeleyiciler</span><span class="sxs-lookup"><span data-stu-id="ac5df-115">L7 load balancers</span></span>

<span data-ttu-id="ac5df-116">Bir L7 yük dengeleyici gelen HTTP/2 isteklerini ayrıştırır ve bağlantının istemci tarafından ne kadar süreceğine bakılmaksızın bunları istek temelli olarak bir istek temelinde, arka uç örneklerine geçirir.</span><span class="sxs-lookup"><span data-stu-id="ac5df-116">An L7 load balancer parses incoming HTTP/2 requests and passes them on to back-end instances on a request-by-request basis, no matter how long the connection is held by the client.</span></span>

<span data-ttu-id="ac5df-117">L7 yük dengeleyiciler örnekleri:</span><span class="sxs-lookup"><span data-stu-id="ac5df-117">Examples of L7 load balancers:</span></span>

- [<span data-ttu-id="ac5df-118">NGıNX</span><span class="sxs-lookup"><span data-stu-id="ac5df-118">NGINX</span></span>](https://www.nginx.com/)
- [<span data-ttu-id="ac5df-119">HAProxy</span><span class="sxs-lookup"><span data-stu-id="ac5df-119">HAProxy</span></span>](https://www.haproxy.com/)
- [<span data-ttu-id="ac5df-120">Traefik</span><span class="sxs-lookup"><span data-stu-id="ac5df-120">Traefik</span></span>](https://traefik.io/)

<span data-ttu-id="ac5df-121">Bir Thumb kuralı olarak, L7 yük dengeleyiciler gRPC ve diğer HTTP/2 uygulamaları için en iyi seçenektir (ve genellikle HTTP uygulamaları için).</span><span class="sxs-lookup"><span data-stu-id="ac5df-121">As a rule of thumb, L7 load balancers are the best choice for gRPC and other HTTP/2 applications (and for HTTP applications generally, in fact).</span></span> <span data-ttu-id="ac5df-122">L4 yük dengeleyiciler gRPC uygulamalarıyla *çalışır* , ancak düşük gecikme süresi ve düşük ek yük önemli olduğunda bu uygulamalar genellikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac5df-122">L4 load balancers will *work* with gRPC applications, but they're mainly useful when low latency and low overhead are important.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac5df-123">Bu yazma sırasında, bazı L7 yük dengeleyiciler, üst bilgiler gibi gRPC Hizmetleri için gerekli olan HTTP/2 belirtiminin tüm parçalarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ac5df-123">At the time of this writing, some L7 load balancers don't support all the parts of the HTTP/2 specification that are required by gRPC services, such as trailing headers.</span></span>

<span data-ttu-id="ac5df-124">TLS şifrelemesini kullanıyorsanız, yük dengeleyiciler TLS bağlantısını sonlandırabilir ve şifrelenmemiş istekleri arka uç uygulamasına geçirebilir veya şifreli isteği de geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="ac5df-124">If you're using TLS encryption, load balancers can terminate the TLS connection and pass unencrypted requests to the back-end application, or they can pass the encrypted request along.</span></span> <span data-ttu-id="ac5df-125">Her iki durumda da yük dengeleyicinin, işleme isteklerinin şifresini çözebilmesi için sunucunun ortak ve özel anahtarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac5df-125">Either way, the load balancer will need to be configured with the server's public and private key so it can decrypt requests for processing.</span></span>

<span data-ttu-id="ac5df-126">Arka uç hizmetleriniz ile HTTP/2 isteklerini işlemek üzere nasıl yapılandıracağınızı öğrenmek için tercih ettiğiniz yük dengeleyiciye yönelik belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="ac5df-126">See to the documentation for your preferred load balancer to find out how to configure it to handle HTTP/2 requests with your back-end services.</span></span>

## <a name="load-balancing-within-kubernetes"></a><span data-ttu-id="ac5df-127">Kubernetes içinde yük dengeleme</span><span class="sxs-lookup"><span data-stu-id="ac5df-127">Load balancing within Kubernetes</span></span>

<span data-ttu-id="ac5df-128">Kubernetes 'deki iç hizmetlerde yük dengelemenin tartışılması için [hizmet kafesleri bölümüne](service-mesh.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="ac5df-128">See [the section on service meshes](service-mesh.md) for a discussion of load balancing across internal services on Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ac5df-129">[Önceki](service-mesh.md)
>[İleri](application-performance-management.md)</span><span class="sxs-lookup"><span data-stu-id="ac5df-129">[Previous](service-mesh.md)
[Next](application-performance-management.md)</span></span>
