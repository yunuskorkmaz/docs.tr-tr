---
title: İzinsiz Değişiklik
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 86446778008782c733629ef94e6b192501bee2da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607192"
---
# <a name="tampering"></a><span data-ttu-id="be373-102">İzinsiz Değişiklik</span><span class="sxs-lookup"><span data-stu-id="be373-102">Tampering</span></span>
<span data-ttu-id="be373-103">*İzinsiz* bir ileti ya da ileti teslimini değiştirme ve ne için tasarlanmıştı dışında bir amaç için değiştirilmiş bir iletiyi kullanarak, işlemidir.</span><span class="sxs-lookup"><span data-stu-id="be373-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="be373-104">WS-Addressing devre dışı bırakmayın</span><span class="sxs-lookup"><span data-stu-id="be373-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="be373-105">WS-Addressing belirtimi, bir ileti alıcı, iletiyi gönderenin doğrulamak izin verme her ileti üzerinde adres üst bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="be373-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="be373-106">Ayarlayarak bu özelliği devre dışı bırakabilirsiniz <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğini <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="be373-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="be373-107">İleti güvenlik modunu ayarlandığında ve WS-Addressing devre dışı bırakılırsa, bir saldırgan, bir istemciden bir isteğin tamamlanması ve başka bir hizmete göndermek ve ikinci hizmet iletiyi özgün istemciden gelen algılama hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="be373-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="be373-108">Aslında, ikinci hizmete konuşurken bir istemci olduğunu ilk hizmeti anlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be373-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="be373-109">Bunu azaltmak için hiçbir zaman ayarlamak <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğini <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>ve kullanmaktan kaçının <xref:System.ServiceModel.Channels.MessageVersion>, statik gibi <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> ayarlar özelliği <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğini <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="be373-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be373-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be373-110">See also</span></span>
- [<span data-ttu-id="be373-111">Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="be373-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [<span data-ttu-id="be373-112">Bilgilerin Açığa Çıkması</span><span class="sxs-lookup"><span data-stu-id="be373-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [<span data-ttu-id="be373-113">Ayrıcalıkların Yükseltilmesi</span><span class="sxs-lookup"><span data-stu-id="be373-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [<span data-ttu-id="be373-114">Hizmet Reddi</span><span class="sxs-lookup"><span data-stu-id="be373-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [<span data-ttu-id="be373-115">Desteklenmeyen Senaryolar</span><span class="sxs-lookup"><span data-stu-id="be373-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [<span data-ttu-id="be373-116">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="be373-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
