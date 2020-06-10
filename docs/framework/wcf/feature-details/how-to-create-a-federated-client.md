---
title: 'Nasıl yapılır: Federe İstemci Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
ms.openlocfilehash: 47e59452edfff74daf17d94a058ce8b12af7867c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593548"
---
# <a name="how-to-create-a-federated-client"></a>Nasıl yapılır: Federe İstemci Oluşturma
Windows Communication Foundation (WCF) ' de, *Federasyon Hizmeti* için bir istemci oluşturmak üç ana adımdan oluşur:  
  
1. [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)Veya benzer bir özel bağlama yapılandırın. Uygun bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md). Alternatif olarak, Federasyon Hizmeti ve bir veya daha fazla güvenlik belirteci hizmeti ile iletişim kurmak için bir yapılandırma dosyası oluşturmak üzere, Federasyon Hizmeti 'nin meta veri uç noktasına karşı [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) çalıştırın.  
  
2. Bir <xref:System.ServiceModel.Security.IssuedTokenClientCredential> güvenlik belirteci hizmeti ile istemci etkileşiminin çeşitli yönlerini denetleyen öğesinin özelliklerini ayarlayın.  
  
3. İçin gerekli olan sertifikaların, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> güvenlik belirteci Hizmetleri gibi belirli uç noktalarla güvenli bir şekilde iletişim kurmasına olanak sağlayan öğesinin özelliklerini ayarlayın.  
  
