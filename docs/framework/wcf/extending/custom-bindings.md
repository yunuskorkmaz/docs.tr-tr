---
title: "Özel Bağlamalar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a3da437f742c46a2229aa00db732b5437ec15e3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="custom-bindings"></a><span data-ttu-id="362a0-102">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="362a0-102">Custom Bindings</span></span>
<span data-ttu-id="362a0-103">Kullanabileceğiniz <xref:System.ServiceModel.Channels.CustomBinding> sistem tarafından sağlanan bağlamalar birini hizmetinizi gereksinimlerini karşılamadığında sınıfı.</span><span class="sxs-lookup"><span data-stu-id="362a0-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="362a0-104">Tüm bağlamaları bağlama öğelerinin sıralı bir kümesinden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="362a0-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="362a0-105">Özel bağlamalar sistem tarafından sağlanan bağlama öğeleri kümesinden oluşturulabilir veya kullanıcı tanımlı özel bağlama öğelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="362a0-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="362a0-106">Özel bağlama öğeleri yeni taşımaları veya bir hizmet uç noktada kodlayıcılar kullanımını etkinleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="362a0-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="362a0-107">Çalışma örnekler için bkz: [özel bağlama örnekleri](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08).</span><span class="sxs-lookup"><span data-stu-id="362a0-107">For working examples, see [Custom Binding Samples](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="362a0-108"> [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="362a0-108"> [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="362a0-109">Özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="362a0-109">Construction of a Custom Binding</span></span>  
 <span data-ttu-id="362a0-110">Özel bağlama kullanılarak oluşturulan <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> bağlama "belirli bir sırada yığılma" öğelerinin bir koleksiyonu oluşturucudan:</span><span class="sxs-lookup"><span data-stu-id="362a0-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="362a0-111">En üstte bir isteğe bağlı olduğu <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> akan sağlayan sınıfı işlemleri.</span><span class="sxs-lookup"><span data-stu-id="362a0-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="362a0-112">Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> bir oturum ve WS-ReliableMessaging belirtiminde tanımlanan mekanizmaları sipariş sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="362a0-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="362a0-113">Bir oturum SOAP ve aktarım aracılar arası.</span><span class="sxs-lookup"><span data-stu-id="362a0-113">A session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="362a0-114">Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.SecurityBindingElement> yetkilendirme, kimlik doğrulama, koruma ve gizliliği gibi güvenlik özellikleri sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="362a0-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>  
  
-   <span data-ttu-id="362a0-115">Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> sahip çift yönlü iletişimi HTTP gibi yerel, desteklemeyen bir Aktarım Protokolü ile iki şekilde çift yönlü iletişim olanağı sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="362a0-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>  
  
-   <span data-ttu-id="362a0-116">Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.OneWayBindingElement>) tek yönlü iletişim sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="362a0-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>  
  
-   <span data-ttu-id="362a0-117">Sonraki aşağıdakilerden biri olabilen bir isteğe bağlı Akış güvenlik bağlama öğedir.</span><span class="sxs-lookup"><span data-stu-id="362a0-117">Next is an optional stream security binding element which can be one of the following.</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="362a0-118">Sonraki gerekli ileti kodlama bağlama öğesi var.</span><span class="sxs-lookup"><span data-stu-id="362a0-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="362a0-119">Kendi ileti Kodlayıcı veya üç ileti kodlama bağlamaları birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="362a0-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 <span data-ttu-id="362a0-120">Pencerenin alt gerekli aktarım öğedir.</span><span class="sxs-lookup"><span data-stu-id="362a0-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="362a0-121">Kendi taşıma veya aşağıdaki aktarım bağlama öğeleriyle birini kullanabilirsiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sağlar:</span><span class="sxs-lookup"><span data-stu-id="362a0-121">You can use your own transport or one of the following transport binding elements [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides:</span></span>  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 <span data-ttu-id="362a0-122">Aşağıdaki tabloda, her katman için seçenekleri özetler.</span><span class="sxs-lookup"><span data-stu-id="362a0-122">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="362a0-123">Katman</span><span class="sxs-lookup"><span data-stu-id="362a0-123">Layer</span></span>|<span data-ttu-id="362a0-124">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="362a0-124">Options</span></span>|<span data-ttu-id="362a0-125">Gerekli</span><span class="sxs-lookup"><span data-stu-id="362a0-125">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="362a0-126">İşlemler</span><span class="sxs-lookup"><span data-stu-id="362a0-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="362a0-127">Hayır</span><span class="sxs-lookup"><span data-stu-id="362a0-127">No</span></span>|  
|<span data-ttu-id="362a0-128">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="362a0-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="362a0-129">Hayır</span><span class="sxs-lookup"><span data-stu-id="362a0-129">No</span></span>|  
|<span data-ttu-id="362a0-130">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="362a0-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="362a0-131">Hayır</span><span class="sxs-lookup"><span data-stu-id="362a0-131">No</span></span>|  
|<span data-ttu-id="362a0-132">Encoding</span><span class="sxs-lookup"><span data-stu-id="362a0-132">Encoding</span></span>|<span data-ttu-id="362a0-133">İkili, ileti iletim en iyi duruma getirme mekanizmasını (MTOM) özel bir metin</span><span class="sxs-lookup"><span data-stu-id="362a0-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="362a0-134">Evet</span><span class="sxs-lookup"><span data-stu-id="362a0-134">Yes</span></span>|  
|<span data-ttu-id="362a0-135">Taşıma</span><span class="sxs-lookup"><span data-stu-id="362a0-135">Transport</span></span>|<span data-ttu-id="362a0-136">TCP, HTTP, HTTPS, adlandırılmış kanallar (IPC olarak da bilinir) eşler arası (P2P), Message Queuing (MSMQ olarak da bilinir), özel</span><span class="sxs-lookup"><span data-stu-id="362a0-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="362a0-137">Evet</span><span class="sxs-lookup"><span data-stu-id="362a0-137">Yes</span></span>|  
  
 <span data-ttu-id="362a0-138">Ayrıca, kendi bağlama öğeleri tanımlamak ve herhangi bir önceki tanımlı katmanlar arasında ekleyin.</span><span class="sxs-lookup"><span data-stu-id="362a0-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="362a0-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="362a0-139">See Also</span></span>  
 [<span data-ttu-id="362a0-140">Uç Nokta Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="362a0-140">Endpoint Creation Overview</span></span>](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="362a0-141">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="362a0-141">Using Bindings to Configure Services and Clients</span></span>](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="362a0-142">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="362a0-142">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="362a0-143">Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="362a0-143">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [<span data-ttu-id="362a0-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="362a0-144">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="362a0-145">Özel Bağlama</span><span class="sxs-lookup"><span data-stu-id="362a0-145">Custom Binding</span></span>](../../../../docs/framework/wcf/samples/custom-binding.md)
