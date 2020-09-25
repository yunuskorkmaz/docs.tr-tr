---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: c21e5186b8afdf8c72cbfc605af94c95bc2bc0d5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201388"
---
# \<certificateReference>

Bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a>Syntax  
  
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
|storeName|X. 509.440 sertifika deposunun adı. Varsayılan değer "My" dır. İsteğe bağlı.|  
|storeLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>X. 509.440 sertifika deposunun konumunu belirten bir değer. Varsayılan değer "LocalMachine" dır. İsteğe bağlı.|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType>Yürütülecek arama türünü belirten bir değer. Varsayılan değer "FindBySubjectDistinguishedName" dır. İsteğe bağlı.|  
|findValue|X. 509.440 sertifika deposunda Aranacak değer. İsteğe bağlı.|  
|Ischaindahil|Doğrulamanın sertifika zinciri kullanılarak gerçekleştirilip gerçekleştirilmeyeceğini belirtir. Varsayılan değer "true" 'dur; doğrulama, sertifika zinciri kullanılarak gerçekleştirilir. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan sertifikayı yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `<certificateReference>`Öğesi, bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirler. Öğesinin alt öğesi olarak belirtildiğinde `<serviceCertificate>` , belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan X. 509.440 sertifikasının konumunu ve doğrulama ayarlarını belirtir. `<certificateReference>`Öğesi sınıfı tarafından temsil edilir <xref:System.ServiceModel.Configuration.CertificateReferenceElement> .
