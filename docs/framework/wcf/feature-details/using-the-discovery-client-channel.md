---
title: Keşif İstemcisi Kanalını Kullanma
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: a74d0ba77977e158a6c6e469a9b6a88c8d1aac82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575985"
---
# <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma
Bir WCF istemci uygulaması yazarken, aradığınız hizmetin uç nokta adresini bilmeniz gerekir. Birçok durumda, bir hizmetin uç nokta adresi önceden bilinmiyor veya zaman içinde hizmet değişikliklerinin adresi. Bulma Istemci kanalı, bir WCF istemci uygulaması yazmanızı, çağırmak istediğiniz hizmeti açıklamanıza ve istemci kanalının otomatik olarak bir araştırma isteği göndermesi için izin verir. Bir hizmet yanıt verdiğinde, bulma istemci kanalı, araştırma yanıtından hizmet için uç nokta adresini alır ve hizmeti çağırmak için onu kullanır.  
  
## <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma  
 Bulma Istemci kanalını kullanmak için, <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> istemci kanal yığınınıza bir örneği ekleyin. Alternatif olarak, <xref:System.ServiceModel.Discovery.DynamicEndpoint> <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> zaten mevcut değilse ' a ve Bağlamalarınızın otomatik olarak eklenmesini sağlayabilirsiniz.  
  
> [!CAUTION]
> <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>İstemci kanal yığınınızın en üstteki öğesi olması önerilir. Üzerine eklenen herhangi bir bağlama öğesi, <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> <xref:System.ServiceModel.ChannelFactory> `Via` `CreateChannel` doğru adresi içeremeyeceği için, oluşturduğu veya kanalın oluşturduğu veya kanalın bitiş noktası adresini veya adresini kullanmadığından emin olmalıdır.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>Sınıfı iki ortak özellik içerir:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, çağırmak istediğiniz hizmeti tanımlamakta kullanılır.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>bulma iletilerinin gönderileceği bulma uç noktasını belirtir.  
  
 <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A>Özelliği, aradığınız hizmet sözleşmesini, gerekli kapsam URI 'lerini ve kanalı açmak için en fazla süreyi belirtmenizi sağlar. Anlaşma türü, Oluşturucu çağırarak belirtilir <xref:System.ServiceModel.Discovery.FindCriteria> . Kapsam URI 'Leri <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> özelliğine eklenebilir. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>Özelliği, istemcinin bağlanmaya çalışacağı en fazla sonuç sayısını belirtmenize olanak tanır. Bir araştırma yanıtı alındığında, istemci, araştırma yanıtından bitiş noktası adresini kullanarak kanalı açmaya çalışır. Bir özel durum oluşursa, istemci sonraki araştırma yanıtına döner ve gerekirse daha fazla yanıt alınması bekleniyor. Kanal başarıyla açılmadan veya en fazla sonuç sayısına ulaşılana kadar bunu yapmaya devam eder. Bu ayarlar hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria> ..  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>Özelliği, kullanılacak bulma uç noktasını belirtmenize olanak tanır. Normalde bu bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> , ancak geçerli bir uç nokta olabilir.  
  
 Hizmetle iletişim kurmak için kullanmak üzere bağlama oluştururken, hizmetle aynı bağlamayı kullanmaya dikkat etmeniz gerekir. Tek fark, istemci bağlamasının <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> yığının en üstünde bir ' tır. Hizmet sistem tarafından belirtilen bağlamalardan birini kullanıyorsa, <xref:System.ServiceModel.Channels.CustomBinding> oluşturucuya sistem tarafından sağlanmış bağlamayı yeni bir oluşturun ve geçirin <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> . Ardından <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> özelliğini çağırarak ekleyebilirsiniz `Insert` <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> .  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>Bağlamaınıza ekledikten ve yapılandırdıktan sonra, WCF istemci sınıfının bir örneğini oluşturabilir, açabilir ve yöntemlerini çağırabilirsiniz. Aşağıdaki örnek, `ICalculator` sınıfını uygulayan (Başlarken WCF öğreticisinde kullanılır) ve yöntemini çağıran BIR WCF hizmetini bulmak Için bulma Istemci kanalını kullanır `Add` .  
  
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
 Bulma istemci kanalını kullanırken iki uç nokta belirtilir. Bunlardan biri, genellikle bulma iletileri için kullanılır <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve diğeri uygulama uç noktasıdır. Güvenli bir hizmet uygularken, her iki bitiş noktasını güvenli hale getirmek için dikkatli olunmalıdır. Güvenlik hakkında daha fazla bilgi için bkz. [Hizmetleri ve Istemcileri güvenli hale getirme](securing-services-and-clients.md).
