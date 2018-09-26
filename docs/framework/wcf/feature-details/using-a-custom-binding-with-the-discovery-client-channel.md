---
title: Keşif İstemci Kanalıyla Özel Bağlama Kullanma
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 7473262ec52adfd917b8ec5cd7ec1f4935a3646d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195231"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Keşif İstemci Kanalıyla Özel Bağlama Kullanma
Özel bağlama ile kullanırken <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, tanımlamanız gerekir bir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> oluşturan <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnekleri.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Bir DiscoveryEndpointProvider oluşturma  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Oluşturmaktan sorumlu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnekleri isteğe bağlı. Bulma uç noktası sağlayıcı tanımlamak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> ve geçersiz kılma <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> yöntemi ve yeni bir bulma uç noktası döndürülecek. Aşağıdaki örnek, bir bulma uç noktası sağlayıcı oluşturma işlemi gösterilmektedir.  
  
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
  
 Özel bağlama oluşturma ve ekleme bulma uç noktası sağlayıcı tanımladıktan sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, aşağıdaki örnekte gösterildiği gibi bulma uç noktası sağlayıcı başvuruyor.  
  
```  
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 Keşif istemcisi kanalını kullanma hakkında daha fazla bilgi için bkz. [keşif istemcisi kanalını kullanma](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md). 
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [WCF Bulmaya Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
- [Keşif İstemcisi Kanalını Kullanma](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  