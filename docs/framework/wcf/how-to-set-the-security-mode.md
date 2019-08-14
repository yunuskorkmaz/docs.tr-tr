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
ms.openlocfilehash: 6bd81bd24d28f0a9e318d60a3b7fb4aa059f9a49
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971987"
---
# <a name="how-to-set-the-security-mode"></a>Nasıl yapılır: Güvenlik Modunu Ayarlama

Windows Communication Foundation (WCF) güvenliği, en önceden tanımlı bağlamalarda bulunan üç ortak güvenlik moduna sahiptir: Transport, Message ve "ileti kimlik bilgileri ile taşıma." İki bağlama özgü iki ek mod vardır: üzerinde <xref:System.ServiceModel.BasicHttpBinding>bulunan "Transport-Credential Only" modu ve <xref:System.ServiceModel.NetMsmqBinding>üzerinde bulunan "both" modu. Ancak, bu konu üç ortak güvenlik modu üzerinde yoğunlaşır: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>ve <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.

Önceden tanımlanmış her bağlamanın bu modların tümünü desteklediğini unutmayın. Bu konu, <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding> sınıfları ile modunu ayarlar ve modu hem programlı olarak hem de yapılandırma aracılığıyla ayarlamayı gösterir.

Daha fazla bilgi için bkz. WCF güvenliği, [güvenlik genel bakış](../../../docs/framework/wcf/feature-details/security-overview.md), [hizmetleri güvenli hale](../../../docs/framework/wcf/securing-services.md)getirme ve [Hizmetleri ve istemcileri güvenli hale getirme](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Aktarım modu ve ileti hakkında daha fazla bilgi için bkz. [Aktarım güvenliği](../../../docs/framework/wcf/feature-details/transport-security.md) ve [ileti güvenliği](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).

## <a name="to-set-the-security-mode-in-code"></a>Koddaki güvenlik modunu ayarlamak için

1. Kullandığınız bağlama sınıfının bir örneğini oluşturun. Önceden tanımlanmış bağlamaların listesi için bkz. [sistem tarafından sunulan bağlamalar](../../../docs/framework/wcf/system-provided-bindings.md). Bu örnek, <xref:System.ServiceModel.WSHttpBinding> sınıfının bir örneğini oluşturur.

2. Özelliği tarafından döndürülen nesnesinin `Mode` `Security` özelliğini ayarlayın.

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

Modunun üç değerden birine ayarlanması, `ClientCredentialType` özelliği nasıl ayarlayabileceğinizi belirler. Örneğin, <xref:System.ServiceModel.WSHttpBinding> sınıfını kullanarak modunu olarak `Transport` ayarlamak, <xref:System.ServiceModel.HttpTransportSecurity> sınıfının <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> özelliğini uygun bir değere ayarlamanız gerekir.

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Taşıma modu için ClientCredentialType özelliğini ayarlamak için

1. Bağlamanın bir örneğini oluşturun.

2. Ayarlama `Mode` özelliğini `Transport`.

3. `ClientCredential` Özelliği uygun bir değere ayarlayın. Aşağıdaki kod özelliği olarak `Windows`ayarlar.

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Ileti modu için ClientCredentialType özelliğini ayarlamak için

1. Bağlamanın bir örneğini oluşturun.

2. Ayarlama `Mode` özelliğini `Message`.

3. `ClientCredential` Özelliği uygun bir değere ayarlayın. Aşağıdaki kod özelliği olarak `Certificate`ayarlar.

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Yapılandırmada Mode ve ClientCredentialType özelliğini ayarlamak için

1. Yapılandırma dosyasının [ \<Bindings >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesine uygun bir bağlama öğesi ekleyin. Aşağıdaki örnek bir [ \<WSHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ekler.

2. Bir `<binding>` öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın.

3. `<security>` Bir öğesi ekleyin ve `mode` özniteliği `Message`, `Transport`veya olarakayarlayın.`TransportWithMessageCredential`

4. Mod olarak `Transport`ayarlandıysa, bir `<transport>` öğesi ekleyin ve `clientCredential` özniteliği uygun bir değere ayarlayın.

     Aşağıdaki örnek,`Transport"`modunu "olarak ayarlar ve sonra `<transport>` öğesinin `clientCredentialType` özniteliğini"`Windows"`olarak ayarlar.

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Alternatif olarak, `security mode` `<"message">` öğesini ve ardından`Message"`öğesini olarak ayarlayın. Bu örnek, `clientCredentialType` "`Certificate"`olarak ayarlar.

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> Değeri kullanmak özel bir durumdur ve aşağıda açıklanmıştır.

### <a name="using-transportwithmessagecredential"></a>TransportWithMessageCredential kullanma

Güvenlik modu olarak `TransportWithMessageCredential`ayarlandığında, taşıma, aktarım düzeyi güvenliği sağlayan gerçek mekanizmayı belirler. Örneğin, HTTP Protokolü HTTP (HTTPS) üzerinden Güvenli Yuva Katmanı (SSL) kullanır. Bu nedenle, herhangi `ClientCredentialType` bir aktarım güvenliği nesnesinin ( <xref:System.ServiceModel.HttpTransportSecurity>gibi) özelliğinin ayarlanması yok sayılır.  Diğer `ClientCredentialType` bir deyişle, yalnızca ileti güvenliği nesnesinin ( `WSHttpBinding` bağlama, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> nesne) kümesini ayarlayabilirsiniz.

Daha fazla bilgi için [nasıl yapılır: Taşıma güvenliği ve Ileti kimlik bilgilerini](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Nasıl yapılır: Taşıma güvenliği ve Ileti kimlik bilgilerini kullanma](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Aktarım Güvenliği](../../../docs/framework/wcf/feature-details/transport-security.md)
- [İleti Güvenliği](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [Güvenliğe Genel Bakış](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../../../docs/framework/wcf/system-provided-bindings.md)
- [\<Güvenlik >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<Güvenlik >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<Güvenlik >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
