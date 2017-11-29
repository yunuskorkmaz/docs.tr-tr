---
title: "Keşif İstemci Kanalıyla Özel Bağlama Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 716dc09d38c778c49a1e2e5fa094ef1bf004eb46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="78287-102">Keşif İstemci Kanalıyla Özel Bağlama Kullanma</span><span class="sxs-lookup"><span data-stu-id="78287-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="78287-103">Özel bağlama ile kullanırken <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, tanımlamanız gerekir bir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> oluşturan <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="78287-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="78287-104">Bir DiscoveryEndpointProvider oluşturma</span><span class="sxs-lookup"><span data-stu-id="78287-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="78287-105"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Oluşturmaktan sorumlu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örneklerini isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="78287-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="78287-106">Bulma uç noktası sağlayıcı tanımlamak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> ve geçersiz kılma <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> yöntemi ve return yeni bir bulma uç noktası.</span><span class="sxs-lookup"><span data-stu-id="78287-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="78287-107">Aşağıdaki örnek, bir bulma uç noktası sağlayıcı oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78287-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="78287-108">Özel bağlama oluşturma ve ekleme bulma uç noktası sağlayıcı tanımladıktan sonra <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, aşağıdaki örnekte gösterildiği gibi bulma uç noktası sağlayıcı başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="78287-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="78287-109">Keşif istemcisi kanalını kullanma Bkz [keşif istemcisi kanalını kullanma](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="78287-109"> using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> <span data-ttu-id="78287-110">Tam kod örneği için bkz: [keşif bağlama öğesi örneği](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)</span><span class="sxs-lookup"><span data-stu-id="78287-110">For a complete code example, see [Discovery Binding Element Sample](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78287-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78287-111">See Also</span></span>  
 [<span data-ttu-id="78287-112">WCF keşif genel bakış</span><span class="sxs-lookup"><span data-stu-id="78287-112">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="78287-113">Keşif istemcisi kanalını kullanma</span><span class="sxs-lookup"><span data-stu-id="78287-113">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [<span data-ttu-id="78287-114">Keşif bağlama öğesi örneği</span><span class="sxs-lookup"><span data-stu-id="78287-114">Discovery Binding Element Sample</span></span>](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)
