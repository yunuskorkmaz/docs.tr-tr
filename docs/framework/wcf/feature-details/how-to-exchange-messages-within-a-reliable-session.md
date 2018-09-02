---
title: 'Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 6b204749ce86b79bf46b2d5c96be1b00dca9500d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419476"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme

Bu konuda, bu tür bir oturumu destekleyen sistem tarafından sağlanan bağlamalar, ancak değil, varsayılan olarak kullanarak bir güvenilir oturum etkinleştirmek için gereken adımlar açıklanmaktadır. Kesin kod kullanarak bir güvenilir oturum etkinleştirmek ya da yapılandırma dosyanızdaki bildirimli olarak. Bu yordam, güvenilir oturum etkinleştirmek ve iletileri, gönderildiği aynı sırada ulşamasını işleyebileceği için hizmet ve istemci yapılandırma dosyalarını kullanır.

Uç nokta yapılandırma öğesi içeren bu yordamı önemli bir parçası olan bir `bindingConfiguration` adlı bir bağlama yapılandırmasını başvuran öznitelik `Binding1`. [  **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesi güvenilir oturumlar etkinleştirmek için bu ada başvuran `enabled` özniteliği [  **\<reliableSession >** ](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) öğesine `true`. Ayarlayarak güvenilir oturum için belirttiğiniz sıralı teslim Güvenceleri `ordered` özniteliğini `true`.

Bu örnekte kaynak kopyası için bkz: [WS güvenilir oturum](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenilir oturum kullanılacak WSHttpBinding hizmetini yapılandırma

1. Hizmet türü için bir hizmet anlaşmasını tanımlar.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Hizmet sözleşmesi bir hizmet sınıfında uygulayın. Adres veya bağlama bilgileri hizmeti uygulaması içinde belirtilmemiş unutmayın. Yapılandırma dosyasından adresi veya bağlama bilgileri bilgileri almak üzere kod yazmak için gerekli değildir.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Oluşturma bir *Web.config* yapılandırmak için bir uç nokta için bir dosya `CalculatorService` kullanan <xref:System.ServiceModel.WSHttpBinding> etkin ve sıralı teslim gerekli iletilerin güvenilir oturum ile.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Oluşturma bir *Service.svc* satırını içeren dosya:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  Bir yerde *Service.svc* Internet Information Services (IIS) sanal dizininizin dosyasında.

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenilir oturum kullanılacak WSHttpBinding istemciyi Yapılandırma

1. Kullanım [ServiceModel meta veri yardımcı Programracı (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Oluşturulan istemci içeren `ICalculator` istemci uygulaması karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Oluşturulan istemci uygulaması da uygulamasını içerir `ClientCalculator`. Adres ve bağlama bilgilerini herhangi bir uygulama hizmetinin içinde belirtilmemiş unutmayın. Yapılandırma dosyasından adresi veya bağlama bilgileri bilgileri almak üzere kod yazmak için gerekli değildir.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe* ayrıca kullanan istemci yapılandırmasını oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı. Yapılandırma dosyası adı *App.config* Visual Studio kullanarak.

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Bir örneğini oluşturmak `ClientCalculator` uygulamada ve hizmet işlemleri çağırın.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Derleyin ve istemci çalıştırın.

## <a name="example"></a>Örnek

Birçok sistem tarafından sağlanan bağlamalar güvenilir oturumlar varsayılan olarak destekler. Bu güncelleştirmeler şunlardır:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Güvenilir oturumlar destekleyen özel bağlama oluşturma örneği için bkz: [nasıl yapılır: HTTPS ile özel bir güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Ayrıca bkz.

[Güvenilir Oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
