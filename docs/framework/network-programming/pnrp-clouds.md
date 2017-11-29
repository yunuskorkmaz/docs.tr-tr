---
title: PNRP Bulutlar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1b9769d4e3936e127407f68de81f9b5b5da4fbc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pnrp-clouds"></a><span data-ttu-id="1589d-102">PNRP Bulutlar</span><span class="sxs-lookup"><span data-stu-id="1589d-102">PNRP Clouds</span></span>
<span data-ttu-id="1589d-103">PNRP "bulut" ağ üzerinden birbirleriyle iletişim düğümler kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1589d-103">A PNRP "cloud" represents a set of nodes that can communicate with each other through the network.</span></span> <span data-ttu-id="1589d-104">"Bulut" terimi "eş kafes" ve "eşler arası grafik" ile eşanlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="1589d-104">The term "cloud" is synonymous with "peer mesh" and "peer-to-peer graph".</span></span>  
  
 <span data-ttu-id="1589d-105">Düğümler arasında iletişim hiçbir zaman bir buluttan diğerine çıkarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1589d-105">Communication between nodes should never cross from one cloud to another.</span></span> <span data-ttu-id="1589d-106">A <xref:System.Net.PeerToPeer.Cloud> örneği duyarlıdır adıyla tarafından tanımlanan benzersiz olarak.</span><span class="sxs-lookup"><span data-stu-id="1589d-106">A <xref:System.Net.PeerToPeer.Cloud> instance is uniquely identified by its name, which is case-sensitive.</span></span> <span data-ttu-id="1589d-107">Tek bir eş veya düğüm için birden fazla bulut bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1589d-107">A single peer or node may be connected to more than one cloud.</span></span>  
  
 <span data-ttu-id="1589d-108">Bulut ağ arabirimlerine çok yakından bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1589d-108">Clouds are tied very closely to network interfaces.</span></span>  <span data-ttu-id="1589d-109">Bir çok konaklı makinede farklı alt ağa bağlı iki ağ kartı olan üç bulut döndürülür: her arabirimi ve tek bir genel kapsam Bulutu başına bağlantı yerel adresler için bir tane.</span><span class="sxs-lookup"><span data-stu-id="1589d-109">On a multi-homed machine with two network cards attached to different subnets, three clouds will be returned: one for each of the link local addresses per interface, and a single global scope cloud.</span></span>  
  
 <span data-ttu-id="1589d-110">"Bir kapsam bir gruplandırma birbirine bulamıyor bilgisayarların olduğu üç bulut kapsamlar", PNRP kullanır:</span><span class="sxs-lookup"><span data-stu-id="1589d-110">PNRP uses three cloud "scopes", in which a scope is a grouping of computers that are able to find each other:</span></span>  
  
-   <span data-ttu-id="1589d-111">Genel bulut genel IPv6 adresi kapsamını ve genel adresleri karşılık gelir ve tüm IPv6 Internet üzerindeki tüm bilgisayarlar temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1589d-111">The global cloud corresponds to the global IPv6 address scope and global addresses and represents all the computers on the entire IPv6 Internet.</span></span> <span data-ttu-id="1589d-112">Yalnızca tek bir genel bulut yok.</span><span class="sxs-lookup"><span data-stu-id="1589d-112">There is only a single global cloud.</span></span>  
  
-   <span data-ttu-id="1589d-113">Bağlantı-yerel bulutta bağlantı-yerel adresleri ve bağlantı yerel IPv6 adresi kapsamını karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1589d-113">The link-local cloud corresponds to the link-local IPv6 address scope and link-local addresses.</span></span> <span data-ttu-id="1589d-114">Bağlantı-yerel bulutta, genellikle yerel olarak bağlı alt ağ ile aynı olan belirli bir bağlantı içindir.</span><span class="sxs-lookup"><span data-stu-id="1589d-114">A link-local cloud is for a specific link, which is typically the same as the locally attached subnet.</span></span> <span data-ttu-id="1589d-115">Birden çok bağlantı-yerel Bulutlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="1589d-115">There can be multiple link-local clouds.</span></span>  
  
 <span data-ttu-id="1589d-116">Üçüncü Bulutu, siteye özgü bulut site IPv6 adresi kapsamı ve site-yerel adresleri karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1589d-116">A third cloud, the site-specific cloud, corresponds to the site IPv6 address scope and site-local addresses.</span></span> <span data-ttu-id="1589d-117">Yine PNRP desteklenmesine karşın, bu bulut onaylanmaz.</span><span class="sxs-lookup"><span data-stu-id="1589d-117">This cloud has been deprecated, although it is still supported in PNRP.</span></span>  
  
## <a name="clouds"></a><span data-ttu-id="1589d-118">Bulutlar</span><span class="sxs-lookup"><span data-stu-id="1589d-118">Clouds</span></span>  
 <span data-ttu-id="1589d-119">PNRP bulut örneği tarafından temsil edilen <xref:System.Net.PeerToPeer.Cloud> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1589d-119">PNRP clouds are represented by instances of the <xref:System.Net.PeerToPeer.Cloud> class.</span></span> <span data-ttu-id="1589d-120">Bulut grupları kullanılan bir eş numaralandırılabilir örneği tarafından temsil edilen <xref:System.Net.PeerToPeer.CloudCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1589d-120">Groups of clouds used a peer are represented by instances of the enumerable <xref:System.Net.PeerToPeer.CloudCollection> class.</span></span> <span data-ttu-id="1589d-121">Geçerli eşler arası bilinen PNRP bulut koleksiyonları elde edilebilir statik çağırarak <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1589d-121">Collections of PNRP clouds known to the current peer can be obtained by calling the static <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> method.</span></span>  
  
 <span data-ttu-id="1589d-122">Tek tek bulut 256 karakter Unicode dize olarak temsil benzersiz adlara sahip.</span><span class="sxs-lookup"><span data-stu-id="1589d-122">Individual clouds have unique names, represented as a 256 character Unicode string.</span></span> <span data-ttu-id="1589d-123">Bu adları benzersiz sınıfın örnekleri, bulut oluşturmak için yukarıda belirtilen kapsamı ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1589d-123">These names, along with the above-mentioned scope, are used to construct unique instances of the Cloud class.</span></span> <span data-ttu-id="1589d-124">Bu örnekler serileştirilmiş ve kalıcı kullanım için yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1589d-124">These instances can be serialized and reconstructed for persistent usage.</span></span>  
  
 <span data-ttu-id="1589d-125">Bir bulut örneği oluşturulan ya da elde sonra eş adlarını bilinen eş kafes oluşturmak için kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="1589d-125">Once a Cloud instance is created or obtained, peer names can be registered with it to create a mesh of known peers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1589d-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1589d-126">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Cloud>  
 [<span data-ttu-id="1589d-127">Eş Adı Çözümleme Protokolü</span><span class="sxs-lookup"><span data-stu-id="1589d-127">Peer Name Resolution Protocol</span></span>](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
