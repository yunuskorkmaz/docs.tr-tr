---
title: Özel İleti Filtresi
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: c9a6e436548d4d1f009833f80899721c4c085513
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400145"
---
# <a name="custom-message-filter"></a>Özel İleti Filtresi
Bu örnek, Windows Communication Foundation (WCF) iletilerini uç noktalarına dağıtmak için kullandığı ileti filtreleri nasıl değiştirileceğini gösterir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 İlk iletinin bir kanalda sunucuda geldiğinde sunucunun hangi (varsa) belirlemelisiniz uç noktası ile ilişkili URI iletisini almanız gerekir. Bu süreci tarafından denetlenen <xref:System.ServiceModel.Dispatcher.MessageFilter> nesneleri iliştirilmiş <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Her bir hizmetin uç noktası tek bir sahip <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Hem de bir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. Bu iki filtreler için bu endpoint kullanılan İleti Filtresi birleşimdir.  
  
 Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> service uç noktasının eşleşen bir adrese gönderilen her mesaj bir uç nokta eşleşiyorsa <xref:System.ServiceModel.EndpointAddress>. Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> bir uç nokta gelen ileti eylemi olup olmadığını denetler ve eylemlerden biri, hizmet uç noktası sözleşmenin işlemleri için karşılık gelen bir eylem ile herhangi bir ileti ile eşleşir (yalnızca `IsInitiating` = `true`eylemleri olarak kabul edilir). Her iki ileti üst bilgisi için ise, sonuç olarak, varsayılan olarak, bir uç nokta için yalnızca eşleşen filtre <xref:System.ServiceModel.EndpointAddress> uç nokta ileti eylem ve uç nokta işlemin eylemlerden birini eşleşir.  
  
 Bu filtreler bir davranış kullanılarak değiştirilebilir. Bu örnekte hizmeti oluşturur bir <xref:System.ServiceModel.Description.IEndpointBehavior> bu yerini <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> üzerinde <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 İki adresi filtreleri tanımlanır:  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 `FilteringEndpointBehavior` Yapılandırılabilir oluşturulur ve iki farklı farklılıklara izin verir.  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 Değişim 1 'e' içeren (ancak herhangi bir işlem olan) adresleri eşleşen değişim 2 'e' eksik adresler eşleşen ise:  
  
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
  
 Hizmet oluşturur ardından `endpointBehavior` her değişim için yapılandırmalar:  
  
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
  
 İstemci uygulaması uygulanması kolaydır; hizmetin URI iki kanalı oluşturur (saniye olarak bu değeri geçirerek (`via`) parametresi <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> ve her kanal, ancak üzerinde tek bir ileti gönderen her biri için farklı bir uç nokta adresleri kullanır. Sonuç olarak, giden iletileri istemciden gösterimleri farklı olması ve sunucu tarafından istemcinin çıkış gösterildiği gibi uygun şekilde yanıt verir:  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Sunucunun yapılandırma dosyası varyasyonu geçiş öğe takas edilemediği için filtreyi neden olur ve istemci karşı davranışı görür (iletiyi `urn:e` başarılı olur, ancak iletinin `urn:a` başarısız olur).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Bir tek makineli yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Çapraz makine yapılandırmasında örneği çalıştırmak için konumundaki yönergeleri [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md) ve Client.cs dosyasında aşağıdaki satırı değiştirin.  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Localhost sunucusunun adı ile değiştirin.  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.
