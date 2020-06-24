---
title: Çift Yönlü Hizmetler
description: WCF 'de çift uç noktaların, istemci tarafından oluşturulan bir kanaldan birbirlerine ileti göndermesini sağlayan bir çift yönlü hizmet sözleşmesi oluşturmayı öğrenin.
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: a43bb63a0ccf1a34b79dce755c19f7ed4cb6c16c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247357"
---
# <a name="duplex-services"></a><span data-ttu-id="46117-103">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="46117-103">Duplex Services</span></span>

<span data-ttu-id="46117-104">Çift yönlü hizmet sözleşmesi, her iki bitiş noktası da birbirlerine ayrı olarak ileti gönderebileceği bir ileti değişim modelidir.</span><span class="sxs-lookup"><span data-stu-id="46117-104">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="46117-105">Bu nedenle bir çift yönlü hizmet, iletileri istemci uç noktasına geri gönderebilirler ve olay benzeri davranışlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="46117-105">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="46117-106">Çift yönlü iletişim, bir istemci bir hizmete bağlandığında ve hizmetin istemciye geri ileti gönderebileceği bir kanalla birlikte hizmetine hizmet sağlıyorsa oluşur.</span><span class="sxs-lookup"><span data-stu-id="46117-106">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="46117-107">Çift yönlü hizmetlerin olay benzeri davranışının yalnızca bir oturum içinde çalışıp çalışmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="46117-107">Note that the event-like behavior of duplex services only works within a session.</span></span>

<span data-ttu-id="46117-108">Bir çift yönlü sözleşme oluşturmak için bir çift arabirim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46117-108">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="46117-109">Birincisi, bir istemcinin çağırabileceği işlemleri açıklayan hizmet sözleşmesi arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="46117-109">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="46117-110">Bu hizmet sözleşmesinin, özelliğinde bir *geri çağırma sözleşmesi* belirtmesi gerekir <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="46117-110">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="46117-111">Geri arama sözleşmesi, hizmetin istemci uç noktasında çağırabileceğine yönelik işlemleri tanımlayan arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="46117-111">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="46117-112">Bir çift yönlü sözleşme, sistem tarafından sağlanmış çift yönlü bağlamaların bunları kullanmasına rağmen bir oturum gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="46117-112">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>

<span data-ttu-id="46117-113">Bir çift yönlü sözleşmenin bir örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46117-113">The following is an example of a duplex contract.</span></span>

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

<span data-ttu-id="46117-114">`CalculatorService`Sınıfı, birincil arabirimini uygular `ICalculatorDuplex` .</span><span class="sxs-lookup"><span data-stu-id="46117-114">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="46117-115">Hizmet, her bir <xref:System.ServiceModel.InstanceContextMode.PerSession> oturumun sonucunu korumak için örnek modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="46117-115">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="46117-116">Adlı özel özellik `Callback` , istemciye geri çağırma kanalına erişir.</span><span class="sxs-lookup"><span data-stu-id="46117-116">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="46117-117">Hizmet, aşağıdaki örnek kodda gösterildiği gibi geri çağırma arabirimi aracılığıyla istemciye geri dönüş iletileri göndermek için geri aramayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="46117-117">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

<span data-ttu-id="46117-118">İstemci, hizmetten ileti almak için çift yönlü sözleşmenin geri çağırma arabirimini uygulayan bir sınıf sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="46117-118">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="46117-119">Aşağıdaki örnek kod, `CallbackHandler` arabirimini uygulayan bir sınıfı gösterir `ICalculatorDuplexCallback` .</span><span class="sxs-lookup"><span data-stu-id="46117-119">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

<span data-ttu-id="46117-120">Bir çift yönlü sözleşme için oluşturulan WCF istemcisinin, <xref:System.ServiceModel.InstanceContext> oluşturma sırasında bir sınıfın sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="46117-120">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="46117-121">Bu <xref:System.ServiceModel.InstanceContext> sınıf, geri çağırma arabirimini uygulayan ve hizmetten geri gönderilen iletileri işleyen bir nesne için sitesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46117-121">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="46117-122">Sınıf bir sınıf <xref:System.ServiceModel.InstanceContext> örneğiyle oluşturulur `CallbackHandler` .</span><span class="sxs-lookup"><span data-stu-id="46117-122">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="46117-123">Bu nesne hizmetten geri çağırma arabirimindeki istemciye gönderilen iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="46117-123">This object handles messages sent from the service to the client on the callback interface.</span></span>

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

