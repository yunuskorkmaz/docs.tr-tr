---
title: '&lt;claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4d4a91e0ed1f437089e26e5902515f73a15d94a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimsauthenticationmanagergt"></a>&lt;claimsAuthenticationManager&gt;
Talep kimlik doğrulama Yöneticisi gelen talepler için kaydeder.  
  
 \<system.identityModel>  
\<identityConfiguration >  
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
|türü|Türetilen bir özel tür belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı. Nasıl belirleneceği hakkında daha fazla bilgi için `type` [özel tür başvuruları] özniteliği için bkz.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Varsa hiçbir `type` özniteliği veya `type` özniteliği başvuruları <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı, `<claimsAuthenticationManager>` öğesi alt öğe olmaz; ancak, türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthenticationManager> alt yapılandırma öğeleri tanımlayabilirsiniz.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Üzerinden sağlanan varsayılan davranışı <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı gelen talepleri görüntülemektedir. Öyle değilse `type` özniteliği belirtilmediyse veya `type` özniteliği belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı, `<claimsAuthenticationManager>` öğesi alt öğe olmaz. Belirleyebileceğiniz `type` türü kaydetmek için öznitelik türetilen <xref:System.Security.Claims.ClaimsAuthenticationManager> özel davranışı uygulamak için sınıf. Türetilen sınıflar, alt öğelerinin üzerinden yapılandırmayı destekleyebilir `<claimsAuthenticationManager>` kılarak öğesi <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> bu öğeleri işlemek için yöntem. Alt öğeler için tanımlanan şema Sınıf Tasarımcısı kadar olur.  
  
 `<claimsAuthenticationManager>` Öğesi kümeleri <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="example"></a>Örnek  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
