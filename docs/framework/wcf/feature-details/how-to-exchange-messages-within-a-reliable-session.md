---
title: "Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aad62d8532fff09157d53f8307fb2b9dcd506cd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme

Bu konuda bu tür bir oturum desteği sistem tarafından sağlanan bağlamalar, ancak varsayılan kullanarak bir güvenilir oturum etkinleştirmek için gereken adımlar açıklanır. İmperatively kod kullanarak bir güvenilir oturum etkinleştirmek veya bildirimli olarak yapılandırma dosyanızda. Bu yordam, güvenli oturum etkinleştirmek ve iletiler içinde gönderildikleri sırayla geldiğinde ilkelerde izni belirtmek için istemci ve hizmet yapılandırma dosyalarını kullanır.

Uç nokta yapılandırma öğesi içeren bu yordamı anahtar parçası olan bir `bindingConfiguration` adlı bir bağlama yapılandırması başvuran özniteliği `Binding1`. [  **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesine başvuruyor ayarlayarak güvenilir oturumlar etkinleştirmek için bu ad `enabled` özniteliği [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) öğesine `true`. Ayarlayarak güvenilir oturum için belirttiğiniz sıralı teslim Güvenceleri `ordered` özniteliğini `true`.

Bu örnekte kaynak kopyası için bkz: [WS güvenilir oturum](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenilir oturum kullanmak için bir WSHttpBinding hizmetini yapılandırma

1. Hizmet türü için bir hizmet sözleşmesini tanımlama.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Bir hizmet sınıfında Hizmet sözleşmesini uygulama. Adres veya bağlama bilgisi hizmet uygulaması içinde belirlenmezse unutmayın. Yapılandırma dosyasından adresi veya bağlama bilgileri bilgileri almak üzere kod yazmak için gerekli değildir.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Oluşturma bir *Web.config* için bir uç nokta yapılandırmak için bir dosya `CalculatorService` kullanan <xref:System.ServiceModel.WSHttpBinding> etkin ve sıralı gerekli iletileri teslimini güvenilir oturum ile.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Oluşturma bir *Service.svc* bir çizgi içeren dosya:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  Yer *Service.svc* , Internet Information Services (IIS) sanal dizinde dosya.

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenilir oturum kullanmak için bir WSHttpBinding istemciyi Yapılandırma

1. Kullanım [ServiceModel meta veri yardımcı Programracı (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Oluşturulan istemci içeren `ICalculator` istemci uygulaması getirmelidir hizmet sözleşmesini tanımlayan arabirimi.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Oluşturulan istemci uygulaması da uyarlamasını içeren `ClientCalculator`. Adres ve bağlama bilgilerini hizmet uygulaması içinde herhangi bir yere belirlenmezse unutmayın. Yapılandırma dosyasından adresi veya bağlama bilgileri bilgileri almak üzere kod yazmak için gerekli değildir.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe* ayrıca kullanan istemci yapılandırması oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı. Yapılandırma dosyası adı *App.config* kullanırken [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Bir örneğini oluşturmak `ClientCalculator` bir uygulamada ve hizmet işlemlerini çağırma.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Derleme ve istemci çalıştırın.

## <a name="example"></a>Örnek

Sistem tarafından sağlanan bağlamalar çeşitli güvenilir oturumlar varsayılan olarak destekler. Bu güncelleştirmeler şunlardır:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Güvenilir oturumlar destekleyen özel bağlama oluşturma örneği için bkz: [nasıl yapılır: HTTPS ile özel bir güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Ayrıca bkz.

[Güvenilir Oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
