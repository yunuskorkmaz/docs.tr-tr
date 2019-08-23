---
title: <serviceCertificate> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 36a228da262095bfe05d66c6d44ac73ba0ca401b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936310"
---
# <a name="servicecertificate-of-servicecredentials"></a>\<\<ServiceCredentials > > ServiceCertificate
Ileti güvenlik modunu kullanan istemcilere hizmetin kimliğini doğrulamak için kullanılacak bir X. 509.952 sertifikası belirtin.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
\<serviceCredentials>  
\<serviceCertificate >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceCertificate findValue="String"
                    storeLocation="LocalMachine/CurrentUser"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`findValue`|X. 509.440 sertifika deposunda aranacak değeri içeren bir dize. Özniteliğinde yer alan türün belirtilen X509FindType gereksinimlerini karşılaması gerekir. Varsayılan değer boş bir dizedir.|  
|`storeLocation`|İstemcinin sunucusunun sertifikasını doğrulamak için kullandığı X. 509.952 sertifika deposunun konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -LocalMachine: yerel makineye atanan sertifika depolama alanı.<br />-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.<br /><br /> Varsayılan değer LocalMachine 'dir.|  
|`storeName`|Açılacak X. 509.440 sertifika deposunun adını belirtir. Geçerli değerler şunlardır:<br /><br /> -AddressBook: Diğer kullanıcılar için sertifika deposu.<br />-AuthRoot: Üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />-CertificatAuthority: Ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />Veril İptal edilen sertifikalar için sertifika deposu.<br />My Kişisel Sertifikalar için sertifika deposu.<br />Asıl Güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />TrustedPeople Doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.<br />-TrustedPublisher: Doğrudan güvenilen yayımcılar için sertifika deposu.<br /><br /> Varsayılan My.|  
|`x509FindType`|Yürütülecek X. 509.440 aramasının türünü tanımlar. Geçerli değerler şunlardır:<br /><br /> -Findbyparmak Izi<br />-FindBySubjectName<br />- FindBySubjectDistinguishedName<br />-FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />- FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> `findValue` Özniteliğinde yer alan türün belirtilen X509FindType gereksinimlerini karşılaması gerekir.<br /><br /> Varsayılan değer FindBySubjectDistinguishedName ' dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](servicecredentials.md)|Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ileti güvenliği modunu kullanan istemcilere hizmetin kimliğini doğrulamak için kullanılacak bir X. 509.952 sertifikası belirtmek için bu öğeyi kullanın. Düzenli olarak yenilenen bir sertifika kullanıyorsanız, parmak izi değişir. Bu durumda, sertifika aynı konu adıyla yeniden verilmediğinden konu `x509FindType` adını olarak kullanın.  
  
 Öğesini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Istemci kimlik bilgileri değerlerini](../../../wcf/how-to-specify-client-credential-values.md)belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [Nasıl yapılır: Istemci kimlik bilgileri değerlerini belirtme](../../../wcf/how-to-specify-client-credential-values.md)
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
