---
title: 'Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme'
description: Uygun arabirimi uygulayarak bir WCF istemcisi veya hizmeti genelinde gelen veya giden iletileri incelemeyi veya değiştirmeyi öğrenin.
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 6f6a3d20d7f3a9fb79de5cd3e29096e270d0f188
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247513"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme
Bir WCF istemcisi genelinde gelen veya giden iletileri, bir <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> oluşturup istemci çalışma zamanına ekleyerek inceleyebilir veya değiştirebilirsiniz. Daha fazla bilgi için bkz. [Istemcileri genişletme](extending-clients.md). Hizmetin eşdeğer özelliği <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> . Tüm kod örneği için bkz. [Ileti Inspectors](../samples/message-inspectors.md) örneği.  
  
### <a name="to-inspect-or-modify-messages"></a>İletileri incelemek veya değiştirmek için  
  
1. <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.  
  
2. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> İstemci ileti denetçisini eklemek istediğiniz kapsama göre veya uygulayın. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>uç nokta düzeyindeki davranışı değiştirmenize izin verir. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>Sözleşme düzeyindeki davranışı değiştirmenize izin verir.  
  
3. Veya metodunu çağırmadan önce davranışını ekleyin <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> . Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri sırasıyla gösterilmektedir:  
  
- Bir istemci denetçisi uygulamasıdır.  
  
- Inspector ekleyen bir uç nokta davranışı.  
  
- Bir <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> yapılandırma dosyasına davranışı eklemenize olanak tanıyan bir türetilmiş sınıf.  
  
- İstemci ileti denetçisini istemci çalışma zamanına ekleyen uç nokta davranışını ekleyen bir yapılandırma dosyası.  
  
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
