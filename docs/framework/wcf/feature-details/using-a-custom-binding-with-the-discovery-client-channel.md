---
title: Keşif İstemci Kanalıyla Özel Bağlama Kullanma
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 406a53dece6370fbb56daa5a30b52621ca1dcd6d
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975985"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Keşif İstemci Kanalıyla Özel Bağlama Kullanma
<xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>ile özel bir bağlama kullanırken <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnekleri oluşturan bir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> tanımlamanız gerekir.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Bir DiscoveryEndpointProvider oluşturma  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>, istek üzerine <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnekleri oluşturmaktan sorumludur. Bir bulma uç noktası sağlayıcısı tanımlamak için <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> bir sınıf türetebilir ve <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> yöntemini geçersiz kılın ve yeni bir bulma uç noktası döndürün. Aşağıdaki örnek, bulma uç noktası sağlayıcısının nasıl oluşturulacağını göstermektedir.  
  
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
  
 Bulma uç noktası sağlayıcısını tanımladıktan sonra özel bir bağlama oluşturabilir ve aşağıdaki örnekte gösterildiği gibi bulma uç noktası sağlayıcısına başvuran <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>ekleyebilirsiniz.  
  
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
  
 Bulma istemci kanalını kullanma hakkında daha fazla bilgi için bkz. [bulma Istemci kanalını kullanma](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md). 
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Bulmaya Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Keşif İstemcisi Kanalını Kullanma](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
