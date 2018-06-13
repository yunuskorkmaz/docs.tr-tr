---
title: 'Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 6cd0f39494006bf51b7c4bb55afcc112ec08aadb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804176"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="bd350-102">Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme</span><span class="sxs-lookup"><span data-stu-id="bd350-102">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="bd350-103">İnceleme veya uygulayarak bir WCF istemcisi gelen veya giden iletiler değiştirme bir <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> ve istemci çalışma zamanına ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="bd350-103">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="bd350-104">Daha fazla bilgi için bkz: [genişletme istemcileri](../../../../docs/framework/wcf/extending/extending-clients.md).</span><span class="sxs-lookup"><span data-stu-id="bd350-104">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md).</span></span> <span data-ttu-id="bd350-105">Hizmette eşdeğer bir özelliktir <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bd350-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bd350-106">Tam kod örneği için bkz: [ileti denetçileri](../../../../docs/framework/wcf/samples/message-inspectors.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="bd350-106">For a complete code example see the [Message Inspectors](../../../../docs/framework/wcf/samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="bd350-107">İletileri incelemek veya değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="bd350-107">To inspect or modify messages</span></span>  
  
1.  <span data-ttu-id="bd350-108">Uygulama <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="bd350-108">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="bd350-109">Uygulama bir <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> bağlı olarak istemci ileti denetçisi eklemek istediğiniz kapsam.</span><span class="sxs-lookup"><span data-stu-id="bd350-109">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="bd350-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> uç nokta düzeyinde davranışını değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="bd350-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="bd350-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> Sözleşme düzeyinde davranışını değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="bd350-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3.  <span data-ttu-id="bd350-112">Davranış çağrılmadan önce Ekle <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> yöntemi <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bd350-112">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bd350-113">Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="bd350-113">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd350-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd350-114">Example</span></span>  
 <span data-ttu-id="bd350-115">Aşağıdaki kod örnekleri, sırada göster:</span><span class="sxs-lookup"><span data-stu-id="bd350-115">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="bd350-116">Bir istemci denetçisi uygulanması.</span><span class="sxs-lookup"><span data-stu-id="bd350-116">A client inspector implementation.</span></span>  
  
-   <span data-ttu-id="bd350-117">Inspector ekler uç noktası davranışı.</span><span class="sxs-lookup"><span data-stu-id="bd350-117">An endpoint behavior that inserts the inspector.</span></span>  
  
-   <span data-ttu-id="bd350-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>-türetilmiş sınıf bir yapılandırma dosyasında davranışı eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd350-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
-   <span data-ttu-id="bd350-119">İstemci ileti denetçisi istemci çalışma zamanına ekler uç noktası davranışı ekler bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="bd350-119">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bd350-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd350-120">See Also</span></span>  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [<span data-ttu-id="bd350-121">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="bd350-121">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
