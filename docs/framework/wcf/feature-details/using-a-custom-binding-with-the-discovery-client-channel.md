---
title: Keşif İstemci Kanalıyla Özel Bağlama Kullanma
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 5f3f5fe24d1f19ce503b793d9aad870d882c7971
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184284"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Keşif İstemci Kanalıyla Özel Bağlama Kullanma
Özel bir bağlama kullanırken <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnekleri oluşturan bir tanımlamalısınız.  
  
## <a name="creating-a-discoveryendpointprovider"></a>DiscoveryEndpointProvider Oluşturma  
 Talep <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> üzerine örnekler <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> oluşturmaktan sorumludur. Bir bulma bitiş noktası sağlayıcısı tanımlamak için, bir sınıf türetmek <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> ve <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> yöntemi geçersiz kılmak ve yeni bir bulma bitiş noktası döndürün. Aşağıdaki örnekte, bir bulma bitiş noktası sağlayıcısının nasıl oluşturulacak olduğu gösterilmektedir.  
  
```csharp
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
  
 Bulma uç noktası sağlayıcısını tanımladıktan sonra özel bir <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>bağlama oluşturabilir ve aşağıdaki örnekte gösterildiği gibi bulma bitiş noktası sağlayıcısına başvuran , bir ekleme yapabilirsiniz.  
  
```csharp
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 Bulma istemcisi kanalını kullanma hakkında daha fazla bilgi için Bkz. [Discovery Client Channel'ı kullanma.](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Keşif Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Keşif İstemcisi Kanalını Kullanma](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
