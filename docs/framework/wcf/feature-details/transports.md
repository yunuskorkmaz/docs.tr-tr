---
title: "Windows Communication Foundation'da Taşımalar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 115e2a69c7d990c7d4c59634644fb557e83ad405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="71b02-102">Windows Communication Foundation'da Taşımalar</span><span class="sxs-lookup"><span data-stu-id="71b02-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="71b02-103">Aktarım katmanı kanal yığının en düşük düzeyinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="71b02-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="71b02-104">Kullanılan ana taşımalar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HTTP, HTTPS, TCP ve adlandırılmış kanallar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="71b02-104">The main transports used in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="71b02-105">Bu bölümdeki konular arasında bu taşımaları seçme, taşıma yapılandırma ve ayarlama özellikleri ayarlama tartışın.</span><span class="sxs-lookup"><span data-stu-id="71b02-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="71b02-106">ek taşımalar içerir.</span><span class="sxs-lookup"><span data-stu-id="71b02-106"> includes additional transports.</span></span> <span data-ttu-id="71b02-107">Message Queuing (MSMQ olarak da bilinir) taşıma hakkında daha fazla bilgi için bkz: [kuyruklar ve güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="71b02-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="71b02-108">Eşler arası taşıma hakkında daha fazla bilgi için bkz: [eşler arası ağ](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="71b02-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71b02-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="71b02-109">In This Section</span></span>  
 [<span data-ttu-id="71b02-110">Taşıma seçme</span><span class="sxs-lookup"><span data-stu-id="71b02-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="71b02-111">Üç ana aktarımları ve seçerek de ilgili önemli noktalar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="71b02-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="71b02-112">İleti Kodlayıcı seçme</span><span class="sxs-lookup"><span data-stu-id="71b02-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="71b02-113">Bir ileti kodlama bağlama öğesi seçerken göz önüne almanız gereken faktörler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71b02-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="71b02-114">İleti aktarma akışı</span><span class="sxs-lookup"><span data-stu-id="71b02-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="71b02-115">Akış yapmak için Aktarım katmanı yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="71b02-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="71b02-116">HTTP ve HTTPS yapılandırma</span><span class="sxs-lookup"><span data-stu-id="71b02-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="71b02-117">Bağlama öğeleri HTTP ve HTTPS taşıma yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="71b02-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="71b02-118">Nasıl yapılır: WCF URL ayırmayı kısıtlı ayırma ile değiştirme</span><span class="sxs-lookup"><span data-stu-id="71b02-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="71b02-119">Nasıl kullanılacağını açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL ayırmalarını kısıtlanmış.</span><span class="sxs-lookup"><span data-stu-id="71b02-119">Describes how to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL restricted reservations.</span></span>  
  
 [<span data-ttu-id="71b02-120">Taşıma kotaları</span><span class="sxs-lookup"><span data-stu-id="71b02-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="71b02-121">Aktarım katmanında kullanılabilir kotaları ayarlama konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71b02-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="71b02-122">NAT ve güvenlik duvarları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="71b02-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="71b02-123">İletileri gönderilen veya alınan bir güvenlik duvarının arkasında veya ağ adresi çevirisi (NAT) mevcut olduğunda, Aktarım katmanı yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="71b02-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="71b02-124">Net.TCP bağlantı noktası paylaşımı</span><span class="sxs-lookup"><span data-stu-id="71b02-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="71b02-125">Net.TCP bağlantı noktası paylaşma bileşeninin kullanmayı açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71b02-125">Describes how to use the Net.TCP Port Sharing component of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="71b02-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="71b02-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="71b02-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="71b02-127">Related Sections</span></span>  
 [<span data-ttu-id="71b02-128">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="71b02-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="71b02-129">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="71b02-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