<span data-ttu-id="46117-124">Her iki oturum iletişimini ve çift yönlü iletişimi destekleyen bir bağlama sağlamak üzere hizmetin yapılandırması ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46117-124">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="46117-125">`wsDualHttpBinding`Öğesi oturum iletişimini destekler ve her yön için bir tane olmak üzere ÇIFT http bağlantısı sağlayarak çift yönlü iletişime olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="46117-125">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>

<span data-ttu-id="46117-126">İstemcisinde, aşağıdaki örnek yapılandırmada gösterildiği gibi, sunucunun istemciye bağlanmak için kullanabileceği bir adres yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46117-126">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="46117-127">Güvenli bir konuşma kullanarak kimlik doğrulaması başarısız olan ve çift yönlü olmayan istemciler genellikle bir oluşturur <xref:System.ServiceModel.Security.MessageSecurityException> .</span><span class="sxs-lookup"><span data-stu-id="46117-127">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="46117-128">Ancak, güvenli bir konuşma kullanan bir çift yönlü istemci kimlik doğrulaması yapamazsa, istemci bir <xref:System.TimeoutException> bunun yerine alır.</span><span class="sxs-lookup"><span data-stu-id="46117-128">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>

<span data-ttu-id="46117-129">Öğesini kullanarak bir istemci/hizmet oluşturursanız `WSHttpBinding` ve istemci geri çağırma uç noktasını eklemezseniz, aşağıdaki hatayı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="46117-129">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

<span data-ttu-id="46117-130">Aşağıdaki örnek kod, istemci uç noktası adresinin programlı olarak nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="46117-130">The following sample code shows how to specify the client endpoint address programmatically.</span></span>

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

<span data-ttu-id="46117-131">Aşağıdaki örnek kod, yapılandırmada istemci uç noktası adresinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46117-131">The following sample code shows how to specify the client endpoint address in configuration.</span></span>

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
> <span data-ttu-id="46117-132">Bir hizmet veya istemci, kanalını kapattığında çift yönlü model otomatik olarak algılamaz.</span><span class="sxs-lookup"><span data-stu-id="46117-132">The duplex model doesn't automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="46117-133">Bu nedenle, bir istemci beklenmedik şekilde sonlandırılırsa, varsayılan olarak hizmete bildirilmez veya bir hizmetin beklenmedik şekilde sonlandırılırsa, istemciye bildirim uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="46117-133">So if a client unexpectedly terminates, by default the service will not be notified, or if a service unexpectedly terminates, the client will not be notified.</span></span> <span data-ttu-id="46117-134">Bağlantısı kesilen bir hizmet kullanırsanız, <xref:System.ServiceModel.CommunicationException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="46117-134">If you use a service that is disconnected, the <xref:System.ServiceModel.CommunicationException> exception is raised.</span></span> <span data-ttu-id="46117-135">İstemciler ve hizmetler, seçeneğini belirlerseniz, birbirlerine bildirimde bulunan kendi protokollerini uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="46117-135">Clients and services can implement their own protocol to notify each other if they so choose.</span></span> <span data-ttu-id="46117-136">Hata işleme hakkında daha fazla bilgi için bkz. [WCF hata işleme](../wcf-error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="46117-136">For more information on error handling, see [WCF Error Handling](../wcf-error-handling.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46117-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46117-137">See also</span></span>

- [<span data-ttu-id="46117-138">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="46117-138">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="46117-139">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="46117-139">Specifying Client Run-Time Behavior</span></span>](../specifying-client-run-time-behavior.md)
- [<span data-ttu-id="46117-140">Nasıl yapılır: Kanal Fabrikası Oluşturma ve Bunu Kanal Oluşturmak ve Yönetmek için Kullanma</span><span class="sxs-lookup"><span data-stu-id="46117-140">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
