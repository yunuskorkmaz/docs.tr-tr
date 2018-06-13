---
title: Çift Yönlü Hizmetler
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: da92b8f2d1223f582677a93a8ff6fd697512d297
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037369"
---
# <a name="duplex-services"></a>Çift Yönlü Hizmetler
Çift yönlü hizmet sözleşmesi, her iki uç nokta ileti diğer bağımsız olarak gönderebilirsiniz bir ileti değişim deseni değil. Çift yönlü bir hizmet, bu nedenle, olay benzeri davranışı sağlama geri istemci uç noktaya iletileri gönderebilir. Çift yönlü iletişimi bir istemci bir hizmetine bağlanır ve hizmet üzerinde hizmet istemciye iletiler gönderebilir bir kanal sağlar oluşur. Çift yönlü hizmetler olay benzeri davranışını yalnızca bir oturumunda çalıştığını unutmayın.  
  
 Çift yönlü sözleşme oluşturmak için bir çift arabirimleri oluşturun. İlk istemci çağırabileceği işlemleri açıklayan hizmet sözleşmesi arabirimidir. Bu hizmet sözleşmesini belirtmelisiniz bir *geri çağırma sözleşme* içinde <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özelliği. Geri arama sözleşmesi, hizmetin istemci uç noktada çağırabilirsiniz işlemleri tanımlayan arabirimidir. Sistem tarafından sağlanan çift yönlü bağlamaları olun olsa da çift yönlü sözleşme bir oturum gerektirmez bunları kullanın.  
  
 Çift yönlü sözleşme örneği verilmiştir.  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 `CalculatorService` Sınıfı uygulayan birincil `ICalculatorDuplex` arabirimi. Hizmet kullandığı <xref:System.ServiceModel.InstanceContextMode.PerSession> her oturum için sonuç korumak için örnek modu. Adlı özel özellik `Callback` geri çağırma kanal istemciye erişir. Hizmet geri çağırma istemciye geri çağırma arabirimi üzerinden ileti göndermek için aşağıdaki örnek kodda gösterildiği gibi kullanır.  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 İstemci hizmetinden iletileri almak için çift yönlü sözleşme geri çağırma arabirimi uygulayan bir sınıf sağlamanız gerekir. Aşağıdaki örnek kod gösterir bir `CallbackHandler` uygulayan sınıf `ICalculatorDuplexCallback` arabirimi.  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 Çift yönlü sözleşme gerektirir oluşturan WCF istemcisini bir <xref:System.ServiceModel.InstanceContext> yapım sağlanacak sınıfı. Bu <xref:System.ServiceModel.InstanceContext> sınıfı, geri çağırma arabirimini uygulayan ve geri hizmetinden gönderilen iletileri işleyen bir nesne için site olarak kullanılır. Bir <xref:System.ServiceModel.InstanceContext> sınıfı örneği ile oluşturulan `CallbackHandler` sınıfı. Bu nesne hizmetinden geri çağırma arabirimi istemciye gönderilen iletileri işler.  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 Oturum iletişim ve çift yönlü iletişimi destekleyen bir bağlama sağlamak için hizmeti için yapılandırma ayarlanması gerekir. `wsDualHttpBinding` Öğesi oturum iletişimi destekler ve her yön için bir tane çift HTTP bağlantılarını sağlayarak çift yönlü iletişimi sağlar.  
  
 İstemcide, sunucu istemciye bağlanmak için kullanabileceğiniz aşağıdaki örnek yapılandırmada gösterildiği gibi bir adresi yapılandırmanız gerekir.  
  
  
  
> [!NOTE]
>  Güvenli Konuşmayla genellikle kullanarak kimlik doğrulaması için başarısız olmayan çift yönlü istemcileri throw bir <xref:System.ServiceModel.Security.MessageSecurityException>. Ancak, istemci kimlik doğrulaması güvenli bir konuşma kullanan çift yönlü istemci başarısız olursa, alır bir <xref:System.TimeoutException> yerine.  
  
 Bir istemci/hizmetini kullanarak oluşturursanız `WSHttpBinding` öğesi ve istemci geri araması endpoint dahil, aşağıdaki hatayı alırsınız.  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 Aşağıdaki örnek kod istemci belirtmek uç nokta adresi programlı olarak gösterilmiştir.
  
```csharp  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")  
```

 Aşağıdaki örnek kod istemci belirtmek uç nokta adresi yapılandırmasında gösterilmiştir.  
  
```xml  
<client>  
    <endpoint name ="ServerEndpoint"   
          address="http://localhost:12000/DuplexTestUsingConfig/Server"  
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"   
            binding="wsDualHttpBinding"  
           contract="IDuplexTest" />  
</client>  
<bindings>  
    <wsDualHttpBinding>  
        <binding name="WSDualHttpBinding_IDuplexTest"    
          clientBaseAddress="http://localhost:8000/myClient/" >  
            <security mode="None"/>  
         </binding>  
    </wsDualHttpBinding>  
</bindings>  
```  
  
> [!WARNING]
>  Bir hizmet veya istemci kendi kanal kapandığında çift yönlü modeli otomatik olarak algılamaz. Bu nedenle istemci beklenmedik şekilde sona ererse, varsayılan olarak hizmet değil bildirilecek veya bir istemci beklenmedik şekilde sona ererse, hizmet olmayan bildirilir. Bu nedenle seçerseniz birbirine bildirmek için kendi protokolü, istemciler ve hizmetler uygulayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çift Yönlü](../../../../docs/framework/wcf/samples/duplex.md)  
 [İstemci Çalışma Zamanı Davranışını Belirtme](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [Nasıl yapılır: Kanal Fabrikası Oluşturma ve Bunu Kanal Oluşturmak ve Yönetmek için Kullanma](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
