---
title: 'Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 2417c2dd16224d6cbf00d3f1f4a8958420830b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319856"
---
# <a name="how-to-specify-client-credential-values"></a>Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme

Hizmet, Windows Communication Foundation (WCF) kullanarak, bir istemcinin hizmette nasıl kimlik doğrulaması yapıldığını belirtebilir. Örneğin, bir hizmet, istemcinin kimliğinin bir sertifikayla doğrulanmasını sağlayabilir.

## <a name="to-determine-the-client-credential-type"></a>İstemci kimlik bilgisi türünü belirleme

1. Hizmetin meta veri uç noktasından meta verileri alın. Meta veriler genellikle iki dosyadan oluşur: seçtiğiniz programlama dilinde istemci kodu (varsayılan olarak görseldir C#) ve bir XML yapılandırma dosyası. Meta verileri almanın bir yolu, istemci kodunu ve istemci yapılandırmasını döndürmek için Svcutil. exe aracını kullanmaktır. Daha fazla bilgi için bkz. [meta verileri](./feature-details/retrieving-metadata.md) ve [ServiceModel meta verilerini alma yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).

2. XML yapılandırma dosyasını açın. Svcutil. exe aracını kullanırsanız, dosyanın varsayılan adı output. config olur.

3. **Mode** özniteliği ( **\<güvenlik modu =** `MessageOrTransport` **>** ) olan **\<security >** öğesini bulur (`MessageOrTransport` ' in güvenlik modlarından birine ayarlandığı).

4. Mode değeriyle eşleşen alt öğe bulun. Örneğin, mod **ileti**olarak ayarlandıysa, **\<güvenlik >** öğesinde içerilen **\<message >** öğesini bulun.

5. **ClientCredentialType** özniteliğine atanan değere göz atar. Gerçek değer, hangi modun kullanıldığı, taşımanın veya iletinin kullanıldığına bağlıdır.

Aşağıdaki XML kodu, ileti güvenliği kullanan bir istemcinin yapılandırmasını gösterir ve istemcinin kimliğini doğrulamak için bir sertifika gerektirir.

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Örnek: Istemci kimlik bilgileri olarak sertifika ile TCP aktarım modu

Bu örnek, güvenlik modunu taşıma moduna ayarlar ve istemci kimlik bilgisi değerini bir X. 509.952 sertifikası olarak ayarlar. Aşağıdaki yordamlarda, istemcide istemci kimlik bilgileri değerinin kod ve yapılandırmada nasıl ayarlanacağı gösterilmektedir. Bu, hizmetten meta verileri (kod ve yapılandırma) döndürmek için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullandığınızı varsayar. Daha fazla bilgi için bkz. [nasıl yapılır: Istemci oluşturma](how-to-create-a-wcf-client.md).

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>İstemcide istemci kimlik bilgileri değerini belirtmek için

1. Hizmetten kod ve yapılandırma oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.

2. Oluşturulan kodu kullanarak WCF istemcisinin bir örneğini oluşturun.

3. İstemci sınıfında, <xref:System.ServiceModel.ClientBase%601> sınıfının <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliğini uygun bir değere ayarlayın. Bu örnek, <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> sınıfının <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemini kullanarak özelliği bir X. 509.440 sertifikası olarak ayarlar.

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     @No__t-0 sınıfının Numaralandırmalardan herhangi birini kullanabilirsiniz. Konu adı, sertifikanın değişmesi durumunda (bir sona erme tarihi nedeniyle) burada kullanılır. Konu adının kullanılması, altyapının sertifikayı tekrar bulmasını sağlar.

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Yapılandırmada istemci kimlik bilgileri değerini belirtmek için

1. [@No__t-3behavior >](../configure-apps/file-schema/wcf/behaviors.md) öğesine [\<behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ekleyin.

2. [@No__t-3davranışlarına >](../configure-apps/file-schema/wcf/behaviors.md) öğesine [\<clientcredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) öğesi ekleyin. Gerekli `name` özniteliğini uygun bir değere ayarladığınızdan emin olun.

3. [@No__t-3clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) öğesine [\<clientcertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) öğesi ekleyin.

4. Aşağıdaki öznitelikleri uygun değerlere ayarlayın: `storeLocation`, `storeName`, `x509FindType` ve `findValue`, aşağıdaki kodda gösterildiği gibi. Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](./feature-details/working-with-certificates.md).

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

5. İstemcisini yapılandırırken, aşağıdaki kodda gösterildiği gibi `<endpoint>` öğesinin `behaviorConfiguration` özniteliğini ayarlayarak davranışı belirtin. Endpoint öğesi [\<client >](../configure-apps/file-schema/wcf/client.md) öğesinin bir alt öğesidir. Ayrıca, `bindingConfiguration` özniteliğini istemci için bağlamaya ayarlayarak bağlama yapılandırmasının adını belirtin. Oluşturulmuş bir yapılandırma dosyası kullanıyorsanız, bağlamanın adı otomatik olarak oluşturulur. Bu örnekte ad `"tcpBindingWithCredential"` ' dır.

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
- [WCF Güvenliğini Programlama](./feature-details/programming-wcf-security.md)
- [Kimlik Bilgisi Türü Seçme](./feature-details/selecting-a-credential-type.md)
- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Sertifikalarla Çalışma](./feature-details/working-with-certificates.md)
- [Nasıl yapılır: İstemci Oluşturma](how-to-create-a-wcf-client.md)
- [\<netTcpBinding >](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<Güvenlik >](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<ileti >](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<davranış >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<davranışlar >](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md)
