---
title: '&lt;knownCertificates&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f62a43f1f8d3d025f62efca341c35e4af590abd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltknowncertificatesgt"></a>&lt;knownCertificates&gt;
Bir güvenlik belirteci hizmeti (STS) gelen verilen güvenlik kimlik bilgilerini doğrulamak için sağlanan X.509 sertifikalarını koleksiyonunu temsil eder.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceCredentials >  
\<issuedTokenAuthentication >  
\<knownCertificates >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<knownCertificates>   
      <add findValue="String"  
         storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
           x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|Bir X.509 sertifikası koleksiyona ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|Bir hizmeti kimlik bilgileri verilen bir belirteç belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Verilen belirteç senaryo üç aşamadan oluşur. İlk aşamada, bir hizmet erişmeye çalışan istemci bilinir bir *güvenli belirteç hizmeti*. Güvenli belirteç hizmeti istemcinin kimliğini doğrular ve bundan sonra istemci genellikle bir güvenlik onaylar biçimlendirme dili (SAML) belirteci bir belirteç verir. İstemci ardından belirteci ile hizmetine döndürür. Hizmet belirteci ve bu nedenle istemci kimliğini doğrulamak hizmet veren veriler için belirteç inceler. Belirteç kimlik doğrulaması için sertifika güvenli belirteç hizmeti kullandığı hizmete bilinmelidir.  
  
 [ \<İssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) depo böyle herhangi bir güvenli belirteç hizmeti sertifika için bir öğedir. Sertifika eklemek için kullanın [ \<knownCertificates > öğesi](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). INSERT bir [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) aşağıdaki örnekte gösterildiği gibi her sertifika için.  
  
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
  
 Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi yanı sıra, bir Federasyon Hizmeti tarafından kimliği doğrulanmış bir istemci için gereken koşulları gözden geçirmek için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgileri yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md). Federasyon senaryoları hakkında daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Yapılandırma koleksiyonunda doldurmak nasıl oluşturulduğunu gösteren örnek için bkz: [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [Güvenlik davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Nasıl yapılır: federe bir hizmette kimlik bilgilerini yapılandırın](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Sertifikalar ile çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
