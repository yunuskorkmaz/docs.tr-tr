---
title: NetHttpBinding Kullanma
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: ac6fc658731d032051f2dfd4058397f9b9a55828
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585642"
---
# <a name="using-the-nethttpbinding"></a>NetHttpBinding Kullanma
<xref:System.ServiceModel.NetHttpBinding>, HTTP veya WebSocket hizmetlerini kullanmak için tasarlanan bir bağlamadır ve varsayılan olarak ikili kodlama kullanır. <xref:System.ServiceModel.NetHttpBinding>, istek-yanıt sözleşmesi veya çift yönlü sözleşmeyle birlikte kullanılıp kullanılmayacağını algılar ve davranışını eşleşecek şekilde değiştirin-bu, istek-yanıt sözleşmeleri için HTTP ve çift yönlü sözleşmeler için WebSockets kullanır. Bu davranış ayarı kullanılarak geçersiz kılınabilir <xref:System.ServiceModel.Channels.WebSocketTransportUsage> :  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>-Bu WebSockets, istek-yanıt sözleşmeleri için bile kullanılmasına zorlar.  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>-Bu, WebSockets kullanılmasını önler. Bu ayarla bir çift yönlü sözleşme kullanılmaya çalışılması bir özel durumla sonuçlanır.  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>-Bu varsayılan değerdir ve yukarıda açıklandığı gibi davranır.  
  
 <xref:System.ServiceModel.NetHttpBinding>hem HTTP modunda hem de WebSocket modunda güvenilir oturumları destekler. WebSocket modundaki oturumlarda, taşıma tarafından sağlanır.  
  
> [!WARNING]
> <xref:System.ServiceModel.NetHttpBinding>Ve bağlamanın TransferMode değeri TransferMode. akışlı olarak ayarlandığında, büyük akışlar kilitlenmeye neden olabilir ve çağrının zaman aşımına uğrayacaktır. Bu sorunu geçici olarak çözmek için daha küçük mesajlar gönderin veya TransferMode. arabellekli kullanın.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>NetHttpBinding kullanmak için bir hizmet yapılandırma  
 , <xref:System.ServiceModel.NetHttpBinding> Diğer bağlamalamayla aynı şekilde yapılandırılabilir. Aşağıdaki yapılandırma kod parçacığında, ile bir WCF hizmetinin nasıl yapılandırılacağı gösterilmektedir <xref:System.ServiceModel.NetHttpBinding> .  
  
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
  
 Aşağıdaki kod parçacığı, içindeki kodun nasıl ekleneceğini gösterir <xref:System.ServiceModel.NetHttpBinding> .  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler için Bağlamaları Yapılandırma](../configuring-bindings-for-wcf-services.md)
- [Bağlamalar](bindings.md)
- [Sistem tarafından sağlanmış bağlamalar](../system-provided-bindings.md)
- [Çift Yönlü Hizmetler](duplex-services.md)
