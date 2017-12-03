---
title: "Eş Kafesleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d747b2916f544294bb69f01aadc1321370878689
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="peer-meshes"></a><span data-ttu-id="a32f0-102">Eş Kafesleri</span><span class="sxs-lookup"><span data-stu-id="a32f0-102">Peer Meshes</span></span>
<span data-ttu-id="a32f0-103">A *mesh* iletişim kendilerini arasında ve bir benzersiz kafes kimliği tarafından tanımlanan eş düğümlerinin adlandırılmış koleksiyonu (birbirine bağlı bir grafik)</span><span class="sxs-lookup"><span data-stu-id="a32f0-103">A *mesh* is a named collection (an interconnected graph) of peer nodes that can communicate among themselves and that are identified by a unique mesh ID.</span></span> <span data-ttu-id="a32f0-104">Her düğüm için birden çok diğer düğümlere bağlanır.</span><span class="sxs-lookup"><span data-stu-id="a32f0-104">Each node is connected to multiple other nodes.</span></span> <span data-ttu-id="a32f0-105">İyi bağlantılı bir kafes kafes en ilerideki kenarlarında düğümler arasında nispeten az durakları herhangi iki düğüm arasında bir yolu yoktur ve bazı düğümler veya bağlantıları bırakma olsa bile kafes bağlı kalır. Diğer eş bunları bulabilmesi için Kafes etkin düğüm karşılık gelen bir kafes kimliği ile uç nokta bilgilerini yayımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a32f0-105">In a well-connected mesh, there is a path between any two nodes, with relatively few hops between the nodes on the furthest edges of the mesh, and the mesh will remain connected even if some nodes or connections drop out. Active nodes in the mesh publish their endpoint information with a corresponding mesh ID so that other peers can find them.</span></span>  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a><span data-ttu-id="a32f0-106">Eş kanalı kullanılarak oluşturulan bir kafes özellikleri</span><span class="sxs-lookup"><span data-stu-id="a32f0-106">Characteristics of a Mesh Created Using Peer Channel</span></span>  
  
#### <a name="uniquely-identified"></a><span data-ttu-id="a32f0-107">Benzersiz olarak tanımlanır</span><span class="sxs-lookup"><span data-stu-id="a32f0-107">Uniquely Identified</span></span>  
  
-   <span data-ttu-id="a32f0-108">Benzersiz bir kimliği her kafes tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a32f0-108">A unique ID identifies each mesh.</span></span> <span data-ttu-id="a32f0-109">Bir etki alanı adı sistemi (DNS) ana bilgisayar adı ile aynı biçimi kafes (veya ağ kimliği) adı kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="a32f0-109">The name of the mesh (or mesh ID) is in the same format as a Domain Name System (DNS) host name.</span></span> <span data-ttu-id="a32f0-110">Bu nedenle, bu kafes kimliği uygulama kapsamı içinde kullanılan çözümleyicinin amaçlanan istemci için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a32f0-110">As such, this mesh ID must be unique for the intended client of the application within the scope of the resolver being used.</span></span> <span data-ttu-id="a32f0-111">Bir ortak adı "MyFamilysPeers" veya "KevinsPokerTable," gibi başka bir kullanıcı adı ile kolayca çakışabilir ve istenmeyen eş gizlilik sorunlara neden veya bağlantı gecikmesi artırın uç nokta bilgileri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="a32f0-111">A common name such as "MyFamilysPeers" or "KevinsPokerTable," may easily collide with other user names and may return unintended peer endpoint information, which could result in privacy issues or increase connection latency.</span></span> <span data-ttu-id="a32f0-112">Benzersiz bir kimliği (örneğin, "KevinsPokerTable90210") kafes için takma ad sonek eklemek için bu sorunları önlemek için bir yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="a32f0-112">One way to avoid these issues may be to add a unique ID as a postfix to the nickname for the mesh (for example, "KevinsPokerTable90210").</span></span>  
  
#### <a name="message-flooding"></a><span data-ttu-id="a32f0-113">İleti taşmasını</span><span class="sxs-lookup"><span data-stu-id="a32f0-113">Message Flooding</span></span>  
  
