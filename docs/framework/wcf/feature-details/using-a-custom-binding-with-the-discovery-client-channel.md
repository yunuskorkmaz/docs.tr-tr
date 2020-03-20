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
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="da183-102">Keşif İstemci Kanalıyla Özel Bağlama Kullanma</span><span class="sxs-lookup"><span data-stu-id="da183-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="da183-103">Özel bir bağlama kullanırken <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnekleri oluşturan bir tanımlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="da183-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="da183-104">DiscoveryEndpointProvider Oluşturma</span><span class="sxs-lookup"><span data-stu-id="da183-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="da183-105">Talep <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> üzerine örnekler <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="da183-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="da183-106">Bir bulma bitiş noktası sağlayıcısı tanımlamak için, bir sınıf türetmek <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> ve <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> yöntemi geçersiz kılmak ve yeni bir bulma bitiş noktası döndürün.</span><span class="sxs-lookup"><span data-stu-id="da183-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="da183-107">Aşağıdaki örnekte, bir bulma bitiş noktası sağlayıcısının nasıl oluşturulacak olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="da183-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="da183-108">Bulma uç noktası sağlayıcısını tanımladıktan sonra özel bir <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>bağlama oluşturabilir ve aşağıdaki örnekte gösterildiği gibi bulma bitiş noktası sağlayıcısına başvuran , bir ekleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da183-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="da183-109">Bulma istemcisi kanalını kullanma hakkında daha fazla bilgi için Bkz. [Discovery Client Channel'ı kullanma.](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)</span><span class="sxs-lookup"><span data-stu-id="da183-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="da183-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da183-110">See also</span></span>

- [<span data-ttu-id="da183-111">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="da183-111">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="da183-112">Keşif İstemcisi Kanalını Kullanma</span><span class="sxs-lookup"><span data-stu-id="da183-112">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
