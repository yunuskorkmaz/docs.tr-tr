---
title: İstemci Davranışlarını Yapılandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: ca466af71f62ef72e021753b132afdc847f75d76
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320687"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="574b6-102">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="574b6-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="574b6-103">Windows Communication Foundation (WCF) davranışları iki şekilde yapılandırır: bir istemci uygulama yapılandırma dosyasının `<behavior>` bölümünde tanımlanan (ya da çağıran uygulamada), davranış yapılandırmalarına başvurularak.</span><span class="sxs-lookup"><span data-stu-id="574b6-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="574b6-104">Bu konuda her iki yaklaşım da açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="574b6-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="574b6-105">Bir yapılandırma dosyası kullanılırken, davranış yapılandırması yapılandırma ayarlarının adlandırılmış bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="574b6-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="574b6-106">Her davranış yapılandırmasının adı benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="574b6-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="574b6-107">Bu dize, uç noktayı davranışa bağlamak için uç nokta yapılandırmasının `behaviorConfiguration` özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="574b6-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="574b6-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="574b6-108">Example</span></span>  
 <span data-ttu-id="574b6-109">Aşağıdaki yapılandırma kodu `myBehavior` adlı bir davranışı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="574b6-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="574b6-110">İstemci uç noktası `behaviorConfiguration` özniteliğinde Bu davranışa başvurur.</span><span class="sxs-lookup"><span data-stu-id="574b6-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="574b6-111">Davranışları programlı kullanma</span><span class="sxs-lookup"><span data-stu-id="574b6-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="574b6-112">Ayrıca, istemciyi açmadan önce Windows Communication Foundation (WCF) istemci nesnesinde veya istemci kanalı fabrikası nesnesinde uygun `Behaviors` özelliğini bularak, davranışları programlı olarak yapılandırabilir veya ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="574b6-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="574b6-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="574b6-113">Example</span></span>  
 <span data-ttu-id="574b6-114">Aşağıdaki kod örneği, kanal nesnesi oluşturmadan önce <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> özelliğinden döndürülen <xref:System.ServiceModel.Description.ServiceEndpoint> ' deki <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> özelliğine erişerek programlı olarak bir davranışın nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="574b6-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="574b6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="574b6-115">See also</span></span>

- [<span data-ttu-id="574b6-116">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="574b6-116">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)
