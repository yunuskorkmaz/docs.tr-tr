---
title: Çift Yönlü Hizmetler
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: f9e563cb87ee376e33442cdf718f70202d300f40
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895175"
---
# <a name="duplex-services"></a><span data-ttu-id="b51d6-102">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="b51d6-102">Duplex Services</span></span>

<span data-ttu-id="b51d6-103">Çift yönlü hizmet sözleşmesi, her iki bitiş noktası da birbirlerine ayrı olarak ileti gönderebileceği bir ileti değişim modelidir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-103">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="b51d6-104">Bu nedenle bir çift yönlü hizmet, iletileri istemci uç noktasına geri gönderebilirler ve olay benzeri davranışlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b51d6-104">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="b51d6-105">Çift yönlü iletişim, bir istemci bir hizmete bağlandığında ve hizmetin istemciye geri ileti gönderebileceği bir kanalla birlikte hizmetine hizmet sağlıyorsa oluşur.</span><span class="sxs-lookup"><span data-stu-id="b51d6-105">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="b51d6-106">Çift yönlü hizmetlerin olay benzeri davranışının yalnızca bir oturum içinde çalışıp çalışmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b51d6-106">Note that the event-like behavior of duplex services only works within a session.</span></span>

<span data-ttu-id="b51d6-107">Bir çift yönlü sözleşme oluşturmak için bir çift arabirim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b51d6-107">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="b51d6-108">Birincisi, bir istemcinin çağırabileceği işlemleri açıklayan hizmet sözleşmesi arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-108">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="b51d6-109">Bu hizmet sözleşmesinin, <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özelliğinde bir *geri çağırma sözleşmesi* belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-109">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b51d6-110">Geri arama sözleşmesi, hizmetin istemci uç noktasında çağırabileceğine yönelik işlemleri tanımlayan arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-110">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="b51d6-111">Bir çift yönlü sözleşme, sistem tarafından sağlanmış çift yönlü bağlamaların bunları kullanmasına rağmen bir oturum gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b51d6-111">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>

<span data-ttu-id="b51d6-112">Bir çift yönlü sözleşmenin bir örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-112">The following is an example of a duplex contract.</span></span>

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

<span data-ttu-id="b51d6-113">Sınıfı, birincil `ICalculatorDuplex` arabirimini uygular. `CalculatorService`</span><span class="sxs-lookup"><span data-stu-id="b51d6-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="b51d6-114">Hizmet, her bir <xref:System.ServiceModel.InstanceContextMode.PerSession> oturumun sonucunu korumak için örnek modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="b51d6-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="b51d6-115">Adlı `Callback` özel özellik, istemciye geri çağırma kanalına erişir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-115">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="b51d6-116">Hizmet, aşağıdaki örnek kodda gösterildiği gibi geri çağırma arabirimi aracılığıyla istemciye geri dönüş iletileri göndermek için geri aramayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b51d6-116">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

<span data-ttu-id="b51d6-117">İstemci, hizmetten ileti almak için çift yönlü sözleşmenin geri çağırma arabirimini uygulayan bir sınıf sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51d6-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="b51d6-118">Aşağıdaki örnek kod, `CallbackHandler` `ICalculatorDuplexCallback` arabirimini uygulayan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-118">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

<span data-ttu-id="b51d6-119">Bir çift yönlü sözleşme için oluşturulan WCF istemcisinin, oluşturma sırasında bir <xref:System.ServiceModel.InstanceContext> sınıfın sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-119">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="b51d6-120">Bu <xref:System.ServiceModel.InstanceContext> sınıf, geri çağırma arabirimini uygulayan ve hizmetten geri gönderilen iletileri işleyen bir nesne için sitesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b51d6-120">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="b51d6-121">Sınıf bir sınıf örneğiyle `CallbackHandler` oluşturulur. <xref:System.ServiceModel.InstanceContext></span><span class="sxs-lookup"><span data-stu-id="b51d6-121">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="b51d6-122">Bu nesne hizmetten geri çağırma arabirimindeki istemciye gönderilen iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="b51d6-122">This object handles messages sent from the service to the client on the callback interface.</span></span>

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

