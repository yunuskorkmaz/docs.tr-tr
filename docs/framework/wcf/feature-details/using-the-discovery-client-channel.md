---
title: Keşif İstemcisi Kanalını Kullanma
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 2d9dd68d233541f4d8cb3185adc1023cd5a19de1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184260"
---
# <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma
Bir WCF istemci uygulaması yazarken aradığınız hizmetin bitiş noktası adresini bilmeniz gerekir. Çoğu durumda, bir hizmetin bitiş noktası adresi önceden bilinmemektedir veya hizmetin adresi zaman içinde değişir. Discovery Client Channel bir WCF istemci uygulaması yazmanızı, aramak istediğiniz hizmeti açıklamanızı sağlar ve istemci kanalı otomatik olarak bir sonda isteği gönderir. Bir hizmet yanıt verdiğinde, bulma istemcisi kanalı sonda yanıtından hizmetin bitiş noktası adresini alır ve hizmeti aramak için kullanır.  
  
## <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma  
 Bulma İstemci Kanalı'nı kullanmak <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> için istemci kanal yığınınıza bir örnek ekleyin. Alternatif olarak kullanabilirsiniz <xref:System.ServiceModel.Discovery.DynamicEndpoint> ve <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> bir otomatik olarak zaten mevcut değilse bağlama eklenir.  
  
> [!CAUTION]
> İstemci <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> kanal yığınınızdaki en üst öğe olması önerilir. Üzerine <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> eklenen herhangi bir bağlama öğesi, doğru <xref:System.ServiceModel.ChannelFactory> adresi içermeyebileceğinden, oluşturduğu veya `Via` oluşturduğu kanalın bitiş `CreateChannel` noktası adresini veya adresini (yönteme geçirilen) kullanmadığından emin olmalıdır.  
  
 Sınıf <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> iki ortak özellik içerir:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, aramak istediğiniz hizmeti tanımlamak için kullanılır.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>hangi keşif iletileri göndermek için keşif bitiş noktası belirtir.  
  
 Özellik, <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> aradığınız hizmet sözleşmesini, gerekli kapsam Uri'lerini ve kanalı açmaya çalışmak için gereken maksimum süreyi belirtmenize olanak tanır. Sözleşme türü yapıcı çağırılarak <xref:System.ServiceModel.Discovery.FindCriteria>belirtilir. Kapsam URI'leri <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> tesise eklenebilir. Özellik, <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> istemcinin bağlanmaya çalıştığı maksimum sonuç sayısını belirtmenize olanak tanır. Sonda yanıtı alındığı zaman istemci, sonda yanıtından uç nokta adresini kullanarak kanalı açmaya çalışır. Bir özel durum oluşursa, istemci bir sonraki sonda yanıtına geçer ve gerekirse daha fazla yanıt alınmasını bekler. Kanal başarıyla açılana veya en fazla sonuç sayısına ulaşılıncaya kadar bunu yapmaya devam ediyor. Bu ayarlar hakkında daha <xref:System.ServiceModel.Discovery.FindCriteria>fazla bilgi için bkz.  
  
 Özellik, <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> kullanılacak keşif bitiş noktasını belirtmenize olanak tanır. Normalde bu bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ama herhangi bir geçerli bitiş noktası olabilir.  
  
 Hizmetle iletişim kurmak için kullanılacak bağlamayı oluştururken, hizmetle aynı bağlamayı kullanırken dikkatli olmalısınız. Tek fark, istemci bağlama <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> yığının üstünde bir olmasıdır. Hizmet sistem tarafından sağlanan bağlamalardan birini kullanıyorsa, <xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> sistem tarafından sağlanan bağlayıcıda yeni bir geçiş oluşturun ve geçirin. Daha sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> `Insert` <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> özelliği arayarak ekleyebilirsiniz.  
  
 Bağlamaya ekledikten <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> ve yapılandırdıktan sonra, WCF istemci sınıfının bir örneğini oluşturabilir, açabilir ve yöntemlerini çağırabilirsiniz. Aşağıdaki örnek, `ICalculator` sınıfı uygulayan (Başlangıç WCF öğreticisinde kullanılan) ve yöntemini `Add` çağıran bir WCF hizmetini bulmak için Discovery Client Channel'ı kullanır.  
  
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
  
## <a name="security-and-the-discovery-client-channel"></a>Güvenlik ve Discovery Client Channel  
 Bulma istemcisi kanalını kullanırken iki uç nokta belirtiliyor. Biri genellikle , ve diğer <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>uygulama bitiş noktası keşif iletileri için kullanılır. Güvenli bir hizmet uygularken, her iki uç noktanın da güvenliğini sağlamaya özen gerekir. Güvenlik hakkında daha fazla bilgi için, [Güvenlik Hizmetleri ve İstemciler'e](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)bakın.
