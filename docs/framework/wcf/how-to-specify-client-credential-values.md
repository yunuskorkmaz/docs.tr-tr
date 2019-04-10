---
title: 'Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: a1b2627c8e9899a122f27dc652f8c91230fed0b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225137"
---
# <a name="how-to-specify-client-credential-values"></a>Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme
Windows Communication Foundation (WCF) kullanarak, hizmet, bir istemci için hizmet kimliğinin nasıl doğrulandığını belirtebilirsiniz. Örneğin, bir hizmeti bir sertifikayla istemcinin kimliğinin doğrulanmasını koşabilirsiniz.  
  
### <a name="to-determine-the-client-credential-type"></a>İstemci kimlik bilgileri türünü belirlemek için  
  
1.  Hizmet meta veri uç noktasından meta verilerini alın. Meta veriler genellikle iki dosyalardan oluşur: İstemci kodu seçtiğiniz programlama dilinde (varsayılan görsel ise C#) ve bir XML yapılandırma dosyası. Meta veri alma yollarından biri İstemci kodu ve istemci yapılandırması döndürmek için Svcutil.exe aracını kullanmaktır. Daha fazla bilgi için [meta verileri alınırken](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) ve [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
2.  XML yapılandırma dosyasını açın. Svcutil.exe aracını kullanırsanız, varsayılan dosya Output.config adıdır.  
  
3.  Bulma  **\<Güvenlik >** öğeyle **modu** özniteliği (**< güvenlik modu =** `MessageOrTransport` **>** nerede `MessageOrTransport` güvenlik modlardan birine ayarlayın.  
  
4.  Mod değeri ile eşleşen alt öğe bulun. Örneğin moduna ayarlanır, **ileti**, bulma  **\<ileti >** içerdiği öğesi  **\<Güvenlik >** öğesi.  
  
5.  Atanan değer Not **clientCredentialType** özniteliği. Hangi modun kullanıldığına, gerçek değer bağlıdır taşıma veya ileti.  
  
 Aşağıdaki XML kodunu, istemcinin kimliğini doğrulamak ileti güveliği kullanarak ve sertifika gerektiren bir istemci için yapılandırmasını gösterir.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Örnek: İstemci kimlik bilgileri olarak sertifika ile TCP taşıma modu  
 Bu örnek, güvenlik modu aktarım modu için ayarlar ve istemci bir X.509 sertifikası için kimlik bilgisi değeri ayarlar. Aşağıdaki yordamlar, istemci kodu ve yapılandırması istemci kimlik bilgisi değeri ayarlamak nasıl ekleyebileceğiniz gösterilmektedir. Bu, kullandığınızı varsayar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmetinden (kod ve yapılandırma) meta verileri döndürmek için. Daha fazla bilgi için [nasıl yapılır: Bir istemci oluşturmanız](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Kod içinde bulunan istemciye istemci kimlik bilgisi değeri belirtmek için  
  
1.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kod ve Yapılandırma hizmeti oluşturmak için.  
  
2.  Oluşturulan kod kullanarak WCF istemci örneği oluşturun.  
  
3.  İstemci sınıfına <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı uygun değeri. Bu örnek özelliği kullanarak bir X.509 sertifikası ayarlar <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> sınıfı.  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     Numaralandırmalar dilediğinizi kullanabilirsiniz <xref:System.Security.Cryptography.X509Certificates.X509FindType> sınıfı. Konu adı, sertifika (sona erme tarihi nedeniyle) değişir durumda burada kullanılır. Konu adı'nı kullanarak sertifikayı yeniden bulmak için altyapı sağlar.  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>İstemci yapılandırması üzerinde istemci kimlik bilgisi değeri belirtmek için  
  
1.  Ekleme bir [ \<davranışı >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesine [ \<davranışları >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.  
  
2.  Ekleme bir [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesine [ \<davranışları >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi. Gerekli ayarladığınızdan emin olun `name` özniteliği için uygun bir değer.  
  
3.  Ekleme bir [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) öğesine [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi.  
  
4.  Aşağıdaki öznitelikler uygun değerlere ayarlayın: `storeLocation`, `storeName`, `x509FindType`, ve `findValue`aşağıdaki kodda gösterildiği gibi. Sertifikalar hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
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
  
5.  İstemci yapılandırırken ayarlayarak davranışı belirtin `behaviorConfiguration` özniteliği `<endpoint>` öğesi, aşağıdaki kodda gösterildiği gibi. Uç nokta öğesi bir alt öğesidir [ \<istemci >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) öğesi. Ayrıca, ayarlayarak bağlama yapılandırmasının adını belirtin. `bindingConfiguration` istemci için bağlama özniteliği. Bağlama adı, oluşturulan yapılandırma dosyası kullanıyorsanız, otomatik olarak oluşturulur. Bu örnekte, addır `"tcpBindingWithCredential"`.  
  
    ```xml  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [WCF Güvenliğini Programlama](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Kimlik Bilgisi Türü Seçme](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Sertifikalarla Çalışma](../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Nasıl yapılır: İstemci Oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<Güvenlik >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<İleti >](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<davranışı >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<davranışlar >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
