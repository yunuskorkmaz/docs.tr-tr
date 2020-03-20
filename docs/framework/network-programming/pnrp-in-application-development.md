---
title: Uygulama Geliştirmede PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: f9a408fbd7fbbb77c0fd5208926f4b06fcf23b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428212"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="2fa3c-102">Uygulama Geliştirmede PNRP</span><span class="sxs-lookup"><span data-stu-id="2fa3c-102">PNRP in Application Development</span></span>
<span data-ttu-id="2fa3c-103">Windows Vista'da ağ uygulamaları basitleştirilmiş bir PNRP uygulama programlama arabirimi (API) aracılığıyla ad yayını ve çözüm işlevlerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="2fa3c-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="2fa3c-104">Eş Adı Çözümleme Protokolünün Uygulanması</span><span class="sxs-lookup"><span data-stu-id="2fa3c-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="2fa3c-105">Basitleştirilmiş PNRP API ile bulutlar, adı ve adresleri kaydetmek için açıkça belirtilmemiştir; PNRP bileşeni, katılmak için uygun bulutları ve bulutlar içinde yayımlanacak adresleri otomatik olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="2fa3c-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="2fa3c-106">Windows Vista'da son derece basitleştirilmiş PNRP ad çözümü için, PNRP adları artık getaddrinfo() Windows Soketleri işlevine entegre edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2fa3c-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="2fa3c-107">Bir adı IPv6 adresine çözmek için PNRP'yi kullanmak için, uygulamalar tam nitelikli alan adı (FQDN) name.prnp.net çözmek için getaddrinfo() işlevini kullanabilir ve bu ad eş adı çözümleniyor.</span><span class="sxs-lookup"><span data-stu-id="2fa3c-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="2fa3c-108">pnrp.net etki alanı, PNRP ad çözümü için Windows Vista'da ayrılmış bir etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="2fa3c-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="2fa3c-109">PeerToPeer uygulamaları arasında geçen ileti hala PeerChannel ve WCF [Büyük Veri ve Akış](../wcf/feature-details/large-data-and-streaming.md)gibi temel mimarileri tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="2fa3c-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa3c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fa3c-110">See also</span></span>

- <xref:System.Net.PeerToPeer>
