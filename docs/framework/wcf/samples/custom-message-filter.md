---
title: Özel İleti Filtresi
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: d71f147a5664b44cf6ef37b4432e295344f0aee2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829399"
---
# <a name="custom-message-filter"></a><span data-ttu-id="bd639-102">Özel İleti Filtresi</span><span class="sxs-lookup"><span data-stu-id="bd639-102">Custom Message Filter</span></span>
<span data-ttu-id="bd639-103">Bu örnek, Windows Communication Foundation (WCF) iletilerini uç noktalarına dağıtmak için kullandığı ileti filtreleri nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd639-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd639-104">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="bd639-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bd639-105">İlk iletinin bir kanalda sunucuda geldiğinde sunucunun hangi (varsa) belirlemelisiniz uç noktası ile ilişkili URI iletisini almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd639-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="bd639-106">Bu süreci tarafından denetlenen <xref:System.ServiceModel.Dispatcher.MessageFilter> nesneleri iliştirilmiş <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="bd639-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="bd639-107">Her bir hizmetin uç noktası tek bir sahip <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="bd639-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="bd639-108"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Hem de bir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="bd639-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="bd639-109">Bu iki filtreler için bu endpoint kullanılan İleti Filtresi birleşimdir.</span><span class="sxs-lookup"><span data-stu-id="bd639-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="bd639-110">Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> service uç noktasının eşleşen bir adrese gönderilen her mesaj bir uç nokta eşleşiyorsa <xref:System.ServiceModel.EndpointAddress>.</span><span class="sxs-lookup"><span data-stu-id="bd639-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="bd639-111">Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> bir uç nokta gelen ileti eylemi olup olmadığını denetler ve eylemlerden biri, hizmet uç noktası sözleşmenin işlemleri için karşılık gelen bir eylem ile herhangi bir ileti ile eşleşir (yalnızca `IsInitiating` = `true`eylemleri olarak kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="bd639-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="bd639-112">Her iki ileti üst bilgisi için ise, sonuç olarak, varsayılan olarak, bir uç nokta için yalnızca eşleşen filtre <xref:System.ServiceModel.EndpointAddress> uç nokta ileti eylem ve uç nokta işlemin eylemlerden birini eşleşir.</span><span class="sxs-lookup"><span data-stu-id="bd639-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="bd639-113">Bu filtreler bir davranış kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bd639-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="bd639-114">Bu örnekte hizmeti oluşturur bir <xref:System.ServiceModel.Description.IEndpointBehavior> bu yerini <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> üzerinde <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span><span class="sxs-lookup"><span data-stu-id="bd639-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 <span data-ttu-id="bd639-115">İki adresi filtreleri tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="bd639-115">Two address filters are defined:</span></span>  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 <span data-ttu-id="bd639-116">`FilteringEndpointBehavior` Yapılandırılabilir oluşturulur ve iki farklı farklılıklara izin verir.</span><span class="sxs-lookup"><span data-stu-id="bd639-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 <span data-ttu-id="bd639-117">Değişim 1 'e' içeren (ancak herhangi bir işlem olan) adresleri eşleşen değişim 2 'e' eksik adresler eşleşen ise:</span><span class="sxs-lookup"><span data-stu-id="bd639-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```  
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="bd639-118">Yapılandırma dosyasında hizmetin yeni davranış kaydeder:</span><span class="sxs-lookup"><span data-stu-id="bd639-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 <span data-ttu-id="bd639-119">Hizmet oluşturur ardından `endpointBehavior` her değişim için yapılandırmalar:</span><span class="sxs-lookup"><span data-stu-id="bd639-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 <span data-ttu-id="bd639-120">Son olarak, hizmet uç noktası birini başvuran `behaviorConfigurations`:</span><span class="sxs-lookup"><span data-stu-id="bd639-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="bd639-121">İstemci uygulaması uygulanması kolaydır; hizmetin URI iki kanalı oluşturur (saniye olarak bu değeri geçirerek (`via`) parametresi <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> ve her kanal, ancak üzerinde tek bir ileti gönderen her biri için farklı bir uç nokta adresleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd639-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="bd639-122">Sonuç olarak, giden iletileri istemciden gösterimleri farklı olması ve sunucu tarafından istemcinin çıkış gösterildiği gibi uygun şekilde yanıt verir:</span><span class="sxs-lookup"><span data-stu-id="bd639-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="bd639-123">Sunucunun yapılandırma dosyası varyasyonu geçiş öğe takas edilemediği için filtreyi neden olur ve istemci karşı davranışı görür (iletiyi `urn:e` başarılı olur, ancak iletinin `urn:a` başarısız olur).</span><span class="sxs-lookup"><span data-stu-id="bd639-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd639-124">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="bd639-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd639-125">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bd639-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bd639-126">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="bd639-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd639-127">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="bd639-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bd639-128">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bd639-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bd639-129">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd639-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="bd639-130">Bir tek makineli yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd639-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="bd639-131">Çapraz makine yapılandırmasında örneği çalıştırmak için konumundaki yönergeleri [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md) ve Client.cs dosyasında aşağıdaki satırı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bd639-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="bd639-132">Localhost sunucusunun adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bd639-132">Replace localhost with the name of server.</span></span>  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
  
