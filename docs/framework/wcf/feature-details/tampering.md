---
title: Tampering (Kurcalama)
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: c2b0cae1dc57fac486122ca17fc8109ffe62f77d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249806"
---
# <a name="tampering"></a><span data-ttu-id="6a47d-102">Tampering (Kurcalama)</span><span class="sxs-lookup"><span data-stu-id="6a47d-102">Tampering</span></span>

<span data-ttu-id="6a47d-103">*Izinsiz değişiklik* , bir iletiyi değiştirme veya bir iletinin teslim etme veya değiştirilmiş iletiyi amaçlanan bir amaç dışında bir amaç için kullanma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="6a47d-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="6a47d-104">WS-Addressing devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="6a47d-104">Do Not Disable WS-Addressing</span></span>  

 <span data-ttu-id="6a47d-105">WS-Addressing belirtimi her ileti üzerinde adres üst bilgileri sağlar ve ileti alıcısının ileti gönderisini doğrulamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6a47d-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="6a47d-106">Özelliğini olarak ayarlayarak bu özelliği devre dışı bırakabilirsiniz <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="6a47d-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="6a47d-107">Güvenlik modu Ileti olarak ayarlandığında ve WS-Addressing devre dışı bırakılmışsa, bir saldırgan istemciden bir istek alabilir ve başka bir hizmete gönderebilir ve ikinci hizmet, iletinin özgün istemciden geldiğini algılamaktır.</span><span class="sxs-lookup"><span data-stu-id="6a47d-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="6a47d-108">Aslında, ilk hizmet ikinci hizmetle görüşülürken istemci olduğunu önedebilir.</span><span class="sxs-lookup"><span data-stu-id="6a47d-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="6a47d-109">Bunu azaltmak için, <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğini hiçbir şekilde ayarlayın <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> ve <xref:System.ServiceModel.Channels.MessageVersion> özelliğini ' a ayarlayan static özelliği gibi ' i kullanmaktan kaçının <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="6a47d-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a47d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a47d-110">See also</span></span>

- [<span data-ttu-id="6a47d-111">Güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="6a47d-111">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="6a47d-112">Bilgilerin Açığa Çıkması</span><span class="sxs-lookup"><span data-stu-id="6a47d-112">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="6a47d-113">Ayrıcalık Yükseltme</span><span class="sxs-lookup"><span data-stu-id="6a47d-113">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="6a47d-114">Hizmet Reddi</span><span class="sxs-lookup"><span data-stu-id="6a47d-114">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="6a47d-115">Desteklenmeyen Senaryolar</span><span class="sxs-lookup"><span data-stu-id="6a47d-115">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="6a47d-116">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="6a47d-116">Replay Attacks</span></span>](replay-attacks.md)
