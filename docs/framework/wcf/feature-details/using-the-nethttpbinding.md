---
title: NetHttpBinding Kullanma
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: b00b4ed24d15519baf91ce38678fd91056eff521
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658734"
---
# <a name="using-the-nethttpbinding"></a>NetHttpBinding Kullanma
<xref:System.ServiceModel.NetHttpBinding> HTTP veya WebSocket hizmetlerini kullanma için tasarlanmış bir bağlama ve ikili kodlama varsayılan olarak kullanır. <xref:System.ServiceModel.NetHttpBinding> İstek-yanıt anlaşması veya çift yönlü sözleşme ile kullanılan olup olmadığını algılar ve davranışını eşleşecek şekilde değiştirmesine - HTTP istek-yanıt sözleşmeleriyle ve WebSockets için çift yönlü sözleşmeler için kullanır. Bu davranış kullanılarak geçersiz kılınabilir <xref:System.ServiceModel.Channels.WebSocketTransportUsage> ayarı:  
  
1. `Always` -Bu, hatta istek-yanıt sözleşmeleriyle için kullanılacak WebSockets zorlar.  
  
2. `Never` -Bu, WebSockets kullanılmasını engeller. Bu ayar ile çift yönlü sözleşme kullanılmaya çalışılırsa, bir özel durum neden olur.  
  
3. `WhenDuplex` -Bu, varsayılan değerdir ve yukarıda açıklandığı gibi davranır.  
  
 <xref:System.ServiceModel.NetHttpBinding> güvenilir oturumlar, hem HTTP modu hem de WebSocket modu destekler. WebSocket içinde modu oturumları taşıma tarafından sağlanır.  
  
> [!WARNING]
>  Kullanırken <xref:System.ServiceModel.NetHttpBinding> ve bağlamanın TransferMode TransferMode.Streamed için ayarlanır, kilitlenme ve çağrı zaman aşımı büyük akışlarını neden olabilir. Bu sorunu Gönder küçük ileti çalışma veya TransferMode.Buffered kullanmak için.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>NetHttpBinding bir hizmetin yapılandırma  
 <xref:System.ServiceModel.NetHttpBinding> Olabilir aynı yapılandırılmış diğer bağlama. Bir WCF Hizmeti ile yapılandırma aşağıdaki yapılandırma parçacığı göstermektedir <xref:System.ServiceModel.NetHttpBinding>.  
  
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
  
 Aşağıdaki kod parçacığını nasıl ekleneceğini gösterir <xref:System.ServiceModel.NetHttpBinding> kod.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hizmetler için Bağlamaları Yapılandırma](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Çift Yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/duplex-services.md)
