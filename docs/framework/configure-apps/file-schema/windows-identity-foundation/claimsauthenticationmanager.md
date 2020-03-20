---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152755"
---
# <a name="claimsauthenticationmanager"></a>\<İddialarAuthenticationManager>
Gelen talepler için bir talep kimlik doğrulama yöneticisi kaydeder.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<İddialarAuthenticationManager>**  
  
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
|type|<xref:System.Security.Claims.ClaimsAuthenticationManager> Sınıftan türeyen özel bir tür belirtir. Öznitelik nasıl belirtilir `type` hakkında daha fazla bilgi için bkz: [Özel Tür Başvuruları].|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Öznitelik yoksa `type` veya `type` öznitelik <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıfa başvuruyorsa, `<claimsAuthenticationManager>` öğe alt öğeleri almaz; ancak, türetilen <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıflar alt yapılandırma öğelerini tanımlayabilir.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Security.Claims.ClaimsAuthenticationManager> Sınıf aracılığıyla sağlanan varsayılan davranış, gelen talepleri yineler. Öznitelik `type` belirtilmemişse veya `type` öznitelik sınıfı <xref:System.Security.Claims.ClaimsAuthenticationManager> belirtmiyorsa, `<claimsAuthenticationManager>` öğe alt öğeleri almaz. Özel davranış `type` uygulamak için <xref:System.Security.Claims.ClaimsAuthenticationManager> sınıftan türetilen bir türü kaydetmek için özniteliği belirtebilirsiniz. Türemiş sınıflar, bu öğeleri `<claimsAuthenticationManager>` işlemek için <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> yöntemi geçersiz kılarak öğenin alt öğeleri aracılığıyla yapılandırmayı destekleyebilir. Alt öğeler için tanımlanan şema sınıfın tasarımcısına kılır.  
  
 Öğe `<claimsAuthenticationManager>` <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> özelliği ayarlar.  
  
## <a name="example"></a>Örnek  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
