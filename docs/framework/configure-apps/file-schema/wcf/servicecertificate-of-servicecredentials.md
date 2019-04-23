---
title: <serviceCertificate> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 086b700b94198aa36e61289178ebbed75d33da98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173569"
---
# <a name="servicecertificate-of-servicecredentials"></a>\<serviceCertificate >, \<issuedTokenAuthentication >
İstemcilere ileti güvenlik modunu kullanarak hizmet kimlik doğrulaması için kullanılan bir X.509 sertifikası belirtin.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
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
|`findValue`|X.509 sertifika deposunda aranacak değeri içeren bir dize. Özniteliğinde bulunan türü belirtilen X509FindType gereksinimlerini karşılaması gerekir. Varsayılan değer boş bir dizedir.|  
|`storeLocation`|İstemcinin sunucu sertifikasını doğrulamak için kullandığı X.509 Sertifika deposunun konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -LocalMachine: yerel makineye atanmış sertifika deposu.<br />-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.<br /><br /> LocalMachine varsayılandır.|  
|`storeName`|Açılacak X.509 Sertifika deposunun adını belirtir. Geçerli değerler şunlardır:<br /><br /> -Adres Defteri: Diğer kullanıcılar için sertifika deposu.<br />-AuthRoot: Üçüncü taraf sertifika yetkilileri (CA'lar) için sertifika deposu.<br />-CertificatAuthority: Ara Sertifika yetkilileri (CA'lar) için sertifika deposu.<br />-İzin verilmedi: İptal edilen sertifikalar için sertifika deposu.<br />-My: Kişisel Sertifikalar için sertifika deposu.<br />-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) için sertifika deposu.<br />-TrustedPeople: Doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.<br />-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposu.<br /><br /> Varsayılan değer benim.|  
|`x509FindType`|Yürütülecek X.509 arama türünü tanımlar. Geçerli değerler şunlardır:<br /><br /> -FindByThumbprint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-   FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-   FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Bulunan tür `findValue` öznitelik belirtilen X509FindType gereksinimlerini karşılaması gerekir.<br /><br /> FindBySubjectDistinguishedName varsayılan değerdir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Hizmet kimlik doğrulaması olarak kullanılacak kimlik bilgisini belirtir ve istemci kimlik bilgileri doğrulaması ilgili ayarları.|  
  
## <a name="remarks"></a>Açıklamalar  
 İstemcilere ileti güvenlik modunu kullanarak hizmet kimlik doğrulaması için kullanılan bir X.509 sertifikasını belirtmek için bu öğeyi kullanırsınız. Ardından, düzenli aralıklarla yenilenmesi bir sertifika kullanıyorsanız, parmak izi değişecektir. Bu durumda, konu adı olarak kullanmak `x509FindType` sertifika ile aynı konu adı verilmesi için.  
  
 Öğe kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: İstemci kimlik bilgileri değerlerini belirtme](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [Nasıl yapılır: İstemci kimlik bilgileri değerlerini belirtme](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)
- [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
