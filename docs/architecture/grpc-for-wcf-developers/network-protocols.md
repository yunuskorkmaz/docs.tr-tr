---
title: Ağ protokolleri-WCF geliştiricileri için gRPC
description: GRPC ağ protokollerine genel bakış.
ms.date: 09/02/2019
ms.openlocfilehash: 801d57c95aec748e5dcf667ca480775ff945b55c
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938565"
---
# <a name="network-protocols"></a><span data-ttu-id="fe504-103">Ağ protokolleri</span><span class="sxs-lookup"><span data-stu-id="fe504-103">Network protocols</span></span>

<span data-ttu-id="fe504-104">Windows Communication Foundation (WCF) aksine gRPC, ağı için bir taban olarak HTTP/2 kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe504-104">Unlike Windows Communication Foundation (WCF), gRPC uses HTTP/2 as a base for its networking.</span></span> <span data-ttu-id="fe504-105">Bu protokol, WCF ve SOAP üzerinde yalnızca HTTP/1.1 üzerinde çalışan önemli avantajlar sunar.</span><span class="sxs-lookup"><span data-stu-id="fe504-105">This protocol offers significant advantages over WCF and SOAP, which operate only on HTTP/1.1.</span></span> <span data-ttu-id="fe504-106">GRPC 'yi kullanmak isteyen geliştiriciler için, HTTP/2 için başka bir seçenek olmadığından, HTTP/2 ' yi daha ayrıntılı bir şekilde incelemek ve gRPC kullanmanın ek avantajlarını belirlemek için ideal bir süre görünür.</span><span class="sxs-lookup"><span data-stu-id="fe504-106">For developers wanting to use gRPC, given that there's no alternative to HTTP/2, it would seem to be the ideal moment to explore HTTP/2 in more detail and identify additional benefits of using gRPC.</span></span>

<span data-ttu-id="fe504-107">2015 ' de Internet Mühendisliği görev gücü tarafından yayınlanan HTTP/2, zaten Google tarafından kullanılmakta olan deneysel SPDY protokolünden türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe504-107">HTTP/2, released by Internet Engineering Task Force in 2015, was derived from the experimental SPDY protocol, which was already being used by Google.</span></span> <span data-ttu-id="fe504-108">Özellikle HTTP/1.1 'den daha verimli, daha hızlı ve daha güvenli olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fe504-108">It was specifically designed to be more efficient, faster, and more secure than HTTP/1.1.</span></span>

## <a name="key-features-of-http2"></a><span data-ttu-id="fe504-109">HTTP/2 ' nin önemli özellikleri</span><span class="sxs-lookup"><span data-stu-id="fe504-109">Key features of HTTP/2</span></span>

<span data-ttu-id="fe504-110">Bu listede HTTP/2 ' nin bazı temel özellikleri ve avantajları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="fe504-110">This list shows some of the key features and advantages of HTTP/2:</span></span>

### <a name="binary-protocol"></a><span data-ttu-id="fe504-111">İkili protokol</span><span class="sxs-lookup"><span data-stu-id="fe504-111">Binary protocol</span></span>

<span data-ttu-id="fe504-112">İstek/yanıt döngülerinde artık metin komutlarına gerek yok.</span><span class="sxs-lookup"><span data-stu-id="fe504-112">Request/response cycles no longer need text commands.</span></span> <span data-ttu-id="fe504-113">Bu etkinlik, komutlarının uygulanmasını basitleştirir ve hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="fe504-113">This activity simplifies and speeds up the implementation of commands.</span></span> <span data-ttu-id="fe504-114">Özellikle, verileri ayrıştırmak daha hızlıdır ve daha az bellek kullanır, ağ gecikmesi, hızsız ilgili açık geliştirmeler ve ağ kaynaklarının genel olarak daha iyi kullanıldığı bir şekilde azaltılır.</span><span class="sxs-lookup"><span data-stu-id="fe504-114">Specifically, parsing data is faster and uses less memory, network latency is reduced with obvious related improvements to speed, and there's an overall better use of network resources.</span></span>

### <a name="streams"></a><span data-ttu-id="fe504-115">Akışlar</span><span class="sxs-lookup"><span data-stu-id="fe504-115">Streams</span></span>

<span data-ttu-id="fe504-116">Akışlar, gönderici ve alıcı arasında çok fazla ileti veya çerçevenin zaman uyumsuz olarak gönderilebileceği uzun süreli bağlantılar oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe504-116">Streams allow you to create long-lived connections between sender and receiver, over which multiple messages or frames can be sent asynchronously.</span></span> <span data-ttu-id="fe504-117">Birden çok akış, tek bir HTTP/2 bağlantısı üzerinden bağımsız olarak çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="fe504-117">Multiple streams can operate independently over a single HTTP/2 connection.</span></span>

### <a name="request-multiplexing-over-a-single-tcp-connection"></a><span data-ttu-id="fe504-118">Tek bir TCP bağlantısı üzerinden çoğullama isteme</span><span class="sxs-lookup"><span data-stu-id="fe504-118">Request multiplexing over a single TCP connection</span></span>

<span data-ttu-id="fe504-119">Bu özellik HTTP/2 ' nin en önemli yeniliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="fe504-119">This feature is one of the most important innovations of HTTP/2.</span></span> <span data-ttu-id="fe504-120">Veriler için birden çok paralel isteğe izin verdiğinden, artık Web dosyalarını tek bir sunucudan aynı anda indirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fe504-120">Because it allows multiple parallel requests for data, it's now possible to download web files concurrently from a single server.</span></span> <span data-ttu-id="fe504-121">Web siteleri daha hızlı yüklenir ve iyileştirme gereksinimi azaltılır.</span><span class="sxs-lookup"><span data-stu-id="fe504-121">Websites load faster, and the need for optimization is reduced.</span></span> <span data-ttu-id="fe504-122">Daha önceki bir istek tamamlanana kadar, izin verilen yanıtların gönderilmesini beklemesi gereken, satır başı (HOL) engelleme, aynı zamanda da azaltılmalıdır (ancak, HOL engelleme yine de TCP-Transport düzeyinde gerçekleşecektir).</span><span class="sxs-lookup"><span data-stu-id="fe504-122">Head-of-line (HOL) blocking, where responses that are ready must wait to be sent until an earlier request is completed, is also mitigated (although HOL blocking can still occur at the TCP-transport level).</span></span>

### <a name="nettcp-like-performance-cross-platform"></a><span data-ttu-id="fe504-123">Net. TCP benzeri performans, platformlar arası</span><span class="sxs-lookup"><span data-stu-id="fe504-123">Net.TCP-like performance, cross-platform</span></span>

<span data-ttu-id="fe504-124">Temel olarak, gRPC ve HTTP/2 ' nin birleşimi, geliştiricilere en azından WCF için net. TCP bağlamalarının ve bazı durumlarda daha fazla hız ve verimlilik sağlayan, büyük hız ve verimlilik sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe504-124">Fundamentally, the combination of gRPC and HTTP/2 offers developers at least the equivalent speed and efficiency of Net.TCP bindings for WCF, and in some cases even greater speed and efficiency.</span></span> <span data-ttu-id="fe504-125">Ancak, net. TCP 'den farklı olarak, HTTP/2 üzerinden gRPC, .NET uygulamalarıyla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="fe504-125">But, unlike Net.TCP, gRPC over HTTP/2 isn't constrained to .NET applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fe504-126">[Önceki](interface-definition-language.md) 
> [Sonraki](why-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="fe504-126">[Previous](interface-definition-language.md)
[Next](why-grpc.md)</span></span>
