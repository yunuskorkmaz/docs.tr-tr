---
title: "Çift Yönlü Hizmetler"
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
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5c7cb9d963e56c6a6e06421afdb14427440643c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="duplex-services"></a><span data-ttu-id="eb56a-102">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="eb56a-102">Duplex Services</span></span>
<span data-ttu-id="eb56a-103">Çift yönlü hizmet sözleşmesi, her iki uç nokta ileti diğer bağımsız olarak gönderebilirsiniz bir ileti değişim deseni değil.</span><span class="sxs-lookup"><span data-stu-id="eb56a-103">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="eb56a-104">Çift yönlü bir hizmet, bu nedenle, olay benzeri davranışı sağlama geri istemci uç noktaya iletileri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="eb56a-104">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="eb56a-105">Çift yönlü iletişimi bir istemci bir hizmetine bağlanır ve hizmet üzerinde hizmet istemciye iletiler gönderebilir bir kanal sağlar oluşur.</span><span class="sxs-lookup"><span data-stu-id="eb56a-105">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="eb56a-106">Çift yönlü hizmetler olay benzeri davranışını yalnızca bir oturumunda çalıştığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="eb56a-106">Note that the event-like behavior of duplex services only works within a session.</span></span>  
  
 <span data-ttu-id="eb56a-107">Çift yönlü sözleşme oluşturmak için bir çift arabirimleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eb56a-107">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="eb56a-108">İlk istemci çağırabileceği işlemleri açıklayan hizmet sözleşmesi arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="eb56a-108">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="eb56a-109">Bu hizmet sözleşmesini belirtmelisiniz bir *geri çağırma sözleşme* içinde <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="eb56a-109">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="eb56a-110">Geri arama sözleşmesi, hizmetin istemci uç noktada çağırabilirsiniz işlemleri tanımlayan arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="eb56a-110">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="eb56a-111">Sistem tarafından sağlanan çift yönlü bağlamaları olun olsa da çift yönlü sözleşme bir oturum gerektirmez bunları kullanın.</span><span class="sxs-lookup"><span data-stu-id="eb56a-111">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>  
  
 <span data-ttu-id="eb56a-112">Çift yönlü sözleşme örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb56a-112">The following is an example of a duplex contract.</span></span>  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 <span data-ttu-id="eb56a-113">`CalculatorService` Sınıfı uygulayan birincil `ICalculatorDuplex` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="eb56a-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="eb56a-114">Hizmet kullandığı <xref:System.ServiceModel.InstanceContextMode.PerSession> her oturum için sonuç korumak için örnek modu.</span><span class="sxs-lookup"><span data-stu-id="eb56a-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="eb56a-115">Adlı özel özellik `Callback` geri çağırma kanal istemciye erişir.</span><span class="sxs-lookup"><span data-stu-id="eb56a-115">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="eb56a-116">Hizmet geri çağırma istemciye geri çağırma arabirimi üzerinden ileti göndermek için aşağıdaki örnek kodda gösterildiği gibi kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb56a-116">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 <span data-ttu-id="eb56a-117">İstemci hizmetinden iletileri almak için çift yönlü sözleşme geri çağırma arabirimi uygulayan bir sınıf sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb56a-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="eb56a-118">Aşağıdaki örnek kod gösterir bir `CallbackHandler` uygulayan sınıf `ICalculatorDuplexCallback` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="eb56a-118">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 <span data-ttu-id="eb56a-119">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Çift yönlü sözleşme gerektirir oluşturan istemci bir <xref:System.ServiceModel.InstanceContext> yapım sağlanacak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="eb56a-119">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="eb56a-120">Bu <xref:System.ServiceModel.InstanceContext> sınıfı, geri çağırma arabirimini uygulayan ve geri hizmetinden gönderilen iletileri işleyen bir nesne için site olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb56a-120">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="eb56a-121">Bir <xref:System.ServiceModel.InstanceContext> sınıfı örneği ile oluşturulan `CallbackHandler` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="eb56a-121">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="eb56a-122">Bu nesne hizmetinden geri çağırma arabirimi istemciye gönderilen iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="eb56a-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 <span data-ttu-id="eb56a-123">Oturum iletişim ve çift yönlü iletişimi destekleyen bir bağlama sağlamak için hizmeti için yapılandırma ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb56a-123">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="eb56a-124">`wsDualHttpBinding` Öğesi oturum iletişimi destekler ve her yön için bir tane çift HTTP bağlantılarını sağlayarak çift yönlü iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb56a-124">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>  
  
 <span data-ttu-id="eb56a-125">İstemcide, sunucu istemciye bağlanmak için kullanabileceğiniz aşağıdaki örnek yapılandırmada gösterildiği gibi bir adresi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb56a-125">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>  
  
  
  
