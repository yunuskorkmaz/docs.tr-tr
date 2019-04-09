---
title: Eş Adı Çözümleme Protokolü
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: 4473ccb01349d2697ba512861aa505d5e363ab19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119073"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="f7560-102">Eş Adı Çözümleme Protokolü</span><span class="sxs-lookup"><span data-stu-id="f7560-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="f7560-103">Eşler arası ortamlarında eşleri belirli ad çözümleme sistemleri birbirlerinin ağ konumlarını (adresleri, protokoller ve bağlantı noktaları) çözümlemek için adları veya türlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7560-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="f7560-104">Geçmişte, diğer etki alanı adı sistemi (DNS) içinde eksiklikleri yanı sıra, doğası gereği geçici bir bağlantı tarafından eş adı çözümleme karmaşık.</span><span class="sxs-lookup"><span data-stu-id="f7560-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="f7560-105">Microsoft® Windows® Eşler arası ağ platformu ile Eş Adı Çözümleme Protokolü (PNRP), güvenli, ölçeklenebilir ve dinamik ad kayıt ve Windows XP için ilk kez geliştirilen ve sonra yükseltme adı çözümleme protokolü bu sorunu çözer. Windows Vista™.</span><span class="sxs-lookup"><span data-stu-id="f7560-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="f7560-106">PNRP uygulama geliştiricileri için heyecan verici yeni olasılıklara açma geleneksel ad çözümlemesi sistemlerden çok farklı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="f7560-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="f7560-107">PNRP ile eş adları, makine veya tek tek uygulamalar veya hizmetler makinede uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7560-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="f7560-108">Eş adı çözümleme bir adresi, bağlantı noktası ve büyük olasılıkla bir genişletilmiş yükü içerir.</span><span class="sxs-lookup"><span data-stu-id="f7560-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="f7560-109">Bu sistemin hata toleransı, hiçbir performans sorunlarını ve eski adreslerin hiçbir zaman döndüreceği ad çözünürlüğü avantajına sahip olur; Protokolü, mobil kullanıcıların bulmak için mükemmel bir çözüm yapılıyor.</span><span class="sxs-lookup"><span data-stu-id="f7560-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="f7560-110">Güvenlik açısından, eş adları olabilir (korumalı) güvenli olarak yayımlanan veya güvenli olmayan (korumasız).</span><span class="sxs-lookup"><span data-stu-id="f7560-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="f7560-111">PNRP güvenli eş adları yanıltmaya karşı korumak için ortak anahtar şifrelemesi kullanır; hem bilgisayarları hem de Hizmetleri ile PNRP adlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7560-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="f7560-112">Eş Adı Çözümleme Protokolü'nü aşağıdaki özellikleri göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="f7560-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
-   <span data-ttu-id="f7560-113">Dağıtılmış ve neredeyse tamamen sunucusuz.</span><span class="sxs-lookup"><span data-stu-id="f7560-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="f7560-114">Sunucular, yalnızca önyükleme işlemi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f7560-114">Servers are only required for the bootstrapping process.</span></span>  
  
-   <span data-ttu-id="f7560-115">Ada yayın olmadan üçüncü taraflara katılımı güvenli hale getirin.</span><span class="sxs-lookup"><span data-stu-id="f7560-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="f7560-116">DNS adı yayını, anlık ve finansal maliyeti PNRP adı yayını.</span><span class="sxs-lookup"><span data-stu-id="f7560-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
-   <span data-ttu-id="f7560-117">PNRP güncelleştirmeleri gerçek zamanlı olarak çözümleme eski adresi engeller.</span><span class="sxs-lookup"><span data-stu-id="f7560-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
-   <span data-ttu-id="f7560-118">PNRP aracılığıyla ad çözümlemesi, ad çözümleme hizmetleri için de izin vererek bilgisayarlar genişletir.</span><span class="sxs-lookup"><span data-stu-id="f7560-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="f7560-119">System.Net.PeerToPeer ad alanı</span><span class="sxs-lookup"><span data-stu-id="f7560-119">The System.Net.PeerToPeer namespace</span></span>  
  
-   <span data-ttu-id="f7560-120">PNRP işlevleri tarafından tanımlanan <xref:System.Net.PeerToPeer> ad alanı içinde .NET Framework sürüm 3.5.</span><span class="sxs-lookup"><span data-stu-id="f7560-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="f7560-121">Bu, kullanılabilir bir PNRP Service eş adları kaydetmek ve çözümlemek için kullanılan türleri kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7560-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
-   <span data-ttu-id="f7560-122">(PNRP ve özel eş çözücüler oluşturulabilir ve örneklenen türlerini kullanarak sağlanan içinde <xref:System.ServiceModel.PeerResolvers> ad.)</span><span class="sxs-lookup"><span data-stu-id="f7560-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
-   <span data-ttu-id="f7560-123">Adları kullanılabilir bir PNRP hizmetiyle kaydetmek ve çözümlemek için kullanılan temel türleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f7560-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
-   <xref:System.Net.PeerToPeer.Cloud><span data-ttu-id="f7560-124">: Kapsamı dahil olmak üzere bir kullanılabilir PNRP bulut açıklayan bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7560-124">: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
-   <xref:System.Net.PeerToPeer.PeerName><span data-ttu-id="f7560-125">: Kaydolun ve sonradan Bulutu içinde bir eş çözümlemek için kullanılan bir eş adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7560-125">: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
-   <xref:System.Net.PeerToPeer.PeerNameRecord><span data-ttu-id="f7560-126">: Eş kurulabileceğinden ağ uç noktaları içeren bir eş için kayıt bilgileri içeren PNRP bulutta kayıt tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7560-126">: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
-   <xref:System.Net.PeerToPeer.PeerNameRegistration><span data-ttu-id="f7560-127">: Kayıt işlemi için eş ad kaydı durdurmak ve başlatmak yöntemleri dahil olmak üzere bir eş adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7560-127">: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
-   <xref:System.Net.PeerToPeer.PeerNameResolver><span data-ttu-id="f7560-128">: Çözüm için zaman uyumlu ve zaman uyumsuz yöntemleri dahil olmak üzere kendi ağ uç noktası için eş adı çözümleme sürecini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7560-128">: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7560-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7560-129">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="f7560-130">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="f7560-130">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
- [<span data-ttu-id="f7560-131">PeerToPeer teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="f7560-131">PeerToPeer Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179571)
