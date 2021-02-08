---
description: Daha fazla bilgi için bkz. uygulama geliştirmede PNRP
title: Uygulama Geliştirmede PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: d3e6e9a329f292d3cde7fb906b28452a4e67fb1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794890"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="9129f-103">Uygulama Geliştirmede PNRP</span><span class="sxs-lookup"><span data-stu-id="9129f-103">PNRP in Application Development</span></span>

<span data-ttu-id="9129f-104">Windows Vista 'da, ağ uygulamaları basitleştirilmiş bir PNRP uygulama programlama arabirimi (API) aracılığıyla ad yayınına ve çözüm işlevlerine erişebilirler.</span><span class="sxs-lookup"><span data-stu-id="9129f-104">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="9129f-105">Eş adı çözümleme protokolünü uygulama</span><span class="sxs-lookup"><span data-stu-id="9129f-105">Implementing the Peer Name Resolution Protocol</span></span>  

 <span data-ttu-id="9129f-106">Basitleştirilmiş PNRP API 'SI ile, bulutlar adı ve adresleri kaydetmek için açıkça belirtilmez; PNRP bileşeni, katılacak uygun bulutları ve bulutlar içinde yayımlanacak adresleri otomatik olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="9129f-106">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="9129f-107">Windows Vista 'da yüksek oranda Basitleştirilmiş PNRP ad çözümlemesi için, PNRP adları artık GetAddrInfo () Windows Yuvaları işleviyle tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="9129f-107">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="9129f-108">Bir adı bir IPv6 adresine çözümlemek üzere PNRP kullanmak için, uygulamalar, ad eş adı olan tam etki alanı adı (FQDN) name.prnp.net çözümlemek için GetAddrInfo () işlevini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9129f-108">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="9129f-109">Pnrp.net etki alanı, Windows Vista 'da PNRP ad çözümlemesi için ayrılmış bir etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="9129f-109">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="9129f-110">PeerToPeer uygulamaları arasında geçen ileti, hala PeerChannel ve WCF [büyük veri ve akış](../wcf/feature-details/large-data-and-streaming.md)gibi temel mimarilerde işlenir.</span><span class="sxs-lookup"><span data-stu-id="9129f-110">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9129f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9129f-111">See also</span></span>

- <xref:System.Net.PeerToPeer>
