---
title: Windows Communication Foundation'da Taşımalar
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 077d63d8038b245a68083611897c1e6c68971071
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598677"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="5b331-102">Windows Communication Foundation'da Taşımalar</span><span class="sxs-lookup"><span data-stu-id="5b331-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="5b331-103">Aktarım katmanı, kanal yığınının en düşük düzeyindedir.</span><span class="sxs-lookup"><span data-stu-id="5b331-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="5b331-104">Windows Communication Foundation (WCF) ' de kullanılan ana aktarımlar HTTP, HTTPS, TCP ve adlandırılmış kanallardır.</span><span class="sxs-lookup"><span data-stu-id="5b331-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="5b331-105">Bu bölümdeki konular, bu aktarımlar arasında seçim yapma, taşımayı yapılandırma ve ayarlama özelliklerini ayarlama hakkında tartışın.</span><span class="sxs-lookup"><span data-stu-id="5b331-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="5b331-106">WCF ek aktarımlar içerir.</span><span class="sxs-lookup"><span data-stu-id="5b331-106">WCF includes additional transports.</span></span> <span data-ttu-id="5b331-107">Message Queuing (MSMQ olarak da bilinir) taşıma hakkında daha fazla bilgi için bkz. [Kuyruklar ve güvenilir oturumlar](queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="5b331-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="5b331-108">Eşler arası aktarım hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="5b331-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b331-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5b331-109">In This Section</span></span>  
 [<span data-ttu-id="5b331-110">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="5b331-110">Choosing a Transport</span></span>](choosing-a-transport.md)  
 <span data-ttu-id="5b331-111">Üç ana aktarım ve seçim ile ilgili dikkat edilmesi gerekenler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b331-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="5b331-112">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="5b331-112">Choosing a Message Encoder</span></span>](choosing-a-message-encoder.md)  
 <span data-ttu-id="5b331-113">İleti kodlama bağlama öğesi seçerken göz önünde bulundurmanız gereken faktörleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="5b331-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="5b331-114">İleti Aktarma Akışı</span><span class="sxs-lookup"><span data-stu-id="5b331-114">Streaming Message Transfer</span></span>](streaming-message-transfer.md)  
 <span data-ttu-id="5b331-115">Akış yapmak için aktarım katmanının nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5b331-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="5b331-116">HTTP ve HTTPS Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5b331-116">Configuring HTTP and HTTPS</span></span>](configuring-http-and-https.md)  
 <span data-ttu-id="5b331-117">HTTP ve HTTPS aktarım bağlama öğelerinin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5b331-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="5b331-118">Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme</span><span class="sxs-lookup"><span data-stu-id="5b331-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="5b331-119">WCFURL kısıtlı ayırmaları kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="5b331-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="5b331-120">Taşıma Kotaları</span><span class="sxs-lookup"><span data-stu-id="5b331-120">Transport Quotas</span></span>](transport-quotas.md)  
 <span data-ttu-id="5b331-121">Aktarım katmanında kullanılabilir kotaları ayarlamayla ilgili önemli noktaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="5b331-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="5b331-122">NAT ve Güvenlik Duvarlarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="5b331-122">Working with NATs and Firewalls</span></span>](working-with-nats-and-firewalls.md)  
 <span data-ttu-id="5b331-123">Bir güvenlik duvarının arkasında veya ağ adresi çevirisi (NAT) olduğunda iletiler gönderildiğinde veya alındığında aktarım katmanının nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5b331-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="5b331-124">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="5b331-124">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)  
 <span data-ttu-id="5b331-125">WCF 'nin net. TCP bağlantı noktası paylaşma bileşeninin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5b331-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5b331-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="5b331-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="5b331-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="5b331-127">Related Sections</span></span>  
 [<span data-ttu-id="5b331-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5b331-128">Bindings</span></span>](bindings.md)  
  
 [<span data-ttu-id="5b331-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="5b331-129">Extending Bindings</span></span>](../extending/extending-bindings.md)
