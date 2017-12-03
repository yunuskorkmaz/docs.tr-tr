---
title: "&lt;clientCredentials&gt; Öğesi &lt;clientCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b42167491de72eff5f17dfd8f25ad862c118c23f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcertificategt-of-ltclientcredentialsgt-element"></a>&lt;clientCredentials&gt; Öğesi &lt;clientCertificate&gt;
Bir hizmet için bir istemci kimlik doğrulaması için kullanılan bir X.509 sertifikası tanımlar.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
\<clientCredentials >  
\<clientCertificate >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<clientCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`findValue`|X.509 sertifika deposunda arama için değer içeren bir dize. Özniteliğinde bulunan türü gereksinimlerini karşılaması gerekir `X509FindType` öznitelik değeri. Varsayılan boş bir dizedir.|  
|`storeLocation`|İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı X.509 sertifikasının konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -LocalMachine: Yerel Makine sertifika deposuna.<br />-Currentuser'a: sertifika deposuna geçerli kullanıcıya atanmış.<br /><br /> LocalMachine varsayılandır. Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|`storeName`|Aranacak X.509 Sertifika deposu adını belirtir. Geçerli değerler şunlardır:<br /><br /> -Adres Defteri: Diğer kullanıcılar sertifika deposu.<br />-AuthRoot: sertifika deposunu üçüncü taraf sertifika yetkilileri (CA'lar) için.<br />-CertificateAuthority: Ara sertifika yetkilileri (CA) sertifika deposu.<br />-İzin verilmeyen: mağaza iptal edilen sertifikaları için sertifika.<br />-My: Sertifika deposunda kişisel sertifikalar için.<br />-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) sertifika deposu.<br />-TrustedPeople: Doğrudan güvenilir kişiler ve kaynaklar sertifika deposu.<br />-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposu.<br /><br /> Varsayılan değer My. Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Yürütülecek X.509 arama türünü tanımlar. İçinde yer alan türü `findValue` özniteliği bu öznitelik gereksinimlerini karşılaması gerekir. Geçerli değerler şunlardır:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> FindBySubjectDistinguishedName varsayılan değerdir. Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Bir hizmet için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi bu öğeye sahip istemci kimlik doğrulaması için kullanılan sertifikayı belirtir. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Nasıl yapılır: istemci kimlik bilgileri değerlerini belirtme](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [Güvenlik davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Nasıl yapılır: istemci kimlik bilgileri değerlerini belirtme](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [İstemcilerinin güvenliğini sağlama](../../../../../docs/framework/wcf/securing-clients.md)  
 [Sertifikalar ile çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
