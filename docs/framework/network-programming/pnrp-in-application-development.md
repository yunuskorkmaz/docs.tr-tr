---
title: Uygulama Geliştirmede PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: 7c59b2be8384c8f8cc6bbdc4546a678cfe1c538d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263197"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="0f89a-102">Uygulama Geliştirmede PNRP</span><span class="sxs-lookup"><span data-stu-id="0f89a-102">PNRP in Application Development</span></span>

<span data-ttu-id="0f89a-103">Windows Vista 'da, ağ uygulamaları basitleştirilmiş bir PNRP uygulama programlama arabirimi (API) aracılığıyla ad yayınına ve çözüm işlevlerine erişebilirler.</span><span class="sxs-lookup"><span data-stu-id="0f89a-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="0f89a-104">Eş adı çözümleme protokolünü uygulama</span><span class="sxs-lookup"><span data-stu-id="0f89a-104">Implementing the Peer Name Resolution Protocol</span></span>  

 <span data-ttu-id="0f89a-105">Basitleştirilmiş PNRP API 'SI ile, bulutlar adı ve adresleri kaydetmek için açıkça belirtilmez; PNRP bileşeni, katılacak uygun bulutları ve bulutlar içinde yayımlanacak adresleri otomatik olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="0f89a-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="0f89a-106">Windows Vista 'da yüksek oranda Basitleştirilmiş PNRP ad çözümlemesi için, PNRP adları artık GetAddrInfo () Windows Yuvaları işleviyle tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="0f89a-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="0f89a-107">Bir adı bir IPv6 adresine çözümlemek üzere PNRP kullanmak için, uygulamalar, ad eş adı olan tam etki alanı adı (FQDN) name.prnp.net çözümlemek için GetAddrInfo () işlevini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0f89a-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="0f89a-108">Pnrp.net etki alanı, Windows Vista 'da PNRP ad çözümlemesi için ayrılmış bir etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="0f89a-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="0f89a-109">PeerToPeer uygulamaları arasında geçen ileti, hala PeerChannel ve WCF [büyük veri ve akış](../wcf/feature-details/large-data-and-streaming.md)gibi temel mimarilerde işlenir.</span><span class="sxs-lookup"><span data-stu-id="0f89a-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f89a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f89a-110">See also</span></span>

- <xref:System.Net.PeerToPeer>
