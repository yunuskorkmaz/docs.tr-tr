---
title: Eş Adı Çözümleme Protokolü
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: c8b7b2190349323bf212d816a77f5f7810f6ca2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428216"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="24a35-102">Eş Adı Çözümleme Protokolü</span><span class="sxs-lookup"><span data-stu-id="24a35-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="24a35-103">Eşler arası ortamlarda, eşler birbirlerinin ağ konumlarını (adresler, protokoller ve bağlantı noktaları) adlardan veya diğer tanımlayıcıtürlerinden çözmek için belirli ad çözümleme sistemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="24a35-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="24a35-104">Geçmişte, eş adı çözümlemesi doğal olarak geçici bağlantı nın yanı sıra Etki Alanı Adı Sistemi (DNS) içindeki diğer eksiklikler tarafından karmaşık hale gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="24a35-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="24a35-105">Microsoft® Windows® Eşler Arası Ağ platformu, bu sorunu önce Windows XP için geliştirilen ve daha sonra yükseltilmiş güvenli, ölçeklenebilir ve dinamik bir ad kaydı ve ad çözümleme protokolü olan Eş Adı Çözümleme Protokolü (PNRP) ile çözer Windows Vista™.</span><span class="sxs-lookup"><span data-stu-id="24a35-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="24a35-106">PNRP, geleneksel ad çözümleme sistemlerinden çok farklı çalışır ve uygulama geliştiricileri için heyecan verici yeni olanaklar sunar.</span><span class="sxs-lookup"><span data-stu-id="24a35-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="24a35-107">PNRP ile, eş adları makineye veya makinedeki tek tek uygulamalara veya hizmetlere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="24a35-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="24a35-108">Eş adı çözümlemesi bir adres, bağlantı noktası ve büyük olasılıkla genişletilmiş bir yük içerir.</span><span class="sxs-lookup"><span data-stu-id="24a35-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="24a35-109">Bu sistemin yararları arasında hata toleransı, darboğaz yok ve eski adresleri asla döndürmeyecek ad çözünürlükleri yer almaktadır; protokolü mobil kullanıcıların yerini bulmak için mükemmel bir çözüm haline getirir.</span><span class="sxs-lookup"><span data-stu-id="24a35-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="24a35-110">Güvenlik açısından, eş adları güvenli (korumalı) veya güvenli olmayan (korumasız) olarak yayımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="24a35-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="24a35-111">PNRP, güvenli eş adlarını sızdırmaya karşı korumak için ortak anahtar şifrelemesini kullanır; hem bilgisayarlar hem de hizmetler PNRP ile adlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="24a35-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="24a35-112">Eş Adı Çözümleme Protokolü aşağıdaki özellikleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="24a35-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="24a35-113">Dağıtılmış ve neredeyse tamamen sunucusuz.</span><span class="sxs-lookup"><span data-stu-id="24a35-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="24a35-114">Sunucular yalnızca önyükleme işlemi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="24a35-114">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="24a35-115">Üçüncü şahısların katılımı olmadan güvenli ad yayını.</span><span class="sxs-lookup"><span data-stu-id="24a35-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="24a35-116">DNS ad yayınının aksine, PNRP ad yayını anlıktır ve finansal maliyeti yoktur.</span><span class="sxs-lookup"><span data-stu-id="24a35-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="24a35-117">PNRP, eski adreslerin çözümünü engelleyen gerçek zamanlı olarak güncellenir.</span><span class="sxs-lookup"><span data-stu-id="24a35-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="24a35-118">PNRP üzerinden adların çözünürlüğü, hizmetler için ad çözümlemesine de izin vererek bilgisayarların ötesine uzanır.</span><span class="sxs-lookup"><span data-stu-id="24a35-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="24a35-119">System.Net.PeerToPeer ad alanı</span><span class="sxs-lookup"><span data-stu-id="24a35-119">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="24a35-120">PNRP işlevselliği,.NET Framework sürüm 3.5'teki <xref:System.Net.PeerToPeer> ad alanı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24a35-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="24a35-121">Kullanılabilir bir PNRP hizmetiyle eş adlarını kaydetmek ve çözmek için kullanılabilecek bir tür kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="24a35-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="24a35-122">(PNRP ve özel eş çözümleyicileri <xref:System.ServiceModel.PeerResolvers> ad alanında sağlanan türler kullanılarak oluşturulabilir ve anında oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="24a35-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="24a35-123">Kullanılabilir bir PNRP hizmetiyle adları kaydetmek ve çözmek için kullanılan temel türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="24a35-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="24a35-124"><xref:System.Net.PeerToPeer.Cloud>: Kapsamı da dahil olmak üzere kullanılabilir bir PNRP bulutunu açıklayan bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24a35-124"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="24a35-125"><xref:System.Net.PeerToPeer.PeerName>: Bir eşin bulut içinde kaydolması ve daha sonra çözümlemesine yardımcı olmak için kullanılabilecek bir eş adı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24a35-125"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="24a35-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: PNRP bulutundaki, eşin bağlantı kurulabileceği ağ uç noktalarını içeren bir eşin kayıt bilgilerini içeren kaydı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24a35-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="24a35-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Eş adı kaydını başlatma ve durdurma yöntemleri de dahil olmak üzere, eş adı için kayıt işlemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24a35-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="24a35-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Eş adı, çözünürlük için hem senkron hem de eşzamanlı yöntemler de dahil olmak üzere, ağ bitiş noktasına(lar) çözme işlemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24a35-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24a35-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24a35-129">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="24a35-130">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="24a35-130">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
