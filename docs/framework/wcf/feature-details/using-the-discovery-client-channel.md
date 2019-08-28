---
title: Keşif İstemcisi Kanalını Kullanma
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 3b6bb38298b47b822a15fee92038a1d6beb15df3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045249"
---
# <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma
Bir WCF istemci uygulaması yazarken, aradığınız hizmetin uç nokta adresini bilmeniz gerekir. Birçok durumda, bir hizmetin uç nokta adresi önceden bilinmiyor veya zaman içinde hizmet değişikliklerinin adresi. Bulma Istemci kanalı, bir WCF istemci uygulaması yazmanızı, çağırmak istediğiniz hizmeti açıklamanıza ve istemci kanalının otomatik olarak bir araştırma isteği göndermesi için izin verir. Bir hizmet yanıt verdiğinde, bulma istemci kanalı, araştırma yanıtından hizmet için uç nokta adresini alır ve hizmeti çağırmak için onu kullanır.  
  
## <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma  
 Bulma istemci kanalını kullanmak için, istemci kanal yığınınıza bir örneği <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> ekleyin. Alternatif olarak, <xref:System.ServiceModel.Discovery.DynamicEndpoint> zaten mevcut değilse ' <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> a ve Bağlamalarınızın otomatik olarak eklenmesini sağlayabilirsiniz.  
  
> [!CAUTION]
> İstemci kanal yığınınızın en <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> üstteki öğesi olması önerilir. Üzerine eklenen <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> herhangi bir bağlama öğesi, doğru bir şekilde içeremeyeceği için <xref:System.ServiceModel.ChannelFactory> , oluşturduğu veya kanalın oluşturduğu veya kanalın bitiş noktası adresini veya `Via` adresini ( `CreateChannel` yöntemine geçirilen) kullandığından emin olmalıdır adrestir.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Sınıfı iki ortak özellik içerir:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, çağırmak istediğiniz hizmeti tanımlamakta kullanılır.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>bulma iletilerinin gönderileceği bulma uç noktasını belirtir.  
  
 <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> Özelliği, aradığınız hizmet sözleşmesini, gerekli kapsam URI 'lerini ve kanalı açmak için en fazla süreyi belirtmenizi sağlar. Anlaşma türü, Oluşturucu <xref:System.ServiceModel.Discovery.FindCriteria>çağırarak belirtilir. Kapsam URI 'leri <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> özelliğine eklenebilir. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> Özelliği, istemcinin bağlanmaya çalışacağı en fazla sonuç sayısını belirtmenize olanak tanır. Bir araştırma yanıtı alındığında, istemci, araştırma yanıtından bitiş noktası adresini kullanarak kanalı açmaya çalışır. Bir özel durum oluşursa, istemci sonraki araştırma yanıtına döner ve gerekirse daha fazla yanıt alınması bekleniyor. Kanal başarıyla açılmadan veya en fazla sonuç sayısına ulaşılana kadar bunu yapmaya devam eder. Bu ayarlar hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria>.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> Özelliği, kullanılacak bulma uç noktasını belirtmenize olanak tanır. Normalde bu bir, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>ancak geçerli bir uç nokta olabilir.  
  
 Hizmetle iletişim kurmak için kullanmak üzere bağlama oluştururken, hizmetle aynı bağlamayı kullanmaya dikkat etmeniz gerekir. Tek fark, istemci bağlamasının yığının en üstünde bir <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> ' tır. Hizmet sistem tarafından belirtilen bağlamalardan birini kullanıyorsa, <xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> oluşturucuya sistem tarafından sağlanmış bağlamayı yeni bir oluşturun ve geçirin. Ardından <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> özelliğini<xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> çağırarak `Insert` ekleyebilirsiniz.  
  
 Bağlamaınıza ekledikten <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> ve yapılandırdıktan sonra, WCF istemci sınıfının bir örneğini oluşturabilir, açabilir ve yöntemlerini çağırabilirsiniz. Aşağıdaki örnek, `ICalculator` sınıfını uygulayan (Başlarken WCF öğreticisinde kullanılır) ve `Add` yöntemini çağıran bir WCF hizmetini bulmak için bulma istemci kanalını kullanır.  
  
```  
// Create the DiscoveryClientBindingElement  
DiscoveryClientBindingElement bindingElement = new DiscoveryClientBindingElement();  
// Search for a service that implements the ICalculator interface, attempting to open  
// the channel a maximum of 2 times  
bindingElement.FindCriteria = new FindCriteria(typeof(ICalculator)) { MaxResults = 2 };  
// Use the UdpDiscoveryEndpoint  
bindingElement.DiscoveryEndpoint = new UdpDiscoveryEndpoint();  
  
// The service uses the BasicHttpBinding, so use that and insert the DiscoveryClientBindingElement at the   
// top of the stack  
CustomBinding binding = new CustomBinding(new BasicHttpBinding());  
binding.Elements.Insert(0,bindingElement);  
  
try  
{  
    // Create the WCF client and call a method  
    CalculatorClient client = new CalculatorClient(binding, new EndpointAddress("http://schemas.microsoft.com/dynamic"));  
    client.Open();  
    client.Add(1, 1);  
}  
catch (EndpointNotFoundException ex)  
{  
    Console.WriteLine("An exception occurred: " + ex.Message);  
}  
```  
  
## <a name="security-and-the-discovery-client-channel"></a>Güvenlik ve bulma Istemci kanalı  
 Bulma istemci kanalını kullanırken iki uç nokta belirtilir. Bunlardan biri, genellikle <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>bulma iletileri için kullanılır ve diğeri uygulama uç noktasıdır. Güvenli bir hizmet uygularken, her iki bitiş noktasını güvenli hale getirmek için dikkatli olunmalıdır. Güvenlik hakkında daha fazla bilgi için bkz. [Hizmetleri ve Istemcileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
