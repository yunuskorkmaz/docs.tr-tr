---
title: 'Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: db1a99d2ed1f765e39815e6b6c70d6ada1db1d15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185534"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="39cfa-102">Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme</span><span class="sxs-lookup"><span data-stu-id="39cfa-102">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="39cfa-103">Bir WCF istemcisi üzerinden gelen veya giden iletileri bir <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> uygulama ve istemci çalışma süresine ekleyerek inceleyebilir veya değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39cfa-103">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="39cfa-104">Daha fazla bilgi için [bkz.](extending-clients.md)</span><span class="sxs-lookup"><span data-stu-id="39cfa-104">For more information, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="39cfa-105">Hizmetteki eşdeğer özellik <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="39cfa-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="39cfa-106">Tam bir kod örneği için [İleti Müfettişleri](../samples/message-inspectors.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="39cfa-106">For a complete code example see the [Message Inspectors](../samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="39cfa-107">İletileri incelemek veya değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="39cfa-107">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="39cfa-108"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="39cfa-108">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="39cfa-109">İstemci ileti denetçisini eklemek istediğiniz kapsama bağlı olarak bir <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> bağlı olarak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="39cfa-109">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="39cfa-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>bitiş noktası düzeyinde davranışı değiştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="39cfa-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="39cfa-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>sözleşme düzeyinde davranış değiştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="39cfa-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3. <span data-ttu-id="39cfa-112">'yi veya <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> yöntemi çağırmadan önce davranışı <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>ekleyin.</span><span class="sxs-lookup"><span data-stu-id="39cfa-112">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="39cfa-113">Ayrıntılar için, [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme'ye](configuring-and-extending-the-runtime-with-behaviors.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="39cfa-113">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39cfa-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="39cfa-114">Example</span></span>  
 <span data-ttu-id="39cfa-115">Aşağıdaki kod örnekleri sırayla gösterir:</span><span class="sxs-lookup"><span data-stu-id="39cfa-115">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="39cfa-116">Bir istemci denetçi uygulaması.</span><span class="sxs-lookup"><span data-stu-id="39cfa-116">A client inspector implementation.</span></span>  
  
- <span data-ttu-id="39cfa-117">Denetçiyi ekleyen bir bitiş noktası davranışı.</span><span class="sxs-lookup"><span data-stu-id="39cfa-117">An endpoint behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="39cfa-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- yapılandırma dosyasında davranış eklemek için izin veren türemiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="39cfa-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
- <span data-ttu-id="39cfa-119">İstemci ileti denetçisini istemci çalışma süresine ekleyen uç nokta davranışını ekleyen yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="39cfa-119">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"
                      binding="wsHttpBinding"
                      behaviorConfiguration="clientInspectorsAdded"
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39cfa-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39cfa-120">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="39cfa-121">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="39cfa-121">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
