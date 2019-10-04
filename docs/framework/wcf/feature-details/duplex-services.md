---
title: Çift Yönlü Hizmetler
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: 4fd8b679dcd4ac9efce5fa915118736b15206068
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834777"
---
# <a name="duplex-services"></a>Çift Yönlü Hizmetler

Çift yönlü hizmet sözleşmesi, her iki bitiş noktası da birbirlerine ayrı olarak ileti gönderebileceği bir ileti değişim modelidir. Bu nedenle bir çift yönlü hizmet, iletileri istemci uç noktasına geri gönderebilirler ve olay benzeri davranışlar sağlar. Çift yönlü iletişim, bir istemci bir hizmete bağlandığında ve hizmetin istemciye geri ileti gönderebileceği bir kanalla birlikte hizmetine hizmet sağlıyorsa oluşur. Çift yönlü hizmetlerin olay benzeri davranışının yalnızca bir oturum içinde çalışıp çalışmadığını unutmayın.

Bir çift yönlü sözleşme oluşturmak için bir çift arabirim oluşturabilirsiniz. Birincisi, bir istemcinin çağırabileceği işlemleri açıklayan hizmet sözleşmesi arabirimidir. Bu hizmet sözleşmesinin <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özelliğinde bir *geri çağırma anlaşması* belirtmesi gerekir. Geri arama sözleşmesi, hizmetin istemci uç noktasında çağırabileceğine yönelik işlemleri tanımlayan arabirimdir. Bir çift yönlü sözleşme, sistem tarafından sağlanmış çift yönlü bağlamaların bunları kullanmasına rağmen bir oturum gerektirmez.

Bir çift yönlü sözleşmenin bir örneği aşağıda verilmiştir.

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

@No__t-0 sınıfı, birincil `ICalculatorDuplex` arabirimini uygular. Hizmet, her bir oturumun sonucunu korumak için <xref:System.ServiceModel.InstanceContextMode.PerSession> örnek modunu kullanır. @No__t-0 adlı özel bir özellik, istemciye geri çağırma kanalına erişir. Hizmet, aşağıdaki örnek kodda gösterildiği gibi geri çağırma arabirimi aracılığıyla istemciye geri dönüş iletileri göndermek için geri aramayı kullanır.

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

İstemci, hizmetten ileti almak için çift yönlü sözleşmenin geri çağırma arabirimini uygulayan bir sınıf sağlamalıdır. Aşağıdaki örnek kod, `ICalculatorDuplexCallback` arabirimini uygulayan `CallbackHandler` sınıfını gösterir.

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

Bir çift yönlü sözleşme için oluşturulan WCF istemcisinin, oluşturma sırasında <xref:System.ServiceModel.InstanceContext> sınıfının sağlanması gerekir. Bu <xref:System.ServiceModel.InstanceContext> sınıfı, geri çağırma arabirimini uygulayan ve hizmetten geri gönderilen iletileri işleyen bir nesnenin sitesi olarak kullanılır. @No__t-0 sınıfı, `CallbackHandler` sınıfının bir örneğiyle oluşturulur. Bu nesne hizmetten geri çağırma arabirimindeki istemciye gönderilen iletileri işler.

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

Her iki oturum iletişimini ve çift yönlü iletişimi destekleyen bir bağlama sağlamak üzere hizmetin yapılandırması ayarlanmalıdır. @No__t-0 öğesi oturum iletişimini destekler ve her yön için bir tane olmak üzere çift HTTP bağlantısı sağlayarak çift yönlü iletişime olanak sağlar.

İstemcisinde, aşağıdaki örnek yapılandırmada gösterildiği gibi, sunucunun istemciye bağlanmak için kullanabileceği bir adres yapılandırmanız gerekir.

> [!NOTE]
> Güvenli bir konuşma kullanarak kimlik doğrulaması başarısız olan ve çift yönlü olmayan istemciler genellikle @no__t (0) oluşturur. Ancak, güvenli bir konuşma kullanan bir çift yönlü istemci kimlik doğrulayamazsa, istemci bunun yerine bir <xref:System.TimeoutException> alır.

@No__t-0 öğesini kullanarak bir istemci/hizmet oluşturursanız ve istemci geri çağırma uç noktasını eklemezseniz, aşağıdaki hatayı alırsınız.

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

Aşağıdaki örnek kod, istemci uç noktası adresinin programlı olarak nasıl kullanılacağını göstermektedir.

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

Aşağıdaki örnek kod, yapılandırmada istemci uç noktası adresinin nasıl ekleneceğini gösterir.

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
> Bir hizmet veya istemci, kanalını kapattığında çift yönlü model otomatik olarak algılamaz. Bu nedenle, bir istemci beklenmedik şekilde sonlandırılırsa, varsayılan olarak hizmete bildirilmez veya bir hizmetin beklenmedik şekilde sonlandırılırsa, istemciye bildirim uygulanmaz. Bağlantısı kesilen bir hizmet kullanıyorsanız, <xref:System.ServiceModel.CommunicationException> özel durumu oluşturulur. İstemciler ve hizmetler, seçeneğini belirlerseniz, birbirlerine bildirimde bulunan kendi protokollerini uygulayabilir. Hata işleme hakkında daha fazla bilgi için bkz. [WCF hata işleme](../wcf-error-handling.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Çift Yönlü](../samples/duplex.md)
- [İstemci Çalışma Zamanı Davranışını Belirtme](../specifying-client-run-time-behavior.md)
- [Nasıl yapılır: Kanal Fabrikası Oluşturma ve Bunu Kanal Oluşturmak ve Yönetmek için Kullanma](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
