---
title: WCF geliştiricileri için Yük Dengeleme gRPC-gRPC
description: GRPC hizmetleriyle çalışmak için bir yük dengeleyici seçme.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5d4a9be9b8f4e511a72af6b68d8a005604fd984d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184395"
---
# <a name="load-balancing-grpc"></a><span data-ttu-id="a0588-103">GRPC yük dengelemesi</span><span class="sxs-lookup"><span data-stu-id="a0588-103">Load balancing gRPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a0588-104">Bir gRPC uygulamasının tipik bir dağıtımı, hizmetin bir dizi özdeş örneğini içerir, bu da esnekliği ve yatay ölçeklenebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0588-104">A typical deployment of a gRPC application includes a number of identical instances of the service, providing resilience and horizontal scalability.</span></span> <span data-ttu-id="a0588-105">Tüm kullanılabilir kaynakların tam kullanımını sağlamak için bu örneklerde dağıtılmış gelen istek yükünü dengeleyin.</span><span class="sxs-lookup"><span data-stu-id="a0588-105">Load balancing distributed incoming requests across these instances to provide full usage of all available resources.</span></span> <span data-ttu-id="a0588-106">Bu yük dengelemeyi istemcide görünmez hale getirmek için, istemcilerden gelen istekleri işlemek ve arka uç örneklerine yönlendirmek için bir proxy yük dengeleyici sunucusu kullanılması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="a0588-106">To make this load balancing invisible to the client, it's common to use a proxy load balancer server to handle requests from clients and route them to back-end instances.</span></span>

<span data-ttu-id="a0588-107">Yük dengeleyiciler üzerinde çalıştıkları *katmana* göre sınıflandırılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0588-107">Load balancers are classified according to the *layer* they operate on.</span></span> <span data-ttu-id="a0588-108">Katman 4 yük dengeleyiciler *Aktarım* düzeyinde (ÖRNEĞIN, TCP yuvaları, bağlantılar ve paketler) çalışır.</span><span class="sxs-lookup"><span data-stu-id="a0588-108">Layer 4 load balancers work on the *transport* level, for example, with TCP sockets, connections and packets.</span></span> <span data-ttu-id="a0588-109">Katman 7 yük dengeleyiciler, özel olarak gRPC uygulamaları için HTTP/2 isteklerini işleyerek *uygulama* düzeyinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="a0588-109">Layer 7 load balancers work at the *application* level, specifically handling HTTP/2 requests for gRPC applications.</span></span>

## <a name="l4-load-balancers"></a><span data-ttu-id="a0588-110">L4 yük dengeleyiciler</span><span class="sxs-lookup"><span data-stu-id="a0588-110">L4 load balancers</span></span>

<span data-ttu-id="a0588-111">Bir L4 yük dengeleyici bir istemciden gelen TCP bağlantı isteğini kabul eder, arka uç örneklerinden birine başka bir bağlantı açar ve gerçek bir işleme olmadan iki bağlantı arasında verileri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="a0588-111">An L4 load balancer accepts a TCP connection request from a client, opens another connection to one of the back-end instances, and copies data between the two connections with no real processing.</span></span> <span data-ttu-id="a0588-112">L4 mükemmel performans ve düşük gecikme süresi, ancak çok az denetim veya zeka sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0588-112">L4 offers excellent performance and low latency, but very little control or intelligence.</span></span> <span data-ttu-id="a0588-113">İstemci bağlantıyı açık sakladığı sürece tüm istekler aynı arka uç örneğine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a0588-113">As long as the client keeps the connection open, all requests will be directed to the same back-end instance.</span></span>

<span data-ttu-id="a0588-114">Bir L4 yük dengeleyiciye bir örnek [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).</span><span class="sxs-lookup"><span data-stu-id="a0588-114">An example of an L4 load balancer is the [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).</span></span>

## <a name="l7-load-balancers"></a><span data-ttu-id="a0588-115">L7 yük dengeleyiciler</span><span class="sxs-lookup"><span data-stu-id="a0588-115">L7 load balancers</span></span>

