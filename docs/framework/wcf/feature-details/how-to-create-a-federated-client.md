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
ms.openlocfilehash: a9213d8cbbafaaa1fffa3a1db0d6936c2fc6544f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185038"
---
# <a name="how-to-create-a-federated-client"></a>Nasıl yapılır: Federe İstemci Oluşturma
Windows Communication Foundation'da (WCF), *federe hizmet* için bir istemci oluşturmak üç ana adımdan oluşur:  
  
1. [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya benzer özel bağlama yı yapılandırın. Uygun bir bağlama oluşturma hakkında daha fazla bilgi için [bkz: WSFederationHttpBinding oluşturun.](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md) Alternatif olarak, federe hizmet ve bir veya daha fazla güvenlik belirteç hizmetleri ile iletişim için bir yapılandırma dosyası oluşturmak için federe hizmet meta veri bitiş noktasına karşı [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) çalıştırın.  
  
2. Bir güvenlik belirteci hizmeti ile istemcinin etkileşiminin çeşitli yönlerini denetleyen özellikleri <xref:System.ServiceModel.Security.IssuedTokenClientCredential> ayarlayın.  
  
3. Güvenlik belirteci <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>hizmetleri gibi verilen uç noktalarla güvenli bir şekilde iletişim kurmak için gereken sertifikaların özelliklerini ayarlayın.  
  
> [!NOTE]
> İstemci, kimliği <xref:System.Security.Cryptography.CryptographicException> meslelenmi, <xref:System.ServiceModel.WSFederationHttpBinding> bağlama veya özel olarak verilmiş bir belirteç ve asimetrik anahtarlar kullandığında a atılabilir. Asimetrik tuşlar, <xref:System.ServiceModel.WSFederationHttpBinding> sırasıyla ve özellikleri nin ayarlandığında, bağlama <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> ve <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> özel <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>olarak verilen belirteçlerle birlikte kullanılır. İstemci <xref:System.Security.Cryptography.CryptographicException> ileti göndermeye çalıştığında ve istemcinin taklit ettiği kimlik için kullanıcı profili olmadığında atılır. Bu sorunu azaltmak için, ileti göndermeden önce `LoadUserProfile` istemci bilgisayarda oturum açın veya arayın.  
  
 Bu konu, bu yordamlar hakkında ayrıntılı bilgi sağlar. Uygun bir bağlama oluşturma hakkında daha fazla bilgi için [bkz: WSFederationHttpBinding oluşturun.](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md) Federe hizmetin nasıl çalıştığı hakkında daha fazla bilgi için [Federasyon'a](../../../../docs/framework/wcf/feature-details/federation.md)bakın.  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Federe hizmet için yapılandırmaoluşturmak ve incelemek  
  
1. [ServiceModel Metadata Utility Tool'u (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmetin meta veri URL'sinin adresiyle komut satırı parametresi olarak çalıştırın.  
  
2. Oluşturulan yapılandırma dosyasını uygun bir düzenleyicide açın.  
  
3. Oluşturulan [ \<herhangi](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) bir verenin ve verenin>ve [ \<verenMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) öğelerinin özniteliklerini ve içeriğini inceleyin. Bunlar [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya özel bağlama öğeleri için [ \<güvenlik>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) öğeleri içinde yer alır. Adreslerin beklenen alan adı veya diğer adres bilgilerini içerdiğinden emin olun. İstemci bu adresleri doğruladığı ve kullanıcı adı/parola çiftleri gibi bilgileri ifşa edebileceğinden, bu bilgileri denetlemek önemlidir. Adres beklenen adres değilse, bu durum istenmeyen bir alıcıya bilgi ifşasına neden olabilir.  
  
4. Yorumlanan <`alternativeIssuedTokenParameters`> öğesi içindeki ek [ \<verilen TokenParametreleri>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) öğeleri inceleyin. Federe bir hizmet için yapılandırma oluşturmak için Svcutil.exe aracını kullanırken, federe hizmet veya herhangi bir ara güvenlik belirteci hizmetleri bir ihraççı adresi belirtmiyorsa, daha çok bir güvenlik belirteci hizmeti için bir meta veri adresi belirtin birden çok uç nokta, ortaya çıkan yapılandırma dosyası ilk bitiş noktasına başvurur. Yapılandırma dosyasında,> öğeleri <yorumlanan <`alternativeIssuedTokenParameters` ek uç noktalar bulunmaktadır.  
  
     Bu <`issuedTokenParameters`> biri yapılandırmada zaten mevcut olana tercih edilip> belirleyin. Örneğin, istemci bir kullanıcı adı/parola çifti yerine Windows CardSpace belirteci kullanarak bir güvenlik belirteci hizmetine kimlik doğrulaması yapmayı tercih edebilir.  
  
    > [!NOTE]
    > Hizmetle iletişim kurmadan önce birden çok güvenlik belirteci hizmetinin geçmesi gerektiğinde, bir ara güvenlik belirteci hizmetinin istemciyi yanlış bir güvenlik belirteci hizmetine yönlendirmesi mümkündür. Bu nedenle, [ \<verilen TokenParametreleri>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) güvenlik belirteci hizmeti için bitiş noktası nın bilinmeyen bir güvenlik belirteci hizmeti değil, beklenen güvenlik belirteci hizmeti olduğundan emin olun.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>IssuedTokenClientCredential kodolarak yapılandırmak için  
  
1. <xref:System.ServiceModel.Security.IssuedTokenClientCredential> Aşağıdaki örnek <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> kodda <xref:System.ServiceModel.Description.ClientCredentials> gösterildiği gibi sınıfın <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliğine <xref:System.ServiceModel.ClientBase%601> (sınıfın özelliği <xref:System.ServiceModel.ChannelFactory> tarafından döndürülen veya sınıf aracılığıyla) erişin.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Belirteç önbelleğe alınması gerekli <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> değilse, özelliği 'ye `false`ayarlayın. Özellik, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> bir güvenlik belirteci hizmetindeki bu tür belirteçlerin önbelleğe alınıp alınmadığını denetler. Bu özellik `false`ayarlanmışsa, istemci, önceki bir belirteç hala geçerli olup olmadığına bakılmaksızın kendisini federated hizmetine yeniden doğrulaması gerektiğinde, güvenlik belirteci hizmetinden yeni bir belirteç ister. Bu özellik `true`ayarlanmışsa, istemci varolan bir belirteci, kendisini federe hizmete yeniden doğrulaması gerektiğinde yeniden kullanır (belirteç süresi dolmamış sayılsa). Varsayılan değer: `true`.  
  
3. Önbelleğe alınmış belirteçlerde bir zaman sınırı <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> gerekiyorsa, <xref:System.TimeSpan> özelliği bir değere ayarlayın. Özellik, bir belirteci nin önbelleğe alınabileceğini belirtir. Belirtilen süre dolduktan sonra belirteç istemci önbelleğinden kaldırılır. Varsayılan olarak, belirteçler süresiz olarak önbelleğe alınır. Aşağıdaki örnekte, zaman aralığı 10 dakika olarak ayarlanır.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. İsteğe bağlı. Yüzdeyi <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> ayarlayın. Varsayılan değer 60 'dir (yüzde). Özellik, belirteç geçerlilik süresinin bir yüzdesini belirtir. Örneğin, verilen belirteç 10 saat boyunca <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> geçerliyse ve 80 olarak ayarlanmışsa, belirteç sekiz saat sonra yenilenir. Aşağıdaki örnekte değeri yüzde 80 olarak ayarlar.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Önbelleğe alma süresinin yenileme eşiği `IssuedTokenRenewalThresholdPercentage` süresinden daha kısa `MaxIssuedTokenCachingTime` olduğu durumlarda, belirteç geçerlilik süresine göre belirlenen yenileme aralığı ve değer değer tarafından geçersiz kılınır. Örneğin, ürün `IssuedTokenRenewalThresholdPercentage` ve belirteç süresi sekiz saat ve `MaxIssuedTokenCachingTime` değeri 10 dakika ise, istemci her 10 dakikada bir güncelleştirilmiş bir belirteç için güvenlik belirteci hizmetiyle bağlantı kurur.  
  
5. İleti güvenliği veya ileti kimlik <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> bilgileriyle aktarım güvenliği kullanmayan bir bağlama üzerinde gerekenin dışında bir anahtar entropi modu gerekiyorsa (örneğin. bağlama, <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> özelliği uygun bir değere ayarlamalıdır. *Entropi* modu, simetrik tuşların <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> özelliği kullanılarak denetlenip denetlenemeyeceğini belirler. Bu varsayılan, hem istemci hem de belirteç verenin gerçek anahtarı oluşturmak için birleştirilen verileri sağladığı değerdir. <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> Diğer değerler <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>ve , tüm anahtarı istemci veya sunucu tarafından sırasıyla belirtilir anlamına gelir. Aşağıdaki örnek, anahtarın yalnızca sunucu verilerini kullanacak özelliği ayarlar.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    > Bir <xref:System.ServiceModel.Channels.SecurityBindingElement> güvenlik belirteci hizmetinde veya hizmet <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> bağlamada <xref:System.ServiceModel.Security.IssuedTokenClientCredential> a varsa, <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> ayarlanan `SecurityBindingElement`özellik .  
  
6. Herhangi bir verene özgü uç nokta davranışlarını <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> özellik tarafından döndürülen koleksiyona ekleyerek yapılandırın.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>IssuedTokenClientCredential yapılandırmasını yapılandırmak için  
  
1. Bir bitiş noktası [ \<davranışında, verilen Token>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) öğesinin alt öğesi olarak verilmiş bir [ \<Token>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) öğesi oluşturun.  
  
2. Belirteç önbelleğe alınması gerekli `cacheIssuedTokens` değilse, özniteliği `issuedToken` (<`false`> öğesi) olarak ayarlayın.  
  
3. Önbelleğe alınmış belirteçlerde bir zaman sınırı `maxIssuedTokenCachingTime` gerekiyorsa, <`issuedToken`> öğesindeki özniteliği uygun bir değere ayarlayın. Örnek:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Varsayılan değer dışında bir değer tercih `issuedTokenRenewalThresholdPercentage` edilirse, <`issuedToken`> öğesindeki özniteliği uygun bir değere ayarlayın:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. İleti güvenliği veya ileti kimlik `CombinedEntropy` bilgileriyle aktarım güvenliği kullanmayan bir bağlama üzerinde yse (örneğin, bağlamanın `SecurityBindingElement`bir `defaultKeyEntropyMode` özelliği yok), `<issuedToken>` öğedeki `ServerEntropy` özniteliği bir ya da `ClientEntropy` gerektiği gibi ayarlayın.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. İsteğe bağlı. <`issuedToken`> öğesinin bir alt öğesi olarak `issuerChannelBehaviors` <> öğesi oluşturarak herhangi bir verene özgü özel bitiş noktası davranışını yapılandırın. Her davranış için, `add` <`issuerChannelBehaviors`> öğesinin bir alt öğesi olarak <bir> öğesi oluşturun. Özniteliği <`issuerAddress` `add`> öğesine ayarlayarak davranışın veren adresini belirtin. <`behaviorConfiguration` `add`> öğesi özniteliği ayarlayarak davranışın kendisini belirtin.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>X509CertificateRecipientClientCredential kodolarak yapılandırmak için  
  
1. <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Sınıfın veya <xref:System.ServiceModel.ChannelFactory> mülkün özelliğinden erişin. <xref:System.ServiceModel.ClientBase%601>  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. Belirli <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> bir bitiş noktası için sertifika için bir <xref:System.Collections.Generic.ICollection%601.Add%2A> örnek varsa, özellik <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> tarafından döndürülen koleksiyon yöntemini kullanın.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> örnek kullanılamıyorsa, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> aşağıdaki örnekte gösterildiği gibi sınıfın yöntemini <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> kullanın.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Bir X509CertificateRecipientClientCredential yapılandırmasını yapılandırmak için  
  
1. Bir bitiş noktası davranışında [ \<istemci kimlik](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) bilgileri>öğesinin kendisi olan [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) öğesinin bir alt öğesi olarak [ \<kapsamlı Sertifikalar>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) öğesi oluşturun.  
  
2. `<add>` Öğenin `<scopedCertificates>` bir alt öğesi olarak bir öğe oluşturun. Uygun sertifikaya `storeLocation` `storeName`başvurmak `x509FindType`için `findValue` , , ve öznitelikler için değerleri belirtin. `targetUri` Özniteliği, aşağıdaki örnekte gösterildiği gibi, sertifikanın kullanılacağı bitiş noktasının adresini sağlayan bir değere ayarlayın.  
  
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
 Aşağıdaki kod örneği, koddaki <xref:System.ServiceModel.Security.IssuedTokenClientCredential> sınıfın bir örneğini yapılandırır.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Olası bilgilerin açıklanmasını önlemek için, federe uç noktalardan meta verileri işlemek için Svcutil.exe aracını çalıştıran istemciler, ortaya çıkan güvenlik belirteç hizmet adreslerinin bekledikleri gibi olduğundan emin olmalıdır. Svcutil.exe aracı, istemcinin kullanması gereken ilk bitiş noktasını kullanmak için ortaya çıkan yapılandırma dosyasını oluşturduğundan, bir güvenlik belirteci hizmeti birden çok uç noktayı ortaya çıkardığında bu özellikle önemlidir.  
  
## <a name="localissuer-required"></a>LocalIssuer Gerekli  
 İstemcilerin her zaman yerel bir veren kullanması bekleniyorsa, aşağıdakileri unutmayın: Svcutil.exe'nin varsayılan çıktısı, zincirdeki sondan ikinci güvenlik belirteci hizmeti bir veren adresi veya veren meta veri adresi belirtmişse yerel ihraççının kullanılmamasıyla sonuçlanır.  
  
 Sınıfın <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>, ve <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> özelliklerinin <xref:System.ServiceModel.Security.IssuedTokenClientCredential> ayarlanması hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
  
## <a name="scoped-certificates"></a>Kapsamlı Sertifikalar  
 Hizmet sertifikalarının güvenlik belirteci hizmetlerinden herhangi biriyle iletişim kurmak için belirtilmesi gerekiyorsa, genellikle sertifika <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> anlaşması kullanılmadığından, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> sınıfın özelliği kullanılarak belirtilebilir. Yöntem <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> a <xref:System.Uri> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> a parametreleri olarak alır. Belirtilen sertifika, belirtilen URI'deki uç noktalarla iletişim kurarken kullanılır. Alternatif olarak, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> özellik tarafından döndürülen koleksiyona sertifika eklemek için yöntemi kullanabilirsiniz.  
  
> [!NOTE]
> Belirli bir URI kapsamına giren sertifikaların istemci fikri yalnızca bu ÜRB'lerde uç noktaları ortaya çıkaran hizmetlere giden çağrılar yapan uygulamalar için geçerlidir. Sınıfın döndürüldettiği koleksiyondaki sunucuda yapılandırılanlar gibi, verilen belirteçleri imzalamak için kullanılan <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> sertifikalar için geçerli değildir. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> Daha fazla bilgi için [bkz: Federasyon Hizmetinde Kimlik Bilgilerini Yapılandırma.](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: WSFederationHttpBinding Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Nasıl yapılır: Yerel Yayımlayan Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
