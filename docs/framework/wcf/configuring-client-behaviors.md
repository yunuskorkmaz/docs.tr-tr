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
# <a name="configuring-client-behaviors"></a>İstemci Davranışlarını Yapılandırma
Windows Communication Foundation (WCF) davranışları iki şekilde yapılandırır: bir istemci uygulama yapılandırma dosyasının `<behavior>` bölümünde tanımlanan (ya da çağıran uygulamada), davranış yapılandırmalarına başvurularak. Bu konuda her iki yaklaşım da açıklanmaktadır.  
  
 Bir yapılandırma dosyası kullanılırken, davranış yapılandırması yapılandırma ayarlarının adlandırılmış bir koleksiyonudur. Her davranış yapılandırmasının adı benzersiz olmalıdır. Bu dize, uç noktayı davranışa bağlamak için uç nokta yapılandırmasının `behaviorConfiguration` özniteliğinde kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma kodu `myBehavior` adlı bir davranışı tanımlar. İstemci uç noktası `behaviorConfiguration` özniteliğinde Bu davranışa başvurur.  
  
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
  
## <a name="using-behaviors-programmatically"></a>Davranışları programlı kullanma  
 Ayrıca, istemciyi açmadan önce Windows Communication Foundation (WCF) istemci nesnesinde veya istemci kanalı fabrikası nesnesinde uygun `Behaviors` özelliğini bularak, davranışları programlı olarak yapılandırabilir veya ekleyebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kanal nesnesi oluşturmadan önce <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> özelliğinden döndürülen <xref:System.ServiceModel.Description.ServiceEndpoint> ' deki <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> özelliğine erişerek programlı olarak bir davranışın nasıl ekleneceğini gösterir.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<davranışlar >](../configure-apps/file-schema/wcf/behaviors.md)
