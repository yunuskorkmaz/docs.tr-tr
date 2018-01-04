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
ms.workload: dotnet
ms.openlocfilehash: f142c7aaa71ab2dbee1d2955f2c235a65e6c8bfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="pnrp-clouds"></a><span data-ttu-id="d3cae-102">PNRP Bulutlar</span><span class="sxs-lookup"><span data-stu-id="d3cae-102">PNRP Clouds</span></span>
<span data-ttu-id="d3cae-103">PNRP "bulut" ağ üzerinden birbirleriyle iletişim düğümler kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d3cae-103">A PNRP "cloud" represents a set of nodes that can communicate with each other through the network.</span></span> <span data-ttu-id="d3cae-104">"Bulut" terimi "eş kafes" ve "eşler arası grafik" ile eşanlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="d3cae-104">The term "cloud" is synonymous with "peer mesh" and "peer-to-peer graph".</span></span>  
  
 <span data-ttu-id="d3cae-105">Düğümler arasında iletişim hiçbir zaman bir buluttan diğerine çıkarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3cae-105">Communication between nodes should never cross from one cloud to another.</span></span> <span data-ttu-id="d3cae-106">A <xref:System.Net.PeerToPeer.Cloud> örneği duyarlıdır adıyla tarafından tanımlanan benzersiz olarak.</span><span class="sxs-lookup"><span data-stu-id="d3cae-106">A <xref:System.Net.PeerToPeer.Cloud> instance is uniquely identified by its name, which is case-sensitive.</span></span> <span data-ttu-id="d3cae-107">Tek bir eş veya düğüm için birden fazla bulut bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d3cae-107">A single peer or node may be connected to more than one cloud.</span></span>  
  
 <span data-ttu-id="d3cae-108">Bulut ağ arabirimlerine çok yakından bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d3cae-108">Clouds are tied very closely to network interfaces.</span></span>  <span data-ttu-id="d3cae-109">Bir çok konaklı makinede farklı alt ağa bağlı iki ağ kartı olan üç bulut döndürülür: her arabirimi ve tek bir genel kapsam Bulutu başına bağlantı yerel adresler için bir tane.</span><span class="sxs-lookup"><span data-stu-id="d3cae-109">On a multi-homed machine with two network cards attached to different subnets, three clouds will be returned: one for each of the link local addresses per interface, and a single global scope cloud.</span></span>  
  
 <span data-ttu-id="d3cae-110">"Bir kapsam bir gruplandırma birbirine bulamıyor bilgisayarların olduğu üç bulut kapsamlar", PNRP kullanır:</span><span class="sxs-lookup"><span data-stu-id="d3cae-110">PNRP uses three cloud "scopes", in which a scope is a grouping of computers that are able to find each other:</span></span>  
  
-   <span data-ttu-id="d3cae-111">Genel bulut genel IPv6 adresi kapsamını ve genel adresleri karşılık gelir ve tüm IPv6 Internet üzerindeki tüm bilgisayarlar temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d3cae-111">The global cloud corresponds to the global IPv6 address scope and global addresses and represents all the computers on the entire IPv6 Internet.</span></span> <span data-ttu-id="d3cae-112">Yalnızca tek bir genel bulut yok.</span><span class="sxs-lookup"><span data-stu-id="d3cae-112">There is only a single global cloud.</span></span>  
  
-   <span data-ttu-id="d3cae-113">Bağlantı-yerel bulutta bağlantı-yerel adresleri ve bağlantı yerel IPv6 adresi kapsamını karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d3cae-113">The link-local cloud corresponds to the link-local IPv6 address scope and link-local addresses.</span></span> <span data-ttu-id="d3cae-114">Bağlantı-yerel bulutta, genellikle yerel olarak bağlı alt ağ ile aynı olan belirli bir bağlantı içindir.</span><span class="sxs-lookup"><span data-stu-id="d3cae-114">A link-local cloud is for a specific link, which is typically the same as the locally attached subnet.</span></span> <span data-ttu-id="d3cae-115">Birden çok bağlantı-yerel Bulutlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="d3cae-115">There can be multiple link-local clouds.</span></span>  
  
 <span data-ttu-id="d3cae-116">Üçüncü Bulutu, siteye özgü bulut site IPv6 adresi kapsamı ve site-yerel adresleri karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d3cae-116">A third cloud, the site-specific cloud, corresponds to the site IPv6 address scope and site-local addresses.</span></span> <span data-ttu-id="d3cae-117">Yine PNRP desteklenmesine karşın, bu bulut onaylanmaz.</span><span class="sxs-lookup"><span data-stu-id="d3cae-117">This cloud has been deprecated, although it is still supported in PNRP.</span></span>  
  
## <a name="clouds"></a><span data-ttu-id="d3cae-118">Bulutlar</span><span class="sxs-lookup"><span data-stu-id="d3cae-118">Clouds</span></span>  
 <span data-ttu-id="d3cae-119">PNRP bulut örneği tarafından temsil edilen <xref:System.Net.PeerToPeer.Cloud> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d3cae-119">PNRP clouds are represented by instances of the <xref:System.Net.PeerToPeer.Cloud> class.</span></span> <span data-ttu-id="d3cae-120">Bulut grupları kullanılan bir eş numaralandırılabilir örneği tarafından temsil edilen <xref:System.Net.PeerToPeer.CloudCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d3cae-120">Groups of clouds used a peer are represented by instances of the enumerable <xref:System.Net.PeerToPeer.CloudCollection> class.</span></span> <span data-ttu-id="d3cae-121">Geçerli eşler arası bilinen PNRP bulut koleksiyonları elde edilebilir statik çağırarak <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d3cae-121">Collections of PNRP clouds known to the current peer can be obtained by calling the static <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> method.</span></span>  
  
 <span data-ttu-id="d3cae-122">Tek tek bulut 256 karakter Unicode dize olarak temsil benzersiz adlara sahip.</span><span class="sxs-lookup"><span data-stu-id="d3cae-122">Individual clouds have unique names, represented as a 256 character Unicode string.</span></span> <span data-ttu-id="d3cae-123">Bu adları benzersiz sınıfın örnekleri, bulut oluşturmak için yukarıda belirtilen kapsamı ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d3cae-123">These names, along with the above-mentioned scope, are used to construct unique instances of the Cloud class.</span></span> <span data-ttu-id="d3cae-124">Bu örnekler serileştirilmiş ve kalıcı kullanım için yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3cae-124">These instances can be serialized and reconstructed for persistent usage.</span></span>  
  
 <span data-ttu-id="d3cae-125">Bir bulut örneği oluşturulan ya da elde sonra eş adlarını bilinen eş kafes oluşturmak için kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="d3cae-125">Once a Cloud instance is created or obtained, peer names can be registered with it to create a mesh of known peers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3cae-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3cae-126">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Cloud>  
 [<span data-ttu-id="d3cae-127">Eş Adı Çözümleme Protokolü</span><span class="sxs-lookup"><span data-stu-id="d3cae-127">Peer Name Resolution Protocol</span></span>](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
