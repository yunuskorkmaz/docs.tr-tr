---
title: Özel İleti Filtresi
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 0b8336fe4d83f45369af31fe34b58696145d08c0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039918"
---
# <a name="custom-message-filter"></a>Özel İleti Filtresi
Bu örnek, Windows Communication Foundation (WCF) tarafından uç noktalara ileti göndermek için kullanılan ileti filtrelerinin nasıl değiştirileceğini gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bir kanaldaki ilk ileti sunucuya ulaştığında, sunucu bu URI ile ilişkili uç noktaların (varsa) iletiyi alacağını belirlemelidir. Bu işlem <xref:System.ServiceModel.Dispatcher.MessageFilter> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>öğesine eklenen nesneler tarafından denetlenir.  
  
 Bir hizmetin her uç noktası tek <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>bir. , <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Hema<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>hemdeiçerir. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> Bu iki filtrenin birleşimi, bu uç nokta için kullanılan ileti filtresidir.  
  
 Varsayılan <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> olarak, bir uç nokta için hizmet <xref:System.ServiceModel.EndpointAddress>uç noktası ile eşleşen bir adrese yönelik olan herhangi bir iletiyle eşleşir. Varsayılan <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> olarak, bir uç nokta için gelen ileti eylemini inceler ve hizmet uç noktası sözleşmesinin işlemlerindeki eylemlerden birine karşılık gelen bir eylemle eşleşen herhangi bir iletiyle eşleşir (yalnızca `IsInitiating` = `true`eylemler göz önünde bulundurululur). Sonuç olarak, varsayılan olarak, bir uç nokta için filtre yalnızca, uç noktanın üst bilgisi ise <xref:System.ServiceModel.EndpointAddress> ve ileti eylemi uç nokta işleminin eylemleriyle eşleştiğinde eşleşir.  
  
 Bu filtreler bir davranış kullanılarak değiştirilebilir. <xref:System.ServiceModel.Description.IEndpointBehavior> Örnekte, hizmet, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> ' <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>nin yerini aldığı bir oluşturur:  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 İki adres filtresi tanımlanmıştır:  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 `FilteringEndpointBehavior` Yapılandırılabilir hale getirilir ve iki farklı çeşitlemeye izin verir.  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 Çeşitleme 1 yalnızca bir ' e ' (herhangi bir eylem) içeren adreslerle eşleşir, ancak değişim 2 yalnızca ' e ' olmayan adreslerle eşleşir:  
  
```  
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
  
 Ardından hizmet her değişim `endpointBehavior` için yapılandırma oluşturur:  
  
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
  
 Son olarak, hizmetin uç noktası aşağıdakilerden birine `behaviorConfigurations`başvurur:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 İstemci uygulaması uygulaması basittir; hizmetin URI 'sine iki kanal oluşturur (Bu değeri ikinci (`via`) <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> parametresi olarak geçirerek her kanalda tek bir ileti gönderir, ancak her biri için farklı uç nokta adresleri kullanır. Sonuç olarak, istemciden gelen giden iletilerin belirlemeleri farklıdır ve sunucu, istemcinin çıkışıyla gösterildiği gibi buna uygun şekilde yanıt verir:  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Sunucunun yapılandırma dosyasındaki varyasyonın değiştirilmesi filtrenin değişmesine neden olur ve istemci karşı davranışı görür ( `urn:e` `urn:a` ileti başarısız olur, bu durum başarısız olur).  
  
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
2. Örneği tek makineli bir yapılandırmada çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Örneği bir çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md) bölümündeki yönergeleri izleyin ve Client.cs içinde aşağıdaki satırı değiştirin.  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Localhost değerini sunucu adıyla değiştirin.  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
