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
ms.openlocfilehash: 988fc79f71b670f5eaed1a305f54cc90374e4b17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950623"
---
# <a name="how-to-create-a-federated-client"></a>Nasıl yapılır: Federe İstemci Oluşturma
Windows Communication Foundation (WCF) ' de, *Federasyon Hizmeti* için bir istemci oluşturmak üç ana adımdan oluşur:  
  
1. Bir [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya benzer bir özel bağlama yapılandırın. Uygun bağlama oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)oluşturun. Alternatif olarak, Federasyon Hizmeti ve bir veya daha fazla güvenlik belirteci hizmeti ile iletişim kurmak için bir yapılandırma dosyası oluşturmak üzere, Federasyon Hizmeti 'nin meta veri uç noktasına karşı [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) çalıştırın.  
  
2. Bir güvenlik belirteci hizmeti ile <xref:System.ServiceModel.Security.IssuedTokenClientCredential> istemci etkileşiminin çeşitli yönlerini denetleyen öğesinin özelliklerini ayarlayın.  
  
3. İçin <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>gerekli olan sertifikaların, güvenlik belirteci Hizmetleri gibi belirli uç noktalarla güvenli bir şekilde iletişim kurmasına olanak sağlayan öğesinin özelliklerini ayarlayın.  
  
> [!NOTE]
> İstemci kimliğe bürünülmüş kimlik bilgileri <xref:System.ServiceModel.WSFederationHttpBinding> , bağlama veya özel olarak verilen bir belirteç ve asimetrik anahtarlar kullandığında bu durum oluşabilir.<xref:System.Security.Cryptography.CryptographicException> Asimetrik <xref:System.ServiceModel.WSFederationHttpBinding> anahtarlar, <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> ve <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> özellikleri sırasıyla olarak <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>ayarlandığında bağlama ve özel verilen belirteçlerle kullanılır. <xref:System.Security.Cryptography.CryptographicException> İstemci bir ileti göndermek istediğinde oluşturulur ve istemcinin kimliğine bürünerek kimliği için bir kullanıcı profili mevcut değildir. Bu sorunu azaltmak için, iletiyi göndermeden önce istemci bilgisayarda oturum açın veya `LoadUserProfile` çağrı yapın.  
  
 Bu konu, bu yordamlar hakkında ayrıntılı bilgi sağlar. Uygun bağlama oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)oluşturun. Federe bir hizmetin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Federasyon Hizmeti için yapılandırma oluşturmak ve incelemek için  
  
1. Bir komut satırı parametresi olarak hizmetin meta veri URL 'SI adresiyle [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) çalıştırın.  
  
2. Oluşturulan yapılandırma dosyasını uygun bir düzenleyicide açın.  
  
