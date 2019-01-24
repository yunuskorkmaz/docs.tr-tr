---
title: '&lt;knownCertificates&gt;'
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 49e5236abdc82fb4ca004c611e706e74fa99bf7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687355"
---
# <a name="ltknowncertificatesgt"></a>&lt;knownCertificates&gt;
Bir güvenlik belirteci hizmeti (STS) öğesinden verilen güvenlik kimlik bilgilerinin doğrulanması için sağlanan X.509 Sertifika koleksiyonunu temsil eder.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
\<ServiceCredentials >  
\<knownCertificates >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|Koleksiyonuna bir X.509 sertifikası ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ServiceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|Bir hizmet kimlik bilgisi olarak verilen bir belirteç belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Verilen belirteç senaryo üç aşamadan oluşur. Bir istemci bir hizmeti erişmeye ilk aşamada, başvurulan bir *güvenli belirteç hizmeti*. Güvenli belirteç hizmeti daha sonra istemci kimliğini doğrular ve bundan sonra istemci genellikle bir güvenlik onaylama işaretleme dili (SAML) belirteci bir belirteç verir. İstemci, ardından belirteci ile hizmetine döndürür. Belirteç için belirteç ve bu nedenle istemci kimliğini doğrulamak hizmet veren bir veri hizmeti inceler. Belirteç kimlik doğrulaması için sertifika hizmete güvenli belirteç hizmeti kullandığı olarak bilinmesi gerekir.  
  
 [ \<ServiceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) depo gibi herhangi bir güvenli belirteç hizmeti sertifika için bir öğedir. Sertifikaları eklemek için [ \<knownCertificates > öğesi](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). INSERT bir [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) aşağıdaki örnekte gösterildiği gibi her sertifika için.  
  
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
  
 Varsayılan olarak, sertifikaları güvenli bir belirteci Hizmeti'nden alınmalıdır. Bu "sertifikalar, istemciler yalnızca yasal olun bilinen" bir hizmete erişebilir.  
  
 Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi yanı sıra, bir Federasyon Hizmeti tarafından doğrulanması bir istemci için gereken koşulları gözden geçirmek için bkz: [nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md). Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Yapılandırma koleksiyonunda doldurmak nasıl gösteren bir örnek için bkz: [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [\<ServiceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Federasyon ve Verilen Belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
