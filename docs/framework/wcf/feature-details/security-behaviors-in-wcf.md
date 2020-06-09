---
title: WCF'de Güvenlik Davranışları
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: b25d476e9c9b4a70834274c6970dad1b056cecb9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595212"
---
# <a name="security-behaviors-in-wcf"></a>WCF'de Güvenlik Davranışları
Windows Communication Foundation (WCF) ' de, davranışlar, hizmet düzeyinde veya uç nokta düzeyinde çalışma zamanı davranışını değiştirir. (Genel olarak davranışlar hakkında daha fazla bilgi için bkz. [hizmet çalışma zamanı davranışını belirtme](../specifying-service-run-time-behavior.md).) *Güvenlik davranışları* kimlik bilgileri, kimlik doğrulama, yetkilendirme ve denetim günlükleri üzerinde denetime izin verir. Davranışları, programlama yoluyla veya yapılandırma yoluyla kullanabilirsiniz. Bu konu, güvenlik işlevleriyle ilgili aşağıdaki davranışları yapılandırmaya odaklanır:  
  
- [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).  
  
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md).  
  
- [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
- [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
- [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md)Ayrıca, istemcilerin meta verilere erişebileceği güvenli bir uç nokta belirtmenize de olanak sağlar.  
  
## <a name="setting-credentials-with-behaviors"></a>Davranış ile kimlik bilgilerini ayarlama  
 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) Bir hizmet veya istemcinin kimlik bilgisi değerlerini ayarlamak için ve kullanın. Temel bağlama yapılandırması, kimlik bilgisinin ayarlanması gerekip gerekmediğini belirler. Örneğin, güvenlik modu olarak ayarlandıysa `None` , hem istemciler hem de hizmetler birbirini doğrualmaz ve herhangi bir türde kimlik bilgileri gerektirmez.  
  
 Öte yandan, hizmet bağlaması bir istemci kimlik bilgisi türü gerektirebilir. Bu durumda, bir davranış kullanarak bir kimlik bilgisi değeri ayarlamanız gerekebilir. (Olası kimlik bilgileri türleri hakkında daha fazla bilgi için bkz. [kimlik bilgisi türü seçme](selecting-a-credential-type.md).) Kimlik doğrulaması için Windows kimlik bilgilerinin kullanıldığı durumlar gibi bazı durumlarda, ortam gerçek kimlik bilgisi değerini otomatik olarak belirler ve kimlik bilgisi değerini açıkça ayarlamanız gerekmez (farklı kimlik bilgileri kümesi belirtmek istemediğiniz sürece).  
  
 Tüm hizmet kimlik bilgileri öğesinin alt öğeleri olarak bulunur [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) . Aşağıdaki örnekte, hizmet kimlik bilgileri olarak kullanılan bir sertifika gösterilmektedir.  
  
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
 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md)Dört alt öğesi içerir. Öğeler ve kullanımları aşağıdaki bölümlerde ele alınmıştır.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate> Öğesi  
 Ileti güvenlik modunu kullanan istemcilere hizmetin kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikası belirtmek için bu öğeyi kullanın. Düzenli olarak yenilenen bir sertifika kullanıyorsanız, parmak izi değişir. Bu durumda, `X509FindType` sertifika aynı konu adıyla yeniden verilmediğinden konu adını olarak kullanın.  
  
 Öğesini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Istemci kimlik bilgisi değerlerini belirtme](../how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<certificate>\<clientCertificate>öğesinin  
 [\<certificate>](../../configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)İstemci ile güvenli iletişim kurmak için hizmetin istemcinin sertifikasının önceden olması gerektiğinde öğesini kullanın. Bu, çift yönlü iletişim deseninin kullanıldığı durumlarda oluşur. Daha tipik istek-yanıt modelinde, istemci, isteğin istemciye geri yanıtını güvenli hale getirmek için kullandığı sertifikayı da içerir. Ancak çift yönlü iletişim deseninin istek ve yanıtları yoktur. Hizmet istemcinin sertifikasını iletişimden çıkarsanamaz ve bu nedenle hizmetin istemciye güvenli hale getirmek için istemcinin sertifikasının önceden olması gerekir. İstemcinin sertifikasını bant dışı bir şekilde edinmeniz ve bu öğeyi kullanarak sertifikayı belirtmeniz gerekir. Çift yönlü hizmetler hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme oluşturma](how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<authentication>\<clientCertificate>öğesinin  
 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)Öğesi, istemcilerinin nasıl doğrulandığını özelleştirmenizi sağlar. Özniteliğini,,, `CertificateValidationMode` veya olarak `None` ayarlayabilirsiniz `ChainTrust` `PeerOrChainTrust` `PeerTrust` `Custom` . Varsayılan olarak, düzeyi olarak ayarlanır `ChainTrust` ; Bu, her bir sertifikanın, zincirinin en üstündeki bir *kök yetkilide* sonlanan sertifikaların hiyerarşisinde bulunması gerektiğini belirtir. En güvenli mod budur. Ayrıca, `PeerOrChainTrust` otomatik olarak verilen sertifikaların (eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değerini olarak da ayarlayabilirsiniz. Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir. Bir istemciyi dağıttığınızda, `ChainTrust` bunun yerine değeri kullanın. Değerini olarak da ayarlayabilirsiniz `Custom` . `Custom`Değere ayarlandığında, `CustomCertificateValidatorType` bir derlemeyi ve sertifikayı doğrulamak için kullanılan türünü de ayarlamanız gerekir. Kendi özel Doğrulayıcısı oluşturmak için soyut sınıftan devralması gerekir <xref:System.IdentityModel.Selectors.X509CertificateValidator> .  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication> Öğesi  
 Verilen belirteç senaryosunda üç aşama vardır. İlk aşamada, bir hizmete erişmeye çalışan bir istemci, *güvenli bir belirteç hizmeti* 'ne (STS) başvurulur. STS daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir. İstemci daha sonra belirtece sahip hizmete geri döner. Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler. Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir. [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)Öğesi, bu tür güvenli belirteç hizmeti sertifikalarının depolandığı depodur. Sertifika eklemek için öğesini kullanın [\<knownCertificates>](../../configure-apps/file-schema/wcf/knowncertificates.md) . [\<add>](../../configure-apps/file-schema/wcf/add-of-knowncertificates.md)Aşağıdaki örnekte gösterildiği gibi her sertifika için bir ekleyin.  
  
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
  
 [\<allowedAudienceUris>](../../configure-apps/file-schema/wcf/allowedaudienceuris.md)Koleksiyonu, güvenlik belirteçleri veren bir *güvenli belirteç hizmeti* (STS) kullanan bir Federasyon uygulamasında kullanmanız gerekir `SamlSecurityToken` . STS güvenlik belirtecini aldığında güvenlik belirtecinin bir güvenlik belirtecine ekleyerek amaçlanan Web hizmetlerinin URI 'sini belirtebilir `SamlAudienceRestrictionCondition` . Bu, `SamlSecurityTokenAuthenticator` alıcı Web hizmeti için, aşağıdaki işlemleri yaparak bu denetimi gerçekleşmelidir belirterek, verilen güvenlik belirtecinin bu Web hizmetine yönelik olduğunu doğrulamasına izin verir:  
  
- `audienceUriMode`Özniteliğini [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) veya olarak ayarlayın `Always` `BearerKeyOnly` .  
  
- URI 'Leri bu koleksiyona ekleyerek geçerli URI 'Ler kümesini belirtin. Bunu yapmak için [\<add>](../../configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) her URI için bir ekleyin  
  
 Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Anonim CardSpace kullanıcılarına izin verme  
 `AllowUntrustedRsaIssuers`Öğenin özniteliğini açıkça ayarlamak, `<IssuedTokenAuthentication>` herhangi bir `true` ISTEMCININ rastgele bir RSA anahtar çifti ile imzalanmış otomatik olarak verilen bir belirteç sunmasını sağlar. Anahtarın kendisiyle ilişkilendirilmiş veren verileri olmadığından veren *güvenilir* değil. Bir CardSpace kullanıcısı, kendi kendine sağlanmış kimlik taleplerini içeren bir otomatik olarak verilen kart oluşturabilir. Bu özelliği dikkatli kullanın. Bu özelliği kullanmak için, RSA ortak anahtarını bir veritabanı içinde bir Kullanıcı adı ile birlikte depolanması gereken daha güvenli bir parola olarak düşünün. İstemciye hizmete erişim izni vermeden önce, sunulan Kullanıcı adı için depolanan ortak anahtarla karşılaştırarak, istemci tarafından sunulan RSA ortak anahtarını doğrulayın. Bu, kullanıcıların kendi kullanıcı adlarını kaydedebileceği ve bunları kendi kendine verilen RSA ortak anahtarlarıyla ilişkilendirebildiği bir kayıt işlemi oluşturmuş olduğunu varsayar.  
  
## <a name="client-credentials"></a>İstemci kimlik bilgileri  
 İstemci kimlik bilgileri, karşılıklı kimlik doğrulamanın gerekli olduğu durumlarda istemcinin kimliğini doğrulamak için kullanılır. Bu bölümü, istemcinin hizmet sertifikası ile iletileri güvenli hale getirmek zorunda olduğu senaryolar için hizmet sertifikaları belirtmek üzere kullanabilirsiniz.  
  
 Ayrıca, bir istemciyi, güvenli bir belirteç hizmetinden veya yerel belirteçlerden oluşan belirteçleri kullanmak üzere bir Federasyon senaryosunun parçası olarak yapılandırabilirsiniz. Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](federation-and-issued-tokens.md). Aşağıdaki kodda gösterildiği gibi tüm istemci kimlik bilgileri altında bulunur [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) .  
  
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
</behaviors>  
```  
  
#### <a name="clientcertificate-element"></a>\<clientCertificate> Öğesi  
 Bu öğeyle istemcinin kimliğini doğrulamak için kullanılan sertifikayı ayarlayın. Daha fazla bilgi için bkz. [nasıl yapılır: Istemci kimlik bilgisi değerlerini belirtme](../how-to-specify-client-credential-values.md).  
  
#### \<httpDigest>  
 Bu özelliğin Windows ve Internet Information Services (IIS) üzerinde Active Directory etkinleştirilmesi gerekir. Daha fazla bilgi için bkz. [ııs 6,0 'de Özet kimlik doğrulaması](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).  
  
#### <a name="issuedtoken-element"></a>\<issuedToken> Öğesi  
 , [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) Belirteçleri yerel olarak veren veya bir güvenlik belirteci hizmeti ile kullanılan davranışları yapılandırmak için kullanılan öğeleri içerir. Bir istemciyi yerel bir veren kullanacak şekilde yapılandırma yönergeleri için bkz. [nasıl yapılır: yerel veren yapılandırma](how-to-configure-a-local-issuer.md).  
  
#### \<localIssuerAddress>  
 Varsayılan bir güvenlik belirteci hizmeti adresi belirtir. Bu, <xref:System.ServiceModel.WSFederationHttpBinding> güvenlik belirteci hizmeti için BIR URL sağlamadığınızda veya bir Federasyon bağlamasının veren adresinin veya olduğu durumlarda kullanılır `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` . Bu gibi durumlarda, <xref:System.ServiceModel.Description.ClientCredentials> yerel veren adresiyle ve bu veren ile iletişim kurmak için kullanılacak bağlama ile yapılandırılmalıdır.  
  
#### \<issuerChannelBehaviors>  
 [\<issuerChannelBehaviors>](../../configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)Bir güvenlik belirteci hizmetiyle iletişim kurulurken kullanılan WCF istemci davranışlarını eklemek için kullanın. Bölümünde istemci davranışlarını tanımlayın [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) . Tanımlı bir davranışı kullanmak için, `add` `<issuerChannelBehaviors>` iki özniteliği olan öğesine bir <> öğesi ekleyin. `issuerAddress`Öğesini güvenlik belirteci HIZMETININ URL 'sine ayarlayın ve `behaviorConfiguration` Aşağıdaki örnekte gösterildiği gibi özniteliği tanımlanan uç nokta davranışının adına ayarlayın.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />
      </issuerChannelBehaviors>  
   </issuedToken>  
</clientCredentials>
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate> Öğesi  
 Hizmet sertifikalarının kimlik doğrulamasını denetlemek için bu öğeyi kullanın.  
  
 [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md)Öğesi, hizmet hiçbir sertifika belirttiğinde kullanılan tek bir sertifikayı depolayabilirler.  
  
 [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) [\<add>](../../configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) Belirli hizmetlerle ilişkili hizmet sertifikalarını ayarlamak için ve kullanın. `<add>`Öğesi, `targetUri` sertifikayı hizmetle ilişkilendirmek için kullanılan bir özniteliği içerir.  
  
 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)Öğesi, sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir. Varsayılan olarak, düzey "ChainTrust" olarak ayarlanır. Bu, her bir sertifikanın, zincirinin en üstünde güvenilir bir sertifika yetkilisinden sonlanan bir sertifika hiyerarşisinde bulunması gerektiğini belirtir. En güvenli mod budur. Ayrıca, otomatik olarak verilen sertifikaların (eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değeri "PeerOrChainTrust" olarak ayarlayabilirsiniz. Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir. İstemci dağıtıldığında, bunun yerine "ChainTrust" değerini kullanın. Ayrıca değeri "Custom" veya "none" olarak da ayarlayabilirsiniz. "Custom" değerini kullanmak için, `CustomCertificateValidatorType` bir derlemeyi ve sertifikayı doğrulamak için kullanılan türünü de ayarlamanız gerekir. Kendi özel Doğrulayıcısı oluşturmak için soyut sınıftan devralması gerekir <xref:System.IdentityModel.Selectors.X509CertificateValidator> . Daha fazla bilgi için bkz. [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)Öğesi, `RevocationMode` sertifikaların iptal için nasıl denetlendiğini belirten bir özniteliği içerir. Varsayılan değer, sertifikaların iptal için otomatik olarak denetlendiğini belirten "çevrimiçi" dır. Daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)Öğesi yetkilendirme, özel rol sağlayıcıları ve kimliğe bürünme işlemlerini etkileyen öğeler içerir.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>Sınıf, bir hizmet yöntemine uygulanır. Özniteliği, korumalı bir yöntemin kullanımını yetkilendirirken kullanılacak kullanıcı gruplarını belirtir. Varsayılan değer "UseWindowsGroups" değeridir ve bir kaynağa erişmeye çalışan bir kimlik için "Yöneticiler" veya "kullanıcılar" gibi Windows gruplarının arandığını belirtir. Ayrıca `system.web` , aşağıdaki kodda gösterildiği gibi, <> öğesi altında yapılandırılan özel bir rol sağlayıcısı kullanmak için "UseAspNetRoles" belirtebilirsiniz.  
  
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
  
 Aşağıdaki kod, `roleProviderName` özniteliğiyle birlikte kullanılan öğesini gösterir `principalPermissionMode` .  
  
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
 [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md)Üzerine yazılan günlüğü ve günlüğe kaydedilecek olay türlerini belirtmek için öğesini kullanın. Daha fazla bilgi için bkz. [Denetim](auditing-security-events.md).  
  
```xml  
<behaviors>
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
 Yapılandırma ve istemci kodu İndirmeleri sağladığından, istemcilere meta verilerin verilmesi, hizmet ve istemci geliştiricileri için uygundur. Bir hizmetin kötü amaçlı kullanıcılara maruz kalmasını azaltmak için, HTTP (HTTPS) üzerinden SSL (HTTPS) mekanizmasını kullanarak aktarımı güvenli hale getirmek mümkündür. Bunu yapmak için, önce uygun bir X. 509.952 sertifikasını hizmeti barındıran bilgisayardaki belirli bir bağlantı noktasına bağlamanız gerekir. (Daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).) İkinci olarak, [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) hizmet yapılandırmasına bir ekleyin ve `HttpsGetEnabled` özniteliğini olarak ayarlayın `true` . Son olarak, `HttpsGetUrl` Aşağıdaki örnekte gösterildiği gibi, özniteliğini hizmet meta veri uç noktasının URL 'si olarak ayarlayın.  
  
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

- [Denetim](auditing-security-events.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
