---
title: 'Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 856d33f88b55c35927998b15acc7bbf8ff1e9fe2
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-specify-client-credential-values"></a>Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme
Kullanarak [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], hizmet istemci hizmete kimlik doğrulamasının nasıl belirtebilirsiniz. Örneğin, bir hizmeti bir sertifikayla istemcinin kimliğinin doğrulanmasını koşabilirsiniz.  
  
### <a name="to-determine-the-client-credential-type"></a>İstemci kimlik bilgisi türü belirlemek için  
  
1.  Meta veri hizmetin meta veri uç noktasından alır. Meta verileri genellikle iki dosyadan oluşur: programlama dili (varsayılan olarak Visual C#), istemci kodu ve bir XML yapılandırma dosyası. Meta Veri almanın bir yolu istemci kodu ve istemci yapılandırması geri dönmek için Svcutil.exe aracını kullanmaktır. Daha fazla bilgi için bkz: [meta verileri alma](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) ve [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
2.  XML yapılandırma dosyasını açın. Svcutil.exe aracı kullanırsanız, varsayılan dosya Output.config adıdır.  
  
3.  Bul  **\<Güvenlik >** öğeyle **modu** özniteliği (**< güvenlik modu =** `MessageOrTransport` **>** burada `MessageOrTransport` güvenlik modlarından birine ayarlayın.  
  
4.  Mod değeri ile eşleşen alt öğesi bulunamıyor. Örneğin modu ayarlamak, **ileti**, bulma  **\<ileti >** öğesi içinde yer alan  **\<Güvenlik >** öğesi.  
  
5.  Atanan değer Not **clientCredentialType** özniteliği. Hangi modun kullanılacağı üzerinde gerçek değer bağlıdır taşıma veya ileti.  
  
 Aşağıdaki XML kodunu istemci kimlik doğrulaması ileti güvenliği kullanan ve bir sertifika gerektiren bir istemci için yapılandırmasını gösterir.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Örnek: TCP taşıma modu istemci kimlik bilgileri olarak sertifikayla  
 Bu örnek güvenlik modunu aktarım modu için ayarlar ve istemci bir X.509 sertifikası kimlik bilgisi değeri ayarlar. Aşağıdaki yordamlar, istemci kodu ve yapılandırma içinde bulunan istemciye kimlik bilgisi değeri ayarlamak nasıl ekleyebileceğiniz gösterilmektedir. Bu, kullandığınız varsayar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta veriler (kod ve yapılandırma) hizmetinden dönün. Daha fazla bilgi için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Kod içinde bulunan istemciye istemci kimlik bilgisi değeri belirtmek için  
  
1.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kod ve Yapılandırma hizmeti oluşturmak için.  
  
2.  Bir örneğini oluşturmak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci kullanılarak oluşturulan kod.  
  
3.  Set istemci sınıfı üzerinde <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> uygun bir değere sınıfı. Bu örnek, bir X.509 sertifikası kullanarak özelliği ayarlar <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> sınıfı.  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     Numaralandırmalar birini kullanabilirsiniz <xref:System.Security.Cryptography.X509Certificates.X509FindType> sınıfı. Konu adı, sertifika (sona erme tarihi nedeniyle) değiştiği durumda burada kullanılır. Konu adı kullanarak sertifikayı yeniden bulmak için altyapı sağlar.  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Yapılandırma içinde bulunan istemciye istemci kimlik bilgisi değeri belirtmek için  
  
1.  Ekleme bir [ \<davranışı >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesine [ \<davranışları >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.  
  
2.  Ekleme bir [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesine [ \<davranışları >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi. Gerekli ayarladığınızdan emin olun `name` öznitelik için uygun bir değer.  
  
3.  Ekleme bir [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) öğesine [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi.  
  
4.  Aşağıdaki öznitelikler uygun değerlere ayarlayın: `storeLocation`, `storeName`, `x509FindType`, ve `findValue`aşağıdaki kodda gösterildiği gibi. Sertifikalar hakkında daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
          <behavior name="endpointCredentialBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="Contoso.com"   
                                 storeLocation="LocalMachine"  
                                 storeName="TrustedPeople"  
                                 x509FindType="FindBySubjectName" />  
            </clientCredentials>  
          </behavior>  
       </endpointBehaviors>  
    </behaviors>  
    ```  
  
5.  İstemci yapılandırırken ayarlayarak davranışı belirtin `behaviorConfiguration` özniteliği `<endpoint>` aşağıdaki kodda gösterildiği gibi öğesi. Uç nokta öğesi bir alt öğesi değil [ \<istemci >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) öğesi. Ayrıca, ayarlayarak bağlama yapılandırması adını belirtin `bindingConfiguration` istemci için bağlama özniteliği. Oluşturulan yapılandırma dosyası kullanıyorsanız, bağlamanın adı otomatik olarak oluşturulur. Bu örnekte, addır `"tcpBindingWithCredential"`.  
  
    ```xml  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [WCF Güvenliğini Programlama](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [Kimlik Bilgisi Türü Seçme](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Sertifikalarla Çalışma](../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Nasıl yapılır: İstemci Oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [\<netTcpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)  
 [\<Güvenlik >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
 [\<İleti >](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)  
 [\<davranışı >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)  
 [\<davranışları >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)  
 [\<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
