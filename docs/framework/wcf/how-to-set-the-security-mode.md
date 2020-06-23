---
title: 'Nasıl yapılır: Güvenlik Modunu Ayarlama'
description: 'En önceden tanımlı bağlamalarda üç ortak WCF güvenlik modunu ayarlamayı öğrenin: Transport, Message ve TransportWithMessageCredential.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 2f834e1930b7676592f6cbc29a577424d75ebc01
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244549"
---
# <a name="how-to-set-the-security-mode"></a>Nasıl yapılır: Güvenlik Modunu Ayarlama

Windows Communication Foundation (WCF) güvenliği, en önceden tanımlı bağlamalarda bulunan üç ortak güvenlik moduna sahiptir: Transport, Message ve "ileti kimlik bilgileri ile taşıma." İki bağlama özgü iki ek mod vardır: üzerinde bulunan "Transport-Credential Only" modu <xref:System.ServiceModel.BasicHttpBinding> ve üzerinde bulunan "both" modu <xref:System.ServiceModel.NetMsmqBinding> . Ancak, bu konu üç ortak güvenlik modu üzerinde yoğunlaşır: <xref:System.ServiceModel.SecurityMode.Transport> , <xref:System.ServiceModel.SecurityMode.Message> ve <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .

Önceden tanımlanmış her bağlamanın bu modların tümünü desteklediğini unutmayın. Bu konu, ve sınıfları ile modunu <xref:System.ServiceModel.WSHttpBinding> Ayarlar <xref:System.ServiceModel.NetTcpBinding> ve modu hem programlı olarak hem de yapılandırma aracılığıyla ayarlamayı gösterir.

Daha fazla bilgi için bkz. WCF güvenliği, [güvenlik genel bakış](./feature-details/security-overview.md), [hizmetleri güvenli hale](securing-services.md)getirme ve [Hizmetleri ve istemcileri güvenli hale getirme](./feature-details/securing-services-and-clients.md). Aktarım modu ve ileti hakkında daha fazla bilgi için bkz. [Aktarım güvenliği](./feature-details/transport-security.md) ve [ileti güvenliği](./feature-details/message-security-in-wcf.md).

## <a name="to-set-the-security-mode-in-code"></a>Koddaki güvenlik modunu ayarlamak için

1. Kullandığınız bağlama sınıfının bir örneğini oluşturun. Önceden tanımlanmış bağlamaların listesi için bkz. [sistem tarafından sunulan bağlamalar](system-provided-bindings.md). Bu örnek, sınıfının bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> .

2. `Mode`Özelliği tarafından döndürülen nesnesinin özelliğini ayarlayın `Security` .

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     Alternatif olarak, aşağıdaki kodda gösterildiği gibi modunu ileti olarak ayarlayın.

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     Ya da aşağıdaki kodda gösterildiği gibi modu ileti kimlik bilgileriyle taşıma olarak ayarlayın.

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. Ayrıca, aşağıdaki kodda gösterildiği gibi, bağlama oluşturucusunda modu da ayarlayabilirsiniz.

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a>ClientCredentialType özelliği ayarlanıyor

Modunun üç değerden birine ayarlanması, özelliği nasıl ayarlayabileceğinizi belirler `ClientCredentialType` . Örneğin, <xref:System.ServiceModel.WSHttpBinding> sınıfını kullanarak modunu olarak ayarlamak, `Transport` <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> <xref:System.ServiceModel.HttpTransportSecurity> sınıfının özelliğini uygun bir değere ayarlamanız gerekir.

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Taşıma modu için ClientCredentialType özelliğini ayarlamak için

1. Bağlamanın bir örneğini oluşturun.

2. `Mode`Özelliğini olarak ayarlayın `Transport` .

3. `ClientCredential`Özelliği uygun bir değere ayarlayın. Aşağıdaki kod özelliği olarak ayarlar `Windows` .

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Ileti modu için ClientCredentialType özelliğini ayarlamak için

1. Bağlamanın bir örneğini oluşturun.

2. `Mode`Özelliğini olarak ayarlayın `Message` .

3. `ClientCredential`Özelliği uygun bir değere ayarlayın. Aşağıdaki kod özelliği olarak ayarlar `Certificate` .

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Yapılandırmada Mode ve ClientCredentialType özelliğini ayarlamak için

1. Yapılandırma dosyasının öğesine uygun bir bağlama öğesi ekleyin [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) . Aşağıdaki örnek bir öğesi ekler [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) .

2. Bir `<binding>` öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın.

3. Bir `<security>` öğesi ekleyin ve `mode` özniteliği `Message` , veya olarak ayarlayın `Transport` `TransportWithMessageCredential` .

4. Mod olarak ayarlandıysa `Transport` , bir `<transport>` öğesi ekleyin ve `clientCredential` özniteliği uygun bir değere ayarlayın.

     Aşağıdaki örnek, modunu " `Transport"` olarak ayarlar ve sonra `clientCredentialType` `<transport>` öğesinin özniteliğini" olarak ayarlar `Windows"` .

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Alternatif olarak, `security mode` `Message"` öğesini ve ardından öğesini olarak ayarlayın `<"message">` . Bu örnek, `clientCredentialType` "olarak ayarlar `Certificate"` .

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Değeri kullanmak <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> özel bir durumdur ve aşağıda açıklanmıştır.

### <a name="using-transportwithmessagecredential"></a>TransportWithMessageCredential kullanma

Güvenlik modu olarak ayarlandığında `TransportWithMessageCredential` , taşıma, aktarım düzeyi güvenliği sağlayan gerçek mekanizmayı belirler. Örneğin, HTTP Protokolü HTTP (HTTPS) üzerinden Güvenli Yuva Katmanı (SSL) kullanır. Bu nedenle, `ClientCredentialType` herhangi bir aktarım güvenliği nesnesinin (gibi) özelliğinin ayarlanması <xref:System.ServiceModel.HttpTransportSecurity> yok sayılır.  Diğer bir deyişle, yalnızca `ClientCredentialType` ileti güvenliği nesnesinin ( `WSHttpBinding` bağlama, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> nesne) kümesini ayarlayabilirsiniz.

Daha fazla bilgi için bkz. [nasıl yapılır: taşıma güvenlik ve Ileti kimlik bilgilerini kullanma](./feature-details/how-to-use-transport-security-and-message-credentials.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Aktarım Güvenliği](./feature-details/transport-security.md)
- [İleti Güvenliği](./feature-details/message-security-in-wcf.md)
- [Güvenliğe genel bakış](./feature-details/security-overview.md)
- [Sistem tarafından sağlanmış bağlamalar](system-provided-bindings.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
