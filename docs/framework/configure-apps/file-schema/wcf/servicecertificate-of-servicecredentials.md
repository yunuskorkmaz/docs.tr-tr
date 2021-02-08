---
description: 'Hakkında daha fazla bilgi <serviceCertificate> edinin: <serviceCredentials>'
title: <serviceCertificate> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: ab52f27949168562ec0cab0433c95843a7c312d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786739"
---
# <a name="servicecertificate-of-servicecredentials"></a>\<serviceCertificate> / \<serviceCredentials>

Ileti güvenlik modunu kullanan istemcilere hizmetin kimliğini doğrulamak için kullanılacak bir X. 509.952 sertifikası belirtin.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a>Syntax  
  
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
|`storeName`|Açılacak X. 509.440 sertifika deposunun adını belirtir. Geçerli değerler şunlardır:<br /><br /> -AddressBook: diğer kullanıcılar için sertifika deposu.<br />-AuthRoot: üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />-CertificatAuthority: ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />-İzin verilmeyen: iptal edilen sertifikalar için sertifika deposu.<br />-My: kişisel sertifikalar için sertifika deposu.<br />-Root: güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />-Trustedkişiler: doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.<br />-TrustedPublisher: doğrudan güvenilen yayımcılar için sertifika deposu.<br /><br /> Varsayılan My şeklindedir.|  
|`x509FindType`|Yürütülecek X. 509.440 aramasının türünü tanımlar. Geçerli değerler şunlardır:<br /><br /> -Findbyparmak Izi<br />-FindBySubjectName<br />- FindBySubjectDistinguishedName<br />-FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />- FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Özniteliğinde yer alan türün `findValue` belirtilen X509FindType gereksinimlerini karşılaması gerekir.<br /><br /> Varsayılan değer FindBySubjectDistinguishedName ' dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Ileti güvenliği modunu kullanan istemcilere hizmetin kimliğini doğrulamak için kullanılacak bir X. 509.952 sertifikası belirtmek için bu öğeyi kullanın. Düzenli olarak yenilenen bir sertifika kullanıyorsanız, parmak izi değişir. Bu durumda, `x509FindType` sertifika aynı konu adıyla yeniden verilmediğinden konu adını olarak kullanın.  
  
 Öğesini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Istemci kimlik bilgisi değerlerini belirtme](../../../wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme](../../../wcf/how-to-specify-client-credential-values.md)
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
