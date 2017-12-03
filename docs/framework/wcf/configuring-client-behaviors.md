---
title: "İstemci Davranışlarını Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c63a91683817311b8d644eb4285101e32eaea7f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-client-behaviors"></a>İstemci Davranışlarını Yapılandırma
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]iki yolla davranışları yapılandırır: tanımlı davranış yapılandırmalara--başvuran ya da `<behavior>` bölüm bir istemci uygulama yapılandırma dosyası – veya program aracılığıyla çağrı yapan uygulamanın. Bu konu, her iki yaklaşımın açıklar.  
  
 Bir yapılandırma dosyası kullanırken davranışını yapılandırma adlandırılmış yapılandırma ayarları koleksiyonudur. Her davranış yapılandırmasının adı benzersiz olmalıdır. Bu dize, kullanılır `behaviorConfiguration` uç nokta için davranış bağlamak için bir uç nokta yapılandırması özniteliğidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma kodunu adlı bir davranış tanımlar `myBehavior`. İstemci uç noktası bu davranışı başvuran `behaviorConfiguration` özniteliği.  
  
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
  
## <a name="using-behaviors-programmatically"></a>Davranışları program aracılığıyla kullanarak  
 Ayrıca yapılandırma veya uygun bularak davranışları programlı olarak Ekle `Behaviors` özellikte [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] istemci nesnesi veya istemci açmadan önce istemci kanal fabrikası nesnesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl erişerek bir davranış program aracılığıyla ekleneceğini gösterir <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> özelliği <xref:System.ServiceModel.Description.ServiceEndpoint> döndürülen <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> kanal nesnesinin oluşturulmasını önce özelliği.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<davranışları >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
