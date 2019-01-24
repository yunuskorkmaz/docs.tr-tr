---
title: Çift Yönlü Hizmetler
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: 9adbb4166d713cea0344c9fa58ce85e5afce086d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717930"
---
# <a name="duplex-services"></a>Çift Yönlü Hizmetler
Çift yönlü hizmet sözleşmesi, her iki bitiş noktası iletileri diğer bağımsız olarak gönderebilir ileti değişim deseni ' dir. Çift yönlü bir hizmet, bu nedenle, olay benzeri davranış sağlayan geri istemci uç noktası için iletileri gönderebilir. Bir istemci bir hizmete bağlanır ve hizmet üzerinde hizmet istemciye iletileri gönderebilir bir kanal sağlar çift yönlü iletişimi gerçekleşir. Çift yönlü hizmetler olay benzeri davranışını yalnızca bir oturumunda çalıştığını unutmayın.  
  
 Çift yönlü sözleşme oluşturma için bir çift arabirimler oluşturun. İlk istemci çağırabilirsiniz işlemleri açıklayan hizmet sözleşme arabirimidir. Bu hizmet sözleşmesini belirtmelisiniz bir *geri çağırma anlaşması* içinde <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özelliği. Geri çağırma anlaşması istemci uç noktada bir hizmeti çağıran işlemleri tanımlayan arabirimidir. Çift yönlü sözleşme bir oturumu gerektirmez, sistem tarafından sağlanan çift yönlü bağlamaları olun olsa da bunları kullanın.  
  
 Çift yönlü sözleşme örneği verilmiştir.  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 `CalculatorService` Sınıfın uyguladığı birincil `ICalculatorDuplex` arabirimi. Hizmeti kullandığı <xref:System.ServiceModel.InstanceContextMode.PerSession> her oturum için sonuç korumak için örnek modu. Adlı bir özel özellik `Callback` istemci geri çağırma kanala erişir. Hizmet geri çağırma aracılığıyla geri çağırma arabirimi istemciye ileti göndermek için aşağıdaki örnek kodda gösterildiği gibi kullanır.  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 İstemci, hizmeti iletileri almak için çift yönlü sözleşme geri arama arabirimini uygulayan bir sınıf sağlamanız gerekir. Aşağıdaki örnek kodun gösterdiği bir `CallbackHandler` uygulayan sınıf `ICalculatorDuplexCallback` arabirimi.  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 Çift yönlü sözleşme gerektirir oluşturan WCF istemcisini bir <xref:System.ServiceModel.InstanceContext> yapım sırasında sağlanacak sınıfı. Bu <xref:System.ServiceModel.InstanceContext> sınıfı, geri arama arayüzü uygular ve hizmetinden gönderilen iletileri işleyen bir nesne için site olarak kullanılır. Bir <xref:System.ServiceModel.InstanceContext> sınıf örneği ile oluşturulmuş `CallbackHandler` sınıfı. Bu nesne, hizmetten geri çağırma arabirimi istemciye gönderilen iletileri işler.  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 Oturum iletişim hem çift yönlü iletişimi destekleyen bir bağlama sağlamak için hizmeti için yapılandırma ayarlanması gerekir. `wsDualHttpBinding` Öğesi oturumu iletişimi destekler ve her yön için bir ikili HTTP bağlantılarını sağlayarak çift yönlü iletişim sağlar.  
  
 İstemcide, sunucu istemciye bağlanmak için aşağıdaki örnek yapılandırmada gösterildiği gibi kullanabileceğiniz bir adresi yapılandırmanız gerekir.  
  
  
  
> [!NOTE]
>  Genellikle bir güvenli konuşma kullanarak kimlik doğrulaması için başarısız olmayan yönlü istemciler durum bir <xref:System.ServiceModel.Security.MessageSecurityException>. Ancak, bir güvenli konuşma kullanan çift yönlü istemci kimlik doğrulaması başarısız olursa, istemci alır bir <xref:System.TimeoutException> yerine.  
  
 Kullanarak bir istemci/hizmet oluşturursanız `WSHttpBinding` öğesi ve istemci geri çağırma uç noktası içermez, aşağıdaki hatayı alırsınız.  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 Aşağıdaki örnek kod istemci belirtmek uç nokta adresi programlı olarak gösterilmektedir.
  
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

 Aşağıdaki örnek kod, uç nokta adresi yapılandırmada istemci belirtmek nasıl gösterir.  
  
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
>  Bir hizmet veya istemcinin, kanal kapandığında çift yönlü modeli otomatik olarak algılamaz. Bu nedenle istemci beklenmedik şekilde sonlandırılırsa, varsayılan olarak hizmet değil bildirilir veya bir istemci beklenmedik şekilde sonlandırılırsa, hizmet olmayan bildirilir. Bu nedenle seçerseniz birbirine bildirmek için kendi protokolü, istemciler ve hizmetler uygulayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çift Yönlü](../../../../docs/framework/wcf/samples/duplex.md)
- [İstemci Çalışma Zamanı Davranışını Belirtme](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [Nasıl yapılır: Kanal fabrikası oluşturma ve bunu kanal oluşturmak ve yönetmek için kullanın](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
