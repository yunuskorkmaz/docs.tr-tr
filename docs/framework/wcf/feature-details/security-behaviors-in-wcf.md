---
title: WCF'de Güvenlik Davranışları
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: f56bbd66aa61b8db9d6e720fb3a67ddbbf5e267e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184532"
---
# <a name="security-behaviors-in-wcf"></a>WCF'de Güvenlik Davranışları
Windows Communication Foundation'da (WCF) davranışlar çalışma zamanı davranışını hizmet düzeyinde veya bitiş noktası düzeyinde değiştirir. (Genel olarak davranışlar hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) *Güvenlik davranışları* kimlik bilgileri, kimlik doğrulama, yetkilendirme ve denetim günlükleri üzerinde denetim sağlar. Davranışları programlama veya yapılandırma yoluyla kullanabilirsiniz. Bu konu, güvenlik işlevleriile ilgili aşağıdaki davranışları yapılandırmaya odaklanır:  
  
- [ \<serviceCredentials>. ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)  
  
- istemciKimlik bilgileri>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
  
- serviceAuthorization>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)  
  
- serviceSecurityAudit>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
  
- serviceMetadata>, istemcilerin meta veriler için erişebileceği güvenli bir uç nokta belirtmenizi de sağlar. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)  
  
## <a name="setting-credentials-with-behaviors"></a>Kimlik Bilgilerini Davranışlarla Ayarlama  
 Bir hizmet veya [ \<istemci](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) için kimlik bilgileri değerlerini ayarlamak için>[ \<>ve](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) istemci kimlik bilgilerini kullan. Altta yatan bağlama yapılandırması, bir kimlik bilgisinin ayarlanıp ayarlanmayacağını belirler. Örneğin, güvenlik modu `None`ayarlanmışsa, hem istemciler hem de hizmetler birbirinin kimliğini doğrulamaz ve herhangi bir türde kimlik belgesi gerektirmez.  
  
 Diğer taraftan, hizmet bağlama istemci kimlik bilgisi türü gerektirebilir. Bu durumda, bir davranışı kullanarak bir kimlik bilgisi değeri ayarlamanız gerekebilir. (Olası kimlik bilgileri türleri hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md) Windows kimlik bilgilerinin kimlik doğrulaması için kullanıldığı bazı durumlarda, ortam gerçek kimlik bilgilerini otomatik olarak belirler ve kimlik bilgilerini açıkça ayarlamanız gerekmez (farklı bir kimlik bilgisi kümesi belirtmek istemediğiniz sürece).  
  
 Tüm hizmet kimlik [ \<bilgileri, hizmetDavranışı'nın ](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)alt öğeleri olarak>. Aşağıdaki örnekte, hizmet kimlik bilgisi olarak kullanılan bir sertifika gösterilmektedir.  
  
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
  
## <a name="service-credentials"></a>Hizmet Kimlik Bilgileri  
 [ \<ServiceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) dört alt öğe içerir. Aşağıdaki bölümlerde elemanlar ve kullanımları ele alınmıştır.  
  
### <a name="servicecertificate-element"></a>\<serviceSertifika> Unsuru  
 İleti güvenlik modunu kullanarak istemcilere hizmetin kimliğini doğrulamak için kullanılan bir X.509 sertifikası belirtmek için bu öğeyi kullanın. Düzenli olarak yenilenen bir sertifika kullanıyorsanız, parmak izi değişir. Bu durumda, sertifika aynı konu `X509FindType` adıyla yeniden düzenlenebileceğinden özne adını kullanın.  
  
 Öğeyi kullanma hakkında daha fazla bilgi için [bkz: İstemci Kimlik Bilgilerini Belirtin.](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
  
### <a name="certificate-of-clientcertificate-element"></a>\<müşteri Sertifikası \<> Öğesi sertifika>  
 Hizmetin istemciyle güvenli bir şekilde iletişim kurabilmesi için istemcinin sertifikasına önceden sahip olması gerektiğinde [ \<sertifika>](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) öğesini kullanın. Bu, çift yönlü iletişim deseni kullanırken oluşur. Daha tipik istek-yanıt deseninde, istemci, hizmetin istemciye yanıtını güvence altına almak için kullandığı isteğe sertifikasını içerir. Ancak çift yönlü iletişim deseninin istek ve yanıtı yoktur. Hizmet, istemcinin sertifikasını iletişimden çıkaramaz ve bu nedenle hizmet, istemciye iletileri güvence altına almak için müşterinin sertifikasını önceden gerektirir. İstemcinin sertifikasını bant dışı bir şekilde almanız ve bu öğeyi kullanarak sertifikayı belirtmeniz gerekir. Çift yönlü hizmetler hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
  
### <a name="authentication-of-clientcertificate-element"></a>\<istemciSertifika> \<Öğesi kimlik doğrulama>  
 Kimlik [ \<doğrulama>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) öğesi, istemcilerin kimlik doğrulama şeklini özelleştirmenize olanak tanır. `CertificateValidationMode` Özniteliği `None`, , `ChainTrust` `PeerOrChainTrust`, `PeerTrust`, veya `Custom`. Varsayılan olarak, `ChainTrust`düzey, her sertifikanın zincirin üst kısmında ki kök *yetkiyle* biten sertifikalar hiyerarşisinde bulunması gerektiğini belirten olarak ayarlanır. Bu en güvenli moddur. Ayrıca, kendi kendine `PeerOrChainTrust`verilen sertifikaların (eş güven) kabul edildiğini belirten değeri ve güvenilir bir zincirdeki sertifikaları da ayarlayabilirsiniz. Kendi kendine verilen sertifikaların güvenilir bir makamdan satın alınması gerekmedığından, bu değer istemciler ve hizmetler geliştirirken ve hata ayıklarken kullanılır. İstemci dağıtırken, `ChainTrust` bunun yerine değeri kullanın. Değeri de ' ye `Custom`ayarlayabilirsiniz. `Custom` Değere ayarlandığında, özniteliği sertifikayı `CustomCertificateValidatorType` doğrulamak için kullanılan bir derlemeye ve türe ayarlamanız gerekir. Kendi özel doğrulayıcınızı oluşturmak için soyut <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıftan devralmanız gerekir.  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication> Öğesi  
 Verilen belirteç senaryosunun üç aşaması vardır. İlk aşamada, bir hizmete erişmeye çalışan bir istemcigüvenli bir *belirteç hizmetine* (STS) başvurur. STS daha sonra istemcinin kimliğini doğrular ve daha sonra istemciye genellikle bir Güvenlik İddiaları Biçimlendirme Dili (SAML) belirteci olan bir belirteç ve daha sonra sorunlar. İstemci daha sonra belirteçle birlikte servise geri döner. Hizmet, hizmetin belirteci ve bu nedenle istemcikimlik doğrulamasını sağlayan verilerin belirteci inceler. Belirteci doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifikanın hizmet tarafından bilinmesi gerekir. Verilen TokenAuthentication>öğesi, bu tür güvenli belirteç hizmet sertifikalarının deposudur. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) Sertifika eklemek için [ \<bilinen Sertifikalar>](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)kullanın. Aşağıdaki örnekte gösterildiği gibi, her sertifika için bir [ \<ekleme>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) ekleyin.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"
           storeLocation="LocalMachine" storeName="My"
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir. Bu "bilinen" sertifikalar, yalnızca yasal istemcilerin bir hizmete erişebilmesini sağlar.  
  
 İzin verilen [AudienceUris>koleksiyonunu, güvenlik belirteçleri veren güvenli bir belirteç hizmeti (STS) kullanan federe bir uygulamada kullanmalısınız. \<](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) *secure token service* `SamlSecurityToken` STS güvenlik belirteci verdiğinde, güvenlik belirteci güvenlik belirteci bir ekleyerek `SamlAudienceRestrictionCondition` amaçlanan Web hizmetlerinin URI belirtebilirsiniz. Bu, `SamlSecurityTokenAuthenticator` bu denetimin aşağıdakileri yaparak gerçekleşmesi gerektiğini belirterek, alıcı Web hizmetinin verilen güvenlik belirtecinin bu Web hizmeti için tasarlandığını doğrulamasına olanak tanır:  
  
- Verilen `audienceUriMode` [ \<TokenAuthentication'ın](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) özniteliğini `Always` `BearerKeyOnly`>veya .  
  
- Bu koleksiyona URI'leri ekleyerek geçerli ÜR'ler kümesini belirtin. Bunu yapmak için, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) her URI için bir ekleme>ekleyin  
  
 Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için [bkz: Federasyon Hizmetinde Kimlik Bilgilerini Yapılandırma.](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Anonim CardSpace Kullanıcılarına İzin Verme  
 Öğenin `AllowUntrustedRsaIssuers` özniteliğini `<IssuedTokenAuthentication>` açıkça, `true` herhangi bir istemcinin rasgele bir RSA anahtar çifti yle imzalanmış kendi kendine verilmiş bir belirteci sunmasına olanak tanır. Anahtarla ilişkili veren verisi olmadığından, verene *güvenilmez.* Bir CardSpace kullanıcısı, kendi kendine sağlanan kimlik iddialarını içeren kendi kendine verilmiş bir kart oluşturabilir. Bu özelliği dikkatli kullanın. Bu özelliği kullanmak için RSA ortak anahtarını, bir kullanıcı adı ile birlikte bir veritabanında depolanması gereken daha güvenli bir parola olarak düşünün. İstemci hizmete erişmesine izin vermeden önce, sunulan kullanıcı adı için depolanan ortak anahtarla karşılaştırarak istemci tarafından sunulan RSA ortak anahtarını doğrulayın. Bu, kullanıcıların kullanıcı adlarını kaydedebilecekleri ve bunları kendi kendine verilen RSA ortak anahtarlarıyla ilişkilendirebilecekleri bir kayıt işlemi oluşturduğunuzu varsayarır.  
  
## <a name="client-credentials"></a>İstemci Kimlik Bilgileri  
 İstemci kimlik bilgileri, karşılıklı kimlik doğrulamanın gerekli olduğu durumlarda istemciyi hizmetlere doğrudoğrulamak için kullanılır. Bu bölümü, istemcinin hizmet sertifikasına sahip bir hizmete iletileri güvenli hale alması gereken senaryolar için hizmet sertifikalarını belirtmek için kullanabilirsiniz.  
  
 Ayrıca, bir istemciyi bir federasyon senaryosunun bir parçası olarak, güvenli bir belirteç hizmetinden veya yerel bir belirteç verenden verilen belirteçleri kullanacak şekilde yapılandırabilirsiniz. Federe senaryolar hakkında daha fazla bilgi için [Federasyon ve İhraç Jetonları'na](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)bakın. Tüm istemci kimlik bilgileri, aşağıdaki kodda gösterildiği gibi, [ \<>uç nokta Davranışı ](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)altında bulunur.  
  
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
  
#### <a name="clientcertificate-element"></a>\<istemciSertifika> Öğesi  
 Bu öğeyle istemcinin kimliğini doğrulamak için kullanılan sertifikayı ayarlayın. Daha fazla bilgi için [bkz: İstemci kimlik bilgilerini belirtin.](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
  
#### <a name="httpdigest"></a>\<httpDigest>  
 Bu özellik, Windows ve Internet Bilgi Hizmetleri (IIS) üzerinde Active Directory ile etkinleştirilmelidir. Daha fazla bilgi için [IIS 6.0'daki Özet Kimlik Doğrulama'ya](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))bakın.  
  
#### <a name="issuedtoken-element"></a>\<issuedToken> Elemanı  
 Verilen Token>belirteçleri yerel bir veren yapılandırmak için kullanılan öğeleri veya bir güvenlik belirteç hizmeti ile kullanılan davranışları içerir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) İstemciyi yerel bir veren kullanacak şekilde yapılandırma yönergeleri için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress>  
 Varsayılan güvenlik belirteç hizmet adresini belirtir. Bu, güvenlik <xref:System.ServiceModel.WSFederationHttpBinding> belirteci hizmeti için bir URL sağlamadığında veya federe bir bağlamanın `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ihraççı adresi veya `null`. Bu gibi durumlarda, yerel <xref:System.ServiceModel.Description.ClientCredentials> verenin adresi ve bu verenle iletişim kurmak için kullanılacak bağlayıcı ile yapılandırılmalıdır.  
  
#### <a name="issuerchannelbehaviors"></a>\<verenKanalDavranışlar>  
 Bir güvenlik [ \<belirteci](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) hizmetiyle iletişim kurarken kullanılan WCF istemci davranışlarını eklemek için verenKanal Davranışları>kullanın. Uç nokta Davranışları>bölümünde istemci davranışlarını tanımlayın. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) Tanımlı bir davranış kullanmak `add` için, iki `<issuerChannelBehaviors>` öznitelik ile öğeye <> öğesi ekleyin. `issuerAddress` Güvenlik belirteci hizmetinin URL'sini ayarlayın `behaviorConfiguration` ve aşağıdaki örnekte gösterildiği gibi tanımlanan bitiş noktası davranışının adına özniteliği ayarlayın.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />
```  
  
#### <a name="servicecertificate-element"></a>\<serviceSertifika> Unsuru  
 Hizmet sertifikalarının kimlik doğrulamasını denetlemek için bu öğeyi kullanın.  
  
 Varsayılan Sertifika>öğesi, hizmette sertifika belirtilmediğinde kullanılan tek bir sertifikayı depolayabilir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)  
  
 ScopedCertificates>kullanın ve [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) belirli hizmetlerle ilişkili hizmet sertifikaları ayarlamak için>ekleyin. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) Öğe, `<add>` sertifikayı hizmetle ilişkilendirmek için kullanılan bir `targetUri` öznitelik içerir.  
  
 Kimlik [ \<doğrulama>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) öğesi, sertifikaları doğrulamak için kullanılan güven düzeyini belirtir. Varsayılan olarak, düzey "ChainTrust" olarak ayarlanır ve bu da her sertifikanın zincirin üst kısmında güvenilir bir sertifika yetkilisiyle biten sertifikalar hiyerarşisinde bulunması gerektiğini belirtir. Bu en güvenli moddur. Ayrıca, kendi kendine verilen sertifikaların (akran güveni) kabul edildiğini belirten "PeerOrChainTrust" değerini ve güvenilir bir zincirdeki sertifikaları da ayarlayabilirsiniz. Kendi kendine verilen sertifikaların güvenilir bir makamdan satın alınması gerekmedığından, bu değer istemciler ve hizmetler geliştirirken ve hata ayıklarken kullanılır. İstemci dağıtırken bunun yerine "ChainTrust" değerini kullanın. Ayrıca değeri "Özel" veya "Hiçbiri" olarak da ayarlayabilirsiniz. "Özel" değerini kullanmak için, özniteliği `CustomCertificateValidatorType` sertifikayı doğrulamak için kullanılan bir derlemeye ve türe ayarlamanız gerekir. Kendi özel doğrulayıcınızı oluşturmak için soyut <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıftan devralmanız gerekir. Daha fazla bilgi için [bkz: Özel Sertifika Doğrulayıcısı Kullanan Bir Hizmet Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [ \<Kimlik doğrulama>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) öğesi, sertifikaların iptal için nasıl denetleniyi belirten bir `RevocationMode` öznitelik içerir. Varsayılan değer, sertifikaların iptal için otomatik olarak denetlenir olduğunu gösteren "çevrimiçi"dir. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
  
## <a name="serviceauthorization"></a>Servis Yetkilendirmesi  
 ServiceAuthorization>öğesi yetkilendirmeyi, özel rol sağlayıcılar ve kimliğe bürünme etkileyen öğeler içerir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)  
  
 Sınıf <xref:System.Security.Permissions.PrincipalPermissionAttribute> bir hizmet yöntemine uygulanır. Öznitelik, korumalı bir yöntemin kullanımına izin verirken kullanılacak kullanıcı gruplarını belirtir. Varsayılan değer "WindowsGroups'u Kullan"dır ve "Yöneticiler" veya "Kullanıcılar" gibi Windows gruplarının kaynağa erişmeye çalışan bir kimlik için arandığını belirtir. Aşağıdaki kodda gösterildiği gibi, <`system.web` > öğesi altında yapılandırılan özel bir rol sağlayıcısı nı kullanmak için "UseAspNetRoles" de belirtebilirsiniz.  
  
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
  
 Aşağıdaki kod öznitelik `roleProviderName` ile `principalPermissionMode` kullanılan gösterir.  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                        roleProviderName ="SqlProvider" />  
