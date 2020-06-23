---
title: 'Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma'
description: WCF 'de aktarım ve Ileti güvenlik modlarını en iyi şekilde sunan ileti kimlik bilgileriyle aktarım güvenliğini nasıl uygulayacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f632a4389eafc155cedcae94707c9418b6696f2c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246655"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma
Hem aktarım hem de ileti kimlik bilgileriyle bir hizmetin güvenliğini sağlamak, Windows Communication Foundation (WCF) içinde hem aktarım hem de Ileti güvenliği modlarından en iyi şekilde yararlanır. Sum olarak, aktarım katmanı güvenliği bütünlük ve gizlilik sağlar, ancak ileti katmanı güvenliği, katı taşıma güvenlik mekanizmalarıyla mümkün olmayan çeşitli kimlik bilgileri sağlar. Bu konuda, ve bağlamaları kullanılarak ileti kimlik bilgileriyle taşıma uygulamak için temel adımlar <xref:System.ServiceModel.WSHttpBinding> gösterilmektedir <xref:System.ServiceModel.NetTcpBinding> . Güvenlik modunu ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenlik modunu ayarlama](../how-to-set-the-security-mode.md).  
  
 Güvenlik modu olarak ayarlandığında `TransportWithMessageCredential` , taşıma, aktarım düzeyi güvenliği sağlayan gerçek mekanizmayı belirler. HTTP için mekanizma, HTTP (HTTPS) üzerinden Güvenli Yuva Katmanı (SSL); TCP, TCP veya Windows üzerinde SSL 'dir.  
  
 Aktarım HTTP ise (kullanılarak <xref:System.ServiceModel.WSHttpBinding> ), http üzerinden SSL, aktarım düzeyi güvenliği sağlar. Bu durumda, hizmeti barındıran bilgisayarı, bu konunun ilerleyen kısımlarında gösterildiği gibi, bir bağlantı noktasına bağlanan bir SSL sertifikası ile yapılandırmanız gerekir.  
  
 Aktarım TCP ise (kullanılarak <xref:System.ServiceModel.NetTcpBinding> ), varsayılan olarak, belirtilen aktarım düzeyi güvenliği Windows güvenliği veya TCP ÜZERINDEN SSL olur. TCP üzerinden SSL kullanırken, <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> Bu konunun ilerleyen kısımlarında gösterildiği gibi, yöntemini kullanarak sertifikayı belirtmeniz gerekir.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>Taşıma güvenliği için bir sertifikayla WSHttpBinding 'i kullanmak için (kodda)  
  
1. Bir SSL sertifikasını makinedeki bir bağlantı noktasına bağlamak için HttpCfg.exe aracını kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2. Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliğini olarak ayarlayın <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .  
  
3. <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>Özelliği uygun bir değere ayarlayın. (Daha fazla bilgi için bkz. [kimlik bilgisi türü seçme](selecting-a-credential-type.md).) Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri kullanır.  
  
4. <xref:System.Uri>Uygun bir temel adresle sınıfının bir örneğini oluşturun. Adresin "HTTPS" düzenini kullanması gerektiğini ve makinenin gerçek adını ve SSL sertifikasının bağlandığı bağlantı noktası numarasını içermesi gerektiğini unutmayın. (Alternatif olarak, yapılandırmada temel adresi ayarlayabilirsiniz.)  
  
5. Yöntemini kullanarak bir hizmet uç noktası ekleyin <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .  
  
6. Örneğini oluşturun <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.ICommunicationObject.Open%2A> aşağıdaki kodda gösterildiği gibi yöntemini çağırın.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>Bir aktarım güvenliği için bir sertifikayla NetTcpBinding kullanmak için (kodda)  
  
1. Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğini olarak ayarlayın <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .  
  
2. Öğesini <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun bir değere ayarlayın. Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri kullanır.  
  
3. <xref:System.Uri>Uygun bir temel adresle sınıfının bir örneğini oluşturun. Adresin "net. TCP" düzenini kullanması gerektiğini unutmayın. (Alternatif olarak, yapılandırmada temel adresi ayarlayabilirsiniz.)  
  
