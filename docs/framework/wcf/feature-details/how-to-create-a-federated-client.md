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
ms.openlocfilehash: 19ffe7e3fb0de9b377279d9cd274f998a104c6b2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303394"
---
# <a name="how-to-create-a-federated-client"></a>Nasıl yapılır: Federe İstemci Oluşturma
Windows Communication Foundation (WCF) oluşturmak için bir istemci bir *Federasyon Hizmeti* üç ana adımdan oluşur:  
  
1. Yapılandırma bir [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ya da benzer özel bağlama. Uygun bir bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Alternatif olarak, çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) karşı Federasyon Hizmeti ve bir veya daha fazlası ile iletişim kurmak için bir yapılandırma dosyası oluşturmak için Federasyon Hizmeti meta veri uç noktası Güvenlik belirteci Hizmetleri.  
  
2. Özelliklerini ayarlama <xref:System.ServiceModel.Security.IssuedTokenClientCredential> , bir istemcinin etkileşim güvenlik belirteci hizmeti çeşitli yönlerini denetler.  
  
3. Özelliklerini ayarlama <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>, güvenli bir şekilde belirli bir güvenlik belirteci Hizmetleri gibi uç noktaları iletişim kurması için gerekli sertifikaları sağlar.  
  
> [!NOTE]
>  A <xref:System.Security.Cryptography.CryptographicException> istemci kimliğine bürünülen kimlik bilgileri kullandığında harekete geçirilebilirse <xref:System.ServiceModel.WSFederationHttpBinding> bağlama veya özel tarafından verilen bir belirteç ve asimetrik anahtarlar. Asimetrik anahtarlar ile kullanılan <xref:System.ServiceModel.WSFederationHttpBinding> bağlama ve özel verilen zaman belirteçler <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> ve <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> özellikleri sırasıyla ayarlanmış <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>. <xref:System.Security.Cryptography.CryptographicException> İleti göndermek istemci dener ve istemci kimliğine bürünme kimlik için mevcut bir kullanıcı profili oluşturulur. Bu sorunu gidermek için oturum açın istemci bilgisayarı veya çağrı `LoadUserProfile` ileti göndermeden önce.  
  
 Bu konu, bu yordamları hakkında ayrıntılı bilgi sağlar. Uygun bir bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Federasyon hizmetinin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Oluşturma ve bir Federasyon Hizmeti için yapılandırma incelemek için  
  
1. Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmetinin komut satırı parametresi olarak meta verileri URL'sini adresine sahip.  
  
2. Oluşturulan yapılandırma dosyasını uygun bir düzenleyicide açın.  
  
