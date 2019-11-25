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
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="46d77-102">Keşif İstemci Kanalıyla Özel Bağlama Kullanma</span><span class="sxs-lookup"><span data-stu-id="46d77-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="46d77-103"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>ile özel bir bağlama kullanırken <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnekleri oluşturan bir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46d77-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="46d77-104">Bir DiscoveryEndpointProvider oluşturma</span><span class="sxs-lookup"><span data-stu-id="46d77-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="46d77-105"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>, istek üzerine <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnekleri oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="46d77-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="46d77-106">Bir bulma uç noktası sağlayıcısı tanımlamak için <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> bir sınıf türetebilir ve <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> yöntemini geçersiz kılın ve yeni bir bulma uç noktası döndürün.</span><span class="sxs-lookup"><span data-stu-id="46d77-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="46d77-107">Aşağıdaki örnek, bulma uç noktası sağlayıcısının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="46d77-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="46d77-108">Bulma uç noktası sağlayıcısını tanımladıktan sonra özel bir bağlama oluşturabilir ve aşağıdaki örnekte gösterildiği gibi bulma uç noktası sağlayıcısına başvuran <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46d77-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="46d77-109">Bulma istemci kanalını kullanma hakkında daha fazla bilgi için bkz. [bulma Istemci kanalını kullanma](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="46d77-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="46d77-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46d77-110">See also</span></span>

- [<span data-ttu-id="46d77-111">WCF Bulmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="46d77-111">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="46d77-112">Keşif İstemcisi Kanalını Kullanma</span><span class="sxs-lookup"><span data-stu-id="46d77-112">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
