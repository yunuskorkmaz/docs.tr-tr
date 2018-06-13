---
title: Özel İleti Filtresi
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: d01fd0d08a7f5d9b12007bc22a26e6f08e006b64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504152"
---
# <a name="custom-message-filter"></a><span data-ttu-id="94682-102">Özel İleti Filtresi</span><span class="sxs-lookup"><span data-stu-id="94682-102">Custom Message Filter</span></span>
<span data-ttu-id="94682-103">Bu örnek, uç noktalara iletileri gönderme Windows Communication Foundation (WCF) kullanan ileti filtreleri değiştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="94682-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94682-104">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="94682-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="94682-105">İlk iletinin kanalda sunucuda geldiğinde sunucunun hangi (varsa) belirlemeniz gerekir ile ilişkili uç noktaları URI iletisini almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="94682-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="94682-106">Bu süreci tarafından denetlenen <xref:System.ServiceModel.Dispatcher.MessageFilter> nesneleri iliştirilmiş <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="94682-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="94682-107">Tek bir hizmetin her uç noktası olan <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="94682-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="94682-108"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Her ikisi de sahip bir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="94682-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="94682-109">Bu uç noktası için kullanılan İleti Filtresi bu iki filtre birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="94682-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="94682-110">Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> hizmet uç noktanın eşleşen bir adresine gönderilen ileti bir uç noktayla eşleşen için <xref:System.ServiceModel.EndpointAddress>.</span><span class="sxs-lookup"><span data-stu-id="94682-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="94682-111">Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> bir uç nokta gelen ileti eylem inceler ve eşleşen tüm iletisi hizmet uç noktası sözleşmenin işlemlerinin eylemlerinden biri karşılık gelen eylemi için (yalnızca `IsInitiating` = `true`eylemler olarak kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="94682-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="94682-112">Her iki ileti başlığına ise, sonuç olarak, varsayılan olarak, bir uç nokta için filtre yalnızca eşleşen <xref:System.ServiceModel.EndpointAddress> uç nokta ve ileti eylem endpoint işlem eylemlerden birini eşleşir.</span><span class="sxs-lookup"><span data-stu-id="94682-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="94682-113">Bu filtreler davranış kullanarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="94682-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="94682-114">Aşağıdaki örnekte hizmeti oluşturur bir <xref:System.ServiceModel.Description.IEndpointBehavior> bu yerine <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> üzerinde <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span><span class="sxs-lookup"><span data-stu-id="94682-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 <span data-ttu-id="94682-115">İki adresi filtreleri tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="94682-115">Two address filters are defined:</span></span>  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 <span data-ttu-id="94682-116">`FilteringEndpointBehavior` Yapılandırılabilir hale getirilen ve iki farklı farklılıklara izin verir.</span><span class="sxs-lookup"><span data-stu-id="94682-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 <span data-ttu-id="94682-117">Değişim 1 'e' içerebilir (ancak herhangi bir eylem sahip) adresleri eşleşen değişim 2 'e' eksik adreslerini eşleştirir ancak:</span><span class="sxs-lookup"><span data-stu-id="94682-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```  
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="94682-118">Yapılandırma dosyasında hizmetin yeni davranış kaydeder:</span><span class="sxs-lookup"><span data-stu-id="94682-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 <span data-ttu-id="94682-119">Hizmeti oluşturur sonra `endpointBehavior` her değişim için yapılandırmalar:</span><span class="sxs-lookup"><span data-stu-id="94682-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
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
  
 <span data-ttu-id="94682-120">Son olarak, hizmet uç noktası birini başvuran `behaviorConfigurations`:</span><span class="sxs-lookup"><span data-stu-id="94682-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="94682-121">İstemci uygulaması uygulanması kolaydır; hizmetin URI iki kanalı oluşturur (saniye olarak bu değer geçirerek (`via`) parametresi <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> ve her kanal, ancak üzerinde tek bir ileti gönderir her biri için farklı bir uç nokta adresler kullanır.</span><span class="sxs-lookup"><span data-stu-id="94682-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="94682-122">Sonuç olarak, istemciden gelen giden iletiler belirtimler farklı olması ve sunucu tarafından istemcinin çıktı gösterildiği gibi uygun şekilde yanıt verir:</span><span class="sxs-lookup"><span data-stu-id="94682-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="94682-123">Sunucu Yapılandırma dosyasındaki değişim geçiş takas için filtre neden olur ve istemci ters davranışı görür (iletiye `urn:e` başarılı olur, ancak iletiyi `urn:a` başarısız olur).</span><span class="sxs-lookup"><span data-stu-id="94682-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="94682-124">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="94682-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94682-125">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="94682-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="94682-126">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="94682-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94682-127">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="94682-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="94682-128">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="94682-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="94682-129">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94682-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="94682-130">Tek makineli yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94682-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="94682-131">Makineler arası yapılandırmasında örneği çalıştırmak için yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md) ve Client.cs dosyasında aşağıdaki satırı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="94682-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="94682-132">Localhost sunucu adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="94682-132">Replace localhost with the name of server.</span></span>  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="94682-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94682-133">See Also</span></span>
