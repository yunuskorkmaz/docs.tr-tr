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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62eb27919e762004667b3d5179c35cb04d9a9422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="040ff-102">Windows Communication Foundation'da Taşımalar</span><span class="sxs-lookup"><span data-stu-id="040ff-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="040ff-103">Aktarım katmanı kanal yığının en düşük düzeyinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="040ff-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="040ff-104">Kullanılan ana taşımalar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HTTP, HTTPS, TCP ve adlandırılmış kanallar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="040ff-104">The main transports used in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="040ff-105">Bu bölümdeki konular arasında bu taşımaları seçme, taşıma yapılandırma ve ayarlama özellikleri ayarlama tartışın.</span><span class="sxs-lookup"><span data-stu-id="040ff-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="040ff-106">ek taşımalar içerir.</span><span class="sxs-lookup"><span data-stu-id="040ff-106"> includes additional transports.</span></span> <span data-ttu-id="040ff-107">Message Queuing (MSMQ olarak da bilinir) taşıma hakkında daha fazla bilgi için bkz: [kuyruklar ve güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="040ff-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="040ff-108">Eşler arası taşıma hakkında daha fazla bilgi için bkz: [eşler arası ağ](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="040ff-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="040ff-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="040ff-109">In This Section</span></span>  
 [<span data-ttu-id="040ff-110">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="040ff-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="040ff-111">Üç ana aktarımları ve seçerek de ilgili önemli noktalar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="040ff-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="040ff-112">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="040ff-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="040ff-113">Bir ileti kodlama bağlama öğesi seçerken göz önüne almanız gereken faktörler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="040ff-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="040ff-114">İleti Aktarma Akışı</span><span class="sxs-lookup"><span data-stu-id="040ff-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="040ff-115">Akış yapmak için Aktarım katmanı yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="040ff-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="040ff-116">HTTP ve HTTPS Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="040ff-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="040ff-117">Bağlama öğeleri HTTP ve HTTPS taşıma yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="040ff-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="040ff-118">Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme</span><span class="sxs-lookup"><span data-stu-id="040ff-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="040ff-119">Nasıl kullanılacağını açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL ayırmalarını kısıtlanmış.</span><span class="sxs-lookup"><span data-stu-id="040ff-119">Describes how to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL restricted reservations.</span></span>  
  
 [<span data-ttu-id="040ff-120">Taşıma Kotaları</span><span class="sxs-lookup"><span data-stu-id="040ff-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="040ff-121">Aktarım katmanında kullanılabilir kotaları ayarlama konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="040ff-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="040ff-122">NAT ve Güvenlik Duvarlarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="040ff-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="040ff-123">İletileri gönderilen veya alınan bir güvenlik duvarının arkasında veya ağ adresi çevirisi (NAT) mevcut olduğunda, Aktarım katmanı yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="040ff-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="040ff-124">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="040ff-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="040ff-125">Net.TCP bağlantı noktası paylaşma bileşeninin kullanmayı açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="040ff-125">Describes how to use the Net.TCP Port Sharing component of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="040ff-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="040ff-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="040ff-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="040ff-127">Related Sections</span></span>  
 [<span data-ttu-id="040ff-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="040ff-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="040ff-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="040ff-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
