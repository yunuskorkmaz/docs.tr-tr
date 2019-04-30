---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: ecf26263bf47e8b4609e7adc208f0a59a2fa795b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667333"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager >
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
|türü|Öğesinden türetilen özel bir türü belirtiyor <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı. Belirtme hakkında daha fazla bilgi için `type` [özel tür başvurularını] özniteliği için bkz.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yoksa hiçbir `type` özniteliği veya `type` başvuruları öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı `<claimsAuthenticationManager>` öğenin alt öğeleri almaz; ancak, türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthenticationManager> alt yapılandırma öğeleri tanımlayabilirsiniz.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sağlanan varsayılan davranışı <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı gelen talepleri görüntülemektedir. Hayır ise `type` özniteliği veya `type` özniteliği belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı `<claimsAuthenticationManager>` öğenin alt öğeleri almaz. Belirtebileceğiniz `type` sınıfından türetilen bir tür kaydetmek için öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> özel davranışı uygulamak sınıfı. Türetilen sınıflar, alt öğelerinin konfigürasyonuyla destekleyebilir `<claimsAuthenticationManager>` kılarak öğesi <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> bu öğelerini işlemek için yöntemi. Sınıf Tasarımcısı kadar alt öğeleri için tanımlanan şema var.  
  
 `<claimsAuthenticationManager>` Öğe kümeleri <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="example"></a>Örnek  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