> [!NOTE]
>  <span data-ttu-id="eb56a-126">Güvenli Konuşmayla genellikle kullanarak kimlik doğrulaması için başarısız olmayan çift yönlü istemcileri throw bir <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="eb56a-126">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="eb56a-127">Ancak, istemci kimlik doğrulaması güvenli bir konuşma kullanan çift yönlü istemci başarısız olursa, alır bir <xref:System.TimeoutException> yerine.</span><span class="sxs-lookup"><span data-stu-id="eb56a-127">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>  
  
 <span data-ttu-id="eb56a-128">Bir istemci/hizmetini kullanarak oluşturursanız `WSHttpBinding` öğesi ve istemci geri araması endpoint dahil, aşağıdaki hatayı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="eb56a-128">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 <span data-ttu-id="eb56a-129">Aşağıdaki örnek kod istemci belirtmek uç nokta adresi kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb56a-129">The following sample code shows how to specify the client endpoint address in code.</span></span>  
  
```  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
  
 <span data-ttu-id="eb56a-130">Aşağıdaki örnek kod istemci belirtmek uç nokta adresi yapılandırmasında gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb56a-130">The following sample code shows how to specify the client endpoint address in configuration.</span></span>  
  
```xml  
<client>  
    <endpoint name ="ServerEndpoint"   
          address="http://localhost:12000/DuplexTestUsingConfig/Server"  
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"   
            binding="wsDualHttpBinding"  
           contract="IDuplexTest" />  
</client>  
<bindings>  
    <wsDualHttpBinding>  
        <binding name="WSDualHttpBinding_IDuplexTest"    
          clientBaseAddress="http://localhost:8000/myClient/" >  
            <security mode="None"/>  
         </binding>  
    </wsDualHttpBinding>  
</bindings>  
```  
  
> [!WARNING]
>  <span data-ttu-id="eb56a-131">Bir hizmet veya istemci kendi kanal kapandığında çift yönlü modeli otomatik olarak algılamaz.</span><span class="sxs-lookup"><span data-stu-id="eb56a-131">The duplex model does not automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="eb56a-132">Bu nedenle istemci beklenmedik şekilde sona ererse, varsayılan olarak hizmet değil bildirilecek veya bir istemci beklenmedik şekilde sona ererse, hizmet olmayan bildirilir.</span><span class="sxs-lookup"><span data-stu-id="eb56a-132">So if a client unexpectedly terminates, by default the service will not be notified, or if a client unexpectedly terminates, the service will not be notified.</span></span> <span data-ttu-id="eb56a-133">Bu nedenle seçerseniz birbirine bildirmek için kendi protokolü, istemciler ve hizmetler uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb56a-133">Clients and services can implement their own protocol to notify each other if they so choose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb56a-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb56a-134">See Also</span></span>  
 [<span data-ttu-id="eb56a-135">Çift yönlü</span><span class="sxs-lookup"><span data-stu-id="eb56a-135">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)  
 [<span data-ttu-id="eb56a-136">İstemci çalışma zamanı davranışını belirtme</span><span class="sxs-lookup"><span data-stu-id="eb56a-136">Specifying Client Run-Time Behavior</span></span>](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [<span data-ttu-id="eb56a-137">Nasıl yapılır: kanal fabrikası oluşturma ve kanal oluşturmak ve yönetmek için kullanın</span><span class="sxs-lookup"><span data-stu-id="eb56a-137">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
