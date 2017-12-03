---
title: "İzinsiz Değişiklik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 96ab38de1fb2a932fefd4e37cbfab3d9bfbea616
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="tampering"></a><span data-ttu-id="7ebe0-102">İzinsiz Değişiklik</span><span class="sxs-lookup"><span data-stu-id="7ebe0-102">Tampering</span></span>
<span data-ttu-id="7ebe0-103">*İzinsiz* bir ileti ya da ileti teslimini değiştirmeyi ve ne için tasarlanmıştır dışında bir amaç için değiştirilmiş iletiyi kullanarak, işlemidir.</span><span class="sxs-lookup"><span data-stu-id="7ebe0-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="7ebe0-104">WS-adresleme devre dışı bırakmayın</span><span class="sxs-lookup"><span data-stu-id="7ebe0-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="7ebe0-105">WS-adresleme belirtimi, iletiyi gönderenin doğrulamak bir ileti alıcısı izin vererek her ileti için adres üstbilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ebe0-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="7ebe0-106">Ayarlayarak bu özelliği devre dışı bırakabilirsiniz <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğine <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ebe0-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="7ebe0-107">Güvenlik modu iletiye ayarlandığında ve WS adresleme devre dışı bırakılırsa, bir saldırgan, bir istemciden bir isteğin tamamlanması ve başka bir hizmete göndermek ve ikinci hizmet özgün istemciden gelen ileti algılama hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="7ebe0-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="7ebe0-108">Gerçekte, ilk hizmet, ikinci hizmete konuşurken istemci olduğunu içeriğini.</span><span class="sxs-lookup"><span data-stu-id="7ebe0-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="7ebe0-109">Bu durumu iyileştirmek için hiçbir zaman ayarlamak <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğine <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>ve kullanmaktan kaçının <xref:System.ServiceModel.Channels.MessageVersion>, statik gibi <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> ayarlar özelliği <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğine <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ebe0-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ebe0-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ebe0-110">See Also</span></span>  
 [<span data-ttu-id="7ebe0-111">Güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="7ebe0-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="7ebe0-112">Bilgilerin açığa çıkmasına</span><span class="sxs-lookup"><span data-stu-id="7ebe0-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="7ebe0-113">Ayrıcalık yükseltme</span><span class="sxs-lookup"><span data-stu-id="7ebe0-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="7ebe0-114">Hizmet reddi</span><span class="sxs-lookup"><span data-stu-id="7ebe0-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="7ebe0-115">Desteklenmeyen senaryolar</span><span class="sxs-lookup"><span data-stu-id="7ebe0-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [<span data-ttu-id="7ebe0-116">Yeniden yürütme saldırıları</span><span class="sxs-lookup"><span data-stu-id="7ebe0-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
