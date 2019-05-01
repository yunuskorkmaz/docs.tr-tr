---
title: Çift Yönlü Hizmetler
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: 33cfcb765b93309d365a85e679107405a55a91f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858045"
---
# <a name="duplex-services"></a><span data-ttu-id="fddff-102">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="fddff-102">Duplex Services</span></span>

<span data-ttu-id="fddff-103">Çift yönlü hizmet sözleşmesi, her iki bitiş noktası iletileri diğer bağımsız olarak gönderebilir ileti değişim deseni ' dir.</span><span class="sxs-lookup"><span data-stu-id="fddff-103">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="fddff-104">Çift yönlü bir hizmet, bu nedenle, olay benzeri davranış sağlayan geri istemci uç noktası için iletileri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="fddff-104">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="fddff-105">Bir istemci bir hizmete bağlanır ve hizmet üzerinde hizmet istemciye iletileri gönderebilir bir kanal sağlar çift yönlü iletişimi gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="fddff-105">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="fddff-106">Çift yönlü hizmetler olay benzeri davranışını yalnızca bir oturumunda çalıştığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fddff-106">Note that the event-like behavior of duplex services only works within a session.</span></span>

<span data-ttu-id="fddff-107">Çift yönlü sözleşme oluşturma için bir çift arabirimler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fddff-107">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="fddff-108">İlk istemci çağırabilirsiniz işlemleri açıklayan hizmet sözleşme arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="fddff-108">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="fddff-109">Bu hizmet sözleşmesini belirtmelisiniz bir *geri çağırma anlaşması* içinde <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fddff-109">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="fddff-110">Geri çağırma anlaşması istemci uç noktada bir hizmeti çağıran işlemleri tanımlayan arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="fddff-110">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="fddff-111">Çift yönlü sözleşme bir oturumu gerektirmez, sistem tarafından sağlanan çift yönlü bağlamaları olun olsa da bunları kullanın.</span><span class="sxs-lookup"><span data-stu-id="fddff-111">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>

<span data-ttu-id="fddff-112">Çift yönlü sözleşme örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fddff-112">The following is an example of a duplex contract.</span></span>

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

<span data-ttu-id="fddff-113">`CalculatorService` Sınıfın uyguladığı birincil `ICalculatorDuplex` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fddff-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="fddff-114">Hizmeti kullandığı <xref:System.ServiceModel.InstanceContextMode.PerSession> her oturum için sonuç korumak için örnek modu.</span><span class="sxs-lookup"><span data-stu-id="fddff-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="fddff-115">Adlı bir özel özellik `Callback` istemci geri çağırma kanala erişir.</span><span class="sxs-lookup"><span data-stu-id="fddff-115">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="fddff-116">Hizmet geri çağırma aracılığıyla geri çağırma arabirimi istemciye ileti göndermek için aşağıdaki örnek kodda gösterildiği gibi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fddff-116">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

<span data-ttu-id="fddff-117">İstemci, hizmeti iletileri almak için çift yönlü sözleşme geri arama arabirimini uygulayan bir sınıf sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fddff-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="fddff-118">Aşağıdaki örnek kodun gösterdiği bir `CallbackHandler` uygulayan sınıf `ICalculatorDuplexCallback` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fddff-118">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

<span data-ttu-id="fddff-119">Çift yönlü sözleşme gerektirir oluşturan WCF istemcisini bir <xref:System.ServiceModel.InstanceContext> yapım sırasında sağlanacak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fddff-119">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="fddff-120">Bu <xref:System.ServiceModel.InstanceContext> sınıfı, geri arama arayüzü uygular ve hizmetinden gönderilen iletileri işleyen bir nesne için site olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fddff-120">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="fddff-121">Bir <xref:System.ServiceModel.InstanceContext> sınıf örneği ile oluşturulmuş `CallbackHandler` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fddff-121">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="fddff-122">Bu nesne, hizmetten geri çağırma arabirimi istemciye gönderilen iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="fddff-122">This object handles messages sent from the service to the client on the callback interface.</span></span>

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

<span data-ttu-id="fddff-123">Oturum iletişim hem çift yönlü iletişimi destekleyen bir bağlama sağlamak için hizmeti için yapılandırma ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fddff-123">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="fddff-124">`wsDualHttpBinding` Öğesi oturumu iletişimi destekler ve her yön için bir ikili HTTP bağlantılarını sağlayarak çift yönlü iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fddff-124">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>

<span data-ttu-id="fddff-125">İstemcide, sunucu istemciye bağlanmak için aşağıdaki örnek yapılandırmada gösterildiği gibi kullanabileceğiniz bir adresi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fddff-125">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="fddff-126">Genellikle bir güvenli konuşma kullanarak kimlik doğrulaması için başarısız olmayan yönlü istemciler durum bir <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="fddff-126">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="fddff-127">Ancak, bir güvenli konuşma kullanan çift yönlü istemci kimlik doğrulaması başarısız olursa, istemci alır bir <xref:System.TimeoutException> yerine.</span><span class="sxs-lookup"><span data-stu-id="fddff-127">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>

<span data-ttu-id="fddff-128">Kullanarak bir istemci/hizmet oluşturursanız `WSHttpBinding` öğesi ve istemci geri çağırma uç noktası içermez, aşağıdaki hatayı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="fddff-128">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>

```
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

<span data-ttu-id="fddff-129">Aşağıdaki örnek kod istemci belirtmek uç nokta adresi programlı olarak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fddff-129">The following sample code shows how to specify the client endpoint address programmatically.</span></span>

```csharp
WSDualHttpBinding binding = new WSDualHttpBinding();
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");
```

```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")
```

<span data-ttu-id="fddff-130">Aşağıdaki örnek kod, uç nokta adresi yapılandırmada istemci belirtmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="fddff-130">The following sample code shows how to specify the client endpoint address in configuration.</span></span>

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
> <span data-ttu-id="fddff-131">Bir hizmet veya istemcinin, kanal kapandığında çift yönlü modeli otomatik olarak algılamaz.</span><span class="sxs-lookup"><span data-stu-id="fddff-131">The duplex model does not automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="fddff-132">Bu nedenle istemci beklenmedik şekilde sonlandırılırsa, varsayılan olarak hizmet değil bildirilir veya bir istemci beklenmedik şekilde sonlandırılırsa, hizmet olmayan bildirilir.</span><span class="sxs-lookup"><span data-stu-id="fddff-132">So if a client unexpectedly terminates, by default the service will not be notified, or if a client unexpectedly terminates, the service will not be notified.</span></span> <span data-ttu-id="fddff-133">Bu nedenle seçerseniz birbirine bildirmek için kendi protokolü, istemciler ve hizmetler uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fddff-133">Clients and services can implement their own protocol to notify each other if they so choose.</span></span>

## <a name="see-also"></a><span data-ttu-id="fddff-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fddff-134">See also</span></span>

- [<span data-ttu-id="fddff-135">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="fddff-135">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)
- [<span data-ttu-id="fddff-136">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="fddff-136">Specifying Client Run-Time Behavior</span></span>](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="fddff-137">Nasıl yapılır: Kanal fabrikası oluşturma ve bunu kanal oluşturmak ve yönetmek için kullanın</span><span class="sxs-lookup"><span data-stu-id="fddff-137">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
