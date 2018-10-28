---
title: 'Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f678c4713bff342cb3e788a85d7e58fc6e47820c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187614"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma
Hem aktarım hem de ileti kimlik bilgileri ile bir hizmeti güvenli hale getirme en iyi şekilde hem aktarım hem de ileti güvenlik modu Windows Communication Foundation (WCF) kullanır. İleti düzeyi güvenlik katı taşıma güvenlik mekanizmaları ile mümkün olmayan kimlik bilgilerini çeşitli sağlarken, toplamda bütünlüğü ve gizliliği, Aktarım Katmanı Güvenliği sağlar. Bu konu, ileti kimlik bilgilerini kullanarak aktarım uygulamak için temel adımları gösterir. <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding> bağlar. Güvenlik modunu ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenlik modunu ayarlama](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
 Güvenlik modunu ayarlama zaman `TransportWithMessageCredential`, aktarım düzeyi güvenlik sağlayan gerçek mekanizması taşıma belirler. HTTP için Güvenli Yuva Katmanı (SSL) HTTP (HTTPS) üzerinden mekanizmadır; TCP için SSL TCP veya Windows üzerinde değil.  
  
 HTTP taşıma ise (kullanarak <xref:System.ServiceModel.WSHttpBinding>), HTTP üzerinden SSL aktarım düzeyi güvenlik sağlar. Bu durumda, bu konunun ilerleyen bölümlerinde gösterilen şekilde bir bağlantı noktasına bağlı bir SSL sertifikasıyla hizmetini barındıran bilgisayarın yapılandırmanız gerekir.  
  
 TCP aktarımı ise (kullanarak <xref:System.ServiceModel.NetTcpBinding>), varsayılan olarak sağlanan aktarım düzeyi güvenlik Windows Güvenlik ya da SSL TCP üzerinden olduğu. TCP üzerinden SSL kullanılırken, sertifika kullanarak belirtilmelisiniz <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi, bu konunun ilerleyen bölümlerinde gösterilen şekilde.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>WSHttpBinding, aktarım güvenliği (kodda) için bir sertifika ile kullanmak için  
  
1.  Makine üzerindeki bir bağlantı noktası bir SSL sertifikası bağlamak için HttpCfg.exe aracını kullanın. Daha fazla bilgi için [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2.  Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding> ayarlayın ve sınıf <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliğini <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
3.  Ayarlama <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> özelliğini uygun bir değer. (Daha fazla bilgi için [kimlik bilgisi türü seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri.  
  
4.  Bir örneğini oluşturmak <xref:System.Uri> sınıfı uygun bir temel adresine sahip. Not adresi "HTTPS" şeması kullanması gerekir ve makine ve SSL sertifikasını bağlı bağlantı noktası numarasını gerçek adını içermelidir. (Alternatif olarak, temel adres yapılandırmasında ayarlayabilirsiniz.)  
  
5.  Kullanarak bir hizmet uç noktası ekleme <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.  
  
6.  Örneği oluşturmak <xref:System.ServiceModel.ServiceHost> ve çağrı <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi, aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>NetTcpBinding, (kod) aktarım güvenliği bir sertifika ile kullanmak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.NetTcpBinding> ayarlayın ve sınıf <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğini <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Ayarlama <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun değeri. Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri.  
  
3.  Bir örneğini oluşturmak <xref:System.Uri> sınıfı uygun bir temel adresine sahip. "Net.tcp" düzeni adresini kullanması gerektiğini unutmayın. (Alternatif olarak, temel adres yapılandırmasında ayarlayabilirsiniz.)  
  
4.  Örneği oluşturmak <xref:System.ServiceModel.ServiceHost> sınıfı.  
  
5.  Kullanım <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> hizmeti için X.509 sertifikası açıkça ayarlamak için sınıf.  
  
6.  Kullanarak bir hizmet uç noktası ekleme <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.  
  
7.  Çağrı <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi, aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>NetTcpBinding Windows ile Aktarım güvenliği (kodda) kullanmak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.NetTcpBinding> ayarlayın ve sınıf <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğini <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Windows ayarlayarak kullanılacak aktarım güvenliği <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> için <xref:System.ServiceModel.TcpClientCredentialType.Windows>. (Bu varsayılan olduğunu unutmayın.)  
  
3.  Ayarlama <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun değeri. Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri.  
  
4.  Bir örneğini oluşturmak <xref:System.Uri> sınıfı uygun bir temel adresine sahip. "Net.tcp" düzeni adresini kullanması gerektiğini unutmayın. (Alternatif olarak, temel adres yapılandırmasında ayarlayabilirsiniz.)  
  
5.  Örneği oluşturmak <xref:System.ServiceModel.ServiceHost> sınıfı.  
  
6.  Kullanım <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> hizmeti için X.509 sertifikası açıkça ayarlamak için sınıf.  
  
7.  Kullanarak bir hizmet uç noktası ekleme <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.  
  
8.  Çağrı <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi, aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Yapılandırma kullanma  
  
#### <a name="to-use-the-wshttpbinding"></a>WSHttpBinding kullanmak için  
  
1.  Bilgisayar bağlantı noktasına bağlı bir SSL sertifikasıyla yapılandırın. (Daha fazla bilgi için [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)). Ayarlanacak gerekmez bir <`transport`> Bu yapılandırmaya sahip öğe değeri.  
  
2.  İleti düzeyi güvenliği için istemci kimlik bilgisi türü belirtin. Aşağıdaki örnek kümeleri `clientCredentialType` özniteliği <`message`> öğesine `UserName`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>NetTcpBinding aktarım güvenliği için bir sertifika ile kullanmak için  
  
1.  TCP üzerinden SSL için sertifikayı açıkça belirtmelisiniz `<behaviors>` öğesi. Aşağıdaki örnek, varsayılan depolama konumu (yerel makine ve kişisel depolar) sertifikayı veren tarafından sertifikayı belirtir.  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  Ekleme bir [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) bağlamalar bölümü için  
  
3.  Bir bağlama öğesi ekleyin ve ayarlayın `name` özniteliği için uygun bir değer.  
  
4.  Ekleme bir <`security`> öğesi ve kümesi `mode` özniteliğini `TransportWithMessageCredential`.  
  
5.  Ekleme bir <`message>` öğesi ve kümesi `clientCredentialType` özniteliği için uygun bir değer.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>NetTcpBinding Windows ile Aktarım güvenliği için kullanılacak  
  
1.  Ekleme bir [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) bağlamalar bölümü için  
  
2.  Ekleme bir <`binding`> öğesi ve kümesi `name` özniteliği için uygun bir değer.  
  
3.  Ekleme bir <`security`> öğesi ve kümesi `mode` özniteliğini `TransportWithMessageCredential`.  
  
4.  Ekleme bir <`transport`> öğesi ve kümesi `clientCredentialType` özniteliğini `Windows`.  
  
5.  Ekleme bir <`message`> öğesi ve kümesi `clientCredentialType` özniteliği için uygun bir değer. Aşağıdaki kod, bir sertifika için değeri ayarlar.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Güvenlik Modunu Ayarlama](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [Hizmetleri Güvenli Hale Getirme](../../../../docs/framework/wcf/securing-services.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
