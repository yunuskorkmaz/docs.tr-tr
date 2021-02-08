---
description: 'Daha fazla bilgi edinin: değişiklik'
title: Tampering (Kurcalama)
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 3b14fef66e5c98737d8d2f6a8b889f16c83020f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793330"
---
# <a name="tampering"></a><span data-ttu-id="75fd6-103">Tampering (Kurcalama)</span><span class="sxs-lookup"><span data-stu-id="75fd6-103">Tampering</span></span>

<span data-ttu-id="75fd6-104">*Izinsiz değişiklik* , bir iletiyi değiştirme veya bir iletinin teslim etme veya değiştirilmiş iletiyi amaçlanan bir amaç dışında bir amaç için kullanma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="75fd6-104">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="75fd6-105">WS-Addressing devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="75fd6-105">Do Not Disable WS-Addressing</span></span>  

 <span data-ttu-id="75fd6-106">WS-Addressing belirtimi her ileti üzerinde adres üst bilgileri sağlar ve ileti alıcısının ileti gönderisini doğrulamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="75fd6-106">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="75fd6-107">Özelliğini olarak ayarlayarak bu özelliği devre dışı bırakabilirsiniz <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="75fd6-107">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="75fd6-108">Güvenlik modu Ileti olarak ayarlandığında ve WS-Addressing devre dışı bırakılmışsa, bir saldırgan istemciden bir istek alabilir ve başka bir hizmete gönderebilir ve ikinci hizmet, iletinin özgün istemciden geldiğini algılamaktır.</span><span class="sxs-lookup"><span data-stu-id="75fd6-108">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="75fd6-109">Aslında, ilk hizmet ikinci hizmetle görüşülürken istemci olduğunu önedebilir.</span><span class="sxs-lookup"><span data-stu-id="75fd6-109">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="75fd6-110">Bunu azaltmak için, <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğini hiçbir şekilde ayarlayın <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> ve <xref:System.ServiceModel.Channels.MessageVersion> özelliğini ' a ayarlayan static özelliği gibi ' i kullanmaktan kaçının <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="75fd6-110">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75fd6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75fd6-111">See also</span></span>

- [<span data-ttu-id="75fd6-112">Güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="75fd6-112">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="75fd6-113">Bilgilerin Açığa Çıkması</span><span class="sxs-lookup"><span data-stu-id="75fd6-113">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="75fd6-114">Ayrıcalık Yükseltme</span><span class="sxs-lookup"><span data-stu-id="75fd6-114">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="75fd6-115">Hizmet Reddi</span><span class="sxs-lookup"><span data-stu-id="75fd6-115">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="75fd6-116">Desteklenmeyen Senaryolar</span><span class="sxs-lookup"><span data-stu-id="75fd6-116">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="75fd6-117">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="75fd6-117">Replay Attacks</span></span>](replay-attacks.md)
