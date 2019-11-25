---
title: Keşif İstemcisi Kanalını Kullanma
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 05ca54d62179d024e619bc5c9c70a4e08b9dd62f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975949"
---
# <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma
Bir WCF istemci uygulaması yazarken, aradığınız hizmetin uç nokta adresini bilmeniz gerekir. Birçok durumda, bir hizmetin uç nokta adresi önceden bilinmiyor veya zaman içinde hizmet değişikliklerinin adresi. Bulma Istemci kanalı, bir WCF istemci uygulaması yazmanızı, çağırmak istediğiniz hizmeti açıklamanıza ve istemci kanalının otomatik olarak bir araştırma isteği göndermesi için izin verir. Bir hizmet yanıt verdiğinde, bulma istemci kanalı, araştırma yanıtından hizmet için uç nokta adresini alır ve hizmeti çağırmak için onu kullanır.  
  
## <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma  
 Bulma Istemci kanalını kullanmak için, <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> bir örneğini istemci kanal yığınınıza ekleyin. Alternatif olarak, <xref:System.ServiceModel.Discovery.DynamicEndpoint> de kullanabilirsiniz <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> ve henüz yoksa, bağlamalarınız otomatik olarak eklenir.  
  
> [!CAUTION]
> <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, istemci kanal yığınınızın en üstteki öğesi olması önerilir. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> üstüne eklenen herhangi bir bağlama öğesi, doğru adresi içeremeyeceği için, oluşturduğu <xref:System.ServiceModel.ChannelFactory> veya kanalın bir uç nokta adresini veya `Via` adresini (`CreateChannel` yöntemine geçirilmiş) kullanmadığından emin olmalıdır.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> sınıfı iki ortak özellik içerir:  
  
1. çağırmak istediğiniz hizmeti tanımlamakta kullanılan <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>.  
  
2. bulma iletilerinin gönderileceği bulma uç noktasını belirten <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>.  
  
 <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> özelliği, aradığınız hizmet sözleşmesini, gerekli tüm kapsam URI 'Lerini ve kanalı açmak için en fazla zaman sayısını belirtmenize olanak tanır. Anlaşma türü, Oluşturucu <xref:System.ServiceModel.Discovery.FindCriteria>çağırarak belirtilir. Kapsam URI 'Leri <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> özelliğine eklenebilir. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> özelliği, istemcinin bağlanmaya çalışacağı en fazla sonuç sayısını belirtmenize olanak tanır. Bir araştırma yanıtı alındığında, istemci, araştırma yanıtından bitiş noktası adresini kullanarak kanalı açmaya çalışır. Bir özel durum oluşursa, istemci sonraki araştırma yanıtına döner ve gerekirse daha fazla yanıt alınması bekleniyor. Kanal başarıyla açılmadan veya en fazla sonuç sayısına ulaşılana kadar bunu yapmaya devam eder. Bu ayarlar hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Discovery.FindCriteria>.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> özelliği, kullanılacak bulma uç noktasını belirtmenize olanak tanır. Normalde bu bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ancak geçerli bir uç nokta olabilir.  
  
 Hizmetle iletişim kurmak için kullanmak üzere bağlama oluştururken, hizmetle aynı bağlamayı kullanmaya dikkat etmeniz gerekir. Tek fark, istemci bağlamasının yığının en üstünde bir <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> sahiptir. Hizmet sistem tarafından belirtilen bağlamalardan birini kullanıyorsa, yeni bir <xref:System.ServiceModel.Channels.CustomBinding> oluşturun ve <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> oluşturucusuna sistem tarafından sağlanmış bağlamayı geçirin. Daha sonra, <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> özelliğine `Insert` çağırarak <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> ekleyebilirsiniz.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> bağlamaınıza ekledikten ve yapılandırdıktan sonra, WCF istemci sınıfının bir örneğini oluşturabilir, açabilir ve yöntemlerini çağırabilirsiniz. Aşağıdaki örnek, `ICalculator` sınıfını uygulayan (Başlarken WCF öğreticisinde kullanılır) ve `Add` yöntemini çağıran bir WCF hizmetini bulmak için bulma Istemci kanalını kullanır.  
  
```csharp
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
 Bulma istemci kanalını kullanırken iki uç nokta belirtilir. Bunlardan biri, genellikle <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>ve diğeri uygulama uç noktasıdır. bulma iletileri için kullanılır. Güvenli bir hizmet uygularken, her iki bitiş noktasını güvenli hale getirmek için dikkatli olunmalıdır. Güvenlik hakkında daha fazla bilgi için bkz. [Hizmetleri ve Istemcileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
