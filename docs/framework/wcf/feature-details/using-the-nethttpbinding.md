---
title: NetHttpBinding Kullanma
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 82222dbfa3f35ed00d0173f2bc927c32e9e98470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184239"
---
# <a name="using-the-nethttpbinding"></a>NetHttpBinding Kullanma
<xref:System.ServiceModel.NetHttpBinding>HTTP veya WebSocket hizmetlerini tüketmek için tasarlanmış bir bağlayıcıdır ve varsayılan olarak ikili kodlama kullanır. <xref:System.ServiceModel.NetHttpBinding>bir istek yanıtlama sözleşmesi veya çift yönlü sözleşme ile kullanılıp kullanılmadığını algılar ve davranışını eşleşecek şekilde değiştirir - bu istek yanıtlama sözleşmeleri için HTTP ve çift yönlü sözleşmeler için WebSockets kullanır. Bu davranış <xref:System.ServiceModel.Channels.WebSocketTransportUsage> ayarı kullanılarak geçersiz kılınabilir:  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>- Bu, WebSockets'i istek-yanıt sözleşmeleri için bile kullanılmaya zorlar.  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>- Bu, WebSockets'in kullanılmasını engeller. Bu ayarile çift yönlü bir sözleşme kullanmaya çalışmak bir özel durumla sonuçlanır.  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>- Bu varsayılan değerdir ve yukarıda açıklandığı gibi şekilde işlem yapılır.  
  
 <xref:System.ServiceModel.NetHttpBinding>hem HTTP modunda hem de WebSocket modunda güvenilir oturumları destekler. WebSocket modunda oturumlar aktarım tarafından sağlanır.  
  
> [!WARNING]
> Bağlamanın <xref:System.ServiceModel.NetHttpBinding> Aktarım Modu'nu ve Aktarım Mode'u Kullanarak TransferMode.Streamed olarak ayarlanırsa, büyük akışlar bir kilitlenmeye neden olabilir ve arama zaman alacaktır. Bu sorunu çözmek için daha küçük iletiler gönderin veya Aktarım Modu.Arabelleğe Alma'yı kullanın.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>Bir Hizmeti Net'i kullanacak şekilde yapılandırmaHttpBinding  
 Diğer <xref:System.ServiceModel.NetHttpBinding> bağlama ile aynı şekilde yapılandırılabilir. Aşağıdaki yapılandırma snippet nasıl bir WCF hizmeti <xref:System.ServiceModel.NetHttpBinding>ile yapılandırılanın gösteriş gösterir.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    ...
  </system.serviceModel>  
```  
  
 Aşağıdaki kod snippet kodu eklemek <xref:System.ServiceModel.NetHttpBinding> için nasıl gösterir.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler için Bağlamaları Yapılandırma](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Sistem Destekli Ciltler](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Çift Yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/duplex-services.md)