3. [ Oluşturulan\<herhangi bir verenin >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) ve [ \<IssuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) öğelerinin özniteliklerini ve içeriğini inceleyin. Bunlar [, \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya özel bağlamalar öğeleri için [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) öğeleri içinde bulunur. Adreslerin beklenen etki alanı adlarını veya diğer adres bilgilerini içerdiğinden emin olun. İstemci bu adreslere kimlik doğrulaması yaptığından ve Kullanıcı adı/parola çiftleri gibi bilgileri açığa çıkarabileceğinden, bu bilgilerin denetlenmesi önemlidir. Adres beklenen adres değilse, bu, istenmeyen bir alıcıya bilgilerin açığa çıkmasına neden olabilir.  
  
4. `alternativeIssuedTokenParameters` [ Diğer\<IssuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) açıklamalı < > öğesi içindeki öğeleri inceleyin. Federasyon Hizmeti için yapılandırma oluşturmak üzere Svcutil. exe aracını kullanırken, Federasyon Hizmeti veya herhangi bir ara güvenlik belirteci hizmeti bir veren adresi belirtmez, ancak bunu sunan bir güvenlik belirteci hizmeti için bir meta veri adresi belirtin birden fazla uç nokta, sonuçta elde edilen yapılandırma dosyası ilk uç noktayı ifade eder. Ek uç noktalar, yapılandırma dosyasında, > öğeleri olarak yorumlanma`alternativeIssuedTokenParameters`<.  
  
     Bu <`issuedTokenParameters`> yapılandırmanın yapılandırmada zaten mevcut olan bir tercih edilip edilmeyeceğini saptayın. Örneğin, istemci bir güvenlik belirteci hizmetinde kimlik doğrulaması yapmayı tercih edebilir veya bir Kullanıcı adı/parola çifti yerine bir Windows CardSpace belirteci kullanın.  
  
    > [!NOTE]
    > Hizmet ile iletişim kurmadan önce birden çok güvenlik belirteci hizmetine çapraz bir güvenlik belirteci hizmeti gönderilmesi gerektiği, bir ara güvenlik belirteci hizmetinin istemciyi yanlış bir güvenlik belirteci hizmetine yönlendirme olasılığı vardır. Bu nedenle, [ \<IssuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) güvenlik belirteci hizmeti uç noktasının, bilinmeyen bir güvenlik belirteci hizmeti değil, beklenen güvenlik belirteci hizmeti olduğundan emin olun.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Kodda bir IssuedTokenClientCredential yapılandırmak için  
  
1. <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> <xref:System.ServiceModel.ChannelFactory> Aşağıdakiörnek<xref:System.ServiceModel.ClientBase%601> kodda gösterildiği gibi, <xref:System.ServiceModel.Description.ClientCredentials> sınıfının özelliği aracılığıylaöğesine(sınıfınınözelliğitarafındandöndürülenveyasınıfıaracılığıyla)erişin.<xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Belirteç önbelleğe alma gerekmiyorsa, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> özelliğini olarak `false`ayarlayın. Özelliği <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> , bir güvenlik belirteci hizmetinden bu tür belirteçlerin önbelleğe alınıp alınmayacağını denetler. Bu özellik olarak `false`ayarlandıysa, istemci, önceki belirtecin hala geçerli olup olmamasından bağımsız olarak, kendisini federe hizmette yeniden kimlik doğrulamasından geçen her seferinde, güvenlik belirteci hizmetinden yeni bir belirteç ister. Bu özellik olarak `true`ayarlandıysa, istemci, Federasyon hizmetine kendisini yeniden kimlik doğrulamasından erdiğinde (belirtecin süresi dolmamışsa), mevcut bir belirteci yeniden kullanır. Varsayılan, `true` değeridir.  
  
3. Önbelleğe alınmış belirteçlerde bir zaman sınırı gerekliyse, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> özelliği bir <xref:System.TimeSpan> değer olarak ayarlayın. Özelliği, belirtecin ne kadar süreyle önbelleğe alınacağını belirtir. Belirtilen süre geçtikten sonra, belirteç istemci önbelleğinden kaldırılır. Belirteçler, varsayılan olarak süresiz olarak önbelleğe alınır. Aşağıdaki örnekte zaman aralığı 10 dakikaya ayarlanır.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. İsteğe bağlı. Değerini bir yüzde olarak ayarlayın. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> Varsayılan değer 60 ' dir (yüzde). Özelliği, belirtecin geçerlilik döneminin yüzdesini belirtir. Örneğin, verilen belirteç 10 saat için geçerliyse ve <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> 80 olarak ayarlanırsa, belirteç sekiz saat sonra yenilenir. Aşağıdaki örnek, değeri yüzde 80 olarak ayarlar.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Belirteç geçerlilik süresi tarafından belirlenen yenileme aralığı ve `IssuedTokenRenewalThresholdPercentage` değer, önbellek saatinin yenileme eşiği süresinden daha kısa olduğu durumlarda değer `MaxIssuedTokenCachingTime` tarafından geçersiz kılınır. Örneğin, ürününün `IssuedTokenRenewalThresholdPercentage` ve belirtecinin süresi sekiz saat ise `MaxIssuedTokenCachingTime` ve değer 10 dakikadır ise, istemci, her 10 dakikada bir güncelleştirilmiş belirteç için güvenlik belirteci hizmetiyle iletişim kurar.  
  
5. İleti güvenlik veya ileti kimlik bilgileriyle aktarım <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> güvenliği kullanmayan bir bağlamada bir anahtar entropi modu gerekliyse (örneğin,. bağlama bir <xref:System.ServiceModel.Channels.SecurityBindingElement>öğesine sahip değil), <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> özelliği uygun bir değere ayarlayın. *Entropi* modu, simetrik anahtarların <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> özelliği kullanılarak denetlenemeyeceğini belirler. Bu varsayılan <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>, hem istemci hem de belirteç verenin gerçek anahtarı oluşturmak için birleştirilen verileri sağladığı yerdir. Diğer değerler ve <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>' dir. Bu, tüm anahtarın, sırasıyla istemci veya sunucu tarafından belirtilme anlamına gelir. Aşağıdaki örnek, özelliğini yalnızca anahtar için sunucu verilerini kullanacak şekilde ayarlar.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    > Bir <xref:System.ServiceModel.Channels.SecurityBindingElement> güvenlik belirteci hizmetinde veya hizmet bağlamasında varsa <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> , <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> üzerinde <xref:System.ServiceModel.Security.IssuedTokenClientCredential> kümesi, `SecurityBindingElement`özelliği tarafından geçersiz kılınır.  
  
6. Verenle özel uç nokta davranışlarını, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> özelliği tarafından döndürülen koleksiyona ekleyerek yapılandırın.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Yapılandırmada IssuedTokenClientCredential yapılandırmak için  
  
1. Bir uç nokta davranışında [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) öğesinin alt öğesi olarak bir [ IssuedToken>öğesioluşturun.\<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)  
  
2. Belirteç önbelleğe alma gerekmiyorsa, (< `cacheIssuedTokens` `issuedToken`> öğesinin) özniteliğini olarak `false`ayarlayın.  
  
3. Önbelleğe alınmış belirteçlerde bir zaman sınırı gerekliyse, < `maxIssuedTokenCachingTime` `issuedToken`> öğesindeki özniteliği uygun bir değere ayarlayın. Örneğin:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Varsayılan değerin dışında bir değer tercih edilirse, < `issuedTokenRenewalThresholdPercentage` `issuedToken`> öğesindeki özniteliği uygun bir değere ayarlayın, örneğin:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. İleti kimlik bilgileriyle ileti güvenliği veya aktarım `CombinedEntropy` güvenliği kullanmayan bir bağlamada dışında bir anahtar entropi modu varsa (örneğin, bağlamanın bir `SecurityBindingElement`değeri yoksa) `defaultKeyEntropyMode` , bu özniteliği `<issuedToken>` öğesi için `ServerEntropy` `ClientEntropy` gerekli.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. İsteğe bağlı. `issuerChannelBehaviors`<`issuedToken`> Öğesinin bir alt öğesi olarak bir < > öğesi oluşturarak, verenle özgü özel uç nokta davranışlarını yapılandırın. Her davranış için, <`add``issuerChannelBehaviors`> öğesinin bir alt öğesi olarak bir < > öğesi oluşturun. `issuerAddress` <`add`> Öğesindeki özniteliği ayarlayarak davranışın veren adresini belirtin. `behaviorConfiguration` <`add`> Öğesindeki özniteliğini ayarlayarak davranışı belirtin.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Kodda bir X509CertificateRecipientClientCredential yapılandırmak için  
  
1. Sınıfınınveya<xref:System.ServiceModel.ClientBase%601> özelliğin özelliği <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>aracılığıylaöğesineerişin. <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> <xref:System.ServiceModel.ChannelFactory>  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. Belirli bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> uç nokta için sertifika için kullanılabilir bir örnek varsa, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> özelliği tarafından döndürülen <xref:System.Collections.Generic.ICollection%601.Add%2A> koleksiyonun yöntemini kullanın.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> örnek yoksa, aşağıdaki örnekte gösterildiği gibi <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> sınıfının <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> yöntemini kullanın.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Yapılandırmada bir X509CertificateRecipientClientCredential yapılandırmak için  
  
1. Bir uç nokta [davranışında \<ClientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesinin bir alt öğesi olan [ \<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) öğesinin bir alt öğesi olarak bir [ ScopedCertificates>oluşturun.\<](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)  
  
2. Öğesinin alt `<add>` `<scopedCertificates>` öğesi olarak bir öğesi oluşturun. İlgili `storeLocation`sertifikaya başvuracak `storeName` `findValue` ,,, ve özniteliklerinin değerlerini belirtin. `x509FindType` Aşağıdaki örnekte gösterildiği gibi, özniteliğini,sertifikanınkullanılacağıbitişnoktasınınadresinisağlayanbirdeğereayarlayın.`targetUri`  
  
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
 Aşağıdaki kod örneği, kodda <xref:System.ServiceModel.Security.IssuedTokenClientCredential> sınıfının bir örneğini yapılandırır.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Olası bilgilerin açıklanmasını engellemek için, Svcutil. exe aracını çalıştıran istemciler, Federasyon uç noktalarından meta verileri işlemek için, sonuçta elde edilen güvenlik belirteci hizmeti adreslerinin bekledikleri gibi olduğundan emin olmalıdır. Bu durum, bir güvenlik belirteci hizmeti birden çok bitiş noktası kullanıma sunduğundan önemlidir, çünkü Svcutil. exe aracı, istemcinin kullanılması gereken ilk uç noktayı kullanmak için ortaya çıkan yapılandırma dosyasını oluşturur.  
  
## <a name="localissuer-required"></a>LocalIssuer gerekli  
 İstemcilerin her zaman yerel bir veren kullanması bekleniyorsa aşağıdakileri aklınızda yapın: zincirde bulunan ikinci-son güvenlik belirteci hizmeti bir veren adresi veya verenin meta veri adresini belirtiyorsa, Svcutil. exe ' nin varsayılan çıktısı yerel veren 'in kullanılmasına neden olur.  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> [Sınıfının, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>, ve<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> özelliklerini ayarlama hakkında daha fazla bilgi için bkz. nasıl yapılır: <xref:System.ServiceModel.Security.IssuedTokenClientCredential> Yerel bir veren](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)yapılandırın.  
  
## <a name="scoped-certificates"></a>Kapsamlı sertifikalar  
 Hizmet sertifikalarının herhangi bir güvenlik belirteci hizmeti ile iletişim kurmak için belirtilmesi gerekiyorsa, genellikle sertifika anlaşması kullanılmadığından, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> sınıfının özelliği kullanılarak belirtilebilir. Yöntemi bir <xref:System.Uri> ve bir<xref:System.Security.Cryptography.X509Certificates.X509Certificate2> as parametresi alır. <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> Belirtilen URI 'de uç noktalarla iletişim kurulurken belirtilen sertifika kullanılıyor. Alternatif olarak, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> özelliği tarafından döndürülen <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> koleksiyona bir sertifika eklemek için yöntemini kullanabilirsiniz.  
  
> [!NOTE]
> Belirli bir URI ile kapsamdaki sertifikaların istemci fikri yalnızca, bu URI 'Ler üzerinde uç noktaları sunan hizmetlere giden çağrılar yapan uygulamalar için geçerlidir. Bu, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> sınıfının tarafından döndürülen koleksiyondaki sunucuda yapılandırılmış olanlar gibi, verilen belirteçleri imzalamak için kullanılan sertifikalara uygulanmaz. Daha fazla bilgi için [nasıl yapılır: Federasyon Hizmeti](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Nasıl yapılır: Bir WSFederationHttpBinding üzerindeki güvenli oturumları devre dışı bırakma](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Nasıl yapılır: Yerel veren yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Nasıl yapılır: Güvenli meta veri uç noktaları](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
