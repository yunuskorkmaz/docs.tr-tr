---
title: Özel İleti Filtresi
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 896407a218073eba53676baa4bcbd125593c80ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183884"
---
# <a name="custom-message-filter"></a><span data-ttu-id="f2087-102">Özel İleti Filtresi</span><span class="sxs-lookup"><span data-stu-id="f2087-102">Custom Message Filter</span></span>
<span data-ttu-id="f2087-103">Bu örnek, Windows Communication Foundation(WCF) iletiyi uç noktalara göndermek için kullandığı ileti filtrelerinin nasıl değiştirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2087-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2087-104">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="f2087-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f2087-105">Bir kanaldaki ilk ileti sunucuya ulaştığında, sunucunun uri ile ilişkili uç noktaların hangisini (varsa) alması gerektiğini belirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2087-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="f2087-106">Bu işlem, <xref:System.ServiceModel.Dispatcher.MessageFilter> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>bağlı nesneler tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="f2087-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="f2087-107">Bir hizmetin her bitiş <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>noktasının tek bir bitiş noktası vardır.</span><span class="sxs-lookup"><span data-stu-id="f2087-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="f2087-108">Hem <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> bir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> hem <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>de bir.</span><span class="sxs-lookup"><span data-stu-id="f2087-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="f2087-109">Bu iki filtrenin birleşimi, bu uç nokta için kullanılan ileti filtresidir.</span><span class="sxs-lookup"><span data-stu-id="f2087-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="f2087-110">Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> uç nokta, hizmet bitiş noktasının 'kiyle <xref:System.ServiceModel.EndpointAddress>eşleşen bir adrese gönderilen tüm iletilerle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="f2087-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="f2087-111">Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> bir uç nokta için gelen iletinin eylemini inceler ve herhangi bir iletiyi hizmet bitiş noktası sözleşmesinin işlemlerinden birine karşılık gelen bir eylemle eşleşir (yalnızca `IsInitiating` = `true` eylemler dikkate alınır).</span><span class="sxs-lookup"><span data-stu-id="f2087-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="f2087-112">Sonuç olarak, varsayılan olarak, bitiş noktası filtresi yalnızca iletinin To başlığı bitiş <xref:System.ServiceModel.EndpointAddress> noktasının ve iletinin eyleminin bitiş noktası işleminin eylemlerinden biriyle eşleşiyorsa eşleşir.</span><span class="sxs-lookup"><span data-stu-id="f2087-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="f2087-113">Bu filtreler bir davranış kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f2087-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="f2087-114">Örnekte, hizmet, <xref:System.ServiceModel.Description.IEndpointBehavior> aşağıdakilerin yerine aşağıdakileri <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A></span><span class="sxs-lookup"><span data-stu-id="f2087-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 <span data-ttu-id="f2087-115">İki adres filtresi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="f2087-115">Two address filters are defined:</span></span>  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 <span data-ttu-id="f2087-116">Bu `FilteringEndpointBehavior` yapılandırılabilir yapılır ve iki farklı varyasyonları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2087-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 <span data-ttu-id="f2087-117">Varyasyon 1 yalnızca 'e' (ancak herhangi bir Eylemi olan) içeren adreslerle eşleşirken, Varyasyon 2 yalnızca 'e' olmayan adreslerle eşleşir:</span><span class="sxs-lookup"><span data-stu-id="f2087-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="f2087-118">Yapılandırma dosyasında, hizmet yeni davranışı kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f2087-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 <span data-ttu-id="f2087-119">Ardından hizmet, `endpointBehavior` her varyasyon için yapılandırmalar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f2087-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
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
  
 <span data-ttu-id="f2087-120">Son olarak, hizmetin bitiş noktası `behaviorConfigurations`başvurularından biri:</span><span class="sxs-lookup"><span data-stu-id="f2087-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="f2087-121">İstemci uygulamasının uygulanması basittir; hizmetin URI'sine iki kanal oluşturur (bu değeri ikinci (`via`) parametresi olarak geçirerek <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> ve her kanalda tek bir ileti gönderir, ancak her kanal için farklı uç nokta adresleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2087-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="f2087-122">Sonuç olarak, istemciden gelen giden iletiler farklı To belirtmelerine sahiptir ve sunucu, istemcinin çıktısından gösterildiği gibi buna göre yanıt verir:</span><span class="sxs-lookup"><span data-stu-id="f2087-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="f2087-123">Sunucunun yapılandırma dosyasındaki varyasyonun değiştirilmesi filtrenin değiştirilmesine neden olur ve istemci ters `urn:e` davranışı görür (ileti `urn:a` başarılı olurken, ileti başarısız olur).</span><span class="sxs-lookup"><span data-stu-id="f2087-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="f2087-124">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2087-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f2087-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f2087-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f2087-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="f2087-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f2087-127">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2087-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f2087-128">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f2087-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f2087-129">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f2087-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="f2087-130">Örneği tek makineyapılandırmasında çalıştırmak [için, Windows Communication Foundation Samples'i çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f2087-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f2087-131">Örneği makineler arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştır'daki](../../../../docs/framework/wcf/samples/running-the-samples.md) yönergeleri izleyin ve Client.cs aşağıdaki satırı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2087-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="f2087-132">Localhost'u sunucu adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2087-132">Replace localhost with the name of server.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
