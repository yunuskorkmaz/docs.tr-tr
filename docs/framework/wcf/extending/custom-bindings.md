---
title: Özel Bağlamalar
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: a4b3abfe9be25c9080a362eb4a6e4c7b070528f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797231"
---
# <a name="custom-bindings"></a><span data-ttu-id="8fdf3-102">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8fdf3-102">Custom Bindings</span></span>

<span data-ttu-id="8fdf3-103">Sistem tarafından belirtilen bağlamalardan biri hizmetinizin gereksinimlerini karşılamadığında <xref:System.ServiceModel.Channels.CustomBinding> sınıfı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="8fdf3-104">Tüm bağlamalar sıralı bir bağlama öğeleri kümesinden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="8fdf3-105">Özel Bağlamalar, sistem tarafından sağlanmış bir bağlama öğelerinden oluşturulabilir veya Kullanıcı tanımlı özel bağlama öğeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="8fdf3-106">Bir hizmet uç noktasında yeni aktarımların veya kodlayıcıların kullanımını etkinleştirmek için, örneğin, özel bağlama öğelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="8fdf3-107">Çalışma örnekleri için bkz. [özel bağlama örnekleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="8fdf3-107">For working examples, see [Custom Binding Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span></span> <span data-ttu-id="8fdf3-108">Daha fazla bilgi için bkz [ \<. CustomBinding >](../../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="8fdf3-108">For more information, see [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="8fdf3-109">Özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fdf3-109">Construction of a Custom Binding</span></span>

<span data-ttu-id="8fdf3-110">Özel bağlama, belirli bir sırada " <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> yığılmış" olan bağlama öğeleri koleksiyonundan Oluşturucu kullanılarak oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="8fdf3-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="8fdf3-111">En üstte, akan işlemlere izin <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> veren isteğe bağlı bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>

- <span data-ttu-id="8fdf3-112">Next, WS- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> ReliableMessaging belirtiminde tanımlanan bir oturum ve sıralama mekanizmalarını sağlayan isteğe bağlı bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="8fdf3-113">Bir oturum, SOAP ve aktarım aracıları arası olabilir.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-113">A session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="8fdf3-114">Daha sonra yetkilendirme, <xref:System.ServiceModel.Channels.SecurityBindingElement> kimlik doğrulama, koruma ve gizlilik gibi güvenlik özellikleri sağlayan isteğe bağlı bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>

- <span data-ttu-id="8fdf3-115">Daha sonra, http <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> gibi çift yönlü iletişimi desteklemeyen bir Aktarım Protokolü ile iki yönlü çift yönlü iletişim olanağı sağlayan isteğe bağlı bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>

- <span data-ttu-id="8fdf3-116">Next, tek yönlü <xref:System.ServiceModel.Channels.OneWayBindingElement>iletişim sağlayan bir isteğe bağlı) sınıftır.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>

- <span data-ttu-id="8fdf3-117">Next, aşağıdakilerden biri olabilecek isteğe bağlı bir akış güvenlik bağlama öğesidir.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-117">Next is an optional stream security binding element which can be one of the following.</span></span>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="8fdf3-118">Next, gerekli bir ileti kodlama bağlama öğesidir.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="8fdf3-119">Kendi ileti kodlayıcısını veya üç ileti kodlama bağlamalarından birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8fdf3-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

<span data-ttu-id="8fdf3-120">En altta gerekli bir taşıma öğesidir.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="8fdf3-121">Kendi taşıyıcıyı veya aşağıdaki taşıma bağlama öğelerinden birini Windows Communication Foundation (WCF) aşağıdakileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="8fdf3-121">You can use your own transport or one of the following transport binding elements Windows Communication Foundation (WCF) provides:</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

<span data-ttu-id="8fdf3-122">Aşağıdaki tabloda her bir katmanın seçenekleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-122">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="8fdf3-123">Katman</span><span class="sxs-lookup"><span data-stu-id="8fdf3-123">Layer</span></span>|<span data-ttu-id="8fdf3-124">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="8fdf3-124">Options</span></span>|<span data-ttu-id="8fdf3-125">Gerekli</span><span class="sxs-lookup"><span data-stu-id="8fdf3-125">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="8fdf3-126">İşlemler</span><span class="sxs-lookup"><span data-stu-id="8fdf3-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="8fdf3-127">Hayır</span><span class="sxs-lookup"><span data-stu-id="8fdf3-127">No</span></span>|
|<span data-ttu-id="8fdf3-128">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="8fdf3-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="8fdf3-129">Hayır</span><span class="sxs-lookup"><span data-stu-id="8fdf3-129">No</span></span>|
|<span data-ttu-id="8fdf3-130">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="8fdf3-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="8fdf3-131">Hayır</span><span class="sxs-lookup"><span data-stu-id="8fdf3-131">No</span></span>|
|<span data-ttu-id="8fdf3-132">Encoding</span><span class="sxs-lookup"><span data-stu-id="8fdf3-132">Encoding</span></span>|<span data-ttu-id="8fdf3-133">Metin, ikili, Ileti Iletimi Iyileştirme mekanizması (MTOM), özel</span><span class="sxs-lookup"><span data-stu-id="8fdf3-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="8fdf3-134">Evet</span><span class="sxs-lookup"><span data-stu-id="8fdf3-134">Yes</span></span>|
|<span data-ttu-id="8fdf3-135">Aktarım</span><span class="sxs-lookup"><span data-stu-id="8fdf3-135">Transport</span></span>|<span data-ttu-id="8fdf3-136">TCP, HTTP, HTTPS, adlandırılmış kanallar (IPC olarak da bilinir), eşler arası (P2P), Message Queuing (MSMQ olarak da bilinir), özel</span><span class="sxs-lookup"><span data-stu-id="8fdf3-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="8fdf3-137">Evet</span><span class="sxs-lookup"><span data-stu-id="8fdf3-137">Yes</span></span>|

<span data-ttu-id="8fdf3-138">Ayrıca, kendi bağlama öğelerinizi tanımlayabilir ve bunları önceki tanımlı katmanlardan herhangi biri arasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fdf3-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fdf3-139">See also</span></span>

- [<span data-ttu-id="8fdf3-140">Uç Nokta Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8fdf3-140">Endpoint Creation Overview</span></span>](../endpoint-creation-overview.md)
- [<span data-ttu-id="8fdf3-141">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="8fdf3-141">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8fdf3-142">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8fdf3-142">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="8fdf3-143">Nasıl yapılır: Sistem tarafından sağlanmış bağlamayı özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8fdf3-143">How to: Customize a System-Provided Binding</span></span>](how-to-customize-a-system-provided-binding.md)
- [<span data-ttu-id="8fdf3-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8fdf3-144">\<customBinding></span></span>](../../configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="8fdf3-145">Özel Bağlama</span><span class="sxs-lookup"><span data-stu-id="8fdf3-145">Custom Binding</span></span>](../samples/custom-binding.md)
