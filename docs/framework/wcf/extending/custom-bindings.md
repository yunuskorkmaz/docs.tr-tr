---
title: Özel Bağlamalar
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 314409f5ac4ecb4b18f3b8d3f2aeb08a507ec9e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696177"
---
# <a name="custom-bindings"></a><span data-ttu-id="aada5-102">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="aada5-102">Custom Bindings</span></span>
<span data-ttu-id="aada5-103">Kullanabileceğiniz <xref:System.ServiceModel.Channels.CustomBinding> sınıfı, sistem tarafından sağlanan bağlamalar birini hizmetinizin gereksinimlerini karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="aada5-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="aada5-104">Tüm bağlamalar bağlama öğelerinin sıralı bir kümesinden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aada5-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="aada5-105">Özel bağlamalar, sistem tarafından sağlanan bağlama öğeleri kümesinden oluşturulabilir veya kullanıcı tanımlı özel bağlama öğelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="aada5-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="aada5-106">Özel bağlama öğeleri, örneğin, yeni taşıma veya bir hizmet uç noktasında kodlayıcılar kullanımını etkinleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aada5-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="aada5-107">Çalışan örnekler için bkz [özel bağlama örnekleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="aada5-107">For working examples, see [Custom Binding Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span></span> <span data-ttu-id="aada5-108">Daha fazla bilgi için [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="aada5-108">For more information, see [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="aada5-109">Özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="aada5-109">Construction of a Custom Binding</span></span>  
 <span data-ttu-id="aada5-110">Özel bağlama kullanılarak oluşturulur <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> bağlama "belirli bir sırayla dizilir" öğelerinin bir koleksiyondan Oluşturucusu:</span><span class="sxs-lookup"><span data-stu-id="aada5-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
- <span data-ttu-id="aada5-111">En üstünde isteğe bağlı olduğu <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> akmasını sağlar sınıfını işlemler.</span><span class="sxs-lookup"><span data-stu-id="aada5-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>  
  
- <span data-ttu-id="aada5-112">Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> bir oturum ve mekanizmaları WS-ReliableMessaging belirtiminde tanımlanan sıralamasını sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="aada5-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="aada5-113">Bir oturum SOAP ve aktarım aracılar arası.</span><span class="sxs-lookup"><span data-stu-id="aada5-113">A session can cross SOAP and transport intermediaries.</span></span>  
  
- <span data-ttu-id="aada5-114">Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.SecurityBindingElement> yetkilendirme, kimlik doğrulaması, koruma ve gizlilik gibi güvenlik özelliklerini sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="aada5-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>  
  
- <span data-ttu-id="aada5-115">Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> çift yönlü iletişim, gibi HTTP desteği olmayan bir Aktarım Protokolü ile iki şekilde çift yönlü iletişim olanağı sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="aada5-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>  
  
- <span data-ttu-id="aada5-116">Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.OneWayBindingElement>) tek yönlü iletişim sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="aada5-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>  
  
- <span data-ttu-id="aada5-117">Sonraki aşağıdakilerden biri olabilecek bir isteğe bağlı Akış güvenlik bağlama öğesi var.</span><span class="sxs-lookup"><span data-stu-id="aada5-117">Next is an optional stream security binding element which can be one of the following.</span></span>  
  
    - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
- <span data-ttu-id="aada5-118">Sonraki gerekli ileti kodlama bağlama öğesi var.</span><span class="sxs-lookup"><span data-stu-id="aada5-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="aada5-119">Kendi ileti Kodlayıcı veya üç ileti kodlama bağlamaları birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aada5-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>  
  
    - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 <span data-ttu-id="aada5-120">Altta bir gerekli aktarım öğesidir.</span><span class="sxs-lookup"><span data-stu-id="aada5-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="aada5-121">Kendi taşıma veya Windows Communication Foundation (WCF) sağlayan aşağıdaki aktarım bağlama öğeleriyle birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aada5-121">You can use your own transport or one of the following transport binding elements Windows Communication Foundation (WCF) provides:</span></span>  
  
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 <span data-ttu-id="aada5-122">Aşağıdaki tabloda, her katman için seçenekler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="aada5-122">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="aada5-123">Katman</span><span class="sxs-lookup"><span data-stu-id="aada5-123">Layer</span></span>|<span data-ttu-id="aada5-124">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="aada5-124">Options</span></span>|<span data-ttu-id="aada5-125">Gerekli</span><span class="sxs-lookup"><span data-stu-id="aada5-125">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="aada5-126">İşlemler</span><span class="sxs-lookup"><span data-stu-id="aada5-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="aada5-127">Hayır</span><span class="sxs-lookup"><span data-stu-id="aada5-127">No</span></span>|  
|<span data-ttu-id="aada5-128">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="aada5-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="aada5-129">Hayır</span><span class="sxs-lookup"><span data-stu-id="aada5-129">No</span></span>|  
|<span data-ttu-id="aada5-130">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="aada5-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="aada5-131">Hayır</span><span class="sxs-lookup"><span data-stu-id="aada5-131">No</span></span>|  
|<span data-ttu-id="aada5-132">Encoding</span><span class="sxs-lookup"><span data-stu-id="aada5-132">Encoding</span></span>|<span data-ttu-id="aada5-133">İkili, ileti aktarım en iyi duruma getirme mekanizması (MTOM) özel bir metin</span><span class="sxs-lookup"><span data-stu-id="aada5-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="aada5-134">Evet</span><span class="sxs-lookup"><span data-stu-id="aada5-134">Yes</span></span>|  
|<span data-ttu-id="aada5-135">Taşıma</span><span class="sxs-lookup"><span data-stu-id="aada5-135">Transport</span></span>|<span data-ttu-id="aada5-136">TCP, HTTP, HTTPS, adlandırılmış kanallar (IPC olarak da bilinir), eşler arası (P2P), Message Queuing (MSMQ olarak da bilinir), özel</span><span class="sxs-lookup"><span data-stu-id="aada5-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="aada5-137">Evet</span><span class="sxs-lookup"><span data-stu-id="aada5-137">Yes</span></span>|  
  
 <span data-ttu-id="aada5-138">Ayrıca, kendi bağlama öğeleri tanımlayıp bunları herhangi bir önceki tanımlanmış katmanları arasında ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aada5-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aada5-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aada5-139">See also</span></span>

- [<span data-ttu-id="aada5-140">Uç Nokta Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aada5-140">Endpoint Creation Overview</span></span>](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [<span data-ttu-id="aada5-141">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="aada5-141">Using Bindings to Configure Services and Clients</span></span>](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="aada5-142">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="aada5-142">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="aada5-143">Nasıl yapılır: Sistem tarafından sağlanan bir bağlamayı özelleştirme</span><span class="sxs-lookup"><span data-stu-id="aada5-143">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
- [<span data-ttu-id="aada5-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="aada5-144">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="aada5-145">Özel Bağlama</span><span class="sxs-lookup"><span data-stu-id="aada5-145">Custom Binding</span></span>](../../../../docs/framework/wcf/samples/custom-binding.md)
