---
title: 'Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 7463f9cfc37c2bf4f271f6e59896a7d77f3f65cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310312"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="74817-102">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="74817-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="74817-103">MSMQ iletileri gelen WCF iletileri ve dönüştürmek için MSMQ tümleştirme bağlama kullanarak Windows Communication Foundation (WCF) uygulamaları ile Message Queuing (MSMQ) uygulamalara tümleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74817-103">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="74817-104">Bu, yanı sıra WCF istemcileri MSMQ alıcı uygulamalardan çağırmak WCF hizmetleri içine MSMQ gönderen uygulamalarından çağırmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="74817-104">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="74817-105">Bu bölümde, biz nasıl kullanılacağını açıklayan <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> (1) bir WCF istemcisi System.Messaging ve (2) bir MSMQ uygulama istemcisi ve bir WCF Hizmeti kullanılarak yazılmış bir MSMQ uygulama hizmeti arasındaki kuyruğa alınan iletişim için.</span><span class="sxs-lookup"><span data-stu-id="74817-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="74817-106">MSMQ alıcı uygulamanın bir WCF istemciden çağırmayı göstermektedir, eksiksiz bir örnek için bkz. [Message Queuing Windows Communication Foundation'a](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="74817-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="74817-107">Bir WCF hizmeti bir MSMQ istemciden çağırmayı göstermektedir, eksiksiz bir örnek için bkz. [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="74817-107">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="74817-108">MSMQ istemciden gelen iletileri alan bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="74817-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1. <span data-ttu-id="74817-109">Aşağıdaki örnek kodda gösterildiği gibi bir MSMQ gönderen uygulamasından kuyruğa alınmış iletiler alan bir WCF hizmeti için hizmet sözleşmesini tanımlayan bir arabirim tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="74817-109">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <span data-ttu-id="74817-110">Arabirim uygulamak ve <xref:System.ServiceModel.ServiceBehaviorAttribute> aşağıdaki örnekte gösterildiği gibi Sınıf özniteliği.</span><span class="sxs-lookup"><span data-stu-id="74817-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. <span data-ttu-id="74817-111">Belirten yapılandırma dosyası oluşturma <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span><span class="sxs-lookup"><span data-stu-id="74817-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  

4. <span data-ttu-id="74817-112">Örneği bir <xref:System.ServiceModel.ServiceHost> yapılandırılmış bağlama kullanan nesne.</span><span class="sxs-lookup"><span data-stu-id="74817-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="74817-113">Bir MSMQ alıcı uygulamasına ileti gönderen bir WCF istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="74817-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1. <span data-ttu-id="74817-114">Aşağıdaki örnek kodda gösterildiği gibi kuyruğa alınmış iletileri MSMQ alıcısına gönderir WCF istemcisi için hizmet sözleşmesini tanımlayan bir arabirim tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="74817-114">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. <span data-ttu-id="74817-115">MSMQ alıcı çağırmak için WCF istemcisini kullanan bir istemci sınıfı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="74817-115">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. <span data-ttu-id="74817-116">MsmqIntegrationBinding bağlama belirtir bir yapılandırma oluşturun.</span><span class="sxs-lookup"><span data-stu-id="74817-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. <span data-ttu-id="74817-117">İstemci sınıfı örneğini oluşturmak ve ileti alma hizmeti tarafından tanımlanan yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="74817-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="74817-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74817-118">See also</span></span>

- [<span data-ttu-id="74817-119">Kuyruklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="74817-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [<span data-ttu-id="74817-120">Nasıl yapılır: WCF uç noktaları ile kuyruğa alınmış iletiler gönderip alır</span><span class="sxs-lookup"><span data-stu-id="74817-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [<span data-ttu-id="74817-121">Windows Communication Foundation'dan Message Queuing’e</span><span class="sxs-lookup"><span data-stu-id="74817-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="74817-122">Message Queuing (MSMQ) Yükleme</span><span class="sxs-lookup"><span data-stu-id="74817-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="74817-123">Message Queuing’den Windows Communication Foundation'a</span><span class="sxs-lookup"><span data-stu-id="74817-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="74817-124">Message Queuing Üzerinden İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="74817-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
