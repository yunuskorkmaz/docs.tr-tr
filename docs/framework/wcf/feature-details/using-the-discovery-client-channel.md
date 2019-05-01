---
title: Keşif İstemcisi Kanalını Kullanma
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 298cafe34b20a3644f967acf15f831be5b0b90ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932702"
---
# <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma
WCF istemci uygulaması yazarken, aradığınız Hizmeti uç nokta adresini bilmeniz gerekir. Çoğu durumda, bir hizmetin uç nokta adresini önceden bilinmiyor veya hizmet adresini zamanla değişir. Keşif istemcisi kanalını aramak istediğiniz hizmet ve istemci kanal bir araştırma isteğinin otomatik olarak gönderir. bir WCF istemci uygulaması yazma sağlar. Bir hizmet yanıt verdiğinde, Keşif istemcisi kanalını araştırma yanıtı hizmeti için uç nokta adresini alır ve hizmeti çağırmak amacıyla kullanır.  
  
## <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma  
 Keşif istemcisi kanalını kullanmak için bir örneğini ekleme <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> istemci kanal yığınınızı için. Alternatif olarak <xref:System.ServiceModel.Discovery.DynamicEndpoint> ve <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> zaten mevcut değilse, bağlamayı otomatik olarak eklenir.  
  
> [!CAUTION]
>  Önerilir <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> istemci kanal yığınınızı en üst öğedir. Üst kısmındaki eklenen herhangi bir bağlama öğesi <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> emin olmanız gerekir <xref:System.ServiceModel.ChannelFactory> veya kanalı oluşturur, uç nokta adresini kullanmaz veya `Via` adresi (geçirilen `CreateChannel` yöntemi) çünkü bunlar doğru içeremez adresi.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Sınıfı iki genel özellikleri içerir:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, çağırmak istediğiniz hizmet için kullanılır.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> bulma ileti göndermek için bulma uç noktası belirtir.  
  
 <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> Özelliği, aradığınız hizmet sözleşmesini belirtmenize olanak sağlar, gerekli tüm URI kapsam ve zaman kanalı açma denemesi sayısı. Sözleşme türü oluşturucusunu çağırarak belirtilen <xref:System.ServiceModel.Discovery.FindCriteria>. Kapsam bir URI'leri eklenebilir <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> özelliği. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> Özelliği, istemci çalışır bağlanmak istediğiniz sonuçları sayısı belirtmenize olanak sağlar. Bir araştırma yanıtı alındığında istemci kullanarak uç nokta adresini araştırma yanıtından kanalını açmayı dener. Bir özel durum oluşursa istemci İleri Araştırma yanıt, gerekirse alınabilmesi daha fazla yanıtlarını beklemek geçer. Bunu kanal başarıyla açıldı veya maksimum sonuç sayısı ulaşılana kadar devam eder. Bu ayarlar hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Discovery.FindCriteria>.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> Özelliğini kullanmak için bulma uç noktası belirtmenize olanak verir. Normalde bu, bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ancak herhangi bir geçerli uç nokta olabilir.  
  
 Hizmetiyle iletişim kurmak için kullanılacak bağlamanın oluştururken, hizmet olarak tam aynı bağlamayı kullanmak dikkatli olmanız gerekir. Bağlama istemci tek fark, bir <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> yığının en üstündeki. Hizmet sistem tarafından sağlanan bağlamalar birini kullanırken, yeni bir oluşturma <xref:System.ServiceModel.Channels.CustomBinding> ve sistem tarafından sağlanan bir bağlamayı için geçirin <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> Oluşturucusu. Ekleyebileceğiniz sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> çağırarak `Insert` üzerinde <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> özelliği.  
  
 Siz ekledikten sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , bağlama için ve, yapılandırılmış bir WCF istemcisi sınıfı örneğini oluşturmak, açın ve kendi yöntemlerini çağırın. Aşağıdaki örnek keşif istemcisi kanalını uygulayan bir WCF hizmeti bulmak için kullanır. `ICalculator` sınıfı (çalışmaya WCF başlama öğreticisinde kullanılan) ve çağrılarını kendi `Add` yöntemi.  
  
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
  
## <a name="security-and-the-discovery-client-channel"></a>Güvenlik ve keşif istemcisi kanalını  
 Keşif istemcisi kanalını kullanma, iki uç nokta belirtilir. Bir kullanılan bulma iletileri için genellikle <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ve diğer uygulama uç noktadır. Güvenli bir hizmetin uygularken, her iki uç noktalarını güvenli hale getirmek için dikkatli olunması gerekir. Güvenlik hakkında daha fazla bilgi için bkz: [Hizmetleri güvenli hale getirme ve istemciler](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
