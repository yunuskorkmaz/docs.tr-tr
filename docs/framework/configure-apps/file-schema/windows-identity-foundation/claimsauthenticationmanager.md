---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 3602a4805e86833ba6070d801cef6758aaee8a5c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941822"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager >
Gelen talepler için bir talep kimlik doğrulama Yöneticisi kaydeder.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<claimsAuthenticationManager >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|türü|<xref:System.Security.Claims.ClaimsAuthenticationManager> Sınıfından türetilen özel bir tür belirtir. `type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları].|  
  
### <a name="child-elements"></a>Alt Öğeler  
 `type` <xref:System.Security.Claims.ClaimsAuthenticationManager> Öznitelik yoksa veya öznitelik sınıfa <xref:System.Security.Claims.ClaimsAuthenticationManager> başvuruyorsa, öğesialtöğelerialmaz;ancak,öğesindentüretilmişsınıflaraltyapılandırmaöğelerinitanımlayabilir.`<claimsAuthenticationManager>` `type`  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IdentityConfiguration >](identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Security.Claims.ClaimsAuthenticationManager> Sınıfı aracılığıyla sunulan varsayılan davranış, gelen talepleri yankılar. Hiçbir `type` öznitelik belirtilmemişse veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı `<claimsAuthenticationManager>` belirtiyorsa, öğesi alt öğeleri almaz. Özel davranışı uygulamak için `type` <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfından türetilmiş bir türü kaydetmek üzere özniteliğini belirtebilirsiniz. Türetilmiş sınıflar, bu öğeleri işlemek için `<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> yöntemini geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir. Alt öğeler için tanımlanan şema, sınıfının tasarımcısına kadar olur.  
  
 `<claimsAuthenticationManager>` Öğesi özelliği<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> ayarlar.  
  
## <a name="example"></a>Örnek  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
