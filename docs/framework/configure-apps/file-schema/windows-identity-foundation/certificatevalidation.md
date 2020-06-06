---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252132"
---
# \<certificateValidation>
Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler. Belirli bir işleyici kendi doğrulayıcısı ile yapılandırıldıysa, bu ayarlar geçersiz kılınır.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
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
|certificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode>X. 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer. Varsayılan değer "PeerOrChainTrust" dır. Özel bir doğrulayıcı belirtmek için, bu özniteliği "Custom" olarak ayarlayın ve öğesini kullanarak Doğrulayıcısı belirtin [\<certificateValidator>](certificatevalidator.md) . İsteğe bağlı.|  
|Revocationmodu|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>X. 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer. Varsayılan değer "çevrimiçi" dır. İsteğe bağlı.|  
|trustedStoreLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>X. 509.440 sertifika deposunu belirten bir değer. Varsayılan değer "LocalMachine" dır. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|Sertifika doğrulaması için özel bir tür belirtir. Bu tür yalnızca `certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) öğenin özniteliği "Custom" olarak ayarlandığında kullanılır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğesi `<certificateValidation>` , öğesinin altındaki hizmet düzeyinde `<identityConfiguration>` veya öğesinin altındaki güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir `<securityTokenHandlerConfiguration>` . Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar. Bazı belirteç işleyicileri, yapılandırmada sertifika doğrulama ayarlarını belirtmenize olanak tanır. Bağımsız belirteç işleyicilerindeki ayarlar, hem hizmet düzeyinde hem de güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.  
  
## <a name="example"></a>Örnek  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
