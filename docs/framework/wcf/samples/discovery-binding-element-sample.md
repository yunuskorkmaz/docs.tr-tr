---
title: Keşif Bağlama Öğesi Örneği
ms.date: 03/30/2017
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
ms.openlocfilehash: d906d9a389c50095f2af5d52e3874c3e43199e68
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696215"
---
# <a name="discovery-binding-element-sample"></a>Keşif Bağlama Öğesi Örneği
Bu örnek, bir hizmet bulmak için bulma istemci bağlama öğesi kullanmayı gösterir. Bu özellik, geliştiricilerin çok sezgisel programlama modeli yaparak kendi mevcut istemci kanal yığınına bir keşif istemcisi kanalını eklemelerini sağlar. İlişkili kanalı açıldığında hizmetinin adresini bulma kullanılarak çözümlenir. Bu örnek aşağıdaki projeleri oluşur:  
  
-   **CalculatorService**: WCF kayıtlı bir bulunabilir hizmet.  
  
-   **CalculatorClient**: bir WCF istemcisi için arama yapın ve CalculatorService çağırmak için keşif istemcisi kanalını kullanan bir uygulama.  
  
-   **DynamicCalculatorClient**: bir WCF istemcisi için arama yapın ve CalculatorService çağırmak için dinamik bir uç nokta kullanan bir uygulama.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a>CalculatorService  
 Bu proje uygulayan basit hesap makinesi hizmette içeren `ICalculatorService` sözleşme.  
  
 Aşağıdaki App.config dosyasına eklemek için kullanılan bir `<serviceDiscovery>` hizmet davranışları ve bunun yanı sıra bulma uç noktası davranışı.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">  
        <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <!--Enable discovery through configuration.-->  
      <serviceBehaviors>  
        <behavior name="CalculatorBehavior">  
          <serviceDiscovery>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 Bu, hizmet ve kendi uç bulunabilmesini sağlar. CalculatorService ekleyen bir uç nokta NetTcpBinding bağlama kullanılarak şirket içinde barındırılan bir hizmettir. Ayrıca ekler bir `EndpointDiscoveryBehavior` uç noktasına ve aşağıdaki kodda gösterildiği gibi bir kapsam belirtiyor.  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a>CalculatorClient  
 Bu proje için CalculatorService iletiler gönderen bir istemci uygulaması içerir. Bu programın kullandığı `CreateCustomBindingWithDiscoveryElement()` keşif istemcisi kanalını özel bağlamayı oluşturmak için gereken yöntemini kullanır.  
  
```  
static CustomBinding CreateCustomBindingWithDiscoveryElement()  
 {  
      DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
            // Provide the search criteria and the endpoint over which the probe is sent  
            discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
            discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
            CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
            // Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
            // An exception is thrown if this binding element is not at the top  
            customBinding.Elements.Insert(0, discoveryBindingElement);  
  
            return customBinding; }  
```  
  
 Sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> olan örneği, geliştirici hizmeti için aramak için kullanılan ölçütü belirtir. Bu durumda, bulma bulma ölçüttür `ICalculatorService` türü. Ayrıca, geliştirici belirtir bir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> döndüren bir <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Hizmetleri aranacağı belirtir. <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Yeni döndürür <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örneği. Daha fazla bilgi için [keşif istemci kanalıyla özel bağlama kullanma](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
    // to the DiscoveryClientBindingElement. The Discovery ClientChannel   
    // uses this endpoint to send Probe message.  
    public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
    {  
        public override DiscoveryEndpoint GetDiscoveryEndpoint()  
        {  
            return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
        }  
    }  
```  
  
 Bu durumda, istemci UDP kullanan yerel alt ağdaki hizmetleri Bulma Protokolü tarafından tanımlanan çok noktaya yayın mekanizması. Yöntemin geri kalanı, özel bir bağlama oluşturur ve yığın üstüne bulma bağlama öğesi ekler.  
  
> [!NOTE]
>  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Bağlama yığınının üzerinde yerleştirilmelidir. Tüm <xref:System.ServiceModel.Channels.BindingElement> üst kısmındaki <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> kanalı oluşturur ve kanal fabrikası kullanmaz emin olmanız gerekir `EndpointAddress` veya `Via` özellikleri, gerçek adresi yalnızca keşif istemcisi kanalını bulunamadığından.  
  
 Ardından, `CalculatorClient` bir uç nokta adresi yanı sıra, bu özel bağlama geçirerek oluşturulabilir.  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 Keşif istemcisi kanalını kullanırken, belirtilen sabit bir uç nokta adresini daha önce geçirilen. Artık çalışma zamanında, Keşif istemcisi kanalını bulma ölçütleri tarafından belirtilen hizmetini bulur ve kendisine bağlar. Hizmet ve istemci bağlantı kurmak için Ayrıca aynı temel alınan bağlama yığına sahip olmalıdır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Bir çözüm açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Çözümü oluşturun.  
  
3.  Hizmet uygulaması ve her bir istemci uygulamaları çalıştırın.  
  
4.  İstemci hizmet adresini bilmeden bulamadı gözlemleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.
