---
title: Uygulama geliştirmede PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0f86b2569b9d4864586a0a7daea0ae5d3b901fd4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205271"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="7cab1-102">Uygulama geliştirmede PNRP</span><span class="sxs-lookup"><span data-stu-id="7cab1-102">PNRP in Application Development</span></span>
<span data-ttu-id="7cab1-103">Windows Vista'da adı yayını ve çözümleme işlevleri bir Basitleştirilmiş PNRP uygulama programlama arabirimiyle (API) ağ uygulamalarına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7cab1-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="7cab1-104">Eş Adı Çözümleme Protokolü'nü uygulama</span><span class="sxs-lookup"><span data-stu-id="7cab1-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="7cab1-105">Basitleştirilmiş PNRP API ile bulut açıkça adı ve adreslerini kaydetmek için belirtilmedi; PNRP bileşeni, uygun bulut birleştirme ve bulutlarda yayımlamak için adresleri otomatik olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="7cab1-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="7cab1-106">Son derece Basitleştirilmiş PNRP ad çözümlemesi için Windows Vista'da, PNRP adları artık Windows Sockets işlevi getaddrinfo() tümleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7cab1-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="7cab1-107">PNRP bir IPv6 adresi için bir ad çözümlemede kullanmak için uygulamaları getaddrinfo() işlevi tam olarak nitelikli etki alanı adı (FQDN) name.prnp.net çözümlemek için kullanabilir hangi çözümlenen Eş adı addır.</span><span class="sxs-lookup"><span data-stu-id="7cab1-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="7cab1-108">Windows Vista'da ayrılmış olarak etki alanı PNRP ad çözümlemesi için pnrp.net etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="7cab1-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="7cab1-109">İleti PeerToPeer uygulamalar arasında geçirme PeerChannel'a ve WCF gibi temel mimarileri tarafından işlenen hala [büyük veriler ve akış](https://go.microsoft.com/fwlink/?LinkID=179652).</span><span class="sxs-lookup"><span data-stu-id="7cab1-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](https://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cab1-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7cab1-110">See Also</span></span>  
 <xref:System.Net.PeerToPeer>
