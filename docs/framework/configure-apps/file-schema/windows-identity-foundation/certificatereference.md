---
title: '&lt;certificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: e04dc90134aadfb8af7b0800c7144963d267f513
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206897"
---
# <a name="ltcertificatereferencegt"></a>&lt;certificateReference&gt;
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
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Şifreleme ve belirteç şifre çözme için kullanılan sertifikayı yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<certificateReference>` Öğesi bulmak ve bir sertifika deposunda bir X.509 sertifikasını doğrulamak için kullanılan ayarları belirtir. Bunu belirtildiğinde alt öğesi olarak `<serviceCertficate>` öğesi, şifreleme ve belirteç şifre çözme için kullanılan X.509 sertifikasının konumunu ve doğrulama ayarlarını belirtir. `<certificateReference>` Öğesi tarafından temsil edilen <xref:System.ServiceModel.Configuration.CertificateReferenceElement> sınıfı.
