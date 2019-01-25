---
title: Keşif İstemci Kanalıyla Özel Bağlama Kullanma
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 6fe9370bb22ca424774fc8cb4566e0802bc06697
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698371"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="2d24b-102">Keşif İstemci Kanalıyla Özel Bağlama Kullanma</span><span class="sxs-lookup"><span data-stu-id="2d24b-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="2d24b-103">Özel bağlama ile kullanırken <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, tanımlamanız gerekir bir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> oluşturan <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="2d24b-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="2d24b-104">Bir DiscoveryEndpointProvider oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d24b-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="2d24b-105"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Oluşturmaktan sorumlu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnekleri isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2d24b-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="2d24b-106">Bulma uç noktası sağlayıcı tanımlamak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> ve geçersiz kılma <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> yöntemi ve yeni bir bulma uç noktası döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="2d24b-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="2d24b-107">Aşağıdaki örnek, bir bulma uç noktası sağlayıcı oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2d24b-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="2d24b-108">Özel bağlama oluşturma ve ekleme bulma uç noktası sağlayıcı tanımladıktan sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, aşağıdaki örnekte gösterildiği gibi bulma uç noktası sağlayıcı başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="2d24b-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="2d24b-109">Keşif istemcisi kanalını kullanma hakkında daha fazla bilgi için bkz. [keşif istemcisi kanalını kullanma](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="2d24b-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="2d24b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d24b-110">See also</span></span>

- [<span data-ttu-id="2d24b-111">WCF Bulmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2d24b-111">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="2d24b-112">Keşif İstemcisi Kanalını Kullanma</span><span class="sxs-lookup"><span data-stu-id="2d24b-112">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
