---
title: 'Nasıl yapılır: Güvenlik Modunu Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 9b9e25cbafb6387b4584a21fd642d80bc41cd8dc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320903"
---
# <a name="how-to-set-the-security-mode"></a>Nasıl yapılır: Güvenlik Modunu Ayarlama

Windows Communication Foundation (WCF) güvenliği, en önceden tanımlı bağlamalarda bulunan üç ortak güvenlik moduna sahiptir: Transport, Message ve "ileti kimlik bilgileri ile taşıma." İki bağlama özgü iki ek mod vardır: <xref:System.ServiceModel.BasicHttpBinding> ve "both" modunda bulunan "yalnızca Transport-Credential" modu, <xref:System.ServiceModel.NetMsmqBinding> ' de bulunur. Ancak, bu konu üç genel güvenlik modunda yoğunlaşır: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message> ve <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.

Önceden tanımlanmış her bağlamanın bu modların tümünü desteklediğini unutmayın. Bu konu, modu <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding> sınıflarıyla ayarlar ve modu hem programlı olarak hem de yapılandırma aracılığıyla ayarlamayı gösterir.

Daha fazla bilgi için bkz. WCF güvenliği, [güvenlik genel bakış](./feature-details/security-overview.md), [hizmetleri güvenli hale](securing-services.md)getirme ve [Hizmetleri ve istemcileri güvenli hale getirme](./feature-details/securing-services-and-clients.md). Aktarım modu ve ileti hakkında daha fazla bilgi için bkz. [Aktarım güvenliği](./feature-details/transport-security.md) ve [ileti güvenliği](./feature-details/message-security-in-wcf.md).

## <a name="to-set-the-security-mode-in-code"></a>Koddaki güvenlik modunu ayarlamak için

1. Kullandığınız bağlama sınıfının bir örneğini oluşturun. Önceden tanımlanmış bağlamaların listesi için bkz. [sistem tarafından sunulan bağlamalar](system-provided-bindings.md). Bu örnek <xref:System.ServiceModel.WSHttpBinding> sınıfının bir örneğini oluşturur.

2. @No__t-1 özelliği tarafından döndürülen nesnenin `Mode` özelliğini ayarlayın.

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

Modunun üç değerden birine ayarlanması `ClientCredentialType` özelliğini nasıl ayarlayabileceğinizi belirler. Örneğin, <xref:System.ServiceModel.WSHttpBinding> sınıfını kullanarak mod `Transport` olarak ayarlandığında, <xref:System.ServiceModel.HttpTransportSecurity> sınıfının <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> özelliğini uygun bir değere ayarlamanız gerekir.

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Taşıma modu için ClientCredentialType özelliğini ayarlamak için

1. Bağlamanın bir örneğini oluşturun.

2. @No__t-0 özelliğini `Transport` olarak ayarlayın.

3. @No__t-0 özelliğini uygun bir değere ayarlayın. Aşağıdaki kod, özelliği `Windows` olarak ayarlar.

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Ileti modu için ClientCredentialType özelliğini ayarlamak için

1. Bağlamanın bir örneğini oluşturun.

2. @No__t-0 özelliğini `Message` olarak ayarlayın.

3. @No__t-0 özelliğini uygun bir değere ayarlayın. Aşağıdaki kod, özelliği `Certificate` olarak ayarlar.

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Yapılandırmada Mode ve ClientCredentialType özelliğini ayarlamak için

1. Yapılandırma dosyasının [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) öğesine uygun bir bağlama öğesi ekleyin. Aşağıdaki örnek [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ekler.

2. @No__t-0 öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın.

3. @No__t-0 öğesi ekleyin ve `mode` özniteliğini `Message`, `Transport` veya `TransportWithMessageCredential` olarak ayarlayın.

4. Mod `Transport` olarak ayarlandıysa, bir `<transport>` öğesi ekleyin ve `clientCredential` özniteliğini uygun bir değere ayarlayın.

     Aşağıdaki örnek, modunu "`Transport"`" olarak ayarlar ve `<transport>` öğesinin `clientCredentialType` özniteliğini "`Windows"`" olarak ayarlar.

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Alternatif olarak, `security mode` ' ı "`Message"`, sonra da `<"message">` öğesi olarak ayarlayın. Bu örnek `clientCredentialType` ' i "`Certificate"` olarak ayarlar.

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     @No__t-0 değerinin kullanılması özel bir durumdur ve aşağıda açıklanmaktadır.

### <a name="using-transportwithmessagecredential"></a>TransportWithMessageCredential kullanma

Güvenlik modunu `TransportWithMessageCredential` olarak ayarlarken, taşıma, aktarım düzeyi güvenliği sağlayan gerçek mekanizmayı belirler. Örneğin, HTTP Protokolü HTTP (HTTPS) üzerinden Güvenli Yuva Katmanı (SSL) kullanır. Bu nedenle, herhangi bir taşıma güvenlik nesnesinin (<xref:System.ServiceModel.HttpTransportSecurity> gibi) `ClientCredentialType` özelliğinin ayarlanması yok sayılır.  Diğer bir deyişle, ileti güvenliği nesnesinin `ClientCredentialType` ' ı (`WSHttpBinding` bağlama, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> nesnesi) ayarlayabilirsiniz.

Daha fazla bilgi için bkz. [nasıl yapılır: taşıma güvenlik ve Ileti kimlik bilgilerini kullanma](./feature-details/how-to-use-transport-security-and-message-credentials.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Nasıl yapılır: Aktarım Güvenliği ve İleti Kimlik Bilgilerini Kullanma](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Aktarım Güvenliği](./feature-details/transport-security.md)
- [İleti Güvenliği](./feature-details/message-security-in-wcf.md)
- [Güvenliğe Genel Bakış](./feature-details/security-overview.md)
- [Sistem Tarafından Sağlanan Bağlamalar](system-provided-bindings.md)
- [\<Güvenlik >](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<Güvenlik >](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<Güvenlik >](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
