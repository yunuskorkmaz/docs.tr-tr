---
title: 'Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme'
description: Bir WCF hizmetinin istemcinin bu hizmette nasıl kimlik doğrulaması yapıldığını nasıl belirtmesini istediğinizi öğrenin. Bu örnek bir X. 509.440 sertifikası ve aktarım modunu belirtir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 75a21a7dc083282f6b2fe839167ff1b2eddfb373
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244458"
---
# <a name="how-to-specify-client-credential-values"></a>Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme

Hizmet, Windows Communication Foundation (WCF) kullanarak, bir istemcinin hizmette nasıl kimlik doğrulaması yapıldığını belirtebilir. Örneğin, bir hizmet, istemcinin kimliğinin bir sertifikayla doğrulanmasını sağlayabilir.

## <a name="to-determine-the-client-credential-type"></a>İstemci kimlik bilgisi türünü belirleme

1. Hizmetin meta veri uç noktasından meta verileri alın. Meta veriler genellikle iki dosyadan oluşur: seçtiğiniz programlama dilinde istemci kodu (varsayılan olarak Visual C#) ve bir XML yapılandırma dosyası. Meta verileri almanın bir yolu, istemci kodunu ve istemci yapılandırmasını döndürmek için Svcutil.exe aracını kullanmaktır. Daha fazla bilgi için bkz. [meta verileri](./feature-details/retrieving-metadata.md) ve [ServiceModel meta verilerini alma yardımcı programı Aracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).

2. XML yapılandırma dosyasını açın. Svcutil.exe aracını kullanırsanız, dosyanın varsayılan adı Output.config.

3. **\<security>** **Mode** özniteliğine sahip öğeyi bulun ( **\<security mode =**`MessageOrTransport`**>** burada `MessageOrTransport` güvenlik modlarından birine ayarlanır).

4. Mode değeriyle eşleşen alt öğe bulun. Örneğin, mod **ileti**olarak ayarlandıysa, **\<message>** öğesinde içerilen öğeyi bulun **\<security>** .

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

Bu örnek, güvenlik modunu taşıma moduna ayarlar ve istemci kimlik bilgisi değerini bir X. 509.952 sertifikası olarak ayarlar. Aşağıdaki yordamlarda, istemcide istemci kimlik bilgileri değerinin kod ve yapılandırmada nasıl ayarlanacağı gösterilmektedir. Bu, hizmetten meta verileri (kod ve yapılandırma) döndürmek için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullandığınızı varsayar. Daha fazla bilgi için bkz. [nasıl yapılır: Istemci oluşturma](how-to-create-a-wcf-client.md).

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>İstemcide istemci kimlik bilgileri değerini belirtmek için

1. Hizmetten kod ve yapılandırma oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.

2. Oluşturulan kodu kullanarak WCF istemcisinin bir örneğini oluşturun.

3. İstemci sınıfında, <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> sınıfının özelliğini uygun bir değer olarak ayarlayın. Bu örnek, sınıfının yöntemini kullanarak özelliği bir X. 509.440 sertifikası olarak ayarlar <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> .

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     Sınıfın Numaralandırmalardan herhangi birini kullanabilirsiniz <xref:System.Security.Cryptography.X509Certificates.X509FindType> . Konu adı, sertifikanın değişmesi durumunda (bir sona erme tarihi nedeniyle) burada kullanılır. Konu adının kullanılması, altyapının sertifikayı tekrar bulmasını sağlar.

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Yapılandırmada istemci kimlik bilgileri değerini belirtmek için

1. Öğeye bir [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğe ekleyin [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) .

2. Öğeye bir [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) öğe ekleyin [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) . Gerekli `name` özniteliği uygun bir değere ayarladığınızdan emin olun.

3. Öğeye bir [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) öğe ekleyin [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) .

4. Aşağıdaki öznitelikleri uygun değerlere ayarlayın:,, `storeLocation` `storeName` `x509FindType` , ve `findValue` , aşağıdaki kodda gösterildiği gibi. Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](./feature-details/working-with-certificates.md).

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

5. İstemcisini yapılandırırken, `behaviorConfiguration` `<endpoint>` aşağıdaki kodda gösterildiği gibi, öğesinin özniteliğini ayarlayarak davranışı belirtin. Endpoint öğesi öğesinin bir alt öğesidir [\<client>](../configure-apps/file-schema/wcf/client.md) . Ayrıca, `bindingConfiguration` özniteliğini istemci için bağlamaya ayarlayarak bağlama yapılandırmasının adını belirtin. Oluşturulmuş bir yapılandırma dosyası kullanıyorsanız, bağlamanın adı otomatik olarak oluşturulur. Bu örnekte, adı ' dir `"tcpBindingWithCredential"` .

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
- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Sertifikalarla Çalışma](./feature-details/working-with-certificates.md)
- [Nasıl yapılır: İstemci Oluşturma](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)
