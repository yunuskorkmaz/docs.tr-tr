---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 6c9c77f96ff6032de43d9b5a257bc0796a19b858
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269347"
---
# <a name="certificatereference"></a>\<certificateReference >
Bulmak ve bir sertifika deposunda bir X.509 sertifikasını doğrulamak için kullanılan ayarları belirtir.  
  
 \<System.IdentityModel.Services >  
\<Federationconfiguration'a >  
\<serviceCertificate >  
\<certificateReference >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|storeName|X.509 Sertifika deposunun adı. Varsayılan değer "My". İsteğe bağlı.|  
|storeLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun konumunu belirten bir değer. "LocalMachine" varsayılan değerdir. İsteğe bağlı.|  
|X509FindType|Bir <xref:System.Security.Cryptography.X509Certificates.X509FindType> yürütüleceğini arama türünü belirten bir değer. "FindBySubjectDistinguishedName" varsayılandır. İsteğe bağlı.|  
|findValue|X.509 sertifika deposunda aranacak değer. İsteğe bağlı.|  
|isChainIncluded|Sertifika zinciri kullanarak doğrulama gerçekleştirilip gerçekleştirilmeyeceğini belirtir. Varsayılan değer: "true"; Sertifika zinciri kullanarak doğrulama gerçekleştirilir. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Şifreleme ve belirteç şifre çözme için kullanılan sertifikayı yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<certificateReference>` Öğesi bulmak ve bir sertifika deposunda bir X.509 sertifikasını doğrulamak için kullanılan ayarları belirtir. Bunu belirtildiğinde alt öğesi olarak `<serviceCertficate>` öğesi, şifreleme ve belirteç şifre çözme için kullanılan X.509 sertifikasının konumunu ve doğrulama ayarlarını belirtir. `<certificateReference>` Öğesi tarafından temsil edilen <xref:System.ServiceModel.Configuration.CertificateReferenceElement> sınıfı.