4. Sınıfının örneğini oluşturun <xref:System.ServiceModel.ServiceHost> .  
  
5. <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> Hizmetin X. 509.440 sertifikasını açıkça ayarlamak için sınıfının yöntemini kullanın.  
  
6. Yöntemini kullanarak bir hizmet uç noktası ekleyin <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .  
  
7. <xref:System.ServiceModel.ICommunicationObject.Open%2A>Aşağıdaki kodda gösterildiği gibi yöntemini çağırın.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>Aktarım güvenliği için Windows ile NetTcpBinding 'i kullanmak için (kodda)  
  
1. Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğini olarak ayarlayın <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .  
  
2. ' İ ' ye ayarlayarak aktarım güvenliğini Windows kullanacak şekilde <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> ayarlayın <xref:System.ServiceModel.TcpClientCredentialType.Windows> . (Bunun varsayılan değer olduğunu unutmayın.)  
  
3. Öğesini <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun bir değere ayarlayın. Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri kullanır.  
  
4. <xref:System.Uri>Uygun bir temel adresle sınıfının bir örneğini oluşturun. Adresin "net. TCP" düzenini kullanması gerektiğini unutmayın. (Alternatif olarak, yapılandırmada temel adresi ayarlayabilirsiniz.)  
  
5. Sınıfının örneğini oluşturun <xref:System.ServiceModel.ServiceHost> .  
  
6. <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> Hizmetin X. 509.440 sertifikasını açıkça ayarlamak için sınıfının yöntemini kullanın.  
  
7. Yöntemini kullanarak bir hizmet uç noktası ekleyin <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .  
  
8. <xref:System.ServiceModel.ICommunicationObject.Open%2A>Aşağıdaki kodda gösterildiği gibi yöntemini çağırın.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Yapılandırma kullanma  
  
#### <a name="to-use-the-wshttpbinding"></a>WSHttpBinding 'i kullanmak için  
  
1. Bilgisayarı bir bağlantı noktasına bağlaan SSL sertifikası ile yapılandırın. (Daha fazla bilgi için bkz. [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md)). `transport`Bu yapılandırmayla bir <> öğesi değeri ayarlamanız gerekmez.  
  
2. İleti düzeyi güvenlik için istemci kimlik bilgisi türünü belirtin. Aşağıdaki örnek, `clientCredentialType` <`message`> öğesinin özniteliğini olarak ayarlar `UserName` .  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>Aktarım güvenliği için bir sertifikayla NetTcpBinding kullanmak için  
  
1. TCP üzerinden SSL için, sertifikayı öğesinde açıkça belirtmeniz gerekir `<behaviors>` . Aşağıdaki örnek, varsayılan depo konumundaki (yerel makine ve kişisel Mağazalar) veren tarafından bir sertifikayı belirtir.  
  
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
  
2. [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)Bağlamalar bölümüne bir ekleyin  
  
3. Bir Binding öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.  
  
4. Bir <`security`> öğesi ekleyin ve `mode` özniteliğini olarak ayarlayın `TransportWithMessageCredential` .  
  
5. <bir `message>` öğesi ekleyin ve `clientCredentialType` özniteliği uygun bir değere ayarlayın.  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>Aktarım güvenliği için Windows ile NetTcpBinding 'i kullanmak için  
  
1. [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)Bağlamalar bölümüne bir ekleyin,  
  
2. Bir <`binding`> öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.  
  
3. Bir <`security`> öğesi ekleyin ve `mode` özniteliğini olarak ayarlayın `TransportWithMessageCredential` .  
  
4. Bir <`transport`> öğesi ekleyin ve `clientCredentialType` özniteliğini olarak ayarlayın `Windows` .  
  
5. Bir <`message`> öğesi ekleyin ve `clientCredentialType` özniteliği uygun bir değere ayarlayın. Aşağıdaki kod, değeri bir sertifika olarak ayarlar.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Güvenlik Modunu Ayarlama](../how-to-set-the-security-mode.md)
- [Hizmetleri Güvenli Hale Getirme](../securing-services.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](securing-services-and-clients.md)
