---
title: 'Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 14c24c16a36be600881de402de50086dd18b30b4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796977"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="16bec-102">Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme</span><span class="sxs-lookup"><span data-stu-id="16bec-102">How to: Inspect or Modify Messages on the Client</span></span>
<span data-ttu-id="16bec-103">Bir WCF istemcisi genelinde gelen veya giden iletileri, bir <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> oluşturup istemci çalışma zamanına ekleyerek inceleyebilir veya değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16bec-103">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="16bec-104">Daha fazla bilgi için bkz. [Istemcileri genişletme](extending-clients.md).</span><span class="sxs-lookup"><span data-stu-id="16bec-104">For more information, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="16bec-105">Hizmetin eşdeğer özelliği <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16bec-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="16bec-106">Tüm kod örneği için bkz. [Ileti Inspectors](../samples/message-inspectors.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="16bec-106">For a complete code example see the [Message Inspectors](../samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="16bec-107">İletileri incelemek veya değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="16bec-107">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="16bec-108"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="16bec-108">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="16bec-109">İstemci ileti denetçisini <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> eklemek istediğiniz kapsama göre veyauygulayın.<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="16bec-109">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="16bec-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>uç nokta düzeyindeki davranışı değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="16bec-110"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="16bec-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>Sözleşme düzeyindeki davranışı değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="16bec-111"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3. <span data-ttu-id="16bec-112"><xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> Veya metodunuçağırmadan<xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>önce davranışını ekleyin. <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="16bec-112">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="16bec-113">Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="16bec-113">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16bec-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="16bec-114">Example</span></span>  
 <span data-ttu-id="16bec-115">Aşağıdaki kod örnekleri sırasıyla gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="16bec-115">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="16bec-116">Bir istemci denetçisi uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="16bec-116">A client inspector implementation.</span></span>  
  
- <span data-ttu-id="16bec-117">Inspector ekleyen bir uç nokta davranışı.</span><span class="sxs-lookup"><span data-stu-id="16bec-117">An endpoint behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="16bec-118">Bir <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>yapılandırma dosyasına davranışı eklemenize olanak tanıyan bir türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="16bec-118">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
- <span data-ttu-id="16bec-119">İstemci ileti denetçisini istemci çalışma zamanına ekleyen uç nokta davranışını ekleyen bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="16bec-119">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16bec-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16bec-120">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="16bec-121">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="16bec-121">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
