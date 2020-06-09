---
title: Özel İleti Filtresi
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 0e4da0f2283fd537afe3cacdddfb36c327cfd3b4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600050"
---
# <a name="custom-message-filter"></a>Özel İleti Filtresi
Bu örnek, Windows Communication Foundation (WCF) tarafından uç noktalara ileti göndermek için kullanılan ileti filtrelerinin nasıl değiştirileceğini gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bir kanaldaki ilk ileti sunucuya ulaştığında, sunucu bu URI ile ilişkili uç noktaların (varsa) iletiyi alacağını belirlemelidir. Bu işlem <xref:System.ServiceModel.Dispatcher.MessageFilter> öğesine eklenen nesneler tarafından denetlenir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> .  
  
 Bir hizmetin her uç noktası tek bir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> . , <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Hem <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a hem de içerir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> . Bu iki filtrenin birleşimi, bu uç nokta için kullanılan ileti filtresidir.  
  
 Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> bir uç nokta için hizmet uç noktası ile eşleşen bir adrese yönelik olan herhangi bir iletiyle eşleşir <xref:System.ServiceModel.EndpointAddress> . Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> bir uç nokta için gelen ileti eylemini inceler ve hizmet uç noktası sözleşmesinin işlemlerindeki eylemlerden birine karşılık gelen bir eylemle eşleşen herhangi bir iletiyle eşleşir (yalnızca `IsInitiating` = `true` Eylemler göz önünde bulundurululur). Sonuç olarak, varsayılan olarak, bir uç nokta için filtre yalnızca, uç noktanın üst bilgisi ise <xref:System.ServiceModel.EndpointAddress> ve ileti eylemi uç nokta işleminin eylemleriyle eşleştiğinde eşleşir.  
  
 Bu filtreler bir davranış kullanılarak değiştirilebilir. Örnekte, hizmet, <xref:System.ServiceModel.Description.IEndpointBehavior> ve ' nin yerini aldığı bir oluşturur <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> :  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 İki adres filtresi tanımlanmıştır:  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 `FilteringEndpointBehavior`Yapılandırılabilir hale getirilir ve iki farklı çeşitlemeye izin verir.  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 Çeşitleme 1 yalnızca bir ' e ' (herhangi bir eylem) içeren adreslerle eşleşir, ancak değişim 2 yalnızca ' e ' olmayan adreslerle eşleşir:  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 Yapılandırma dosyasında hizmet yeni davranışı kaydeder:  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 Ardından hizmet `endpointBehavior` Her değişim için yapılandırma oluşturur:  
  
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
  
 Son olarak, hizmetin uç noktası aşağıdakilerden birine başvurur `behaviorConfigurations` :  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 İstemci uygulaması uygulaması basittir; hizmetin URI 'sine iki kanal oluşturur (Bu değeri ikinci ( `via` ) parametresi olarak geçirerek <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> her kanalda tek bir ileti gönderir, ancak her biri için farklı uç nokta adresleri kullanır. Sonuç olarak, istemciden gelen giden iletilerin belirlemeleri farklıdır ve sunucu, istemcinin çıkışıyla gösterildiği gibi buna uygun şekilde yanıt verir:  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Sunucunun yapılandırma dosyasındaki varyasyonın değiştirilmesi filtrenin değişmesine neden olur ve istemci karşı davranışı görür ( `urn:e` ileti başarısız olur, bu durum `urn:a` başarısız olur).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
2. Örneği tek makineli bir yapılandırmada çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Örneği bir çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md) bölümündeki yönergeleri izleyin ve Client.cs içinde aşağıdaki satırı değiştirin.  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Localhost değerini sunucu adıyla değiştirin.  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
