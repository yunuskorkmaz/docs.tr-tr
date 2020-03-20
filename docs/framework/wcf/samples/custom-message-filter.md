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
# <a name="custom-message-filter"></a>Özel İleti Filtresi
Bu örnek, Windows Communication Foundation(WCF) iletiyi uç noktalara göndermek için kullandığı ileti filtrelerinin nasıl değiştirilebildiğini gösterir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bir kanaldaki ilk ileti sunucuya ulaştığında, sunucunun uri ile ilişkili uç noktaların hangisini (varsa) alması gerektiğini belirlemesi gerekir. Bu işlem, <xref:System.ServiceModel.Dispatcher.MessageFilter> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>bağlı nesneler tarafından denetlenir.  
  
 Bir hizmetin her bitiş <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>noktasının tek bir bitiş noktası vardır. Hem <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> bir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> hem <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>de bir. Bu iki filtrenin birleşimi, bu uç nokta için kullanılan ileti filtresidir.  
  
 Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> uç nokta, hizmet bitiş noktasının 'kiyle <xref:System.ServiceModel.EndpointAddress>eşleşen bir adrese gönderilen tüm iletilerle eşleşir. Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> bir uç nokta için gelen iletinin eylemini inceler ve herhangi bir iletiyi hizmet bitiş noktası sözleşmesinin işlemlerinden birine karşılık gelen bir eylemle eşleşir (yalnızca `IsInitiating` = `true` eylemler dikkate alınır). Sonuç olarak, varsayılan olarak, bitiş noktası filtresi yalnızca iletinin To başlığı bitiş <xref:System.ServiceModel.EndpointAddress> noktasının ve iletinin eyleminin bitiş noktası işleminin eylemlerinden biriyle eşleşiyorsa eşleşir.  
  
 Bu filtreler bir davranış kullanılarak değiştirilebilir. Örnekte, hizmet, <xref:System.ServiceModel.Description.IEndpointBehavior> aşağıdakilerin yerine aşağıdakileri <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 İki adres filtresi tanımlanır:  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 Bu `FilteringEndpointBehavior` yapılandırılabilir yapılır ve iki farklı varyasyonları sağlar.  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 Varyasyon 1 yalnızca 'e' (ancak herhangi bir Eylemi olan) içeren adreslerle eşleşirken, Varyasyon 2 yalnızca 'e' olmayan adreslerle eşleşir:  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 Yapılandırma dosyasında, hizmet yeni davranışı kaydeder:  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 Ardından hizmet, `endpointBehavior` her varyasyon için yapılandırmalar oluşturur:  
  
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
  
 Son olarak, hizmetin bitiş noktası `behaviorConfigurations`başvurularından biri:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 İstemci uygulamasının uygulanması basittir; hizmetin URI'sine iki kanal oluşturur (bu değeri ikinci (`via`) parametresi olarak geçirerek <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> ve her kanalda tek bir ileti gönderir, ancak her kanal için farklı uç nokta adresleri kullanır. Sonuç olarak, istemciden gelen giden iletiler farklı To belirtmelerine sahiptir ve sunucu, istemcinin çıktısından gösterildiği gibi buna göre yanıt verir:  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Sunucunun yapılandırma dosyasındaki varyasyonun değiştirilmesi filtrenin değiştirilmesine neden olur ve istemci ters `urn:e` davranışı görür (ileti `urn:a` başarılı olurken, ileti başarısız olur).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
2. Örneği tek makineyapılandırmasında çalıştırmak [için, Windows Communication Foundation Samples'i çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
3. Örneği makineler arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştır'daki](../../../../docs/framework/wcf/samples/running-the-samples.md) yönergeleri izleyin ve Client.cs aşağıdaki satırı değiştirin.  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Localhost'u sunucu adı ile değiştirin.  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
