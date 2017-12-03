---
title: "Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 75b18dab37a18723671cebf51c3cc943b907b38a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="e810c-102">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="e810c-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="e810c-103">Message Queuing (MSMQ) uygulamalarınız ile tümleştirebilirsiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] gelen ve giden MSMQ iletileri dönüştürmek için MSMQ tümleştirme bağlama kullanarak uygulamaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletileri.</span><span class="sxs-lookup"><span data-stu-id="e810c-103">You can integrate existing Message Queuing (MSMQ) applications with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications by using the MSMQ integration binding to convert MSMQ messages to and from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] messages.</span></span> <span data-ttu-id="e810c-104">Bu sayede MSMQ alıcı uygulamalardan çağırmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çağrısına yanı sıra istemcilerin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ Gönderen uygulamalardan Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="e810c-104">This allows you to call into MSMQ receiver applications from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients as well as call into [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="e810c-105">Bu bölümde, biz nasıl kullanılacağını açıklayan <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> arasında kuyruğa alınan iletişim için (1) bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System.Messaging ve (2) bir MSMQ uygulama istemcisi kullanılarak yazılmış bir MSMQ uygulama hizmet ve istemci ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="e810c-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="e810c-106">Bir MSMQ alıcı uygulamasından nasıl çağırılacağını tam bir örnek için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, bkz: [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="e810c-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="e810c-107">Nasıl çağırılacağını tam bir örnek için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet MSMQ istemciden bkz [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="e810c-107">For a complete sample that demonstrates how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="e810c-108">MSMQ istemciden gelen iletileri alan bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e810c-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1.  <span data-ttu-id="e810c-109">İçin hizmet sözleşmesini tanımlayan bir arabirim tanımlayın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , alan hizmetini sıraya alınan iletileri bir MSMQ gönderen uygulamasından aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e810c-109">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  <span data-ttu-id="e810c-110">Arabirim uygulamak ve <xref:System.ServiceModel.ServiceBehaviorAttribute> aşağıdaki örnek kodda gösterildiği gibi sınıfa öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e810c-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  <span data-ttu-id="e810c-111">Belirten yapılandırma dosyası oluşturma <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span><span class="sxs-lookup"><span data-stu-id="e810c-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  
  
  
  
4.  <span data-ttu-id="e810c-112">Örneği bir <xref:System.ServiceModel.ServiceHost> yapılandırılan bağlama kullanan nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e810c-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="e810c-113">MSMQ alıcı uygulamaya iletileri gönderen bir WCF istemcisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e810c-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1.  <span data-ttu-id="e810c-114">İçin hizmet sözleşmesini tanımlayan bir arabirim tanımlayın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sıraya alınan gönderen istemci iletileri MSMQ alıcı için aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e810c-114">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  <span data-ttu-id="e810c-115">Bir istemci tanımlamak, sınıf [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcisi MSMQ alıcı çağırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e810c-115">Define a client class that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  <span data-ttu-id="e810c-116">MsmqIntegrationBinding bağlama kullanılmasını belirtiyor. bir yapılandırmasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e810c-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  <span data-ttu-id="e810c-117">İstemci sınıfı örneği oluşturun ve hizmet alma iletisi tarafından tanımlanan yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="e810c-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e810c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e810c-118">See Also</span></span>  
 [<span data-ttu-id="e810c-119">Kuyruklar genel bakış</span><span class="sxs-lookup"><span data-stu-id="e810c-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [<span data-ttu-id="e810c-120">Nasıl yapılır: WCF uç noktaları iletileri kuyruğa alınan</span><span class="sxs-lookup"><span data-stu-id="e810c-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [<span data-ttu-id="e810c-121">Message Queuing için Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="e810c-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="e810c-122">Message Queuing (MSMQ) yükleme</span><span class="sxs-lookup"><span data-stu-id="e810c-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="e810c-123">Windows Communication Foundation'a ileti kuyruğa alma</span><span class="sxs-lookup"><span data-stu-id="e810c-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="e810c-124">İleti kuyruğa alma ile ileti güvenliği</span><span class="sxs-lookup"><span data-stu-id="e810c-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
