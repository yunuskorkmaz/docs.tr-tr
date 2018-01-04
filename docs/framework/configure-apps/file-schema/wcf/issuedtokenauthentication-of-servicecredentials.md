---
title: "&lt;serviceCredentials&gt; için &lt;issuedTokenAuthentication&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1007abbb91787ed7be4fe3a7f8c1b0173191d60e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuedtokenauthenticationgt-of-ltservicecredentialsgt"></a>&lt;serviceCredentials&gt; için &lt;issuedTokenAuthentication&gt;
Bir hizmeti kimlik bilgileri özel bir belirteç belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceCredentials >  
\<issuedTokenAuthentication >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<issuedTokenAuthentication   
   allowUntrustedRsaIssuers="Boolean"  
   audienceUriMode="Always/BearerKeyOnly/Never"  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   samlSerializer="String"  
    trustedStoreLocation="CurrentUser/LocalMachine">  
      <allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
      </allowedAudienceUris>  
      <knownCertificates>   
         <add findValue="String"  
                 storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
      </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`allowedAudienceUris`|Hedef URI kümesini alır, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği. Bu öznitelik kullanma hakkında daha fazla bilgi için bkz: <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.|  
|`allowUntrustedRsaIssuers`|Güvenilmeyen RSA sertifika verenler izinleri olup olmadığını belirten bir Boole değeri.<br /><br /> Sertifikalar orijinalliğini doğrulamak için sertifika yetkililerini tarafından imzalanır. Güvenilmeyen bir veren sertifikaları imzalamak için güvenilecek belirtilmemiş bir CA'dır.|  
|`audienceUriMode`|Belirten bir değeri alır olup olmadığını <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirtecinin <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> doğrulanmalıdır. Bu değer türünde <xref:System.IdentityModel.Selectors.AudienceUriMode>. Bu öznitelik kullanma hakkında daha fazla bilgi için bkz: <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.|  
|`certificateValidationMode`|Sertifika doğrulama modunu ayarlar. Geçerli değerlerini birini <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Varsa kümesine `Custom`, sonra bir `customCertificateValidator` de sağlanmalıdır. Varsayılan, `ChainTrust` değeridir.|  
|`customCertificateValidatorType`|İsteğe bağlı dize. Tür ve bir özel tür doğrulamak için kullanılan derleme. Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.|  
|`revocationMode`|İptal denetimi olup oluşur ve çevrimiçi veya çevrimdışı gerçekleştirilen varsa belirten iptal modu ayarlar. Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.|  
|`samlSerializer`|Hizmet kimlik bilgisi için kullanılan SamlSerializer türünü belirtir. isteğe bağlı dize özniteliği. Varsayılan boş bir dizedir.|  
|`trustedStoreLocation`|İsteğe bağlı numaralandırması. İki sistem deposu konumlardan birini: `LocalMachine` veya `CurrentUser`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`knownCertificates`|Bir koleksiyonunu belirtir <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> öğeleri güvenilen verenler için hizmet kimlik bilgilerini belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Hizmet ve istemci kimlik doğrulama ile ilgili ayarları kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Verilen belirteç senaryo üç aşamadan oluşur. İlk aşamada, bir hizmet erişmeye çalışan istemci bilinir bir *güvenli belirteç hizmeti*. Güvenli belirteç hizmeti istemcinin kimliğini doğrular ve bundan sonra istemci genellikle bir güvenlik onaylar biçimlendirme dili (SAML) belirteci bir belirteç verir. İstemci ardından belirteci ile hizmetine döndürür. Hizmet belirteci ve bu nedenle istemci kimliğini doğrulamak hizmet veren veriler için belirteç inceler. Belirteç kimlik doğrulaması için sertifika güvenli belirteç hizmeti kullandığı hizmete bilinmelidir.  
  
 Bu öğe, bu tür bir güvenli belirteç hizmeti sertifikalar için depodur. Sertifika eklemek için kullanın [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). INSERT bir [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) aşağıdaki örnekte gösterildiği gibi her sertifika için.  
  
```xml  
<issuedTokenAuthorization>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Varsayılan olarak, sertifikaları güvenli bir belirteci Hizmeti'nden alınması gerekir. Bu ", istemciler yalnızca yasal olun sertifikaları bilinen" hizmet erişebilir.  
  
 Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgileri yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
