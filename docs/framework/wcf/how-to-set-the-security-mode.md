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
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e8c08fba0e4a74eafab00e75977a9f756c1b1cfa
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-set-the-security-mode"></a>Nasıl yapılır: Güvenlik Modunu Ayarlama
Windows Communication Foundation (WCF) güvenlik üzerinde en önceden tanımlanmış bağlamaları bulunan üç genel güvenlik modu vardır: Aktarım, iletisi ve "ileti kimlik bilgileri ile taşıma." İki ek modları için iki bağlamaları belirli: "yalnızca Aktarım-credential" modu bulunan <xref:System.ServiceModel.BasicHttpBinding>ve bulunan "İki" modu <xref:System.ServiceModel.NetMsmqBinding>. Ancak, bu konuda üç genel güvenlik modlarını yoğunlaşır: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, ve <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
 Önceden tanımlanmış her bağlama tüm bu modlarını desteklediğini unutmayın. Bu konuda moduyla ayarlar <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding> sınıfları ve modunu hem program aracılığıyla ve yapılandırma yoluyla nasıl ayarlanacağını gösterir.  
  
 Daha fazla bilgi için bkz: WCF güvenliği, bkz: [güvenliğine genel bakış](../../../docs/framework/wcf/feature-details/security-overview.md), [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md), ve [güvenli hale getirme hizmetler ve istemcileri](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Aktarım modu ve ileti hakkında daha fazla bilgi için bkz: [taşıma güvenliği](../../../docs/framework/wcf/feature-details/transport-security.md) ve [ileti güvenliği](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
### <a name="to-set-the-security-mode-in-code"></a>Kod içinde kullanılan güvenlik modunu ayarlamak için  
  
1.  Kullanmakta olduğunuz bağlama sınıfının bir örneğini oluşturun. Önceden tanımlanmış bağlamaları listesi için bkz: [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md). Bu örnek bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı.  
  
2.  Ayarlama `Mode` tarafından döndürülen nesne özelliğinin `Security` özelliği.  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     Alternatif olarak, modunu aşağıdaki kodda gösterildiği gibi iletiyi ayarlayın.  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     Veya aşağıdaki kodda gösterildiği gibi ileti kimlik bilgileriyle taşıma için modunu ayarlayın.  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  Aşağıdaki kodda gösterildiği gibi bağlama oluşturucuda modu da ayarlayabilirsiniz.  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a>ClientCredentialType özelliği ayarlama  
 Üç değerden birini modunu ayarlama belirler nasıl ayarlanacağını `ClientCredentialType` özelliği. Örneğin, kullanarak <xref:System.ServiceModel.WSHttpBinding> modu ayarını sınıfı `Transport` ayarlamalısınız anlamına gelir <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.HttpTransportSecurity> uygun bir değere sınıfı.  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Aktarım modu için ClientCredentialType özelliğini ayarlamak için  
  
1.  Bağlama örneği oluşturun.  
  
2.  Ayarlama `Mode` özelliğine `Transport`.  
  
3.  Ayarlama `ClientCredential` uygun bir değere özelliği. Aşağıdaki kod özelliği ayarlar `Windows`.  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>İleti modu ClientCredentialType özelliğini ayarlamak için  
  
1.  Bağlama örneği oluşturun.  
  
2.  Ayarlama `Mode` özelliğine `Message`.  
  
3.  Ayarlama `ClientCredential` uygun bir değere özelliği. Aşağıdaki kod özelliği ayarlar `Certificate`.  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Yapılandırma modu ve ClientCredentialType özelliğini ayarlamak için  
  
1.  Bir uygun bağlama öğesi ekleme [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası öğesi. Aşağıdaki örnek, bir [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.  
  
2.  Ekleme bir `<binding>` öğesi ve kümesi kendi `name` öznitelik için uygun bir değer.  
  
3.  Ekleme bir `<security>` öğesi ve kümesi `mode` özniteliğini `Message`, `Transport`, veya `TransportWithMessageCredential`.  
  
4.  Mod ayarlanmışsa `Transport`, ekleme bir `<transport>` öğesi ve kümesi `clientCredential` öznitelik için uygun bir değer.  
  
     Aşağıdaki örnek modunu ayarlar "`Transport"`ve ardından ayarlar `clientCredentialType` özniteliği `<transport>` öğesine"`Windows"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" />  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Alternatif olarak, kümesinin `security mode` için "`Message"`takip eden bir `<"message">` öğesi. Bu örnek ayarlar `clientCredentialType` için "`Certificate"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Kullanarak <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> değeri özel bir durumdur ve aşağıda açıklanmıştır.  
  
### <a name="using-transportwithmessagecredential"></a>TransportWithMessageCredential kullanma  
 Güvenlik modu ayarlarken `TransportWithMessageCredential`, aktarım düzeyinde güvenlik sağlayan gerçek mekanizması taşıma belirler. Örneğin, HTTP protokolünü HTTP (HTTPS) üzerinden Güvenli Yuva Katmanı (SSL) kullanır. Bu nedenle, ayarı `ClientCredentialType` herhangi bir aktarım güvenlik nesnenin özelliği (gibi <xref:System.ServiceModel.HttpTransportSecurity>) göz ardı edilir.  Diğer bir deyişle, yalnızca ayarlayabilirsiniz `ClientCredentialType` ileti güvenlik nesnesinin (için `WSHttpBinding` bağlama, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> nesnesi).  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: kullanım taşıma Güveniği ve ileti kimlik bilgilerini](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Nasıl yapılır: Aktarım Güvenliği ve İleti Kimlik Bilgilerini Kullanma](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Aktarım Güvenliği](../../../docs/framework/wcf/feature-details/transport-security.md)  
 [İleti Güvenliği](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [Güvenliğe Genel Bakış](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Sistem Tarafından Sağlanan Bağlamalar](../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<Güvenlik >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)  
 [\<Güvenlik >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)  
 [\<Güvenlik >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
