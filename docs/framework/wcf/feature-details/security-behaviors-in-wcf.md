---
title: WCF'de Güvenlik Davranışları
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 12ae9bb90752fe3ee76404948693c501fc42efe6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730949"
---
# <a name="security-behaviors-in-wcf"></a>WCF'de Güvenlik Davranışları
Windows Communication Foundation (WCF) ' de, davranışlar, hizmet düzeyinde veya uç nokta düzeyinde çalışma zamanı davranışını değiştirir. (Genel olarak davranışlar hakkında daha fazla bilgi için bkz. [hizmet çalışma zamanı davranışını belirtme](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Güvenlik davranışları* kimlik bilgileri, kimlik doğrulama, yetkilendirme ve denetim günlükleri üzerinde denetime izin verir. Davranışları, programlama yoluyla veya yapılandırma yoluyla kullanabilirsiniz. Bu konu, güvenlik işlevleriyle ilgili aşağıdaki davranışları yapılandırmaya odaklanır:  
  
- [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
- [clientCredentials >\<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
- [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
- [\<Servicesecurityauıdıt >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
- Ayrıca, istemcilerin meta verilere erişebileceği güvenli bir uç nokta belirtmenize olanak sağlayan [serviceMetadata >\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md).  
  
## <a name="setting-credentials-with-behaviors"></a>Davranış ile kimlik bilgilerini ayarlama  
 Bir hizmet veya istemcinin kimlik bilgisi değerlerini ayarlamak için [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ve [ClientCredentials >\<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) kullanın. Temel bağlama yapılandırması, kimlik bilgisinin ayarlanması gerekip gerekmediğini belirler. Örneğin, güvenlik modu `None`olarak ayarlandıysa, hem istemciler hem de hizmetler birbirlerinin kimliğini doğrular ve herhangi bir türde kimlik bilgileri gerektirmez.  
  
 Öte yandan, hizmet bağlaması bir istemci kimlik bilgisi türü gerektirebilir. Bu durumda, bir davranış kullanarak bir kimlik bilgisi değeri ayarlamanız gerekebilir. (Olası kimlik bilgileri türleri hakkında daha fazla bilgi için bkz. [kimlik bilgisi türü seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Kimlik doğrulaması için Windows kimlik bilgilerinin kullanıldığı durumlar gibi bazı durumlarda, ortam gerçek kimlik bilgisi değerini otomatik olarak belirler ve kimlik bilgisi değerini açıkça ayarlamanız gerekmez (farklı kimlik bilgileri kümesi belirtmek istemediğiniz sürece).  
  
 Tüm hizmet kimlik bilgileri, [\<Servicedavranışların >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)alt öğeleri olarak bulunur. Aşağıdaki örnekte, hizmet kimlik bilgileri olarak kullanılan bir sertifika gösterilmektedir.  
  
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
 [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) dört alt öğe içerir. Öğeler ve kullanımları aşağıdaki bölümlerde ele alınmıştır.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate > öğesi  
 Ileti güvenlik modunu kullanan istemcilere hizmetin kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikası belirtmek için bu öğeyi kullanın. Düzenli olarak yenilenen bir sertifika kullanıyorsanız, parmak izi değişir. Bu durumda, sertifika aynı konu adıyla yeniden verilmediğinden konu adını `X509FindType` olarak kullanın.  
  
 Öğesini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Istemci kimlik bilgisi değerlerini belirtme](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<> sertifika \<clientCertificate > öğesi  
 İstemci ile güvenli bir şekilde iletişim kurmak için hizmetin istemcinin sertifikasının önceden olması gereken [\<sertifika >](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) öğesini kullanın. Bu, çift yönlü iletişim deseninin kullanıldığı durumlarda oluşur. Daha tipik istek-yanıt modelinde, istemci, isteğin istemciye geri yanıtını güvenli hale getirmek için kullandığı sertifikayı da içerir. Ancak çift yönlü iletişim deseninin istek ve yanıtları yoktur. Hizmet istemcinin sertifikasını iletişimden çıkarsanamaz ve bu nedenle hizmetin istemciye güvenli hale getirmek için istemcinin sertifikasının önceden olması gerekir. İstemcinin sertifikasını bant dışı bir şekilde edinmeniz ve bu öğeyi kullanarak sertifikayı belirtmeniz gerekir. Çift yönlü hizmetler hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<clientCertificate > öğesinin \<kimlik doğrulaması >  
 [\<authentication >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) öğesi istemcilerin nasıl doğrulandığını özelleştirmenize olanak sağlar. `CertificateValidationMode` özniteliğini `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`veya `Custom`olarak ayarlayabilirsiniz. Varsayılan olarak, düzey `ChainTrust`olarak ayarlanır ve bu, her bir sertifikanın, zincirin en üstündeki bir *kök yetkilide* sonlanan sertifikaların hiyerarşisinde bulunması gerektiğini belirtir. En güvenli mod budur. Ayrıca, kendi kendine verilen sertifikaların (eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten `PeerOrChainTrust`değerini de ayarlayabilirsiniz. Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir. Bir istemciyi dağıttığınızda, bunun yerine `ChainTrust` değerini kullanın. Ayrıca değeri `Custom`olarak ayarlayabilirsiniz. `Custom` değere ayarlandığında, sertifikayı doğrulamak için kullanılacak bir derlemeye ve türüne `CustomCertificateValidatorType` özniteliğini de ayarlamanız gerekir. Kendi özel Doğrulayıcısı oluşturmak için soyut <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfından devralması gerekir.  
  
### <a name="issuedtokenauthentication-element"></a>\<IssuedTokenAuthentication > öğesi  
 Verilen belirteç senaryosunda üç aşama vardır. İlk aşamada, bir hizmete erişmeye çalışan bir istemci, *güvenli bir belirteç hizmeti* 'ne (STS) başvurulur. STS daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir. İstemci daha sonra belirtece sahip hizmete geri döner. Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler. Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir. [\<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) öğesi, bu tür güvenli belirteç hizmeti sertifikalarının deposıdır. Sertifika eklemek için [\<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)kullanın. Aşağıdaki örnekte gösterildiği gibi her sertifika için bir [\<ekleme >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) ekleyin.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir. Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.  
  
 Güvenlik belirteçleri `SamlSecurityToken` veren bir *güvenli belirteç hizmeti* (STS) kullanan bir federasyon uygulamasında [\<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) koleksiyonunu kullanmanız gerekir. STS güvenlik belirtecini aldığında, güvenlik belirtecine bir `SamlAudienceRestrictionCondition` ekleyerek güvenlik belirtecinin amaçlanan Web hizmetlerinin URI 'sini belirtebilir. Bu, alıcı Web hizmetinin `SamlSecurityTokenAuthenticator`, aşağıdaki işlemleri yaparak bu denetimi gerçekleşmelidir belirterek, verilen güvenlik belirtecinin bu Web hizmetine yönelik olduğunu doğrulamasına izin verir:  
  
- [\<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) `audienceUriMode` özniteliğini `Always` veya `BearerKeyOnly`olarak ayarlayın.  
  
- URI 'Leri bu koleksiyona ekleyerek geçerli URI 'Ler kümesini belirtin. Bunu yapmak için her URI için bir [\<ekle >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) ekleyin  
  
 Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Anonim CardSpace kullanıcılarına izin verme  
 `<IssuedTokenAuthentication>` öğesinin `AllowUntrustedRsaIssuers` özniteliğini açıkça `true` olarak ayarlamak, herhangi bir istemcinin rastgele bir RSA anahtar çifti ile imzalanmış bir otomatik olarak verilen belirteç sunmasını sağlar. Anahtarın kendisiyle ilişkilendirilmiş veren verileri olmadığından veren *güvenilir* değil. Bir CardSpace kullanıcısı, kendi kendine sağlanmış kimlik taleplerini içeren bir otomatik olarak verilen kart oluşturabilir. Bu özelliği dikkatli kullanın. Bu özelliği kullanmak için, RSA ortak anahtarını bir veritabanı içinde bir Kullanıcı adı ile birlikte depolanması gereken daha güvenli bir parola olarak düşünün. İstemciye hizmete erişim izni vermeden önce, sunulan Kullanıcı adı için depolanan ortak anahtarla karşılaştırarak, istemci tarafından sunulan RSA ortak anahtarını doğrulayın. Bu, kullanıcıların kendi kullanıcı adlarını kaydedebileceği ve bunları kendi kendine verilen RSA ortak anahtarlarıyla ilişkilendirebildiği bir kayıt işlemi oluşturmuş olduğunu varsayar.  
  
## <a name="client-credentials"></a>İstemci kimlik bilgileri  
 İstemci kimlik bilgileri, karşılıklı kimlik doğrulamanın gerekli olduğu durumlarda istemcinin kimliğini doğrulamak için kullanılır. Bu bölümü, istemcinin hizmet sertifikası ile iletileri güvenli hale getirmek zorunda olduğu senaryolar için hizmet sertifikaları belirtmek üzere kullanabilirsiniz.  
  
 Ayrıca, bir istemciyi, güvenli bir belirteç hizmetinden veya yerel belirteçlerden oluşan belirteçleri kullanmak üzere bir Federasyon senaryosunun parçası olarak yapılandırabilirsiniz. Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Tüm istemci kimlik bilgileri, aşağıdaki kodda gösterildiği gibi [\<Endpointdavranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)altında bulunur.  
  
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
 Bu öğeyle istemcinin kimliğini doğrulamak için kullanılan sertifikayı ayarlayın. Daha fazla bilgi için bkz. [nasıl yapılır: Istemci kimlik bilgisi değerlerini belirtme](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest >  
 Bu özelliğin Windows ve Internet Information Services (IIS) üzerinde Active Directory etkinleştirilmesi gerekir. Daha fazla bilgi için bkz. [ııs 6,0 'de Özet kimlik doğrulaması](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).  
  
#### <a name="issuedtoken-element"></a>\<IssuedToken > öğesi  
 [\<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) , belirteçleri yerel olarak veren veya bir güvenlik belirteci hizmeti ile kullanılan davranışları yapılandırmak için kullanılan öğeleri içerir. Bir istemciyi yerel bir veren kullanacak şekilde yapılandırma yönergeleri için bkz. [nasıl yapılır: yerel veren yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<LocalIssuerAddress >  
 Varsayılan bir güvenlik belirteci hizmeti adresi belirtir. Bu, <xref:System.ServiceModel.WSFederationHttpBinding> güvenlik belirteci hizmeti için bir URL sağlamadığınızda veya bir Federasyon bağlamasının veren adresinin `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` veya `null`olduğu durumlarda kullanılır. Bu gibi durumlarda, <xref:System.ServiceModel.Description.ClientCredentials> yerel veren adresiyle ve bu veren ile iletişim kurmak için kullanılacak bağlamayı yapılandırmak gerekir.  
  
#### <a name="issuerchannelbehaviors"></a>\<ıssuerchanneldavranışlar >  
 Bir güvenlik belirteci hizmetiyle iletişim kurulurken kullanılan WCF istemci davranışları eklemek için [\<ıssuerchanneldavranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) kullanın. [\<endpointdavranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) bölümünde istemci davranışlarını tanımlayın. Tanımlı bir davranışı kullanmak için, iki özniteliğe sahip `<issuerChannelBehaviors>` öğesine bir <`add`> öğesi ekleyin. `issuerAddress`, güvenlik belirteci hizmetinin URL 'SI olarak ayarlayın ve aşağıdaki örnekte gösterildiği gibi `behaviorConfiguration` özniteliğini tanımlanan uç nokta davranışının adı olarak ayarlayın.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate > öğesi  
 Hizmet sertifikalarının kimlik doğrulamasını denetlemek için bu öğeyi kullanın.  
  
 [\<defaultcertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) öğesi, hizmet hiçbir sertifika belirttiğinde kullanılan tek bir sertifikayı depolayabilirler.  
  
 [\<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) kullanın ve belirli hizmetlerle ilişkili hizmet sertifikalarını ayarlamak için [> ekleyin\<](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) . `<add>` öğesi, sertifikayı hizmetle ilişkilendirmek için kullanılan bir `targetUri` özniteliği içerir.  
  
 [\<authentication >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) öğesi, sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir. Varsayılan olarak, düzey "ChainTrust" olarak ayarlanır. Bu, her bir sertifikanın, zincirinin en üstünde güvenilir bir sertifika yetkilisinden sonlanan bir sertifika hiyerarşisinde bulunması gerektiğini belirtir. En güvenli mod budur. Ayrıca, otomatik olarak verilen sertifikaların (eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değeri "PeerOrChainTrust" olarak ayarlayabilirsiniz. Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir. İstemci dağıtıldığında, bunun yerine "ChainTrust" değerini kullanın. Ayrıca değeri "Custom" veya "none" olarak da ayarlayabilirsiniz. "Custom" değerini kullanmak için, `CustomCertificateValidatorType` özniteliğini Ayrıca sertifikayı doğrulamak için kullanılan bir derleme ve tür olarak ayarlamanız gerekir. Kendi özel Doğrulayıcısı oluşturmak için soyut <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfından devralması gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [\<authentication >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) öğesi, sertifikaların iptal için nasıl denetlendiğini belirten bir `RevocationMode` özniteliği içerir. Varsayılan değer, sertifikaların iptal için otomatik olarak denetlendiğini belirten "çevrimiçi" dır. Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) öğesi yetkilendirme, özel rol sağlayıcıları ve kimliğe bürünme işlemlerini etkileyen öğeler içerir.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> sınıfı bir hizmet yöntemine uygulanır. Özniteliği, korumalı bir yöntemin kullanımını yetkilendirirken kullanılacak kullanıcı gruplarını belirtir. Varsayılan değer "UseWindowsGroups" değeridir ve bir kaynağa erişmeye çalışan bir kimlik için "Yöneticiler" veya "kullanıcılar" gibi Windows gruplarının arandığını belirtir. Ayrıca, aşağıdaki kodda gösterildiği gibi, <`system.web` > öğesi altında yapılandırılan özel bir rol sağlayıcısı kullanmak için "UseAspNetRoles" belirtebilirsiniz.  
  
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
  
 Aşağıdaki kod, `principalPermissionMode` özniteliğiyle kullanılan `roleProviderName` gösterir.  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">          
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                        roleProviderName ="SqlProvider" />  
</behavior>   
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>Güvenlik denetimlerini yapılandırma  
 Günlüğe yazılan günlüğü ve günlüğe kaydedilecek olay türlerini belirtmek için [\<Servicesecurityauıdıt >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) kullanın. Daha fazla bilgi için bkz. [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
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
 Yapılandırma ve istemci kodu İndirmeleri sağladığından, istemcilere meta verilerin verilmesi, hizmet ve istemci geliştiricileri için uygundur. Bir hizmetin kötü amaçlı kullanıcılara maruz kalmasını azaltmak için, HTTP (HTTPS) üzerinden SSL (HTTPS) mekanizmasını kullanarak aktarımı güvenli hale getirmek mümkündür. Bunu yapmak için, önce uygun bir X. 509.952 sertifikasını hizmeti barındıran bilgisayardaki belirli bir bağlantı noktasına bağlamanız gerekir. (Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) İkinci olarak, hizmet yapılandırmasına bir [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) ekleyin ve `HttpsGetEnabled` özniteliğini `true`olarak ayarlayın. Son olarak, aşağıdaki örnekte gösterildiği gibi `HttpsGetUrl` özniteliğini hizmet meta veri uç noktasının URL 'SI olarak ayarlayın.  
  
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
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
