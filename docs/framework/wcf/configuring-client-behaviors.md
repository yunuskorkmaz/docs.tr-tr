---
title: İstemci Davranışlarını Yapılandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 83fdc77bd17115f9952f2ca6c494ed0eb873cd9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608781"
---
# <a name="configuring-client-behaviors"></a>İstemci Davranışlarını Yapılandırma
Windows Communication Foundation (WCF) iki şekilde davranışları yapılandırır: tarafından tanımlanan davranışı yapılandırmaları--başvuran `<behavior>` bölümü bir istemci uygulama yapılandırma dosyası – veya program aracılığıyla arama uygulama. Bu konuda, her iki yaklaşım açıklanmaktadır.  
  
 Bir yapılandırma dosyası kullanırken davranışı yapılandırmasına yapılandırma ayarlarının adlandırılmış bir koleksiyondur. Her davranışı yapılandırmasının adı benzersiz olmalıdır. Bu dize, kullanılır `behaviorConfiguration` uç nokta için davranış bağlamak için bir uç nokta yapılandırması özniteliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırmayı kod olarak adlandırılan bir davranış tanımlar `myBehavior`. Bu davranış, istemci uç noktası başvuran `behaviorConfiguration` özniteliği.  
  
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
  
## <a name="using-behaviors-programmatically"></a>Davranışlar programlı olarak kullanma  
 Ayrıca yapılandırma veya uygun bularak davranışları program aracılığıyla ekleme `Behaviors` özelliği Windows Communication Foundation (WCF) istemci nesnesi veya istemci açmadan önce istemci kanal fabrikası nesnesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, program aracılığıyla erişerek bir davranış eklemek gösterilmektedir <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> özelliği <xref:System.ServiceModel.Description.ServiceEndpoint> döndürüldüğü <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> önce kanal nesnesi oluşturma özelliği.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<davranışlar >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
