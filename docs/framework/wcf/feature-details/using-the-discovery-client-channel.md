---
title: "Keşif İstemcisi Kanalını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f012cc43d7160b737e5a9a5d4ceb5e50e91d07a1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma
Bir WCF istemcisi uygulama yazarken, aradığınız hizmet uç noktası adresi bilmeniz gerekir. Çoğu durumda, bir hizmetin uç noktası adresi önceden bilinmiyor veya zamanla hizmetinin adresini değiştirir. Keşif istemcisi kanalını aramak istediğiniz hizmetini tanımlayan ve istemci kanal otomatik olarak bir yoklama isteği gönderir bir WCF istemci uygulaması yazmanızı sağlar. Bir hizmet yanıtladığında keşif istemcisi kanalını hizmeti için uç nokta adresi araştırma yanıtı alır ve hizmeti çağırmak için kullanır.  
  
## <a name="using-the-discovery-client-channel"></a>Keşif İstemcisi Kanalını Kullanma  
 Keşif istemcisi kanalını kullanmak için bir örnek ekler <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> istemci kanal yığınına. Alternatif olarak kullanabileceğiniz <xref:System.ServiceModel.Discovery.DynamicEndpoint> ve <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> zaten yüklü değilse, bağlama otomatik olarak eklenir.  
  
> [!CAUTION]
>  Önerilir <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , istemci kanal yığında en üstteki öğesidir. Üstünde eklenen herhangi bir bağlama öğesi <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> emin olmanız gerekir <xref:System.ServiceModel.ChannelFactory> veya kanal oluşturur, uç nokta adresi kullanmaz veya `Via` adresi (geçirilen `CreateChannel` yöntemi) çünkü bunlar doğru içeremez adresi.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Sınıfı iki genel özellikleri içerir:  
  
1.  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, istediğiniz çağırmak için hizmeti açıklamak için kullanılır.  
  
2.  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>bulma ileti göndermek için bulma uç noktası belirtir.  
  
 <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> Özellik aradığınız hizmet sözleşmesini belirtmenize olanak tanır, gerekli tüm kapsam URI'ler ve kanalını açmayı denemek için saat sayısı. Oluşturucu çağırarak belirtilen sözleşme türü <xref:System.ServiceModel.Discovery.FindCriteria>. Kapsam URI'ler eklenebilir <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> özelliği. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> Özelliği için istemci çalıştığı bağlanmak sonuçları sayısını belirtmenize olanak verir. Bir araştırma yanıtı aldığında istemci yoklama yanıtı uç nokta adresinden kullanarak kanalını açmayı dener. Bir özel durum oluşursa, istemcinin sonraki yoklama yanıtı gerekiyorsa alınabilmesi daha fazla yanıt bekleniyor geçer. Kanal başarıyla açıldı veya sonuçları sayısı üst sınırına kadar bunun devam eder. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz. Bu ayarları <xref:System.ServiceModel.Discovery.FindCriteria>.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> Özelliğini kullanmak için bulma uç noktası belirtmenize olanak verir. Normalde bu olan bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ancak herhangi bir geçerli uç nokta olabilir.  
  
 Hizmet ile iletişim kurmak için kullanılacak bağlama oluştururken, hizmet olarak tam aynı bağlama kullanılacağını dikkatli olmanız gerekir. Tek fark bağlama istemcisinin yüklü olduğu bir <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> yığının üst kısmında. Hizmet sistem tarafından sağlanan bağlamalar birini kullanıyorsanız, yeni bir oluşturma <xref:System.ServiceModel.Channels.CustomBinding> ve sistem tarafından sağlanan bir bağlamayı için geçirin <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> Oluşturucusu. Ekleyebileceğiniz sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> çağırarak `Insert` üzerinde <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> özelliği.  
  
 Bunu ekledikten sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , bağlama için ve, yapılandırılmış WCF istemci sınıfının bir örneğini oluşturur, bunu açın ve yöntemlerini çağırın. Aşağıdaki örnek, uygulayan bir WCF hizmeti bulmak için keşif istemcisi kanalını kullanır `ICalculator` sınıfı (başlatıldı WCF alma öğreticide kullanılan) ve çağrıları kendi `Add` yöntemi.  
  
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
 Keşif istemcisi kanalını kullanırken, iki uç nokta belirtilir. Bir kullanılan bulma iletileri için genellikle <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ve diğer uygulama uç noktadır. Güvenli bir hizmet uygularken, her iki uç noktalarını güvenli hale getirmek için dikkatli olunması gerekir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Güvenlik, bkz: [güvenli hale getirme hizmetler ve istemcileri](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
