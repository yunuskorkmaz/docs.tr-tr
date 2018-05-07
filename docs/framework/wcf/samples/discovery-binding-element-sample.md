---
title: Keşif Bağlama Öğesi Örneği
ms.date: 03/30/2017
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
ms.openlocfilehash: 7dc38acbe91e03f579414294da07bff5cc53cc4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="discovery-binding-element-sample"></a>Keşif Bağlama Öğesi Örneği
Bu örnek, bir hizmet bulmak için bulma istemci bağlama öğesi kullanılacak gösterilmiştir. Bu özellik, bir keşif istemcisi kanalını programlama modeli çok sezgisel hale getirme, mevcut istemci kanal yığınına eklemek için geliştiricilere sağlar. İlişkili kanalı açıldığında hizmetinin adresini bulma kullanılarak çözümlenir. Bu örnek aşağıdaki projeleri oluşur:  
  
-   **CalculatorService**: bir bulunabilirlik [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
-   **CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aramak ve CalculatorService çağırmak için keşif istemcisi kanalını kullanan istemci uygulaması.  
  
-   **DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aramak ve CalculatorService çağırmak için dinamik bir uç noktası kullanan istemci uygulaması.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a>CalculatorService  
 Bu proje uygulayan bir basit hesap makinesi hizmetinin içeriyor `ICalculatorService` sözleşme.  
  
 Aşağıdaki App.config dosyası eklemek için kullanılan bir `<serviceDiscovery>` hizmet davranışları ve bunun yanı sıra bulma uç noktası davranışı.  
  
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
  
 Bu, hizmet ve bitiş noktaları bulunabilirlik kolaylaştırır. CalculatorService NetTcpBinding bağlama kullanarak bir uç nokta ekler kendini barındıran bir hizmettir. Ayrıca ekler bir `EndpointDiscoveryBehavior` uç noktasına ve aşağıdaki kodda gösterildiği gibi bir kapsam belirtir.  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a>CalculatorClient  
 Bu proje için CalculatorService iletileri gönderen bir istemci uygulaması içerir. Bu programın kullandığı `CreateCustomBindingWithDiscoveryElement()` yöntemi bir özel, bağlama oluşturmak için keşif istemcisi kanalını kullanır.  
  
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
  
 Sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> olan örneği, geliştirici için bir hizmet ararken kullanılacak ölçütleri belirtir. Bu durumda, bulma bulma ölçüttür `ICalculatorService` türü. Ayrıca, geliştirici belirten bir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> döndüren bir <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> nerede Hizmetleri araması belirtir. <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Yeni döndürür <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örneği. Daha fazla bilgi için bkz: [keşif istemci kanalıyla özel bağlama kullanma](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).  
  
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
  
 Bu durumda, istemci UDP kullanan Hizmetleri yerel alt ağda aramak için keşif protokolü tarafından tanımlanan çok noktaya yayın mekanizması. Yöntem kalanı özel bağlama oluşturur ve yığının en üstte keşif bağlama öğesi ekler.  
  
> [!NOTE]
>  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Bağlama yığının üst kısmında yer almalıdır. Tüm <xref:System.ServiceModel.Channels.BindingElement> üstünde <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> kanal fabrikası veya oluşturduğu kanal kullanmayan emin olmanız gerekir `EndpointAddress` veya `Via` özellikler, gerçek adresini yalnızca keşif istemcisi kanalını bulunamadığı için.  
  
 Ardından, `CalculatorClient` bir uç nokta adresi yanı sıra, bu özel bağlama geçirerek oluşturulabilir.  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 Keşif istemcisi kanalını kullanırken, belirtilen sabit uç noktası adresi daha önce geçirilen. Artık çalışma zamanında keşif istemcisi kanalını bulma ölçütleri tarafından belirtilen hizmetini bulur ve kendisine bağlar. Hizmet ve bağlantı kurmak için istemci için de aynı temel bağlama yığınına olmalıdır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Çözümde açmak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Çözümü oluşturun.  
  
3.  Hizmet uygulaması ve her bir istemci uygulamaları çalıştırın.  
  
4.  İstemci hizmet adresini bilmeden bulamıyor gözlemleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.
