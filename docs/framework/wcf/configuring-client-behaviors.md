---
title: İstemci Davranışlarını Yapılandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 062e726b6f1d6831303e1cc0ae82a434daab860c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458113"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="642ad-102">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="642ad-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="642ad-103">Windows Communication Foundation (WCF) iki yolla davranışları yapılandırır: tanımlı davranış yapılandırmalara--başvuran ya da `<behavior>` bölüm bir istemci uygulama yapılandırma dosyası – veya program aracılığıyla arama uygulama.</span><span class="sxs-lookup"><span data-stu-id="642ad-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="642ad-104">Bu konu, her iki yaklaşımın açıklar.</span><span class="sxs-lookup"><span data-stu-id="642ad-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="642ad-105">Bir yapılandırma dosyası kullanırken davranışını yapılandırma adlandırılmış yapılandırma ayarları koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="642ad-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="642ad-106">Her davranış yapılandırmasının adı benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="642ad-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="642ad-107">Bu dize, kullanılır `behaviorConfiguration` uç nokta için davranış bağlamak için bir uç nokta yapılandırması özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="642ad-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="642ad-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="642ad-108">Example</span></span>  
 <span data-ttu-id="642ad-109">Aşağıdaki yapılandırma kodunu adlı bir davranış tanımlar `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="642ad-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="642ad-110">İstemci uç noktası bu davranışı başvuran `behaviorConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="642ad-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="642ad-111">Davranışları program aracılığıyla kullanarak</span><span class="sxs-lookup"><span data-stu-id="642ad-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="642ad-112">Ayrıca yapılandırma veya uygun bularak davranışları programlı olarak Ekle `Behaviors` özelliği Windows Communication Foundation (WCF) istemci nesnesi ya da istemci açmadan önce istemci kanal fabrikası nesnesi.</span><span class="sxs-lookup"><span data-stu-id="642ad-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="642ad-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="642ad-113">Example</span></span>  
 <span data-ttu-id="642ad-114">Aşağıdaki kod örneğinde nasıl erişerek bir davranış program aracılığıyla ekleneceğini gösterir <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> özelliği <xref:System.ServiceModel.Description.ServiceEndpoint> döndürülen <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> kanal nesnesinin oluşturulmasını önce özelliği.</span><span class="sxs-lookup"><span data-stu-id="642ad-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="642ad-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="642ad-115">See Also</span></span>  
 [<span data-ttu-id="642ad-116">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="642ad-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
