---
title: <issuedTokenAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 280aa49019f68a0906307e24842a585a92c6600a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925362"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a>\<\<ServiceCredentials > IssuedTokenAuthentication >
Hizmet kimlik bilgisi olarak verilen özel bir belirteci belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
\<serviceCredentials>  
\<IssuedTokenAuthentication >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`allowedAudienceUris`|<xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin kümesini alır. Bu özniteliği kullanma hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.|  
|`allowUntrustedRsaIssuers`|Güvenilmeyen RSA sertifikası verenler için izin verilip verilmeyeceğini belirten bir Boole değeri.<br /><br /> Sertifikalar, özgünlük doğrulaması için sertifika yetkilileri (CA) tarafından imzalanır. Güvenilmeyen bir veren, sertifikaları imzalamak için güvenilmeyecek şekilde belirtilmemiş bir CA 'dır.|  
|`audienceUriMode`|<xref:System.IdentityModel.Tokens.SamlSecurityToken> Güvenlik<xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> belirtecinin doğrulanıp doğrulanması gerekip gerekmediğini belirten bir değer alır. Bu değer türünde <xref:System.IdentityModel.Selectors.AudienceUriMode>. Bu özniteliği kullanma hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.|  
|`certificateValidationMode`|Sertifika doğrulama modunu ayarlar. Geçerli değerlerinden <xref:System.ServiceModel.Security.X509CertificateValidationMode>biri. Olarak `Custom`ayarlanırsa, bir `customCertificateValidator` de sağlanmalıdır. Varsayılan, `ChainTrust` değeridir.|  
|`customCertificateValidatorType`|İsteğe bağlı dize. Özel bir türü doğrulamak için kullanılan tür ve derleme. Bu öznitelik `certificateValidationMode` , olarak `Custom`ayarlandığında ayarlanmalıdır.|  
|`revocationMode`|Bir iptal denetiminin oluşup oluşmadığını ve çevrimiçi veya çevrimdışı gerçekleştirildiğini belirten iptal modunu ayarlar. Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.|  
|`samlSerializer`|Hizmet kimlik bilgisi için kullanılan SamlSerializer türünü belirten isteğe bağlı bir dize özniteliği. Varsayılan değer boş bir dizedir.|  
|`trustedStoreLocation`|İsteğe bağlı sabit listesi. İki sistem depolama konumlarından biri: `LocalMachine` veya. `CurrentUser`|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`knownCertificates`|Hizmet kimlik bilgisi için <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> güvenilen verenler belirten bir öğe koleksiyonunu belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](servicecredentials.md)|Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Verilen belirteç senaryosunda üç aşama vardır. İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti*denir. Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir. İstemci daha sonra belirtece sahip hizmete geri döner. Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler. Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.  
  
 Bu öğe, bu tür güvenli belirteç hizmeti sertifikalarının deposıdır. Sertifika eklemek için, [ \<KnownCertificates >](knowncertificates.md)kullanın. Aşağıdaki örnekte gösterildiği gibi her sertifika için bir [ \<ekleme >](add-of-knowncertificates.md) ekleyin.  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir. Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.  
  
 Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
