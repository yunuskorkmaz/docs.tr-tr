---
title: <clientCertificate><clientCredentials> öğesinin
ms.date: 03/30/2017
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
ms.openlocfilehash: fb95ef3168378227e41e55c6fd5e5b772cb7ad0f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400513"
---
# <a name="clientcertificate-of-clientcredentials-element"></a>\<\<ClientCredentials > öğesinin ClientCertificate >
Bir hizmette istemcinin kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikası tanımlar.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clientCertificate >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<clientCertificate findValue="String"
                   storeLocation="LocalMachine/CurrentUser"
                   storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                   X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`findValue`|X. 509.440 sertifika deposunda aranacak değeri içeren bir dize. Özniteliğinde yer alan türün, `X509FindType` öznitelik değerinin gereksinimlerini karşılaması gerekir. Varsayılan değer boş bir dizedir.|  
|`storeLocation`|İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı X. 509.952 sertifikasının konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -LocalMachine: yerel makineye atanan sertifika depolama alanı.<br />-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.<br /><br /> Varsayılan değer LocalMachine 'dir. Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|`storeName`|Arama yapılacak X. 509.440 sertifika deposunun adını belirtir. Geçerli değerler şunlardır:<br /><br /> -AddressBook: Diğer kullanıcılar için sertifika deposu.<br />-AuthRoot: Üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />CertificateAuthority Ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />Veril İptal edilen sertifikalar için sertifika deposu.<br />My Kişisel Sertifikalar için sertifika deposu.<br />Asıl Güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />TrustedPeople Doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.<br />-TrustedPublisher: Doğrudan güvenilen yayımcılar için sertifika deposu.<br /><br /> Varsayılan My. Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Yürütülecek X. 509.440 aramasının türünü tanımlar. `findValue` Özniteliğinde yer alan türün bu özniteliğin gereksinimlerini karşılaması gerekir. Geçerli değerler şunlardır:<br /><br /> -Findbyparmak Izi<br />-FindBySubjectName<br />- FindBySubjectDistinguishedName<br />-FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />- FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Varsayılan değer FindBySubjectDistinguishedName ' dir. Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](clientcredentials.md)|Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi, bu öğeyle istemcinin kimliğini doğrulamak için kullanılan sertifikayı belirtir. Daha fazla bilgi için [nasıl yapılır: Istemci kimlik bilgileri değerlerini](../../../wcf/how-to-specify-client-credential-values.md)belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Nasıl yapılır: Istemci kimlik bilgileri değerlerini belirtme](../../../wcf/how-to-specify-client-credential-values.md)
- [İstemcileri Güvenli Hale Getirme](../../../wcf/securing-clients.md)
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
