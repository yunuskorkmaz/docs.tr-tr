---
title: 'Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 58a392fc6295e82f41e08c80a3343b4059afad7e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141684"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme

Bu konu, bu tür bir oturumu destekleyen ancak varsayılan olarak değil, sistem tarafından belirtilen bağlamalardan birini kullanarak güvenilir bir oturumu etkinleştirmek için gereken adımları açıklar. Yapılandırma dosyanızda kod kullanarak veya bildirimli olarak güvenilir bir oturum imperatively etkinleştirirsiniz. Bu yordam, güvenilir oturumu etkinleştirmek ve iletilerin gönderildikleri sırada gelmesi için istemci ve hizmet yapılandırma dosyalarını kullanır.

Bu yordamın anahtar bölümü, uç nokta yapılandırma öğesinin `Binding1`adlı bağlama yapılandırmasına başvuran bir `bindingConfiguration` özniteliği içermisimdir. [ **\<binding >** ](../../configure-apps/file-schema/wcf/bindings.md) yapılandırma öğesi, [ **\<reliablesession >** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) öğesinin `enabled` özniteliğini `true`olarak ayarlayarak güvenilir oturumları etkinleştirmek için bu ada başvurur. `ordered` özniteliğini `true`olarak ayarlayarak güvenilir oturum için sıralı teslim bildirimlerini belirtirsiniz.

Bu örneğin kaynak kopyası için bkz. [WS güvenilir oturumu](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenli bir oturum kullanmak için bir WSHttpBinding ile hizmeti yapılandırma

1. Hizmet türü için bir hizmet sözleşmesi tanımlayın.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Hizmet sözleşmesini bir hizmet sınıfına uygulayın. Adresin veya bağlama bilgilerinin hizmet uygulamasının içinde belirtilmediğini unutmayın. Yapılandırma dosyasından adresi veya bağlama bilgilerini almak için kod yazmanız gerekmez.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Güvenilir oturum etkinken <xref:System.ServiceModel.WSHttpBinding> kullanan `CalculatorService` için bir uç nokta yapılandırmak üzere bir *Web. config* dosyası oluşturun ve gerekli iletilerin sıralı teslimini yapın.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Satırı içeren bir *Service. svc* dosyası oluşturun:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. *Service. svc* dosyasını Internet INFORMATION SERVICES (IIS) sanal dizinine yerleştirin.

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenli bir oturum kullanmak için istemciyi bir WSHttpBinding ile yapılandırma

1. Hizmet meta verilerinden kod oluşturmak için, komut satırından [ServiceModel meta veri yardımcı programı aracını (*Svcutil. exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Oluşturulan istemci, istemci uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan `ICalculator` arabirimini içerir.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Oluşturulan istemci uygulaması, `ClientCalculator`uygulamasını da içerir. Adres ve bağlama bilgilerinin, hizmet uygulamasının içinde herhangi bir yerde belirtilmediğini unutmayın. Yapılandırma dosyasından adresi veya bağlama bilgilerini almak için kod yazmanız gerekmez.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil. exe* , <xref:System.ServiceModel.WSHttpBinding> sınıfını kullanan istemcinin yapılandırmasını da oluşturur. Visual Studio kullanırken yapılandırma dosyasını *app. config* olarak adlandırın.

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Bir uygulamada `ClientCalculator` örneği oluşturun ve hizmet işlemlerini çağırın.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. İstemcisini derleyin ve çalıştırın.

## <a name="example"></a>Örnek

Sistem tarafından sunulan bağlamalardan bazıları varsayılan olarak güvenilir oturumları destekler. Bu güncelleştirmeler şunlardır:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Güvenilir oturumları destekleyen özel bir bağlamanın nasıl oluşturulacağı hakkında bir örnek için bkz. [nasıl yapılır: https Ile özel bir güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenilir Oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
