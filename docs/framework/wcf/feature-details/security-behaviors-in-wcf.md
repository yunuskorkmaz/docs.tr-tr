---
title: WCF'de Güvenlik Davranışları
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 378edb6ddd7a66249a0c7548a3d9465475f670a8
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487755"
---
# <a name="security-behaviors-in-wcf"></a>WCF'de Güvenlik Davranışları
Windows Communication Foundation (WCF) davranışlar çalışma zamanı davranışını hizmet düzeyinde veya uç nokta düzeyine değiştirin. (Genel olarak, davranışları hakkında daha fazla bilgi için bkz [hizmet çalışma zamanı davranışını belirtme](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Güvenlik davranışları* kimlik bilgileri, kimlik doğrulaması, yetkilendirme denetime izin vermek ve günlüklerini denetleme. Programlama veya yapılandırma yoluyla davranışları kullanabilirsiniz. Bu konu, aşağıdaki davranışları güvenlik işlevleri için ilgili yapılandırma üzerinde durulmaktadır:  
  
- [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
- [\<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
- [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
- [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
- [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md), hangi de istemciler için meta verileri erişimi güvenli bir uç nokta belirtmenize imkan tanır.  
  
## <a name="setting-credentials-with-behaviors"></a>Davranışlarla kimlik bilgilerini ayarlama  
 Kullanım [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ve [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) hizmet veya istemci kimlik bilgileri değerlerini ayarlamak için. Temel bağlama yapılandırması, bir kimlik bilgisi ayarlamak uygun olup olmadığını belirler. Örneğin, güvenlik modunu ayarlama `None`, hem istemci hem de Hizmetleri değil doğrulaması ve herhangi bir türde herhangi bir kimlik bilgisi gerektirir.  
  
 Öte yandan, hizmet bağlaması, istemci kimlik bilgisi türü gerektirebilir. Bu durumda, davranış kullanarak bir kimlik bilgisi değeri ayarlamanız gerekebilir. (Kimlik bilgileri olası türleri hakkında daha fazla bilgi için bkz. [kimlik bilgisi türü seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Windows kimlik bilgilerini doğrulamak için kullanıldığında gibi bazı durumlarda, ortam gerçek kimlik değeri otomatik olarak oluşturur ve kimlik bilgisi değeri (farklı bir kimlik bilgileri kümesi belirtmek istemediğiniz sürece) açık olarak gerekmez.  
  
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
  
## <a name="service-credentials"></a>Hizmet kimlik bilgileri  
 [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) dört alt öğeleri içerir. Öğeleri ve kullanımlarının aşağıdaki bölümlerde ele alınmıştır.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate > öğesi  
 İleti güvenlik modunu kullanarak istemcilere hizmet kimliğini doğrulamak için kullanılan bir X.509 sertifikasını belirtmek için bu öğeyi kullanırsınız. Düzenli aralıklarla bir sertifika kullanıyorsanız yenilenmesi, ardından kendi parmak izi değişiklikleri. Bu durumda, konu adı olarak kullanmak `X509FindType` sertifika ile aynı konu adı verilmesi için.  
  
 Öğe kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: İstemci kimlik bilgileri değerlerini belirtme](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<Sertifika >, \<clientCertificate > öğesi  
 Kullanım [ \<sertifika >](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) öğesi hizmet istemcisi ile önceden güvenli şekilde iletişim kurması için istemci sertifikasını sahip olmalıdır. Bu, çift yönlü iletişim deseni kullanırken gerçekleşir. Daha tipik istek-yanıt düzende, istemci sertifikasını istemciye yanıtına güvenliğini sağlamak için hizmeti kullanır isteğindeki içerir. Çift yönlü iletişim deseni, ancak hiçbir istek ve yanıtları sahiptir. Hizmet iletişim istemci sertifikasının çıkarsanamıyor ve bu nedenle hizmet önceden istemciye iletileri güvenli hale getirmek için istemci sertifikasını gerektirir. Bir bant dışı şekilde istemci sertifikası alın ve bu öğenin kullanarak sertifikayı belirtmeniz gerekir. Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<kimlik doğrulama >, \<clientCertificate > öğesi  
 [ \<Kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) öğesi, istemci kimliklerinin nasıl özelleştirmenize olanak sağlar. Ayarlayabileceğiniz `CertificateValidationMode` özniteliğini `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, veya `Custom`. Varsayılan olarak, düzeyini ayarlamak `ChainTrust`, belirten her sertifika sonu sertifika hiyerarşisini bulunması gereken bir *kök yetkilisi* zinciri üstünde. En güvenli mod budur. De değer ayarlayabilirsiniz `PeerOrChainTrust`, kendi kendine verilen sertifikaların (eş güven) güvenilen bir zinciri olan sertifikaları yanı sıra kabul edildiğini belirtir. Bu değer, geliştirme ve istemciler ve hizmetler kendi kendine verilen sertifikaların güvenilir yetkilisinden satın alınması değil çünkü hata ayıklama kullanılır. Bir istemci dağıtırken kullanırsınız `ChainTrust` yerine değeri. De değer ayarlayabilirsiniz `Custom`. Ayarlandığında `Custom` değeri ayarlamanız gerekir `CustomCertificateValidatorType` öznitelik bir bütünleştirilmiş kod ve sertifikayı doğrulamak için kullanılan tür. Kendi özel Doğrulayıcı sağlayıcısı oluşturmak için Özet devralmalıdır <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.  
  
### <a name="issuedtokenauthentication-element"></a>\<ServiceCredentials > öğesi  
 Verilen belirteç senaryo üç aşamadan oluşur. Bir istemci bir hizmeti erişmeye ilk aşamada, başvurulan bir *güvenli belirteç hizmeti* (STS). STS, istemci kimlik doğrulaması yapar ve daha sonra istemci genellikle bir güvenlik onaylama işaretleme dili (SAML) belirteci bir belirteç verir. İstemci, ardından belirteci ile hizmetine döndürür. Belirteç için belirteç ve bu nedenle istemci kimliğini doğrulamak hizmet veren bir veri hizmeti inceler. Belirteç kimlik doğrulaması için güvenli belirteç hizmeti kullandığı sertifikayı hizmete bilinmesi gerekir. [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) depo gibi herhangi bir güvenli belirteç hizmeti sertifika için bir öğedir. Sertifikaları eklemek için [ \<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). INSERT bir [ \<Ekle >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) aşağıdaki örnekte gösterildiği gibi her sertifika için.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Varsayılan olarak, sertifikaları güvenli bir belirteci Hizmeti'nden alınmalıdır. Bu "sertifikalar, istemciler yalnızca yasal olun bilinen" bir hizmete erişebilir.  
  
 Kullanmanız gereken [ \<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) yararlanan bir federasyon uygulaması koleksiyonda bir *güvenli belirteç hizmeti* (STS) sorunları `SamlSecurityToken` güvenlik belirteçleri. Güvenlik belirteci STS verdiğinde, kendisi için güvenlik belirteci amaçlanmıştır ekleyerek Web Hizmetleri URI'sini belirtebilirsiniz bir `SamlAudienceRestrictionCondition` için güvenlik belirteci. Veren `SamlSecurityTokenAuthenticator` alıcı Web hizmetinin aşağıdakileri yaparak bu denetimi olacağını belirleyerek verilen güvenlik belirteci için bu Web hizmetini kullandığınızdan emin olun:  
  
- Ayarlama `audienceUriMode` özniteliği [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) için `Always` veya `BearerKeyOnly`.  
  
- Bu koleksiyona bir URI'leri ekleyerek geçerli URI'lerin kümesini belirtin. Bunu yapmak için INSERT bir [ \<Ekle >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) her URI  
  
 Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Anonim CardSpace kullanıcıların  
 Ayarı `AllowUntrustedRsaIssuers` özniteliği `<IssuedTokenAuthentication>` öğesine `true` açıkça herhangi bir istemci bir rastgele RSA anahtar çifti ile imzalanmış şirket içinde verilen bir belirteç sunmasını sağlar. Veren *güvenilmeyen* anahtar ile ilişkili hiçbir veren verileri sildiğinden. Kendi kendine sağlanan talep kimliğini içeren kendi kendine verilen bir kart CardSpace kullanıcı oluşturabilirsiniz. Bu özellik, dikkatli kullanın. Bu özelliği kullanmak için RSA ortak anahtarını bir veritabanında bir kullanıcı adı ile birlikte depolanmalıdır daha güvenli bir parola olarak düşünebilirsiniz. Bir istemci erişim hizmetine izin vermeden önce istemci sunulan RSA ortak anahtarı sunulan kullanıcı adı için depolanan ortak anahtarı ile karşılaştırarak doğrulayın. Bu, kayıt işleminden yapabildiği kullanıcılar kullanıcı adlarını kaydetmeleri ve bunları Self verilen RSA ortak anahtarlarla ilişkilendirme sağladıktan varsayılır.  
  
## <a name="client-credentials"></a>İstemci kimlik bilgileri  
 İstemci kimlik bilgileri, hizmetleri karşılıklı kimlik doğrulaması gerekli olduğu durumlarda istemcinin kimliğini doğrulamak için kullanılır. Bölümü, istemci Hizmet sertifikası ile bir hizmeti iletileri burada güvenlik altına almanız gerekir senaryolar için hizmet sertifikaları belirtmek için kullanabilirsiniz.  
  
 Ayrıca bir istemci bir Federasyon senaryonun parçası olarak kullanım verilen belirteçleri için bir güvenli belirteç hizmeti veya yerel yayımlayan belirteçlerin yapılandırabilirsiniz. Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Tüm istemci kimlik bilgileri altında bulunan [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)aşağıdaki kodda gösterildiği gibi.  
  
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
  
#### <a name="clientcertificate-element"></a>\<clientCertificate > öğesi  
 Bu öğe istemcinin kimliğini doğrulamak için kullanılan sertifika ayarlayın. Daha fazla bilgi için [nasıl yapılır: İstemci kimlik bilgileri değerlerini belirtme](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest >  
 Bu özellik, Windows ve Internet Information Services (IIS) üzerinde Active Directory ile etkinleştirilmelidir. Daha fazla bilgi için [Özet kimlik doğrulaması IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).  
  
#### <a name="issuedtoken-element"></a>\<IssuedToken > öğesi  
 [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) belirteçleri veya güvenlik belirteci hizmeti ile kullanılan davranışlar yerel yayımlayan yapılandırma için kullanılan öğeleri içerir. Yerel yayımlayan kullanmak bir istemci yapılandırma yönergeleri için bkz: [nasıl yapılır: Yerel yayımlayan yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress >  
 Varsayılan bir güvenlik belirteci hizmeti adresi belirtir. Bu zaman <xref:System.ServiceModel.WSFederationHttpBinding> URL veya güvenlik belirteci hizmeti için bir federe bağlama veren adresini olduğunda sağlamaz `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` veya `null`. Bu gibi durumlarda <xref:System.ServiceModel.Description.ClientCredentials> yerel dağıtımcının ve bağlama bu veren ile iletişim kurmak için kullanılacak adresi ile yapılandırılmalıdır.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors>  
 Kullanım [ \<issuerChannelBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) güvenlik belirteci hizmeti ile iletişim kurarken kullanılan WCF istemci davranışlarını eklemek için. İstemci davranışlarını tanımlayan [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) bölümü. Tanımlı bir davranışı kullanmak için ekleme bir <`add`> öğesine `<issuerChannelBehaviors>` iki öznitelik sahip öğe. Ayarlama `issuerAddress` ayarlama ve güvenlik belirteci hizmeti URL'sini `behaviorConfiguration` aşağıdaki örnekte gösterildiği gibi öznitelik için tanımlanmış uç nokta davranışı adı.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate > öğesi  
 Hizmet sertifikalarının kimlik doğrulamayı denetlemek için bu öğeyi kullanırsınız.  
  
 [ \<DefaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) öğesi, tek bir sertifika kullanılması için hizmet sertifikası yok belirtir depolayabilir.  
  
 Kullanım [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) ve [ \<Ekle >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) belirli hizmetler ile ilişkilendirilen hizmet sertifikaları ayarlamak için. `<add>` Öğesi içeren bir `targetUri` sertifika hizmeti ile ilişkilendirmek için kullanılan öznitelik.  
  
 [ \<Kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) öğesi sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir. Varsayılan olarak, "her sertifika sertifika zincirinin üst bir güvenilen sertifika yetkilisi sonu hiyerarşisini bulunması gereken belirten ChainTrust," için düzeyi ayarlanır. En güvenli mod budur. Ayrıca güvenilen bir zinciri olan sertifikaları yanı sıra şirket içinde verilen sertifikaların (eş güven) kabul edildiğini belirtir, "PeerOrChainTrust" değerine ayarlayabilirsiniz. Bu değer, geliştirme ve istemciler ve hizmetler kendi kendine verilen sertifikaların güvenilir yetkilisinden satın alınması değil çünkü hata ayıklama kullanılır. Bir istemci dağıtımı sırasında "ChainTrust" değerini kullanın. "Özel" veya "None". değer de ayarlayabilirsiniz "Özel" değerini kullanmak için de ayarlamalısınız `CustomCertificateValidatorType` öznitelik bir bütünleştirilmiş kod ve sertifikayı doğrulamak için kullanılan tür. Kendi özel Doğrulayıcı sağlayıcısı oluşturmak için Özet devralmalıdır <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı. Daha fazla bilgi için [nasıl yapılır: Özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [ \<Kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) öğesi içeren bir `RevocationMode` sertifika iptali için nasıl denetlenir belirten özniteliği. Sertifika iptali için otomatik olarak denetlenir gösteren "çevrimiçi" varsayılandır. Daha fazla bilgi için [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [ \<ServiceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) öğesi kimliğe bürünme yetkilendirme ve özel rol sağlayıcıları etkileyen öğeleri içerir.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Sınıfı, bir hizmet yönteme uygulanır. Öznitelik, bir korumalı yöntem kullanımını yetkilendirirken kullanmak için kullanıcı gruplarını belirtir. Varsayılan değer "UseWindowsGroups" ve "Yöneticiler" veya "Kullanıcılar" gibi Windows gruplarını bir kaynağa erişmeye çalışırken bir kimlik için aranır belirtir. "UseAspNetRoles" de belirtebilirsiniz altında yapılandırılmış bir özel rol sağlayıcıyı kullanacak şekilde <`system.web` > öğesi, aşağıdaki kodda gösterildiği gibi.  
  
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
 Kullanım [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) yazılan günlük ve hangi belirtmek için oturum olay türleri. Daha fazla bilgi için [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
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
 İstemciler için meta verileri dışarı aktarma yapılandırması ve istemci kodunun indirmeler etkinleştirdiği geliştiriciler, hizmet ve istemci için uygundur. Kötü amaçlı kullanıcılara bir hizmet riskini azaltmak için Güvenli HTTP (HTTPS) mekanizması üzerinde SSL kullanılarak aktarım mümkündür. Bunu yapmak için önce uygun bir X.509 sertifikası hizmeti barındıran bilgisayardaki belirli bir bağlantı noktası bağlamanız gerekir. (Daha fazla bilgi için [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) İkinci olarak, ekleme bir [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) hizmet yapılandırmasını ve kümesi `HttpsGetEnabled` özniteliğini `true`. Son olarak, ayarlama `HttpsGetUrl` aşağıdaki örnekte gösterildiği gibi hizmet meta veri uç noktası URL'sine özniteliği.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
