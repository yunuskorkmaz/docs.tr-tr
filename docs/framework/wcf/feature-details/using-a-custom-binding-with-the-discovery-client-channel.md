---
description: 'Hakkında daha fazla bilgi edinin: bulma Istemci kanalı ile özel bağlama kullanma'
title: Keşif İstemci Kanalıyla Özel Bağlama Kullanma
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: a4dd823aed01785aab4127e4323cdc0a0a6d952a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632379"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="09ccd-103">Keşif İstemci Kanalıyla Özel Bağlama Kullanma</span><span class="sxs-lookup"><span data-stu-id="09ccd-103">Using a Custom Binding with the Discovery Client Channel</span></span>

<span data-ttu-id="09ccd-104">İle özel bir bağlama kullanılırken <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , örnek oluşturan bir ' i tanımlamanız gerekir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="09ccd-104">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="09ccd-105">Bir DiscoveryEndpointProvider oluşturma</span><span class="sxs-lookup"><span data-stu-id="09ccd-105">Creating a DiscoveryEndpointProvider</span></span>  

 <span data-ttu-id="09ccd-106"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> İstek üzerine örneklerin oluşturulmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="09ccd-106">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="09ccd-107">Bir bulma uç noktası sağlayıcısı tanımlamak için, öğesinden bir sınıf türetebilir <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> ve <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> yöntemi geçersiz kılın ve yeni bir bulma uç noktası döndürün.</span><span class="sxs-lookup"><span data-stu-id="09ccd-107">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="09ccd-108">Aşağıdaki örnek, bulma uç noktası sağlayıcısının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="09ccd-108">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="09ccd-109">Bulma uç noktası sağlayıcısını tanımladıktan sonra özel bir bağlama oluşturabilir ve <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Aşağıdaki örnekte gösterildiği gibi bulma uç noktası sağlayıcısına başvuran öğesini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ccd-109">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="09ccd-110">Bulma istemci kanalını kullanma hakkında daha fazla bilgi için bkz. [bulma Istemci kanalını kullanma](using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="09ccd-110">For more information about using the discovery client channel, see [Using the Discovery Client Channel](using-the-discovery-client-channel.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="09ccd-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09ccd-111">See also</span></span>

- [<span data-ttu-id="09ccd-112">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="09ccd-112">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="09ccd-113">Keşif İstemcisi Kanalını Kullanma</span><span class="sxs-lookup"><span data-stu-id="09ccd-113">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)
