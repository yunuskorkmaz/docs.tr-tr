---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152755"
---
# \<claimsAuthenticationManager>
Gelen talepler için bir talep kimlik doğrulama Yöneticisi kaydeder.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
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
|tür|Sınıfından türetilen özel bir tür belirtir <xref:System.Security.Claims.ClaimsAuthenticationManager> . Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].|  
  
### <a name="child-elements"></a>Alt Öğeler  
 `type`Öznitelik yoksa veya `type` öznitelik sınıfa başvuruyorsa, <xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthenticationManager>` öğesi alt öğeleri almaz; ancak, öğesinden türetilmiş sınıflar <xref:System.Security.Claims.ClaimsAuthenticationManager> alt yapılandırma öğelerini tanımlayabilir.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıfı aracılığıyla sunulan varsayılan davranış, <xref:System.Security.Claims.ClaimsAuthenticationManager> gelen talepleri yankılar. Hiçbir `type` öznitelik belirtilmemişse veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfı belirtiyorsa, `<claimsAuthenticationManager>` öğesi alt öğeleri almaz. `type` <xref:System.Security.Claims.ClaimsAuthenticationManager> Özel davranışı uygulamak için sınıfından türetilmiş bir türü kaydetmek üzere özniteliğini belirtebilirsiniz. Türetilmiş sınıflar, `<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> Bu öğeleri işlemek için yöntemini geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir. Alt öğeler için tanımlanan şema, sınıfının tasarımcısına kadar olur.  
  
 `<claimsAuthenticationManager>`Öğesi <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği ayarlar.  
  
## <a name="example"></a>Örnek  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
