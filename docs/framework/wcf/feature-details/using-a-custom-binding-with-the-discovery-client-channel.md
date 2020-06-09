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
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="709a4-102">Keşif İstemci Kanalıyla Özel Bağlama Kullanma</span><span class="sxs-lookup"><span data-stu-id="709a4-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="709a4-103">İle özel bir bağlama kullanılırken <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , örnek oluşturan bir ' i tanımlamanız gerekir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="709a4-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="709a4-104">Bir DiscoveryEndpointProvider oluşturma</span><span class="sxs-lookup"><span data-stu-id="709a4-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="709a4-105"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> İstek üzerine örneklerin oluşturulmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="709a4-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="709a4-106">Bir bulma uç noktası sağlayıcısı tanımlamak için, öğesinden bir sınıf türetebilir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> ve <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> yöntemi geçersiz kılın ve yeni bir bulma uç noktası döndürün.</span><span class="sxs-lookup"><span data-stu-id="709a4-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="709a4-107">Aşağıdaki örnek, bulma uç noktası sağlayıcısının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="709a4-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="709a4-108">Bulma uç noktası sağlayıcısını tanımladıktan sonra özel bir bağlama oluşturabilir ve <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Aşağıdaki örnekte gösterildiği gibi bulma uç noktası sağlayıcısına başvuran öğesini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="709a4-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="709a4-109">Bulma istemci kanalını kullanma hakkında daha fazla bilgi için bkz. [bulma Istemci kanalını kullanma](using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="709a4-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](using-the-discovery-client-channel.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="709a4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="709a4-110">See also</span></span>

- [<span data-ttu-id="709a4-111">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="709a4-111">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="709a4-112">Keşif İstemcisi Kanalını Kullanma</span><span class="sxs-lookup"><span data-stu-id="709a4-112">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)