3. Öznitelikleri ve oluşturulan tüm içeriğini İnceleme [ \<veren >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) ve [ \<İssuedtokenparameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) öğeleri. Bunlar içinde bulunan [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) için öğeleri [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya özel bağlamalar öğeleri. Adresleri beklenen etki alanı adlarını veya diğer adres bilgilerini içerdiğinden emin olun. İstemci kimlik doğrulaması için bu adresleri ve kullanıcı adı/parola çiftleri gibi bilgileri açıklayabilir çünkü bu bilgileri denetlemek önemlidir. Adresi beklenen adres değilse, bu istenmeyen bir alıcının bilgileri açığa çıkmasına neden olabilir.  
  
4. Ek inceleyin [ \<İssuermetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) açıklamalı içinde öğeleri kullanıma <`alternativeIssuedTokenParameters`> öğesi. Federe hizmet veya tüm ara güvenlik belirteci hizmetlerine veren adresi belirtmeyin, ancak bunun yerine bir kullanıma sunan bir güvenlik belirteci hizmeti meta veri adresini belirtin, bir Federasyon Hizmeti için yapılandırma üretmek için Svcutil.exe aracını kullanırken birden fazla uç nokta, elde edilen yapılandırma dosyası Birinci uç nokta için ifade eder. Ek uç noktalar olan derleme dışı bırakılan yapılandırma dosyasındaki <`alternativeIssuedTokenParameters`> öğeleri.  
  
     Az olup olmadığını belirlemek bunların <`issuedTokenParameters`> zaten yapılandırmada mevcut bir tercih edilir. Örneğin, bir istemci kullanarak bir Windows Güvenlik belirteci hizmeti için kimlik doğrulaması tercih edebilirsiniz [!INCLUDE[infocard](../../../../includes/infocard-md.md)] yerine bir kullanıcı adı/parola çift belirteci.  
  
    > [!NOTE]
    >  Burada birden çok güvenlik belirteci Hizmetleri hizmet ile iletişim kurmadan önce geçmesi gereken yanlış güvenlik belirteci hizmeti istemcisi yönlendirmek bir ara güvenlik belirteci hizmeti mümkündür. Bu nedenle, güvenlik belirteç hizmeti için uç nokta emin [ \<İssuermetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) beklenen güvenlik belirteci hizmeti ve bir bilinmeyen bir güvenlik belirteci hizmeti değil.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Kodda bir IssuedTokenClientCredential yapılandırmak için  
  
1. Erişim <xref:System.ServiceModel.Security.IssuedTokenClientCredential> aracılığıyla <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> özelliği <xref:System.ServiceModel.Description.ClientCredentials> sınıfı (tarafından döndürülen <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı aracılığıyla veya <xref:System.ServiceModel.ChannelFactory> sınıfı), aşağıdaki örnekte gösterildiği gibi.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Belirteç önbelleğe gerekli değilse, ayarlama <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> özelliğini `false`. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> Özellik denetimleri bu tür bir güvenlik belirteçleri hizmeti olup belirteç önbelleğe alınır. Bu özellik ayarlanırsa `false`, kendisini Federasyon Hizmeti için yeniden kimliğini doğrulaması gerekir her istemci yeni bir belirteç güvenlik belirteci Hizmeti'nden ister, önceki bir belirteç isteyip bakılmaksızın, hala geçerli olduğunu. Bu özellik ayarlanırsa `true`, istemci, her (belirtecin süresinin sona sürece), kendisini Federasyon Hizmeti için yeniden kimliğini doğrulaması gerekir, mevcut bir belirteç yeniden kullanır. Varsayılan, `true` değeridir.  
  
3. Bir süre önbelleğe alınan belirteçleri üzerinde gerekiyorsa ayarlayın <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> özelliğini bir <xref:System.TimeSpan> değeri. Özelliğin ne kadar bir belirteç belirtir önbelleğe alınır. Belirtilen süre geçtikten sonra belirteci istemci önbellekten kaldırılır. Varsayılan olarak, belirteçleri süresiz olarak önbelleğe alınır. Aşağıdaki örnek, zaman aralığı 10 dakika olarak ayarlar.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. İsteğe bağlı. Ayarlama <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> bir yüzde. 60 (yüzde) varsayılandır. Özelliği belirtecin geçerlilik süresi yüzdesini belirtir. Örneğin, 10 saat için verilen belirtecin geçerli olup olmadığını ve <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> belirteç sekiz saat sonra yenilendikten sonra 80 ayarlanır. Aşağıdaki örnek, yüzde 80'i için değeri ayarlar.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Yenileme aralığı belirtecin geçerlilik dönemine göre belirlenir ve `IssuedTokenRenewalThresholdPercentage` değer tarafından geçersiz kılınmıştır `MaxIssuedTokenCachingTime` durumlarda önbelleğe alma süresi olduğu yenileme eşiği süreden daha kısa bir değer. Örneğin, ürün `IssuedTokenRenewalThresholdPercentage` ve belirtecin süresi sekiz saatte bir ve `MaxIssuedTokenCachingTime` değeri 10 dakika, istemci her 10 dakikada güncelleştirilmiş bir belirteci için güvenlik belirteci hizmeti ile iletişim kurar.  
  
5. Dışında bir anahtar entropi modunda değilse <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> ileti güvenliği kullanın veya güvenlik ileti kimlik bilgilerine sahip (örneğin. taşıma üzerindeki bir bağlamaya gereklidir bağlama sahip olmadığı bir <xref:System.ServiceModel.Channels.SecurityBindingElement>) ayarlayın <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> özelliğini uygun bir değer. *Entropi* modu belirler simetrik anahtarlar kullanılarak denetlenir olmadığını <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> özelliği. Bu varsayılan <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>, hem istemci hem de belirteci veren gerçek anahtarı oluşturmak için birleştirilmiş veri sağlarsınız. Diğer değerler <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> ve <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>, tüm anahtarı başka bir deyişle, istemci veya sunucu tarafından sırasıyla belirtilir. Aşağıdaki örnek, anahtarı yalnızca sunucu verileri kullanma özelliğini ayarlar.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    >  Varsa bir <xref:System.ServiceModel.Channels.SecurityBindingElement> bir güvenlik belirteci hizmeti ya da hizmet bağlaması var. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> ayarlamak <xref:System.ServiceModel.Security.IssuedTokenClientCredential> tarafından geçersiz kılınır <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> özelliği `SecurityBindingElement`.  
  
6. Tarafından döndürülen koleksiyonuna ekleyerek issuer özel uç nokta davranışları yapılandırma <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> özelliği.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Yapılandırmada IssuedTokenClientCredential yapılandırmak için  
  
1. Oluşturma bir [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) öğesi alt öğesi olarak [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) öğesinde bir uç nokta davranışı.  
  
2. Belirteç önbelleğe gerekli değilse, ayarlama `cacheIssuedTokens` özniteliği ('ın <`issuedToken`> öğe) için `false`.  
  
3. Bir süre önbelleğe alınan belirteçleri üzerinde gerekiyorsa ayarlayın `maxIssuedTokenCachingTime` özniteliği <`issuedToken`> öğesi için uygun bir değer. Örneğin:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Tercih edilen varsayılan dışında bir değer verilirse `issuedTokenRenewalThresholdPercentage` özniteliği <`issuedToken`> öğesi uygun değeri, örneğin:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. Dışında bir anahtar entropi modunda değilse `CombinedEntropy` kullanım ileti güvenliği veya aktarım güvenlik ileti kimlik bilgileriyle bir bağlaması olduğundan (örneğin, bağlama sahip olmadığı bir `SecurityBindingElement`) ayarlayın `defaultKeyEntropyMode` özniteliği `<issuedToken>` bir ya da öğeye `ServerEntropy` veya `ClientEntropy` gerektiğinde.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. İsteğe bağlı. Oluşturarak tüm veren özgü özel uç nokta davranışı yapılandırmak bir <`issuerChannelBehaviors`> öğesi alt öğesi olarak <`issuedToken`> öğesi. Her davranışı için oluşturmak bir <`add`> öğesi alt öğesi olarak <`issuerChannelBehaviors`> öğesi. Davranış veren adresini belirtmek `issuerAddress` özniteliği <`add`> öğesi. Davranışı belirtmek `behaviorConfiguration` özniteliği <`add`> öğesi.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Kodda bir X509CertificateRecipientClientCredential yapılandırmak için  
  
1. Erişim <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> aracılığıyla <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> özelliği <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı veya <xref:System.ServiceModel.ChannelFactory> özelliği.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. Varsa bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> kullanın, örnek, belirli bir uç noktası için sertifika kullanılabilir <xref:System.Collections.Generic.ICollection%601.Add%2A> yöntemi tarafından döndürülen koleksiyon <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> özelliği.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Varsa bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> örneği kullanılabilir değil, kullanın <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> aşağıdaki örnekte gösterildiği gibi sınıf.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Yapılandırmada bir X509CertificateRecipientClientCredential yapılandırmak için  
  
1. Oluşturma bir [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) öğesi alt öğesi olarak [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) kendisi bir alt öğesi olan öğeyi [ \< clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesinde bir uç nokta davranışı.  
  
2. Oluşturma bir `<add>` öğesi alt öğesi olarak `<scopedCertificates>` öğesi. İçin değerler belirtin `storeLocation`, `storeName`, `x509FindType`, ve `findValue` uygun sertifika için başvurmak için öznitelikler. Ayarlama `targetUri` özniteliği aşağıdaki örnekte gösterildiği gibi kullanılacak sertifika olan uç nokta adresini sağlayan bir değer.  
  
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
 Aşağıdaki kod örneği bir örneğini yapılandırır <xref:System.ServiceModel.Security.IssuedTokenClientCredential> kod sınıfı.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Olası bilgilerin açığa çıkmasını önlemek için Federasyon uç noktalarından meta verileri işlemek için Svcutil.exe aracını çalıştıran istemcilerde ne bekledikleri elde edilen güvenlik belirteci hizmeti adresleri olduğundan emin olun. Birden fazla uç noktası, bir güvenlik belirteci hizmeti sunan, Svcutil.exe aracını ilk kullanmak için elde edilen yapılandırma dosyası oluşturur. Bu özellikle önemlidir çünkü böyle endpoint istemci kullanarak olmayabilir.  
  
## <a name="localissuer-required"></a>Gerekli LocalIssuer  
 İstemcileri her zaman yerel yayımlayan kullanacak şekilde bekleniyorsa, aşağıdakilere dikkat edin: varsayılan çıkış Svcutil.exe sonuçlarının yerel sertifika verenin zincirinde ikinci en son güvenlik belirteci hizmeti veren adres veya sertifikayı verenin meta veri adresi belirtiyorsa kullanılmıyor.  
  
 Ayar hakkında daha fazla bilgi için <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>, ve <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> özelliklerini <xref:System.ServiceModel.Security.IssuedTokenClientCredential> sınıfı [nasıl yapılır: Yerel yayımlayan yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Kapsamlı sertifikalar  
 Herhangi bir güvenlik belirteci Hizmetleri ile iletişim kurmak için hizmet sertifikaları belirtilmesi gerekir, sertifika anlaşma kullanılmayan olduğundan, genellikle bunlar kullanılarak belirtilebilir <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> özelliği <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> sınıfı. <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> Yöntemi bir <xref:System.Uri> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> parametre olarak. Belirtilen sertifika belirtilen URI'de uç noktaları ile iletişim kurarken kullanılır. Alternatif olarak, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> yöntemi tarafından döndürülen bir koleksiyonda bir sertifika eklemek için <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> özelliği.  
  
> [!NOTE]
>  Belirtilen URI'yı kapsayan sertifikalar istemci fikrini uç noktada bu bir URI'leri açığa çıkaran hizmetler giden çağrıları yapan uygulamalar için geçerlidir. Tarafından döndürülen bir koleksiyonda sunucuda yapılandırılan gibi verilen Belirteçleri imzalamak için kullanılan sertifikaları için uygulanmaz <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> , <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> sınıfı. Daha fazla bilgi için [nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: WSFederationHttpBinding Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Nasıl yapılır: Yerel Yayımlayan Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
