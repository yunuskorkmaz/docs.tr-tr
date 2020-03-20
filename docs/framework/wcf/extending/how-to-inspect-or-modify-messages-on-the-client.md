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
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme
Bir WCF istemcisi üzerinden gelen veya giden iletileri bir <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> uygulama ve istemci çalışma süresine ekleyerek inceleyebilir veya değiştirebilirsiniz. Daha fazla bilgi için [bkz.](extending-clients.md) Hizmetteki eşdeğer özellik <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>. Tam bir kod örneği için [İleti Müfettişleri](../samples/message-inspectors.md) örneğine bakın.  
  
### <a name="to-inspect-or-modify-messages"></a>İletileri incelemek veya değiştirmek için  
  
1. <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.  
  
2. İstemci ileti denetçisini eklemek istediğiniz kapsama bağlı olarak bir <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> bağlı olarak uygulayın. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>bitiş noktası düzeyinde davranışı değiştirmenizi sağlar. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>sözleşme düzeyinde davranış değiştirmenize olanak sağlar.  
  
3. 'yi veya <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> yöntemi çağırmadan önce davranışı <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>ekleyin. Ayrıntılar için, [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme'ye](configuring-and-extending-the-runtime-with-behaviors.md)bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri sırayla gösterir:  
  
- Bir istemci denetçi uygulaması.  
  
- Denetçiyi ekleyen bir bitiş noktası davranışı.  
  
- A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- yapılandırma dosyasında davranış eklemek için izin veren türemiş sınıf.  
  
- İstemci ileti denetçisini istemci çalışma süresine ekleyen uç nokta davranışını ekleyen yapılandırma dosyası.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](configuring-and-extending-the-runtime-with-behaviors.md)
