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
# <a name="network-protocols"></a><span data-ttu-id="850e8-103">Ağ protokolleri</span><span class="sxs-lookup"><span data-stu-id="850e8-103">Network protocols</span></span>

<span data-ttu-id="850e8-104">WCF 'den farklı olarak, gRPC, ağı için bir taban olarak HTTP/2 kullanır.</span><span class="sxs-lookup"><span data-stu-id="850e8-104">Unlike WCF, gRPC uses HTTP/2 as a base for its networking.</span></span> <span data-ttu-id="850e8-105">Bu, WCF ve SOAP üzerinde yalnızca HTTP/1.1 üzerinde çalışan önemli avantajlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="850e8-105">This offers significant advantages over WCF and SOAP, which only operate on HTTP/1.1.</span></span> <span data-ttu-id="850e8-106">GRPC 'yi kullanmak isteyen geliştiriciler için, HTTP/2 için başka bir seçenek olmadığından, HTTP/2 ' yi daha ayrıntılı bir şekilde incelemek ve gRPC 'yi kullanmaya yönelik ek avantajları belirlemek için ideal bir süre görünür.</span><span class="sxs-lookup"><span data-stu-id="850e8-106">For developers wanting to use gRPC, given that there's no alternative to HTTP/2, it would seem to be the ideal moment to explore HTTP/2 in more detail and identify additional benefits to using gRPC.</span></span>

<span data-ttu-id="850e8-107">2015 ' de Internet Mühendisliği görev gücü tarafından yayınlanan HTTP/2, zaten Google tarafından kullanılmakta olan deneysel SPDY protokolünden türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="850e8-107">HTTP/2, released by Internet Engineering Task Force in 2015, was derived from the experimental SPDY protocol, which was already being used by Google.</span></span> <span data-ttu-id="850e8-108">Özellikle HTTP/1.1 'den daha verimli, daha hızlı ve daha güvenli olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="850e8-108">It was specifically designed to be more efficient, faster, and more secure than HTTP/1.1.</span></span>

## <a name="key-features-of-http2"></a><span data-ttu-id="850e8-109">HTTP/2 ' nin önemli özellikleri</span><span class="sxs-lookup"><span data-stu-id="850e8-109">Key features of HTTP/2</span></span>

<span data-ttu-id="850e8-110">Aşağıdaki listede HTTP/2 ' nin bazı temel özellikleri ve avantajları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="850e8-110">The following list shows some of the key features and advantages of HTTP/2:</span></span>

### <a name="binary-protocol"></a><span data-ttu-id="850e8-111">İkili protokol</span><span class="sxs-lookup"><span data-stu-id="850e8-111">Binary protocol</span></span>

<span data-ttu-id="850e8-112">İstek/yanıt döngülerinde artık metin komutlarına gerek yok.</span><span class="sxs-lookup"><span data-stu-id="850e8-112">Request/response cycles no longer need text commands.</span></span> <span data-ttu-id="850e8-113">Bu, komutların uygulanmasını basitleştirir ve hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="850e8-113">This simplifies and speeds up implementation of commands.</span></span> <span data-ttu-id="850e8-114">Özellikle, verileri ayrıştırmak daha hızlıdır ve daha az bellek kullanır, ağ gecikmesi, hızsız ilgili açık geliştirmeler ve ağ kaynaklarının genel olarak daha iyi kullanıldığı bir şekilde azaltılır.</span><span class="sxs-lookup"><span data-stu-id="850e8-114">Specifically, parsing data is faster and uses less memory, network latency is reduced with obvious related improvements to speed, and there's an overall better use of network resources.</span></span>

### <a name="streams"></a><span data-ttu-id="850e8-115">Akışlar</span><span class="sxs-lookup"><span data-stu-id="850e8-115">Streams</span></span>

<span data-ttu-id="850e8-116">Akışlar, birden fazla ileti veya çerçevenin zaman uyumsuz olarak gönderilebileceği gönderici ve alıcı arasında uzun süreli bağlantılar oluşturulmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="850e8-116">Streams allow for the creation of long-lived connections between sender and receiver, over which multiple messages or frames can be sent asynchronously.</span></span> <span data-ttu-id="850e8-117">Birden çok akış, tek bir HTTP/2 bağlantısı üzerinden bağımsız olarak çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="850e8-117">Multiple streams can operate independently over a single HTTP/2 connection.</span></span>

### <a name="request-multiplexing-over-a-single-tcp-connection"></a><span data-ttu-id="850e8-118">Tek bir TCP bağlantısı üzerinden çoğullama isteme</span><span class="sxs-lookup"><span data-stu-id="850e8-118">Request multiplexing over a single TCP connection</span></span>

<span data-ttu-id="850e8-119">Bu özellik HTTP/2 ' nin en önemli yeniliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="850e8-119">This feature is one of the most important innovations of HTTP/2.</span></span> <span data-ttu-id="850e8-120">Veriler için birden çok paralel isteğe izin vererek, Web dosyalarını aynı anda tek bir sunucudan indirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="850e8-120">By allowing multiple parallel requests for data, it's now possible to download web files concurrently from a single server.</span></span> <span data-ttu-id="850e8-121">Web siteleri daha hızlı yüklenir ve iyileştirme gereksinimi azaltılır.</span><span class="sxs-lookup"><span data-stu-id="850e8-121">Websites load faster and the need for optimization is reduced.</span></span> <span data-ttu-id="850e8-122">Daha önceki bir istek tamamlanana kadar, izin verilen yanıtların gönderilmesi bekleneceği, satır başı (HOL) engelleme, daha önce de azaltılmalıdır (ancak, HOL engelleme yine de TCP Aktarım düzeyinde gerçekleşecektir).</span><span class="sxs-lookup"><span data-stu-id="850e8-122">Head-of-line (HOL) blocking, where responses that are ready must wait to be sent until an earlier request is completed, is also mitigated (although HOL blocking can still occur at the TCP transport level).</span></span>

### <a name="nettcp-like-performance-cross-platform"></a><span data-ttu-id="850e8-123">NetTCP benzeri performans, platformlar arası</span><span class="sxs-lookup"><span data-stu-id="850e8-123">NetTCP-like performance, cross-platform</span></span>

<span data-ttu-id="850e8-124">Temel olarak, gRPC ve HTTP/2 ' nin birleşimi, geliştiricilerin WCF için NetTCP bağlamalarının en az hızını ve verimliliğini ve bazı durumlarda daha da hızlı ve verimlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="850e8-124">Fundamentally, the combination of gRPC and HTTP/2 offer developers at least the equivalent speed and efficiency of NetTCP bindings for WCF, and in some cases even greater speed and efficiency.</span></span> <span data-ttu-id="850e8-125">Ancak NetTCP 'nin aksine, HTTP/2 üzerinden gRPC, .NET uygulamalarıyla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="850e8-125">However, unlike NetTCP, gRPC over HTTP/2 isn't constrained to .NET applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="850e8-126">[Önceki](interface-definition-language.md)
>[İleri](why-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="850e8-126">[Previous](interface-definition-language.md)
[Next](why-grpc.md)</span></span>
