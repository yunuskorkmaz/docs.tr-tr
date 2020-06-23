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
# <a name="configuring-client-behaviors"></a>İstemci Davranışlarını Yapılandırma
Windows Communication Foundation (WCF) davranışları iki şekilde yapılandırır: `<behavior>` bir istemci uygulama yapılandırma dosyasının bölümünde tanımlanan (ya da çağıran uygulamada) bir davranış yapılandırmasına başvurarak. Bu konuda her iki yaklaşım da açıklanmaktadır.  
  
 Bir yapılandırma dosyası kullanılırken, davranış yapılandırması yapılandırma ayarlarının adlandırılmış bir koleksiyonudur. Her davranış yapılandırmasının adı benzersiz olmalıdır. Bu dize `behaviorConfiguration` , uç noktayı davranışa bağlamak için bir uç nokta yapılandırması özniteliğinde kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma kodu adlı bir davranışı tanımlar `myBehavior` . İstemci uç noktası, özniteliğinde Bu davranışa başvurur `behaviorConfiguration` .  
  
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
 Ayrıca, `Behaviors` istemciyi açmadan önce Windows Communication Foundation (WCF) istemci nesnesinde veya istemci kanalı fabrikası nesnesinde uygun özelliği bularak de davranışları programlı bir şekilde yapılandırabilir veya ekleyebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> Kanal nesnesinin oluşturulmasından önce özelliğinden döndürülen özelliğe erişerek programlı bir şekilde davranış ekleme gösterilmektedir.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
