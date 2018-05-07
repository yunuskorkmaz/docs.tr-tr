---
title: WCF'de Güvenlik Davranışları
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 57bd34c72e98091c4a429d683a0da4ce2d3967c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-behaviors-in-wcf"></a>WCF'de Güvenlik Davranışları
Windows Communication Foundation (WCF) davranışlar çalışma zamanı davranışını hizmet düzeyinde veya uç nokta düzeyine değiştirin. (Genel olarak, davranışları hakkında daha fazla bilgi için bkz [hizmet çalışma zamanı davranışını belirtme](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Güvenlik davranışları* kimlik bilgileri, kimlik doğrulama, yetkilendirme denetime izin vermek ve günlükleri denetleme. Programlama ile veya yapılandırma yoluyla davranışları kullanabilirsiniz. Bu konuda, güvenlik işlevleri ile ilgili aşağıdaki davranışları yapılandırma üzerinde durulmaktadır:  
  
-   [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
-   [\<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
-   [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
-   [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
-   [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md), hangi Ayrıca istemciler için meta verileri erişimi güvenli bir uç nokta belirtmenize olanak sağlar.  
  
## <a name="setting-credentials-with-behaviors"></a>Davranışlarla kimlik bilgilerini ayarlama  
 Kullanım [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ve [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) bir hizmet veya istemci kimlik bilgileri değerlerini ayarlamak için. Temel bağlama yapılandırması bir kimlik bilgisi ayarlanmış olup olmadığını belirler. Örneğin, güvenlik modu ayarlanmışsa `None`, istemciler ve hizmetler değil birbirinin kimliğini doğrular ve herhangi bir türde kimlik bilgisi gerektirir.  
  
 Diğer taraftan, hizmet bağlama bir istemci kimlik bilgisi türü gerektirebilir. Bu durumda, bir davranış kullanarak bir kimlik bilgisi değeri ayarlamanız gerekebilir. (Kimlik bilgilerinin olası türleri hakkında daha fazla bilgi için bkz: [bir kimlik bilgisi türü seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Windows kimlik bilgileri kimlik doğrulaması için kullanıldığında gibi bazı durumlarda, ortam gerçek kimlik bilgisi değeri otomatik olarak oluşturur ve (farklı kimlik bilgileri kümesi belirtmek istemediğiniz sürece) kimlik bilgisi değeri açıkça ayarlanmış gerekmez.  
  
 Tüm hizmet kimlik bilgilerini alt öğeleri olarak bulunan [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Aşağıdaki örnek, bir hizmeti kimlik bilgileri kullanılan bir sertifika gösterir.  
  
```xml  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"   
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="service-credentials"></a>Hizmeti kimlik bilgileri  
 [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) dört alt öğeleri içerir. Öğeleri ve kullanımlarının aşağıdaki bölümlerde ele alınmıştır.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate > öğesi  
 İleti güvenlik modunu kullanarak istemcilere hizmet kimliğini doğrulamak için kullanılan bir X.509 sertifikasını belirtmek için bu öğeyi kullanın. Düzenli aralıklarla olan bir sertifikayı kullanıyorsanız, yenileme, ardından parmak izi değişikliklerin. Bu durumda konu adı olarak kullanın `X509FindType` sertifika ile aynı konu adı verilmesi için.  
  
 Öğe kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: istemci kimlik bilgileri değerlerini belirtme](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<Sertifika >, \<clientCertificate > öğesi  
 Kullanım [ \<sertifika >](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) öğesi hizmeti istemcisi ile önceden güvenli bir şekilde iletişim kurmak için istemci sertifikasını sahip olmalıdır. Bu, çift yönlü iletişim düzeni kullanırken oluşur. Daha tipik istek-yanıt desende istemci sertifikasını istemciye yanıt güvenliğini sağlamak için hizmeti kullanır istekte içerir. Çift yönlü iletişim düzeni, ancak hiçbir istekleri ve yanıtları vardır. Hizmet iletişim istemci sertifikasının gösterilemez ve bu nedenle hizmet önceden istemci iletileri güvenli hale getirmek için istemci sertifikasını gerektirir. İstemci sertifikasının bir bant dışı şekilde edinmeli ve bu öğe kullanarak sertifikayı belirtin. Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<kimlik doğrulama >, \<clientCertificate > öğesi  
 [ \<Kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) öğeleri nasıl istemcilerinin kimlik doğrulamalarının özelleştirmenize olanak sağlar. Ayarlayabileceğiniz `CertificateValidationMode` özniteliğini `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, veya `Custom`. Varsayılan olarak, düzeyini ayarlamak `ChainTrust`, belirten her sertifika biten sertifika hiyerarşisini bulunması gereken bir *kök yetkilisi* zincirinin üstünde. Bu en güvenli bir moddur. De değer ayarlayabilirsiniz `PeerOrChainTrust`, kendi kendine verilen sertifikaların (eş güven) güvenilen zincirinde sertifikaları yanı sıra kabul edileceğini belirtir. Bu değer, geliştirme ve kendi kendine verilen sertifikaların güvenilir bir yetkiliden satın alınması değil çünkü hata ayıklama istemcileri ve Hizmetleri zaman kullanılır. Bir istemci dağıtımı sırasında kullanmak `ChainTrust` yerine değer. De değer ayarlayabilirsiniz `Custom`. Ayarlandığında `Custom` değeri de ayarlamanız gerekir `CustomCertificateValidatorType` özniteliği bir derleme ve sertifikayı doğrulamak için kullanılan türü. Kendi özel Doğrulayıcısı oluşturmak için Özet devralmalıdır <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication > öğesi  
 Verilen belirteç senaryo üç aşamadan oluşur. İlk aşamada, bir hizmet erişmeye çalışan istemci bilinir bir *güvenli belirteç hizmeti* (STS). STS istemcinin kimliğini doğrular ve bundan sonra istemci genellikle bir güvenlik onaylar biçimlendirme dili (SAML) belirteci bir belirteç verir. İstemci ardından belirteci ile hizmetine döndürür. Hizmet belirteci ve bu nedenle istemci kimliğini doğrulamak hizmet veren veriler için belirteç inceler. Belirteç kimlik doğrulaması için güvenli belirteç hizmeti kullandığı sertifikayı hizmete bilinmesi gerekir. [ \<İssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) depo böyle herhangi bir güvenli belirteç hizmeti sertifika için bir öğedir. Sertifika eklemek için kullanın [ \<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). INSERT bir [ \<Ekle >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) aşağıdaki örnekte gösterildiği gibi her sertifika için.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Varsayılan olarak, sertifikaları güvenli bir belirteci Hizmeti'nden alınması gerekir. Bu ", istemciler yalnızca yasal olun sertifikaları bilinen" hizmet erişebilir.  
  
 Kullanmanız gereken [ \<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) yararlanan bir federasyon uygulaması koleksiyonda bir *güvenli belirteç hizmeti* (STS) sorunları `SamlSecurityToken` güvenlik belirteçleri. Güvenlik belirteci STS gönderdiğinde, kendisi için güvenlik belirteci amaçlanmıştır ekleyerek Web Hizmetleri URI'sini belirtebilirsiniz bir `SamlAudienceRestrictionCondition` için güvenlik belirteci. İzin veren `SamlSecurityTokenAuthenticator` verilen güvenlik belirteci bu Web hizmeti için bu onay aşağıdakileri yaparak olacağını belirterek hedeflenen doğrulamak alıcı Web hizmeti için:  
  
-   Ayarlama `audienceUriMode` özniteliği [ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) için `Always` veya `BearerKeyOnly`.  
  
-   Bu koleksiyona URI'ler ekleyerek geçerli URI'ler kümesini belirtin. Bunu yapmak için INSERT bir [ \<Ekle >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) her URI  
  
 Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgileri yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Anonim CardSpace kullanıcılar izin verme  
 Ayarı `AllowUntrustedRsaIssuers` özniteliği `<IssuedTokenAuthentication>` öğesine `true` açıkça rasgele bir RSA anahtar çifti ile imzalanmış otomatik olarak verilen bir belirteç sunmak herhangi bir istemci sağlar. Veren *güvenilmeyen* ilişkili veren veri anahtara sahip olduğundan. A [!INCLUDE[infocard](../../../../includes/infocard-md.md)] kullanıcı, kendi kendine sağlanan talep kimliğini içerir kendini yayınlayan bir kart oluşturabilirsiniz. Bu özellik dikkatli kullanın. Bu özelliği kullanmak için RSA ortak anahtarı bir kullanıcı adı ile birlikte bir veritabanında depolanması daha güvenli bir parola olarak düşünün. Bir istemci erişim hizmetine izin vermeden önce istemci sunulan RSA ortak anahtar sunulan kullanıcı adı için depolanan ortak anahtar ile karşılaştırarak doğrulayın. Bu, kullanıcılar kullanıcı adlarını kaydedebilir ve kendi kendine verilen RSA ortak anahtarlarla ilişkilendirme alınabildiği bir kayıt işlemi kurulan varsayar.  
  
## <a name="client-credentials"></a>İstemci kimlik bilgileri  
 İstemci kimlik bilgileri, karşılıklı kimlik doğrulaması gerekli olduğu durumlarda Hizmetleri için istemci kimlik doğrulaması için kullanılır. Bölümü, istemci Hizmeti'ne hizmetin sertifikayla iletileri burada güvenlik altına almanız gerekir senaryolar için hizmet sertifikaları belirtmek için kullanabilirsiniz.  
  
 Ayrıca bir istemci Federasyon senaryosunun bir parçası verilen kullanım belirteçleri güvenli belirteç hizmeti veya yerel yayımlayan belirteçlerin yapılandırabilirsiniz. Federasyon senaryoları hakkında daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Tüm istemci kimlik bilgileri altında bulunan [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)aşağıdaki kodda gösterildiği gibi.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"     
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"   
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
#### <a name="clientcertifictate-element"></a>\<clientCertifictate > öğesi  
 Bu öğe ile istemci kimlik doğrulaması için kullanılan sertifikayı ayarlayın. Daha fazla bilgi için bkz: [nasıl yapılır: istemci kimlik bilgileri değerlerini belirtme](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest >  
 Bu özellik, Windows ve Internet Information Services (IIS) üzerinde Active Directory ile etkinleştirilmelidir. Daha fazla bilgi için bkz: [IIS 6.0 Özet kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkId=88443).  
  
#### <a name="issuedtoken-element"></a>\<IssuedToken > öğesi  
 [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) belirteçleri veya güvenlik belirteci hizmeti ile kullanılan davranışlar yerel yayımlayan yapılandırma için kullanılan öğeleri içerir. Yerel yayımlayan kullanmak bir istemci yapılandırma yönergeleri için bkz: [nasıl yapılır: yerel yayımlayan yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress >  
 Varsayılan bir güvenlik belirteci hizmeti adresi belirtir. Bu kullanılan zaman <xref:System.ServiceModel.WSFederationHttpBinding> bir URL veya güvenlik belirteci hizmeti için Federasyon bağlaması veren adresi olduğunda sağlamıyor http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous veya `null`. Böyle durumlarda, <xref:System.ServiceModel.Description.ClientCredentials> adresi bu veren ile iletişim kurmak için kullanılacak yerel yayımlayan ve bağlama ile yapılandırılması gerekir.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors >  
 Kullanım [ \<issuerChannelBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) bir güvenlik belirteci hizmeti ile iletişim kurarken kullanılan WCF istemci davranışlarını eklemek için. İstemci davranışlarını tanımlamak [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) bölümü. Tanımlanan bir davranış kullanmak için ekleyin bir <`add`> öğesine `<issuerChannelBehaviors>` iki özniteliklerle öğesi. Ayarlama `issuerAddress` kümesi ve güvenlik belirteci hizmeti URL'sini `behaviorConfiguration` aşağıdaki örnekte gösterildiği gibi tanımlanmış uç noktası davranışı adına özniteliği.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate > öğesi  
 Hizmet sertifikaları denetim kimlik doğrulaması için bu öğeyi kullanın.  
  
 [ \<DefaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) öğesi hizmeti sertifika belirttiğinde kullanılan tek bir sertifika depolayabilir.  
  
 Kullanım [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) ve [ \<Ekle >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) belirli hizmetleri ile ilişkilendirilmiş hizmet sertifikaları ayarlamak için. `<add>` Öğesi içeren bir `targetUri` sertifika hizmeti ile ilişkilendirmek için kullanılan öznitelik.  
  
 [ \<Kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) öğesi sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir. Varsayılan olarak, "her sertifika zinciri üstündeki bir güvenilen sertifika yetkilisi biten sertifikaların bir hiyerarşideki bulunması gereken belirten ChainTrust," düzeyinde ayarlanır. Bu en güvenli bir moddur. Ayrıca, bir güvenilen zincirindeki sertifikaları yanı sıra kendi kendine verilen sertifikaların (eş güven) kabul edileceğini belirtir, "PeerOrChainTrust" değerine ayarlayabilirsiniz. Bu değer, geliştirme ve kendi kendine verilen sertifikaların güvenilir bir yetkiliden satın alınması değil çünkü hata ayıklama istemcileri ve Hizmetleri zaman kullanılır. Bir istemci dağıtımı sırasında bunun yerine "ChainTrust" değeri kullanın. "Özel" veya "None" değerine de ayarlayabilirsiniz "Özel" değerini kullanmak için de ayarlamalısınız `CustomCertificateValidatorType` özniteliği bir derleme ve sertifikayı doğrulamak için kullanılan türü. Kendi özel Doğrulayıcısı oluşturmak için Özet devralmalıdır <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı. Daha fazla bilgi için bkz: [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [ \<Kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) öğesi içeren bir `RevocationMode` sertifika iptali için nasıl denetlenir belirten özniteliği. Sertifikaları iptal edilmek üzere otomatik olarak denetlenir belirten "çevrimiçi" varsayılandır. Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [ \<ServiceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) öğesi yetkilendirme, özel rol sağlayıcıları ve kimliğe bürünme etkileyen öğeleri içerir.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Sınıfı, bir hizmet yöntemi uygulanır. Öznitelik, korumalı bir yöntemin kullanılması yetkilendirirken kullanmak için kullanıcı gruplarını belirtir. Varsayılan değer "UseWindowsGroups" ve "Yöneticiler" veya "Kullanıcı" gibi Windows grupları için bir kaynağa erişmeye çalışırken bir kimlik aranır belirtir. Ayrıca, "UseAspNetRoles" belirtebilirsiniz altında yapılandırılmış bir özel rol sağlayıcıyı kullanacak şekilde <`system.web` > aşağıdaki kodda gösterildiği gibi öğesi.  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 Aşağıdaki kodda gösterildiği `roleProviderName` ile kullanılan `principalPermissionMode` özniteliği.  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">          
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                        roleProviderName ="SqlProvider" />  
</behavior>   
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>Güvenlik denetimleri yapılandırma  
 Kullanım [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) yazılan günlük ve ne belirtmek için olayları günlük türleri. Daha fazla bilgi için bkz: [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
```xml  
<system.serviceModel>  
<serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="secure-metadata-exchange"></a>Güvenli meta veri değişimi  
 İstemciler için meta verileri dışarı aktarma yüklemelerinin yapılandırma ve istemci kodunun gibi hizmet ve istemci geliştiriciler için uygundur. Kötü niyetli kullanıcılar için bir hizmet riskini azaltmak için Güvenli HTTP (HTTPS) mekanizması üzerinde SSL kullanılarak aktarım mümkündür. Bunu yapmak için önce uygun bir X.509 sertifikası hizmetini barındıran bilgisayarda belirli bir bağlantı noktası bağlamanız gerekir. (Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) İkinci olarak, ekleme bir [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) hizmet yapılandırmasını ve kümesi `HttpsGetEnabled` özniteliğini `true`. Son olarak, ayarlamak `HttpsGetUrl` aşağıdaki örnekte gösterildiği gibi hizmet meta veri uç noktasının URL'sini özniteliği.  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"   
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
