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
ms.openlocfilehash: 32fd1ebede841488d1bfabd2f92bd3fb1ffb55e8
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193193"
---
# <a name="how-to-set-the-security-mode"></a>Nasıl yapılır: Güvenlik Modunu Ayarlama
Windows Communication Foundation (WCF) güvenlik üzerinde en önceden tanımlanmış bağlamaları bulunan üç yaygın güvenlik modu vardır: aktarım iletisi ve "ileti kimlik bilgileri ile aktarma." İki ek modları için iki bağlamaları belirli: "yalnızca Aktarım-credential" modu sonucuna <xref:System.ServiceModel.BasicHttpBinding>ve bulunan "Hem" modu <xref:System.ServiceModel.NetMsmqBinding>. Ancak, bu konuda üç yaygın güvenlik modlarını yoğunlaşır: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, ve <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
 Önceden tanımlanmış her bağlama tüm bu modlardan desteklediğini unutmayın. Bu konuda moduyla ayarlar <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding> sınıfları ve programlı ve yapılandırma yoluyla modunu ayarlama işlemi gösterilmektedir.  
  
 Daha fazla bilgi için bkz, WCF güvenlik bkz [güvenliğine genel bakış](../../../docs/framework/wcf/feature-details/security-overview.md), [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md), ve [Hizmetleri güvenli hale getirme ve istemciler](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Aktarım modu ve ileti hakkında daha fazla bilgi için bkz. [aktarım güvenliği](../../../docs/framework/wcf/feature-details/transport-security.md) ve [ileti güvenliği](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
### <a name="to-set-the-security-mode-in-code"></a>Kod içinde güvenlik modunu ayarlama  
  
1.  Kullanmakta olduğunuz bağlama sınıfının bir örneğini oluşturun. Önceden tanımlanmış bağlamaları bir listesi için bkz. [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md). Bu örnek, bir örneğini oluşturur. <xref:System.ServiceModel.WSHttpBinding> sınıfı.  
  
2.  Ayarlama `Mode` özelliği tarafından döndürülen nesne `Security` özelliği.  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     Alternatif olarak, aşağıdaki kodda gösterildiği gibi modu iletisine ayarlayın.  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     Veya aşağıdaki kodda gösterildiği gibi ileti kimlik bilgileri ile aktarma için moduna ayarlayın.  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  Bağlama oluşturucusunun içinde aşağıdaki kodda gösterildiği gibi modunu ayarlayabilirsiniz.  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a>ClientCredentialType özelliğini ayarlama  
 Üç değerden birini modunu ayarlama belirler nasıl ayarlanacağını `ClientCredentialType` özelliği. Örnek olarak, <xref:System.ServiceModel.WSHttpBinding> modu ayarını sınıfı `Transport` ayarlamalısınız anlamına gelir <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.HttpTransportSecurity> sınıfı uygun değeri.  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Aktarım modu için ClientCredentialType özelliğini ayarlamak için  
  
1.  Bağlama örneği oluşturun.  
  
2.  Ayarlama `Mode` özelliğini `Transport`.  
  
3.  Ayarlama `ClientCredential` özelliğini uygun bir değer. Aşağıdaki kod özelliği ayarlar `Windows`.  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>İleti modu ClientCredentialType özelliğini ayarlamak için  
  
1.  Bağlama örneği oluşturun.  
  
2.  Ayarlama `Mode` özelliğini `Message`.  
  
3.  Ayarlama `ClientCredential` özelliğini uygun bir değer. Aşağıdaki kod özelliği ayarlar `Certificate`.  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Yapılandırma modu ve ClientCredentialType özelliği ayarlamak için  
  
1.  Uygun bağlama öğeye ekleme [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyasının öğesi. Aşağıdaki örnek ekler bir [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.  
  
2.  Ekleme bir `<binding>` öğesi ve kümesi kendi `name` özniteliği için uygun bir değer.  
  
3.  Ekleme bir `<security>` öğesi ve kümesi `mode` özniteliğini `Message`, `Transport`, veya `TransportWithMessageCredential`.  
  
4.  Modu ayarlanırsa `Transport`, ekleme bir `<transport>` öğesi ve kümesi `clientCredential` özniteliği için uygun bir değer.  
  
     Aşağıdaki örnekte modu ayarlar "`Transport"`ve ardından ayarlar `clientCredentialType` özniteliği `<transport>` öğesine"`Windows"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" />  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Alternatif olarak, kümesinin `security mode` için "`Message"`ve ardından bir `<"message">` öğesi. Bu örnekte ayarlar `clientCredentialType` için "`Certificate"`.  
  
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
 Güvenlik modunu ayarlama zaman `TransportWithMessageCredential`, aktarım düzeyi güvenlik sağlayan gerçek mekanizması taşıma belirler. Örneğin, HTTP protokolü, HTTP (HTTPS) üzerinden Güvenli Yuva Katmanı (SSL) kullanır. Bu nedenle, ayarı `ClientCredentialType` herhangi bir aktarım güvenliği nesnenin özellik (gibi <xref:System.ServiceModel.HttpTransportSecurity>) göz ardı edilir.  Diğer bir deyişle, yalnızca ayarlayabilirsiniz `ClientCredentialType` ileti güvenlik nesnesi (için `WSHttpBinding` bağlamayı <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> nesne).  
  
 Daha fazla bilgi için [nasıl yapılır: kullanım taşıma Güveniği ve ileti kimlik bilgilerini](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).  
  
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
