---
title: Windows Communication Foundation'da Taşımalar
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 6bb8e8b90c26533661684bd403b9ec439f1bb37e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933737"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="8b039-102">Windows Communication Foundation'da Taşımalar</span><span class="sxs-lookup"><span data-stu-id="8b039-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="8b039-103">Kanal yığının en düşük düzey aktarım katmanıdır.</span><span class="sxs-lookup"><span data-stu-id="8b039-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="8b039-104">Windows Communication Foundation (WCF) kullanılan ana taşımalar, HTTP, HTTPS, TCP ve adlandırılmış kanallar ' dir.</span><span class="sxs-lookup"><span data-stu-id="8b039-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="8b039-105">Bu bölümdeki konular arasında bu taşımaları seçme, aktarım yapılandırma ve ayarlama özellikleri ayarlama açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b039-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="8b039-106">WCF ek taşımalar içerir.</span><span class="sxs-lookup"><span data-stu-id="8b039-106">WCF includes additional transports.</span></span> <span data-ttu-id="8b039-107">Message Queuing (MSMQ olarak da bilinir) taşıma hakkında daha fazla bilgi için bkz. [kuyruklar ve güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="8b039-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="8b039-108">Eşler arası taşıma hakkında daha fazla bilgi için bkz. [eşler arası ağ](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="8b039-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b039-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8b039-109">In This Section</span></span>  
 [<span data-ttu-id="8b039-110">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="8b039-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="8b039-111">Üç ana aktarımları ve bir seçerken konularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b039-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="8b039-112">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="8b039-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="8b039-113">Bir ileti kodlama bağlama öğesi seçerken dikkate alınması gereken faktörler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b039-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="8b039-114">İleti Aktarma Akışı</span><span class="sxs-lookup"><span data-stu-id="8b039-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="8b039-115">Akış yapmak için Aktarım katmanı yapılandırılması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b039-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="8b039-116">HTTP ve HTTPS Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8b039-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="8b039-117">HTTP ve HTTPS aktarım bağlama öğelerinin yapılandırılması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b039-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="8b039-118">Nasıl yapılır: WCF URL ayırmayı kısıtlı ayırma ile değiştirme</span><span class="sxs-lookup"><span data-stu-id="8b039-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="8b039-119">Kısıtlı WCFURL ayırmaları kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b039-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="8b039-120">Taşıma Kotaları</span><span class="sxs-lookup"><span data-stu-id="8b039-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="8b039-121">Aktarım katmanında kullanılabilir kotaları ayarlama konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b039-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="8b039-122">NAT ve Güvenlik Duvarlarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="8b039-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="8b039-123">Aktarım katmanı gönderilen ya da bir güvenlik duvarının arkasındaki veya ağ adresi çevirisi (NAT) olduğunda alınan iletileri yapılandırılması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b039-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="8b039-124">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="8b039-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="8b039-125">Net.TCP bağlantı noktası paylaşımı bileşen WCF kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b039-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8b039-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8b039-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="8b039-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8b039-127">Related Sections</span></span>  
 [<span data-ttu-id="8b039-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8b039-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="8b039-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8b039-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
