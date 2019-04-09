---
title: 'Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: cc2a03806dbc9ff33c1b16da7a31d862001534aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167485"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme
İnceleme veya uygulayarak bir WCF istemcisi gelen veya giden iletileri değiştirme bir <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> ve istemci çalışma zamanına ekleme. Daha fazla bilgi için [genişletme istemciler](../../../../docs/framework/wcf/extending/extending-clients.md). Hizmette eşdeğer özellik <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>. Tam kod örneği için bkz. [ileti denetçileri](../../../../docs/framework/wcf/samples/message-inspectors.md) örnek.  
  
### <a name="to-inspect-or-modify-messages"></a>İletileri denetleme veya değiştirme için  
  
1.  <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.  
  
2.  Uygulama bir <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> istemci ileti Inspector'ı eklemek istediğiniz kapsama bağlı olarak. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> uç nokta düzeyinde davranışı değiştirmenize izin verir. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> Sözleşme düzeyinde davranışı değiştirmenize izin verir.  
  
3.  Çağrılmadan önce davranışı eklemek <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodunda <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri, sırada göster:  
  
-   Bir istemci denetçisi uygulaması.  
  
-   Inspector ekleyen bir uç nokta davranışı.  
  
-   A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>-türetilmiş bir yapılandırma dosyasında davranışı eklemenizi sağlar sınıfını.  
  
-   İstemci çalışma zamanına istemci ileti denetçisi ekleyen bir uç nokta davranışı ekler bir yapılandırma dosyası.  
  
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
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