<span data-ttu-id="b51d6-123">Her iki oturum iletişimini ve çift yönlü iletişimi destekleyen bir bağlama sağlamak üzere hizmetin yapılandırması ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51d6-123">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="b51d6-124">`wsDualHttpBinding` Öğesi oturum iletişimini destekler ve her yön için bir tane olmak üzere çift http bağlantısı sağlayarak çift yönlü iletişime olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b51d6-124">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>

<span data-ttu-id="b51d6-125">İstemcisinde, aşağıdaki örnek yapılandırmada gösterildiği gibi, sunucunun istemciye bağlanmak için kullanabileceği bir adres yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-125">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="b51d6-126">Güvenli bir konuşma kullanarak kimlik doğrulaması başarısız olan ve çift yönlü olmayan istemciler genellikle bir <xref:System.ServiceModel.Security.MessageSecurityException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b51d6-126">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="b51d6-127">Ancak, güvenli bir konuşma kullanan bir çift yönlü istemci kimlik doğrulaması yapamazsa, istemci bir <xref:System.TimeoutException> bunun yerine alır.</span><span class="sxs-lookup"><span data-stu-id="b51d6-127">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>

<span data-ttu-id="b51d6-128">`WSHttpBinding` Öğesini kullanarak bir istemci/hizmet oluşturursanız ve istemci geri çağırma uç noktasını eklemezseniz, aşağıdaki hatayı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b51d6-128">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

<span data-ttu-id="b51d6-129">Aşağıdaki örnek kod, istemci uç noktası adresinin programlı olarak nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-129">The following sample code shows how to specify the client endpoint address programmatically.</span></span>

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

<span data-ttu-id="b51d6-130">Aşağıdaki örnek kod, yapılandırmada istemci uç noktası adresinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-130">The following sample code shows how to specify the client endpoint address in configuration.</span></span>

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
> <span data-ttu-id="b51d6-131">Bir hizmet veya istemci, kanalını kapattığında çift yönlü model otomatik olarak algılamaz.</span><span class="sxs-lookup"><span data-stu-id="b51d6-131">The duplex model doesn't automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="b51d6-132">Bu nedenle, bir istemci beklenmedik şekilde sonlandırılırsa, varsayılan olarak hizmete bildirilmez veya bir hizmetin beklenmedik şekilde sonlandırılırsa, istemciye bildirim uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="b51d6-132">So if a client unexpectedly terminates, by default the service will not be notified, or if a service unexpectedly terminates, the client will not be notified.</span></span> <span data-ttu-id="b51d6-133">Bağlantısı kesilen bir hizmet kullanırsanız, <xref:System.ServiceModel.CommunicationException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b51d6-133">If you use a service that is disconnected, the <xref:System.ServiceModel.CommunicationException> exception is raised.</span></span> <span data-ttu-id="b51d6-134">İstemciler ve hizmetler, seçeneğini belirlerseniz, birbirlerine bildirimde bulunan kendi protokollerini uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="b51d6-134">Clients and services can implement their own protocol to notify each other if they so choose.</span></span> <span data-ttu-id="b51d6-135">Hata işleme hakkında daha fazla bilgi için bkz. [WCF hata işleme](../wcf-error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="b51d6-135">For more information on error handling, see [WCF Error Handling](../wcf-error-handling.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="b51d6-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b51d6-136">See also</span></span>

- [<span data-ttu-id="b51d6-137">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="b51d6-137">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="b51d6-138">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="b51d6-138">Specifying Client Run-Time Behavior</span></span>](../specifying-client-run-time-behavior.md)
- [<span data-ttu-id="b51d6-139">Nasıl yapılır: Kanal fabrikası oluşturma ve kanal oluşturmak ve yönetmek için kullanın</span><span class="sxs-lookup"><span data-stu-id="b51d6-139">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
