---
title: İstemci Davranışlarını Yapılandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 83fdc77bd17115f9952f2ca6c494ed0eb873cd9c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193661"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="ead2c-102">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ead2c-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="ead2c-103">Windows Communication Foundation (WCF) iki şekilde davranışları yapılandırır: tarafından tanımlanan davranışı yapılandırmaları--başvuran `<behavior>` bölümü bir istemci uygulama yapılandırma dosyası – veya program aracılığıyla arama uygulama.</span><span class="sxs-lookup"><span data-stu-id="ead2c-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="ead2c-104">Bu konuda, her iki yaklaşım açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ead2c-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="ead2c-105">Bir yapılandırma dosyası kullanırken davranışı yapılandırmasına yapılandırma ayarlarının adlandırılmış bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="ead2c-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="ead2c-106">Her davranışı yapılandırmasının adı benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ead2c-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="ead2c-107">Bu dize, kullanılır `behaviorConfiguration` uç nokta için davranış bağlamak için bir uç nokta yapılandırması özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ead2c-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ead2c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ead2c-108">Example</span></span>  
 <span data-ttu-id="ead2c-109">Aşağıdaki yapılandırmayı kod olarak adlandırılan bir davranış tanımlar `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="ead2c-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="ead2c-110">Bu davranış, istemci uç noktası başvuran `behaviorConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ead2c-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="ead2c-111">Davranışlar programlı olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="ead2c-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="ead2c-112">Ayrıca yapılandırma veya uygun bularak davranışları program aracılığıyla ekleme `Behaviors` özelliği Windows Communication Foundation (WCF) istemci nesnesi veya istemci açmadan önce istemci kanal fabrikası nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ead2c-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ead2c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="ead2c-113">Example</span></span>  
 <span data-ttu-id="ead2c-114">Aşağıdaki kod örneği, program aracılığıyla erişerek bir davranış eklemek gösterilmektedir <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> özelliği <xref:System.ServiceModel.Description.ServiceEndpoint> döndürüldüğü <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> önce kanal nesnesi oluşturma özelliği.</span><span class="sxs-lookup"><span data-stu-id="ead2c-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="ead2c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ead2c-115">See also</span></span>

- [<span data-ttu-id="ead2c-116">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="ead2c-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
