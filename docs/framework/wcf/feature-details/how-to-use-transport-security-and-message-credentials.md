---
title: "Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 70575732e7840d243373fd1512f788c776f17ceb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma
Taşıma ve ileti kimlik bilgileri olan bir hizmeti güvenli hale getirme kullanan taşıma ve ileti güvenlik modlarında iyi [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. İleti Katmanı Güvenliği katı taşıma güvenlik mekanizmaları ile mümkün olmayan kimlik bilgilerini, çeşitli sağlarken, toplamda bütünlüğü ve gizliliği, Aktarım Katmanı Güvenliği sağlar. Bu konuda, ileti kimlik bilgilerini kullanarak aktarım uygulamak için temel adımlar açıklanmıştır <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding> bağlar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz: güvenlik modunu ayarlama, [nasıl yapılır: güvenlik modunu ayarlama](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
 Güvenlik modu ayarlarken `TransportWithMessageCredential`, aktarım düzeyinde güvenlik sağlayan gerçek mekanizması taşıma belirler. HTTP için Güvenli Yuva Katmanı (SSL) HTTP (HTTPS) üzerinden mekanizmasıdır; TCP için bu SSL TCP veya Windows üzerinde değil.  
  
 Taşıma HTTP ise (kullanarak <xref:System.ServiceModel.WSHttpBinding>), HTTP üzerinden SSL, aktarım düzeyinde güvenlik sağlar. Bu durumda, bu konunun ilerleyen bölümlerinde gösterildiği gibi bir bağlantı noktasına bağlı bir SSL sertifikası ile hizmetini barındıran bilgisayarın yapılandırmanız gerekir.  
  
 Taşıma TCP ise (kullanarak <xref:System.ServiceModel.NetTcpBinding>), tarafından sağlanan aktarım düzeyinde güvenlik Windows güvenliği ya da SSL TCP üzerinden varsayılandır. TCP üzerinden SSL kullanırken, sertifikayı kullanarak belirtmelisiniz <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> bu konunun ilerleyen bölümlerinde gösterildiği gibi yöntemi.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>WSHttpBinding aktarım güvenliğinde (kod) için bir sertifika ile kullanmak için  
  
1.  Makine üzerindeki bir bağlantı noktası bir SSL sertifikası bağlamak için HttpCfg.exe aracını kullanın. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2.  Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding> sınıfı ve ayarlayın <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliğine <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
3.  Ayarlama <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> uygun bir değere özelliği. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Bir kimlik bilgisi türü seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri.  
  
4.  Bir örneğini oluşturmak <xref:System.Uri> uygun taban adresi olan sınıf. Adres "HTTPS" şeması kullanması gerekir ve makine ve SSL sertifikasını bağlı bağlantı noktası numarasını gerçek adını içermelidir unutmayın. (Alternatif olarak, taban adresi yapılandırmasında ayarlayabilirsiniz.)  
  
5.  Kullanarak bir hizmet uç noktası ekleme <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.  
  
6.  Örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> ve arama <xref:System.ServiceModel.ICommunicationObject.Open%2A> aşağıdaki kodda gösterildiği gibi yöntemi.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>NetTcpBinding aktarım güvenliğinde (kod) için bir sertifika ile kullanmak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.NetTcpBinding> sınıfı ve ayarlayın <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğine <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Ayarlama <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun bir değere. Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri.  
  
3.  Bir örneğini oluşturmak <xref:System.Uri> uygun taban adresi olan sınıf. Adres "net.tcp" düzeni kullanması gerektiğini unutmayın. (Alternatif olarak, taban adresi yapılandırmasında ayarlayabilirsiniz.)  
  
4.  Örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> sınıfı.  
  
5.  Kullanım <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> hizmeti X.509 sertifikası açıkça ayarlamak için sınıf.  
  
6.  Kullanarak bir hizmet uç noktası ekleme <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.  
  
7.  Çağrı <xref:System.ServiceModel.ICommunicationObject.Open%2A> aşağıdaki kodda gösterildiği gibi yöntemi.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>NetTcpBinding (kodda) taşıma güvenliği Windows ile birlikte kullanılmak üzere  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.NetTcpBinding> sınıfı ve ayarlayın <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğine <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Windows ayarlayarak kullanılacak Aktarım güvenlik <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> için <xref:System.ServiceModel.TcpClientCredentialType.Windows>. (Bu varsayılan olduğunu unutmayın.)  
  
3.  Ayarlama <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun bir değere. Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri.  
  
4.  Bir örneğini oluşturmak <xref:System.Uri> uygun taban adresi olan sınıf. Adres "net.tcp" düzeni kullanması gerektiğini unutmayın. (Alternatif olarak, taban adresi yapılandırmasında ayarlayabilirsiniz.)  
  
5.  Örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> sınıfı.  
  
6.  Kullanım <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> hizmeti X.509 sertifikası açıkça ayarlamak için sınıf.  
  
7.  Kullanarak bir hizmet uç noktası ekleme <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.  
  
8.  Çağrı <xref:System.ServiceModel.ICommunicationObject.Open%2A> aşağıdaki kodda gösterildiği gibi yöntemi.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Yapılandırma kullanma  
  
#### <a name="to-use-the-wshttpbinding"></a>WSHttpBinding kullanmak için  
  
1.  Bilgisayarı bir bağlantı noktasına bağlı bir SSL sertifikası ile yapılandırın. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)). Ayarlanacak gerekmez bir <`transport`> öğesinin değeri bu yapılandırmaya sahip.  
  
2.  İleti düzeyi güvenlik için istemci kimlik bilgisi türünü belirtin. Aşağıdaki örnek kümeleri `clientCredentialType` özniteliği <`message`> öğesine `UserName`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>NetTcpBinding taşıma güvenliği için bir sertifika ile kullanmak için  
  
1.  TCP üzerinden SSL için sertifikayı açıkça belirtmelisiniz `<behaviors>` öğesi. Aşağıdaki örnek, bir sertifika, veren tarafından varsayılan depolama konumunda (yerel makine ve kişisel depoları) belirtir.  
  
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
  
2.  Ekleme bir [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) bağlamaları bölümüne  
  
3.  Bir bağlama öğesi ekleyin ve ayarlayın `name` öznitelik için uygun bir değer.  
  
4.  Ekleme bir <`security`> öğesi ve kümesi `mode` özniteliğini `TransportWithMessageCredential`.  
  
5.  Ekleme bir <`message>` öğesi ve kümesi `clientCredentialType` öznitelik için uygun bir değer.  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>NetTcpBinding taşıma güvenliği için Windows ile birlikte kullanmak için  
  
1.  Ekleme bir [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) bağlamaları bölümüne  
  
2.  Ekleme bir <`binding`> öğesi ve kümesi `name` öznitelik için uygun bir değer.  
  
3.  Ekleme bir <`security`> öğesi ve kümesi `mode` özniteliğini `TransportWithMessageCredential`.  
  
4.  Ekleme bir <`transport`> öğesi ve kümesi `clientCredentialType` özniteliğini `Windows`.  
  
5.  Ekleme bir <`message`> öğesi ve kümesi `clientCredentialType` öznitelik için uygun bir değer. Aşağıdaki kod, bir sertifika için değeri ayarlar.  
  
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
