---
title: Keşif İstemci Kanalıyla Özel Bağlama Kullanma
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 49983c3ab303d3839350af72b1aa4821c071fe99
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595043"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Keşif İstemci Kanalıyla Özel Bağlama Kullanma
İle özel bir bağlama kullanılırken <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , örnek oluşturan bir ' i tanımlamanız gerekir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> .  
  
## <a name="creating-a-discoveryendpointprovider"></a>Bir DiscoveryEndpointProvider oluşturma  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> İstek üzerine örneklerin oluşturulmasından sorumludur. Bir bulma uç noktası sağlayıcısı tanımlamak için, öğesinden bir sınıf türetebilir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> ve <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> yöntemi geçersiz kılın ve yeni bir bulma uç noktası döndürün. Aşağıdaki örnek, bulma uç noktası sağlayıcısının nasıl oluşturulacağını göstermektedir.  
  
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
  
 Bulma uç noktası sağlayıcısını tanımladıktan sonra özel bir bağlama oluşturabilir ve <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Aşağıdaki örnekte gösterildiği gibi bulma uç noktası sağlayıcısına başvuran öğesini ekleyebilirsiniz.  
  
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
  
 Bulma istemci kanalını kullanma hakkında daha fazla bilgi için bkz. [bulma Istemci kanalını kullanma](using-the-discovery-client-channel.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Keşif Genel Bakış](wcf-discovery-overview.md)
- [Keşif İstemcisi Kanalını Kullanma](using-the-discovery-client-channel.md)