-   <span data-ttu-id="a32f0-114">Mesh iletileri bir veya daha fazla göndericilerden aynı kafes içindeki tüm diğer eş düğümlere dağıtılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a32f0-114">The mesh allows messages to be propagated from one or more senders to all other peer nodes in the same mesh.</span></span> <span data-ttu-id="a32f0-115">Eş düğümleri tarafından yayılan iletileri kullanan ad alanında belirtilen üstbilgileri `http://schemas.microsoft.com/net/2006/05/peer`.</span><span class="sxs-lookup"><span data-stu-id="a32f0-115">Messages flooded by peer nodes use headers specified in the namespace at `http://schemas.microsoft.com/net/2006/05/peer`.</span></span>  
  
#### <a name="optimized-connections"></a><span data-ttu-id="a32f0-116">En iyi duruma getirilmiş bağlantıları</span><span class="sxs-lookup"><span data-stu-id="a32f0-116">Optimized Connections</span></span>  
  
-   <span data-ttu-id="a32f0-117">Düğümleri katılma ve bırakın, tüm düğümler bölümleri (birbirlerinden düğümlerinin grup) oluşturma az olasılığını düzgün bağlantısı sahip olduktan eş kanalı kafes otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a32f0-117">A Peer Channel mesh automatically adjusts when nodes join and leave, ensuring that all nodes have good connectivity with little chance of creating partitions (groups of nodes isolated from each other).</span></span> <span data-ttu-id="a32f0-118">Ağ bağlantıları da dinamik alıcı gönderenden ileti gecikme süresini olabildiğince küçük böylece geçerli trafik düzenlerini esas alarak en iyi duruma getirilir.</span><span class="sxs-lookup"><span data-stu-id="a32f0-118">Connections in the mesh are also dynamically optimized based on current traffic patterns so that message latency from sender to receiver is as small as possible.</span></span>  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a><span data-ttu-id="a32f0-119">Eş kanal sağlamaz popüler ağ özellikleri</span><span class="sxs-lookup"><span data-stu-id="a32f0-119">Popular Network Features That Peer Channel Does Not Provide</span></span>  
 <span data-ttu-id="a32f0-120">Eş kanal sağlamaz popüler ağ özelliklerini haberdar olmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a32f0-120">It is important to be aware of popular network features that Peer Channel does not provide.</span></span> <span data-ttu-id="a32f0-121">Tüm eş kanalı üstünde oluşturulmuş, bu özellikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="a32f0-121">These features, which may all be built on top of Peer Channel, include the following:</span></span>  
  
-   <span data-ttu-id="a32f0-122">**İleti sıralama:** iletiler tek bir kaynaktan kaynaklanan tüm diğer taraflar aynı sırada veya kaynak gönderilen sırada değil geldiğinde.</span><span class="sxs-lookup"><span data-stu-id="a32f0-122">**Message ordering:** Messages originating from a single source may not arrive at all other parties in the same order or in the order that the source sent.</span></span> <span data-ttu-id="a32f0-123">İletileri gerektiren uygulamalar içinde teslim edilemiyor belirli bir sipariş, uygulamalarına (örneğin, tüm iletileri artan Kimliğiyle ekleyerek) oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a32f0-123">Applications that require messages be delivered in a certain order must build it into their applications (for example, by including a monotonically increasing ID with all messages).</span></span>  
  
-   <span data-ttu-id="a32f0-124">**Güvenilir Mesajlaşma:** eş kanalı ileti alma tüm eşleri tarafından emin olmak için bir mekanizma içermez.</span><span class="sxs-lookup"><span data-stu-id="a32f0-124">**Reliable messaging:** Peer Channel does not include a mechanism to ensure message reception by all peers.</span></span> <span data-ttu-id="a32f0-125">İleti teslimi güvence altına almak için güvenilirlik katmanı eş kanal üzerine yazması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a32f0-125">To guarantee message delivery, you must write a reliability layer on top of Peer Channel.</span></span>
