---
title: "Nasıl yapılır: Federe İstemci Oluşturma"
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
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fda534d591ae5142fb732607c7e248ef3cc71bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-federated-client"></a>Nasıl yapılır: Federe İstemci Oluşturma
İçinde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], bir istemci için oluşturma bir *Federasyon Hizmeti* üç ana adımdan oluşur:  
  
1.  Yapılandırma bir [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ya da benzer özel bağlama. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]uygun bir bağlama bkz [nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Alternatif olarak, çalıştırın [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Federasyon Hizmeti ve bir veya daha fazla ile iletişim için bir yapılandırma dosyası oluşturmak için Federasyon Hizmeti meta veri uç noktası Güvenlik belirteci Hizmetleri.  
  
2.  Özellik kümesinin <xref:System.ServiceModel.Security.IssuedTokenClientCredential> bir güvenlik belirteci hizmeti ile bir istemcinin etkileşimi çeşitli yönlerini denetler.  
  
3.  Özellik kümesinin <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>, güvenli bir şekilde belirli bir güvenlik belirteci Hizmetleri gibi uç noktaları iletişim kurması için gerekli sertifikaları izin verir.  
  
> [!NOTE]
>  A <xref:System.Security.Cryptography.CryptographicException> istemci kimliğine bürünülen kimlik bilgileri kullandığında oluşturulan <xref:System.ServiceModel.WSFederationHttpBinding> bağlama veya özel tarafından verilen bir belirteç ve asimetrik anahtarlar. Asimetrik anahtarlar ile kullanılan <xref:System.ServiceModel.WSFederationHttpBinding> bağlama ve özel verilen ne zaman belirteçler <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> ve <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> özellikleri, sırasıyla ayarlandığında <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>. <xref:System.Security.Cryptography.CryptographicException> Bir ileti göndermek istemci çalışır ve bir kullanıcı profili için istemci kimliğine bürünme kimlik yok zaman oluşturulur. Bu sorunu azaltmak için oturum açın istemci bilgisayarı veya çağrı `LoadUserProfile` iletiyi göndermeden önce.  
  
 Bu konu, bu yordamları hakkında ayrıntılı bilgi sağlar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]uygun bir bağlama bkz [nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Federasyon hizmetinin çalıştığı bkz [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Oluştur ve bir Federasyon Hizmeti için yapılandırma incelemek için  
  
1.  Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet komut satırı parametresi olarak meta veri URL'sini adresine sahip.  
  
2.  Oluşturulan yapılandırma dosyasını uygun bir düzenleyicide açın.  
  
3.  Öznitelikler ve içerik herhangi oluşturulan inceleyin [ \<veren >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) ve [ \<İssuedtokenparameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) öğeleri. Bunlar içinde bulunan [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) için öğeleri [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya özel bağlama öğeleri. Adresleri beklenen etki alanı adlarını veya diğer adres bilgilerini içerdiğinden emin olun. İstemci bu adreslere kimliğini doğrular ve kullanıcı adı/parola çiftleri gibi bilgileri açıklayabilir çünkü bu bilgileri denetlemek önemlidir. Adresi beklenen adres değilse, bu istenmeyen bir alıcıya bilginin açığa çıkmasına neden olabilir.  
  
4.  Ek inceleyin [ \<İssuermetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) açıklamalı içinde öğeleri çıkışı <`alternativeIssuedTokenParameters`> öğesi. Federe hizmet veya Ara güvenlik belirteci hizmetlerin bir veren adresi belirtmeyin, ancak bunun yerine kullanıma sunan bir güvenlik belirteci hizmeti için bir meta veri adresi belirtin, Federasyon Hizmeti için yapılandırma oluşturmak için Svcutil.exe aracını kullanırken birden çok uç nokta, sonuçta elde edilen yapılandırma dosyasının ilk uç noktasına başvurur. Ek noktalarıdır kılınan olarak yapılandırma dosyasında <`alternativeIssuedTokenParameters`> öğeleri.  
  
     Bir olup olmadığını belirlemek bunların <`issuedTokenParameters`> yapılandırmada zaten mevcut bir tercih edilir. Örneğin, istemci bir Windows kullanarak bir güvenlik belirteci hizmeti için kimlik doğrulaması tercih edebilirsiniz [!INCLUDE[infocard](../../../../includes/infocard-md.md)] yerine bir kullanıcı adı/parola çifti belirteci.  
  
    > [!NOTE]
    >  Burada birden çok güvenlik belirteci Hizmetleri hizmeti ile iletişim kurmadan önce geçmesi gereken yanlış güvenlik belirteci hizmeti istemciye yönlendirmek bir ara güvenlik belirteci hizmeti mümkündür. Bu nedenle, güvenlik belirteci Hizmeti uç noktasının emin [ \<İssuermetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) beklenen güvenlik belirteci hizmeti ve bir bilinmeyen bir güvenlik belirteci hizmeti değil.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Kodda bir IssuedTokenClientCredential yapılandırmak için  
  
1.  Erişim <xref:System.ServiceModel.Security.IssuedTokenClientCredential> aracılığıyla <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> özelliği <xref:System.ServiceModel.Description.ClientCredentials> sınıfı (tarafından döndürülen <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı aracılığıyla veya <xref:System.ServiceModel.ChannelFactory> sınıfı), aşağıdaki örnek kodda gösterildiği gibi.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2.  Belirteç önbelleğe alma gerekli değilse, ayarlamak <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> özelliğine `false`. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> Özellik denetimleri olup olmadığı gibi güvenlik belirteçlerinden hizmet belirteci önbelleğe alınır. Bu özellik ayarlanmışsa `false`, istemci, kendisi için Federasyon Hizmeti yeniden kimlik doğrulaması gerekir her güvenlik belirteci Hizmeti'nden yeni bir belirteç ister, ne olursa olsun, önceki bir belirteç isteyip hala geçerli olduğu. Bu özellik ayarlanmışsa `true`, (belirtecin süresi geçmemiş sürece), kendisi için Federasyon Hizmeti yeniden kimlik doğrulaması gerekir her istemci varolan bir belirteci yeniden kullanır. Varsayılan, `true` değeridir.  
  
3.  Bir süre önbelleğe alınmış simgelerinde gerekiyorsa ayarlayın <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> özelliğine bir <xref:System.TimeSpan> değeri. Özellik ne kadar bir belirteç belirtir önbelleğe alınmış. Belirtilen süre geçtikten sonra belirteç istemci önbelleğinden kaldırılır. Varsayılan olarak, belirteçleri süresiz olarak önbelleğe alınır. Aşağıdaki örnek süresi 10 dakika olarak ayarlar.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4.  İsteğe bağlı. Ayarlama <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> bir yüzde. Varsayılan değer 60 (yüzde) ' dir. Özelliği belirtecin geçerlilik süresi yüzdesini belirtir. Örneğin, 10 saat için verilen belirtecin geçerli olup olmadığını ve <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> belirteç sekiz saat sonra yenilendikten sonra 80 ayarlanır. Aşağıdaki örnek, yüzde 80'için değeri ayarlar.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Belirteç geçerlilik süresi tarafından belirlenen yenileme aralığı ve `IssuedTokenRenewalThresholdPercentage` değer tarafından geçersiz kılınmış `MaxIssuedTokenCachingTime` önbelleğe alma süresi olduğu yenileme eşiği saatten kısa durumlarda değeri. Örneğin, varsa çarpımını `IssuedTokenRenewalThresholdPercentage` ve belirtecin süresi sekiz saat ve `MaxIssuedTokenCachingTime` değer 10 dakika, istemci her 10 dakikada bir güncelleştirilmiş belirteci için güvenlik belirteci hizmeti kurar.  
  
5.  Bir anahtar entropi mod dışında <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> ileti güvenliği kullanın veya (örneğin, aktarım güvenliği ileti kimlik bilgilerine sahip bir bağlama gereklidir bağlama sahip olmayan bir <xref:System.ServiceModel.Channels.SecurityBindingElement>) ayarlayın <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> uygun bir değere özelliği. *Entropi* modunu belirler simetrik anahtarlar kullanılarak denetlenir olup olmadığını <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> özelliği. Bu varsayılandır <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>, burada hem istemci hem de Belirteç Verenin gerçek anahtarı üretmek için birleşik veriler sağlar. Diğer değerler <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> ve <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>, anahtarın tamamının başka bir deyişle, istemci veya sunucu tarafından sırasıyla belirtilir. Aşağıdaki örnek anahtarı için kullanılacak özelliği yalnızca sunucu verilerini ayarlar.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    >  Varsa bir <xref:System.ServiceModel.Channels.SecurityBindingElement> bir güvenlik belirteci hizmeti ya da hizmet bağlama mevcut <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> ayarlamak <xref:System.ServiceModel.Security.IssuedTokenClientCredential> tarafından geçersiz kılınır <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> özelliği `SecurityBindingElement`.  
  
6.  Tarafından döndürülen koleksiyonuna ekleyerek veren özgü endpoint davranışları yapılandırmak <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> özelliği.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Yapılandırmada IssuedTokenClientCredential yapılandırmak için  
  
1.  Oluşturma bir [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) öğesi bir alt öğesi olarak [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) bir uç noktası davranışı öğesinde.  
  
2.  Belirteç önbelleğe alma gerekli değilse, ayarlamak `cacheIssuedTokens` özniteliği (biri <`issuedToken`> öğesi) için `false`.  
  
3.  Bir süre önbelleğe alınmış simgelerinde gerekiyorsa ayarlayın `maxIssuedTokenCachingTime` özniteliği <`issuedToken`> öğesi için uygun bir değer. Örneğin:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4.  Varsayılan dışında bir değer tercih edilen ise `issuedTokenRenewalThresholdPercentage` özniteliği <`issuedToken`> öğesi örnek için uygun bir değere:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5.  Anahtar entropi mod dışında `CombinedEntropy` kullanım ileti güvenliği veya taşıma güvenliği ileti kimlik bilgilerine sahip olmayan bir bağlaması olduğundan (örneğin, bağlama sahip olmayan bir `SecurityBindingElement`) ayarlayın `defaultKeyEntropyMode` özniteliği `<issuedToken>` bir ya da öğesine `ServerEntropy` veya `ClientEntropy` gerektiği gibi.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6.  İsteğe bağlı. Oluşturarak tüm veren özgü özel uç noktası davranışı yapılandırmak bir <`issuerChannelBehaviors`> öğesi bir alt öğesi olarak <`issuedToken`> öğesi. Her davranışı için oluşturmak bir <`add`> öğesi bir alt öğesi olarak <`issuerChannelBehaviors`> öğesi. Davranış veren adresini ayarlayarak belirtin `issuerAddress` özniteliği <`add`> öğesi. Ayarlayarak davranışı belirtmek `behaviorConfiguration` özniteliği <`add`> öğesi.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Kodda bir X509CertificateRecipientClientCredential yapılandırmak için  
  
1.  Erişim <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> aracılığıyla <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> özelliği <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı veya <xref:System.ServiceModel.ChannelFactory> özelliği.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2.  Varsa bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> örneği için sertifikanın belirli bir uç noktası için kullanılabilir, kullanın <xref:System.Collections.Generic.ICollection%601.Add%2A> yöntemi tarafından döndürülen koleksiyonunun <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> özelliği.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3.  Varsa bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> örneği kullanılabilir değil, kullanın <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> sınıfı aşağıdaki örnekte gösterildiği gibi.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Yapılandırmada bir X509CertificateRecipientClientCredential yapılandırmak için  
  
1.  Oluşturma bir [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) öğesi bir alt öğesi olarak [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) kendisini bir alt öğesi olan öğeyi [ \< clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) bir uç noktası davranışı öğesinde.  
  
2.  Oluşturma bir `<add>` öğesi bir alt öğesi olarak `<scopedCertificates>` öğesi. İçin değerler belirten `storeLocation`, `storeName`, `x509FindType`, ve `findValue` uygun sertifika başvurmak için öznitelikler. Ayarlama `targetUri` özniteliği aşağıdaki örnekte gösterildiği gibi kullanılacak sertifika olan uç noktası adresi sağlayan bir değer.  
  
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
 Aşağıdaki kod örneği örneği yapılandırır <xref:System.ServiceModel.Security.IssuedTokenClientCredential> kodda sınıfı.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Olası bilgilerin açığa çıkmasını önlemek için Federasyon uç noktaları meta verilerini işlemek için Svcutil.exe aracını çalıştıran istemciler ortaya çıkan güvenlik belirteci hizmeti adresleri ne bekledikleri emin olun. Birden fazla uç noktası, bir güvenlik belirteci hizmeti sunan Svcutil.exe aracı ilk kullanmak için sonuçta elde edilen yapılandırma dosyasını oluşturduğundan bu özellikle önemlidir istemci kullanarak olmayabilir böyle uç noktası.  
  
## <a name="localissuer-required"></a>Gerekli LocalIssuer  
 İstemciler her zaman yerel yayımlayan kullan beklenir, aşağıdakilere dikkat edin: ikinci en son güvenlik belirteci hizmeti zincirde bir veren adresi veya veren meta veri adresi belirtiyorsa kullanılmayan yerel yayımlayan Svcutil.exe sonuçlarında varsayılan çıktısı.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ayarı <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>, ve <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> özelliklerini <xref:System.ServiceModel.Security.IssuedTokenClientCredential> sınıfı için bkz: [nasıl yapılır: yerel yayımlayan yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Kapsamlı sertifikaları  
 Herhangi bir güvenlik belirteci Hizmetleri ile iletişim kurmak için hizmet sertifikaları belirtilmelidir, sertifikası anlaşması kullanılmaması nedeni genellikle bunlar kullanılarak belirtilebilir <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> özelliği <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> sınıfı. <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> Metodu bir <xref:System.Uri> ve bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> parametre olarak. Belirtilen sertifika belirtilen URI'sine uç noktalar ile iletişim kurarken kullanılır. Alternatif olarak, kullanabileceğiniz <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> yöntemi tarafından döndürülen koleksiyonu için bir sertifika eklemek için <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> özelliği.  
  
> [!NOTE]
>  Verili URI için kapsamlı sertifikaları istemci fikrini yalnızca Uç noktalara bu URI kullanıma hizmetlerine giden çağrıları yapma uygulamalar için geçerlidir. Tarafından döndürülen toplama sunucusuna yapılandırılanlar gibi verilen Belirteçleri imzalamak için kullanılan sertifikaları uygulanmaz <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> , <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> sınıfı. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: federe bir hizmette kimlik bilgilerini yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Nasıl yapılır: WSFederationHttpBinding Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Nasıl yapılır: Yerel Yayımlayan Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
