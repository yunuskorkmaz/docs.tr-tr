---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 7b8823d792e3f15846a9483d670994be4b368980
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273903"
---
# <a name="certificatevalidation"></a>\<certificateValidation >
Belirteç işleyicileri sertifikalarını doğrulamak için ayar denetler. Belirli bir işleyici kendi Doğrulayıcı ile yapılandırılmışsa, bu ayarlar geçersiz kılınır.  
  
 \<system.identityModel>  
\<identityConfiguration >  
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
|Certificatevalidationmode'u|Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası için kullanılacak doğrulama modu belirten bir değer. "PeerOrChainTrust" varsayılan değerdir. Özel Doğrulayıcı sağlayıcısı belirtmek için bu özniteliği "Özel" olarak ayarlanmış ve kullanarak Doğrulayıcı belirtin [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) öğesi. İsteğe bağlı.|  
|revocationMode|Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası için İptal modu belirten bir değer. Varsayılan değer "Çevrimiçi" olur. İsteğe bağlı.|  
|trustedStoreLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun belirten bir değer. "LocalMachine" varsayılan değerdir. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|Sertifika doğrulama için özel bir türünü belirtir. Bu tür, yalnızca kullanılan `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) "Özel" olarak ayarlanır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 A `<certificateValidation>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyi altında `<securityTokenHandlerConfiguration>` öğesi. Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar. Bazı belirteç işleyicileri yapılandırmada sertifika doğrulaması ayarları belirtmenize olanak sağlar. Ayarları tek tek belirteç işleyicileri belirtilen hizmet düzeyinde ve güvenlik belirteci işleyicisi koleksiyonu geçersiz kılar.  
  
## <a name="example"></a>Örnek  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