</behavior>
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>Güvenlik Denetimlerinin Yapılandırılması  
 Günlük yazdı ve günlüğe ne tür olaylar günlük belirtmek için [ \<hizmetSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) kullanın. Daha fazla bilgi için [denetime](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)bakın.  
  
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
  
## <a name="secure-metadata-exchange"></a>Güvenli Meta veri değişimi  
 Yapılandırma ve istemci kodunun karşıdan yüklemesini sağladığından, meta verileri istemcilere dışa aktarmak hizmet ve istemci geliştiricileri için uygundur. Kötü niyetli kullanıcılara bir hizmetin maruz kalmasını azaltmak için, HTTP (HTTPS) mekanizması üzerinden SSL kullanarak aktarım güvenliğini sağlamak mümkündür. Bunu yapmak için, öncelikle hizmeti barındıran bilgisayardaki belirli bir bağlantı noktasına uygun bir X.509 sertifikası bağlamanız gerekir. (Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) İkinci olarak, hizmet yapılandırmasına>bir `HttpsGetEnabled` `true` [ \<hizmet metaveri](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) ekleyin ve özniteliğini . Son olarak, `HttpsGetUrl` aşağıdaki örnekte gösterildiği gibi hizmet meta veri bitiş noktasının URL'sine özniteliği ayarlayın.  
  
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
- [Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
