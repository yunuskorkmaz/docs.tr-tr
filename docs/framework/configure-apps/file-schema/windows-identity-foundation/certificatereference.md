---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c8acf4b6d6e6e8a0fcf7d73139a1d2c5ea03f063
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatereferencegt"></a>&lt;certificateReference&gt;
Bul ve bir X.509 sertifikası sertifika deposunda doğrulamak için kullanılan ayarları belirtir.  
  
 \<system.identityModel.services >  
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
|storeName|X.509 Sertifika deposu adı. Varsayılan değer "Benim". İsteğe bağlı.|  
|storeLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun konumu belirten değer. Varsayılan değer "LocalMachine" dir. İsteğe bağlı.|  
|X509FindType|Bir <xref:System.Security.Cryptography.X509Certificates.X509FindType> yürütüleceğini arama türünü belirten değer. Varsayılan değer "FindBySubjectDistinguishedName" dir. İsteğe bağlı.|  
|findValue|X.509 sertifika deposunda arama için değer. İsteğe bağlı.|  
|isChainIncluded|Sertifika zincirini kullanarak doğrulama gerçekleştirilmesi gerekip gerekmediğini belirtir. Varsayılan değer "true"; doğrulama, sertifika zinciri kullanılarak gerçekleştirilir. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Şifrelemek ve belirteçlerin şifresini çözmek için kullanılan sertifikayı yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<certificateReference>` Öğesi bulmak ve bir X.509 sertifikası sertifika deposunda doğrulamak için kullanılan ayarları belirtir. Bunu belirtildiğinde alt öğesi olarak `<serviceCertficate>` öğesi, şifrelemek ve belirteçlerin şifresini çözmek için kullanılan X.509 sertifikasının konumunu ve doğrulama ayarlarını belirtir. `<certificateReference>` Öğesi ile temsil edilir <xref:System.ServiceModel.Configuration.CertificateReferenceElement> sınıfı.
