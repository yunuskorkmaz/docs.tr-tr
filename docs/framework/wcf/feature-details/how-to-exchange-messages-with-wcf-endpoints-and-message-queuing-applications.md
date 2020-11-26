---
title: 'Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 8f8baf345059c01b0fef3b61ef85556151269118
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246426"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="32ea9-102">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="32ea9-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>

<span data-ttu-id="32ea9-103">MSMQ iletilerini WCF iletilerine dönüştürmek için MSMQ tümleştirme bağlamasını kullanarak mevcut Message Queuing (MSMQ) uygulamalarını Windows Communication Foundation (WCF) uygulamalarıyla tümleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32ea9-103">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="32ea9-104">Bu, WCF istemcilerinden MSMQ alıcı uygulamalarına ve MSMQ gönderici uygulamalarından WCF Hizmetleri 'ne çağrı yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="32ea9-104">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="32ea9-105">Bu bölümde, <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> (1) BIR WCF istemcisi Ile System. Messaging ve (2) ile BIR MSMQ uygulama istemcisi ve bır WCF hizmeti kullanılarak yazılan BIR MSMQ uygulama hizmeti arasındaki sıraya alınmış iletişim için nasıl kullanılacağını açıkladık.</span><span class="sxs-lookup"><span data-stu-id="32ea9-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="32ea9-106">Bir WCF istemcisinden MSMQ alıcı uygulamasının nasıl çağrılacağını gösteren bir örnek için, [Windows Communication Foundation Message Queuing](../samples/wcf-to-message-queuing.md) örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="32ea9-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="32ea9-107">Bir MSMQ istemcisinden bir WCF hizmetinin nasıl çağrılacağını gösteren bir örnek için, [Message Queuing Windows Communication Foundation](../samples/message-queuing-to-wcf.md) örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="32ea9-107">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="32ea9-108">MSMQ istemcisinden iletiler alan bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="32ea9-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1. <span data-ttu-id="32ea9-109">Aşağıdaki örnek kodda gösterildiği gibi, bir MSMQ gönderici uygulamasından sıraya alınan iletileri alan WCF hizmeti için hizmet sözleşmesini tanımlayan bir arabirim tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="32ea9-109">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <span data-ttu-id="32ea9-110"><xref:System.ServiceModel.ServiceBehaviorAttribute>Aşağıdaki örnek kodda gösterildiği gibi, arabirimini uygulayın ve özniteliğini sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="32ea9-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. <span data-ttu-id="32ea9-111">Öğesini belirten bir yapılandırma dosyası oluşturun <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> .</span><span class="sxs-lookup"><span data-stu-id="32ea9-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  

4. <span data-ttu-id="32ea9-112"><xref:System.ServiceModel.ServiceHost>Yapılandırılmış bağlamayı kullanan bir nesne örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="32ea9-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="32ea9-113">MSMQ alıcı uygulamasına ileti gönderen bir WCF istemcisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="32ea9-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1. <span data-ttu-id="32ea9-114">Aşağıdaki örnek kodda gösterildiği gibi, MSMQ alıcısına sıraya alınan iletileri gönderen WCF istemcisinin hizmet sözleşmesini tanımlayan bir arabirim tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="32ea9-114">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. <span data-ttu-id="32ea9-115">WCF istemcisinin MSMQ alıcısını çağırmak için kullandığı bir istemci sınıfı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="32ea9-115">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. <span data-ttu-id="32ea9-116">MsmqIntegrationBinding bağlamasının kullanımını belirten bir yapılandırma oluşturun.</span><span class="sxs-lookup"><span data-stu-id="32ea9-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. <span data-ttu-id="32ea9-117">İstemci sınıfının bir örneğini oluşturun ve ileti alma hizmeti tarafından tanımlanan yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="32ea9-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="32ea9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32ea9-118">See also</span></span>

- [<span data-ttu-id="32ea9-119">Kuyruklar Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="32ea9-119">Queues Overview</span></span>](queues-overview.md)
- [<span data-ttu-id="32ea9-120">Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma</span><span class="sxs-lookup"><span data-stu-id="32ea9-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [<span data-ttu-id="32ea9-121">Windows Communication Foundation'dan İleti Kuyruğuna</span><span class="sxs-lookup"><span data-stu-id="32ea9-121">Windows Communication Foundation to Message Queuing</span></span>](../samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="32ea9-122">İleti Kuyruğa Alma Yükleme (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="32ea9-122">Installing Message Queuing (MSMQ)</span></span>](../samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="32ea9-123">Windows Communication Foundation'a İleti Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="32ea9-123">Message Queuing to Windows Communication Foundation</span></span>](../samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="32ea9-124">İleti Kuyruğa Alma ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="32ea9-124">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
