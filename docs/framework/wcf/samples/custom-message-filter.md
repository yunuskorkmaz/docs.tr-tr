---
title: "Özel İleti Filtresi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37b8721fe1e56bda400f3254fd5d19f828df523e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-message-filter"></a>Özel İleti Filtresi
Bu örnek nasıl değiştirileceğini göstermektedir ileti filtreleri [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Uç noktalara iletileri gönderme kullanır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 İlk iletinin kanalda sunucuda geldiğinde sunucunun hangi (varsa) belirlemeniz gerekir ile ilişkili uç noktaları URI iletisini almanız gerekir. Bu süreci tarafından denetlenen <xref:System.ServiceModel.Dispatcher.MessageFilter> nesneleri iliştirilmiş <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Tek bir hizmetin her uç noktası olan <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Her ikisi de sahip bir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. Bu uç noktası için kullanılan İleti Filtresi bu iki filtre birleşimidir.  
  
 Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> hizmet uç noktanın eşleşen bir adresine gönderilen ileti bir uç noktayla eşleşen için <xref:System.ServiceModel.EndpointAddress>. Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> bir uç nokta gelen ileti eylem inceler ve eşleşen tüm iletisi hizmet uç noktası sözleşmenin işlemlerinin eylemlerinden biri karşılık gelen eylemi için (yalnızca `IsInitiating` = `true`eylemler olarak kabul edilir). Her iki ileti başlığına ise, sonuç olarak, varsayılan olarak, bir uç nokta için filtre yalnızca eşleşen <xref:System.ServiceModel.EndpointAddress> uç nokta ve ileti eylem endpoint işlem eylemlerden birini eşleşir.  
  
 Bu filtreler davranış kullanarak değiştirilebilir. Aşağıdaki örnekte hizmeti oluşturur bir <xref:System.ServiceModel.Description.IEndpointBehavior> bu yerine <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> üzerinde <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 İki adresi filtreleri tanımlanmıştır:  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 `FilteringEndpointBehavior` Yapılandırılabilir hale getirilen ve iki farklı farklılıklara izin verir.  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 Değişim 1 'e' içerebilir (ancak herhangi bir eylem sahip) adresleri eşleşen değişim 2 'e' eksik adreslerini eşleştirir ancak:  
  
```  
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 Yapılandırma dosyasında hizmetin yeni davranış kaydeder:  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 Hizmeti oluşturur sonra `endpointBehavior` her değişim için yapılandırmalar:  
  
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
  
 Son olarak, hizmet uç noktası birini başvuran `behaviorConfigurations`:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 İstemci uygulaması uygulanması kolaydır; hizmetin URI iki kanalı oluşturur (saniye olarak bu değer geçirerek (`via`) parametresi <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> ve her kanal, ancak üzerinde tek bir ileti gönderir her biri için farklı bir uç nokta adresler kullanır. Sonuç olarak, istemciden gelen giden iletiler belirtimler farklı olması ve sunucu tarafından istemcinin çıktı gösterildiği gibi uygun şekilde yanıt verir:  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Sunucu Yapılandırma dosyasındaki değişim geçiş takas için filtre neden olur ve istemci ters davranışı görür (iletiye `urn:e` başarılı olur, ancak iletiyi `urn:a` başarısız olur).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Tek makineli yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Makineler arası yapılandırmasında örneği çalıştırmak için yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md) ve Client.cs dosyasında aşağıdaki satırı değiştirin.  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Localhost sunucu adıyla değiştirin.  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.
