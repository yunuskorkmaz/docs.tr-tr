---
title: Eş Adı Çözümleme Protokolü
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: c8b7b2190349323bf212d816a77f5f7810f6ca2c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428216"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="1e5a2-102">Eş Adı Çözümleme Protokolü</span><span class="sxs-lookup"><span data-stu-id="1e5a2-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="1e5a2-103">Eşler arası ortamlarda, eşler, her birinin ağ konumlarını (adresler, protokoller ve bağlantı noktaları) adlarla veya diğer tanımlayıcı türlerinden çözümlemek için belirli ad çözümleme sistemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="1e5a2-104">Geçmişte, eş adı çözümlemesi, etki alanı adı sistemi (DNS) içindeki diğer eksikler tarafından da doğal olarak geçici bağlantı tarafından karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="1e5a2-105">Microsoft® Windows® Eşler arası ağ platformu, ilk olarak Windows XP için geliştirilmiş ve ardından ' de yükseltilen eş adı çözümleme Protokolü (PNRP), güvenli, ölçeklenebilir ve dinamik bir ad kaydı ve ad çözümleme protokolü ile bu sorunu çözer. Windows Vista™.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="1e5a2-106">PNRP geleneksel ad çözümleme sistemlerinden çok farklı çalışır ve uygulama geliştiricileri için heyecan verici yeni olanaklar sunar.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="1e5a2-107">PNRP ile, eş adları makineye veya makinedeki ayrı uygulamalara veya hizmetlere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="1e5a2-108">Eş adı çözümlemesi bir adres, bağlantı noktası ve büyük olasılıkla genişletilmiş bir yük içerir.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="1e5a2-109">Bu sistemin avantajları arasında hata toleransı, performans sorunu olmaması ve hiçbir şekilde eski adresleri döndürmeyecek ad çözümlemeleri dahildir; Protokolü mobil kullanıcıları bulmaya yönelik harika bir çözüm haline getirme.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="1e5a2-110">Güvenlik açısından, eş adları güvenli (korumalı) veya güvenli olmayan (korumasız) olarak yayımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="1e5a2-111">PNRP güvenli eş adlarını yanıltmaya karşı korumak için ortak anahtar şifrelemeyi kullanır; Her iki bilgisayar ve hizmet da PNRP ile adlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="1e5a2-112">Eş adı çözümleme protokolü aşağıdaki özellikleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="1e5a2-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="1e5a2-113">Dağıtılmış ve neredeyse tamamen sunucusuz.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="1e5a2-114">Sunucular yalnızca önyükleme işlemi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-114">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="1e5a2-115">Üçüncü tarafların katılımı olmadan güvenli ad yayını.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="1e5a2-116">DNS ad yayınının aksine, PNRP ad yayını anında ve finans maliyeti olmadan olur.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="1e5a2-117">PNRP, eski adreslerin çözümlenmesini önleyen gerçek zamanlı olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="1e5a2-118">PNRP aracılığıyla adların çözümlenmesi bilgisayarların ötesinde de hizmetler için ad çözümlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="1e5a2-119">System .net. PeerToPeer ad alanı</span><span class="sxs-lookup"><span data-stu-id="1e5a2-119">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="1e5a2-120">PNRP işlevselliği, .NET Framework sürüm 3,5 içinde <xref:System.Net.PeerToPeer> ad alanı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="1e5a2-121">Kullanılabilir bir PNRP hizmeti ile eş adlarını kaydetmek ve çözümlemek için kullanılabilecek bir tür kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="1e5a2-122">(PNRP ve özel eşdüzey çözümleyiciler <xref:System.ServiceModel.PeerResolvers> ad alanında belirtilen türler kullanılarak oluşturulabilir ve oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="1e5a2-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="1e5a2-123">Kullanılabilir bir PNRP hizmeti ile adları kaydettirmek ve çözümlemek için kullanılan temel türler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1e5a2-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="1e5a2-124"><xref:System.Net.PeerToPeer.Cloud>: kapsamı dahil, kullanılabilir bir PNRP bulutunu açıklayan bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-124"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="1e5a2-125"><xref:System.Net.PeerToPeer.PeerName>: bir bulut içindeki bir eşi kaydettirmek ve daha sonra çözümlemek için kullanılabilecek bir eş adı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-125"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="1e5a2-126"><xref:System.Net.PeerToPeer.PeerNameRecord>:, eşe bağlantı kurulabileceği ağ uç noktalarını içeren bir eş için kayıt bilgilerini içeren, PNRP bulutundaki kaydı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="1e5a2-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: eş adı kaydını başlatma ve durdurma yöntemleri de dahil olmak üzere bir eş adı için kayıt işlemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="1e5a2-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: bir eş adı çözümleme için hem zaman uyumlu hem de zaman uyumsuz yöntemler de dahil olmak üzere ağ uç noktaları için çözümleme işlemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5a2-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e5a2-129">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="1e5a2-130">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="1e5a2-130">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
