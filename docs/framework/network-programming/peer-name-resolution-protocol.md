---
title: "Eş Adı Çözümleme Protokolü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 805f6f6ed7990b42065dfe7985a5d81844961897
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="b15f3-102">Eş Adı Çözümleme Protokolü</span><span class="sxs-lookup"><span data-stu-id="b15f3-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="b15f3-103">Eşler arası ortamlarda, eş belirli ad çözümleme sistemleri birbirlerinin ağ konumlarını (adresler, protokoller ve bağlantı noktaları) gidermek için adlarını veya diğer türlerinden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b15f3-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="b15f3-104">Geçmişte, diğer etki alanı adı sistemi (DNS) içinde eksiklikleri yanı sıra doğası gereği geçici bir bağlantı tarafından eş adı çözümleme karmaşık.</span><span class="sxs-lookup"><span data-stu-id="b15f3-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="b15f3-105">Microsoft® Windows® Eşler arası ağ platformu ile Eş Adı Çözümleme Protokolü (PNRP), güvenli, ölçeklenebilir ve dinamik ad kaydı ve ilk Windows XP için geliştirilen ve içinde yükseltme adı çözümleme protokolü bu sorunu çözer Windows Vista™.</span><span class="sxs-lookup"><span data-stu-id="b15f3-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="b15f3-106">PNRP uygulama geliştiricileri için heyecan verici yeni olanaklarını açma geleneksel ad çözümleme sistemlerinden çok farklı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="b15f3-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="b15f3-107">PNRP ile eş adlarını makine veya tek tek uygulamalar veya hizmetler makinede uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b15f3-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="b15f3-108">Eş adı çözümleme bir adresi, bağlantı noktası ve büyük olasılıkla bir genişletilmiş yükü içerir.</span><span class="sxs-lookup"><span data-stu-id="b15f3-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="b15f3-109">Bu sistemin hata toleransı, hiçbir performans sorunlarını ve eski adreslerin hiçbir zaman döndürülecek ad çözünürlüğü yararları; protokol mobil kullanıcılar bulmak için mükemmel bir çözüm sağlayarak.</span><span class="sxs-lookup"><span data-stu-id="b15f3-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="b15f3-110">Güvenlik açısından, eş adları olabilir olarak güvenli (korumalı) yayımlanan ya da güvenli olmayan (korumasız).</span><span class="sxs-lookup"><span data-stu-id="b15f3-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="b15f3-111">PNRP yanıltmaya karşı güvenli eş adlarını korumak için ortak anahtar şifrelemesini kullanır; bilgisayarlar ve hizmetler ile PNRP adlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b15f3-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
-   <span data-ttu-id="b15f3-112">Eş Adı Çözümleme Protokolü'nü aşağıdaki özellikleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="b15f3-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
-   <span data-ttu-id="b15f3-113">Dağıtılmış ve neredeyse tamamen sunucusuz.</span><span class="sxs-lookup"><span data-stu-id="b15f3-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="b15f3-114">Sunucular, yalnızca önyükleme işlemi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b15f3-114">Servers are only required for the bootstrapping process.</span></span>  
  
-   <span data-ttu-id="b15f3-115">Ad yayını üçüncü tarafların katılımı olmadan güvenli hale getirin.</span><span class="sxs-lookup"><span data-stu-id="b15f3-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="b15f3-116">DNS ad yayını farklı olarak, anlık ve finansal maliyet gerektirmeden PNRP ad yayını.</span><span class="sxs-lookup"><span data-stu-id="b15f3-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
-   <span data-ttu-id="b15f3-117">PNRP güncelleştirmeleri gerçek zamanlı, eski adreslerin çözümleme engeller.</span><span class="sxs-lookup"><span data-stu-id="b15f3-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
-   <span data-ttu-id="b15f3-118">Adların PNRP aracılığıyla çözümlenmesi bilgisayarlar da ad çözümleme hizmetleri için sağlayarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="b15f3-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
-  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="b15f3-119">System.Net.PeerToPeer Namespace</span><span class="sxs-lookup"><span data-stu-id="b15f3-119">The System.Net.PeerToPeer Namespace</span></span>  
  
-   <span data-ttu-id="b15f3-120">PNRP işlevi tarafından tanımlanan <xref:System.Net.PeerToPeer> ad alanı .NET Framework sürüm 3.5 içinde.</span><span class="sxs-lookup"><span data-stu-id="b15f3-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="b15f3-121">Eş adları kullanılabilir bir PNRP hizmeti ile kaydetmek ve çözümlemek için kullanılan türleri kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b15f3-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
-  
  
-   <span data-ttu-id="b15f3-122">(PNRP ve özel eş çözücüler oluşturulabilir ve başlatılan türlerini kullanarak sağlanan <xref:System.ServiceModel.PeerResolvers> ad.)</span><span class="sxs-lookup"><span data-stu-id="b15f3-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
-  
  
-   <span data-ttu-id="b15f3-123">Kullanılabilir bir PNRP hizmetiyle adları kaydetmek ve çözümlemek için kullanılan temel türleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b15f3-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
-  
  
-   <span data-ttu-id="b15f3-124"><xref:System.Net.PeerToPeer.Cloud>: Kapsamı dahil olmak üzere bir kullanılabilir PNRP bulut açıklayan bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b15f3-124"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
-   <span data-ttu-id="b15f3-125"><xref:System.Net.PeerToPeer.PeerName>: Kaydetmek ve daha sonra bir eş Bulutu içindeki çözümlemek için kullanılan bir eş adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b15f3-125"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
-   <span data-ttu-id="b15f3-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: PNRP bulutta eş kurulabildiğinden ağ uç noktalarını içeren bir eş için kayıt bilgilerini içeren kayıt tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b15f3-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
-   <span data-ttu-id="b15f3-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Eş ad kaydı durdurmak ve başlatmak için yöntemleri de dahil olmak üzere eş adını, kayıt işlemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b15f3-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
-   <span data-ttu-id="b15f3-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Bir eş adı çözümleme için zaman uyumlu ve zaman uyumsuz yöntemleri de dahil olmak üzere kendi ağ uç çözümleme işlemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b15f3-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
-  
  
-  
  
## <a name="see-also"></a><span data-ttu-id="b15f3-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b15f3-129">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers>  
 <xref:System.Net.PeerToPeer>  
 [<span data-ttu-id="b15f3-130">Ağ programlama örnekleri</span><span class="sxs-lookup"><span data-stu-id="b15f3-130">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="b15f3-131">PeerToPeer teknoloji örnek</span><span class="sxs-lookup"><span data-stu-id="b15f3-131">PeerToPeer Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179571)