<span data-ttu-id="a0588-116">Bir L7 yük dengeleyici gelen HTTP/2 isteklerini ayrıştırır ve bağlantının istemci tarafından ne kadar süreceğine bakılmaksızın bunları istek temelli olarak bir istek temelinde, arka uç örneklerine geçirir.</span><span class="sxs-lookup"><span data-stu-id="a0588-116">An L7 load balancer parses incoming HTTP/2 requests and passes them on to back-end instances on a request-by-request basis, no matter how long the connection is held by the client.</span></span>

<span data-ttu-id="a0588-117">L7 yük dengeleyiciler örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a0588-117">Examples of L7 load balancers include:</span></span>

- [<span data-ttu-id="a0588-118">NGINX</span><span class="sxs-lookup"><span data-stu-id="a0588-118">Nginx</span></span>](https://www.nginx.com/)
- [<span data-ttu-id="a0588-119">HAproxy</span><span class="sxs-lookup"><span data-stu-id="a0588-119">HAproxy</span></span>](https://www.haproxy.com/)
- [<span data-ttu-id="a0588-120">Traefik</span><span class="sxs-lookup"><span data-stu-id="a0588-120">Traefik</span></span>](https://traefik.io/)

<span data-ttu-id="a0588-121">Bir Thumb kuralı olarak, L7 yük dengeleyiciler gRPC ve diğer HTTP/2 uygulamaları için en iyi seçenektir (ve genellikle HTTP uygulamaları için).</span><span class="sxs-lookup"><span data-stu-id="a0588-121">As a rule of thumb, L7 load balancers are the best choice for gRPC and other HTTP/2 applications (and for HTTP applications generally, in fact).</span></span> <span data-ttu-id="a0588-122">L4 yük dengeleyiciler gRPC uygulamalarıyla *çalışır* , ancak düşük gecikme süresi ve düşük ek yük önemli öneme sahip olduğunda özellikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0588-122">L4 load balancers will *work* with gRPC applications, but are primarily useful when low latency and low overhead are of paramount importance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a0588-123">Bu yazma sırasında, tüm L7 yük dengeleyiciler, gRPC Hizmetleri için gerekli olan HTTP/2 belirtiminin, sondaki üstbilgiler gibi tüm parçalarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a0588-123">At the time of this writing, not all L7 load balancers support all parts of the HTTP/2 specification required by gRPC services, such as trailing headers.</span></span>

<span data-ttu-id="a0588-124">TLS şifrelemesini kullanırken, yük dengeleyiciler TLS bağlantısını sonlandırabilir ve şifrelenmemiş istekleri arka uç uygulamasına geçirebilir veya şifreli isteği bir daha geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="a0588-124">When using TLS encryption, load balancers can terminate the TLS connection and pass unencrypted requests to the back-end application, or pass the encrypted request along.</span></span> <span data-ttu-id="a0588-125">Her iki durumda da yük dengeleyicinin sunucunun ortak ve özel anahtarıyla yapılandırılması gerekir; böylece, işleme isteklerinin şifresini çözebilirler.</span><span class="sxs-lookup"><span data-stu-id="a0588-125">Either way, the load balancer will need to be configured with the server's public and private key, so that it can decrypt requests for processing.</span></span>

<span data-ttu-id="a0588-126">Arka uç hizmetleriniz ile HTTP/2 isteklerini işlemek üzere nasıl yapılandıracağınızı öğrenmek için tercih ettiğiniz yük dengeleyiciye yönelik belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="a0588-126">Refer to the documentation for your preferred load balancer to find out how to configure it to handle HTTP/2 requests with your back-end services.</span></span>

## <a name="load-balancing-within-kubernetes"></a><span data-ttu-id="a0588-127">Kubernetes içinde yük dengeleme</span><span class="sxs-lookup"><span data-stu-id="a0588-127">Load balancing within Kubernetes</span></span>

<span data-ttu-id="a0588-128">Kubernetes 'deki iç hizmetlerde yük dengelemenin tartışılması için [hizmet kafesleri bölümüne](service-mesh.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="a0588-128">See [the section on Service Meshes](service-mesh.md) for a discussion of load balancing across internal services on Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a0588-129">[Önceki](service-mesh.md)
>[İleri](application-performance-management.md)</span><span class="sxs-lookup"><span data-stu-id="a0588-129">[Previous](service-mesh.md)
[Next](application-performance-management.md)</span></span>
