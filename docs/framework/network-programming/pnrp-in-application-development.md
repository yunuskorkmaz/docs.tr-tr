---
title: Uygulama Geliştirmede PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: 4cd0d739e58cd252213e8d5c16d29cc612338df6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642002"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="9ca91-102">Uygulama Geliştirmede PNRP</span><span class="sxs-lookup"><span data-stu-id="9ca91-102">PNRP in Application Development</span></span>
<span data-ttu-id="9ca91-103">Windows Vista'da adı yayını ve çözümleme işlevleri bir Basitleştirilmiş PNRP uygulama programlama arabirimiyle (API) ağ uygulamalarına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ca91-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="9ca91-104">Eş Adı Çözümleme Protokolü'nü uygulama</span><span class="sxs-lookup"><span data-stu-id="9ca91-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="9ca91-105">Basitleştirilmiş PNRP API ile bulut açıkça adı ve adreslerini kaydetmek için belirtilmedi; PNRP bileşeni, uygun bulut birleştirme ve bulutlarda yayımlamak için adresleri otomatik olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="9ca91-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="9ca91-106">Son derece Basitleştirilmiş PNRP ad çözümlemesi için Windows Vista'da, PNRP adları artık Windows Sockets işlevi getaddrinfo() tümleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9ca91-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="9ca91-107">PNRP bir IPv6 adresi için bir ad çözümlemede kullanmak için uygulamaları getaddrinfo() işlevi tam olarak nitelikli etki alanı adı (FQDN) name.prnp.net çözümlemek için kullanabilir hangi çözümlenen Eş adı addır.</span><span class="sxs-lookup"><span data-stu-id="9ca91-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="9ca91-108">Windows Vista'da ayrılmış olarak etki alanı PNRP ad çözümlemesi için pnrp.net etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="9ca91-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="9ca91-109">İleti PeerToPeer uygulamalar arasında geçirme PeerChannel'a ve WCF gibi temel mimarileri tarafından işlenen hala [büyük veriler ve akış](https://go.microsoft.com/fwlink/?LinkID=179652).</span><span class="sxs-lookup"><span data-stu-id="9ca91-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](https://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca91-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ca91-110">See also</span></span>

- <xref:System.Net.PeerToPeer>