> [!NOTE]
> <xref:System.Security.Cryptography.CryptographicException>İstemci kimliğe bürünülmüş kimlik bilgileri, <xref:System.ServiceModel.WSFederationHttpBinding> bağlama veya özel olarak verilen bir belirteç ve asimetrik anahtarlar kullandığında bu durum oluşabilir. Asimetrik anahtarlar, <xref:System.ServiceModel.WSFederationHttpBinding> <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> ve <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> özellikleri sırasıyla olarak ayarlandığında bağlama ve özel verilen belirteçlerle kullanılır <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey> . <xref:System.Security.Cryptography.CryptographicException>İstemci bir ileti göndermek istediğinde oluşturulur ve istemcinin kimliğine bürünerek kimliği için bir kullanıcı profili mevcut değildir. Bu sorunu azaltmak için, iletiyi göndermeden önce istemci bilgisayarda oturum açın veya çağrı yapın `LoadUserProfile` .  
  
 Bu konu, bu yordamlar hakkında ayrıntılı bilgi sağlar. Uygun bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md). Federe bir hizmetin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Federasyon](federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Federasyon Hizmeti için yapılandırma oluşturmak ve incelemek için  
  
1. Bir komut satırı parametresi olarak hizmetin meta veri URL 'SI adresiyle [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) çalıştırın.  
  
2. Oluşturulan yapılandırma dosyasını uygun bir düzenleyicide açın.  
  
3. Oluşturulan ve öğelerinin özniteliklerini ve içeriğini inceleyin [\<issuer>](../../configure-apps/file-schema/wcf/issuer.md) [\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) . Bunlar [\<security>](../../configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya özel bağlamalar öğeleri için öğeler içinde bulunur. Adreslerin beklenen etki alanı adlarını veya diğer adres bilgilerini içerdiğinden emin olun. İstemci bu adreslere kimlik doğrulaması yaptığından ve Kullanıcı adı/parola çiftleri gibi bilgileri açığa çıkarabileceğinden, bu bilgilerin denetlenmesi önemlidir. Adres beklenen adres değilse, bu, istenmeyen bir alıcıya bilgilerin açığa çıkmasına neden olabilir.  
  
4. [\<issuedTokenParameters>](../../configure-apps/file-schema/wcf/issuedtokenparameters.md)Açıklamalı <> öğesi içindeki ek öğeleri inceleyin `alternativeIssuedTokenParameters` . Bir Federasyon Hizmeti için yapılandırma oluşturmak üzere Svcutil. exe aracını kullanırken, Federasyon Hizmeti veya herhangi bir ara güvenlik belirteci hizmeti bir veren adresi belirtmez, ancak birden fazla uç nokta sunan bir güvenlik belirteci hizmeti için meta veri adresi belirtirseniz, sonuçta elde edilen yapılandırma dosyası ilk uç noktayı ifade eder. Ek uç noktalar, yapılandırma dosyasında,> öğeleri olarak yorumlanma <`alternativeIssuedTokenParameters` .  
  
     Bu <`issuedTokenParameters`> yapılandırmanın yapılandırmada zaten mevcut olan bir tercih edilip edilmeyeceğini saptayın. Örneğin, istemci bir güvenlik belirteci hizmetinde kimlik doğrulaması yapmayı tercih edebilir veya bir Kullanıcı adı/parola çifti yerine bir Windows CardSpace belirteci kullanın.  
  
    > [!NOTE]
    > Hizmet ile iletişim kurmadan önce birden çok güvenlik belirteci hizmetine çapraz bir güvenlik belirteci hizmeti gönderilmesi gerektiği, bir ara güvenlik belirteci hizmetinin istemciyi yanlış bir güvenlik belirteci hizmetine yönlendirme olasılığı vardır. Bu nedenle, içindeki güvenlik belirteci hizmeti uç noktasının, [\<issuedTokenParameters>](../../configure-apps/file-schema/wcf/issuedtokenparameters.md) bilinmeyen bir güvenlik belirteci hizmeti değil, beklenen güvenlik belirteci hizmeti olduğundan emin olun.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Kodda bir IssuedTokenClientCredential yapılandırmak için  
  
1. <xref:System.ServiceModel.Security.IssuedTokenClientCredential> <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> <xref:System.ServiceModel.Description.ClientCredentials> <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> Aşağıdaki örnek kodda gösterildiği gibi, sınıfının özelliği aracılığıyla öğesine (sınıfının özelliği tarafından döndürülen veya sınıfı aracılığıyla) erişin <xref:System.ServiceModel.ChannelFactory> .  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Belirteç önbelleğe alma gerekmiyorsa, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> özelliğini olarak ayarlayın `false` . <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A>Özelliği, bir güvenlik belirteci hizmetinden bu tür belirteçlerin önbelleğe alınıp alınmayacağını denetler. Bu özellik olarak ayarlandıysa `false` , istemci, önceki belirtecin hala geçerli olup olmamasından bağımsız olarak, kendisini federe hizmette yeniden kimlik doğrulamasından geçen her seferinde, güvenlik belirteci hizmetinden yeni bir belirteç ister. Bu özellik olarak ayarlandıysa `true` , istemci, Federasyon hizmetine kendisini yeniden kimlik doğrulamasından erdiğinde (belirtecin süresi dolmamışsa), mevcut bir belirteci yeniden kullanır. Varsayılan değer: `true`.  
  
3. Önbelleğe alınmış belirteçlerde bir zaman sınırı gerekliyse, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> özelliği bir değer olarak ayarlayın <xref:System.TimeSpan> . Özelliği, belirtecin ne kadar süreyle önbelleğe alınacağını belirtir. Belirtilen süre geçtikten sonra, belirteç istemci önbelleğinden kaldırılır. Belirteçler, varsayılan olarak süresiz olarak önbelleğe alınır. Aşağıdaki örnekte zaman aralığı 10 dakikaya ayarlanır.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. İsteğe bağlı. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A>Değerini bir yüzde olarak ayarlayın. Varsayılan değer 60 ' dir (yüzde). Özelliği, belirtecin geçerlilik döneminin yüzdesini belirtir. Örneğin, verilen belirteç 10 saat için geçerliyse ve <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> 80 olarak ayarlanırsa, belirteç sekiz saat sonra yenilenir. Aşağıdaki örnek, değeri yüzde 80 olarak ayarlar.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Belirteç geçerlilik süresi tarafından belirlenen yenileme aralığı ve `IssuedTokenRenewalThresholdPercentage` değer, `MaxIssuedTokenCachingTime` önbellek saatinin yenileme eşiği süresinden daha kısa olduğu durumlarda değer tarafından geçersiz kılınır. Örneğin, ürününün `IssuedTokenRenewalThresholdPercentage` ve belirtecinin süresi sekiz saat ise ve `MaxIssuedTokenCachingTime` değer 10 dakikadır ise, istemci, her 10 dakikada bir güncelleştirilmiş belirteç için güvenlik belirteci hizmetiyle iletişim kurar.  
  
5. İleti <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> güvenlik veya ileti kimlik bilgileriyle aktarım güvenliği kullanmayan bir bağlamada bir anahtar entropi modu gerekliyse (örneğin,. bağlama bir öğesine sahip değil <xref:System.ServiceModel.Channels.SecurityBindingElement> ), <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> özelliği uygun bir değere ayarlayın. *Entropi* modu, simetrik anahtarların özelliği kullanılarak denetlenemeyeceğini belirler <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> . Bu varsayılan, <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> hem istemci hem de belirteç verenin gerçek anahtarı oluşturmak için birleştirilen verileri sağladığı yerdir. Diğer değerler <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> ve <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy> ' dir. Bu, tüm anahtarın, sırasıyla istemci veya sunucu tarafından belirtilme anlamına gelir. Aşağıdaki örnek, özelliğini yalnızca anahtar için sunucu verilerini kullanacak şekilde ayarlar.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    > Bir <xref:System.ServiceModel.Channels.SecurityBindingElement> güvenlik belirteci hizmetinde veya hizmet bağlamasında varsa, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> üzerinde kümesi <xref:System.ServiceModel.Security.IssuedTokenClientCredential> , özelliği tarafından geçersiz kılınır <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> `SecurityBindingElement` .  
  
6. Verenle özel uç nokta davranışlarını, özelliği tarafından döndürülen koleksiyona ekleyerek yapılandırın <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> .  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Yapılandırmada IssuedTokenClientCredential yapılandırmak için  
  
1. Bir [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) uç nokta davranışında öğesinin alt öğesi olarak bir öğesi oluşturun.  
  
2. Belirteç önbelleğe alma gerekmiyorsa, `cacheIssuedTokens` (<`issuedToken`> öğesinin) özniteliğini olarak ayarlayın `false` .  
  
3. Önbelleğe alınmış belirteçlerde bir zaman sınırı gerekliyse, `maxIssuedTokenCachingTime` <`issuedToken`> öğesindeki özniteliği uygun bir değere ayarlayın. Örnek:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Varsayılan değerin dışında bir değer tercih edilirse, `issuedTokenRenewalThresholdPercentage` <`issuedToken`> öğesindeki özniteliği uygun bir değere ayarlayın, örneğin:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. İleti `CombinedEntropy` kimlik bilgileriyle ileti güvenliği veya aktarım güvenliği kullanmayan bir bağlamada dışında bir anahtar entropi modu varsa (örneğin, bağlamanın bir değeri yoksa `SecurityBindingElement` ), `defaultKeyEntropyMode` öğe üzerinde özniteliğini `<issuedToken>` `ServerEntropy` veya gereken şekilde ayarlayın `ClientEntropy` .  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. İsteğe bağlı. `issuerChannelBehaviors`<> öğesinin bir alt öğesi olarak bir <> öğesi oluşturarak, verenle özgü özel uç nokta davranışlarını yapılandırın `issuedToken` . Her davranış için, `add` <> öğesinin bir alt öğesi olarak bir <> öğesi oluşturun `issuerChannelBehaviors` . `issuerAddress`<> öğesindeki özniteliği ayarlayarak davranışın veren adresini belirtin `add` . `behaviorConfiguration`<> öğesindeki özniteliğini ayarlayarak davranışı belirtin `add` .  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Kodda bir X509CertificateRecipientClientCredential yapılandırmak için  
  
1. Sınıfının veya özelliğin özelliği aracılığıyla öğesine erişin <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> <xref:System.ServiceModel.ChannelFactory> .  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>Belirli bir uç nokta için sertifika için kullanılabilir bir örnek varsa, <xref:System.Collections.Generic.ICollection%601.Add%2A> özelliği tarafından döndürülen koleksiyonun yöntemini kullanın <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> .  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> örnek yoksa, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> Aşağıdaki örnekte gösterildiği gibi sınıfının yöntemini kullanın.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Yapılandırmada bir X509CertificateRecipientClientCredential yapılandırmak için  
  
1. Bir [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) uç nokta davranışında öğesinin bir alt öğesi olan öğesinin bir alt öğesi olarak bir öğesi oluşturun.  
  
2. Öğesinin `<add>` alt öğesi olarak bir öğesi oluşturun `<scopedCertificates>` . `storeLocation` `storeName` `x509FindType` İlgili sertifikaya başvuracak,,, ve `findValue` özniteliklerinin değerlerini belirtin. `targetUri`Aşağıdaki örnekte gösterildiği gibi, özniteliğini, sertifikanın kullanılacağı bitiş noktasının adresini sağlayan bir değere ayarlayın.  
  
    ```xml  
    <scopedCertificates>  
     <add targetUri="http://fabrikam.com/sts"
          storeLocation="CurrentUser"  
          storeName="TrustedPeople"  
          x509FindType="FindBySubjectName"  
          findValue="FabrikamSTS" />  
    </scopedCertificates>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kodda sınıfının bir örneğini yapılandırır <xref:System.ServiceModel.Security.IssuedTokenClientCredential> .  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Olası bilgilerin açıklanmasını engellemek için, Svcutil. exe aracını çalıştıran istemciler, Federasyon uç noktalarından meta verileri işlemek için, sonuçta elde edilen güvenlik belirteci hizmeti adreslerinin bekledikleri gibi olduğundan emin olmalıdır. Bu durum, bir güvenlik belirteci hizmeti birden çok bitiş noktası kullanıma sunduğundan önemlidir, çünkü Svcutil. exe aracı, istemcinin kullanılması gereken ilk uç noktayı kullanmak için ortaya çıkan yapılandırma dosyasını oluşturur.  
  
## <a name="localissuer-required"></a>LocalIssuer gerekli  
 İstemcilerin her zaman yerel bir veren kullanması bekleniyorsa aşağıdakileri aklınızda yapın: zincirde bulunan ikinci-son güvenlik belirteci hizmeti bir veren adresi veya verenin meta veri adresini belirtiyorsa, Svcutil. exe ' nin varsayılan çıktısı yerel veren 'in kullanılmasına neden olur.  
  
 Sınıfının,, ve özelliklerini ayarlama hakkında daha fazla bilgi için <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> <xref:System.ServiceModel.Security.IssuedTokenClientCredential> bkz. [nasıl yapılır: yerel veren yapılandırma](how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Kapsamlı sertifikalar  
 Hizmet sertifikalarının herhangi bir güvenlik belirteci hizmeti ile iletişim kurmak için belirtilmesi gerekiyorsa, genellikle sertifika anlaşması kullanılmadığından, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> sınıfının özelliği kullanılarak belirtilebilir <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> . <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A>Yöntemi bir <xref:System.Uri> ve bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> as parametresi alır. Belirtilen URI 'de uç noktalarla iletişim kurulurken belirtilen sertifika kullanılıyor. Alternatif olarak, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> özelliği tarafından döndürülen koleksiyona bir sertifika eklemek için yöntemini kullanabilirsiniz <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> .  
  
> [!NOTE]
> Belirli bir URI ile kapsamdaki sertifikaların istemci fikri yalnızca, bu URI 'Ler üzerinde uç noktaları sunan hizmetlere giden çağrılar yapan uygulamalar için geçerlidir. Bu, sınıfının tarafından döndürülen koleksiyondaki sunucuda yapılandırılmış olanlar gibi, verilen belirteçleri imzalamak için kullanılan sertifikalara uygulanmaz <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> . Daha fazla bilgi için bkz. [nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma](how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon Örneği](../samples/federation-sample.md)
- [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: WSFederationHttpBinding Oluşturma](how-to-create-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](how-to-configure-credentials-on-a-federation-service.md)
- [Nasıl yapılır: Yerel Yayımlayan Yapılandırma](how-to-configure-a-local-issuer.md)
- [Meta Veriler Hakkında Güvenlik Konuları](security-considerations-with-metadata.md)
- [Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme](how-to-secure-metadata-endpoints.md)
