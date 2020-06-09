---
title: İzinsiz Değişiklik
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: e618ab369a46d403aa8db26c4b472e2be3634785
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600717"
---
# <a name="tampering"></a><span data-ttu-id="de427-102">İzinsiz Değişiklik</span><span class="sxs-lookup"><span data-stu-id="de427-102">Tampering</span></span>
<span data-ttu-id="de427-103">*Izinsiz değişiklik* , bir iletiyi değiştirme veya bir iletinin teslim etme veya değiştirilmiş iletiyi amaçlanan bir amaç dışında bir amaç için kullanma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="de427-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="de427-104">WS-Addressing ' i devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="de427-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="de427-105">WS-Addressing belirtimi, her ileti için adres üst bilgileri sağlar ve ileti alıcısının iletiyi göndereni doğrulamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="de427-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="de427-106">Özelliğini olarak ayarlayarak bu özelliği devre dışı bırakabilirsiniz <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="de427-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="de427-107">Güvenlik modu Ileti olarak ayarlandığında ve WS-Addressing devre dışıysa saldırgan bir istemciden bir istek alabilir ve bu hizmeti başka bir hizmete gönderebilir ve ikinci hizmette iletinin özgün istemciden geldiğini algılamaktan bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="de427-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="de427-108">Aslında, ilk hizmet ikinci hizmetle görüşülürken istemci olduğunu önedebilir.</span><span class="sxs-lookup"><span data-stu-id="de427-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="de427-109">Bunu azaltmak için, <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğini hiçbir şekilde ayarlayın <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> ve <xref:System.ServiceModel.Channels.MessageVersion> özelliğini ' a ayarlayan static özelliği gibi ' i kullanmaktan kaçının <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="de427-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de427-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de427-110">See also</span></span>

- [<span data-ttu-id="de427-111">Güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="de427-111">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="de427-112">Bilgileri Açıklama</span><span class="sxs-lookup"><span data-stu-id="de427-112">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="de427-113">Ayrıcalıkların Yükseltilmesi</span><span class="sxs-lookup"><span data-stu-id="de427-113">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="de427-114">Hizmet Reddi</span><span class="sxs-lookup"><span data-stu-id="de427-114">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="de427-115">Desteklenmeyen Senaryolar</span><span class="sxs-lookup"><span data-stu-id="de427-115">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="de427-116">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="de427-116">Replay Attacks</span></span>](replay-attacks.md)
