---
title: "Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2de8341be66952bd88de0a46d7c76675ab404aed
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme
İnceleme veya üzerinden gelen veya giden iletiler değiştirme bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulayarak istemci bir <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> ve istemci çalışma zamanına ekleniyor. Daha fazla bilgi için bkz: [genişletme istemcileri](../../../../docs/framework/wcf/extending/extending-clients.md). Hizmette eşdeğer bir özelliktir <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>. Tam kod örneği için bkz: [ileti denetçileri](../../../../docs/framework/wcf/samples/message-inspectors.md) örnek.  
  
### <a name="to-inspect-or-modify-messages"></a>İletileri incelemek veya değiştirmek için  
  
1.  Uygulama <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> arabirimi.  
  
2.  Uygulama bir <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> bağlı olarak istemci ileti denetçisi eklemek istediğiniz kapsam. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>uç nokta düzeyinde davranışını değiştirmenize izin verir. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>Sözleşme düzeyinde davranışını değiştirmenize izin verir.  
  
3.  Davranış çağrılmadan önce Ekle <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> yöntemi <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri, sırada göster:  
  
-   Bir istemci denetçisi uygulanması.  
  
-   Inspector ekler uç noktası davranışı.  
  
-   A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>-türetilmiş sınıf bir yapılandırma dosyasında davranışı eklemenizi sağlar.  
  
-   İstemci ileti denetçisi istemci çalışma zamanına ekler uç noktası davranışı ekler bir yapılandırma dosyası.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [Yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
