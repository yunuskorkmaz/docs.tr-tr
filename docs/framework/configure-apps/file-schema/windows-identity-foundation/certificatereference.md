---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152820"
---
# <a name="certificatereference"></a>\<sertifikaReferans>
Bir sertifika deposunda X.509 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federasyonKonfigürasyon>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceSertifika>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sertifikaReferans>**  
  
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
|Storename|X.509 sertifika deposunun adı. Varsayılan değer "Benim"dir. İsteğe bağlı.|  
|Storelocation|X.509 sertifika deposunun konumunu belirten bir <xref:System.Security.Cryptography.X509Certificates.StoreLocation> değer. Varsayılan değer "LocalMachine"dir. İsteğe bağlı.|  
|X509findtype|Yürütülecek arama türünü belirten bir <xref:System.Security.Cryptography.X509Certificates.X509FindType> değer. Varsayılan "FindBySubjectDistinguishedName"dir. İsteğe bağlı.|  
|findValue|X.509 sertifika deposunda aranacak değer. İsteğe bağlı.|  
|isChainIncluded|Sertifika zinciri kullanılarak doğrulamanın yapılıp yapılmaması gerektiğini belirtir. Varsayılan "true"; doğrulama sertifika zinciri kullanılarak gerçekleştirilir. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 None  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceSertifika>](servicecertificate.md)|Belirteçleri şifrelemek ve şifresini çözmek için kullanılan sertifikayı yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `<certificateReference>` bir sertifika deposunda X.509 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir. `<serviceCertificate>` Öğenin alt öğesi olarak belirtildiğinde, belirteçleri şifrelemek ve şifresini çözmek için kullanılan X.509 sertifikasının konum ve doğrulama ayarlarını belirtir. Öğe `<certificateReference>` <xref:System.ServiceModel.Configuration.CertificateReferenceElement> sınıf tarafından temsil edilir.
