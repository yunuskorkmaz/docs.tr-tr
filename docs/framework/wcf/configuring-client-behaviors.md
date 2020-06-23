---
title: İstemci Davranışlarını Yapılandırma
description: "WCF 'nin davranışları nasıl yapılandırdığından oluşan iki yol hakkında bilgi edinin: uygulama yapılandırma dosyasında veya program aracılığıyla çağıran uygulamadan."
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 4b83862221cf249455478c3ade159a3101062f3e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245446"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="47aee-103">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47aee-103">Configuring Client Behaviors</span></span>
<span data-ttu-id="47aee-104">Windows Communication Foundation (WCF) davranışları iki şekilde yapılandırır: `<behavior>` bir istemci uygulama yapılandırma dosyasının bölümünde tanımlanan (ya da çağıran uygulamada) bir davranış yapılandırmasına başvurarak.</span><span class="sxs-lookup"><span data-stu-id="47aee-104">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="47aee-105">Bu konuda her iki yaklaşım da açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47aee-105">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="47aee-106">Bir yapılandırma dosyası kullanılırken, davranış yapılandırması yapılandırma ayarlarının adlandırılmış bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="47aee-106">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="47aee-107">Her davranış yapılandırmasının adı benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47aee-107">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="47aee-108">Bu dize `behaviorConfiguration` , uç noktayı davranışa bağlamak için bir uç nokta yapılandırması özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47aee-108">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47aee-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="47aee-109">Example</span></span>  
 <span data-ttu-id="47aee-110">Aşağıdaki yapılandırma kodu adlı bir davranışı tanımlar `myBehavior` .</span><span class="sxs-lookup"><span data-stu-id="47aee-110">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="47aee-111">İstemci uç noktası, özniteliğinde Bu davranışa başvurur `behaviorConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="47aee-111">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="47aee-112">Davranışları programlı kullanma</span><span class="sxs-lookup"><span data-stu-id="47aee-112">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="47aee-113">Ayrıca, `Behaviors` istemciyi açmadan önce Windows Communication Foundation (WCF) istemci nesnesinde veya istemci kanalı fabrikası nesnesinde uygun özelliği bularak de davranışları programlı bir şekilde yapılandırabilir veya ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47aee-113">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47aee-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="47aee-114">Example</span></span>  
 <span data-ttu-id="47aee-115">Aşağıdaki kod örneği, <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> Kanal nesnesinin oluşturulmasından önce özelliğinden döndürülen özelliğe erişerek programlı bir şekilde davranış ekleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47aee-115">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="47aee-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47aee-116">See also</span></span>

- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
