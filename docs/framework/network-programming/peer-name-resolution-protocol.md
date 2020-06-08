---
title: Eş Adı Çözümleme Protokolü
description: Eş adı çözümleme Protokolü (PNRP), güvenli, ölçeklenebilir ve dinamik ad kaydı ve ad çözümleme protokolü hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: 72eb63c2c90f398c515d77cd2b2d693237e533a5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502229"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="bf491-103">Eş Adı Çözümleme Protokolü</span><span class="sxs-lookup"><span data-stu-id="bf491-103">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="bf491-104">Eşler arası ortamlarda, eşler, her birinin ağ konumlarını (adresler, protokoller ve bağlantı noktaları) adlarla veya diğer tanımlayıcı türlerinden çözümlemek için belirli ad çözümleme sistemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf491-104">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="bf491-105">Geçmişte, eş adı çözümlemesi, etki alanı adı sistemi (DNS) içindeki diğer eksikler tarafından da doğal olarak geçici bağlantı tarafından karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="bf491-105">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="bf491-106">Microsoft® Windows® Eşler arası ağ platformu, ilk olarak Windows XP için geliştirilmiş ve ardından Windows Vista™ ' de yükseltilen eş adı çözümleme Protokolü (PNRP), güvenli, ölçeklenebilir ve dinamik bir ad kaydı ve ad çözümleme protokolü ile bu sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="bf491-106">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="bf491-107">PNRP geleneksel ad çözümleme sistemlerinden çok farklı çalışır ve uygulama geliştiricileri için heyecan verici yeni olanaklar sunar.</span><span class="sxs-lookup"><span data-stu-id="bf491-107">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="bf491-108">PNRP ile, eş adları makineye veya makinedeki ayrı uygulamalara veya hizmetlere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="bf491-108">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="bf491-109">Eş adı çözümlemesi bir adres, bağlantı noktası ve büyük olasılıkla genişletilmiş bir yük içerir.</span><span class="sxs-lookup"><span data-stu-id="bf491-109">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="bf491-110">Bu sistemin avantajları arasında hata toleransı, performans sorunu olmaması ve hiçbir şekilde eski adresleri döndürmeyecek ad çözümlemeleri dahildir; Protokolü mobil kullanıcıları bulmaya yönelik harika bir çözüm haline getirme.</span><span class="sxs-lookup"><span data-stu-id="bf491-110">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="bf491-111">Güvenlik açısından, eş adları güvenli (korumalı) veya güvenli olmayan (korumasız) olarak yayımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="bf491-111">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="bf491-112">PNRP güvenli eş adlarını yanıltmaya karşı korumak için ortak anahtar şifrelemeyi kullanır; Her iki bilgisayar ve hizmet da PNRP ile adlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf491-112">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="bf491-113">Eş adı çözümleme protokolü aşağıdaki özellikleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="bf491-113">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="bf491-114">Dağıtılmış ve neredeyse tamamen sunucusuz.</span><span class="sxs-lookup"><span data-stu-id="bf491-114">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="bf491-115">Sunucular yalnızca önyükleme işlemi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bf491-115">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="bf491-116">Üçüncü tarafların katılımı olmadan güvenli ad yayını.</span><span class="sxs-lookup"><span data-stu-id="bf491-116">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="bf491-117">DNS ad yayınının aksine, PNRP ad yayını anında ve finans maliyeti olmadan olur.</span><span class="sxs-lookup"><span data-stu-id="bf491-117">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="bf491-118">PNRP, eski adreslerin çözümlenmesini önleyen gerçek zamanlı olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bf491-118">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="bf491-119">PNRP aracılığıyla adların çözümlenmesi bilgisayarların ötesinde de hizmetler için ad çözümlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="bf491-119">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="bf491-120">System .net. PeerToPeer ad alanı</span><span class="sxs-lookup"><span data-stu-id="bf491-120">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="bf491-121">PNRP işlevselliği <xref:System.Net.PeerToPeer> .NET Framework sürüm 3,5 içinde ad alanı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bf491-121">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="bf491-122">Kullanılabilir bir PNRP hizmeti ile eş adlarını kaydetmek ve çözümlemek için kullanılabilecek bir tür kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf491-122">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="bf491-123">(PNRP ve özel eşdüzey çözümleyiciler ad alanında belirtilen türler kullanılarak oluşturulabilir ve oluşturulabilir <xref:System.ServiceModel.PeerResolvers> .)</span><span class="sxs-lookup"><span data-stu-id="bf491-123">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="bf491-124">Kullanılabilir bir PNRP hizmeti ile adları kaydettirmek ve çözümlemek için kullanılan temel türler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bf491-124">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="bf491-125"><xref:System.Net.PeerToPeer.Cloud>: Kapsamı dahil olmak üzere kullanılabilir bir PNRP bulutunu açıklayan bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf491-125"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="bf491-126"><xref:System.Net.PeerToPeer.PeerName>: Bir bulut içindeki bir eşi kaydettirmek ve daha sonra çözümlemek için kullanılabilen bir eş adı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf491-126"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="bf491-127"><xref:System.Net.PeerToPeer.PeerNameRecord>: Eşin iletişim kurulabileceği ağ uç noktalarını içeren bir eş için kayıt bilgilerini içeren, PNRP bulutundaki kaydı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf491-127"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="bf491-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Eş adı kaydını başlatma ve durdurma yöntemleri de dahil olmak üzere bir eş adı için kayıt işlemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf491-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="bf491-129"><xref:System.Net.PeerToPeer.PeerNameResolver>: Çözüm için hem zaman uyumlu hem de zaman uyumsuz yöntemler de dahil olmak üzere, eş adı ağ uç noktaları için çözümleme işlemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf491-129"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf491-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf491-130">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="bf491-131">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="bf491-131">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
