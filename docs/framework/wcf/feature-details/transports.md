---
description: 'Daha fazla bilgi edinin: Windows Communication Foundation aktarımları'
title: Windows Communication Foundation'da Taşımalar
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: e80a1730de107c0433949b7d476944f38e386702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752619"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="9d04e-103">Windows Communication Foundation'da Taşımalar</span><span class="sxs-lookup"><span data-stu-id="9d04e-103">Transports in Windows Communication Foundation</span></span>

<span data-ttu-id="9d04e-104">Aktarım katmanı, kanal yığınının en düşük düzeyindedir.</span><span class="sxs-lookup"><span data-stu-id="9d04e-104">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="9d04e-105">Windows Communication Foundation (WCF) ' de kullanılan ana aktarımlar HTTP, HTTPS, TCP ve adlandırılmış kanallardır.</span><span class="sxs-lookup"><span data-stu-id="9d04e-105">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="9d04e-106">Bu bölümdeki konular, bu aktarımlar arasında seçim yapma, taşımayı yapılandırma ve ayarlama özelliklerini ayarlama hakkında tartışın.</span><span class="sxs-lookup"><span data-stu-id="9d04e-106">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="9d04e-107">WCF ek aktarımlar içerir.</span><span class="sxs-lookup"><span data-stu-id="9d04e-107">WCF includes additional transports.</span></span> <span data-ttu-id="9d04e-108">Message Queuing (MSMQ olarak da bilinir) taşıma hakkında daha fazla bilgi için bkz. [Kuyruklar ve güvenilir oturumlar](queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="9d04e-108">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="9d04e-109">Eşler arası aktarım hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="9d04e-109">For information about peer-to-peer transport, see [Peer-to-Peer Networking](peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d04e-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9d04e-110">In This Section</span></span>  

 [<span data-ttu-id="9d04e-111">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="9d04e-111">Choosing a Transport</span></span>](choosing-a-transport.md)  
 <span data-ttu-id="9d04e-112">Üç ana aktarım ve seçim ile ilgili dikkat edilmesi gerekenler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d04e-112">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="9d04e-113">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="9d04e-113">Choosing a Message Encoder</span></span>](choosing-a-message-encoder.md)  
 <span data-ttu-id="9d04e-114">İleti kodlama bağlama öğesi seçerken göz önünde bulundurmanız gereken faktörleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d04e-114">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="9d04e-115">İleti Aktarma Akışı</span><span class="sxs-lookup"><span data-stu-id="9d04e-115">Streaming Message Transfer</span></span>](streaming-message-transfer.md)  
 <span data-ttu-id="9d04e-116">Akış yapmak için aktarım katmanının nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d04e-116">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="9d04e-117">HTTP ve HTTPS Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9d04e-117">Configuring HTTP and HTTPS</span></span>](configuring-http-and-https.md)  
 <span data-ttu-id="9d04e-118">HTTP ve HTTPS aktarım bağlama öğelerinin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d04e-118">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="9d04e-119">Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme</span><span class="sxs-lookup"><span data-stu-id="9d04e-119">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="9d04e-120">WCFURL kısıtlı ayırmaları kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d04e-120">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="9d04e-121">Taşıma Kotaları</span><span class="sxs-lookup"><span data-stu-id="9d04e-121">Transport Quotas</span></span>](transport-quotas.md)  
 <span data-ttu-id="9d04e-122">Aktarım katmanında kullanılabilir kotaları ayarlamayla ilgili önemli noktaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d04e-122">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="9d04e-123">NAT ve Güvenlik Duvarlarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="9d04e-123">Working with NATs and Firewalls</span></span>](working-with-nats-and-firewalls.md)  
 <span data-ttu-id="9d04e-124">Bir güvenlik duvarının arkasında veya ağ adresi çevirisi (NAT) olduğunda iletiler gönderildiğinde veya alındığında aktarım katmanının nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d04e-124">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="9d04e-125">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="9d04e-125">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)  
 <span data-ttu-id="9d04e-126">WCF 'nin net. TCP bağlantı noktası paylaşma bileşeninin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d04e-126">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9d04e-127">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9d04e-127">Reference</span></span>  

 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="9d04e-128">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9d04e-128">Related Sections</span></span>  

 [<span data-ttu-id="9d04e-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9d04e-129">Bindings</span></span>](bindings.md)  
  
 [<span data-ttu-id="9d04e-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="9d04e-130">Extending Bindings</span></span>](../extending/extending-bindings.md)
