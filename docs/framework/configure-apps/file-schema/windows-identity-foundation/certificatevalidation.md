---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 8185153eb02c5794b0f6ac02a6837806f2073c07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941915"
---
# <a name="certificatevalidation"></a>\<certificateValidation >
Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler. Belirli bir işleyici kendi doğrulayıcısı ile yapılandırıldıysa, bu ayarlar geçersiz kılınır.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<certificateValidation >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|certificateValidationMode|X <xref:System.ServiceModel.Security.X509CertificateValidationMode> . 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer. Varsayılan değer "PeerOrChainTrust" dır. Özel bir doğrulayıcı belirtmek için, bu özniteliği "Custom" olarak ayarlayın ve [ \<CertificateValidator >](certificatevalidator.md) öğesini kullanarak Doğrulayıcısı belirtin. İsteğe bağlı.|  
|Revocationmodu|X <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer. Varsayılan değer "çevrimiçi" dır. İsteğe bağlı.|  
|trustedStoreLocation|X <xref:System.Security.Cryptography.X509Certificates.StoreLocation> . 509.440 sertifika deposunu belirten bir değer. Varsayılan değer "LocalMachine" dır. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<certificateValidator >](certificatevalidator.md)|Sertifika doğrulaması için özel bir tür belirtir. Bu tür yalnızca `certificateValidationMode` [ \<certificatevalidation >](certificatevalidation.md) öğesinin özniteliği "Custom" olarak ayarlandığında kullanılır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IdentityConfiguration >](identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğesi, `<identityConfiguration>` öğesinin altındaki hizmet düzeyinde veya öğesinin altındaki `<securityTokenHandlerConfiguration>` güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir. `<certificateValidation>` Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar. Bazı belirteç işleyicileri, yapılandırmada sertifika doğrulama ayarlarını belirtmenize olanak tanır. Bağımsız belirteç işleyicilerindeki ayarlar, hem hizmet düzeyinde hem de güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.  
  
## <a name="example"></a>Örnek  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
